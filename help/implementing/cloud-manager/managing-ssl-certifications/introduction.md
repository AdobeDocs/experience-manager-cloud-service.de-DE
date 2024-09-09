---
title: Einführung – Verwalten von SSL-Zertifikaten
description: Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation von SSL-Zertifikaten bereitstellt.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: a9bcbae1317d95e3710a19a79115f1437b418e41
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 42%

---


# Einführung – Verwalten von SSL-Zertifikaten{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL-Zertifikate verwalten"
>abstract="Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten zur Verfügung stellt, um Ihre Website für Ihre Benutzerinnen und Benutzer zu sichern. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kundinnen bzw. Kunden gehören und von unabhängigen Zertifizierungsstellen bezogen werden."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Überprüfen des Status eines SSL-Zertifikats"


Cloud Manager bietet Self-Service-Tools zum Installieren und Verwalten von SSL-Zertifikaten (Secure Socket Layer), die die Site-Sicherheit Ihrer Benutzer gewährleisten. Die folgenden beiden Anwendungsfälle werden unterstützt:

<!-- CQDOC-21758, #1 -->

| | Anwendungsfall | Beschreibung |
| --- | --- | --- |
| 1 | **Adobe verwaltetes Zertifikat (DV)** | Mit Cloud Manager können Benutzer ein DV-Zertifikat (Domain Validation) konfigurieren, das von Adobe zur schnellen Einrichtung von Domänen stammt. DV-Zertifikate sind die grundlegendsten SSL-Zertifizierungsstufen und werden häufig zu Testzwecken oder zum Schützen von Websites mit grundlegender Verschlüsselung verwendet. DV-Zertifikate sind sowohl in [Produktions- als auch in Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) verfügbar. |
| 2 | **Vom Kunden verwaltetes Zertifikat (OV/EV)** | Cloud Manager verwendet einen Platform-TLS-Dienst (Transport Layer Security), um kundeneigene SSL-Zertifikate und private Schlüssel von Zertifizierungsstellen von Drittanbietern zu verwalten, z. B. *Let&#39;s Encrypt*. |

>[!NOTE]
>
>Kunden dürfen keine DV-Zertifikate (Domain Validation) hochladen.


## Einführung in Zertifikate {#certificates}

Unternehmen und Organisationen verwenden SSL-Zertifikate, um ihre Websites zu schützen und ihren Kunden das Vertrauen in sie zu geben. Um das SSL-Protokoll verwenden zu können, muss ein Webserver ein SSL-Zertifikat verwenden.

Wenn eine Organisation oder ein Unternehmen ein Zertifikat von einer Zertifizierungsstelle (Zertifizierungsstelle) anfordert, führt die Zertifizierungsstelle einen Überprüfungsprozess durch. Dieser Prozess kann von der Verifizierung der Domain-Namenskontrolle über die Erfassung von Firmenregisterdokumenten bis hin zu Abonnentenvereinbarungen reichen. Nachdem die Informationen eines Unternehmens überprüft wurden, signiert die Zertifizierungsstelle seinen öffentlichen Schlüssel mithilfe des privaten Schlüssels der Zertifizierungsstelle. Da alle wichtigen Zertifikatbehörden Stammzertifikate in Webbrowsern haben, wird das Zertifikat der Entität über eine *Vertrauenskette* verknüpft und vom Webbrowser als vertrauenswürdiges Zertifikat erkannt.

>[!IMPORTANT]
>
>Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese Informationen müssen bei einer Zertifizierungsstelle, einer vertrauenswürdigen Drittorganisation, eingeholt werden. Zu den bekannten Zertifikatbehörden gehören *DigiCert*, *Let&#39;s Encrypt*, *GlobalSign*, *Entrust* und *Verisign*.

## Cloud Manager-SSL-Verwaltungsfunktionen {#features}

Cloud Manager unterstützt die folgenden Optionen für die Verwendung von SSL-Zertifikaten durch Kunden.

* Mehrere Umgebungen können ein SSL-Zertifikat verwenden. Das heißt, sie kann einmal hinzugefügt, aber mehrmals verwendet werden.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält normalerweise mehrere Domains.
* Der Plattform-TLS-Service leitet Anfragen basierend auf dem zum Beenden verwendeten SSL-Zertifikat und dem CDN-Service, der diese Domain hostet, an den CDN-Service des Kunden weiter.
* AEM as a Cloud Service akzeptiert Platzhalter-SSL-Zertifikate für eine Domain.

## Empfehlungen {#recommendations}

AEM as a Cloud Service unterstützt nur sichere `https`-Sites.

* Kunden mit mehreren benutzerdefinierten Domänen möchten kein Zertifikat jedes Mal hochladen, wenn sie eine Domäne hinzufügen.
* Daher profitieren solche Kundinnen und Kunden von einem Zertifikat mit mehreren Domains.

## Zertifikatsanforderungen {#requirements}

* AEM as a Cloud Service akzeptiert Zertifikate, die der OV- (Organisationsvalidierung), der EV- (erweiterte Validierung) oder der DV-Richtlinie (Domänenvalidierung) entsprechen. <!-- CQDOC-21758, #2 -->
* Jedes Zertifikat muss ein X.509-TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel sein.
* Selbstsignierte Zertifikate werden nicht akzeptiert.

OV- und EV-Zertifikate bieten CA-validierte Informationen. Mithilfe dieser Informationen können Benutzer bewerten, ob der Website-Eigentümer, der E-Mail-Absender oder der digitale Unterzeichner von Code- oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate erlauben keine solche Eigentumsprüfung.

### Vom Kunden verwaltetes Zertifikatformat {#certificate-format}

<!-- CQDOC-21758, #3 -->

SSL-Dateien müssen im PEM-Format vorliegen, damit sie in Cloud Manager installiert werden können. Die gängigen Dateierweiterungen des PEM-Formats umfassen `.pem,`. `crt`, `.cer` und `.cert`.

Folgende `openssl`-Befehle können zum Konvertieren von Nicht-PEM-Zertifikaten verwendet werden.

* Konvertieren von PFX in PEM

  ```shell
  openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes
  ```

* Konvertieren von P7B in PEM

  ```shell
  openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer
  ```

* Konvertieren von DER in PEM

  ```shell
  openssl x509 -inform der -in certificate.cer -out certificate.pem
  ```

## Einschränkungen {#limitations}

Cloud Manager ermöglicht jederzeit maximal 50 installierte SSL-Zertifikate. Diese Zertifikate können mit einer oder mehreren Umgebungen in Ihrem Programm verknüpft werden und auch abgelaufene Zertifikate enthalten.

Wenn Sie den Grenzwert erreicht haben, überprüfen Sie Ihre Zertifikate und erwägen Sie Folgendes:

* Löschen abgelaufener Zertifikate.
* Gruppieren mehrerer Domains im selben Zertifikat, da ein Zertifikat mehrere Domains (bis zu 100 SANs) abdecken kann.

## Weitere Informationen {#learn-more}

Ein Benutzer mit den erforderlichen Berechtigungen kann Cloud Manager verwenden, um SSL-Zertifikate für ein Programm zu verwalten. Weitere Details zur Verwendung dieser Funktionen finden Sie in den folgenden Dokumenten.

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

