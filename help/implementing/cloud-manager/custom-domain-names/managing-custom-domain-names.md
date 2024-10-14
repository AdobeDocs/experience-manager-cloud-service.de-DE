---
title: Verwalten von benutzerdefinierten Domain-Namen
description: Erfahren Sie, wie Sie mit Cloud Manager benutzerdefinierte Domain-Namen anzeigen, aktualisieren, ersetzen und löschen können.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 62%

---


# Verwalten von benutzerdefinierten Domain-Namen {#managing-custom-domain-names}

Mit Cloud Manager können Sie benutzerdefinierte Domänennamen bearbeiten, aktualisieren, ersetzen, überprüfen und löschen.

## Bearbeiten der Konfiguration eines benutzerdefinierten Domain-Namens {#view-and-update}

Unter Adobe Cloud Manager können Sie eine benutzerdefinierte Domain-Namenskonfiguration aus folgenden Gründen bearbeiten:

* **Wechseln von Umgebungen**: Um die richtige Konfiguration anzuwenden, je nachdem, ob Sie Inhalte für Endbenutzende (Veröffentlichen) oder interne Benutzende (Autor) bereitstellen.
* **Sicherheits-Updates**: Zum Aktualisieren auf ein neueres SSL-Zertifikat, um die Sicherheit oder Compliance zu verbessern.
* **Ändern der Bereitstellungsstrategie**: Um sicherzustellen, dass das richtige SSL-Zertifikat auf eine bestimmte Umgebung angewendet wird, um eine ordnungsgemäße Verschlüsselung und den Site-Zugriff zu gewährleisten.

**So bearbeiten Sie die Konfiguration eines benutzerdefinierten Domain-Namens:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie oben links auf der Seite auf das Symbol ![Anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Menü links einzublenden.

1. Klicken Sie unter der Überschrift **Services** auf **CDN-Konfigurationen**.

1. Klicken Sie auf der Seite **CDN-Konfigurationen** auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren CDN Sie bearbeiten möchten.

1. Klicken Sie auf **Bearbeiten**.

1. Gehen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** wie folgt vor:

   * Wählen Sie aus der Dropdown-Liste **Ebene** die Ebene (Veröffentlichung oder Vorschau) aus, die Sie verwenden möchten.
   * Wählen Sie in der Dropdownliste **SSL-Zertifikat** das SSL-Zertifikat aus, das Sie verwenden möchten.

1. Klicken Sie auf **Aktualisieren**.


## Aktualisieren des SSL-Zertifikats eines benutzerdefinierten Domain-Namens {#update-cert}

Führen Sie die oben beschriebenen Schritte aus, um das SSL-Zertifikat eines benutzerdefinierten Domänennamens zu aktualisieren.

>[!NOTE]
>
>Das SSL-Zertifikat muss gültig und [bereits konfiguriert](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) sein und den benutzerdefinierten Domain-Namen enthalten, den Sie aktualisieren.


## Benutzerdefinierten Domänennamen überprüfen {#verify-custom-domain-name}

Siehe auch [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie über den Bildschirm **Umgebungen** zur Seite **Domain-Einstellungen**.

1. Identifizieren Sie die Zeile des benutzerdefinierten Domänennamens, den Sie überprüfen möchten.

1. Klicken Sie ganz rechts in der Zeile auf das Symbol ![Mehr .](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)

1. Klicken Sie im Dropdown-Menü auf **Verify**.

1. Wählen Sie im Dialogfeld **Domain verifizieren** aus der Dropdown-Liste **Welchen Zertifikatstyp möchten Sie mit dieser Domain verwenden?** eine der folgenden Optionen aus:

   | Option für den Zertifikatstyp | Beschreibung |
   | --- | --- |
   | Adobe managed (DV) SSL-Zertifikat | Wählen Sie diesen Zertifikatstyp aus, wenn Sie ein DV(Domain Validation)-Zertifikat verwenden möchten. Diese Option eignet sich in den meisten Fällen hervorragend, da sie eine grundlegende Domain-Validierung ermöglicht. Adobe verwaltet und erneuert das Zertifikat automatisch. |
   | Vom Kunden verwaltetes SSL-Zertifikat (OV/EV) | Wählen Sie diesen Zertifikatstyp aus, wenn Sie zum Schützen der Domäne ein EV/OV-SSL-Zertifikat verwenden möchten. Diese Option bietet verbesserte Sicherheit mit OV (Organisationsvalidierung) oder EV (erweiterte Validierung). Verwenden Sie sie, wenn eine strengere Überprüfung, eine höhere Vertrauensebene oder eine benutzerdefinierte Kontrolle über die Zertifikate erforderlich sind. |

1. Führen Sie im Dialogfeld **Domain verifizieren** je nach ausgewähltem Zertifikatstyp einen der folgenden Schritte aus:

   | Ausgewählter Zertifikatstyp | Beschreibung |
   | --- | ---  |
   | Verwaltetes Adobe-Zertifikat | a. Führen Sie die [Adobe verwalteten Zertifikatschritte](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-steps) aus. Wenn Sie die Schritte im Dialogfeld **Domäne verifizieren** ausführen, klicken Sie auf **Überprüfen**.<ul><li>Die DNS-Überprüfung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.</li><li>Cloud Manager überprüft schließlich das Eigentum an Domänennamen und aktualisiert den Status in der Tabelle **Domäneneinstellungen**. Weitere Informationen finden Sie unter [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).</li>![Verifizierung des Domänenstatus](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. Sie können jetzt [ein von Adobe verwaltetes (DV) SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert).</li></ul> |
   | Kundenseitig verwaltetes Zertifikat | a. Klicken Sie auf **OK**.<br>b. Sie können jetzt ein kundenverwaltetes SSL-Zertifikat (OV/EV) [ hinzufügen.](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert)<br>Nachdem Sie das Zertifikat hinzugefügt haben, wird Ihr Domänenname in der Tabelle **Domäneneinstellungen** als verifiziert markiert. Weitere Informationen finden Sie unter [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).</li></ul><br>![Verifizieren der Domain für ein kundenseitig verwaltetes EV/OV-Zertifikat](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |


## Löschen eines benutzerdefinierten Domain-Namens aus allen zugehörigen Umgebungen {#deleting}

Benutzende mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können Cloud Manager verwenden, um einen benutzerdefinierten Domain-Namen zu löschen.

### Löschen eines benutzerdefinierten Domain-Namens aus allen zugehörigen Umgebungen {#delete-cdn-all}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie über den Bildschirm **Umgebungen** zur Seite **Domain-Einstellungen**.

1. Ermitteln Sie die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.

1. Klicken Sie ganz rechts in der Zeile auf das Symbol ![Mehr .](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)

1. Wählen Sie **Löschen** aus.

1. Bestätigen Sie Ihre Übermittlung.


### Löschen eines benutzerdefinierten Domain-Namens aus einer bestimmten Umgebung {#delete-cdn-specific}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie von der Seite **Umgebungen** zum Bildschirm „Umgebungsdetails“ der betreffenden Umgebung.

1. Ermitteln Sie in der Tabelle mit den Domain-Namen die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.

1. Klicken Sie ganz rechts in der Zeile auf das Symbol ![Mehr .](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)

1. Wählen Sie **Löschen** aus.

1. Bestätigen Sie Ihre Übermittlung.
