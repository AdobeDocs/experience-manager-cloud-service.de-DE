---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Erfahren Sie, wie Sie in Cloud Manager mithilfe der Domain-Einstellungen einen benutzerdefinierten Domain-Namen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b2852673ad313e5ea6be6dc0ed185d60a46fedeb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

Erfahren Sie, wie Sie in Cloud Manager mithilfe der **Domain-Einstellungen** einen benutzerdefinierten Domain-Namen hinzufügen.

## Voraussetzungen {#requirements}

Erfüllen Sie die folgenden Anforderungen, bevor Sie einen benutzerdefinierten Domain-Namen in Cloud Manager hinzufügen.

* *Bevor* Sie einen benutzerdefinierten Domain-Namen hinzufügen, müssen Sie ein SSL-Domain-Zertifikat für die gewünschte Domain hinzugefügt haben, wie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) beschrieben.
* Sie müssen über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzufügen zu können.
* Verwenden Sie Fastly oder ein anderes CDN (Content Delivery Network).

>[!IMPORTANT]
>
>Wenn Sie ein von Adobe verwaltetes CDN verwenden, müssen Sie Ihre Domain dennoch zu Cloud Manager hinzufügen.

## Wo Sie benutzerdefinierte Domain-Namen hinzufügen können {#where-to-add-cdn}

