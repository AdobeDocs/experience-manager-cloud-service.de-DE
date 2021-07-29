---
title: Wie werden Suchfilter für den Posteingang konfiguriert?
description: Erfahren Sie, wie Sie Suchfilter für Posteingangselemente konfigurieren.
source-git-commit: ee32ab3659ee4696caa55b945b6b7895d94914a9
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 2%

---

# Suchfilter für den Posteingang konfigurieren {#configure-search-filters-inbox}

Sie können Suchfilter für Posteingangselemente konfigurieren. Stützen Sie Ihre Suchkriterien auf eine bestimmte Spalte im Posteingang, um die Ergebnisse zu filtern.

Um beispielsweise die Posteingangselemente nach dem Datumsbereich des Posteingangsdatums zu filtern, können Sie mit dem Datumsbereichsprädikat den Datumsbereich definieren.

Im Folgenden finden Sie die verfügbaren Prädikatypen für den Posteingang:

* Eigenschaft für Bereich

* Texteigenschaft

* Datumsbereich-Eigenschaft

* Options-Eigenschaftsprädikat

>[!NOTE]
>
>Stellen Sie sicher, dass Sie Mitglied der Gruppe `workflow-administrators` sind, um Suchfilter für den Posteingang zu konfigurieren.

## Erstellen oder Öffnen einer benutzerdefinierten Konfiguration {#creating-opening-customized-configuration}

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Suchformulare]**.

1. Wählen Sie die Konfiguration **[!UICONTROL Inbox Search Rail]** aus und tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Integrieren Sie die Konfigurationsänderungen der Prädikate mithilfe von **[!UICONTROL Edit Search Forms]**.
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Konfiguration zu speichern.

## Benutzerdefinierte Konfiguration löschen {#delete-customized-configuration}

So löschen Sie eine benutzerdefinierte Konfiguration:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Suchformulare]**.

1. Wählen Sie die Konfiguration **[!UICONTROL Inbox Search Rail]** aus und tippen Sie auf **[!UICONTROL Löschen]**.

## Konfigurieren von Bereichsprädikaten {#range-predicate}

Sie können Posteingangselemente filtern, um mithilfe des Bereichsprädikats innerhalb einer Posteingangsspalte nach einem Zahlenbereich zu suchen. Sie können auch Dezimalwerte für Zahlen angeben.

So konfigurieren Sie ein Bereichsprädikat:

1. Öffnen Sie das Formular [für die Konfiguration](#creating-opening-customized-configuration).
1. Tippen Sie auf die Registerkarte **[!UICONTROL Wählen Sie Prädikat]** und ziehen Sie **[!UICONTROL Bereichsprädikat]** in das Formular.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** den Spaltennamen des Posteingangs aus, auf dem die Suche basieren soll. Wählen Sie dazu das Feld **[!UICONTROL Spaltenname]** aus.
1. Geben Sie den Titel für den Filter im Feld **[!UICONTROL Filterbezeichnung]** an. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Dezimalwerte aktivieren]** , um Dezimalwerte für Zahlen zu akzeptieren, während Sie den Bereich definieren.
1. Geben Sie eine optionale Beschreibung für die Konfiguration an und tippen Sie auf **[!UICONTROL Fertig]**, um sie zu speichern.

Die Konfigurationsänderungen werden beim Öffnen der Seite &quot;Filter&quot;übernommen. Die in Schritt 4 angegebene Filterbeschriftung wird als Beschriftung mit einer Option zur Definition der Mindest- und Höchstwerte angezeigt. Wenn Sie die Eingabetaste drücken, wendet [!DNL Experience Manager] die Suchkriterien auf den in Schritt 3 angegebenen Spaltennamen an und gibt die Posteingangselemente zurück.

>[!NOTE]
>
>In diesem Artikel werden die neuesten Optionen der Benutzeroberfläche aufgeführt. Die Optionsnamen werden in der kommenden Version auf der Benutzeroberfläche aktualisiert.

