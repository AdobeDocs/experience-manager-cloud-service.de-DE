---
title: Einführung in SSL-Zertifikate
description: Erfahren Sie mehr über die Self-Service-Tools, die Cloud Manager Ihnen zur Installation und Verwaltung von SSL-Zertifikaten bereitstellt.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: fa99656e0dd02bb97965e8629d5fa657fbae9424
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 100%

---


# Einführung in SSL-Zertifikate{#introduction}

Erfahren Sie mehr über die Self-Service-Tools, die Cloud Manager Ihnen zur Installation und Verwaltung von SSL(Secure Socket Layer)-Zertifikaten bereitstellt.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Verwalten von SSL-Zertifikaten"
>abstract="Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten zur Verfügung stellt, um Ihre Website für Ihre Benutzerinnen und Benutzer zu sichern. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kundinnen bzw. Kunden gehören und von unabhängigen Zertifizierungsstellen bezogen werden."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats"
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Überprüfen des Status eines SSL-Zertifikats"

## Was sind SSL-Zertifikate? {#overview}

Unternehmen und Organisationen verwenden SSL(Secure Socket Layer)-Zertifikate, um ihre Websites sicher zu machen, damit ihre Kundinnen und Kunden ihnen vertrauen können. Um das SSL-Protokoll verwenden zu können, erfordert ein Webserver ein SSL-Zertifikat.

Wenn eine Organisation oder ein Unternehmen ein Zertifikat von einer Zertifizierungsstelle (ZS) anfordert, führt die Zertifizierungsstelle einen Überprüfungsprozess durch. Dieser Prozess kann von der Überprüfung der Namenskontrolle der Domains bis zur Erfassung von Unternehmensregistrierungsdokumenten und Abonnentenvereinbarungen reichen. Sobald die Informationen eines Unternehmens oder einer Organisation verifiziert wurden, signiert die Zertifizierungsstelle den entsprechenden öffentlichen Schlüssel mithilfe des privaten Schlüssels der Zertifizierungsstelle. Da alle wichtigen Zertifizierungsstellen über Stammzertifikate in Webbrowsern verfügen, wird das Zertifikat der Organisation oder des Unternehmens über eine *Vertrauenskette* verknüpft und vom Webbrowser als vertrauenswürdiges Zertifikat erkannt.

>[!IMPORTANT]
>
>Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei einer Zertifizierungsstelle, einer vertrauenswürdigen Drittorganisation, eingeholt werden. Zu den bekannten Zertifizierungsstellen gehören *DigiCert*, *Let&#39;s Encrypt*, *GlobalSign*, *Entrust* und *Verisign*.

## Verwalten von Zertifikaten mit Cloud Manager {#cloud-manager}

Cloud Manager bietet Self-Service-Tools zum Installieren und Verwalten von SSL(Secure Socket Layer)-Zertifikaten, die die Site für Benutzende sicher machen. Cloud Manager unterstützt zwei Modelle für die Verwaltung Ihrer Zertifikate.

