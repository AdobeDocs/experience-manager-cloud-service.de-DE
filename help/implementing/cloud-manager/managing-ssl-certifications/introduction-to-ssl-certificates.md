---
title: Einführung in SSL-Zertifikate
description: Erfahren Sie mehr über die Self-Service-Tools, die Cloud Manager Ihnen zur Installation und Verwaltung von SSL-Zertifikaten bereitstellt.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b0c8769b5941ed772a91cf189e8c7355d1db766b
workflow-type: ht
source-wordcount: '1160'
ht-degree: 100%

---


# Einführung in SSL-Zertifikate{#introduction}

Erfahren Sie mehr über die Self-Service-Tools, die Cloud Manager Ihnen zur Installation und Verwaltung von SSL(Secure Socket Layer)-Zertifikaten bereitstellt.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Verwalten von SSL-Zertifikaten"
>abstract="Erfahren Sie, inwiefern Cloud Manager Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten zur Verfügung stellt, um Ihre Website für Ihre Benutzenden zu sichern. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die der Kundschaft gehören und von unabhängigen Zertifizierungsstellen bezogen werden."
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

>[!IMPORTANT]
>
>Wenn Ihre Umgebung (DV)-SSL-Zertifikate mit einer CNAME-basierten Validierung verwendet, beachten Sie, dass das Entfernen des CNAME-Eintrags vor der automatischen Zertifikatsverlängerung dazu führen kann, dass die Verlängerung fehlschlägt. Das Entfernen kann zum Ablauf des Zertifikats und zur Unterbrechung des Services führen. Um dieses Problem zu vermeiden, stellen Sie sicher, dass der CNAME-Eintrag während des gesamten Verlängerungsprozesses bestehen bleibt. Der Verlängerungsprozess basiert auf dem Vorhandensein des CNAME-Eintrags für die Validierung der Domain-Inhaberschaft.

### Kundenseitig verwaltete SSL-Zertifikate (OV/EV) {#customer-managed}

OV- und EV-Zertifikate bieten CA-validierte Informationen. Mithilfe dieser Informationen können Benutzende bewerten, ob die Eigentümerin bzw. der Eigentümer der Website, die Absenderin bzw. der Absender der E-Mail oder die digitale Unterzeichnerin bzw. der digitale Unterzeichner von Code- oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate erlauben keine solche Prüfung der Eigentümerschaft.

OV und EV bieten diese Funktionen zusätzlich über DV-Zertifikate in Cloud Manager an.

* Ein OV/EV-Zertifikat kann von mehreren Umgebungen verwendet werden. Es wird also nur einmal hinzugefügt, kann aber mehrmals verwendet werden.
* Jedes OV/EV-Zertifikat enthält normalerweise mehrere Domains.
* Cloud Manager akzeptiert Platzhalter-OV/EV-Zertifikate für eine Domain.

>[!TIP]
>
>Wenn Sie mehrere benutzerdefinierte Domains haben, möchten Sie vielleicht nicht jedes Mal, wenn Sie eine neue Domain hinzufügen, ein Zertifikat hochladen. In diesem Fall können Sie von einem einzigen Zertifikat profitieren, das mehrere Domains abdeckt.

#### Anforderungen für kundenseitig verwaltete OV/EV-SSL-Zertifikate {#requirements}

Wenn Sie sich dafür entscheiden, Ihr eigenes kundenseitig verwaltetes SSL-Zertifikat hinzuzufügen, muss es die folgenden aktualisierten Anforderungen erfüllen:

* DV(Domain Validation)-Zertifikate und selbstsignierte Zertifikate werden nicht unterstützt.
* Das Zertifikat muss den Richtlinien der OV (Organization Validation) oder EV (Extended Validation) entsprechen.
* Das Zertifikat muss ein X.509-TLS-Zertifikat sein, das von einer vertrauenswürdigen Zertifizierungsstelle (ZS) ausgestellt wurde.
* Folgende Kryptografieschlüsseltypen werden unterstützt:

   * RSA 2048-Bit, Standardunterstützung.
RSA-Schlüssel, die größer als 2048 Bit sind (z. B. 3072-Bit- oder 4096-Bit-RSA-Schlüssel), werden derzeit nicht unterstützt.
   * Elliptic Curve(EC)-Schlüssel `prime256v1` (`secp256r1`) und `secp384r1`.
   * Elliptic Curve Digital Signature Algorithm(ECDSA)-Zertifikate. Solche Zertifikate sind gemäß Adobe-Empfehlung RSA vorzuziehen, um die Leistung, Sicherheit und Effizienz zu verbessern.

* Zertifikate müssen korrekt formatiert sein, damit die Validierung erfolgreich ist. Private Schlüssel müssen im `PKCS#8`-Format vorliegen.

>[!NOTE]
>Wenn Ihre Organisation 3072-Bit-RSA-Schlüssel voraussetzt, empfiehlt Adobe als Alternative, ECDSA-Zertifikate (`secp256r1` oder `secp384r1`) zu verwenden.


#### Best Practices für die Zertifikatsverwaltung

* **Vermeiden von sich überschneidenden Zertifikaten:**

   * Um eine reibungslose Zertifikatsverwaltung sicherzustellen, sollten Sie die Bereitstellung sich überschneidender Zertifikate vermeiden, die derselben Domain entsprechen. Beispielsweise kann ein Platzhalterzertifikat (*.example.com) neben einem bestimmten Zertifikat (dev.example.com) zu Verwirrung führen.
   * Die TLS-Ebene priorisiert das spezifischste und zuletzt bereitgestellte Zertifikat.

  Beispielszenarien:

   * Ein „Dev-Zertifikat“ umfasst `dev.example.com` und wird als Domain-Zuordnung für `dev.example.com` bereitgestellt.
   * Das „Staging-Zertifikat“ umfasst `stage.example.com` und wird als Domain-Zuordnung für `stage.example.com` bereitgestellt.
   * Wenn das „Staging-Zertifikat“ *nach* dem „Dev-Zertifikat“ bereitgestellt/aktualisiert wird, bedient es auch Anfragen für `dev.example.com`.

     Um solche Konflikte zu vermeiden, stellen Sie sicher, dass Zertifikate genau auf ihre vorgesehenen Domains beschränkt bleiben.

* **Platzhalterzertifikate**

  Platzhalterzertifikate (z. B. `*.example.com`) werden zwar unterstützt, sollten aber nur verwendet werden, wenn dies notwendig ist. Bei Überschneidungen hat das spezifischere Zertifikat Vorrang. Beispielsweise bedient das spezifische Zertifikat `dev.example.com` anstelle des Platzhalters (`*.example.com`).

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

## Begrenzung der Anzahl installierter SSL-Zertifikate {#limitations}

Cloud Manager unterstützt immer bis zu 50 installierte Zertifikate. Diese Zertifikate können mit einer oder mehreren Umgebungen in Ihrem Programm verknüpft sein und auch abgelaufene Zertifikate enthalten.

Wenn Sie den Grenzwert erreicht haben, überprüfen Sie Ihre Zertifikate und löschen Sie ggf. abgelaufene Zertifikate. Oder gruppieren Sie mehrere Domains im selben Zertifikat, da ein Zertifikat mehrere Domains (bis zu 100 SANs) abdecken kann.

## Weitere Informationen {#learn-more}

Benutzende mit den erforderlichen Berechtigungen können Cloud Manager verwenden, um SSL-Zertifikate für ein Programm zu verwalten. Weitere Details zur Verwendung dieser Funktionen finden Sie in den folgenden Dokumenten.

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

