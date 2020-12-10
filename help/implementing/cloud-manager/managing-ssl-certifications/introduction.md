---
title: Einführung - Verwalten von SSL-Zertifikaten
description: Einführung - Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: 4ab944ad15390f9399138672a024aa30cf4aede8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---


# Einführung {#introduction}

Cloud Manager bietet Kunden die Selbstbedienungsfunktion zum Installieren von SSL-Zertifikaten über die Cloud Manager-Benutzeroberfläche. Cloud Manager verwendet einen Plattform-TLS-Dienst zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kunden gehören und die üblicherweise von Zertifizierungsstellen von Drittanbietern bezogen werden, z. B. *Let&#39;s Encrypt*.

## Wichtige Überlegungen {#important-considerations}


* Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei Zertifizierungsstellen von Dritten eingeholt werden. Weitere Informationen finden Sie unter [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) abrufen.

* AEM als Cloud Service unterstützt nur sichere `https` Sites. Kunden mit mehreren benutzerdefinierten Domänen möchten kein Zertifikat jedes Mal hochladen, wenn sie eine Domäne hinzufügen. Daher profitieren diese Kunden davon, wenn sie ein Zertifikat mit mehreren Domänen erhalten.

Cloud Manager unterstützt die folgenden SSL-Zertifikatsanforderungen für Kunden:

* Ein SSL-Zertifikat kann von mehreren Umgebung verwendet werden, d. h. einmal hinzufügen und mehrere Male verwenden.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält in der Regel mehrere Domänen.
* Der Platform TLS-Dienst leitet Anforderungen basierend auf dem SSL-Zertifikat, das zum Beenden verwendet wird, und dem CDN-Dienst, der diese Domäne hostet, an den CDN-Dienst des Kunden weiter.

Auf der Seite &quot;SSL-Zertifikate für die Benutzeroberfläche von Cloud Manager&quot;kann ein Benutzer mit Berechtigungen mehrere Aufgaben zum Verwalten von SSL-Zertifikaten für ein Programm ausführen:

* [SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/view-update-replace-ssl-certificate.md)
   >[!NOTE]
   >Diese Aktionen ermöglichen Ihnen die Ansicht von Details oder das Ersetzen eines Zertifikats, das demnächst abläuft.
* [Löschen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/delete-ssl-certificate.md)