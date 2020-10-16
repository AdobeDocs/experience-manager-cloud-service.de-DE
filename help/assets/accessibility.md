---
title: Zugänglichkeit in [!DNL Experience Manager Assets]
description: Erkennen Sie, wie Barrierefreiheitsfunktionen [!DNL Adobe Experience Manager] in einem Cloud Service Benutzern mit Behinderungen helfen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9b52d37a5af866dfb1bce6ee18b524a0f6ede19e
workflow-type: tm+mt
source-wordcount: '1904'
ht-degree: 2%

---


<!--
Original scope of this article for Core Assets for all a11y topics is around the following topics. This has changed since then but keeping this list of topics for posterity's sake.

* Convert the absolute doc links to relative links.
* Add an overview
* Compile a list of enhancements done in the last ~1 year.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, popup dialogs, etc.)
* Specific user tasks supported, such as, download assets, datepicker, editing metadata, etc.
* Support matrix of user tasks with browsers and screen readers + OSes combinations
* Exceptions that users should be aware of.
* CTA – what is next and more info from AEM team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Examples of other a11y DX Docs from Elle.
  * Link to a11y-specific channels to report issues, seek support, or request enhancements, if any. Available info from Elle.
-->

# Accessibility in [!DNL Adobe Experience Manager Assets] as a Cloud Service {#accessibility-in-aem-assets}

[!DNL Adobe Experience Manager] Ersteller und Herausgeber von Inhalten können beeindruckende Erlebnisse im Web bereitstellen. Die Adobe bemüht sich, die Schöpfer mit Behinderungen einzubeziehen, indem sie die Zugänglichkeit von [!DNL Experience Manager]. Die Software wird kontinuierlich erweitert, um den Anforderungen aller Benutzertypen gerecht zu werden und die weltweiten Standards einzuhalten, zu denen Personen mit Sehbehinderungen, Hörgeschäften, Mobilitäten oder anderen Beeinträchtigungen gehören.

[!DNL Experience Manager] veröffentlicht Konformitätsinformationen, die die Standards, die es einhält, beschreiben, die Barrierefreiheitsmerkmale des Produkts skizzieren und den Grad der Konformität beschreiben. Diese Berichte zur Barrierefreiheitskonformität helfen [!DNL Experience Manager] Benutzern, den Umfang der Einhaltung zu verstehen. Die Verbesserungen, die mit vorgenommen wurden, [!DNL Assets] ermöglichen es allen Benutzern, die Schnittstellen einfach über Tastatur, Bildschirmlesehilfe, Vergrößerungssoftware und andere Hilfstechnologien zu nutzen.

[!DNL Experience Manager] bietet unterschiedliche Unterstützung für die folgenden Standards:

* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [Überarbeiteter Abschnitt 508 des Rehabilitationsgesetzes](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines).
* [Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) von W3C](https://www.w3.org/WAI/standards-guidelines/aria/).
* [EN 301 549](https://en.wikipedia.org/wiki/EN_301_549).

Informationen zum Zugriff auf den Bericht mit detaillierten Informationen zu den Compliance-Stufen finden Sie auf der Seite [Barrierefreiheitskonformitätsberichte](https://www.adobe.com/accessibility/compliance.html) (ACR) für alle Adoben.

## Hilfstechnologien {#at-support}

Benutzer mit Behinderungen greifen häufig auf Hardware und Software zurück, um auf Webinhalte zuzugreifen. Diese Werkzeuge werden als Hilfstechnologien bezeichnet. [!DNL Experience Manager Assets] kann mit folgenden Arten von Hilfstechnologien (AT) arbeiten, wenn die Kernfunktionen der Software verwendet werden:

* Bildschirmlesehilfen und Vergrößerungssoftware.
* Spracherkennungssoftware.
* Verwendung der Tastatur - Navigation und Tastaturbefehle.
* Hilfreiche Hardware, einschließlich Switch-Steuerungen, erfrischbare Braille-Displays und andere Computer-Eingabegeräte.
* Werkzeuge zum Vergrößern der Benutzeroberfläche

## [!DNL Experience Manager Assets] Nutzungsszenarien, auf die zugegriffen werden kann {#accessible-assets-use-cases}

Die Barrierefreiheitsfunktionen [!DNL Experience Manager]decken zwei wichtige Anforderungen von [!DNL Experience Manager] Benutzern und ihren Kunden ab.

Für Inhaltsentwickler und -ersteller gibt es Funktionen zum Erstellen und Veröffentlichen von barrierefreien Inhalten, die wiederum von ihren Kunden und Website-Besuchern verwendet werden. Die Inhalte können von Menschen mit Behinderungen mithilfe von Hilfstechnologien genutzt werden. Weitere Informationen finden Sie unter Richtlinien für [die Barrierefreiheit](/help/onboarding/accessibility/web-accessibility.md)im Web.

Außerdem [!DNL Experience Manager] können Benutzer und Administratoren mit Behinderungen auf die Benutzeroberfläche und Steuerelemente zugreifen, um Inhalte zu erstellen und zu verwalten. Menschen mit Behinderungen können mithilfe von Hilfstechnologien die [!DNL Assets] Funktionen navigieren, nutzen und verwalten.

Die Kernfunktionen in [!DNL Assets] sind leichter zugänglich als zuvor und werden regelmäßig aktualisiert, um die Einhaltung globaler Standards zu verbessern. Die CRUD-Vorgänge in Assets verfügen über einen gewissen Grad an Barrierefreiheit. DAM-Workflows wie das Hinzufügen, Verwalten, Suchen und Verteilen von Assets sind mithilfe von Tastaturbefehlen, Bildschirmlesehilfen-Text, Farbkontrast usw. verfügbar.

## Unterstützung für die Verwendung der Tastatur {#keyboard-use}

Viele Benutzeroberflächenelemente, die mit einem Zeiger angeklickt oder bearbeitet werden können, können auch mit der Tastatur verknüpft werden. Mithilfe einer Tastatur können Benutzer sich auf Elemente der Benutzeroberfläche konzentrieren und geeignete Maßnahmen ergreifen. Benutzer können Tastaturbefehle direkt verwenden, um einen Befehl oder eine Aktion auszulösen, ohne sich auf Elemente der Benutzeroberfläche konzentrieren und ihn über die Tastatur auslösen zu müssen. Beispielsweise können Benutzer die Zeitschiene eines Assets auf der linken Seite öffnen, indem sie mit der Tastatur zum Steuerelement der Benutzeroberfläche navigieren, die Eingabetaste drücken und den `alt + 2` Tastaturbefehl drücken.

<!-- TBD items:

* The button/menu to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* How to open and browse through the profile popup dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the buttons like delete tag? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### Tastaturbefehle in Assets {#keyboard-shortcuts}

Die folgenden Aktionen in Assets funktionieren mit den aufgelisteten Tastaturbefehlen. Die meisten Tastaturbefehle, die für [!DNL Experience Manager] Konsolen gelten, gelten auch für Assets. See [Keyboard Shortcuts for Consoles](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/essentials/keyboard-shortcuts.html). Erfahren Sie, wie Sie die Tastaturbefehle [aktivieren oder deaktivieren](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md).

| Benutzeroberfläche oder Szenario | Tastaturbefehl | Aktion |
|---|---|---|
| Ansicht von Spalten in der Benutzeroberfläche &quot;Assets&quot; | Nach-oben- und Nach-unten-Pfeiltasten | Navigieren Sie zu Dateien und Ordnern in derselben Hierarchie. |
| Ansicht von Spalten in der Benutzeroberfläche &quot;Assets&quot; | Pfeiltasten links und rechts | Navigieren Sie zu Dateien und Ordnern über oder unter dem aktuellen Ordner. |
| Durchsuchen von Ordnern in Assets | `/` | Rufen Sie die Suche auf, indem Sie das Feld Omniture Search öffnen. |
| Assets-Konsole | ` | Seitenleisten umschalten |
| Assets-Konsole | `Alt + 1` | Öffnen Sie die Inhaltsstruktur. |
| Assets-Konsole | `Alt + 2` | Öffnen Sie die [!UICONTROL Navigationsleiste] links. |
| Assets-Konsole | `Alt + 3` | Anzeigen der [!UICONTROL Zeitschiene] eines ausgewählten Assets |
| Assets-Konsole | `Alt + 4` | Öffnen Sie die Live Copy-Verweise des ausgewählten Assets. |
| Assets-Konsole | `Alt + 5` | Rufen Sie die Suche und Suche im ausgewählten Ordner auf. |
| Asset oder Ordner ausgewählt | Rücktaste | Löschen Sie das ausgewählte Asset oder den ausgewählten Ordner. |
| Asset oder Ordner ausgewählt | `p` | Öffnen Sie die Seite Eigenschaften des ausgewählten Assets. |
| Asset oder Ordner ausgewählt | `e` | Bearbeiten Sie das ausgewählte Asset. |
| Asset oder Ordner ausgewählt | `m` | Verschiebt das ausgewählte Asset. |
| Asset oder Ordner ausgewählt | `Ctrl + c` | Kopieren Sie das ausgewählte Asset. |
| Asset oder Ordner ausgewählt | `Esc` | Deaktivieren Sie die Auswahl. |
| Das Dialogfeld wird geöffnet und befindet sich im Fokus | `Esc` | Dialogfeld schließen |
| Innerhalb eines Ordners in DAM | `Ctrl + v` | Fügen Sie das kopierte Asset ein. |
| Assets-Konsole | `Ctrl + A` | Wählen Sie alle Assets aus. |
| Seiten mit Asset-Eigenschaften | `Ctrl + S` | Speichern Sie die Änderungen. |
| Assets-Konsole | `?` | Siehe Liste der Tastaturbefehle. |

## Anmelden und Navigieren in der [!DNL Assets] Benutzeroberfläche {#login}

Benutzer können die Tastatur verwenden, um zum Anmeldefeld zu navigieren und es auszufüllen und sich anzumelden. Die Fehlermeldungen aufgrund falscher Benutzername- und Passwortkombinationen auf der Anmeldeseite werden von Bildschirmlesehilfen bei jedem Auftreten des Fehlers angekündigt.

Nach der Anmeldung können DAM-Benutzer über die Tastatur in der [!DNL Assets] Benutzeroberfläche navigieren. Die Elemente der Benutzeroberfläche, wie die linke Leiste, die Menüs, das Profil, die Suchleiste, die Dateien und Ordner sowie die Administrations- und Konfigurationseinstellungen, können über die Tastatur navigiert werden. Die Navigationsreihenfolge der Tastatur ist von links nach rechts und von oben nach unten angeordnet. Beim Navigieren mit einer Tastatur wird eine Option, die im Fokus aktiviert werden kann, mit einem besseren Farbkontrast hervorgehoben und von einer Bildschirmlesehilfe kommentiert. Gegebenenfalls wird der Status der fokussierten Optionen im Menü - z. B. erweitert, reduziert und gemischt - von einer Bildschirmlesehilfe angekündigt. Außerdem wird der Zweck der Option &quot;Akzeptabel&quot;von einer Bildschirmlesehilfe angekündigt, anstatt beispielsweise das Erscheinungsbild oder die Platzierung der Benutzeroberfläche.

Wenn ein Benutzer die Profil- oder Hilfe-Option aus dem Menü erweitert, wird die entsprechende Option bzw. der entsprechende Status von der Bildschirmlesehilfe angekündigt. Wenn ein Benutzer die Option &quot;Benutzertastatur&quot;erweitert, können die verfügbaren Profil über eine Tastatur ausgewählt werden. Ein Administrator kann beispielsweise einen anderen Benutzer imitieren. Wenn ein Benutzer über die Option [!UICONTROL Hilfe] nach einer Zeichenfolge sucht, gibt ein Erzähler &quot;Hilfe suchen&quot;an, dass eine Suche ausgeführt wird.

<!-- TBD: Removing for now. Add a more informative video later. Host it on tv.adobe

![Keyboard navigation of top options in Experience Manager user interface](assets/keyboard-navigation-in-aem.gif)

*Figure: Navigating through the options at the top of Experience Manager user interface using `Tab` key.*
-->

## Durchsuchen vorhandener Assets und Informationen zur Ansicht {#browse}

In der [!DNL Assets] Benutzeroberfläche können Benutzer die Tastatur verwenden, um die Liste vorhandener digitaler Assets im DAM-Repository zu durchsuchen, ein Asset zu Vorschau oder herunterzuladen, die generierten Darstellungen anzuzeigen, die Ansichten zu wechseln, die generierten Darstellungen anzuzeigen, die Chronik und den Versionsverlauf anzuzeigen, Kommentare und Verweise zu lesen sowie Metadaten zu Ansicht und Verwaltung zu verwenden.

<!-- TBD: Not sure about the following list items mean:

In Experience Manager header section, when navigating in browse mode, screen reader now announces,
  
  * Suggestions to search in Omnisearch.
  * The state as expanded or collapsed for Solutions, Help, Inbox and User options.
  * The Searching Help status message that is displayed when user enters a search string in Search for Help field under Help option
  * The error message if incorrect value is entered in Impersonate as field under User option and focus correctly moves to the text field (NPR-33804).

Review CQ-4282133 before adding - Close button in a coral-dialog wasn't accessible through keyboard, due to which user cannot trigger close button through keyboard press in version preview dialog. After fix, user can close dialog through close button using keyboard.

* CQ-4273122 - Assets of video/audio type will have aria-label in format "Multimedia player: <Title>" so users relying on screen-reader will get to know that they are video/audio assets.
-->

Beim Durchsuchen des Assets-Repositorys wird die Barrierefreiheit durch folgende Funktionen verbessert:

* Bildschirmlesehilfen geben Textalternativen an, die den Zweck oder die Funktionalität der Symbole anstelle ihrer Namen darstellen.
* Die Benutzer können die Optionen der interaktiven Benutzeroberfläche in der Liste der Verweise auf Assets mithilfe von Tastenkombinationen aufrufen und fokussieren.
* Die Elemente in jeder Zeile in der Ansicht Liste werden von Bildschirmlesehilfen als Elemente derselben Zeile angekündigt.
* Der Benutzerfokus beim Navigieren mit der `Tab` Taste kann zur Schließoption in der Vorschau der Version wechseln.
* Wenn Sie zum Durchsuchen die Tastatur verwenden, haben die hervorgehobenen Optionen der Benutzeroberfläche einen auffälligeren visuellen Fokus mit erhöhtem Kontrast. Dadurch wird der Fokusbereich für den Benutzer leichter erkennbar.
* Die Verwendung der `Esc` Taste zum Entfernen der Schnellaktion-Symbole aus der Miniaturansicht-Ansicht entfernt den Tastaturfokus nicht vom zuletzt fokussierten Element.
* Wenn ein Asset ausgewählt ist, wird durch Drücken der `Alt + 4` Tastenkombination die Liste &quot; [!UICONTROL Referenzen] &quot;in der linken Leiste geöffnet. Mithilfe der `Tab` Taste können Benutzer durch die Nicht-Null-Referenzeinträge navigieren. Wenn Sie nur die Nicht-Null-Referenzeinträge durchsuchen, sparen Sie auch Arbeitsaufwand und Tastenanschläge.
* Kommentare zu einem Asset sind in der Asset-Zeitleiste verfügbar. Es ist verfügbar, wenn über eine Tastatur oder einen Tastaturbefehl auf die linke Leiste zugegriffen wird.
* [!UICONTROL Auf die Einstellungen] der Ansicht in [!DNL Experience Manager] können Sie über eine Tastatur zugreifen. Die Benutzer können mithilfe der Pfeiltasten durch die verfügbaren Kartengrößen navigieren und durch die Pfeiltasten navigieren, um durch andere Elemente in der Ansicht &quot;Einstellungen für Ansichten&quot;zu navigieren und andere Elemente festzulegen.

<!-- TBD: Gradually,  as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?
-->

## Verwalten digitaler Assets {#manage-assets}

Viele Asset-Management-Aufgaben wie CRUD-Vorgänge, das Herunterladen eines Assets und das Hinzufügen von Metadaten sind in unterschiedlichem Umfang verfügbar. Mit Assets können Sie die Aufgaben mithilfe verschiedener Hilfstechnologien, insbesondere eines Bildschirmlesehilfen und einer Tastatur, durchführen.

Sehen Sie sich ein Video an, in dem gezeigt wird, wie Sie mit der Tastatur das Repository [durchsuchen und ein Asset](https://youtu.be/K3dgqMRQJys)herunterladen können.

Für Metadaten-Vorgänge, die in der Regel von Rollen wie Marketingexperten und Administratoren ausgeführt werden, verbessern die folgenden Funktionen die Zugänglichkeit:

* [!UICONTROL Die Option &quot;Speichern und Schließen] &quot;auf der Seite &quot;Asset-Eigenschaften&quot;kann jetzt über die Tastatur aufgerufen werden.
* Bildschirmlesehilfen geben die Optionen zum Löschen der ausgewählten Tags auf der Registerkarte &quot;Einfach&quot;der Schaltflächen &quot;Asset-Eigenschaften&quot;an, um die ausgewählten Tags zu löschen.
* Das Popup-Dialogfeld für die Datumsauswahl kann über eine Tastatur verwendet werden. Mit dem Benutzeroberflächenelement &quot;Datepicker&quot;können Sie On-Time- und Off-Time-Zeiten festlegen.
* Die Funktion zum Ziehen mit der Tastatur funktioniert im Metadaten-Schema-Editor im Durchsuchen-Modus der Bildschirmlesehilfe korrekt.
* Ein Benutzer kann den Fokus mithilfe der Tastatur in das Feld &quot;Hinzufügen Benutzer&quot;oder &quot;Gruppe&quot;unter &quot;Geschlossene Benutzergruppe&quot;auf der Registerkarte &quot;Berechtigungen&quot;der Ordnereigenschaften verschieben.

## Suchen nach digitalen Assets {#search-assets}

Eine schnelle und nahtlose Suche nach Assets beschleunigt die Inhaltsgeschwindigkeit. Die Einsatzfälle mit Inhaltsgeschwindigkeit sind Teil der Kernfunktionalität [!DNL Assets] . Um eine Suche über die Omniture Suchleiste Beginn, können Benutzer den Tastaturbefehl verwenden `/` `Tab` oder zusammen mit Bildschirmlesehilfen die Suchoption schnell finden. Die Bildschirmlesehilfe erläutert den Namen der Option als [!UICONTROL Suchschaltfläche] , wenn der Fokus auf der ![Suchoption](assets/do-not-localize/search_icon.png)liegt. Benutzer können die Suchbox `Return` durch Drücken der Taste öffnen. Die Bildschirmlesehilfe erläutert nicht nur den in das Suchfeld eingegebenen Suchbegriff, sondern auch die von [!DNL Experience Manager Assets]ihm angebotenen Vorschläge. Benutzer können eine Kombination aus Pfeiltasten verwenden `Return``Tab` und auf die verschiedenen Optionen zugreifen, um eine Suche auszulösen.

Die Suchfunktion steht mit den folgenden Funktionen zur Verfügung:

* Der Seitentitel, der einer Bildschirmlesehilfe zur Verfügung steht, hilft, die Seite als Asset-Suchseite zu identifizieren.
* Benutzer suchen in der Omniture Suchleiste nach Assets. Verwenden Sie entweder die Tastaturbefehle oder den Tastaturbefehl, um auf die Omniture Suchleiste `/` zuzugreifen.
* Beginn, der den Suchbegriff eingibt, wählen die automatischen Vorschläge mit der Tastatur aus. Drücken Sie die Eingabetaste, um eine automatisch vorgeschlagene Zeichenfolge zu akzeptieren und Assets dafür zu suchen.
* Bildschirmlesehilfen können die Kontrollkästchen mit gemischtem Status identifizieren und ankündigen (in denen, wenn Sie nicht alle verschachtelten Kontrollkästchen auswählen, die ersten Ebenen nicht ausgewählt sind und durchgestrichen werden), wenn Sie die Suchergebnisse filtern, im Bedienfeld &quot;Filter&quot;anzeigen.
* Der Benutzerfokus wechselt zu den Suchoptionen, nachdem das Omniture Suchfeld geschlossen wurde.

Beim Filtern der Suchergebnisse:

* Die Suchergebnisseite hat einen informativen Titel, der ein besseres Verständnis der Benutzer von Bildschirmlesehilfen vermittelt.
* Eine Bildschirmlesehilfe kündigt die Optionen im Suchfilter als erweiterbare Akkordeons an.
* Prädikate mit Schaltflächen mit gemischtem Status werden von Bildschirmlesehilfen angekündigt.

## Freigeben von Assets {#share-assets}

<!-- TBD: Accessibility in DA, BP, AAL? Asked CCE team for AAL content?
-->

Beim Freigeben von Assets verbessern die folgenden Funktionen die Zugänglichkeit:

* Ein Benutzer kann den Fokus mithilfe der Tastatur im Feld Suchen und Hinzufügen E-Mail-Adresse im Dialogfeld Linkfreigabe verschieben.

* Wenn Sie im Dialogfeld für die Freigabe von Links im Durchsuchen-Modus navigieren,

   * Die Tabelleninformationen sollten nicht kommentiert werden, sobald das Dialogfeld geladen wurde.
   * Kann zu allen aufgelisteten Vorschlägen navigieren.
   * Geben Sie die angezeigten Vorschläge für Hinzufügen Felder &quot;E-Mail-Adresse&quot;und &quot;Suche&quot;an.

<!-- TBD: With more info from the DM team. A few Sev1 issues are fixed and if those are shipped, then mention those here.

## Accessibility in [!DNL Dynamic Media] {#dynamic-media-accessibility}

When using Dynamic Media, the following functionality helps make it accessible:

* A user can focus to `Flyout`, `InlineZoom`, `Shoppable_Banner`, `Zoom_dark`, `Zoom_light`, `ZoomVertical_dark`, and `ZoomVertical_light` options using `Tab` key in asset details Viewers in [!DNL Dynamic Media].
-->

## Barrierefreie Dokumentation {#accessible-docs}

[!DNL Experience Manager] bietet zugängliche Dokumentation, die von Menschen mit Behinderungen genutzt werden kann. Die folgenden Hilfen helfen Ihnen, die Inhalte, die derzeit verfügbar sind, barrierefrei zu machen, während die Adobe die Vorlage und den Inhalt weiter verbessert:

* Bildschirmlesehilfen können den Text lesen.
* Bilder und Illustrationen haben alternativen Text verfügbar.
* Die Tastaturnavigation ist möglich.
* Kontrastverhältnisse helfen, einige Teile der Dokumentation-Website hervorzuheben.

<!-- 
## More resources for accessibility {#a11y-resources}

TBD: If anyone is aware of AEM-specific resources that help users leverage any accessibility features or use any assistive technology with AEM, please share a reference with asgupta@adobe.com.
-->

>[!MORELIKETHIS]
>
>* [Versionshinweise zu bestimmten Verbesserungen, die in den einzelnen Versionen](/help/release-notes/release-notes-cloud/release-notes-current.md)vorgenommen wurden.
>* [AEM Hinweise zur Barrierefreiheit](/help/onboarding/accessibility/web-accessibility.md).
>* [Konformitätsberichte für Adoben](https://www.adobe.com/accessibility/compliance.html).

