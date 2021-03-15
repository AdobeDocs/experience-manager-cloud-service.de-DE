---
title: Einführung – Verwalten von SSL-Zertifikaten
description: Einführung – Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: 4ab944ad15390f9399138672a024aa30cf4aede8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 100%

---


# Einführung {#introduction}

Cloud Manager bietet Kunden die Self-Service-Funktion zum Installieren von SSL-Zertifikaten über die Cloud Manager-Benutzeroberfläche. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kunden gehören und normalerweise von Zertifizierungsstellen Dritter bezogen werden, z. B. *Let&#39;s Encrypt*.

## Wichtige Überlegungen {#important-considerations}


* Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei Zertifizierungsstellen Dritter eingeholt werden. Weitere Informationen finden Sie unter [Abrufen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md).

* AEM as a Cloud Service unterstützt nur sichere `https`-Sites. Kunden mit mehreren benutzerdefinierten Domains möchten nicht jedes Mal, wenn sie eine Domain hinzufügen, ein Zertifikat hochladen. Daher profitieren solche Kunden von einem Zertifikat mit mehreren Domains.

Cloud Manager unterstützt die folgenden Kundenanforderungen für SSL-Zertifikate:

* Ein SSL-Zertifikat kann von mehreren Umgebungen verwendet werden, d. h. es wird einmal hinzugefügt und kann mehrfach verwendet werden.
* Jede Cloud Manager-Umgebung kann mehrere Zertifikate verwenden.
* Ein privater Schlüssel kann mehrere SSL-Zertifikate ausstellen.
* Jedes Zertifikat enthält in der Regel mehrere Domains.
* Der Plattform-TLS-Dienst leitet Anfragen basierend auf dem zum Beenden verwendeten SSL-Zertifikat und dem CDN-Service, der diese Domain hostet, an den CDN-Service des Kunden weiter.

Auf der Seite „SSL-Zertifikate“ der Cloud Manager-Benutzeroberfläche kann ein Benutzer mit den entsprechenden Berechtigungen mehrere Aufgaben ausführen, um SSL-Zertifikate für ein Programm zu verwalten:

* [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Anzeigen, Aktualisieren oder Ersetzen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/view-update-replace-ssl-certificate.md)
   >[!NOTE]
   >Mit diesen Aktionen können Sie Details anzeigen oder ein Zertifikat ersetzen, das demnächst abläuft.
* [Löschen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/delete-ssl-certificate.md)