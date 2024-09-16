---
title: Einführung in SSL-Zertifikate
description: Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation von SSL-Zertifikaten bereitstellt.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 83%

---


# Einführung in SSL-Zertifikate{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Verwalten von SSL-Zertifikaten"
>abstract="Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten zur Verfügung stellt, um Ihre Website für Ihre Benutzerinnen und Benutzer zu sichern. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kundinnen bzw. Kunden gehören und von unabhängigen Zertifizierungsstellen bezogen werden."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats"
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Überprüfen des Status eines SSL-Zertifikats"


Cloud Manager bietet Self-Service-Tools zum Installieren und Verwalten von SSL(Secure Socket Layer)-Zertifikaten, die die Site für Benutzende sicher machen. Die beiden folgenden Anwendungsfälle werden unterstützt:

<!-- CQDOC-21758, #1 -->

| | Anwendungsfall | Beschreibung |
| --- | --- | --- |
| 1 | **Von Adobe verwaltetes Zertifkat (DV)** | Mit Cloud Manager können Benutzende ein DV(Domain Validation)-Zertifikat konfigurieren, das von Adobe zur schnellen Einrichtung von Domains bereitgestellt wird. DV-Zertifikate stehen für die einfachste SSL-Zertifizierungsstufe und werden häufig zu Testzwecken oder zum Schützen von Websites mit Grundverschlüsselung verwendet. DV-Zertifikate sind sowohl in [Produktionsprogrammen als auch in Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) verfügbar. Nachdem das DV-Zertifikat erstellt wurde, erneuert Adobe es automatisch alle drei Monate, es sei denn, es wird gelöscht. |
| 2 | **Kundenseitig verwaltetes Zertifikat (OV/EV)** | Cloud Manager verwendet einen Plattform-TLS(Transport Layer Security)-Dienst, um kundeneigene SSL-Zertifikate und private Schlüssel von Zertifizierungsstellen von Drittanbietern zu verwalten, z. B. *Let’s Encrypt*. |

>[!NOTE]
>
>Kundinnen und Kunden dürfen keine DV(Domain Validation)-Zertifikate hochladen.


## Einführung in SSL-Zertifikate {#certificates}

Unternehmen und Organisationen verwenden SSL-Zertifikate, um ihre Websites sicher zu machen, damit ihre Kundinnen und Kunden ihnen vertrauen können. Um das SSL-Protokoll verwenden zu können, muss ein Webserver ein SSL-Zertifikat verwenden.

Wenn eine Organisation oder ein Unternehmen ein Zertifikat von einer Zertifizierungsstelle (CA) anfordert, führt die Zertifizierungsstelle einen Überprüfungsprozess durch. Dieser Prozess kann von der Überprüfung der Namenskontrolle der Domains bis zur Erfassung von Unternehmensregistrierungsdokumenten und Abonnentenvereinbarungen reichen. Sobald die Informationen eines Unternehmens oder einer Organisation verifiziert wurden, signiert die Zertifizierungsstelle den entsprechenden öffentlichen Schlüssel mithilfe des privaten Schlüssels der Zertifizierungsstelle. Da alle wichtigen Zertifizierungsstellen über Stammzertifikate in Webbrowsern verfügen, wird das Zertifikat der Organisation oder des Unternehmens über eine *Vertrauenskette* verknüpft und vom Webbrowser als vertrauenswürdiges Zertifikat erkannt.

>[!IMPORTANT]
>
>Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei einer Zertifizierungsstelle, einer vertrauenswürdigen Drittorganisation, eingeholt werden. Zu den bekannten Zertifizierungsstellen gehören *DigiCert*, *Let&#39;s Encrypt*, *GlobalSign*, *Entrust* und *Verisign*.

Cloud Manager unterstützt die folgenden Optionen für die Verwendung von SSL-Zertifikaten durch Kundinnen und Kunden.

* Ein SSL-Zertifikat kann von mehreren Umgebungen verwendet werden. Es kann also einmal hinzugefügt, aber mehrmals verwendet werden.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält normalerweise mehrere Domains.
* Der Plattform-TLS-Service leitet Anfragen basierend auf dem zum Beenden verwendeten SSL-Zertifikat und dem CDN-Service, der diese Domain hostet, an den CDN-Service des Kunden weiter.
* AEM as a Cloud Service akzeptiert Platzhalter-SSL-Zertifikate für eine Domain.

AEM as a Cloud Service unterstützt nur sichere `https`-Sites. Kunden mit mehreren benutzerdefinierten Domänen möchten kein Zertifikat jedes Mal hochladen, wenn sie eine Domäne hinzufügen. Daher profitieren solche Kundinnen und Kunden von einem Zertifikat mit mehreren Domains.

## SSL-Zertifikatanforderungen {#requirements}

* AEM as a Cloud Service akzeptiert Zertifikate, die den Richtlinien für OV (Organization Validation), EV (Extended Validation) oder DV (Domain Validation) entsprechen. <!-- CQDOC-21758, #2 -->
* Es muss sich immer um ein X.509-TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle mit einem passenden privaten 2048-Bit-RSA-Schlüssel handeln.
* Selbstsignierte Zertifikate werden nicht akzeptiert.

OV- und EV-Zertifikate bieten CA-validierte Informationen. Mithilfe dieser Informationen können Benutzende bewerten, ob die Eigentümerin bzw. der Eigentümer der Website, die Absenderin bzw. der Absender der E-Mail oder die digitale Unterzeichnerin bzw. der digitale Unterzeichner von Code- oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate erlauben keine solche Prüfung der Eigentümerschaft.

### Vom Kunden verwaltetes SSL-Zertifikatformat {#certificate-format}

<!-- CQDOC-21758, #3 -->

SSL-Dateien müssen im PEM-Format vorliegen, damit sie in Cloud Manager installiert werden können. Häufige Dateierweiterungen des PEM-Formats umfassen `.pem,`, `crt`, `.cer` und `.cert`.

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

## Begrenzung der Anzahl installierter SSL-Zertifikate {#limitations}

Cloud Manager ermöglicht zu jedem Zeitpunkt maximal 50 installierte SSL-Zertifikate. Diese Zertifikate können mit einer oder mehreren Umgebungen in Ihrem Programm verknüpft sein und auch abgelaufene Zertifikate enthalten.

Wenn Sie die Grenze erreicht haben, überprüfen Sie Ihre Zertifikate und erwägen Sie, abgelaufene Zertifikate zu löschen. Alternativ können Sie mehrere Domänen im selben Zertifikat gruppieren, da ein Zertifikat mehrere Domänen (bis zu 100 SANs) abdecken kann.

## Weitere Informationen {#learn-more}

Benutzende mit den erforderlichen Berechtigungen können Cloud Manager verwenden, um SSL-Zertifikate für ein Programm zu verwalten. Weitere Details zur Verwendung dieser Funktionen finden Sie in den folgenden Dokumenten.

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

