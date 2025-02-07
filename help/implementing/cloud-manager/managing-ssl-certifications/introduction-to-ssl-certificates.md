---
title: Einführung in SSL-Zertifikate
description: Erfahren Sie mehr über die Self-Service-Tools, die Cloud Manager Ihnen zur Installation und Verwaltung von SSL-Zertifikaten bereitstellt.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: a91b15836d0ca0308fbc860ec57aacda908f610d
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 64%

---


# Einführung in SSL-Zertifikate{#introduction}

Erfahren Sie mehr über die Self-Service-Tools, die Cloud Manager Ihnen zur Installation und Verwaltung von SSL(Secure Socket Layer)-Zertifikaten bereitstellt.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Verwalten von SSL-Zertifikaten"
>abstract="Erfahren Sie, wie Cloud Manager Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten zur Verfügung stellt, um Ihre Website für Ihre Benutzerinnen und Benutzer zu schützen. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kundinnen bzw. Kunden gehören und von unabhängigen Zertifizierungsstellen bezogen werden."
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
| A | **[Adobe-verwaltetes SSL-Zertifikat (DV)](#adobe-managed)** | Mit Cloud Manager können Benutzer DV-Zertifikate (Domain-Validierung) konfigurieren, die von Adobe für die schnelle Domain-Einrichtung bereitgestellt werden. |
| B | **[Kundenverwaltetes SSL-Zertifikat (OV/EV)](#customer-managed)** | Cloud Manager verwendet einen Plattform-TLS(Transport Layer Security)-Dienst, damit Sie Ihre eigenen OV- und EV-SSL-Zertifikate und private Schlüssel von Zertifizierungsstellen von Drittanbietern, z. B. *Let’s Encrypt*, verwalten können. |

Beide Modelle bieten die folgenden allgemeinen Funktionen für die Verwaltung Ihrer Zertifikate:

* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Der Plattform-TLS-Service leitet Anfragen basierend auf dem zum Beenden verwendeten SSL-Zertifikat und dem CDN-Service, der diese Domain hostet, an den CDN-Service der Kundin bzw. des Kunden weiter.

>[!IMPORTANT]
>
>[Um eine benutzerdefinierte Domain hinzuzufügen und mit einer Umgebung zu verknüpfen](/help/implementing/cloud-manager/custom-domain-names/introduction.md), müssen Sie über ein gültiges SSL-Zertifikat verfügen, das die Domain abdeckt.

### Adobe-verwaltete SSL-Zertifikate (DV) {#adobe-managed}

DV-Zertifikate stehen für die einfachste SSL-Zertifizierungsstufe und werden häufig zu Testzwecken oder zum Schützen von Websites mit einer einfachen Verschlüsselung verwendet. DV-Zertifikate sind in [Produktions- und Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) verfügbar.

Nachdem das DV-Zertifikat erstellt wurde, erneuert Adobe es automatisch alle drei Monate, es sei denn, es wird gelöscht.

### Kundenverwaltete SSL-Zertifikate (OV/EV) {#customer-managed}

OV- und EV-Zertifikate bieten CA-validierte Informationen. Mithilfe dieser Informationen können Benutzende bewerten, ob die Eigentümerin bzw. der Eigentümer der Website, die Absenderin bzw. der Absender der E-Mail oder die digitale Unterzeichnerin bzw. der digitale Unterzeichner von Code- oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate erlauben keine solche Prüfung der Eigentümerschaft.

OV und EV bieten diese Funktionen zusätzlich über DV-Zertifikate in Cloud Manager an.

* Ein OV/EV-Zertifikat kann von mehreren Umgebungen verwendet werden. Es wird also nur einmal hinzugefügt, kann aber mehrmals verwendet werden.
* Jedes OV/EV-Zertifikat enthält normalerweise mehrere Domains.
* Cloud Manager akzeptiert Platzhalter-OV/EV-Zertifikate für eine Domain.

>[!TIP]
>
>Wenn Sie mehrere benutzerdefinierte Domains haben, möchten Sie vielleicht nicht jedes Mal, wenn Sie eine neue Domain hinzufügen, ein Zertifikat hochladen. In diesem Fall können Sie von einem einzigen Zertifikat profitieren, das mehrere Domains abdeckt.

#### Anforderungen für kundenverwaltete OV/EV-SSL-Zertifikate {#requirements}

Wenn Sie Ihr eigenes kundenverwaltetes SSL-Zertifikat hinzufügen möchten, muss es die folgenden aktualisierten Anforderungen erfüllen:

* DV-Zertifikate (Domain Validation) und selbstsignierte Zertifikate werden nicht unterstützt.
* Das Zertifikat muss den OV- (Organisationsvalidierung) oder EV-Richtlinien (erweiterte Validierung) entsprechen.
* Das Zertifikat muss ein X.509-TLS-Zertifikat sein, das von einer vertrauenswürdigen Zertifizierungsstelle (CA) ausgestellt wird.
* Folgende kryptografische Schlüsseltypen werden unterstützt:

   * RSA 2048-Bit, Standard Support.
RSA-Schlüssel, die größer als 2048 Bit sind (z. B. 3072-Bit- oder 4096-Bit-RSA-Schlüssel) werden derzeit nicht unterstützt.
   * Elliptische Kurve (EC) `prime256v1` (`secp256r1`) und `secp384r1`
   * Zertifikate des Elliptic Curve Digital Signature Algorithm (ECDSA). Solche Zertifikate werden im Adobe-Modus gegenüber RSA empfohlen, um die Leistung, Sicherheit und Effizienz zu verbessern.

* Zertifikate müssen korrekt formatiert sein, damit die Validierung erfolgreich ist. Private Schlüssel müssen im `PKCS#8` Format vorliegen.

>[!NOTE]
>Wenn Ihr Unternehmen die Einhaltung von Richtlinien mit 3072-Bit-RSA-Schlüsseln fordert, ist die von der Adobe empfohlene Alternative die Verwendung von ECDSA-Zertifikaten (`secp256r1` oder `secp384r1`).


#### Best Practices für die Zertifikatverwaltung

* **Überschneidungen von Zertifikaten vermeiden:**

   * Um eine reibungslose Zertifikatverwaltung zu gewährleisten, sollten Sie vermeiden, sich überschneidende Zertifikate bereitzustellen, die derselben Domain entsprechen. Beispielsweise kann ein Platzhalterzertifikat (*.example.com) neben einem bestimmten Zertifikat (dev.example.com) verwirrend sein.
   * Die TLS-Ebene priorisiert das spezifischste und zuletzt bereitgestellte Zertifikat.

  Beispielszenarien:

   * „Dev Certificate“ umfasst `dev.example.com` und wird als Domain-Zuordnung für `dev.example.com` bereitgestellt.
   * Das „Staging-Zertifikat“ deckt `stage.example.com` ab und wird als Domain-Zuordnung für `stage.example.com` bereitgestellt.
   * Wenn „Staging-Zertifikat“ bereitgestellt/aktualisiert wird *nach* „Dev-Zertifikat“, werden auch Anfragen für `dev.example.com` bearbeitet.

     Um solche Konflikte zu vermeiden, stellen Sie sicher, dass Zertifikate sorgfältig auf ihre vorgesehenen Domains beschränkt sind.

* **Platzhalterzertifikate:**

  Platzhalterzertifikate (z. B. `*.example.com`) werden zwar unterstützt, sollten aber nur verwendet werden, wenn dies notwendig ist. Bei Überschneidungen hat das spezifischere Zertifikat Vorrang. Beispielsweise dient das spezifische Zertifikat `dev.example.com` anstelle des Platzhalters (`*.example.com`).

* **Validierung und Fehlerbehebung:**
Bevor Sie versuchen, ein Zertifikat mit Cloud Manager zu installieren, empfiehlt Adobe, die Integrität Ihres Zertifikats lokal mit Tools wie `openssl` zu überprüfen. Zum Beispiel:

  `openssl verify -untrusted intermediate.pem certificate.pem`


<!--
>[!NOTE]
>
>If two certificates cover the same domain are installed, the one that is more exact is applied.
>
>For example, if your domain is `dev.adobe.com` and you have one certificate for `*.adobe.com` and another for `dev.adobe.com`, the more specific one (`dev.adobe.com`) is used.
-->

#### Format für kundenverwaltete Zertifikate {#certificate-format}

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

Cloud Manager unterstützt immer bis zu 50 installierte Zertifikate. Diese Zertifikate können mit einer oder mehreren Umgebungen in Ihrem Programm verknüpft sein und auch abgelaufene Zertifikate enthalten.

Wenn Sie den Grenzwert erreicht haben, überprüfen Sie Ihre Zertifikate und löschen Sie ggf. abgelaufene Zertifikate. Oder gruppieren Sie mehrere Domains im selben Zertifikat, da ein Zertifikat mehrere Domains (bis zu 100 SANs) abdecken kann.

## Weitere Informationen {#learn-more}

Benutzende mit den erforderlichen Berechtigungen können Cloud Manager verwenden, um SSL-Zertifikate für ein Programm zu verwalten. Weitere Details zur Verwendung dieser Funktionen finden Sie in den folgenden Dokumenten.

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

