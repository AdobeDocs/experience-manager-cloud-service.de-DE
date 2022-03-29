---
title: Bekannte Probleme und Einschränkungen
description: Bekannte Probleme und Einschränkungen der  [!DNL AEM Forms] as a Cloud Service-Umgebung
contentOwner: khsingh
role: User, Developer
level: Intermediate
topic: Administration
exl-id: 871f294d-f251-4966-a021-39df65b613f0
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 100%

---

# Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

Bevor Sie mit der Nutzung von [!DNL AEM Forms] as a Cloud Service beginnen, machen Sie sich mit folgenden bekannten Problemen und Einschränkungen vertraut:

## Bekannte Probleme {#known-issues}

* Bis auf Weiteres sollten Sie keinen Test hinzufügen und ausführen, der ein adaptives Formular von einer Veröffentlichungsinstanz an einen AEM-Workflow übermittelt, der auf einer Autoreninstanz ausgeführt wird.

* Wenn Sie ein adaptives Formular importieren, das eine Vorlage mit der Schaltfläche **[!UICONTROL Speichern]** verwendet, wird die Schaltfläche **[!UICONTROL Speichern]** auch nach dem Entfernen aus der entsprechenden Vorlage weiterhin im adaptiven Formular angezeigt. Entfernen Sie die Schaltfläche **[!UICONTROL Speichern]** aus dem adaptiven Formular, bevor Sie es veröffentlichen. Beachten Sie die Versionshinweise zur Verfügbarkeit des Formularportals und der Funktion „Als Entwurf speichern“, um die Schaltfläche wiederherzustellen und zu verwenden.

* Der Schritt **[!UICONTROL Variable festlegen]** in AEM-Workflows unterstützt keine Variablen vom Typ „Array-Liste“. Sie können den Prozessschritt verwenden, um Variablen vom Typ „Array-Liste“ festzulegen.

* Wenn Sie ein adaptives Formular mit einem standardmäßigen HTML-Upload-Feld von einem Apple iOS-Gerät senden, wird der Inhalt der Datei nicht gesendet und am anderen Ende wird eine Datei mit 0 Byte empfangen. Das Problem tritt gelegentlich und nur bei Verwendung der synchronen Übermittlung auf. Dies ist ein [bekanntes Problem](https://feedbackassistant.apple.com/feedback/9117687) in Apple iOS.

* Wenn Sie ein Formular mit einem standardmäßigen HTML-Upload-Feld von einem Apple iOS-Gerät senden, wird manchmal der Inhalt der Datei nicht gesendet und am anderen Ende wird eine Datei mit 0 Byte empfangen. Dies ist ein bekanntes Problem in Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)


## Beschränkungen {#limitations}

* Die Unterstützung für XFA-basierte adaptive Formulare ist nicht standardmäßig. Wenn Sie XFA-basierte adaptive Formulare verwenden möchten, wenden Sie sich mit den Details zu Ihrem Anwendungsfall und den spezifischen Anforderungen an den Adobe-Support.

