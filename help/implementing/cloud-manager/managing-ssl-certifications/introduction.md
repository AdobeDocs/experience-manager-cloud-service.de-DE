---
title: Einführung in die Verwaltung von SSL-Zertifikaten
description: Erfahren Sie, wie Cloud Manager Ihnen Self-Service-Tools zur Installation von SSL-Zertifikaten bereitstellt.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: 898f7bc46a3f1b0ac93ee43fbf7b60a11682a073
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 29%

---


# Einführung in die Verwaltung von SSL-Zertifikaten{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Verwalten von SSL-Zertifikaten"
>abstract="Erfahren Sie, wie Sie mit Cloud Manager Self-Service-Tools zum Installieren und Verwalten von SSL-Zertifikaten erhalten, um Ihre Site für Ihre Benutzer zu sichern. Cloud Manager verwendet einen Platform-TLS-Dienst zur Verwaltung von SSL-Zertifikaten und privaten Schlüsseln, die im Besitz von Kunden sind und von Zertifizierungsstellen von Drittanbietern erhalten wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html" text="Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html" text="Überprüfen des Status eines SSL-Zertifikats"

Cloud Manager bietet Self-Service-Tools zur Installation und Verwaltung von SSL-Zertifikaten, um Ihre Site für Ihre Benutzer zu schützen. Cloud Manager verwendet einen Platform-TLS-Dienst zur Verwaltung von SSL-Zertifikaten und privaten Schlüsseln, die im Besitz von Kunden sind und von Zertifizierungsstellen von Drittanbietern wie Let’s Encrypt erhalten wurden.

## Einführung in Zertifikate {#certificates}

Unternehmen verwenden SSL-Zertifikate, um ihre Websites zu sichern, damit ihre Kunden ihnen vertrauen können. Um das SSL-Protokoll verwenden zu können, muss ein Webserver ein SSL-Zertifikat verwenden.

Wenn eine Entität ein Zertifikat von einer Zertifizierungsstelle anfordert, führt die Zertifizierungsstelle eine Überprüfung durch. Diese kann von der Überprüfung der Namenskontrolle der Domains bis zur Erfassung von Unternehmensregistrierungsdokumenten und Abonnentenvereinbarungen reichen. Sobald die Informationen eines Unternehmens verifiziert wurden, signiert die Zertifizierungsstelle dessen öffentlichen Schlüssel mithilfe des privaten Schlüssels der Zertifizierungsstelle. Da alle wichtigen Zertifizierungsstellen über Stammzertifikate in Webbrowsern verfügen, wird das Zertifikat der Entität über eine *Vertrauenskette* verknüpft und vom Webbrowser als vertrauenswürdiges Zertifikat erkannt.

>[!IMPORTANT]
>
>Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei Zertifizierungsstellen erhältlich sein.

## SSL-Management-Funktionen in Cloud Manager {#features}

Cloud Manager unterstützt die folgenden Nutzungsoptionen für SSL-Zertifikate von Kunden.

* Ein SSL-Zertifikat kann von mehreren Umgebungen verwendet werden. Es kann also einmal hinzugefügt und mehrmals verwendet werden.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält normalerweise mehrere Domänen.
* Der Plattform-TLS-Dienst leitet Anfragen an den CDN-Dienst des Kunden basierend auf dem SSL-Zertifikat, das zum Beenden verwendet wird, und dem CDN-Dienst, der diese Domäne hostet, weiter.
* AEM as a Cloud Service akzeptiert Platzhalter-SSL-Zertifikate für eine Domäne.

## Empfehlungen {#recommendations}

AEM as a Cloud Service unterstützt nur sichere `https`-Sites.

* Kunden mit mehreren benutzerdefinierten Domains möchten nicht jedes Mal, wenn sie eine Domain hinzufügen, ein Zertifikat hochladen.
* Diese Kunden profitieren von einem Zertifikat mit mehreren Domänen.

## Voraussetzungen {#requirements}

* AEM as a Cloud Service akzeptiert nur Zertifikate, die der OV- (Organisationsvalidierung) oder der EV-Richtlinie (erweiterte Validierung) entsprechen.
* Jedes Zertifikat muss ein X.509-TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle (CA) mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel sein.
* Die DV-Richtlinie (Domain Validation) wird nicht akzeptiert.
* Selbstsignierte Zertifikate werden nicht akzeptiert.

OV- und EV-Zertifikate bieten Benutzern zusätzliche, von einer Zertifizierungsstelle validierte Informationen, mit denen sie entscheiden können, ob der Eigentümer einer Website, der Absender einer E-Mail oder der digitale Unterzeichner von ausführbarem Code oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate erlauben keine solche Eigentumsprüfung.

## Beschränkungen {#limitations}

Cloud Manager lässt die Installation von maximal 50 SSL-Zertifikaten jederzeit zu. Diese können mit einer oder mehreren Umgebungen in Ihrem Programm verknüpft werden und auch abgelaufene Zertifikate enthalten.

Wenn Sie den Grenzwert erreicht haben, überprüfen Sie Ihre Zertifikate und beachten Sie Folgendes:

* Löschen abgelaufener Zertifikate.
* Gruppieren mehrerer Domänen im selben Zertifikat, da ein Zertifikat mehrere Domänen (bis zu 100 SANs) abdecken kann.

## Weitere Informationen {#learn-more}

Ein Benutzer mit den erforderlichen Berechtigungen kann Cloud Manager verwenden, um SSL-Zertifikate für ein Programm zu verwalten. Weitere Informationen zur Verwendung dieser Funktionen finden Sie in den folgenden Dokumenten.

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
* [Löschen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
