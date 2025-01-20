---
title: Kundenseitig verwaltete Schlüssel für AEM as a Cloud Service
description: Erfahren Sie, wie Sie Verschlüsselungsschlüssel für AEM as a Cloud Service verwalten
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 100ddbf2-9c63-406f-a78d-22862501a085
source-git-commit: 18fe0125351c635c226bebf0f309710634230e64
workflow-type: ht
source-wordcount: '1199'
ht-degree: 100%

---

# Einrichten von kundenseitig verwalteten Schlüsseln für AEM as a Cloud Service {#cusomer-managed-keys-for-aem-as-a-cloud-service}

AEM as a Cloud Service speichert derzeit Kundendaten in Azure Blob Storage und MongoDB, wobei zur Datensicherung standardmäßig vom Anbieter verwaltete Verschlüsselungsschlüssel verwendet werden. Dieses Setup erfüllt zwar die Sicherheitsanforderungen vieler Organisationen, aber Unternehmen in regulierten Branchen oder Unternehmen, die eine verbesserte Datensouveränität benötigen, streben möglicherweise eine bessere Kontrolle über ihre Verschlüsselungsverfahren an. Für Unternehmen, die Datensicherheit, Compliance und die Möglichkeit priorisieren, ihre Verschlüsselungsschlüssel zu verwalten, bietet die CMK-Lösung (Customer-Managed Keys, kundenseitig verwaltete Schlüssel) eine wichtige Verbesserung.

## Das zu lösende Problem {#the-problem-being-solved}

Von Anbietern verwaltete Schlüssel können für Unternehmen in Bereichen wie Finanzen, Gesundheitswesen und Behörden problematisch sein, in denen strenge Vorschriften eine umfassende Kontrolle über die Datensicherheit erfordern. Ohne Kontrolle über das Schlüssel-Management stehen Organisationen vor Herausforderungen bei der Einhaltung von Compliance-Anforderungen, der Implementierung benutzerdefinierter Sicherheitsrichtlinien und der Gewährleistung vollständiger Datensouveränität.

Durch die Einführung von kundenseitig verwalteten Schlüsseln (CMK) werden diese Bedenken behoben, da AEM-Kundschaft die volle Kontrolle über ihre Verschlüsselungsschlüssel erhält. Durch die Authentifizierung über die Microsoft Entra ID (ehemals Azure Active Directory) stellt AEM CS eine sichere Verbindung zu Azure Key Vault von Kundschaft her, sodass diese den Lebenszyklus ihrer Verschlüsselungsschlüssel verwalten kann, einschließlich Schlüsselerstellung, -rotation und -widerruf.

CMK bietet mehrere Vorteile:

* **Verbesserte Sicherheit:** Kundschaft kann sicherstellen, dass ihre Verschlüsselungsverfahren bestimmten Sicherheitsanforderungen entsprechen, sodass sie sich auf den Datenschutz verlassen kann.
* **Compliance-Flexibilität:** Aufgrund der vollständigen Kontrolle über den Lebenszyklus der Schlüssel können sich Unternehmen einfach an sich verändernde Regulierungsstandards wie DSGVO, HIPAA oder CCPA anpassen und so sicherzustellen, dass ihr Compliance-Status unverändert bleibt.
* **Nahtlose Integration:** Die CMK-Lösung kann direkt mit Azure Blob Storage und MongoDB in AEM CS integriert werden. So wird sichergestellt, dass der Speichervorgang und die Benutzerfreundlichkeit nicht beeinträchtigt werden. Gleichzeitig erhält Kundschaft leistungsstarke Verschlüsselungsfunktionen.

Durch die Verwendung von CMK kann Kundschaft die Kontrolle über ihre Datensicherheits- und Verschlüsselungsverfahren erhöhen, die Compliance verbessern und Risiken mindern, während sie gleichzeitig weiterhin von der Skalierbarkeit und Flexibilität von AEM CS profitiert.

Mit AEM as a Cloud Service können Sie Ihre eigenen Verschlüsselungsschlüssel für die Verschlüsselung von Daten im Ruhezustand mitbringen. In diesem Handbuch werden die Schritte zum Einrichten eines kundenseitig verwalteten Schlüssels (CMK) in Azure Key Vault für AEM as a Cloud Service beschrieben.

>[!WARNING]
>
>Nach dem Einrichten von CMK können Sie nicht zu systemseitig verwalteten Schlüsseln zurückkehren. Sie sind dafür verantwortlich, Ihre Schlüssel sicher zu verwalten und den Zugriff auf Ihre Key Vault-, Schlüssel- und CMK-App in Azure bereitzustellen, um zu verhindern, dass der Zugriff auf Ihre Daten verloren geht.

Außerdem werden Sie durch die folgenden Schritte zum Erstellen und Konfigurieren der erforderlichen Infrastruktur geführt:

1. Einrichten Ihrer Arbeitsumgebung
1. Erhalten einer Anwendungs-ID von Adobe
1. Erstellen einer neuen Ressourcengruppe
1. Erstellen eines Schlüsseltresors
1. Gewähren des Zugriffs auf den Schlüsseltresor für Adobe
1. Erstellen eines Verschlüsselungsschlüssels

