---
title: Einführung - Verwalten von SSL-Zertifikaten
description: Einführung - Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: 74cc587874c4d0a0ef9b542549801198d4f2d7a5
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Einführung {#introduction}

Cloud Manager bietet Kunden die Selbstbedienungsfunktion zum Installieren von SSL-Zertifikaten über die Cloud Manager-Benutzeroberfläche. Cloud Manager verwendet einen Platform TLS-Dienst, um SSL-Zertifikate und private Schlüssel zu verwalten, die Kunden gehören und die normalerweise von Zertifizierungsstellen von Drittanbietern bezogen werden, z. B. Let’s Encrypt.

>[!IMPORTANT]
>Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei Zertifizierungsstellen von Dritten eingeholt werden. Weitere Informationen finden Sie unter Abrufen eines SSL-Zertifikats. LINK EINFÜGEN

>[!NOTE]
>AEM als Cloud Service unterstützt nur sichere HTTPS-Sites. Kunden mit mehreren benutzerdefinierten Domänen möchten kein Zertifikat jedes Mal hochladen, wenn sie eine Domäne hinzufügen. Daher profitieren diese Kunden davon, wenn sie ein Zertifikat mit mehreren Domänen erhalten.

Cloud Manager unterstützt die folgenden SSL-Zertifikatsanforderungen für Kunden:

* Ein SSL-Zertifikat kann von mehreren Umgebung verwendet werden - einmal Hinzufügen und mehrmals.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält in der Regel mehrere Domänen.
* Der Platform TLS-Dienst leitet Anforderungen basierend auf dem SSL-Zertifikat, das zum Beenden verwendet wird, und dem CDN-Dienst, der diese Domäne hostet, an den CDN-Dienst des Kunden weiter.

Auf der Seite &quot;SSL-Zertifikate für die Benutzeroberfläche von Cloud Manager&quot;kann ein Benutzer mit Berechtigungen mehrere Aufgaben zum Verwalten von SSL-Zertifikaten für ein Programm ausführen:

* Hinzufügen eines SSL-Zertifikats.
* Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats. Diese Aktionen ermöglichen Ihnen die Ansicht von Details oder das Ersetzen eines Zertifikats, das demnächst abläuft.
* Löschen eines SSL-Zertifikats.