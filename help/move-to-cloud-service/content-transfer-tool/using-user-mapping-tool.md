---
title: Verwenden des User Mapping Tools
description: Verwenden des User Mapping Tools
exl-id: 88ce7ed3-46fe-4b3f-8e18-c7c8423faf24
source-git-commit: 7d67bdb5e0571d2bfee290ed47d2d7797a91e541
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 80%

---

# Verwenden des User Mapping Tools {#user-mapping-tool}

## Übersicht {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="Mit dem Content Transfer Tool können Sie Anwender und Gruppen aus Ihrem vorhandenen AEM-System in AEM as a Cloud Service verschieben. Vorhandene Anwender und Gruppen müssen ihren IMS-IDs zugeordnet werden, um doppelte Anwender und Gruppen in der Cloud Service-Autoreninstanz zu vermeiden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#important-considerations" text="Wichtige Überlegungen zur Verwendung des User Mapping Tools"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#using-user-mapping-tool" text="Verwenden des User Mapping Tools"

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Sie Benutzer und Gruppen aus Ihrem bestehenden AEM-System in AEM as a Cloud Service überführen. Verwenden Sie hierzu das Content Transfer Tool.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene.  Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerprofilinformationen werden im Adobe Identity Management System (IMS) zentralisiert, das eine einmalige Anmeldung für alle Adobe Cloud-Programme ermöglicht. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung müssen bestehende Benutzer und Gruppen ihren IMS-IDs zugeordnet werden, um doppelte Benutzer und Gruppen in der Cloud Service-Autoreninstanz zu vermeiden.

### Benutzerzuordnungs-Tool {#mapping-tool}

Das Content Transfer Tool (ohne Benutzerzuordnung) migriert alle Benutzer und Gruppen, die mit dem migrierten Inhalt verknüpft sind. Das Tool für die Benutzerzuordnung ist Teil des Content Transfer-Tools und soll nur dazu dienen, die Benutzer und Gruppen so zu ändern, dass sie von IMS, der von AEM as a Cloud Service Single-Sign-On-Funktion, richtig erkannt werden. Sobald diese Änderungen vorgenommen wurden, migriert das Content Transfer Tool die Benutzer und Gruppen des angegebenen Inhalts wie gewohnt.

## Wichtige Überlegungen {#important-considerations}

### Ausnahmefälle {#exceptional-cases}

Die folgenden Sonderfälle werden protokolliert:

1. Wenn ein Benutzer keine E-Mail-Adresse im `profile/email`-Feld seines *jcr*-Knotens hat, wird der betreffende Benutzer oder die betreffende Gruppe migriert, jedoch nicht zugeordnet.

1. Wenn eine bestimmte E-Mail im Adobe Identity Management System (IMS) für die verwendete Organisations-ID nicht gefunden wird (oder wenn die IMS-ID aus einem anderen Grund nicht abgerufen werden kann), wird der betreffende Benutzer oder die betreffende Gruppe migriert, aber nicht zugeordnet.

1. Wenn der Benutzer derzeit deaktiviert ist, wird er genauso behandelt, als wäre er nicht deaktiviert. Er wird normal zugeordnet und migriert und bleibt in der Cloud-Instanz deaktiviert.

1. Wenn auf der Ziel-AEM Cloud Service-Instanz ein Benutzer mit demselben Benutzernamen (rep:principalName) wie einer der Benutzer in der Quell-AEM-Instanz vorhanden ist, wird der betreffende Benutzer oder die betreffende Gruppe nicht migriert.

### Weitere Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** festgelegt ist, werden bereits übertragene Benutzer in der Cloud Service-Instanz gelöscht und das gesamte vorhandene Repository wird neu erstellt, um Inhalte zu erfassen. Dadurch werden auch alle Einstellungen einschließlich der Berechtigungen für die Ziel-Cloud Service-Instanz zurückgesetzt. Dies gilt für einen Administrator, der der Gruppe **Administratoren** hinzugefügt wurde. Der Administrator muss der Gruppe **Administratoren** erneut hinzugefügt werden, um das Zugriffs-Token für CTT abzurufen.

* Es wird empfohlen, alle vorhandenen Benutzer aus der Ziel-AEM Cloud Service-Instanz zu entfernen, bevor CTT mit Benutzerzuordnung ausgeführt wird. Dies dient dazu, Konflikte zwischen migrierenden Benutzern der Quell-AEM-Instanz und der Ziel-AEM-Instanz zu vermeiden. Die Konflikte treten während der Aufnahme auf, wenn derselbe Benutzer in der Quell-AEM-Instanz und in der Zielgruppe-AEM-Instanz vorhanden ist.

* Wenn beim Auffüllen von Inhalten der Inhalt nicht übertragen wird, weil er sich seit der vorherigen Übertragung nicht geändert hat, werden auch die mit diesem Inhalt verknüpften Benutzer und Gruppen nicht übertragen, selbst wenn sich die Benutzer und Gruppen in der Zwischenzeit geändert haben. Dies liegt daran, dass Benutzer und Gruppen zusammen mit dem Inhalt, mit dem sie verknüpft sind, migriert werden.

* Wenn die AEM Cloud Service-Zielinstanz über einen Benutzer mit einem anderen Benutzernamen, aber derselben E-Mail-Adresse wie einer der Benutzer in der Quell-AEM-Instanz verfügt und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung in die Protokolle geschrieben und der Quell-AEM-Benutzer wird nicht übertragen, da nur ein Benutzer mit einer bestimmten E-Mail-Adresse im Zielsystem zulässig ist.

