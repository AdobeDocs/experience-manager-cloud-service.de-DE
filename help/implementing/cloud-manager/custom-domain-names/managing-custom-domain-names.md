---
title: Verwalten von benutzerdefinierten Domain-Namen
description: Erfahren Sie, wie Sie mit Cloud Manager benutzerdefinierte Domain-Namen anzeigen, aktualisieren, ersetzen und löschen können.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1683d53491e06ebe2dfcc96184ce251539ecf732
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 100%

---


# Verwalten von benutzerdefinierten Domain-Namen {#managing-custom-domain-names}

Mit Cloud Manager können Sie benutzerdefinierte Domain-Namen bearbeiten, aktualisieren, ersetzen, überprüfen und löschen.

## Bearbeiten der Konfiguration eines benutzerdefinierten Domain-Namens {#view-and-update}

Es könnte aus folgenden Gründen erforderlich sein, dass Sie die Konfiguration eines benutzerdefinierten Domain-Namens in Adobe Cloud Manager bearbeiten:

* **Wechseln von Umgebungen**: Um die richtige Konfiguration anzuwenden, je nachdem, ob Sie Inhalte für Endbenutzende (Veröffentlichen) oder interne Benutzende (Autor) bereitstellen.
* **Sicherheits-Updates**: Zum Aktualisieren auf ein neueres SSL-Zertifikat, um die Sicherheit oder Compliance zu verbessern.
* **Ändern der Bereitstellungsstrategie**: Um sicherzustellen, dass das richtige SSL-Zertifikat auf eine bestimmte Umgebung angewendet wird, um eine ordnungsgemäße Verschlüsselung und den Site-Zugriff zu gewährleisten.

**So bearbeiten Sie die Konfiguration eines benutzerdefinierten Domain-Namens:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.

1. Klicken Sie unter der Überschrift **Services** auf ![Symbol für soziale Netzwerke](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain-Zuordnungen**.

1. Klicken Sie auf der Seite **Domain-Zuordnungen** auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende der Zeile, deren CDN Sie bearbeiten möchten.

1. Klicken Sie auf **Bearbeiten**.

1. Gehen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** wie folgt vor:

   * Wählen Sie aus der Dropdown-Liste **Ebene** die Ebene (Veröffentlichung oder Vorschau) aus, die Sie verwenden möchten.
   * Wählen Sie in der Dropdown-Liste **SSL-Zertifikat** das SSL-Zertifikat aus, das Sie verwenden möchten.

1. Klicken Sie auf **Aktualisieren**.


## Aktualisieren des SSL-Zertifikats eines benutzerdefinierten Domain-Namens {#update-cert}

Führen Sie die oben beschriebenen Schritte aus, um das SSL-Zertifikat eines benutzerdefinierten Domain-Namens zu aktualisieren.

>[!NOTE]
>
>Das SSL-Zertifikat muss gültig und [bereits konfiguriert](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) sein und den benutzerdefinierten Domain-Namen enthalten, den Sie aktualisieren.


## Überprüfen eines benutzerdefinierten Domain-Namens {#verify-custom-domain-name}

Siehe auch [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie über den Bildschirm **Umgebungen** zur Seite **Domain-Einstellungen**.

1. Ermitteln Sie die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie überprüfen möchten.

1. Klicken Sie ganz rechts in der Zeile auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. Klicken Sie im Dropdown-Menü auf **Überprüfen**.

1. Wählen Sie im Dialogfeld **Domain verifizieren** aus der Dropdown-Liste **Welchen Zertifikatstyp möchten Sie mit dieser Domain verwenden?** eine der folgenden Optionen aus:

   | Option für den Zertifikatstyp | Beschreibung |
   | --- | --- |
   | Von Adobe verwaltetes SSL-Zertifikat (DV) | Wählen Sie diesen Zertifikatstyp aus, wenn Sie ein DV(Domain Validation)-Zertifikat verwenden möchten. Diese Option eignet sich in den meisten Fällen hervorragend, da sie eine grundlegende Domain-Validierung ermöglicht. Adobe verwaltet und erneuert das Zertifikat automatisch. |
   | Kundenseitig verwaltetes SSL-Zertifikat (OV/EV) | Wählen Sie diesen Zertifikatstyp aus, wenn zum Schutz der Domain ein EV/OV-SSL-Zertifikat verwendet werden soll. Diese Option bietet eine verbesserte Sicherheit mit OV (Organization Validation) oder EV (Extended Validation). Verwenden Sie sie, wenn eine strengere Überprüfung, eine höhere Vertrauensebene oder eine benutzerdefinierte Kontrolle über die Zertifikate erforderlich sind. |

1. Führen Sie im Dialogfeld **Domain verifizieren** je nach ausgewähltem Zertifikatstyp einen der folgenden Schritte aus:

   | Ausgewählter Zertifikatstyp | Beschreibung |
   | --- | ---  |
   | Verwaltetes Adobe-Zertifikat | a. Führen Sie die [Schritte für von Adobe verwaltete Zertifikate](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-steps) aus. Klicken Sie nach Abschluss der Schritte im Dialogfeld **Domain verifizieren** auf **Überprüfen**.<ul><li>Die DNS-Überprüfung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.</li><li>Cloud Manager überprüft schließlich die Eigentümerschaft des Domain-Namens und aktualisiert den Status in der Tabelle **Domain-Einstellungen**. Weitere Informationen finden Sie unter [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).</li>![Überprüfen des Domain-Status](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. Sie können jetzt [ein von Adobe verwaltetes (DV) SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert).</li></ul> |
   | Kundenseitig verwaltetes Zertifikat | a. Klicken Sie auf **OK**.<br>b. Sie können jetzt ein [kundenseitig verwaltetes (OV/EV) SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert).<br>Nachdem Sie das Zertifikat hinzugefügt haben, wird Ihr Domain-Name in der Tabelle **Domain-Einstellungen** als verifiziert markiert. Weitere Informationen finden Sie unter [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).</li></ul><br>![Verifizieren der Domain für ein kundenseitig verwaltetes EV/OV-Zertifikat](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |


## Löschen eines benutzerdefinierten Domain-Namens aus allen zugehörigen Umgebungen {#deleting}

Benutzende mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können Cloud Manager verwenden, um einen benutzerdefinierten Domain-Namen zu löschen.

### Löschen eines benutzerdefinierten Domain-Namens aus allen zugehörigen Umgebungen {#delete-cdn-all}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie über den Bildschirm **Umgebungen** zur Seite **Domain-Einstellungen**.

1. Ermitteln Sie die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.

1. Klicken Sie ganz rechts in der Zeile auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. Wählen Sie **Löschen** aus.

1. Bestätigen Sie Ihre Übermittlung.


### Löschen eines benutzerdefinierten Domain-Namens aus einer bestimmten Umgebung {#delete-cdn-specific}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie von der Seite **Umgebungen** zum Bildschirm „Umgebungsdetails“ der betreffenden Umgebung.

1. Ermitteln Sie in der Tabelle mit den Domain-Namen die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.

1. Klicken Sie ganz rechts in der Zeile auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. Wählen Sie **Löschen** aus.

1. Bestätigen Sie Ihre Übermittlung.
