---
title: Verwalten von digitalen Asset-Sammlungen
description: Machen Sie sich mit dem Konzept der Sammlung in Adobe Experience Manager Assets vertraut. Erfahren Sie, wie Sie Sammlungen verwalten, bearbeiten und mit anderen Benutzern teilen können.
contentOwner: AG
mini-toc-levels: 1
feature: Collections,Asset Management
role: User
exl-id: b0798adc-56a4-4577-b4ee-8d1fca3bff09
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '2400'
ht-degree: 81%

---

# Verwalten von Sammlungen {#manage-collections}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-collections.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Eine Sammlung ist ein Satz von Assets innerhalb von Adobe Experience Manager Assets. Anhand von Sammlungen können Assets von mehreren Benutzern gemeinsam verwendet werden. Der Satz kann eine statische Sammlung oder eine dynamische Sammlung sein, die auf Suchergebnissen basiert.

Im Gegensatz zu Ordnern kann eine Sammlung Assets von verschiedenen Speicherorten enthalten. Sie können Sammlungen für verschiedene Benutzende freigeben, denen unterschiedliche Berechtigungsstufen zugewiesen sind, z. B. „Anzeigen“, „Bearbeiten“ usw.

Sie können mehrere Sammlungen für eine Benutzerin bzw. einen Benutzer freigeben. Jede Sammlung enthält Verweise auf Assets. Die referenzielle Integrität von Assets wird sammlungsübergreifend aufrechterhalten.

Sammlungen weisen die folgenden Typen auf, basierend auf der Art und Weise, wie sie Assets zusammenstellen:

* Eine Sammlung mit einer statischen Referenzliste von Assets, Ordnern und anderen Sammlungen.

* Eine Smart-Sammlung, die Assets auf Grundlage eines Suchkriteriums dynamisch verwendet.

## Aufrufen der Konsole „Sammlungen“ {#navigate-the-collections-console}

So öffnen Sie die Konsole **[!UICONTROL Sammlungen]**:

So öffnen Sie die **[!UICONTROL Sammlungen]**, wählen Sie das Experience Manager-Logo aus. Gehen Sie auf der Navigationsseite zu **[!UICONTROL Assets]** > **[!UICONTROL Sammlungen]**.

## Erstellen von Sammlungen {#create-a-collection}

Sie können eine Sammlung mit [statischen Referenzen](#create-a-collection-with-static-references) oder basierend auf einem [Suchkriterien-spezifischen Filter](#create-a-smart-collection) erstellen. Sie können eine Sammlung auch über eine Lightbox erstellen.

### Erstellen von Sammlungen mit statischen Referenzen {#create-a-collection-with-static-references}

Sie können eine Sammlung mit statischen Referenzen erstellen, z. B. eine Sammlung mit Referenzen zu Assets, Ordnern, Sammlungen, Rotationssets und Bildsets.

1. Navigieren Sie zur Konsole **[!UICONTROL Sammlungen]**.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Erstellen]**.
1. Geben Sie auf der Seite **[!UICONTROL Sammlung erstellen]** einen Titel und eine optionale Beschreibung für die Sammlung ein.
1. Fügen Sie Mitglieder zur Sammlung hinzu und weisen Sie entsprechende Berechtigungen zu. Wählen Sie alternativ **[!UICONTROL Öffentliche Sammlung]**, um allen Benutzern Zugriff auf die Sammlung zu ermöglichen.

   >[!NOTE]
   >
   >Um es Mitgliedern zu ermöglichen, Sammlungen mit anderen Benutzern zu teilen, gewähren Sie der Gruppe `dam-users` Leseberechtigungen für den Pfad `home/users`. Erteilen Sie den Benutzern eine Berechtigung für den Pfad `/content/dam/collections`, damit Benutzer Sammlungen in Popup-Listen anzeigen können. Alternativ dazu können Sie Benutzer auch in die Gruppe `dam-users` aufnehmen.

