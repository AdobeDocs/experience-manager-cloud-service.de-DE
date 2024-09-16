---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: dd696580758e7ab9a5427d47fda4275f9ad7997f
workflow-type: tm+mt
source-wordcount: '1488'
ht-degree: 43%

---


# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.

## Voraussetzungen {#requirements}

Erfüllen Sie die folgenden Anforderungen, bevor Sie einen benutzerdefinierten Domain-Namen in Cloud Manager hinzufügen.

* Sie müssen ein SSL-Domänenzertifikat für die Domäne hinzugefügt haben, die Sie hinzufügen möchten, bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, wie im Dokument [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) beschrieben.
* Sie müssen über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzufügen zu können.
* Verwenden Sie das Fastly CDN.

>[!IMPORTANT]
>
>Selbst wenn Sie ein Nicht-Adobe-CDN verwenden, müssen Sie Ihre Domäne dennoch zu Cloud Manager hinzufügen.

## Hinzufügen benutzerdefinierter Domänennamen {#}

In Cloud Manager können Sie einen benutzerdefinierten Domain-Namen aus zwei Positionen hinzufügen:

* [Auf der Seite „Domain-Einstellungen“](#adding-cdn-settings)
* [Auf der Seite „Umgebungen“](#adding-cdn-environments)

Beim Hinzufügen eines benutzerdefinierten Domain-Namens wird die Domain mit dem spezifischsten der gültigen Zertifikate bereitgestellt. Wenn mehrere Zertifikate dieselbe Domain haben, wird die zuletzt aktualisierte ausgewählt. Adobe empfiehlt, Zertifikate so zu verwalten, dass es keine überlappenden Domains gibt.

Die Schritte für beide in diesem Dokument beschriebenen Methoden basieren auf Fastly. Wenn Sie ein anderes CDN verwenden, konfigurieren Sie die Domain mit dem CDN, das Sie für die Verwendung ausgewählt haben.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Domain-Einstellungen {#adding-cdn-settings}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Wählen Sie im linken Navigationsbereich die Registerkarte **Domäneneinstellungen** aus.

   ![Fenster „Domain-Einstellungen“](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie in der rechten oberen Ecke der Seite **Domäneneinstellungen** auf **Domäne hinzufügen**.

1. Geben Sie im Dialogfeld **Domäne hinzufügen** im Feld **Domänenname** den von Ihnen verwendeten benutzerdefinierten Domänennamen ein.
Verwenden Sie bei der Eingabe Ihrer Domain weder `http://`, noch `https://` oder Leerzeichen.

1. Klicken Sie auf **Erstellen**.

1. Im Dialogfeld **Domäne verifizieren** im Dialogfeld **Welchen Zertifikatstyp beabsichtigen Sie mit dieser Domäne zu verwenden?** eine der folgenden Optionen auswählen:

   | Zertifikatstyp | Beschreibung |
   | --- | --- |
   | Verwaltetes Adobe-Zertifikat | Wählen Sie aus, ob Sie ein DV-Zertifikat (Domain Validation) verwenden möchten. Diese Option eignet sich in den meisten Fällen hervorragend, da sie eine grundlegende Domänenvalidierung ermöglicht. Adobe verwaltet und erneuert das Zertifikat automatisch. |
   | Kundenseitig verwaltetes Zertifikat | Wählen Sie aus, ob Sie ein EV-/OV-Zertifikat verwenden möchten. Diese Option bietet verbesserte Sicherheit mit EV (erweiterte Validierung) oder OV (Organisationsvalidierung). Verwenden Sie diese Option, wenn eine strengere Überprüfung, höhere Vertrauensstufen oder benutzerdefinierte Kontrolle über die Zertifikate erforderlich sind. |

1. Führen Sie im Dialogfeld **Verify domain** je nach ausgewähltem Zertifikatstyp einen der folgenden Schritte aus:

   | Wenn Sie den Zertifikatstyp ausgewählt haben | Beschreibung |
   | --- | ---  |
   | Verwaltetes Adobe-Zertifikat | Führen Sie die [Adobe verwalteten Zertifikatschritte](#abobe-managed-cert-steps) aus, bevor Sie mit dem nächsten Schritt fortfahren. |
   | Kundenseitig verwaltetes Zertifikat | Führen Sie die [vom Kunden verwalteten Zertifikatschritte](#customer-managed-cert-steps) aus, bevor Sie mit dem nächsten Schritt fortfahren. |

1. Klicken Sie auf **Verify**.

1. Sie können jetzt [ein SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

   >[!NOTE]
   >
   >Wenn Sie ein selbstverwaltetes SSL-Zertifikat und einen selbst verwalteten CDN-Anbieter verwenden, können Sie diesen Schritt überspringen und direkt zu [CDN-Konfiguration hinzufügen](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) wechseln, sobald er fertig ist.



### Adobe-verwaltete Zertifikatschritte {#adobe-managed-cert-steps}

Wenn Sie den Zertifikatstyp *Adobe verwaltetes Zertifikat* ausgewählt haben, führen Sie die folgenden Schritte im Dialogfeld **Domäne überprüfen** aus.

![Adobe verwaltete Zertifikatschritte](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

Um die verwendete Domäne zu überprüfen, müssen Sie einen CNAME hinzufügen und überprüfen.

Ein `CNAME` - oder ein Datensatz leitet nach der Bereitstellung den gesamten Internet-Traffic für die Domäne an den Ort weiter, auf den er verweist. Wenn dieser Speicherort nicht für den Traffic vorgesehen ist, kommt es zu einem Ausfall. Wenn er nicht getestet wurde, kann es zu Fehlern in den Inhalten kommen. Aus diesem Grund wird dieser Schritt immer durchgeführt, nachdem der Test abgeschlossen ist und Sie bereit sind, live zu gehen.

Um diese Einstellungen zu konfigurieren, stellen Sie fest, ob ein `CNAME`- oder ein Apex-Eintrag so konfiguriert werden muss, dass Ihr benutzerdefinierter Domänenname auf den Cloud Manager-Domänennamen verweist. Die folgenden Abschnitte dieses Dokuments helfen Ihnen bei der Bestimmung des für Ihre DNS-Konfiguration geeigneten Datensatztyps.

>[!NOTE]
>
>Bei von Adobe verwalteten CDNs sind bei Verwendung von DV-Zertifikaten (Domain Validation) nur Sites mit ACME-Validierung zulässig.

#### Voraussetzungen {#dv-requirements}

Erfüllen Sie diese Anforderungen, bevor Sie Ihre DNS-Einträge konfigurieren.

* Identifizieren Sie Ihren Domain-Host oder Ihre Registrierungsstelle, falls Sie sie noch nicht kennen.
* Sie können die DNS-Einträge für die Domäne Ihres Unternehmens bearbeiten oder sich an die entsprechende Person wenden, die dies kann.
* Sie müssen Ihren konfigurierten, benutzerdefinierten Domain-Namen bereits überprüft haben, wie im Dokument [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) beschrieben.

#### CNAME-Eintrag {#cname-record}

Ein kanonischer Name oder CNAME-Eintrag ist eine Art von DNS-Eintrag, der einen Aliasnamen einem wahren oder kanonischen Domain-Namen zuordnet. CNAME-Datensätze werden normalerweise dazu verwendet, eine Unter-Domain wie `www.example.com` der Domain zuzuordnen, in der der Inhalt dieser Unter-Domain gehostet wird.

Melden Sie sich bei Ihrem DNS-Dienstanbieter an und erstellen Sie einen `CNAME` -Datensatz, um Ihren benutzerdefinierten Domänennamen auf das Ziel zu verweisen, z. B. in der folgenden Tabelle.

| CNAME | Benutzerdefinierter Domänendame zeigt auf Ziel |
| --- | --- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

#### APEX-Eintrag {#apex-record}

Eine Apex-Domain ist eine benutzerdefinierte Domain, die keine Unter-Domain enthält, z. B. `example.com`. Eine Apex-Domäne wird über Ihren DNS-Provider mit einem `A`-, `ALIAS`- oder `ANAME` -Datensatz konfiguriert. Die Apex-Domains müssen auf bestimmte IP-Adressen verweisen.

Fügen Sie die folgenden `A`-Einträge über Ihren Domain-Provider in den DNS-Einstellungen Ihrer Domain hinzu.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`



### Vom Kunden verwaltete Zertifikatschritte {#customer-managed-cert-steps}

Wenn Sie den Zertifikatstyp *Vom Kunden verwaltetes Zertifikat* ausgewählt haben, führen Sie die folgenden Schritte im Dialogfeld **Domäne überprüfen** aus.

![Vom Kunden verwaltete Zertifikatschritte](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

Um die verwendete Domain zu überprüfen, müssen Sie einen TXT-Eintrag hinzufügen und überprüfen.

Ein Texteintrag (auch als TXT-Eintrag bezeichnet) ist ein Typ von Ressourceneintrag im DNS (Domain Name System). Damit können Sie beliebigen Text mit einem Hostnamen verknüpfen. Dieser Text könnte für Menschen lesbare Details wie Server- oder Netzwerkinformationen enthalten.

Cloud Manager nutzt einen spezifischen TXT-Eintrag, um das Hosting einer Domain in einem CDN-Service zu autorisieren. Erstellen Sie einen DNS-TXT-Eintrag in der Zone, die Cloud Manager berechtigt, den CDN-Dienst mit der benutzerdefinierten Domäne bereitzustellen und ihn mit dem Backend-Dienst zu verknüpfen. Diese Zuordnung steht vollständig unter Ihrer Kontrolle und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Service für eine Domain bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden. Der TXT-Eintrag ist spezifisch für die Domain und die Cloud Manager-Umgebung.

## Voraussetzungen {#requirements-customer-cert}

Erfüllen Sie diese Anforderungen, bevor Sie einen TXT-Eintrag hinzufügen.

* Identifizieren Sie Ihren Domain-Host oder Ihre Registrierungsstelle, falls Sie sie noch nicht kennen.
* Sie können die DNS-Einträge für die Domäne Ihres Unternehmens bearbeiten oder sich an die entsprechende Person wenden, die dies kann.
* Fügen Sie zunächst einen benutzerdefinierten Domänennamen hinzu, wie zuvor in diesem Artikel beschrieben.

## Hinzufügen eines TXT-Eintrags zur Überprüfung {#verification}

1. Im Dialogfeld **Verify domain** zeigt Cloud Manager den Namen und den TXT-Wert an, der zur Überprüfung verwendet werden soll. Kopieren Sie diesen Wert.

1. Melden Sie sich bei Ihrem DNS-Dienstanbieter an und suchen Sie den Abschnitt DNS-Einträge .

1. Fügen Sie `aemverification.[yourdomainname]` als **Name** des Werts hinzu und fügen Sie den TXT-Wert genau so hinzu, wie er im Feld **Domänenname** angezeigt wird.

   **TXT-Datensatzbeispiele**

   | Domain | Name | TXT-Wert |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Kopieren Sie den gesamten in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser Wert ist spezifisch für die Domäne und die Umgebung. Beispiel:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Kopieren Sie den gesamten in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser Wert ist spezifisch für die Domäne und die Umgebung. Beispiel:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Speichern Sie den TXT-Eintrag auf Ihrem Domain-Host.

## TXT-Eintrag überprüfen {#verify}

Wenn Sie fertig sind, können Sie das Ergebnis überprüfen, indem Sie den folgenden Befehl ausführen.

```shell
dig _aemverification.[yourdomainname] -t txt
```

Das erwartete Ergebnis sollte den TXT-Wert anzeigen, der in der Cloud Manager-Benutzeroberfläche im Dialogfeld **Domain-Namen hinzufügen** auf der Registerkarte **Überprüfung** angegeben ist.

Wenn Ihre Domain beispielsweise `example.com` lautet, führen Sie Folgendes aus:

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Es sind mehrere [DNS-Suchwerkzeuge](https://www.ultratools.com/tools/dnsLookup) verfügbar. Google DoH kann verwendet werden, um TXT-Eintragungen nachzuschlagen und zu ermitteln, ob der TXT-Eintrag fehlt oder fehlerhaft ist.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle &quot;Domäneneinstellungen&quot;angezeigt wird. Weitere Informationen finden Sie unter [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) .

<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->

>[!TIP]
>
>Der TXT-Eintrag und der CNAME oder A Record können gleichzeitig auf dem herrschenden DNS-Server gesetzt werden, wodurch Zeit eingespart wird.
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite „Umgebungen“ {#adding-cdn-environments}

Die Schritte zum Hinzufügen eines benutzerdefinierten Domain-Namens von der Seite **Umgebungen** aus sind dieselben wie beim [Hinzufügen eines benutzerdefinierten Domain-Namens von der Seite „Domain-Einstellungen“ aus](#adding-cdn-settings), der Einstiegspunkt ist jedoch ein anderer. Führen Sie die folgenden Schritte von der Seite **Umgebungen** aus, um einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zur Detailseite **Umgebungsdetails** für die Umgebung, die von Interesse ist.

   ![Eingabe des Domain-Namens auf der Seite „Umgebungsdetails“](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Tabelle **Domain-Namen**, um den benutzerdefinierten Domain-Namen zu übermitteln.

   1. Geben Sie den benutzerdefinierten Domain-Namen ein.
   1. Wählen Sie in der Dropdown-Liste das mit diesem Namen verknüpfte SSL-Zertifikat aus.
   1. Klicken Sie auf **+Hinzufügen**.

   ![Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Mittels des Dialogfelds **Domain-Namen hinzufügen** wird die Registerkarte **Domain-Name** geöffnet. Fahren Sie so fort wie bei [Hinzufügen eines benutzerdefinierten Domänennamens von der Seite &quot;Domäneneinstellungen&quot;](#adding-cdn-settings). —>
