---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Erfahren Sie, wie Sie in Cloud Manager mithilfe der Domain-Einstellungen einen benutzerdefinierten Domain-Namen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b9fb178760b74cb0e101506b6a9ff5ae30c18490
workflow-type: ht
source-wordcount: '1509'
ht-degree: 100%

---


# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

Erfahren Sie, wie Sie in Cloud Manager mithilfe der **Domain-Einstellungen** einen benutzerdefinierten Domain-Namen hinzufügen.

## Voraussetzungen {#requirements}

Erfüllen Sie die folgenden Anforderungen, bevor Sie einen benutzerdefinierten Domain-Namen in Cloud Manager hinzufügen.

* Bevor Sie einen benutzerdefinierten Domain-Namen hinzufügen, müssen Sie ein SSL-Domain-Zertifikat für die gewünschte Domain hinzugefügt haben, wie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) beschrieben.
* Sie müssen über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzufügen zu können.
* Sie müssen Fastly oder ein anderes CDN (Content Delivery Network) verwenden.

>[!IMPORTANT]
>
>Selbst wenn Sie ein Adobe-fremdes CDN verwenden, müssen Sie Ihre Domain dennoch zu Cloud Manager hinzufügen.

## Wo Sie benutzerdefinierte Domain-Namen hinzufügen können {#where-to-add-cdn}

In Cloud Manager können Sie einen benutzerdefinierten Domain-Namen über die beiden folgenden Seiten hinzufügen:

