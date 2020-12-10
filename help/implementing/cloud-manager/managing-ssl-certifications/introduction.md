---
title: Einführung - Verwalten von SSL-Zertifikaten
description: Einführung - Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: 5ebe94c8562b952521effa3b67267c3eab925d16
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Einführung {#introduction}

Cloud Manager bietet Kunden die Selbstbedienungsfunktion zum Installieren von SSL-Zertifikaten über die Cloud Manager-Benutzeroberfläche. Cloud Manager verwendet einen Platform TLS-Dienst, um SSL-Zertifikate und private Schlüssel zu verwalten, die Kunden gehören und die normalerweise von Zertifizierungsstellen von Drittanbietern bezogen werden, z. B. Let’s Encrypt.

>[!IMPORTANT]
>Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei Zertifizierungsstellen von Dritten eingeholt werden. Weitere Informationen finden Sie unter [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) abrufen.

>[!NOTE]
>AEM als Cloud Service unterstützt nur sichere HTTPS-Sites. Kunden mit mehreren benutzerdefinierten Domänen möchten kein Zertifikat jedes Mal hochladen, wenn sie eine Domäne hinzufügen. Daher profitieren diese Kunden davon, wenn sie ein Zertifikat mit mehreren Domänen erhalten.

Cloud Manager unterstützt die folgenden SSL-Zertifikatsanforderungen für Kunden:

* Ein SSL-Zertifikat kann von mehreren Umgebung verwendet werden, d. h. einmal hinzufügen und mehrere Male verwenden.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält in der Regel mehrere Domänen.
* Der Platform TLS-Dienst leitet Anforderungen basierend auf dem SSL-Zertifikat, das zum Beenden verwendet wird, und dem CDN-Dienst, der diese Domäne hostet, an den CDN-Dienst des Kunden weiter.

Auf der Seite &quot;SSL-Zertifikate für die Benutzeroberfläche von Cloud Manager&quot;kann ein Benutzer mit Berechtigungen mehrere Aufgaben zum Verwalten von SSL-Zertifikaten für ein Programm ausführen:

* SSL-Zertifikat hinzufügen
* Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats
   >[!NOTE]
   >Diese Aktionen ermöglichen Ihnen die Ansicht von Details oder das Ersetzen eines Zertifikats, das demnächst abläuft.
* Löschen eines SSL-Zertifikats