---
title: Verwenden des User Mapping Tools (Frühere Version)
description: Verwenden des Benutzerzuordnungs-Tools (veraltet)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
source-git-commit: fb961ee6c369f5488deb794892caf9785d6b3068
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 91%

---

# Verwenden des User Mapping Tools {#using-user-mapping-tool}

Das User Mapping Tool verwendet eine API, über die Sie anhand der E-Mail-Adresse nach Benutzern im Adobe Identity Management System (IMS) suchen und ihre IMS-IDs zurückgeben können. Für diese API muss der Benutzer eine Client-ID für das Unternehmen, einen geheimen Client-Schlüssel und ein Zugriffs- oder Inhaber-Token erstellen.

## Einrichten des Tools für die Benutzerzuordnung {#setting-up-user-mapping}

**Voraussetzung:** Für die Benutzerzuordnung muss jeder Benutzer seiner IMS-ID zugeordnet sein, in seinem Profil in AEM und in IMS über eine E-Mail-Adresse verfügen.  Beachten Sie, dass die Zuordnung für diesen Benutzer selbst dann nicht funktioniert, wenn der Benutzer eine E-Mail-Adresse als Benutzer-ID für die Anmeldung verwendet, es sei denn, die E-Mail-Adresse ist ebenfalls im Profil und auch in IMS enthalten.

Führen Sie die nachfolgenden Schritte aus, um dieses einzurichten:

1. Öffnen Sie mit Ihrer Adobe ID die [Adobe Developer Console](https://console.adobe.io).
1. Erstellen Sie ein neues Projekt oder öffnen Sie ein vorhandenes.
1. API hinzufügen – Klicken Sie auf **Zum Projekt hinzufügen** und wählen Sie **API** aus.
1. Wählen Sie „User Management API“. Sie müssen Systemadministrator-Berechtigungen besitzen, damit diese Option verfügbar ist.
1. Erstellen Sie JWT-Anmeldedaten.
1. Generieren Sie ein Schlüsselpaar oder laden Sie einen öffentlichen Schlüssel hoch (RSA ist nicht empfehlenswert).  Es gibt eine Schaltfläche **Erzeugen eines öffentlich/privaten Schlüsselpaares**, die dies für Sie erledigen kann. Achten Sie darauf, sowohl die öffentlichen als auch die privaten Schlüssel zu speichern.
1. Gehen Sie zur User Management-API.
1. Erzeugen Sie ein Zugriffstoken (oder Bearer-Token), indem Sie den Inhalt des privaten Schlüssels in das Textfeld einfügen und auf **Token erzeugen** klicken.
1. Speichern Sie alle diese Informationen wie **Client-ID**, **geheimen Client-Schlüssel**, **ID des technischen Kontos**, **E-Mail-Adresse des technischen Kontos**, **Organisations-ID** und **Zugriffs-Token** sicher.

## Zugriff auf die Benutzeroberfläche für das Tool für die Benutzerzuordnung {#user-interface}

Das User Mapping Tool ist in das Content Transfer Tool integriert. Sie können das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunterladen. Weitere Informationen zur neuesten Version finden Sie in den [Aktuellen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Content-Migration**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Klicken Sie auf die Karte **Benutzerzuordnung**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Klicken Sie auf **Create User Mapping Config**.

   >[!NOTE]
   >Wenn Sie diesen Schritt überspringen, wird die Zuordnung von Benutzern und Gruppen während der Extraktion übersprungen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Füllen Sie die Felder in **Konfiguration der User Management-API** wie unten beschrieben aus.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **Org ID**: Geben Sie die Organisations-ID aus dem Adobe Identity Management System (IMS) für das Unternehmen ein, deren Anwender migriert werden.

      >[!NOTE]
      >Um die Organisations-ID abzurufen, melden Sie sich bei der [Admin Console](https://adminconsole.adobe.com/) an und wählen Sie rechts oben Ihr Unternehmen, wenn Sie zu mehren gehören. Die Organisations-ID befindet sich in der URL der Seite und hat das Format `xx@AdobeOrg`, wobei xx die IMS-Organisations-ID ist.  Alternativ können Sie die Organisations-ID auf der Seite [Adobe Developer Console](https://console.adobe.io) suchen, auf der Sie das Zugriffs-Token generieren.

   * **Client ID**: Geben Sie die Client-ID ein, die Sie im Setup-Schritt gespeichert haben.

   * **Access Token**: Geben Sie das Zugriffs-Token ein, das Sie im Setup-Schritt gespeichert haben.

      >[!NOTE]
      >Das Zugriffs-Token läuft alle 24 Stunden ab und muss dann neu erstellt werden. Um ein neues Token zu erstellen, gehen Sie zurück zur [Adobe Developer Console](https://console.adobe.io), wählen Sie Ihr Projekt aus, klicken Sie auf **User Management API** und fügen Sie denselben privaten Schlüssel in das Feld ein.

1. Klicken Sie nach dem Ausfüllen der Felder auf **Testen der Konfiguration**, um die Verbindung zum User Management-API-Service zu testen. Wenn die Verbindung erfolgreich hergestellt wurde, können Sie auf **Speichern** klicken, um die Konfiguration zu speichern.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Wählen Sie nach dem Speichern der Konfiguration diese aus und klicken Sie auf **Benutzerzuordnung starten**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Klicken Sie im Dialogfeld auf **Starten**, um den Prozess „Benutzerzuordnung“ zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Der **Status** wird als **AUSFÜHRUNG** angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Sobald die Benutzerzuordnung abgeschlossen ist, klicken Sie auf **Ergebnisse**, um die Zusammenfassung anzuzeigen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* Sobald die Benutzerzuordnung abgeschlossen ist, können Sie mit der Breadcrumb-Leiste zurück zur Seite „Inhaltsmigration“ wechseln. Auf der Karte „Benutzerzuordnung“ werden der Status und der Zeitstempel angezeigt. Klicken Sie auf **Inhaltstransfer**, um einen Migrationssatz zu erstellen und die Extraktion auszuführen. Weitere Informationen finden Sie unter [Ausführen des Content Transfer-Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#running-tool).


### Fortsetzen des Prozesses der Benutzerzuordnung {#resume-user-mapping-process}

Wenn der Prozess der Benutzerzuordnung aus einem der folgenden Gründe angehalten wird:

* Der Benutzer hat die Option **Benutzerzuordnung stoppen** gewählt,
* das Zugriffstoken ist während des Prozesses abgelaufen oder
* der Fortschritt wird aus einem anderen Grund

   >[!NOTE]
   >dort gespeichert, wo der Prozess gestoppt wurde.

Gehen Sie wie folgt vor, um den Prozess „Benutzerzuordnung“ fortzusetzen:

1. Klicken Sie auf **Protokoll anzeigen**, um das Benutzerzuordnungsprotokoll zu überprüfen und den gespeicherten Fortschritt zu überprüfen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Klicken Sie erneut auf die Schaltfläche **Benutzerzuordnung starten**, um sie von der Stelle, an der sie aufgehört hat, wieder aufzunehmen.

   >[!NOTE]
   >Stellen Sie vor dem Neustart sicher, dass das Zugriffstoken weiterhin gültig ist oder aktualisiert wurde.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Klicken Sie im Dialogfeld auf **Starten**, um den Prozess der Benutzerzuordnung wieder aufzunehmen.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Sobald der Prozess der Benutzerzuordnung abgeschlossen ist, wird der **Status** für diese spezifische Konfiguration als **FERTIG** angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