| | Modell | Beschreibung |
| --- | --- | --- |
| A | **[Von Adobe verwaltetes SSL-Zertifkat (DV)](#adobe-managed)** | Mit Cloud Manager können Benutzende DV(Domain Validation)-Zertifikate konfigurieren, die von Adobe zur schnellen Einrichtung von Domains bereitgestellt werden. |
| B | **[Kundenseitig verwaltetes SSL-Zertifikat (OV/EV)](#customer-managed)** | Cloud Manager verwendet einen Plattform-TLS(Transport Layer Security)-Dienst, damit Sie Ihre eigenen OV- und EV-SSL-Zertifikate und private Schlüssel von Zertifizierungsstellen von Drittanbietern, z. B. *Let’s Encrypt*, verwalten können. |

Beide Modelle bieten die folgenden allgemeinen Funktionen für die Verwaltung Ihrer Zertifikate:

* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Der Plattform-TLS-Service leitet Anfragen basierend auf dem zum Beenden verwendeten SSL-Zertifikat und dem CDN-Service, der diese Domain hostet, an den CDN-Service der Kundin bzw. des Kunden weiter.

>[!IMPORTANT]
>
>[Um eine benutzerdefinierte Domain hinzuzufügen und mit einer Umgebung zu verknüpfen](/help/implementing/cloud-manager/custom-domain-names/introduction.md), müssen Sie über ein gültiges SSL-Zertifikat verfügen, das die Domain abdeckt.

### Von Adobe verwaltete SSL-Zertifikate (DV) {#adobe-managed}

DV-Zertifikate stehen für die einfachste SSL-Zertifizierungsstufe und werden häufig zu Testzwecken oder zum Schützen von Websites mit einer einfachen Verschlüsselung verwendet. DV-Zertifikate sind in [Produktions- und Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) verfügbar.

Nachdem das DV-Zertifikat erstellt wurde, erneuert Adobe es automatisch alle drei Monate, es sei denn, es wird gelöscht.

### Kundenseitig verwaltete SSL-Zertifikate (OV/EV) {#customer-managed}

OV- und EV-Zertifikate bieten CA-validierte Informationen. Mithilfe dieser Informationen können Benutzende bewerten, ob die Eigentümerin bzw. der Eigentümer der Website, die Absenderin bzw. der Absender der E-Mail oder die digitale Unterzeichnerin bzw. der digitale Unterzeichner von Code- oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate erlauben keine solche Prüfung der Eigentümerschaft.

OV und EV bieten diese Funktionen zusätzlich über DV-Zertifikate in Cloud Manager an.

* Ein OV/EV-Zertifikat kann von mehreren Umgebungen verwendet werden. Es wird also nur einmal hinzugefügt, kann aber mehrmals verwendet werden.
* Jedes OV/EV-Zertifikat enthält normalerweise mehrere Domains.
* Cloud Manager akzeptiert Platzhalter-OV/EV-Zertifikate für eine Domain.

>[!TIP]
>
>Wenn Sie mehrere benutzerdefinierte Domains haben, möchten Sie vielleicht nicht jedes Mal, wenn Sie eine neue Domain hinzufügen, ein Zertifikat hochladen. In diesem Fall können Sie von einem einzigen Zertifikat profitieren, das mehrere Domains abdeckt.

>[!NOTE]
>
>Wenn zwei Zertifikate für dieselbe Domain installiert sind, wird das genauere angewendet.
>
>Wenn Ihre Domain beispielsweise `dev.adobe.com` ist und Sie ein Zertifikat für `*.adobe.com` und ein weiteres für `dev.adobe.com` haben, wird das spezifischere Zertifikat (`dev.adobe.com`) verwendet.

#### Anforderungen für kundenseitig verwaltete OV/EV-SSL-Zertifikate {#requirements}

Wenn Sie sich dafür entscheiden, Ihr eigenes EV/OV-SSL-Zertifikat hinzuzufügen, muss es die folgenden Anforderungen erfüllen:

* AEM as a Cloud Service akzeptiert nur Zertifikate, welche die Richtlinien der OV (Organisationsvalidierung) oder EV (erweiterte Validierung) erfüllen.
   * Cloud Manager unterstützt nicht das Hinzufügen eigener DV(Domain Validation)-Zertifikate.
* Es muss sich immer um ein X.509-TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle mit einem passenden privaten 2048-Bit-RSA-Schlüssel handeln.
* Selbstsignierte Zertifikate werden nicht akzeptiert.

#### Format für kundenseitig verwaltete Zertifikate {#certificate-format}

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

>[!TIP]
>
>Adobe empfiehlt, die Integrität Ihres Zertifikats lokal mit einem Tool wie `openssl verify -untrusted intermediate.pem certificate.pem` zu überprüfen, bevor Sie versuchen, es mit Cloud Manager zu installieren.

## Begrenzung der Anzahl installierter SSL-Zertifikate {#limitations}

Cloud Manager ermöglicht zu jedem Zeitpunkt maximal 50 installierte SSL-Zertifikate. Diese Zertifikate können mit einer oder mehreren Umgebungen in Ihrem Programm verknüpft sein und auch abgelaufene Zertifikate enthalten.

Wenn Sie den Grenzwert erreicht haben, überprüfen Sie Ihre Zertifikate und löschen Sie ggf. abgelaufene Zertifikate. Oder gruppieren Sie mehrere Domains im selben Zertifikat, da ein Zertifikat mehrere Domains (bis zu 100 SANs) abdecken kann.

## Weitere Informationen {#learn-more}

Benutzende mit den erforderlichen Berechtigungen können Cloud Manager verwenden, um SSL-Zertifikate für ein Programm zu verwalten. Weitere Details zur Verwendung dieser Funktionen finden Sie in den folgenden Dokumenten.

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

