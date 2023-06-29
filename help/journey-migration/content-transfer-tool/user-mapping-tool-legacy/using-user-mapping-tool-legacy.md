---
title: Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
description: Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 46%

---

# Verwenden des Benutzerzuordnungstools (alt) {#using-user-mapping-tool}

>[!INFO]
>
>Diese Dokumentation bezieht sich auf eine veraltete Version des Tools. Weitere Informationen zur neuesten Version finden Sie unter [Benutzerzuordnung und Hauptmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

Das User Mapping Tool verwendet eine API, über die Sie anhand der E-Mail-Adresse nach Benutzern im Adobe Identity Management System (IMS) suchen und ihre IMS-IDs zurückgeben können. Für diese API muss der Benutzer eine Client-ID für das Unternehmen, einen geheimen Client-Schlüssel und ein Zugriffs- oder Inhaber-Token erstellen.

## Einrichten des Tools für die Benutzerzuordnung {#setting-up-user-mapping}

**Voraussetzung**: Für die Benutzerzuordnung muss jede Person, die ihrer IMS-ID zugeordnet werden soll, über eine E-Mail-Adresse in ihrem Profil in AEM und in IMS verfügen. Selbst wenn der Benutzer eine E-Mail-Adresse als Benutzer-ID für die Anmeldung verwendet, funktioniert die Zuordnung für diesen Benutzer nur dann, wenn sich die E-Mail-Adresse auch im Profil und auch in IMS befindet.

Führen Sie die nachfolgenden Schritte aus, um dieses einzurichten:

1. Öffnen Sie mit Ihrer Adobe ID die [Adobe Developer Console](https://developer.adobe.com/console/).
1. Erstellen Sie ein Projekt oder öffnen Sie ein vorhandenes Projekt.
1. API hinzufügen – Klicken Sie auf **Zum Projekt hinzufügen** und wählen Sie **API** aus.
1. Wählen Sie „User Management API“. Sie müssen Systemadministrator-Berechtigungen besitzen, damit diese Option verfügbar ist.
1. Erstellen Sie JWT-Anmeldedaten.
1. Generieren Sie ein Schlüsselpaar oder laden Sie einen öffentlichen Schlüssel hoch (RSA ist nicht empfehlenswert). Es gibt eine Schaltfläche, **Generieren eines öffentlichen/privaten Keypairs** das dieses Keypair für Sie erstellt. Achten Sie darauf, sowohl die öffentlichen als auch die privaten Schlüssel zu speichern.
1. Gehen Sie zur User Management-API.
1. Generieren Sie ein Zugriffstoken (oder Trägertoken), indem Sie den Inhalt des privaten Schlüssels in das Textfeld einfügen und auf **Generate Token**.
1. Speichern Sie alle diese Informationen wie **Client-ID**, **geheimen Client-Schlüssel**, **ID des technischen Kontos**, **E-Mail-Adresse des technischen Kontos**, **Organisations-ID** und **Zugriffs-Token** sicher.

## Zugriff auf die Benutzeroberfläche für das Tool für die Benutzerzuordnung {#user-interface}

Das User Mapping Tool ist in das Content Transfer Tool integriert. Sie können das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunterladen. Weitere Informationen zur neuesten Version finden Sie unter [Aktuelle Versionshinweise](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Content-Migration**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Klicken Sie auf **Benutzerzuordnung** Karte.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Klicken **Erstellen der Konfiguration der Benutzerzuordnung**.

   >[!NOTE]
   >Wenn Sie diesen Schritt überspringen, wird die Benutzer- und Gruppenzuordnung während der Extraktionsphase übersprungen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Füllen Sie die Felder in **Konfiguration der User Management-API** wie unten beschrieben aus.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **Organisations-ID**: Geben Sie die Adobe Identity Management System (IMS)-Organisations-ID für die Organisation ein, die migriert wird.

     >[!NOTE]
     >Um die Organisations-ID abzurufen, melden Sie sich bei der [Admin Console](https://adminconsole.adobe.com/) und wählen Sie Ihre Organisation (oben rechts) aus, wenn Sie mehreren Benutzern angehören. Die Organisations-ID befindet sich in der URL dieser Seite im Format `xx@AdobeOrg`, wobei xx die IMS-Organisations-ID ist. Alternativ können Sie die Organisations-ID auf der Seite [Adobe Developer Console](https://developer.adobe.com/console/) suchen, auf der Sie das Zugriffs-Token generieren.

   * **Client ID**: Geben Sie die Client-ID ein, die Sie im Setup-Schritt gespeichert haben.

   * **Access Token**: Geben Sie das Zugriffs-Token ein, das Sie im Setup-Schritt gespeichert haben.

     >[!NOTE]
     >Das Zugriffstoken läuft alle 24 Stunden ab und es muss ein neuer erstellt werden. Um ein Token zu erstellen, gehen Sie zurück zu [Adobe Developer-Konsole](https://developer.adobe.com/console/), wählen Sie Ihr Projekt aus, klicken Sie auf **User Management-API** und fügen Sie denselben privaten Schlüssel in das Feld ein.

1. Klicken Sie nach dem Ausfüllen der Felder auf **Testen der Konfiguration** , um die Verbindung zum User Management-API-Dienst zu testen. Wenn die Verbindung erfolgreich hergestellt wurde, können Sie auf **Speichern** , um die Konfiguration zu speichern.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Wählen Sie nach dem Speichern der Konfiguration die Konfiguration aus und klicken Sie auf **Benutzerzuordnung starten**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Klicken **Starten** aus dem Dialogfeld, damit Sie den Prozess &quot;Benutzerzuordnung&quot;starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Der **Status** wird als **AUSFÜHRUNG** angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Nachdem die Benutzerzuordnung abgeschlossen ist, klicken Sie auf **Ergebnisse** um die Zusammenfassung anzuzeigen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >
   >* Nachdem die Benutzerzuordnung abgeschlossen ist, können Sie mit der Breadcrumb-Leiste zurück zur Seite Inhaltsmigration navigieren. Auf der Karte „Benutzerzuordnung“ werden der Status und der Zeitstempel angezeigt. Klicken **Inhaltstransfer** , damit Sie einen Migrationssatz erstellen können, um die Extraktion auszuführen. Siehe [Ausführen des Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#running-tool) für weitere Details.

### Fortsetzen des Prozesses der Benutzerzuordnung {#resume-user-mapping-process}

Wenn der Prozess der Benutzerzuordnung aus einem der folgenden Gründe angehalten wird:

* Die Option **Benutzerzuordnung stoppen** vom Benutzer ausgewählt wurde.
* Das Zugriffstoken ist während des Prozesses abgelaufen.
* Oder ein anderer Grund.

  >[!NOTE]
  >dort gespeichert, wo der Prozess gestoppt wurde.

Gehen Sie wie folgt vor, um den Prozess „Benutzerzuordnung“ fortzusetzen:

1. Klicken **Protokoll anzeigen** , um das Benutzerzuordnungsprotokoll zu überprüfen, damit Sie den gespeicherten Fortschritt überprüfen können.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Klicken **Benutzerzuordnung starten** erneut, um von der Stelle, an der sie aufgehört hat, wieder aufzunehmen.

   >[!NOTE]
   >Stellen Sie vor dem Neustart sicher, dass das Zugriffstoken weiterhin gültig ist oder aktualisiert wurde.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Klicken **Starten** aus dem Dialogfeld, damit Sie den Prozess &quot;Benutzerzuordnung&quot;fortsetzen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Nach Abschluss des Prozesses für die Benutzerzuordnung können Sie die **Status** as **FERTIG** für diese spezifische Konfiguration.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
