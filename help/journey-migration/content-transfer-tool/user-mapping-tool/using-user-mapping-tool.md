---
title: Verwenden des User Mapping Tools
description: Verwenden des User Mapping Tools
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 50%

---


# Verwenden des User Mapping Tools {#using-user-mapping-tool}

Das User Mapping Tool verwendet eine API, über die Sie anhand der E-Mail-Adresse nach Benutzern im Adobe Identity Management System (IMS) suchen und ihre IMS-IDs zurückgeben können. Für diese API muss der Benutzer eine Client-ID für das Unternehmen, einen geheimen Client-Schlüssel und ein Zugriffs- oder Inhaber-Token erstellen.

## Einrichten des Benutzerzuordnungstools {#setting-up-user-mapping}

Führen Sie die nachfolgenden Schritte aus, um dieses einzurichten:

1. Öffnen Sie mit Ihrer Adobe ID die [Adobe Developer Console](https://console.adobe.io).
1. Erstellen Sie ein neues Projekt oder öffnen Sie ein vorhandenes.
1. API hinzufügen - Klicken Sie auf **Zum Projekt hinzufügen** und wählen Sie **API**
1. Wählen Sie „User Management API“.  Möglicherweise müssen Sie Berechtigungen für diese Option erhalten.
1. Erstellen Sie JWT-Anmeldedaten.
1. Generieren Sie ein Schlüsselpaar oder laden Sie einen öffentlichen Schlüssel hoch (RSA ist nicht empfehlenswert).  Es gibt eine Schaltfläche, **Generieren eines öffentlichen/privaten Keypairs**, die dies für Sie tun wird.  Achten Sie darauf, sowohl die öffentlichen als auch die privaten Schlüssel zu speichern.
1. Navigieren Sie zur User Management-API.
1. Generieren Sie ein Zugriffstoken (oder Trägertoken), indem Sie den Inhalt des privaten Schlüssels in das Textfeld einfügen und auf **Generate Token**.
1. Speichern Sie alle diese Informationen wie **Client-ID**, **geheimen Client-Schlüssel**, **ID des technischen Kontos**, **E-Mail-Adresse des technischen Kontos**, **Organisations-ID** und **Zugriffs-Token** sicher.

## Zugriff auf die Benutzeroberfläche für das Benutzerzuordnungs-Tool {#user-interface}

Das User Mapping Tool ist in das Content Transfer Tool integriert. Sie können das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunterladen. Weitere Informationen zur neuesten Version finden Sie in den [Aktuellen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Inhaltsmigration**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Klicken Sie auf **Benutzerzuordnung** Karte.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Klicken Sie auf **Create User Mapping Config**.

   >[!NOTE]
   >Wenn Sie diesen Schritt überspringen, wird die Zuordnung von Benutzern und Gruppen während der Extraktion übersprungen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Füllen Sie die Felder in **Konfiguration der User Management-API**, wie unten beschrieben.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **Org ID**: Geben Sie die Organisations-ID aus dem Adobe Identity Management System (IMS) für das Unternehmen ein, deren Anwender migriert werden.

      >[!NOTE]
      >Um die Organisations-ID abzurufen, melden Sie sich bei der [Admin Console](https://adminconsole.adobe.com/) an und wählen Sie rechts oben Ihr Unternehmen, wenn Sie zu mehren gehören. Die Organisations-ID befindet sich in der URL der Seite und hat das Format `xx@AdobeOrg`, wobei xx die IMS-Organisations-ID ist.  Alternativ können Sie die Organisations-ID auf der Seite [Adobe Developer Console](https://console.adobe.io) suchen, auf der Sie das Zugriffs-Token generieren.

   * **Client ID**: Geben Sie die Client-ID ein, die Sie im Setup-Schritt gespeichert haben.

   * **Access Token**: Geben Sie das Zugriffs-Token ein, das Sie im Setup-Schritt gespeichert haben.

      >[!NOTE]
      >Das Zugriffs-Token läuft alle 24 Stunden ab und muss dann neu erstellt werden. Um ein neues Token zu erstellen, gehen Sie zurück zur [Adobe Developer Console](https://console.adobe.io), wählen Sie Ihr Projekt aus, klicken Sie auf **User Management API** und fügen Sie denselben privaten Schlüssel in das Feld ein.

1. Klicken Sie nach dem Ausfüllen der Felder auf **Testen der Konfiguration** , um die Verbindung zum User Management-API-Dienst zu testen. Wenn die Verbindung erfolgreich hergestellt wurde, können Sie auf **Speichern** , um die Konfiguration zu speichern.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Wählen Sie nach dem Speichern der Konfiguration die Konfiguration aus und klicken Sie auf **Benutzerzuordnung starten**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Klicken Sie auf **Starten** aus dem Dialogfeld, um den Prozess &quot;Benutzerzuordnung&quot;zu starten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Sie zeigt die **Status** as **AUSFÜHRUNG**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Sobald die Benutzerzuordnung abgeschlossen ist, klicken Sie auf **Ergebnisse** um die Zusammenfassung anzuzeigen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* Sobald die Benutzerzuordnung abgeschlossen ist, können Sie mit der Breadcrumb-Leiste zurück zur Seite Inhaltsmigration navigieren. Auf der Karte Benutzerzuordnung werden der Status und der Zeitstempel angezeigt. Klicken Sie auf **Inhaltstransfer** , um einen Migrationssatz zu erstellen, um die Extraktion auszuführen. Siehe [Ausführen des Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool) für weitere Details.


### Fortsetzen des Prozesses für die Benutzerzuordnung {#resume-user-mapping-process}

Wenn der Prozess der Benutzerzuordnung aus einem der folgenden Gründe angehalten wird:

* Der ausgewählte Benutzer **Benutzerzuordnung stoppen**
* das Zugriffstoken während des Prozesses abgelaufen ist oder
* irgendein anderer Grund

   >[!NOTE]
   >Der Fortschritt wird an der Stelle gespeichert, an der der Prozess angehalten wurde.

Gehen Sie wie folgt vor, um den Prozess &quot;Benutzerzuordnung&quot;fortzusetzen:

1. Klicken Sie auf **Protokoll anzeigen** , um das Benutzerzuordnungsprotokoll zu überprüfen und den gespeicherten Fortschritt zu überprüfen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Klicken Sie auf **Benutzerzuordnung starten** erneut, um von der Stelle, an der sie aufgehört hat, wieder aufzunehmen.

   >[!NOTE]
   >Stellen Sie vor dem Neustart sicher, dass das Zugriffstoken weiterhin gültig ist oder aktualisiert wurde.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Klicken Sie auf **Starten** aus dem Dialogfeld, um den Prozess &quot;Benutzerzuordnung&quot;fortzusetzen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Sobald der Prozess der Benutzerzuordnung abgeschlossen ist, wird der **Status** as **FERTIG** für diese spezifische Konfiguration.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