* Wenn zwei Benutzer in der Quell-AEM-Instanz dieselbe E-Mail-Adresse haben und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung in die Protokolle geschrieben und eine der Quell-AEM-Benutzer wird nicht übertragen, da nur ein Benutzer mit einer bestimmten E-Mail-Adresse im Zielsystem zulässig ist.


## Verwenden des User Mapping Tools {#using-user-mapping-tool}

Das User Mapping Tool verwendet eine API, über die Sie anhand der E-Mail-Adresse nach Benutzern im Adobe Identity Management System (IMS) suchen und ihre IMS-IDs zurückgeben können. Für diese API muss der Benutzer eine Client-ID für das Unternehmen, einen geheimen Client-Schlüssel und ein Zugriffs- oder Inhaber-Token erstellen.

Führen Sie die nachfolgenden Schritte aus, um dieses einzurichten:

1. Öffnen Sie mit Ihrer Adobe ID die [Adobe Developer Console](https://console.adobe.io).
1. Erstellen Sie ein neues Projekt oder öffnen Sie ein vorhandenes.
1. API hinzufügen - Klicken Sie auf **Zum Projekt hinzufügen** und wählen Sie **API** aus.
1. Wählen Sie „User Management API“.  Möglicherweise müssen Sie Berechtigungen für diese Option erhalten.
1. Erstellen Sie JWT-Anmeldedaten.
1. Generieren Sie ein Schlüsselpaar oder laden Sie einen öffentlichen Schlüssel hoch (RSA ist nicht empfehlenswert).  Es gibt eine Schaltfläche, **Generieren Sie ein öffentliches/privates Keypair**, das dies für Sie tun wird.  Achten Sie darauf, sowohl die öffentlichen als auch die privaten Schlüssel zu speichern.
1. Navigieren Sie zur User Management-API.
1. Generieren Sie ein Zugriffstoken (oder Trägertoken), indem Sie den Inhalt des privaten Schlüssels in das Textfeld einfügen und auf **Generate Token** klicken.
1. Speichern Sie alle diese Informationen wie **Client-ID**, **geheimen Client-Schlüssel**, **ID des technischen Kontos**, **E-Mail-Adresse des technischen Kontos**, **Organisations-ID** und **Zugriffs-Token** sicher.

## Benutzeroberfläche {#user-interface}

Das User Mapping Tool ist in das Content Transfer Tool integriert. Sie können das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunterladen. Weitere Informationen zur neuesten Version finden Sie in den [Aktuellen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Inhaltstransfer**.
1. Klicken Sie auf **Create User Mapping Config**.

   >[!NOTE]
   >Wenn Sie diesen Schritt überspringen, wird die Zuordnung von Benutzern und Gruppen während der Extraktion übersprungen.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-1.png)

   Füllen Sie die Felder in „User Management API Configuration“ wie unten beschrieben aus:

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-2.png)

   * **Org ID**: Geben Sie die Organisations-ID aus dem Adobe Identity Management System (IMS) für das Unternehmen ein, deren Anwender migriert werden.

      >[!NOTE]
      >Um die Organisations-ID abzurufen, melden Sie sich bei der [Admin Console](https://adminconsole.adobe.com/) an und wählen Sie rechts oben Ihr Unternehmen, wenn Sie zu mehren gehören. Die Organisations-ID befindet sich in der URL der Seite und hat das Format `xx@AdobeOrg`, wobei xx die IMS-Organisations-ID ist.  Alternativ können Sie die Organisations-ID auf der Seite [Adobe Developer Console](https://console.adobe.io) suchen, auf der Sie das Zugriffs-Token generieren.

   * **Client ID**: Geben Sie die Client-ID ein, die Sie im Setup-Schritt gespeichert haben.

   * **Access Token**: Geben Sie das Zugriffs-Token ein, das Sie im Setup-Schritt gespeichert haben.

      >[!NOTE]
      >Das Zugriffs-Token läuft alle 24 Stunden ab und muss dann neu erstellt werden. Um ein neues Token zu erstellen, gehen Sie zurück zur [Adobe Developer Console](https://console.adobe.io), wählen Sie Ihr Projekt aus, klicken Sie auf **User Management API** und fügen Sie denselben privaten Schlüssel in das Feld ein.

1. Klicken Sie nach Eingabe der obigen Informationen auf **Save**.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-3.png)


1. Erstellen Sie einen Migrationssatz, indem Sie auf **Create Migration Set** klicken, die Felder ausfüllen und dann auf **Save** klicken. Weitere Informationen finden Sie unter [Ausführen des Content Transfer Tools](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool).

   >[!NOTE]
   >Der Umschalter zum Einschließen der Zuordnung von Benutzern aus IMS-Benutzern und -Gruppen ist standardmäßig aktiviert. Bei dieser Einstellung wird das User Mapping Tool ggf. während der Extraktion für den Migrationssatz ausgeführt. Dies ist die empfohlene Methode zum Durchführen der Extraktion mit dem Content Transfer Tool. Wenn dieser Umschalter deaktiviert ist und/oder keine Benutzerzuordnungskonfiguration erstellt wurde, wird die Zuordnung von Benutzern und Gruppen während der Extraktion übersprungen.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-4.png)

1. Informationen zum Ausführen der Extraktion finden Sie unter [Ausführen des Content Transfer Tools](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool).
