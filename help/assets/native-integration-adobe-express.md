---
title: Native AEM Assets-Integration mit Adobe Express
description: Die native AEM Assets-Integration mit Adobe Express ermöglicht Ihnen den direkten Zugriff auf die in AEM Assets gespeicherten Assets über die Adobe Express-Benutzeroberfläche.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 18%

---

# Native Integration mit Adobe Express {#native-integration-adobe-express}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets-Entwicklerdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Dank der nativen Integration von AEM Assets mit Adobe Express können Sie über die Adobe Express-Benutzeroberfläche direkt auf die in AEM Assets gespeicherten Assets zugreifen. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern. Die Integration bietet die folgenden Hauptvorteile:

* Verbesserte Wiederverwendung von Inhalten durch Bearbeiten und Speichern neuer Assets in AEM.

* Die Zeit und der Aufwand für das Erstellen neuer Assets oder das Erstellen neuer Versionen vorhandener Assets wurden insgesamt reduziert.

## Voraussetzungen {#prerequisites}

Berechtigungen für den Zugriff auf Adobe Express und mindestens eine Umgebung in AEM Assets. Die Umgebung kann eines der Repositorys in Assets as a Cloud Service oder Assets Essentials sein.


## Verwenden von AEM Assets im Adobe Express-Editor {#use-aem-assets-in-express}

Führen Sie die folgenden Schritte aus, um mit der Verwendung von AEM Assets im Adobe Expreß-Editor zu beginnen:

1. Öffnen Sie die Adobe Express-Web-Anwendung.

2. Öffnen Sie eine neue leere Arbeitsfläche, indem Sie eine neue Vorlage oder ein Projekt laden oder ein Asset erstellen.

3. Klicken Sie im linken Navigationsbereich auf **[!UICONTROL Assets]** . Adobe Express zeigt die Liste der Repositorys, auf die Sie Zugriff haben, zusammen mit der Liste der Assets und Ordner an, die auf der Stammebene verfügbar sind.

4. Durchsuchen oder suchen Sie Assets in Ihrem Repository, um sie per Drag &amp; Drop auf die Arbeitsfläche zu ziehen. Sie können Assets mit verschiedenen verfügbaren Filtern filtern, wie Dateityp, MIME-Typ und Dimensionen.

   >[!NOTE]
   >
   >Die Filterung nach Dimension gilt nicht für Videos.

   ![Einschließen von Assets aus dem Assets-Add-on](assets/adobe-express-native-integration.png)


## Speichern von Adobe Express-Projekten in AEM Assets {#save-express-projects-in-assets}

Nachdem Sie entsprechende Änderungen in die Express-Arbeitsfläche eingefügt haben, können Sie sie im AEM Assets-Repository speichern.

1. Klicken Sie auf **[!UICONTROL Freigabe]** , um das Dialogfeld **[!UICONTROL Freigabe]** zu öffnen.

   ![Speichern von Assets in AEM](assets/adobe-express-share.png)

2. Wählen Sie im Bereich Speicher im rechten Bereich **AEM Assets** aus. Adobe Express zeigt das Dialogfeld &quot;Hochladen&quot;an.
3. Wählen Sie entweder **Aktuelle Seite** oder **Alle Seiten** aus. Geben Sie einen Namen und ein Format für die zu exportierenden Assets an. Sie können den Inhalt der Arbeitsfläche in die Formate PNG, JPEG, PDF, MP4, MP4+PNG oder MP4+JPEG exportieren. Das Format passt sich automatisch an die Assets auf der/den Leinwandseite(n) an.
Durch Auswahl von **Aktuelle Seite** wird das Asset auf Ihrer aktuellen Seite in Ihrem Zielordner gespeichert. Wenn Sie &quot;**Alle Seiten**&quot;auswählen und das Exportformat nicht &quot;PDF&quot;lautet, werden alle Leinwandseiten als separate Dateien in einem neuen Ordner in Ihrem Zielordner gespeichert. Wenn das Exportformat PDF ist, werden alle Leinwandseiten als einzelne PDF-Datei im Zielordner gespeichert.

4. Klicken Sie auf das Ordnersymbol unter &quot;**Zielordner**&quot;, um einen Speicherort auszuwählen und die Assets zu speichern.

   ![Speichern von Assets in AEM](/help/assets/assets/page-selection-and-destination-folder.svg)

5. Optional: Sie können mit dem Feld **Projekt- oder Kampagnenname** Kampagnenmetadaten für Ihren Upload hinzufügen. Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Sie können mehrere Projekt- oder Kampagnennamen für Ihren Upload definieren. Um den Namen zu registrieren, geben Sie einfach den Namen ein und drücken Sie die Eingabetaste.
Als Best Practice empfiehlt Adobe, Werte im Rest der Felder anzugeben und eine erweiterte Sucherfahrung für Ihre hochgeladenen Assets zu erstellen.

6. Definieren Sie auf ähnliche Weise Werte für die Felder **[!UICONTROL Suchbegriffe]** und **[!UICONTROL Kanäle]** .

7. Klicken Sie auf **[!UICONTROL Hochladen]** , um die Assets in AEM Assets hochzuladen.

## Einschränkungen {#limitations}

1. Für den Import und Export wird MP4 als Videodateityp unterstützt.

2. Für den MP4-Videoimport:

   1. Die maximal unterstützte Dateigröße beträgt 200 MB. Wenn dieser Grenzwert überschritten wird, wird eine Warnmeldung angezeigt.
   2. Die maximal unterstützte Auflösung beträgt 3840 x 3840 Pixel.
   3. Videos mit transparentem Hintergrund (Alphakanal) werden nicht unterstützt.

3. Für den MP4-Videoexport:

   1. Die maximal unterstützte Dateigröße beträgt 200 MB. Wenn dieser Grenzwert überschritten wird, wird ein Warnhinweis angezeigt, das Video auf 200 MB oder weniger zu reduzieren oder es nach dem Herunterladen manuell in den Zielordner von AEM Assets hochzuladen.



