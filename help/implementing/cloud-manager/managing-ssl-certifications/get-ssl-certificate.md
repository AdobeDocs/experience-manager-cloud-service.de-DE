---
title: SSL-Zertifikat abrufen - Verwalten von SSL-Zertifikaten
description: SSL-Zertifikat abrufen - Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: 40119f7b3bdf36af668b79afbcb2802a0b2a6033
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Abrufen eines SSL-Zertifikats {#getting-an-ssl-certificate}

Unternehmen verwenden SSL-Zertifikate, um ihre Websites zu sichern und ihren Kunden das Vertrauen in sie zu geben. Um das SSL-Protokoll verwenden zu können, muss ein Webserver ein SSL-Zertifikat verwenden. Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei den Zertifizierungsstellen eingeholt werden.

Wenn eine Entität ein Zertifikat von einer Zertifizierungsstelle anfordert, führt die Zertifizierungsstelle einen Überprüfungsprozess durch. Dies kann von der Überprüfung der Domänennamenkontrolle bis zur Erfassung von Dokumenten zur Registrierung von Firmen und Abonnentenvereinbarungen reichen. Sobald die Informationen eines Unternehmens verifiziert wurden, signiert das CA seinen öffentlichen Schlüssel mithilfe des privaten Schlüssels der Zertifizierungsstelle. Da alle wichtigen Zertifizierungsstellen Stammzertifikate in Webbrowsern haben, wird das Zertifikat der Entität über eine *Vertrauenskette* verknüpft und vom Webbrowser als vertrauenswürdiges Zertifikat erkannt.

>[!NOTE]
>AEM als Cloud Service akzeptiert nur OV-(Organisationsüberprüfung) oder EV-(erweiterte Validierung) Zertifikate. DV-(Domänenvalidierung) oder selbst signierte Zertifikate werden nicht akzeptiert. OV- und EV-Zertifikate bieten Benutzern zusätzliche, CA-validierte Informationen, mit deren Hilfe sie entscheiden können, ob der Eigentümer einer Website, Absender einer E-Mail oder der digitale Unterzeichner von ausführbarem Code oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate sind häufig und kostengünstig. Sie lassen jedoch keine Eigentümerbestätigung zu.
>Darüber hinaus muss jedes Zertifikat ein X.509 TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle (CA) mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel sein.