## Texteigenschaft konfigurieren {#text-predicate}

Filtern Sie Posteingangselemente, um mithilfe der Texteigenschaft in einer Spalte im Posteingang nach einer Textzeichenfolge zu suchen.

So konfigurieren Sie eine Texteigenschaft:

1. Öffnen Sie das Formular [für die Konfiguration](#creating-opening-customized-configuration).
1. Tippen Sie auf die Registerkarte **[!UICONTROL Wählen Sie Prädikat]** und ziehen Sie **[!UICONTROL Texteigenschaft]** in das Formular.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** den Spaltennamen des Posteingangs aus, auf dem die Suche basieren soll. Wählen Sie dazu das Feld **[!UICONTROL Spaltenname]** aus.
1. Geben Sie den Text, der im Textfeld Suchen als Platzhaltertext im Feld **[!UICONTROL Suchtextfeld-Platzhalter]** angezeigt wird, an.
1. Geben Sie eine optionale Beschreibung für die Konfiguration an und tippen Sie auf **[!UICONTROL Fertig]**, um sie zu speichern.

Die Konfigurationsänderungen werden beim Öffnen der Seite &quot;Filter&quot;übernommen. Wenn Sie die Eingabetaste drücken, wendet [!DNL Experience Manager] den in Schritt 4 angegebenen Suchtext auf den in Schritt 3 angegebenen Spaltennamen an und gibt die Posteingangselemente zurück.

## Datumsbereichsprädikat konfigurieren {#date-range-predicate}

Sie können Posteingangselemente filtern, um mithilfe des Datumsbereichsprädikats in einer Spalte im Posteingang nach einem Datumsbereich zu suchen.

So konfigurieren Sie ein Datumsbereichsprädikat:

1. Öffnen Sie das Formular [für die Konfiguration](#creating-opening-customized-configuration).
1. Tippen Sie auf die Registerkarte **[!UICONTROL Wählen Sie Prädikat]** und ziehen Sie **[!UICONTROL Datumsbereichsprädikat]** in das Formular.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** den Spaltennamen des Posteingangs aus, auf dem die Suche basieren soll. Wählen Sie dazu das Feld **[!UICONTROL Spaltenname]** aus.
1. Geben Sie die Bezeichnung für den Filter für den Datumsbereich im Feld **[!UICONTROL Filterbezeichnung]** an.
1. Geben Sie die Beschriftungen für das Start- und Enddatum für den Filter an.
1. Geben Sie eine optionale Beschreibung für die Konfiguration an und tippen Sie auf **[!UICONTROL Fertig]**, um sie zu speichern.

Die Konfigurationsänderungen werden beim Öffnen der Seite &quot;Filter&quot;übernommen. Die in Schritt 4 angegebene Filterbeschriftung wird zusammen mit den in Schritt 5 angegebenen Beschriftungen für das Startdatum und das Enddatum für den Datumsbereichfilter angezeigt. [!DNL Experience Manager] wendet die Suchkriterien auf den in Schritt 3 angegebenen Spaltennamen an und gibt die Posteingangselemente zurück.

## Eigenschaft für benutzerdefinierte Spaltenoptionen konfigurieren {#custom-column-options-predicate}

Sie können Posteingangselemente filtern, um mithilfe des Prädikats Benutzerdefinierte Spaltenoptionen in einer Spalte im Posteingang nach einer benutzerdefinierten Option zu suchen.

So konfigurieren Sie ein Prädikat für benutzerdefinierte Spaltenoptionen:

1. Öffnen Sie das Formular [für die Konfiguration](#creating-opening-customized-configuration).
1. Tippen Sie auf die Registerkarte **[!UICONTROL Wählen Sie Prädikat]** und ziehen Sie **[!UICONTROL Benutzerdefinierte Spaltenoptionen-Eigenschaft]** in das Formular.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** den Spaltennamen des Posteingangs aus, auf dem die Suche basieren soll. Wählen Sie dazu das Feld **[!UICONTROL Spaltenname]** aus.
1. Geben Sie den Titel für den Filter für benutzerdefinierte Spaltenoptionen im Feld **[!UICONTROL Filterbezeichnung]** an.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Einzelauswahl]** , um die Auswahl nur einer Option zu aktivieren, während Sie den Filter auf eine Posteingangsspalte anwenden.
1. Fügen Sie im Abschnitt **[!UICONTROL Optionen]** hinzu:
   1. Wählen Sie **[!UICONTROL Manuell]** aus, um die Filtersuchoptionen manuell zu definieren. Tippen Sie auf **[!UICONTROL Filteroptionen hinzufügen]** , um die erste Option zu definieren. Geben Sie den Titel für die Spaltenoption und den Text für den Optionswert an, nach dem gesucht werden soll. Wenn Sie beispielsweise **Female** als Wert in einer Posteingangsspalte suchen möchten, können Sie **F** als Titel für die Spaltenoption angeben und **Weiblich** als Optionswerttext hinzufügen. Auf ähnliche Weise können Sie weitere Filteroptionen hinzufügen.
   1. Wählen Sie **[!UICONTROL JSON-Pfad]** aus, um Optionen mithilfe eines JSON-Dateipfads zu definieren. Im Folgenden finden Sie eine JSON-Beispieldatei zum Definieren von Filteroptionen:

      ```JSON
          {
         "options":[
            {
            "text":"Female",
            "value":"F"
            },
            {
            "text":"Male",
            "value":"M"
            }
          ]
        }
      ```

   1. Wählen Sie **[!UICONTROL CRX Options Path]** aus, um Optionen mithilfe der CRX-Repository-Pfade zu definieren. Tippen Sie auf **[!UICONTROL Hinzufügen von Optionspfaden]** , um mehrere Pfade hinzuzufügen. Im Folgenden finden Sie ein Beispiel zur Definition der Filteroptionen `Male` und `Female`:

      ```JSON
         <gender jcr:primaryType="sling:OrderedFolder">
                        <male
                            jcr:primaryType="nt:unstructured"
                            jcr:title="Male"
                            value="M"/>
                        <female
                            jcr:primaryType="nt:unstructured"
                            jcr:title="Female"
                            value="F"/>
                    </gender>
      ```

1. Geben Sie eine optionale Beschreibung für die Konfiguration an und tippen Sie auf **[!UICONTROL Fertig]**, um sie zu speichern.

Die Konfigurationsänderungen werden beim Öffnen der Seite &quot;Filter&quot;übernommen. Die Filterbeschriftung, die Sie in Schritt 4 angegeben haben, wird als Beschriftung für das Prädikat Benutzerdefinierte Spaltenoptionen angezeigt. [!DNL Experience Manager] wendet die in Schritt 6 definierten Suchkriterien auf den in Schritt 3 angegebenen Spaltennamen an und gibt die Posteingangselemente zurück.

Das folgende Video zeigt die Schritte zum Filtern einer Spalte anhand der Optionswerte `true` und `false`.

>[!VIDEO](https://video.tv.adobe.com/v/335679)

## Suchfilter basierend auf Eigenschaften anzeigen {#view-search-filters-for-predicates}

Sie können Suchfilter basierend auf Eigenschaften anzeigen. Wählen Sie auf der Seite &quot;Posteingang&quot;die Option **[!UICONTROL Filter]** aus. Die Filter werden im linken Bereich angezeigt. Anschließend können Sie die Suchkriterien zum Filtern von Posteingangselementen angeben.

![Filterseite](assets/apply-filters.png)

Weitere Informationen zum Verwalten von Prädikatkonfigurationen finden Sie unter [Konfigurieren von Search Forms](search-forms.md).