In Cloud Manager können Sie einen benutzerdefinierten Domain-Namen über die Seite [Domain-Einstellungen](#adding-cdn-settings) hinzufügen.

Beim Hinzufügen eines benutzerdefinierten Domain-Namens wird die Domain mit dem spezifischsten der gültigen Zertifikate bereitgestellt. Wenn mehrere Zertifikate dieselbe Domain haben, wird die zuletzt aktualisierte ausgewählt. Adobe empfiehlt, Zertifikate so zu verwalten, dass es keine überlappenden Domains gibt.

Die Schritte, die in diesem Dokument für beide Methoden beschrieben werden, basieren auf Fastly. Wenn Sie ein anderes CDN (Content Delivery Network) verwenden, konfigurieren Sie die Domain mit dem entsprechenden CDN.

## Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn-settings}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/ ) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie im Seitenmenü unter **Services** auf ![Einstellungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) **Domain-Einstellungen**.

   ![Fenster „Domain-Einstellungen“](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie oben rechts auf der Seite **Domain-Einstellungen** auf **Domain hinzufügen**.

1. Geben Sie im Dialogfeld **Domain hinzufügen** in das Feld **Domain-Name** den von Ihnen verwendeten benutzerdefinierten Domain-Namen ein.
Achten Sie bei der Eingabe des Domain-Namens darauf, weder `http://`, `https://` noch Leerzeichen einzuschließen.

   >[!NOTE]
   >
   >Wenn Sie sowohl die `www`- als auch die `non-www`-Version einer Domain benötigen, müssen Sie sie separat hinzufügen. Zum Beispiel `example.com` und `www.example.com`.
   <!-- Marius Petria on SLACK tmp-skyline-cdn-certificates - Actually  my opinion is that this option should be explicit in UI (that was present in the initial mocks of the design but for some reason it was dropped). I think when adding a domain there should be a check mark to also add www.domain. When adding example.com Customer should be prompted with the following options: Do you also want to add www.example.com and have a redirect example.com -> www.example.com?Do you also want to add www.example.com and have a redirect www.example.com -> example.com? -->

1. Klicken Sie auf **Erstellen**.

1. Wählen Sie im Dialogfeld **Domain verifizieren** aus der Dropdown-Liste **Welchen Zertifikatstyp möchten Sie mit dieser Domain verwenden?** eine der folgenden Optionen aus:

   | Option für den Zertifikatstyp | Beschreibung |
   | --- | --- |
   | Von Adobe verwaltetes SSL-Zertifikat (DV) | Wählen Sie diesen Zertifikatstyp aus, wenn Sie ein DV(Domain Validation)-Zertifikat verwenden möchten. Diese Option eignet sich in den meisten Fällen hervorragend, da sie eine grundlegende Domain-Validierung ermöglicht. Adobe verwaltet und erneuert das Zertifikat automatisch. |
   | Kundenseitig verwaltetes SSL-Zertifikat (OV/EV) | Wählen Sie diesen Zertifikatstyp aus, wenn zum Schutz der Domain ein EV/OV-SSL-Zertifikat verwendet werden soll. Diese Option bietet eine verbesserte Sicherheit mit OV (Organization Validation) oder EV (Extended Validation). Verwenden Sie sie, wenn eine strengere Überprüfung, eine höhere Vertrauensebene oder eine benutzerdefinierte Kontrolle über die Zertifikate erforderlich sind. |

1. Führen Sie im Dialogfeld **Domain verifizieren** je nach ausgewähltem Zertifikatstyp einen der folgenden Schritte aus:

   | Ausgewählter Zertifikatstyp | Beschreibung |
   | --- | ---  |
   | Verwaltetes Adobe-Zertifikat | a. Führen Sie die folgenden [Schritte für von Adobe verwaltete Zertifikate](#adobe-managed-cert-steps) aus. Klicken Sie nach Abschluss der Schritte im Dialogfeld **Domain verifizieren** auf **Überprüfen**.<ul><li>Die DNS-Überprüfung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.</li><li>Cloud Manager überprüft schließlich die Eigentümerschaft des Domain-Namens und aktualisiert den Status in der Tabelle **Domain-Einstellungen**. Weitere Informationen finden Sie unter [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).</li>![Überprüfen des Domain-Status](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. Sie können jetzt [ein von Adobe verwaltetes (DV) SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert).</li></ul> |
   | Kundenseitig verwaltetes Zertifikat | a. Klicken Sie auf **OK**.<br>b. Sie können jetzt ein [kundenseitig verwaltetes (OV/EV) SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert).<br>Nachdem Sie das Zertifikat hinzugefügt haben, wird Ihr Domain-Name in der Tabelle **Domain-Einstellungen** als verifiziert markiert. Weitere Informationen finden Sie unter [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).</li></ul><br>![Verifizieren der Domain für ein kundenseitig verwaltetes EV/OV-Zertifikat](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |

   >[!NOTE]
   >
   >Wenn Sie Ihr eigenes kundenseitig verwaltetes SSL-Zertifikat (OV/EV oder DV) verwenden und planen, einen kundenseitig verwalteten CDN-***Anbieter*** zu nutzen, müssen Sie kein SSL-Zertifikat hinzuzufügen. Gehen Sie stattdessen direkt zu [Hinzufügen einer CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md), sobald Sie dazu bereit sind.


### Schritte bei verwalteten Adobe-Zertifikaten {#adobe-managed-cert-steps}

Wenn Sie den Zertifikatstyp *Verwaltetes Adobe-Zertifikat* ausgewählt haben, führen Sie den folgenden Schritt im Dialogfeld **Domain verifizieren** aus.

![Schritte bei verwalteten Adobe-Zertifikaten](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

Um die verwendete Domain zu überprüfen, müssen Sie einen CNAME hinzufügen und überprüfen.

Ein `CNAME` -Record-Typ oder ein `A` -Record-Typ routet nach der Bereitstellung den gesamten Internet-Traffic für die Domäne an den Ort, an den sie verweist. Wenn dieser Speicherort nicht für den Traffic vorgesehen ist, kommt es zu einem Ausfall. Wenn er nicht getestet wurde, kann es zu Fehlern in den Inhalten kommen. Aus diesem Grund wird dieser Schritt immer durchgeführt, nachdem der Test abgeschlossen ist und Sie bereit sind, live zu gehen.

Um diese Einstellungen zu konfigurieren, legen Sie fest, ob ein `CNAME`- oder ein Apex-Eintrag so konfiguriert sein muss, dass Ihr benutzerdefinierter Domain-Name auf den Cloud Manager-Domain-Namen verweist. Die folgenden Abschnitte dieses Dokuments können Ihnen dabei helfen, zu ermitteln, welche Art von Eintrag für Ihre DNS-Konfiguration geeignet ist.

>[!NOTE]
>
>Bei von Adobe verwalteten CDNs sind bei Verwendung von DV(Domain Validation)-Zertifikaten nur Sites mit ACME-Validierung zulässig.

#### Voraussetzungen {#adobe-managed-cert-dv-requirements}

Sie müssen diese Anforderungen erfüllen, bevor Sie Ihre DNS-Einträge konfigurieren.

* Identifizieren Sie Ihren Domain-Host oder Ihre Registrierungsstelle, falls Sie sie noch nicht kennen.
* Sie müssen in der Lage sein, die DNS-Einträge für die Domain Ihres Unternehmens zu ändern, oder sich andernfalls an eine entsprechende Person wenden, die dies kann.
* Sie müssen Ihren konfigurierten, benutzerdefinierten Domain-Namen bereits überprüft haben, wie im Dokument [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) beschrieben.

#### CNAME-Eintrag {#adobe-managed-cert-cname-record}

Ein kanonischer Name oder CNAME-Eintrag ist eine Art von DNS-Eintrag, der einen Aliasnamen einem wahren oder kanonischen Domain-Namen zuordnet. CNAME-Datensätze werden normalerweise dazu verwendet, eine Unter-Domain wie `www.example.com` der Domain zuzuordnen, in der der Inhalt dieser Unter-Domain gehostet wird.

Melden Sie sich bei Ihrem DNS-Dienstleister an und erstellen Sie einen `CNAME`-Eintrag, um Ihren benutzerdefinierten Domain-Namen auf das Ziel verweisen zu lassen, wie in der folgenden Tabelle dargestellt.

| CNAME | Benutzerdefinierter Domain-Name, der auf das Ziel verweist |
| --- | --- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

#### APEX-Eintrag {#adobe-managed-cert-apex-record}

Eine Apex-Domain ist eine benutzerdefinierte Domain, die keine Subdomain enthält, z. B. `example.com`. Eine Apex-Domain wird mit einem `A`-, `ALIAS`- oder `ANAME`-Eintrag über Ihren DNS-Anbieter konfiguriert. Die Apex-Domains müssen auf bestimmte IP-Adressen verweisen.

Fügen Sie die folgenden `A`-Einträge über Ihren Domain-Provider in den DNS-Einstellungen Ihrer Domain hinzu.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

>[!TIP]
>
>Der *CNAME-Eintrag* oder der *Datensatz* kann auf dem herrschenden DNS-Server festgelegt werden, um Ihnen Zeit zu sparen.

<!--
![Customer managed certificate steps](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

To verify the domain in use, you are required to add and verify a TXT record.

A text record (also known as a TXT record) is a type of resource record in the Domain Name System (DNS). It lets you associate arbitrary text with a hostname. This text could include human-readable details like server or network information.

Cloud Manager uses a specific TXT record to authorize a domain to be hosted in a CDN service. Create a DNS TXT record in the zone that authorizes Cloud Manager to deploy the CDN service with the custom domain and associate it with the backend service. This association is entirely under your control and authorizes Cloud Manager to serve content from the service to a domain. This authorization may be granted and withdrawn. The TXT record is specific to the domain and the Cloud Manager environment.

#### Requirements {#customer-managed-cert-requirements}

Fulfill these requirements before adding a TXT record.

* Identify your domain host or registrar if you do not know it already.
* Be able to edit the DNS records for your organization's domain, or contact the appropriate person who can.
* First, add a custom domain name as described earlier in this article.

#### Add a TXT record for verification {#customer-managed-cert-verification}

1. In the **Verify domain** dialog box, Cloud Manager displays the name and TXT value to use for verification. Copy this value.

1. Log in to your DNS service provider and find the DNS records section. 

1. Add `aemverification.[yourdomainname]` as the **Name** of the value and add the TXT value exactly as it appears in the **Domain Name** field.

   **TXT record examples**

   | Domain | Name | TXT Value |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Save the TXT record to your domain host.

#### Verify TXT record {#customer-managed-cert-verify}

When you are done, you can verify the result by running the following command.

```shell
dig _aemverification.[yourdomainname] -t txt
```

The expected result should display the TXT value provided on the **Verification** tab of the **Add Domain Name** dialog of the Cloud Manager UI.

For example, if your domain is `example.com`, then run:

```shell
dig TXT _aemverification.example.com -t txt
```


>[!TIP]
>
>There are several [DNS lookup tools](https://www.ultratools.com/tools/dnsLookup) available. Google DoH can be used to look up TXT record entries and identify if the TXT record is missing or erroneous.

-->



<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->


><!-- The TXT entry and the CNAME or A Record can be set simultaneously on the governing DNS server, thus saving time. -->
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->

