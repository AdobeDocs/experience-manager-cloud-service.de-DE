---
title: Einführung – Verwalten von SSL-Zertifikaten
description: Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation von SSL-Zertifikaten bereitstellt.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: 898f7bc46a3f1b0ac93ee43fbf7b60a11682a073
workflow-type: ht
source-wordcount: '636'
ht-degree: 100%

---


# Einführung – Verwalten von SSL-Zertifikaten{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Verwalten von SSL-Zertifikaten"
>abstract="Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten zur Verfügung stellt, um Ihre Website für Ihre Benutzer zu sichern. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kunden gehören und von unabhängigen Zertifizierungsstellen bezogen werden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html?lang=de" text="Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html?lang=de" text="Überprüfen des Status eines SSL-Zertifikats"

Cloud Manager bietet Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten, um Ihre Site für Ihre Benutzer zu sichern. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kunden gehören und von unabhängigen Zertifizierungsstellen bezogen werden, z. B. Let&#39;s Encrypt.

## Einführung in Zertifikate {#certificates}

Unternehmen verwenden SSL-Zertifikate, um ihre Websites zu sichern, damit ihre Kunden ihnen vertrauen können. Um das SSL-Protokoll verwenden zu können, muss ein Webserver ein SSL-Zertifikat verwenden.

Wenn eine Entität ein Zertifikat von einer Zertifizierungsstelle anfordert, führt die Zertifizierungsstelle eine Überprüfung durch. Diese kann von der Überprüfung der Namenskontrolle der Domains bis zur Erfassung von Unternehmensregistrierungsdokumenten und Abonnentenvereinbarungen reichen. Sobald die Informationen eines Unternehmens verifiziert wurden, signiert die Zertifizierungsstelle dessen öffentlichen Schlüssel mithilfe des privaten Schlüssels der Zertifizierungsstelle. Da alle wichtigen Zertifizierungsstellen über Stammzertifikate in Webbrowsern verfügen, wird das Zertifikat der Entität über eine *Vertrauenskette* verknüpft und vom Webbrowser als vertrauenswürdiges Zertifikat erkannt.

>[!IMPORTANT]
>
>Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen von Zertifizierungsstellen (Certification Authorities, CAs) bezogen werden.

## SSL-Management-Funktionen in Cloud Manager {#features}

Cloud Manager unterstützt die folgenden Optionen für die Verwendung von SSL-Zertifikaten durch Kunden.

* Ein SSL-Zertifikat kann von mehreren Umgebungen verwendet werden. Es kann also einmal hinzugefügt und mehrmals verwendet werden.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält normalerweise mehrere Domains.
* Der Plattform-TLS-Service leitet Anfragen basierend auf dem zum Beenden verwendeten SSL-Zertifikat und dem CDN-Service, der diese Domain hostet, an den CDN-Service des Kunden weiter.
* AEM as a Cloud Service akzeptiert Platzhalter-SSL-Zertifikate für eine Domain.

## Empfehlungen {#recommendations}

AEM as a Cloud Service unterstützt nur sichere `https`-Sites.

* Kunden mit mehreren benutzerdefinierten Domains möchten nicht jedes Mal, wenn sie eine Domain hinzufügen, ein Zertifikat hochladen.
* Daher profitieren solche Kunden von einem Zertifikat mit mehreren Domains.

## Voraussetzungen {#requirements}

* AEM as a Cloud Service akzeptiert nur OV- (Organisationsvalidierung) oder EV-Richtlinien (erweiterte Validierung). 
* Außerdem muss es sich um ein X.509-TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel handeln.
* Eine DV (Domain-Validierung)-Richtlinie wird nicht akzeptiert.
* Selbstsignierte Zertifikate werden nicht akzeptiert.

OV- und EV-Zertifikate bieten Benutzern zusätzliche, von der Zertifizierungsstelle validierte Informationen, anhand derer sie entscheiden können, ob der Eigentümer einer Website, der Absender einer E-Mail oder der digitale Unterzeichner von ausführbarem Code oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate erlauben keine solche Eigentumsprüfung.

## Beschränkungen {#limitations}

Der Cloud Manager erlaubt die Installation von maximal 50 SSL-Zertifikaten zur gleichen Zeit. Diese können mit einer oder mehreren Umgebungen in Ihrem Programm verknüpft werden und auch abgelaufene Zertifikate enthalten.

Wenn Sie den Grenzwert erreicht haben, überprüfen Sie Ihre Zertifikate und erwägen Sie Folgendes:

* Löschen abgelaufener Zertifikate.
* Gruppieren mehrerer Domains im selben Zertifikat, da ein Zertifikat mehrere Domains (bis zu 100 SANs) abdecken kann.

## Weitere Informationen {#learn-more}

Ein Benutzer mit den erforderlichen Berechtigungen kann Cloud Manager verwenden, um SSL-Zertifikate für ein Programm zu verwalten. Weitere Informationen zur Verwendung dieser Funktionen finden Sie in den folgenden Dokumenten.

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
* [Löschen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
