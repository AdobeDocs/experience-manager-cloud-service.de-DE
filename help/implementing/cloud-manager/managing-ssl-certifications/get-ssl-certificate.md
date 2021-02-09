---
title: Abrufen eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
description: Abrufen eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: 40119f7b3bdf36af668b79afbcb2802a0b2a6033
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 90%

---


# Abrufen eines SSL-Zertifikats {#getting-an-ssl-certificate}

Unternehmen verwenden SSL-Zertifikate, um ihre Websites zu sichern, damit ihre Kunden ihnen vertrauen können. Um das SSL-Protokoll verwenden zu können, muss ein Webserver ein SSL-Zertifikat verwenden. Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei den Zertifizierungsstellen eingeholt werden.

Wenn eine Entität ein Zertifikat von einer Zertifizierungsstelle anfordert, führt die Zertifizierungsstelle eine Überprüfung durch. Diese kann von der Überprüfung der Namenskontrolle der Domains bis zur Erfassung von Unternehmensregistrierungsdokumenten und Abonnentenvereinbarungen reichen. Sobald die Informationen eines Unternehmens verifiziert wurden, signiert die Zertifizierungsstelle dessen öffentlichen Schlüssel mithilfe des privaten Schlüssels der Zertifizierungsstelle. Da alle wichtigen Zertifizierungsstellen über Stammzertifikate in Webbrowsern verfügen, wird das Zertifikat der Entität über eine *Vertrauenskette* verknüpft und vom Webbrowser als vertrauenswürdiges Zertifikat erkannt.

>[!NOTE]
>AEM as a Cloud Service akzeptiert nur OV (Organization Validation)- oder EV (Extended Validation)-Zertifikate. DV-(Domain Validation) oder selbst signierte Zertifikate werden nicht akzeptiert. OV- und EV-Zertifikate bieten Benutzern zusätzliche, von der Zertifizierungsstelle validierte Informationen, anhand derer sie entscheiden können, ob der Eigentümer einer Website, der Absender einer E-Mail oder der digitale Unterzeichner von ausführbarem Code oder PDF-Dokumenten vertrauenswürdig ist. DV-Zertifikate sind weit verbreitet und kostengünstig. Sie ermöglichen jedoch keine Überprüfung der Eigentümerschaft.
>Darüber hinaus muss jedes Zertifikat ein X.509 TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle (CA) mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel sein.

