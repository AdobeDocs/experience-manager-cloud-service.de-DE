---
title: Native Integration von AEM Assets in Adobe Express
description: Durch die native Integration von AEM Assets in Adobe Express können Sie über die Adobe Express-Benutzeroberfläche direkt auf die in AEM Assets gespeicherten Assets zugreifen.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '635'
ht-degree: 100%

---

# Native Integration in Adobe Express {#native-integration-adobe-express}

Dank der nativen Integration von AEM Assets mit Adobe Express können Sie über die Adobe Express-Benutzeroberfläche direkt auf die in AEM Assets gespeicherten Assets zugreifen. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern. Die Integration bietet vor allem die folgenden Vorteile:

* Verbesserte Wiederverwendung von Inhalten durch das Bearbeiten und Speichern neuer Assets in AEM.

* Verringerter Zeit- und Arbeitsaufwand beim Erstellen neuer Assets oder beim Erstellen neuer Versionen von vorhandenen Assets.

## Voraussetzungen {#prerequisites}

Es sind Berechtigungen für den Zugriff auf Adobe Express und mindestens eine Umgebung in AEM Assets erforderlich. Die Umgebung kann eines der Repositorys in Assets as a Cloud Service oder Assets Essentials sein.


## Verwenden von AEM Assets im Adobe Express-Editor {#use-aem-assets-in-express}

Führen Sie die folgenden Schritte aus, um mit der Verwendung von AEM Assets im Adobe Express-Editor zu beginnen:

1. Öffnen Sie die Adobe Express-Web-Anwendung.

2. Öffnen Sie eine neue leere Arbeitsfläche, indem Sie eine neue Vorlage oder ein Projekt laden oder ein Asset erstellen.

3. Klicken Sie im linken Navigationsbereich auf **[!UICONTROL Assets]**. Adobe Express zeigt die Liste der Repositorys an, auf die Sie Zugriff haben, zusammen mit der Liste der Assets und Ordner, die auf der Stammebene verfügbar sind.

4. Durchsuchen oder suchen Sie Assets in Ihrem Repository, um sie per Drag-and-Drop auf die Arbeitsfläche zu ziehen. Sie können Assets mit verschiedenen verfügbaren Filtern filtern, wie Dateityp, MIME-Typ und Dimensionen.

   >[!NOTE]
   >
   >Das Filtern nach Dimension gilt nicht für Videos.

   ![Einschließen von Assets aus dem Assets-Add-on](assets/adobe-express-native-integration.png)


## Speichern von Adobe Express-Projekten in AEM Assets {#save-express-projects-in-assets}

Nachdem Sie entsprechende Änderungen in die Express-Arbeitsfläche eingefügt haben, können Sie sie im AEM Assets-Repository speichern.

1. Klicken Sie auf **[!UICONTROL Freigeben]**, um das Dialogfeld **[!UICONTROL Freigeben]** zu öffnen.

   ![Speichern von Assets in AEM](assets/adobe-express-share.png)

2. Wählen Sie im rechten Bereich im Abschnitt „Speicher“ **AEM Assets** aus. Adobe Express zeigt das Dialogfeld „Hochladen“ an.
3. Wählen Sie entweder **Aktuelle Seite** oder **Alle Seiten** aus. Geben Sie einen Namen und ein Format für die Assets an, die exportiert werden sollen. Sie können die Inhalte der Arbeitsfläche in die folgenden Formate exportieren: PNG, JPEG, PDF, MP4, MP4+PNG oder MP4+JPEG. Das Format passt sich basierend auf den Assets automatisch an die Seite(n) der Arbeitsfläche an.
Durch Auswahl von **Aktuelle Seite** wird das Asset auf Ihrer aktuellen Seite in Ihrem Zielordner gespeichert. Wenn Sie **Alle Seiten** auswählen und das Exportformat nicht „PDF“ lautet, werden alle Seiten der Arbeitsfläche als separate Dateien in einem neuen Ordner in Ihrem Zielordner gespeichert. Wenn das Exportformat „PDF“ lautet, werden alle Seiten der Arbeitsfläche als eine einzige PDF-Datei im Zielordner gespeichert.

4. Klicken Sie auf das Ordnersymbol unter „**Zielordner**“, um einen Speicherort auszuwählen und die Assets zu speichern.

   ![Speichern von Assets in AEM](/help/assets/assets/page-selection-and-destination-folder.svg)

5. Optional: Sie können mit dem Feld **Projekt- oder Kampagnenname** Kampagnen-Metadaten für Ihren Upload hinzufügen. Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Sie können mehrere Projekt- oder Kampagnennamen für Ihren Upload definieren. Geben Sie zum Registrieren des Namens einfach den Namen ein und drücken Sie die Eingabetaste.
Adobe empfiehlt als Best Practice, in den restlichen Feldern Werte anzugeben sowie ein verbessertes Sucherlebnis für Ihre hochgeladenen Assets zu schaffen.

6. Definieren Sie auf ähnliche Weise Werte für die Felder **[!UICONTROL Keywords]** und **[!UICONTROL Kanäle]**.

7. Klicken Sie auf **[!UICONTROL Hochladen]**, um die Assets in AEM Assets hochzuladen.

## Einschränkungen {#limitations}

1. Für den Import und Export wird MP4 als Videodateityp unterstützt.

2. Für den Import von MP4-Videos:

   1. Die maximal unterstützte Dateigröße beträgt 200 MB. Bei Überschreiten dieses Grenzwerts wird eine Warnmeldung angezeigt.
   2. Die maximal unterstützte Auflösung beträgt 3840 x 3840 Pixel.
   3. Videos mit transparentem Hintergrund (Alphakanal) werden nicht unterstützt.

3. Für den Export von MP4-Videos:

   1. Die maximal unterstützte Dateigröße beträgt 200 MB. Bei Überschreiten dieses Grenzwerts wird ein Warnhinweis angezeigt, das Video auf 200 MB oder weniger zu reduzieren oder es nach dem Herunterladen manuell in den Zielordner in AEM Assets hochzuladen.



