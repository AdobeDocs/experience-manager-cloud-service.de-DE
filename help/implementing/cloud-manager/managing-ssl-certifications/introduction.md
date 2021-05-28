---
title: Einführung – Verwalten von SSL-Zertifikaten
description: Einführung – Verwalten von SSL-Zertifikaten
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: dfbd0f38017d02810da05ccadbc5f2fbd5826aa3
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 86%

---

# Einführung {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Verwalten von SSL-Zertifikaten"
>abstract="Cloud Manager bietet Kunden die Self-Service-Funktion zum Installieren von SSL-Zertifikaten über die Cloud Manager-Benutzeroberfläche. Cloud Manager verwendet einen Platform TLS-Dienst zur Verwaltung von SSL-Zertifikaten und privaten Schlüsseln, die im Besitz von Kunden sind und normalerweise von Zertifizierungsstellen von Drittanbietern bezogen werden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/view-update-replace-ssl-certificate.html?lang=de" text="Anzeigen, Aktualisieren und Ersetzen eines SSL-Zertifikats"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/check-status-ssl-certificate.html?lang=de" text="Status eines SSL-Zertifikats überprüfen"


Cloud Manager bietet Kunden die Self-Service-Funktion zum Installieren von SSL-Zertifikaten über die Cloud Manager-Benutzeroberfläche. Cloud Manager verwendet einen Plattform-TLS-Service zum Verwalten von SSL-Zertifikaten und privaten Schlüsseln, die Kunden gehören und normalerweise von Zertifizierungsstellen Dritter bezogen werden, z. B. *Let&#39;s Encrypt*.

## Wichtige Überlegungen {#important-considerations}

* Cloud Manager stellt keine SSL-Zertifikate oder privaten Schlüssel bereit. Diese müssen bei Zertifizierungsstellen Dritter eingeholt werden. Weitere Informationen finden Sie unter [Abrufen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md).

* AEM as a Cloud Service unterstützt nur sichere `https`-Sites. Kunden mit mehreren benutzerdefinierten Domains möchten nicht jedes Mal, wenn sie eine Domain hinzufügen, ein Zertifikat hochladen. Daher profitieren solche Kunden von einem Zertifikat mit mehreren Domains.

* AEM as a Cloud Service akzeptiert nur OV (Organization Validation)- oder EV (Extended Validation)-Zertifikate. DV-Zertifikate (Domain-Validation-Zertifikate) werden nicht akzeptiert. Außerdem muss es sich um ein X.509-TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel handeln.

* AEM als Cloud Service akzeptiert Wildcard-SSL-Zertifikate für eine Domäne.

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