Sie müssen die Schlüsseltresor-URL, den Verschlüsselungsschlüsselnamen und Informationen über den Schlüsseltresor für Adobe freigeben.

## Einrichten der Umgebung {#setup-your-environment}

Einzige Voraussetzung, um den Anweisungen dieses Handbuchs folgen zu können, ist die Azure-Befehlszeilenschnittstelle (CLI). Wenn Sie die Azure-CLI noch nicht installiert haben, befolgen Sie die offiziellen Installationsanweisungen [hier](https://learn.microsoft.com/de-de/cli/azure/install-azure-cli).

Bevor Sie mit dem Rest dieses Handbuchs fortfahren, melden Sie sich bitte mit `az login` bei Ihrer CLI an.

>[!NOTE]
>
>Obwohl dieses Handbuch die Azure-CLI verwendet, ist es möglich, dieselben Vorgänge über die Azure-Konsole auszuführen. Wenn Sie die Azure-Konsole bevorzugen, verwenden Sie die folgenden Befehle als Referenz.

## Erhalten einer Anwendungs-ID von Adobe {#obtain-an-application-id-from-adobe}

Adobe stellt Ihnen eine Entra-Anwendungs-ID zur Verfügung, die Sie zum Ausführen der restlichen Anweisungen in diesem Handbuch benötigen. Wenn Sie noch nicht über eine Anwendungs-ID verfügen, wenden Sie sich an Adobe, um eine zu erhalten.

## Erstellen einer neuen Ressourcengruppe {#create-a-new-resource-group}

Erstellen Sie eine neue Ressourcengruppe an einem Speicherort Ihrer Wahl.

```powershell
# Choose a location and a name for the resource group.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Create the resource group.
az group create --location $location --resource-group $resourceGroup
```

Wenn Sie bereits über eine Ressourcengruppe verfügen, können Sie stattdessen diese verwenden. Im Rest dieses Handbuchs werden der Speicherort der Ressourcengruppe und ihr Name mit `$location` bzw. `$resourceGroup` bezeichnet.

## Erstellen eines Schlüsseltresors {#create-a-key-vault}

Sie müssen einen Schlüsseltresor erstellen, der Ihren Verschlüsselungsschlüssel enthält. Für den Schlüsseltresor muss der Bereinigungsschutz aktiviert sein. Der Bereinigungsschutz ist erforderlich, um Daten im Ruhezustand von anderen Azure-Services zu verschlüsseln. Der Zugriff auf das öffentliche Netzwerk muss ebenfalls aktiviert sein, damit der Adobe-Mandant auf den Schlüsseltresor zugreifen kann.

>[!IMPORTANT]
>Wenn der Schlüsseltresor erstellt wird, während der Zugriff auf das öffentliche Netzwerk deaktiviert ist, wird erzwungen, dass alle Vorgänge im Zusammenhang mit dem Schlüsseltresor, wie Schlüsselerstellung oder -rotation, von einer Umgebung aus ausgeführt werden müssen, die Netzwerkzugriff auf den Schlüsseltresor hat – z. B. eine VM, die auf den Schlüsseltresor zugreifen kann.

```powershell
# Reuse this information from the previous step.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Choose a name for the key vault.
$keyVaultName="<KEY VAULT NAME>"

# Create the key vault.
az keyvault create `
  --location $location `
  --resource-group $resourceGroup `
  --name $keyVaultName `
  --default-action=Deny `
  --enable-purge-protection `
  --enable-rbac-authorization `
  --public-network-access Enabled
```

## Gewähren des Zugriffs auf den Schlüsseltresor für Adobe {#grant-adone-access-to-the-key-vault}

In diesem Schritt ermöglichen Sie Adobe den Zugriff auf Ihren Schlüsseltresor über eine Entra-Anwendung. Die ID der Entra-Anwendung sollte bereits von Adobe zur Verfügung gestellt worden sein.

Zunächst müssen Sie einen Dienstprinzipal erstellen, der an die Entra-Anwendung angehängt ist, und diesem die Rollen **Schlüsseltresorleser** und **Schlüsseltresor-Crypto-Benutzer** zuweisen. Die Rollen sind auf den in diesem Handbuch erstellten Schlüsseltresor beschränkt.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# The application ID is provided by Adobe.
$appId="<APPLICATION ID>"

# Retrieve the ID of the key vault.
$keyVaultId=(az keyvault show --resource-group $resourceGroup --name $keyVaultName --query id --output tsv)

# Create a new service principal.
$servicePrincipalId=(az ad sp create --id $appId --query id --out tsv)

# Assign the roles to the service principal.
az role assignment create --assignee $servicePrincipalId --role "Key Vault Reader" --scope $keyVaultId
az role assignment create --assignee $servicePrincipalId --role "Key Vault Crypto User" --scope $keyVaultId
```

## Erstellen eines Verschlüsselungsschlüssels {#create-an-ecryption-key}

Schließlich können Sie einen Verschlüsselungsschlüssel in Ihrem Schlüsseltresor erstellen. Bitte beachten Sie, dass Sie die Rolle **Schlüsseltresor-Crypto-Beauftragter** benötigen, um diesen Schritt abzuschließen. Wenn die angemeldete Benutzerin bzw. der angemeldete Benutzer nicht über diese Rolle verfügt, wenden Sie sich an den oder die Systemadmin, damit Ihnen diese Rolle zugewiesen wird, oder bitten Sie jemanden, der bereits über diese Rolle verfügt, diesen Schritt für Sie auszuführen.

Zum Erstellen des Verschlüsselungsschlüssels ist Netzwerkzugriff auf den Schlüsseltresor erforderlich. Stellen Sie zunächst sicher, dass Sie auf den Schlüsseltresor zugreifen können, und fahren Sie mit der Erstellung des Schlüssels fort:

```powershell
# Reuse this information from the previous steps.
$keyVaultName="<KEY VAULT NAME>"

# Chose a name for your key.
$keyName="<KEY NAME>"

# Create the key.
az keyvault key create --vault-name $keyVaultName --name $keyName
```

## Freigeben von Schlüsseltresorinformationen {#share-the-key-vault-information}

An dieser Stelle sind Sie bereit. Sie müssen nur einige erforderliche Informationen an Adobe freigeben und wir kümmern uns um die Konfiguration Ihrer Umgebung für Sie.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# Retrieve the URL of your key vault.
$keyVaultUri=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.vaultUri `
    --output tsv)

# In addition we would need the tenantId and the subscriptionId in order to setup the connection.
$tenantId=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.tenantId `
    --output tsv)