1. (Optional) Fügen Sie eine Miniatur für die Sammlung hinzu.
1. Auswählen **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL OK]** , um das Dialogfeld zu schließen. In der Konsole „Sammlungen“ wird eine Sammlung mit dem angegebenen Titel und ihren Eigenschaften geöffnet.

   >[!NOTE]
   >
   >Mit Experience Manager Assets können Sie Prüfungsaufgaben für eine Sammlung auf ähnliche Weise wie Prüfungsaufgaben für einen Assets-Ordner erstellen.

   Um Assets zur Sammlung hinzuzufügen, navigieren Sie zur Assets-Benutzeroberfläche. Weitere Informationen finden Sie unter [Hinzufügen von Assets zu einer Sammlung](#add-assets-to-a-collection).

### Erstellen von Sammlungen mithilfe der Dropzone {#create-collections-using-dropzone}

Sie können Assets aus der Assets-Benutzeroberfläche in eine Sammlung ziehen. Sie können auch eine Kopie einer Sammlung erstellen und Assets dort hinziehen.

1. Wählen Sie in der Assets-Benutzeroberfläche die Assets aus, die Sie zu einer Sammlung hinzufügen möchten.
1. Ziehen Sie die Assets in den Bereich **[!UICONTROL In Sammlung ablegen]**. Alternativ können Sie die **[!UICONTROL Zu Sammlung]** in der Symbolleiste.
1. Im **[!UICONTROL Zu Sammlung hinzufügen]** Seite, wählen Sie die **[!UICONTROL Sammlung erstellen]** in der Symbolleiste. Wenn Sie die Assets zu einer vorhandenen Sammlung hinzufügen möchten, wählen Sie sie auf der Seite aus und wählen Sie **[!UICONTROL Hinzufügen]**. Standardmäßig wird die zuletzt aktualisierte Sammlung ausgewählt.
1. Geben Sie im Dialogfeld **[!UICONTROL Neue Sammlung erstellen]** einen Namen für die Sammlung an. Wenn die Sammlung allen Benutzern zugänglich sein soll, wählen Sie **[!UICONTROL Öffentliche Sammlung]** aus.
1. Auswählen **[!UICONTROL Weiter]** , um die Sammlung zu erstellen.

### Erstellen von Smart-Sammlungen {#create-a-smart-collection}

Eine Smart-Sammlung verwendet Suchkriterien, um Assets dynamisch zu füllen. Sie können eine Smart-Sammlung nur mit Dateien und nicht mit Ordnern oder Dateien und Ordnern erstellen.

1. Navigieren Sie zur Assets-Benutzeroberfläche und wählen Sie die **[!UICONTROL Suche]** Symbol.
1. Geben Sie im OmniSearch-Feld das Keyword ein und drücken Sie die `Enter`-Taste. Wählen Sie das GlobalNav-Symbol aus, um den Bereich Filter anzuzeigen und einen Suchfilter aus dem Suchbereich anzuwenden.
1. Wählen Sie aus der Liste **[!UICONTROL Dateien und Ordner]** die Option **[!UICONTROL Dateien]** aus.
1. Auswählen **[!UICONTROL Intelligente Sammlung speichern]**.
1. Geben Sie einen Namen für die Sammlung an. Aktivieren Sie **[!UICONTROL Öffentlich]**, um die DAM-Benutzergruppe mit der Rolle „Betrachter“ zur Smart-Sammlung hinzuzufügen.

   >[!NOTE]
   >
   >Bei Auswahl von **[!UICONTROL Öffentlich]** wird die Smart-Sammlung nach der Erstellung für alle Benutzer mit der Eigentümerrolle verfügbar. Wenn Sie die Option **[!UICONTROL Öffentlich]** deaktivieren, ist die DAM-Benutzergruppe nicht mehr mit der Smart-Sammlung verknüpft.

1. Auswählen **[!UICONTROL Speichern]** , um die Smart-Sammlung zu erstellen, und schließen Sie dann das Meldungsfeld, um den Prozess abzuschließen. Die neue Smart-Sammlung wird auch zur Liste **[!UICONTROL Gespeicherte Suchen]** hinzugefügt.
Die Bezeichnung der Schaltfläche **[!UICONTROL Smart-Sammlung erstellen]** wird in **[!UICONTROL Smart-Sammlung bearbeiten]** geändert. Um die Einstellungen der Smart-Sammlung zu bearbeiten, wählen Sie **[!UICONTROL Dateien]** aus der Liste **[!UICONTROL Dateien und Ordner]** aus. Wählen Sie anschließend die **[!UICONTROL Smart-Auswahl bearbeiten]** Schaltfläche.

## Hinzufügen von Assets zu einer Sammlung {#add-assets-to-a-collection}

Sie können einer Sammlung mit einer Liste referenzierter Assets oder Ordner Assets hinzufügen.

>[!NOTE]
>
>Smart-Sammlungen verwenden eine Suchabfrage zum Ausfüllen von Assets. Daher sind statische Referenzen zu Assets und Ordnern für sie nicht anwendbar.

1. Navigieren Sie in der Assets-Benutzeroberfläche zum Speicherort des Assets, das Sie einer Sammlung hinzufügen möchten.
1. Wählen Sie das Asset aus und wählen Sie die **[!UICONTROL Zu Sammlung]** in der Symbolleiste. Alternativ können Sie das Asset in den Bereich **[!UICONTROL In Sammlung ablegen]** ziehen. Lassen Sie die Maustaste los, wenn die Dropzone aktiv wird und sich ihre Bezeichnung in **[!UICONTROL Zum Hinzufügen ablegen]** ändert.
1. Wählen Sie auf der Seite **[!UICONTROL Zu Sammlung hinzufügen]** die Sammlung aus, der Sie das Asset hinzufügen möchten.
1. Auswählen **[!UICONTROL Hinzufügen]** und schließen Sie dann die Bestätigungsmeldung. Das Asset wird zur Sammlung hinzugefügt.

## Bearbeiten von Smart-Sammlungen {#edit-a-smart-collection}

Smart-Sammlungen werden durch Speichern von Suchvorgängen erstellt. Das heißt, Sie können den Inhalt ändern, indem Sie die Suchparameter der [gespeicherten Suche](#saved-searches) ändern.

1. Wählen Sie in der Assets-Benutzeroberfläche das **[!UICONTROL Suche]** in der Symbolleiste.
1. Betätigen Sie bei in das OmniSearch-Feld gesetztem Cursor die `Enter`-Taste.
1. Wählen Sie das GlobalNav-Symbol aus, um den Bereich Filter anzuzeigen.
1. Wählen Sie in der Liste **[!UICONTROL Gespeicherte Suchen]** die Smart-Sammlung aus, die Sie ändern möchten. Im Suchbereich werden die für die gespeicherte Suche konfigurierten Filter angezeigt.
1. Wählen Sie aus der Liste **[!UICONTROL Dateien und Ordner]** die Option **[!UICONTROL Dateien]** aus.
1. Ändern Sie den bzw. die Filter nach Bedarf. Auswählen **[!UICONTROL Intelligente Sammlung bearbeiten]**. Sie können auch den Namen der Smart-Sammlung ändern.
1. Wählen Sie **[!UICONTROL Speichern]** aus. Das Dialogfeld **[!UICONTROL Smart-Sammlung bearbeiten]** wird angezeigt.
1. Auswählen **[!UICONTROL Überschreiben]** , um die ursprüngliche Smart-Sammlung durch die bearbeitete Sammlung zu ersetzen. Wählen Sie alternativ **[!UICONTROL Speichern unter]** aus, um die bearbeitete Sammlung separat zu speichern.
1. Wählen Sie im Bestätigungsdialogfeld **[!UICONTROL Speichern]** , um den Prozess abzuschließen.

## Anzeigen und Bearbeiten von Sammlungsmetadaten {#view-and-edit-collection-metadata}

Sammlungsmetadaten umfassen die Daten zur Sammlung, einschließlich aller hinzugefügten Tags.

1. Wählen Sie in der Konsole &quot;Sammlungen&quot;eine Sammlung aus und wählen Sie die **[!UICONTROL Eigenschaften]** in der Symbolleiste.
1. Zeigen Sie auf der Seite **[!UICONTROL Sammlungs-Metadaten]** die Metadaten der Sammlung auf den Registerkarten **[!UICONTROL Allgemein]** und **Erweitert** an.
1. Ändern Sie die Metadaten nach Bedarf und wählen Sie **[!UICONTROL Speichern und schließen]** aus der Symbolleiste, um die Änderungen zu speichern.

### Massenbearbeitung von Sammlungsmetadaten {#edit-collection-metadata-in-bulk}

Sie können die Metadaten mehrerer Sammlungen gleichzeitig bearbeiten. Mit dieser Funktion können Sie gängige Metadaten in mehreren Sammlungen schnell replizieren.

1. Wählen Sie in der Konsole „Sammlungen“ zwei oder mehr Sammlungen aus, für die Sie Metadaten bearbeiten möchten.
1. Wählen Sie in der Symbolleiste die **[!UICONTROL Eigenschaften]** Symbol.
1. Bearbeiten Sie auf der Seite **[!UICONTROL Sammlungs-Metadaten]** die Metadaten auf den Registerkarten **[!UICONTROL Allgemein]** und **[!UICONTROL Erweitert]** nach Bedarf.
1. Auswählen **[!UICONTROL Speichern und schließen]** aus der Symbolleiste und schließen Sie dann das Bestätigungsdialogfeld, um den Prozess abzuschließen.
1. Um die neuen Metadaten an die vorhandenen Metadaten anzuhängen, wählen Sie **[!UICONTROL Beifügemodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Klicken Sie auf **[!UICONTROL Übermitteln]**.

   >[!NOTE]
   >
   >Der Anlagenmodus funktioniert nur für Felder, die mehrere Werte enthalten können. Für Felder, die nur einen einzigen Wert enthalten können, werden neue Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie den **[!UICONTROL Anlagenmodus]** auswählen.

## Suchen {#searching}

Die Suchfunktion für Sammlungen unterstützt sowohl das [Suchen nach Sammlungen](#search-collections) als auch das [Suchen nach Assets in Sammlungen](#search-within-collections).

### Suchen nach Sammlungen {#search-collections}

Sie können mit der Konsole „Sammlungen“ nach Sammlungen suchen. Wenn Sie die Suche mit Keywords im Suchfeld durchführen, sucht [!DNL Experience Manager Assets] nach Sammlungsnamen, Sammlungsmetadaten und den Tags, die zu den Sammlungen hinzugefügt wurden.

Wenn Sie auf der obersten Ebene nach Sammlungen suchen, werden nur die einzelnen Sammlungen in den Suchergebnissen zurückgegeben. Assets oder Ordner innerhalb der Sammlungen sind ausgeschlossen. In allen anderen Fällen (z. B. innerhalb einer individuellen Sammlung oder in einer Ordnerhierarchie) werden alle relevanten Assets, Ordner und Sammlungen zurückgegeben.

### Suchen in Sammlungen {#search-within-collections}

Wählen Sie in der Konsole &quot;Sammlungen&quot;eine Sammlung aus, um sie zu öffnen.

Innerhalb einer Sammlung ist die Suche von [!DNL Experience Manager] auf Assets (sowie deren Tags und Metadaten) in der angezeigten Sammlung begrenzt. Wenn Sie in einem Ordner suchen, werden alle passenden Assets und untergeordneten Ordner innerhalb des aktuellen Ordners zurückgegeben. Wenn Sie in einer Sammlung suchen, werden nur übereinstimmende Assets, Ordner und andere Sammlungen zurückgegeben, die direkt zur Sammlung gehören.

## Bearbeiten von Sammlungseinstellungen {#edit-collection-settings}

Sie können Sammlungseinstellungen, wie z. B. Titel und Beschreibung, bearbeiten oder Mitglieder zu einer Sammlung hinzufügen.

1. Wählen Sie eine Sammlung aus und wählen Sie die **[!UICONTROL Einstellungen]** in der Symbolleiste. Verwenden Sie alternativ die Schnellaktion **[!UICONTROL Einstellungen]** in der Miniatur der Sammlung.
1. Ändern Sie die Sammlungseinstellungen auf der Seite **[!UICONTROL Einstellungen für Sammlung]**. Ändern Sie beispielsweise den Sammlungstitel, die Beschreibung, die Mitglieder und Berechtigungen wie in [Sammlungen hinzufügen](#create-a-collection) beschrieben.
1. Auswählen **[!UICONTROL Speichern]** , um die Änderungen zu speichern.

## Löschen von Sammlungen {#delete-a-collection}

1. Wählen Sie in der Konsole &quot;Sammlungen&quot;mindestens eine Sammlung aus und klicken Sie in der Symbolleiste auf das Symbol Löschen .
1. Wählen Sie im Dialogfeld **[!UICONTROL Löschen]** , um die Löschaktion zu bestätigen.

   >[!NOTE]
   >
   >Sie können Smart-Sammlungen auch löschen, indem Sie [gespeicherte Suchen löschen](#saved-searches).

## Herunterladen von Sammlungen {#download-a-collection}

Wenn Sie eine Sammlung herunterladen, wird die gesamte Asset-Hierarchie innerhalb der Sammlung ebenfalls heruntergeladen, einschließlich Ordnern und untergeordneten Sammlungen.

1. Wählen Sie in der Konsole „Sammlungen“ eine oder mehrere Sammlungen für den Download aus.
1. Wählen Sie in der Symbolleiste das Symbol Download aus.
1. Im **[!UICONTROL Herunterladen]** Dialogfeld auswählen **[!UICONTROL Herunterladen]**. Wählen Sie **[!UICONTROL Ausgabedarstellungen]** aus, wenn Sie die Ausgabedarstellungen des Assets in der Sammlung herunterladen möchten. <!-- Select the **[!UICONTROL Email]** option to send an email notification to the owner of the collection. -->

   Bei Auswahl einer Sammlung für den Download wird die gesamte Ordnerstruktur unter dieser Sammlung heruntergeladen. Um jede Sammlung (einschließlich Assets in untergeordneten Sammlungen, die unter der übergeordneten Sammlung verschachtelt sind), die Sie herunterladen, in einem eigenen Ordner zu speichern, wählen Sie **[!UICONTROL Separaten Ordner für jedes Asset erstellen]** aus.

## Bearbeiten von Metadateneigenschaften mehrerer Sammlungen {#editing-metadata-properties-of-multiple-collections}

Mit Adobe Enterprise Manager Assets können Sie die Metadaten vieler Sammlungen in Massen bearbeiten. Auf der Seite [!UICONTROL Eigenschaften] können Sie Metadatenänderungen an mehreren Sammlungen durchführen, beispielsweise Metadateneigenschaften in einen allgemeinen Wert ändern bzw. Tags hinzufügen oder ändern.

Verwenden Sie zum Anpassen der Seite mit den [!UICONTROL Eigenschaften] von Metadaten, einschließlich Hinzufügen, Ändern und Löschen von Metadateneigenschaften, den Schemaeditor.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einer Sammlung enthalten sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](/help/assets/search-assets.md#metadata-updates).

1. Wählen Sie in der Konsole „Sammlungen“ die Sammlungen aus, die Sie bearbeiten möchten.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Eigenschaften]** , um die [!UICONTROL Eigenschaften] für die ausgewählten Sammlungen.
1. Ändern Sie die Metadateneigenschaften für ausgewählte Sammlungen auf den verschiedenen Registerkarten.

   >[!NOTE]
   >
   >Die Metadaten, die Sie für die ausgewählten Sammlungen hinzufügen, überschreiben die vorherigen Metadaten für diese Sammlungen, außer für Tags. Alle Tags, die Sie im Feld **[!UICONTROL Tags]** hinzufügen, werden der vorhandenen Liste der Tags in den Metadaten anhängt.

1. Heben Sie die Auswahl der anderen Sammlungen in der Sammlungsliste auf, um die Metadateneigenschaften für eine bestimmte Sammlung anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für die bestimmte Sammlung gefüllt.

   >[!NOTE]
   >
   >* Auf der Sammlungseigenschaftenseite können Sie Sammlungen aus der Liste der Sammlungen entfernen, indem Sie die Auswahl aufheben. In der Sammlungsliste sind alle Sammlungen standardmäßig ausgewählt. Die Metadaten für Sammlungen, die Sie entfernen, werden nicht aktualisiert.
   >* Aktivieren Sie über der Sammlungsliste das Kontrollkästchen neben **[!UICONTROL Titel]**, um zwischen der Auswahl von Sammlungen und dem Deaktivieren der Liste umzuschalten.

1. Speichern Sie die Änderungen.

## Erstellen verschachtelter Sammlungen {#create-nested-collections}

Sie können eine Sammlung zu einer anderen Sammlung hinzufügen und so eine verschachtelte Sammlung erstellen.

1. Wählen Sie in der Konsole &quot;Sammlungen&quot;die gewünschte Sammlung oder Gruppe von Sammlungen aus und wählen Sie **[!UICONTROL Zu Sammlung]** in der Symbolleiste.
1. Wählen Sie auf der Seite **[!UICONTROL Zu Sammlung hinzufügen]** die Sammlung aus, der die Sammlung hinzugefügt werden soll.

   >[!NOTE]
   >
   >Die zuletzt aktualisierte Sammlung wird standardmäßig auf der Seite **[!UICONTROL Zu Sammlung hinzufügen]** ausgewählt.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**. Eine Meldung bestätigt, dass die Sammlung zur Zielsammlung auf der Seite **[!UICONTROL Ziel auswählen]** hinzugefügt wird. Schließen Sie die Meldung, um den Vorgang abzuschließen.

>[!NOTE]
>
>Smart-Sammlungen können nicht verschachtelt werden. Mit anderen Worten: Smart-Sammlungen können keine andere Sammlung enthalten.

## Gespeicherte Suchvorgänge {#saved-searches}

In der Assets-Benutzeroberfläche können Sie Assets basierend auf bestimmten Regeln, Suchkriterien oder benutzerdefinierten Suchfacetten durchsuchen oder filtern. Wenn Sie diese Einstellungen als **[!UICONTROL Gespeicherte Suchen]** speichern, können Sie später in der Liste **[!UICONTROL Gespeicherte Suchen]** im Filterbereich darauf zugreifen. Beim Erstellen einer gespeicherten Suche wird auch eine Smart-Sammlung erstellt.

Gespeicherte Suchen werden erstellt, wenn Sie eine Smart-Sammlung erstellen. Smart-Sammlungen werden automatisch der Liste **[!UICONTROL Gespeicherte Suchen]** hinzugefügt. Die Abfrage der gespeicherten Suche für die Sammlung wird in der Eigenschaft `dam:query` in CRXDE unter dem relativen Speicherort `/content/dam/collections/` gespeichert. Die Suchen, die Sie speichern können, und die gespeicherten Suchen, die in der Liste angezeigt werden, sind unbegrenzt.

>[!NOTE]
>
>Sie können Smart-Sammlungen auf gleiche Weise wie statische Sammlungen freigeben.

Gespeicherte Suchen werden genauso wie Smart-Sammlungen bearbeitet. Einzelheiten dazu finden Sie unter [Bearbeiten von Smart-Sammlungen](#edit-a-smart-collection).

Gehen Sie wie folgt vor, um gespeicherte Suchen zu löschen:

1. Wählen Sie in der Assets-Benutzeroberfläche in der Symbolleiste das Suchsymbol aus.

1. Betätigen Sie bei in das OmniSearch-Feld gesetztem Cursor die `Enter`-Taste.
1. Wählen Sie das GlobalNav-Symbol aus, um den Bereich Filter anzuzeigen.
1. Aus dem **[!UICONTROL Gespeicherte Suchen]** Liste auswählen **[!UICONTROL Löschen]** neben der Smart-Sammlung, die Sie löschen möchten.
1. Wählen Sie im Dialogfeld **[!UICONTROL Löschen]** , um die gespeicherte Suche zu löschen.

## Ausführen eines Workflows für eine Sammlung {#run-a-workflow-on-a-collection}

Sie können einen Workflow für die Assets in einer Sammlung ausführen. Wenn die Sammlung verschachtelte Sammlungen enthält, wird der Workflow auch für die Assets innerhalb der verschachtelten Sammlungen ausgeführt. Wenn die Sammlung und die verschachtelte Sammlung jedoch doppelte Assets enthalten, wird der Workflow für diese Assets nur einmal ausgeführt.

1. Wählen Sie in der Konsole „Sammlungen“ eine Sammlung aus, für die Sie einen Workflow ausführen möchten.
1. Wählen Sie das GlobalNav-Symbol aus und wählen Sie **[!UICONTROL Timeline]** aus der Liste.
1. Wählen Sie in der Timeline das Caret-Symbol unten aus oder tippen Sie darauf und wählen Sie **[!UICONTROL Workflow starten]**.
1. Wählen Sie im Abschnitt **[!UICONTROL Workflow starten]** ein Workflow-Modell aus der Liste aus. Wählen Sie beispielsweise das **[!UICONTROL DAM Update Asset]**-Modell aus.
1. Geben Sie einen Titel für den Workflow ein und wählen Sie **[!UICONTROL Starten]**.
1. Wählen Sie im Dialogfeld **[!UICONTROL Fortfahren]**. Der Workflow wird für alle Assets in der Sammlung ausgeführt.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Massenimport von Metadaten](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [Erstellen einer Prüfungsaufgabe für Sammlungen](/help/assets/bulk-approval.md)
