---
title: Native AEM Assets-Integration mit Adobe Expreß
description: Die native AEM Assets-Integration mit Adobe Expreß ermöglicht Ihnen den direkten Zugriff auf die in AEM Assets gespeicherten Assets über die Adobe Expreß-Benutzeroberfläche.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
source-git-commit: 8bbf9a2ba8f708a5a03d11bc0388d39b32d4c7b3
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 34%

---

# Native Integration mit Adobe Expreß {#native-integration-adobe-express}

AEM Assets lässt sich nativ in Adobe Expreß integrieren, sodass Sie direkt über die Adobe Expreß-Benutzeroberfläche auf die in AEM Assets gespeicherten Assets zugreifen können. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern. Die Integration bietet die folgenden Hauptvorteile:

* Verbesserte Wiederverwendung von Inhalten durch Bearbeiten und Speichern neuer Assets in AEM.

* Die Zeit und der Aufwand für das Erstellen neuer Assets oder das Erstellen neuer Versionen vorhandener Assets wurden insgesamt reduziert.

## Voraussetzungen {#prerequisites}

Berechtigungen für den Zugriff auf Adobe Expreß und mindestens eine Umgebung in AEM Assets. Die Umgebung kann eines der Repositorys in Assets as a Cloud Service oder Assets Essentials sein.


## Verwenden von AEM Assets im Adobe Express-Editor {#use-aem-assets-in-express}

Führen Sie die folgenden Schritte aus, um mit der Verwendung von AEM Assets im Adobe Expreß-Editor zu beginnen:

1. Öffnen Sie die Adobe Express-Web-Anwendung.

1. Öffnen Sie eine neue leere Arbeitsfläche, indem Sie eine neue Vorlage oder ein Projekt laden oder ein Asset erstellen.

1. Klicks **[!UICONTROL Assets]** im linken Navigationsbereich verfügbar. Adobe Expreß zeigt die Liste der Repositorys, auf die Sie Zugriff haben, zusammen mit der Liste der Assets und Ordner an, die auf der Stammebene verfügbar sind.

1. Durchsuchen oder suchen Sie Assets in Ihrem Repository, um sie per Drag &amp; Drop auf die Arbeitsfläche zu ziehen. Sie können Assets mit verschiedenen verfügbaren Filtern filtern, wie Dateityp, MIME-Typ und Dimensionen.

   ![Einschließen von Assets aus dem Assets-Add-on](assets/adobe-express-native-integration.png)


## Speichern von Adobe Express-Projekten in AEM Assets {#save-express-projects-in-assets}

Nachdem Sie entsprechende Änderungen in die Express-Arbeitsfläche eingefügt haben, können Sie sie im AEM Assets-Repository speichern.

1. Klicks **[!UICONTROL Freigeben]** , um die **[!UICONTROL Freigeben]** angezeigt.

   ![Speichern von Assets in AEM](assets/adobe-express-share.png)

1. Auswählen **[!UICONTROL AEM Assets]** aus dem **[!UICONTROL Speicherung]** im rechten Bereich verfügbar. Adobe Expreß zeigt das Dialogfeld &quot;Hochladen&quot;an.
1. Geben Sie einen Namen und ein Format für das Asset an. Sie können den Inhalt der Arbeitsfläche im PNG- oder JPEG-Format speichern.

1. Klicken Sie auf das Ordnersymbol neben dem Feld **[!UICONTROL Speicherort]**, navigieren Sie zu dem Speicherort, an dem Sie das Asset speichern müssen, und klicken Sie auf **[!UICONTROL Auswählen]**. Der Name des Ordners wird im Feld **[!UICONTROL Speicherort]** angezeigt.

   ![Speichern von Assets in AEM](assets/adobe-express-upload.png)

1. Optional: Sie können Kampagnenmetadaten für Ihren Upload mit dem **[!UICONTROL Projekt- oder Kampagnenname]** -Feld. Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Sie können mehrere Projekt- oder Kampagnennamen für Ihren Upload definieren. Wenn Sie einen Namen eingeben, klicken Sie entweder auf eine andere Stelle im Dialogfeld oder drücken Sie die `,` (Komma) Schlüssel zur Registrierung des Namens.

   Als Best Practice empfiehlt Adobe, Werte im Rest der Felder anzugeben und eine erweiterte Sucherfahrung für Ihre hochgeladenen Assets zu erstellen.
1. Definieren Sie auf ähnliche Weise Werte für die **[!UICONTROL Schlüsselwörter]** und **[!UICONTROL Kanäle]** -Felder.

1. Klicken Sie auf **[!UICONTROL Hochladen]**, um das Asset in AEM Assets hochzuladen.




## Einschränkungen {#limitations}

Es gibt einen bekannten Fehler bei einigen Benutzern mit Zugriff auf mehr als ein Asset-Repository, wenn ein Dokument mit Assets aus mehreren Repositorys gespeichert wird.