$subscriptionId="<Subscription ID>"
```


## Auswirkungen eines Widerrufs des Schlüsselzugriffs {#implications-of-revoking-key-access}

Das Widerrufen oder Deaktivieren des Zugriffs auf die Key Vault-, Schlüssel- oder CMK-App kann zu erheblichen Störungen führen, darunter auch zu Änderungen an den Vorgängen Ihrer Plattform, die Probleme verursachen könnten. Sobald diese Schlüssel deaktiviert sind, kann es sein, dass Daten in Platform nicht mehr zugänglich sind, und nachgelagerte Vorgänge, die auf diese Daten angewiesen sind, funktionieren nicht mehr. Es ist wichtig, die nachgelagerten Auswirkungen vollständig zu verstehen, bevor Sie Änderungen an Ihren Schlüsselkonfigurationen vornehmen.

Wenn Sie sich entscheiden, den Platform-Zugriff auf Ihre Daten zu widerrufen, können Sie dies tun, indem Sie die mit der Anwendung verknüpfte Benutzerrolle aus dem Schlüsseltresor in Azure entfernen.

## Nächste Schritte {#next-steps}

Kontaktaufnahme mit Adobe:

* Die URL Ihres Schlüsseltresors. Sie haben sie in diesem Schritt abgerufen und in der Variablen `$keyVaultUri` gespeichert.
* Der Name Ihres Verschlüsselungsschlüssels. Sie haben den Schlüssel in einem vorherigen Schritt erstellt und in der Variablen `$keyName` gespeichert.
* `$resourceGroup`, `$subscriptionId` und `$tenantId`, die zum Einrichten der Verbindung mit dem Schlüsseltresor erforderlich sind.

<!-- Alexandru: hiding this for now

### Private Link Approvals {#private-link-approvals}

>[!TIP]
>You can also consult the [Azure Documentation](https://learn.microsoft.com/en-us/azure/key-vault/general/private-link-service?tabs=portal#how-to-manage-a-private-endpoint-connection-to-key-vault-using-the-azure-portal) on how to approve a Private Endpoint Connection.

Afterwards, an Adobe Engineer assigned to you will contact you to confirm the creation of the private endpoints, and will request you to approve a set of required Connection Requests. The requests can be approved either using the Azure Portal UI, where you can go to **KeyVault > Settings > Networking > Private Endpoint Connections** and approve the requests with names similar to these: 

`mongodb-atlas-<REGION>-<NUMBER>`, `storage-account-private-endpoint` and `backup-storage-account-private-endpoint`. 

Notify the Adobe Engineer once this process is complete and the Private Endpoints show up as **Approved**. -->

## Kundenseitig verwaltete Schlüssel in Private Beta {#customer-managed-keys-in-private-beta}

Das Entwicklungs-Team von Adobe arbeitet derzeit an einer erweiterten Implementierung von CMK unter Verwendung von Azure Private Link. Die neue Implementierung ermöglicht die Freigabe Ihres Schlüssels über Azure-Backbone dank einer direkten Verbindung über Private Link zwischen dem Adobe-Mandanten und Key Vault.

Diese erweiterte Implementierung befindet sich derzeit in Private Beta und kann für ausgewählte Kundinnen und Kunden aktiviert werden, die sich damit einverstanden erklären, das Private Beta-Programm zu abonnieren und eng mit dem Entwicklungs-Team von Adobe zusammenzuarbeiten. Wenn Sie an der Private Beta für CMK unter Verwendung von Private Link interessiert sind, kontaktieren Sie Adobe für weitere Informationen.