* [Seite „Domain-Einstellungen“](#adding-cdn-settings)
* [Seite „Umgebungen“](#adding-cdn-environments)

Beim Hinzufügen eines benutzerdefinierten Domain-Namens wird die Domain mit dem spezifischsten der gültigen Zertifikate bereitgestellt. Wenn mehrere Zertifikate dieselbe Domain haben, wird die zuletzt aktualisierte ausgewählt. Adobe empfiehlt, Zertifikate so zu verwalten, dass es keine überlappenden Domains gibt.

Die Schritte, die in diesem Dokument für beide Methoden beschrieben werden, basieren auf Fastly. Wenn Sie ein anderes CDN (Content Delivery Network) verwenden, konfigurieren Sie die Domain mit dem entsprechenden CDN.

## Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn-settings}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Wählen Sie im Seitenmenü unter **Services** die Option ![Einstellungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) **Domain-Einstellungen** aus.

   ![Fenster „Domain-Einstellungen“](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie oben rechts auf der Seite **Domain-Einstellungen** auf **Domain hinzufügen**.

1. Geben Sie im Dialogfeld **Domain hinzufügen** in das Feld **Domain-Name** den von Ihnen verwendeten benutzerdefinierten Domain-Namen ein.
Verwenden Sie bei der Eingabe Ihrer Domain weder `http://` noch `https://` oder Leerzeichen.

1. Klicken Sie auf **Erstellen**.

1. Wählen Sie im Dialogfeld **Domain verifizieren** aus der Dropdown-Liste **Welchen Zertifikatstyp möchten Sie mit dieser Domain verwenden?** eine der folgenden Optionen aus:

   | Option für den Zertifikatstyp | Beschreibung |
   | --- | --- |
   | Verwaltetes Adobe-Zertifikat | Wählen Sie diesen Zertifikatstyp aus, wenn Sie ein DV(Domain Validation)-Zertifikat verwenden möchten. Diese Option eignet sich in den meisten Fällen hervorragend, da sie eine grundlegende Domain-Validierung ermöglicht. Adobe verwaltet und erneuert das Zertifikat automatisch. |
   | Kundenseitig verwaltetes Zertifikat | Wählen Sie diesen Zertifikatstyp aus, wenn Sie ein EV/OV-Zertifikat verwenden möchten. Diese Option bietet verbesserte Sicherheit mit EV (Extended Validation) oder OV (Organization Validation). Verwenden Sie sie, wenn eine strengere Überprüfung, eine höhere Vertrauensebene oder eine benutzerdefinierte Kontrolle über die Zertifikate erforderlich sind. |

1. Führen Sie im Dialogfeld **Domain verifizieren** je nach ausgewähltem Zertifikatstyp einen der folgenden Schritte aus:

   | Ausgewählter Zertifikatstyp | Beschreibung |
   | --- | ---  |
   | Verwaltetes Adobe-Zertifikat | Führen Sie die [Schritte für von Adobe verwaltete Zertifikate](#adobe-managed-cert-steps) aus, bevor Sie mit dem nächsten Schritt fortfahren. |
   | Kundenseitig verwaltetes Zertifikat | Führen Sie die [Schritte für kundenseitig verwaltete Zertifikate](#customer-managed-cert-steps) aus, bevor Sie mit dem nächsten Schritt fortfahren. |

1. Klicken Sie auf **Überprüfen**.

1. Sie können jetzt [ein SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

   >[!NOTE]
   >
   >Wenn Sie ein kundenseitig verwaltetes SSL-Zertifikat und einen kundenseitig verwalteten CDN-Anbieter verwenden, müssen Sie kein SSL-Zertifikat hinzufügen und können direkt zu [CDN-Konfiguration hinzufügen](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) gehen, sobald Sie bereit sind.


### Schritte bei verwalteten Adobe-Zertifikaten {#adobe-managed-cert-steps}

Wenn Sie den Zertifikatstyp *Verwaltetes Adobe-Zertifikat* ausgewählt haben, führen Sie die folgenden Schritte im Dialogfeld **Domain überprüfen** aus.

![Schritte bei verwalteten Adobe-Zertifikaten](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

Um die verwendete Domain zu überprüfen, müssen Sie einen CNAME hinzufügen und überprüfen.

Ein `CNAME`- oder A-Eintrag leitet, sobald er bereitgestellt ist, den gesamten Internet-Traffic für die Domain zu dem Punkt, auf den er verweist. Wenn dieser Speicherort nicht für den Traffic vorgesehen ist, kommt es zu einem Ausfall. Wenn er nicht getestet wurde, kann es zu Fehlern in den Inhalten kommen. Aus diesem Grund wird dieser Schritt immer durchgeführt, nachdem der Test abgeschlossen ist und Sie bereit sind, live zu gehen.

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

| CNAME | Benutzerdefinierter Domain-Name, der auf das Ziel verweist. |
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


### Schritte bei kundenseitig verwalteten Zertifikaten {#customer-managed-cert-steps}

Wenn Sie den Zertifikatstyp *Kundenseitig verwaltetes Zertifikat* ausgewählt haben, führen Sie die folgenden Schritte im Dialogfeld **Domain überprüfen** aus.

![Schritte bei kundenseitig verwalteten Zertifikaten](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

Um die verwendete Domain zu überprüfen, müssen Sie einen TXT-Eintrag hinzufügen und überprüfen.

Ein Texteintrag (auch als TXT-Eintrag bezeichnet) ist ein Typ von Ressourceneintrag im DNS (Domain Name System). Damit können Sie einen beliebigen Text mit einem Host-Namen verknüpfen. Dieser Text könnte für Menschen lesbare Details wie Server- oder Netzwerkinformationen enthalten.

Cloud Manager nutzt einen spezifischen TXT-Eintrag, um das Hosting einer Domain in einem CDN-Service zu autorisieren. Erstellen Sie einen DNS-TXT-Eintrag in der Zone, die Cloud Manager dazu autorisiert, den CDN-Service mit der benutzerdefinierten Domain bereitzustellen, und ordnen Sie ihn dem Backend-Service zu. Diese Zuordnung steht vollständig unter Ihrer Kontrolle und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Service für eine Domain bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden. Der TXT-Eintrag ist spezifisch für die Domain und die Cloud Manager-Umgebung.

#### Voraussetzungen {#customer-managed-cert-requirements}

Sie müssen die folgenden Anforderungen erfüllen, bevor Sie einen TXT-Eintrag hinzufügen.

* Identifizieren Sie Ihren Domain-Host oder Ihre Registrierungsstelle, falls Sie sie noch nicht kennen.
* Sie müssen in der Lage sein, die DNS-Einträge für die Domain Ihres Unternehmens zu ändern, oder sich andernfalls an eine entsprechende Person wenden, die dies kann.
* Fügen Sie zunächst einen benutzerdefinierten Domain-Namen hinzu, wie zuvor in diesem Artikel beschrieben.

#### Hinzufügen eines TXT-Eintrags zur Überprüfung {#customer-managed-cert-verification}

1. In Cloud Manager werden im Dialogfeld **Domain überprüfen** der Name und der TXT-Wert angezeigt, die zur Überprüfung verwendet werden sollen. Kopieren Sie diesen Wert.

1. Melden Sie sich bei Ihrem DNS-Dienstleister an und gehen Sie zum Abschnitt mit den DNS-Einträgen.

1. Fügen Sie `aemverification.[yourdomainname]` als den **Namen** des Werts hinzu und fügen Sie den TXT-Wert genau so hinzu, wie er im Dialogfeld **Domain-Namen** angezeigt wird.

   **Beispiele für TXT-Einträge**

   | Domain | Name | TXT-Wert |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Speichern Sie den TXT-Eintrag auf Ihrem Domain-Host.

#### Überprüfen des TXT-Eintrags {#customer-managed-cert-verify}

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
>Es sind mehrere [DNS-Suchwerkzeuge](https://www.ultratools.com/tools/dnsLookup) verfügbar. Google DoH kann verwendet werden, um TXT-Einträge zu suchen und zu erkennen, ob der TXT-Eintrag fehlt oder fehlerhaft ist.

>[!NOTE]
>
>Die DNS-Überprüfung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Weitere Informationen finden Sie unter [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->

>[!TIP]
>
>Der TXT-Eintrag und der CNAME- oder A-Eintrag können zeitsparend gleichzeitig auf dem entsprechenden DNS-Server eingerichtet werden.
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite „Umgebungen“ {#adding-cdn-environments}

<!-- I DON'T SEE THIS ABILITY ANYMORE IN THE UI -->

Die Schritte zum Hinzufügen eines benutzerdefinierten Domain-Namens von der Seite **Umgebungen** aus sind dieselben wie beim [Hinzufügen eines benutzerdefinierten Domain-Namens von der Seite „Domain-Einstellungen“ aus](#adding-cdn-settings), der Einstiegspunkt ist jedoch ein anderer. Führen Sie die folgenden Schritte von der Seite **Umgebungen** aus, um einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zur Seite mit den **Umgebungsdetails** für die gewünschte Umgebung.

   ![Eingabe des Domain-Namens auf der Seite „Umgebungsdetails“](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Tabelle **Domain-Namen**, um den benutzerdefinierten Domain-Namen zu übermitteln.

   1. Geben Sie den benutzerdefinierten Domain-Namen ein.
   1. Wählen Sie in der Dropdown-Liste das mit diesem Namen verknüpfte SSL-Zertifikat aus.
   1. Klicken Sie auf ![Hinzufügen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **Hinzufügen**.

   ![Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Mittels des Dialogfelds **Domain-Namen hinzufügen** wird die Registerkarte **Domain-Name** geöffnet. Fahren Sie so fort wie bei [Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite „Domain-Einstellungen“](#adding-cdn-settings).
