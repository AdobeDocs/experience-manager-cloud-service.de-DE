---
title: Zugänglichkeit in [!DNL Experience Manager Assets]
description: Erkennen Sie, wie Barrierefreiheitsfunktionen [!DNL Adobe Experience Manager] in einem Cloud Service Benutzern mit Behinderungen helfen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b866d9317ba1795b34f7e308426240c44bd1131c
workflow-type: tm+mt
source-wordcount: '1841'
ht-degree: 3%

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

Die Adobe setzt sich dafür ein, Produkte für alle Nutzer, auch für Menschen mit Behinderungen, herzustellen. [!DNL Adobe Experience Manager] wird ständig erweitert, um den Bedürfnissen aller Benutzer gerecht zu werden. [!DNL Experience Manager] veröffentlicht Informationen zur Konformität, die die Standards, die es einhält, detailliert beschreiben, die Barrierefreiheitsmerkmale im Produkt skizzieren und den Grad der Konformität beschreiben. Es hilft Benutzern, das Ausmaß der Einhaltung zu verstehen.

[!DNL Adobe Experience Manager] bietet unterschiedliche Unterstützung für die folgenden Standards:

* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [Abschnitt 508](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines)überarbeitet.
* [WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/).
* [EN 301 549](https://en.wikipedia.org/wiki/EN_301_549).

Informationen zum Zugriff auf den Bericht mit detaillierten Informationen zu den Compliance-Stufen finden Sie auf der Seite [Barrierefreiheitskonformitätsberichte ](https://www.adobe.com/accessibility/compliance.html) (ACR) für alle Adoben.

## Hilfstechnologien {#at-support}

Benutzer mit Behinderungen greifen häufig auf Hardware und Software zurück, um auf Webinhalte zuzugreifen. Diese Werkzeuge werden als Hilfstechnologien bezeichnet. [!DNL Adobe Experience Manager Assets] mit den folgenden Hilfstechnologien arbeiten, um Benutzern Unterstützung bei der Verwendung der Kernfunktionen der Software zu bieten:

* Bildschirmlesehilfen.
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

<!-- TBD: Add here only those keyboard shortcuts that work for/with Assets. Do with Oct release.
-->

| Benutzeroberfläche oder Szenario | Tastaturbefehl | Aktion |
|---|---|---|
| Ansicht von Spalten in der Benutzeroberfläche &quot;Assets&quot; | Nach-oben- und Nach-unten-Pfeiltasten | Navigieren Sie zu Dateien und Ordnern in derselben Hierarchie. |
| Ansicht von Spalten in der Benutzeroberfläche &quot;Assets&quot; | Pfeiltasten links und rechts | Navigieren Sie zu Dateien und Ordnern über oder unter dem aktuellen Ordner. |
| Durchsuchen von Ordnern in Assets | `/` | Rufen Sie die Suche auf, indem Sie das Feld Omniture Search öffnen. |
| Assets-Konsole | ` | Seitenleisten umschalten |
| Assets-Konsole | Alt + 1 | Öffnen Sie die Inhaltsstruktur. |
| Assets-Konsole | Alt + 2 | Öffnen Sie die [!UICONTROL Navigationsleiste] . |
| Assets-Konsole | Alt + 3 | Anzeigen der [!UICONTROL Zeitschiene] eines ausgewählten Assets |
| Assets-Konsole | Alt + 4 | Öffnen Sie die Live Copy-Verweise des ausgewählten Assets. |
| Assets-Konsole | Alt + 5 | Rufen Sie die Suche und Suche im ausgewählten Ordner auf. |
| Asset oder Ordner ausgewählt | Rücktaste | Löschen Sie das ausgewählte Asset oder den ausgewählten Ordner. |
| Asset oder Ordner ausgewählt | `p` | Öffnen Sie die Seite Eigenschaften des ausgewählten Assets. |
| Asset oder Ordner ausgewählt | `e` | Bearbeiten Sie das ausgewählte Asset. |
| Asset oder Ordner ausgewählt | `m` | Verschiebt das ausgewählte Asset. |
| Asset oder Ordner ausgewählt | Strg+C | Kopieren Sie das ausgewählte Asset. |
| Asset oder Ordner ausgewählt | Esc | Deaktivieren Sie die Auswahl. |
| Das Dialogfeld wird geöffnet und befindet sich im Fokus | Esc | Dialogfeld schließen |
| Innerhalb eines Ordners in DAM | Strg+V | Fügen Sie das kopierte Asset ein. |
| Assets-Konsole | Strg+A | Wählen Sie alle Assets aus. |
| Seiten mit Asset-Eigenschaften | Strg+S | Speichern Sie die Änderungen. |
| Assets-Konsole | `?` | Siehe Liste der Tastaturbefehle. |

Die meisten Tastaturbefehle, die für [!DNL Experience Manager] Konsolen gelten, gelten auch für Assets. See [Keyboard Shortcuts for Consoles](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/essentials/keyboard-shortcuts.html). Erfahren Sie, wie Sie die Tastaturbefehle [aktivieren oder deaktivieren](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md).

## Anmelden und Navigieren in der [!DNL Assets] Benutzeroberfläche {#login}

Benutzer können die Tastatur verwenden, um zum Anmeldefeld zu navigieren und es auszufüllen und sich anzumelden. Die Fehlermeldungen aufgrund falscher Benutzername- und Passwortkombinationen auf der Anmeldeseite werden von Bildschirmlesehilfen bei jedem Auftreten des Fehlers angekündigt.

Nach der Anmeldung können DAM-Benutzer über die Tastatur zur [!DNL Assets] Benutzeroberfläche navigieren. Die Navigationsreihenfolge der Tastatur ist von links nach rechts und von oben nach unten angeordnet. Beim Navigieren mit einer Tastatur werden alle umsetzbaren Optionen, die fokussiert sind, mit einem besseren Farbkontrast hervorgehoben und von einer Bildschirmlesehilfe kommentiert. Der Status - erweitert oder reduziert - der fokussierten Optionen im Menü wird von einer Bildschirmlesehilfe angekündigt.

Wenn ein Benutzer die Profil- oder Hilfe-Option aus dem Menü erweitert, wird die entsprechende Option bzw. der entsprechende Status von der Bildschirmlesehilfe angekündigt. Wenn ein Benutzer die Option &quot;Benutzertastatur&quot;erweitert, können die verfügbaren Profil über eine Tastatur ausgewählt werden. Ein Benutzer kann beispielsweise einen anderen Benutzer imitieren. Option und Fehlermeldung zur Benutzeroberfläche

![Tastaturnavigation der wichtigsten Optionen in der Benutzeroberfläche des Experience Managers](assets/keyboard-navigation-in-aem.gif)

*Abbildung: Navigieren durch die Optionen oben in der Benutzeroberfläche des Experience Managers mithilfe des`Tab`Schlüssels.*

Wenn ein Benutzer über die Option [!UICONTROL Hilfe] nach einer Zeichenfolge sucht, gibt ein Erzähler &quot;Hilfe suchen&quot;an, dass eine Suche ausgeführt wird.

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
* Wenn ein Asset ausgewählt ist, wird durch Drücken der Tastenkombination Alt + 4 die Liste &quot;Referenzen&quot;geöffnet. Mithilfe der `Tab` Taste können Benutzer durch die Referenzeinträge &quot;none-zero&quot;navigieren.
* Kommentare zu einem Asset sind in der Asset-Zeitleiste verfügbar. Er ist über die Tastatur zugänglich.
* Auf die Einstellungen für die Ansicht in Experience Manager kann über die Tastatur zugegriffen werden. Der Benutzer kann mithilfe der Pfeiltasten durch die verfügbaren Kartengrößen navigieren und durch die Optionen navigieren und andere Elemente in der Ansicht &quot;Einstellungen für Ansichten&quot;auswählen und durch Registerkarten navigieren.

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
* Das Popup-Dialogfeld für die Datumsauswahl kann über eine Tastatur verwendet werden. Mit dem Datumsauswahl können Sie Zeit- und Nebenzeiten einstellen.
* Die Funktion zum Ziehen mit der Tastatur funktioniert im Metadaten-Schema-Editor im Durchsuchen-Modus der Bildschirmlesehilfe korrekt.
* Ein Benutzer kann den Fokus mithilfe der Tastatur in das Feld &quot;Hinzufügen Benutzer&quot;oder &quot;Gruppe&quot;unter &quot;Geschlossene Benutzergruppe&quot;auf der Registerkarte &quot;Berechtigungen&quot;der Ordnereigenschaften verschieben.

## Suchen nach digitalen Assets {#search-assets}

Eine schnelle und nahtlose Suche nach Assets beschleunigt die Inhaltsgeschwindigkeit. Die Einsatzfälle mit Inhaltsgeschwindigkeit sind Teil der Kernfunktionalität [!DNL Assets] . Um eine Suche über die Omniture Suchleiste Beginn, können Benutzer den Tastaturbefehl verwenden `/` `Tab` oder zusammen mit Bildschirmlesehilfen die Suchoption schnell finden. Die Bildschirmlesehilfe erläutert den Namen der Option als [!UICONTROL Suchschaltfläche] , wenn der Fokus auf der ![Suchoption](assets/do-not-localize/search_icon.png)liegt. Benutzer können die Suchbox `Return` durch Drücken der Taste öffnen. Die Bildschirmlesehilfe erläutert nicht nur den in das Suchfeld eingegebenen Suchbegriff, sondern auch die von [!DNL Experience Manager Assets]ihr angebotenen Vorschläge zur automatischen Vervollständigung. Benutzer können eine Kombination aus Pfeiltasten verwenden `Return``Tab` und auf die verschiedenen Optionen zugreifen, um eine Suche auszulösen.

Die Suchfunktion steht mit den folgenden Funktionen zur Verfügung:

* Der Seitentitel, der einer Bildschirmlesehilfe zur Verfügung steht, hilft, die Seite als Asset-Suchseite zu identifizieren.
* Benutzer suchen in der Omniture Suchleiste nach Assets. Verwenden Sie entweder die Tastaturbefehle oder den Tastaturbefehl, um auf die Omniture Suchleiste `/` zuzugreifen.
* Beginn, der den Suchbegriff eingibt, wählen die automatischen Vorschläge mit der Tastatur aus. Drücken Sie die Eingabetaste, um eine automatisch vorgeschlagene Zeichenfolge zu akzeptieren und Assets dafür zu suchen.
* Bildschirmlesehilfen können die Kontrollkästchen mit gemischtem Status identifizieren und ankündigen (in denen, wenn Sie nicht alle verschachtelten Kontrollkästchen auswählen, die ersten Ebenen nicht ausgewählt sind und durchgestrichen werden), wenn Sie die Suchergebnisse filtern, im Bedienfeld &quot;Filter&quot;anzeigen.
* Der Benutzerfokus wechselt zu den Suchoptionen, nachdem das Omniture Suchfeld geschlossen wurde.

Beim Filtern der Suchergebnisse:

* Auf der Suchergebnisseite finden Sie informative Titel, die ein besseres Verständnis der Bildschirmlesehilfen-Benutzer ermöglichen.
* Eine Bildschirmlesehilfe kündigt die Optionen im Suchfilter als erweiterbare Akkordeons an.
* Prädikate mit Schaltflächen mit gemischtem Status werden von Bildschirmlesehilfen angekündigt.

## Freigeben von Assets {#share-assets}

<!-- TBD: Accessibility in DA, BP, AAL? Asked CCE team for AAL content?
-->

Beim Freigeben von Assets verbessern die folgenden Funktionen die Zugänglichkeit:

* Ein Benutzer kann den Fokus mithilfe der Tastatur im Feld Suchen und Hinzufügen E-Mail-Adresse im Dialogfeld Linkfreigabe verschieben.

* Wenn Sie im Dialogfeld für die Freigabe von Links im Durchsuchen-Modus navigieren,

   * Die Tabelleninformationen sollten nicht kommentiert werden, sobald das Dialogfeld geladen wurde.
   * Kann zu allen aufgelisteten automatischen Empfehlungen navigieren.
   * Geben Sie die angezeigten automatischen Vorschläge für Hinzufügen Felder &quot;E-Mail-Adresse&quot;und &quot;Suche&quot;an.

## Zugänglichkeit in [!DNL Dynamic Media] {#dynamic-media-accessibility}

Bei der Verwendung von dynamischen Medien hilft die folgende Funktion, sie barrierefrei zu gestalten:

* Ein Benutzer kann mithilfe des `Flyout`Schlüssels in den Asset-Details-Viewern in `InlineZoom`, `Shoppable_Banner`, `Zoom_dark`, `Zoom_light`, `ZoomVertical_dark`und `ZoomVertical_light` Optionen auf Optionen fokussieren `Tab` [!DNL Dynamic Media].

## Barrierefreie Dokumentation {#accessible-docs}

[!DNL Experience Manager] bietet zugängliche Dokumentation, die von Menschen mit Behinderungen genutzt werden kann. Die folgenden Hilfen helfen Ihnen, die Inhalte, die derzeit verfügbar sind, barrierefrei zu machen, während die Adobe die Vorlage und den Inhalt weiter verbessert:

* Bildschirmlesehilfen können den Text lesen.
* Bilder und Illustrationen haben alternativen Text verfügbar.
* Die Tastaturnavigation ist möglich.
* Kontrastverhältnisse helfen, einige Teile der Dokumentation-Website hervorzuheben.

<!-- 
## More resources for accessibility {#a11y-resources}

TBD: If anyone is aware of AEM-specific resources that help users leverage any accessibility features or use any assistive technology with AEM, please share or leave a link here.
-->

## Verbesserungen in [!DNL Experience Manager Assets] Versionen {#rn-fixes}

Eine Liste der in den einzelnen Versionen vorgenommenen spezifischen Verbesserungen finden Sie in den [Versionshinweisen](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/release-notes/home.html) der jeweiligen Versionen.

>[!MORELIKETHIS]
>
>* [AEM](/help/onboarding/accessibility/web-accessibility.md)
>* [Konformitätsberichte für Adoben](https://www.adobe.com/accessibility/compliance.html)

