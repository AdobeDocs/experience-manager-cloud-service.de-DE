---
title: Hinzufügen eines SSL-Zertifikats
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL-Zertifikat oder Adobe-verwaltetes DV-Zertifikat (Domänenvalidierung) hinzufügen.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 75%

---


# Hinzufügen eines SSL-Zertifikats {#add-ssl-cert}

Erfahren Sie, wie Sie mithilfe von Cloud Ihr eigenes SSL-Zertifikat oder Adobe-verwaltetes DV-Zertifikat (Domänenvalidierung) hinzufügen.

>[!TIP]
>
>Die Bereitstellung eines Zertifikats kann einige Tage dauern. Daher empfiehlt Adobe, dass Sie, wenn Sie Ihr eigenes Zertifikat bereitstellen, dieses rechtzeitig vor einer Frist oder einem Live-Datum bereitstellen.

## Voraussetzungen {#prerequisites}

* Ein Benutzer muss Mitglied der Rolle **Business Owner** oder **Deployment Manager** sein, um ein Zertifikat hinzuzufügen.
* Wenn Sie Ihr eigenes Zertifikat installieren, finden Sie weitere Informationen unter **Zertifikatanforderungen** in der Einführung in die Verwaltung von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements).[

## Hinzufügen eines SSL-Zertifikats {#add-certificate}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü anzuzeigen.
1. Klicken Sie unter der Überschrift **Services** auf ![Sperrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL-Zertifikate**.

   ![Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Klicken Sie oben rechts auf der Seite „SSL-Zertifikate“ auf **SSL-Zertifikat hinzufügen**.

1. Führen Sie im Dialogfeld **SSL-Zertifikat hinzufügen** basierend auf dem [vorliegenden Anwendungsfall](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) einen der folgenden Schritte aus:

   | | Anwendungsfall | Schritte |
   | --- | --- | --- |
   | 1 | **Hinzufügen eines von Adobe verwalteten Zertifikats (DV)** | **So fügen Sie ein von Adobe verwaltetes Zertifikat (DV) hinzu:**<br> a. Wählen Sie im Dialogfeld **SSL-Zertifikat hinzufügen** für den Zertifikatstyp die Option **Von Adobe verwaltet (DV)** aus.<br>![Hinzufügen eines DV-Zertifikats](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. Geben Sie im Feld **Zertifikatname** einen Namen ein, der dem Zertifikat zugeordnet werden soll.<br>c. Wählen Sie in der Dropdown-Liste **Domains auswählen** eine oder mehrere Domains aus, die dem DV-Zertifikat zugeordnet werden sollen.<br>Keine Domains auswählbar? Ist dies der Fall, müssen Sie eine benutzerdefinierte Domain hinzufügen. Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Nachdem Sie einen benutzerdefinierten Domain-Namen hinzugefügt haben, kehren Sie zu diesem Thema zurück und beginnen Sie erneut mit Schritt 1.<br>d. Fahren Sie mit Schritt 7 fort. |
   | 2 | **Hinzufügen eines kundenseitig verwalteten Zertifikats (OV/EV)** | **So fügen Sie ein kundenseitig verwaltetes Zertifikats (OV/EV) hinzu:**<br> a. Wählen Sie im Dialogfeld **SSL-Zertifikat hinzufügen** als Zertifikatstyp die Option **Kundenseitig verwaltet (OV/EV)** aus.<br>b. Geben Sie in das Feld **Zertifikatname** einen Namen für Ihr Zertifikat ein. Dieses Feld dient nur zu Informationszwecken, und der Name kann so gewählt werden, dass Sie Ihr Zertifikat leicht finden können.<br>c. Fügen Sie in die Felder **Zertifikat**, **Privater Schlüssel** und **Zertifikatskette** die erforderlichen Werte ein.<br>![Dialogfeld „SSL-Zertifikat hinzufügen“](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Alle erkannten Fehler in den Werten werden angezeigt. Bevor Sie Ihr Zertifikat speichern können, müssen Sie alle Fehler beheben. Weitere Informationen zum Beheben häufiger Fehler finden Sie unter [Zertifikatfehler](#certificate-errors).<br>d. Fahren Sie mit Schritt 7 fort. |

1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

Nachdem das Zertifikat erfolgreich ausgestellt wurde, wird es mit einem grünen Häkchen in der Tabelle **SSL-Zertifikate** angezeigt.

Sie haben jetzt ein funktionierendes SSL-Zertifikat für Ihr Projekt hinzugefügt. Dieser Schritt ist oft der erste, um einen benutzerdefinierten Domain-Namen einzurichten.

* Informationen zum Einrichten eines benutzerdefinierten Domain-Namens finden Sie unter [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
* Informationen zum Aktualisieren und Verwalten Ihrer SSL-Zertifikate in Cloud Manager finden Sie unter [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

>[!TIP]
>
>Wenn Sie Probleme beim Hinzufügen oder Verwalten Ihrer Zertifikate haben, finden Sie weitere Informationen unter [Fehlerbehebung für SSL-Zertifikatfehler](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).
