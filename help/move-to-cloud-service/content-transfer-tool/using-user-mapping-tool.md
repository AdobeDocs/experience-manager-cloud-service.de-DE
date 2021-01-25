---
title: Verwenden des Tools für die Benutzerzuordnung
description: Verwenden des Tools für die Benutzerzuordnung
translation-type: tm+mt
source-git-commit: 410b7900981596590fa80b286b40a965700f108e
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 6%

---


# Verwenden des Benutzerzuordnungstools {#user-mapping-tool}

## Überblick {#overview}

Als Teil der Transition-Journey zum AEM als Cloud Service müssen Sie Benutzer und Gruppen aus Ihrem bestehenden AEM als Cloud Service AEM. Dies erfolgt über das Inhaltsübermittlungstool.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene.  Dies erfordert die Verwendung des Adobe Admin Console zur Verwaltung von Benutzern und Benutzergruppen. Die Benutzerinformationen werden im Adobe Identity Management System (IMS) zentralisiert, das eine einmalige Anmeldung für alle Adobe Cloud-Anwendungen ermöglicht. Weitere Informationen finden Sie unter Identity Management. Aufgrund dieser Änderung müssen bestehende Benutzer und Gruppen ihren IMS-IDs zugeordnet werden, um Duplikat-Benutzer und -Gruppen in der Autoreninstanz des Cloud Service zu vermeiden.

## Wichtige Überlegungen {#important-considerations}

Es gibt einige außergewöhnliche Fälle, die in Betracht gezogen werden müssen. Die folgenden spezifischen Fälle werden protokolliert und der betreffende Benutzer bzw. die betreffende Gruppe wird nicht zugeordnet:

1. Wenn ein Benutzer keine E-Mail-Adresse im Feld `profile/email` seines jcr-Knotens hat.

1. Wenn im IMS-System keine bestimmte E-Mail für die verwendete Organisations-ID gefunden wird (oder wenn die IMS-ID aus einem anderen Grund nicht abgerufen werden kann).

1. Wenn der Benutzer derzeit deaktiviert ist, wird er genauso behandelt, als wäre er nicht deaktiviert.  Es wird als normal zugeordnet und migriert und bleibt in der Cloud-Instanz deaktiviert.

## Verwenden des Tools für die Benutzerzuordnung {#using-user-mapping-tool}

Das Benutzerzuordnungstool verwendet eine API, mit der IMS-Benutzer per E-Mail suchen und ihre IMS-IDs zurückgeben können. Für diese API muss der Benutzer eine Client-ID für sein Unternehmen, einen geheimen Clientschlüssel und ein Zugriffstoken-/InhaberToken erstellen.

Führen Sie die folgenden Schritte aus, um dies einzurichten:

1. Navigieren Sie mit Ihrem Adobe ID zu [Adobe Developer Console](https://console.adobe.io).
1. Neues Projekt erstellen oder vorhandenes Projekt öffnen
1. hinzufügen einer API
1. User Management-API auswählen
1. JWT-Berechtigung erstellen
1. Generieren Sie ein Schlüsselpaar oder Hochladen eines öffentlichen Schlüssels (rsa ist nicht gut)
1. Erstellen Sie ein Zugriffstoken (oder ein JWT-Token oder ein Inhabertoken).
1. Speichern Sie alle diese Informationen (Client-ID, geheimer Clientschlüssel, technische Konto-ID, E-Mail-Adresse des technischen Kontos, Organisations-ID, Zugriffstoken) an einem sicheren Ort.

## Benutzeroberfläche {#user-interface}

Das Tool zur Benutzerzuordnung ist in das Inhaltsübermittlungstool integriert. Sie können das Content Transfer Tool vom Software Distribution Portal herunterladen. Weitere Informationen zur neuesten Version finden Sie in den Versionshinweisen.

1. Wählen Sie &quot;Adobe Experience Manager auswählen&quot;und navigieren Sie zu &quot;tools -> **Operations** -> **Content Transfer**&quot;.
1. Klicken Sie auf **Benutzerzuordnungskonfiguration erstellen**.

   >[!NOTE]
   >Wenn Sie diesen Schritt überspringen, wird die Zuordnung von Benutzern und Gruppen während der Extraktion übersprungen.

   Füllen Sie die Felder in User Management API Configuration wie unten beschrieben aus:

   * **Organisations-ID**: Geben Sie die IMS-Organisations-ID für das Unternehmen ein, das migriert wird.

      >[!NOTE]
      >Um die Organisations-ID abzurufen, melden Sie sich bei der [Admin Console](https://adminconsole.adobe.com/) an und wählen Sie Ihr Unternehmen (im oberen rechten Bereich), wenn Sie zu mehr als einer gehören. Die Organisations-ID befindet sich in der URL der Seite im Format `xx@AdobeOrg`, wobei xx die IMS-Organisations-ID ist.  Alternativ können Sie die Organisations-ID auf der Seite [Adobe Developer Console](https://console.adobe.io) suchen, auf der Sie das Zugriffstoken generieren.

   * **Client-ID**: Geben Sie die Client-ID ein, die Sie im Setup-Schritt gespeichert haben

   * **Zugriffstoken**: Geben Sie das Zugriffstoken ein, das Sie im Setup-Schritt gespeichert haben

      >[!NOTE]
      >Das Zugriffstoken läuft alle 24 Stunden ab und es muss ein neues erstellt werden. Um ein neues Token zu erstellen, gehen Sie zurück zu [Adobe Developer Console](https://console.adobe.io), wählen Sie Ihr Projekt aus, klicken Sie auf User Management API und fügen Sie denselben privaten Schlüssel in das Feld ein.

1. Klicken Sie nach Eingabe der obigen Informationen auf Speichern.

1. Erstellen Sie ein Migrationsset, indem Sie auf &quot;Migrationsset erstellen&quot;klicken, die Felder ausfüllen und dann auf &quot;Speichern&quot;klicken. Weitere Informationen finden Sie unter Ausführen des Inhaltsübermittlungstools.

   >[!NOTE]
   >Der Umschalter zum Einschließen der Zuordnung von Benutzern aus IMS-Benutzern und -Gruppen ist standardmäßig aktiviert. Bei dieser Einstellung wird das Benutzerzuordnungstool während der Extraktion ausgeführt, wenn eine Extraktion für diesen Migrationssatz durchgeführt wird. Dies ist die empfohlene Methode zum Ausführen der Extraktion des Inhaltsübermittlungstools. Wenn dieser Umschalter deaktiviert ist und/oder keine Benutzerzuordnungskonfiguration erstellt wurde, wird die Zuordnung von Benutzern und Gruppen während der Extraktion übersprungen.

1. Informationen zum Ausführen der Extraktion finden Sie unter [Ausführen des Inhaltsübermittlungstools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool).



