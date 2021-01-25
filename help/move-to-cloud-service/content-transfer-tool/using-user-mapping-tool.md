---
title: Verwenden des Tools für die Benutzerzuordnung
description: Verwenden des Tools für die Benutzerzuordnung
translation-type: tm+mt
source-git-commit: 664c278494a5ac88362b994946060ab3baa846d8
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 7%

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