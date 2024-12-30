---
title: Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
description: Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: e5fd1b351047213adbb83ef1d1722352958ce823
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---


# Verwendung des Tools für die Benutzerzuordnung (veraltete Version) {#using-user-mapping-tool}

>[!INFO]
>
>Diese Dokumentation bezieht sich auf eine veraltete Version des Tools. Weitere Informationen zur neuesten Version finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Das User Mapping Tool verwendet eine API, über die Sie anhand der E-Mail-Adresse nach Benutzern im Adobe Identity Management System (IMS) suchen und ihre IMS-IDs zurückgeben können. Für diese API muss der Benutzer eine Client-ID für das Unternehmen, einen geheimen Client-Schlüssel und ein Zugriffs- oder Inhaber-Token erstellen.

## Einrichten des Tools für die Benutzerzuordnung {#setting-up-user-mapping}

**Voraussetzung**: Für die Benutzerzuordnung muss jede Person, die ihrer IMS-ID zugeordnet werden soll, über eine E-Mail-Adresse in ihrem Profil in AEM und in IMS verfügen. Die Zuordnung für diese Person funktioniert selbst dann nicht, wenn sie eine E-Mail-Adresse als Benutzer-ID für die Anmeldung verwendet, es sei denn, die E-Mail-Adresse ist ebenfalls im Profil und auch in IMS enthalten.

Führen Sie die nachfolgenden Schritte aus, um dieses einzurichten:

1. Öffnen Sie mit Ihrer Adobe ID die [Adobe Developer Console](https://developer.adobe.com/console/).
1. Erstellen Sie ein Projekt oder öffnen Sie ein vorhandenes.
1. API hinzufügen – Klicken Sie auf **Zum Projekt hinzufügen** und wählen Sie **API** aus.
1. Wählen Sie „User Management API“. Sie müssen Systemadministrator-Berechtigungen besitzen, damit diese Option verfügbar ist.
1. Erstellen Sie JWT-Anmeldedaten.
1. Generieren Sie ein Schlüsselpaar oder laden Sie einen öffentlichen Schlüssel hoch (RSA ist nicht empfehlenswert). Es gibt eine Schaltfläche zum **Erzeugen eines öffentlich/privaten Schlüsselpaares**, die dieses Schlüsselpaar für Sie erstellt. Achten Sie darauf, sowohl die öffentlichen als auch die privaten Schlüssel zu speichern.
1. Gehen Sie zur User Management-API.
1. Erzeugen Sie ein Zugriffs-Token (oder Bearer-Token), indem Sie den Inhalt des privaten Schlüssels in das Textfeld einfügen und auf **Token erzeugen** klicken.
1. Speichern Sie alle diese Informationen wie **Client-ID**, **geheimen Client-Schlüssel**, **ID des technischen Kontos**, **E-Mail-Adresse des technischen Kontos**, **Organisations-ID** und **Zugriffs-Token** sicher.

## Zugriff auf die Benutzeroberfläche für das Tool für die Benutzerzuordnung {#user-interface}

Das User Mapping Tool ist in das Content Transfer Tool integriert. Sie können das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) herunterladen. Weitere Informationen zur neuesten Version finden Sie in den [Aktuellen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Inhaltsmigration**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Klicken Sie auf die Karte **Benutzerzuordnung**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Klicken Sie auf **Benutzerzuordnungskonfiguration erstellen**.

   >[!NOTE]
   >Wenn Sie diesen Schritt überspringen, wird die Zuordnung von Benutzenden und Gruppen während der Extraktion übersprungen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Füllen Sie die Felder in **Konfiguration der User Management-API** wie unten beschrieben aus.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **Org ID**: Geben Sie die Organisations-ID aus dem Adobe Identity Management System (IMS) für die Organisation ein, deren Benutzende migriert werden.

     >[!NOTE]
     >Um die Organisations-ID abzurufen, melden Sie sich bei [Admin Console](https://adminconsole.adobe.com/) an und wählen Sie (rechts oben) Ihre Organisation, wenn Sie nicht nur zu einer gehören. Die Organisations-ID befindet sich in der URL der Seite und hat das Format `xx@AdobeOrg`, wobei xx der IMS-Organisations-ID entspricht. Alternativ können Sie die Organisations-ID auf der Seite [Adobe Developer Console](https://developer.adobe.com/console/) suchen, auf der Sie das Zugriffs-Token generieren.

   * **Client ID**: Geben Sie die Client-ID ein, die Sie im Setup-Schritt gespeichert haben.

   * **Access Token**: Geben Sie das Zugriffs-Token ein, das Sie im Setup-Schritt gespeichert haben.

     >[!NOTE]
     >Das Zugriffs-Token läuft alle 24 Stunden ab und muss dann neu erstellt werden. Um ein Token zu erstellen, gehen Sie zurück zu [Adobe Developer Console](https://developer.adobe.com/console/), wählen Sie Ihr Projekt, klicken Sie auf **User Management-API** und fügen Sie denselben privaten Schlüssel in das Feld ein.

1. Klicken Sie nach dem Ausfüllen der Felder auf **Testkonfiguration**, um die Verbindung zum User Management-API-Service zu testen. Wenn die Verbindung erfolgreich hergestellt wurde, klicken Sie auf **Speichern**, um die Konfiguration zu speichern.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Wählen Sie nach dem Speichern der Konfiguration diese aus und klicken Sie auf **Benutzerzuordnung starten**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Klicken Sie im Dialogfeld auf **Starten**, um mit der Benutzerzuordnung zu beginnen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Der **Status** wird als **AUSFÜHRUNG** angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Sobald die Benutzerzuordnung abgeschlossen ist, klicken Sie auf **Ergebnisse**, um die Zusammenfassung anzuzeigen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >
   >* Nachdem die Benutzerzuordnung abgeschlossen ist, können Sie mit der Breadcrumb-Leiste zurück zur Seite „Inhaltsmigration“ navigieren. Auf der Karte „Benutzerzuordnung“ werden der Status und der Zeitstempel angezeigt. Klicken Sie auf **Inhaltstransfer**, damit Sie einen Migrationssatz erstellen können, um die Extraktion auszuführen. Weitere Informationen finden Sie unter [Ausführen des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#running-tool).

### Fortsetzen des Prozesses der Benutzerzuordnung {#resume-user-mapping-process}

Wenn der Prozess der Benutzerzuordnung aus einem der folgenden Gründe angehalten wird:

* Die Option **Benutzerzuordnung stoppen** wurde benutzerseitig ausgewählt.
* Das Zugriffs-Token ist während des Prozesses abgelaufen.
* Es liegt ein anderer Grund vor.

  >[!NOTE]
  >dort gespeichert, wo der Prozess gestoppt wurde.

Gehen Sie wie folgt vor, um den Prozess „Benutzerzuordnung“ fortzusetzen:

1. Klicken Sie auf **Protokoll anzeigen**, um das Benutzerzuordnungsprotokoll und darüber den gespeicherten Fortschritt zu überprüfen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Klicken Sie erneut auf die Schaltfläche **Benutzerzuordnung starten**, um sie von der Stelle, an der sie aufgehört hat, wieder aufzunehmen.

   >[!NOTE]
   >Stellen Sie vor dem Neustart sicher, dass das Zugriffstoken weiterhin gültig ist oder aktualisiert wurde.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Klicken Sie im Dialogfeld auf **Starten**, um den Prozess der Benutzerzuordnung fortzusetzen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Sobald der Prozess der Benutzerzuordnung abgeschlossen ist, wird der **Status** für diese spezifische Konfiguration als **BEENDET** angegeben.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
