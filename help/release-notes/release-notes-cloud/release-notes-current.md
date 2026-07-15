---
title: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager] as a Cloud Service
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
nudge: please
source-git-commit: b1490f7cf89e2e1dc05411e1fe2bb121f851a368
workflow-type: tm+mt
source-wordcount: '4609'
ht-degree: 15%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen wie 2024 oder 2025 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2026.6.0) war der 25. Juni 2026. Die nächste Version (2026.7.0) ist für den 30. Juli 2026 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the May 2026 Release Overview video for a summary of the features added in the 2026.5.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3491490/?quality=12)

-->

## AEM Beta-Programme {#aem-beta-programs}

Beta-Programme für Adobe Experience Manager (AEM) bieten Kunden eine Möglichkeit, auf Vorabversionsfunktionen und -code zuzugreifen, Feedback zu geben und die Zukunft von AEM zu gestalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

**Vorteile der Teilnahme**

Wenn Sie frühzeitig auf von Adobe entwickelte Funktionen zugreifen können, können Kunden und Partner Feedback geben und die Produktentwicklung mitgestalten. Außerdem erhalten sie Unterstützung bei der Vorbereitung auf die Einführung neuer Funktionen vor der allgemeinen Verfügbarkeit.

**Aktuelle Beta-Programme**

In den folgenden Abschnitten sind aktive Beta-Programme aufgeführt.

### Agenten in AEM {#agents-in-aem}

Wenn Sie die leistungsstarken neuen AEM-Agentenfunktionen für Produktion, Governance, Optimierung, Erkennung und Entwicklung erkunden möchten, [erfahren Sie hier, wie Sie darauf zugreifen können.](/help/ai-in-aem/agents/overview.md)

<!--
### Agents in AEM (Explorer program) {#agents-in-aem-beta-program}

Gain early access to powerful, new AEM agentic capabilities across production, governance, optimization, discovery, and development. Your feedback directly shapes Adobe's roadmap and final features. See [Overview of Agents in AEM](/help/ai-in-aem/agents/overview.md) to learn more.

This program typically lasts 4-6 weeks, but can be tailored to be flexible around your ability to actively participate. 

To opt in to participate in this program, email [aemagentsteam@adobe.com](mailto:aemagentsteam@adobe.com) and include the following details to the extent possible:

* Names and Adobe ID's of team members who will actively use agents.
* List Specific agents that you or your team will want to use. Or simply say "All Agents."

Customers selected for participation will be notified directly by Adobe. Participation is subject to eligibility considerations, including customer licensing and limited program capacity. While not all requests can be accommodated initially, additional customers may be considered in future beta waves.
-->

### AEM Foundation (Beta-Programme) {#aem-foundation-beta-programs}

Siehe [AEM Foundation-Betaprogramme](#foundation-early-adopter).

### Cloud Manager (Beta-Programme) {#cloud-manager-beta-programs}

Siehe [Cloud Manager-Beta-Programme](/help/implementing/cloud-manager/release-notes/current.md).

### AEM Assets (Beta-Programme) {#aem-assets-beta-programs}

Siehe [AEM Assets-Beta-Programme](#assets-beta-program-features).

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Visual Content Fragments {#visual-content-fragments}

AEM unterstützt jetzt [visuelle Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md) die die Inhaltsfragmentausgabe als formatierte HTML-Erlebnisse mithilfe angehängter HTML-Vorlagen rendern. Dadurch können Inhaltsautorinnen und -autoren strukturierte Inhalte vor der Veröffentlichung in der Vorschau anzeigen und validieren und modulare Erlebnisse konsistent über verschiedene Kanäle hinweg bereitstellen - einschließlich Web, E-Mail und Edge Delivery Services. Eine integrierte generische Vorlage ist für grundlegende Qualitätssicherung verfügbar, ohne dass eine benutzerdefinierte Vorlage erforderlich ist.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Öffnen von Photoshop-Assets im eingebetteten Adobe Express-Editor**

Sie können jetzt zusätzlich zu den JPEG- und PNG-Formaten auch Adobe Photoshop-Dateien (.psd) im eingebetteten Adobe Express-Editor über die Assets-Ansicht und Content Hub öffnen. Diese Verbesserung ermöglicht es Kreativ- und Marketing-Teams, mit mehrschichtigen Design-Dateien zu arbeiten, ohne AEM Assets verlassen zu müssen, was die Aktualisierung von Inhalten optimiert und die Notwendigkeit des Wechsels zwischen Anwendungen reduziert. Der PSD-Support beschleunigt die Inhaltserstellungs-Workflows und erhält gleichzeitig die Flexibilität von Quell-Design-Assets. Benutzende können resultierende Remix-Erstellungen als kanalfertige Assets in AEM speichern.

**Importieren von Adobe Illustrator- und Adobe InDesign-Assets aus AEM Assets in Adobe Express**

Adobe Express unterstützt jetzt den Import von Adobe Illustrator- (.ai) und Adobe InDesign-Dateien (.indd) aus AEM Assets mithilfe des Assets-Plug-ins. Adobe Illustrator-Dateien können in das aktuelle Dokument oder in ein neues Express-Dokument importiert werden. Adobe InDesign-Dateien können in ein neues Express-Dokument importiert werden. Diese Funktion ermöglicht es Kreativ- und Marketing-Teams, einfacher auf genehmigte Design-Assets zuzugreifen und diese wiederzuverwenden, wodurch die Inhaltserstellung beschleunigt und konsistente Markenerlebnisse über alle Kanäle hinweg sichergestellt werden.

>[!IMPORTANT]
>
>Diese Funktion ist als Funktion für eingeschränkte Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

**Die Asset-Herkunft zwischen Adobe Express und AEM Assets beibehalten**

AEM Assets bewahrt jetzt Informationen zur Herkunft für Assets auf, die in Adobe Express mithilfe von Assets aus AEM erstellt wurden. Diese Funktion zeichnet Beziehungen zwischen Quell-Assets und den resultierenden Inhalten auf und speichert sie als Asset-Metadaten in AEM, sodass Unternehmen verfolgen können, wie genehmigte Assets in Kreativ-Workflows wiederverwendet werden.

Durch die Pflege der Metadaten zur Asset-Herkunft können Teams die Governance, Compliance und die Transparenz von supply chain-Inhalten verbessern. Es hilft Marketing-Experten und Content-Administratoren auch, die Wiederverwendung von Assets besser zu verstehen, Initiativen zur Rechteverwaltung zu unterstützen und die Herkunft von Assets zu verfolgen, die in veröffentlichten Inhalten verwendet werden.

>[!IMPORTANT]
>
>Diese Funktion ist als Funktion für eingeschränkte Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

**AEM-Integration mit Workfront Planning und GenStudio for Performance Marketing für Standard-Kampagnenmetadaten**

Wenn AEM Assets mit [Workfront Planning und GenStudio for Performance Marketing](https://experienceleague.adobe.com/en/docs/workfront/using/adobe-workfront-planning/planning-and-genstudio-integration/planning-and-genstudio-integration-article-index) integriert ist, sind jetzt Kampagnenmetadatenfelder, einschließlich Kampagnenname, Region, Kanal, Rolle und Produkt, in der Leiste „Asset-Ansicht“ der Eigenschaften in einer dedizierten schreibgeschützten Kampagnenregisterkarte verfügbar. Wenn Benutzerinnen und Benutzer in Workfront Planning Assets aus AEM mit GenStudio mit den entsprechenden Objekten in Adobe GenStudio Workspace verbinden, werden bestimmte Werte (z. B. ein bestimmter Kampagnenname) automatisch zu den Metadaten des AEM-Assets hinzugefügt.

Die Integration ermöglicht es Benutzenden, auf der Grundlage von Kampagnenattributen schnell Assets zu finden und nach ihnen zu suchen. Diese Verbesserung verbessert die Auffindbarkeit von Assets, optimiert die Workflows für das Content-Management und hilft Teams, die richtigen Assets für bestimmte Marketing-Initiativen effizienter zu finden.

>[!IMPORTANT]
>
>Diese Funktion ist als Funktion mit eingeschränkter Verfügbarkeit verfügbar und erfordert Lizenzen für Workfront Planning und GenStudio for Performance Marketing. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

**KI-gestütztes Content-Onboarding und supply chain-Automatisierung von Inhalten**

Verwenden Sie einen KI-gestützten Agenten, um Inhaltsmigrationen und wiederkehrende Synchronisierungen zwischen unterstützten Inhalts-Repositorys zu konfigurieren und zu automatisieren. Der Agent führt Sie durch die Einrichtung der Verbindung, die Metadatenzuordnung und die Validierung mit Probeläufen vor der Übertragung von Inhalten. Durch die Eliminierung manueller Prozesse und benutzerdefinierter Integrationen beschleunigt diese Funktion das Onboarding, vereinfacht die laufende Synchronisierung und hilft, Assets und Metadaten systemübergreifend konsistent zu halten.

>[!IMPORTANT]
>
>Diese Funktion ist als Funktion für eingeschränkte Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.


### Neue Funktionen in Dynamic Media mit OpenAPI-Funktionen {#new-features-dynamic-media-openapi}

**KI-generierte Videountertitel**

KI-generierte Videountertitel in Dynamic Media mit OpenAPI-Funktionen verwenden künstliche Intelligenz, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion hat das Ziel, die Barrierefreiheit und das Benutzererlebnis zu verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Die KI analysiert die Audiospur des Videos, um Sprache zu transkribieren und Untertitel zu erstellen, die zwecks Korrektheit oder Anpassung bearbeitet werden können. Diese Untertitel dienen der Barrierefreiheit und machen Videos für Zielgruppen attraktiver, die textbasierte Videounterstützung nutzen bzw. bevorzugen.

>[!IMPORTANT]
>
>Diese Funktion ist als Funktion für eingeschränkte Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

**Eingebettete Videotranskripte für bessere Barrierefreiheit und SEO**

Die Dynamic Media-Komponente bettet jetzt Transkripte für Videos ein, um die Barrierefreiheit für Ihre Kunden zu verbessern. Hierbei handelt es sich um Server Side Rendered (SSR)-Transkripte, die die SEO- und LLM-Sichtbarkeit von Videos direkt erhöhen. Außerdem wird ein kompatibles VideoObject ([ https://schema.org/VideoObject) eingebettet] mit dem Suchmaschinen- und LLM-Tools Videos auf Ihrer Seite erkennen können.

>[!IMPORTANT]
>
>Diese Funktion ist als Funktion für eingeschränkte Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

**Benutzerdefinierte Miniaturansichten für Videos**

Mit Dynamic Media mit OpenAPI-Funktionen können Sie jetzt benutzerdefinierte Miniaturansichten für Video-Assets hochladen. Durch das Ersetzen automatisch generierter Miniaturansichten durch gebrandete oder speziell entwickelte Bilder können Unternehmen die Präsentation von Inhalten verbessern, die Auffindbarkeit von Assets verbessern und ein ansprechenderes Anwendererlebnis schaffen.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms

#### Editor für die interaktive Kommunikation

[Editor für interaktive Kommunikation (IC](/help/forms/interactive-communication/introduction.md) ist jetzt in AEM Forms as a Cloud Service verfügbar. Es handelt sich dabei um eine Browser-basierte Lösung zur Erstellung, Verwaltung und Bereitstellung datengesteuerter interaktiver Korrespondenzen wie Geschäftskorrespondenz, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-E-Mails, Rechnungen und Begrüßungspakete.

![Editor für interaktive Kommunikationen](/help/forms/assets/ic-editor.png)

* **Cloud-basierter Editor**: Im Gegensatz zu AEM Forms Desktop Designer, das nur auf Windows-Computern installiert werden kann, wird der Editor für interaktive Kommunikation in jedem modernen Browser ausgeführt, ohne dass eine Installation erforderlich ist. Dieser Cloud-basierte Ansatz beseitigt Installationsprobleme, bietet plattformübergreifende Barrierefreiheit und ermöglicht die Zusammenarbeit von einem beliebigen Standort aus mit Internetzugang. Weitere Informationen finden Sie unter [Erste Schritte mit dem IC-Editor](/help/forms/interactive-communication/getting-started.md).

* **Komponenten und Eigenschaften**: Erstellen Sie Kommunikationen mithilfe einer Drag-and-Drop-Komponentenbibliothek - Textfelder, Tabellen, Bilder, Barcodes, Teilformulare und mehr. Konfigurieren Sie Layout, Typografie, Ränder und Erscheinungsbild über das Bedienfeld Eigenschaften . Weitere Informationen finden Sie unter [Einführung in den Editor für interaktive Kommunikation](/help/forms/interactive-communication/introduction.md).

* **Datenbindung**: Verbinden Sie Komponenten mit Formulardatenmodellen (FDM), indem Sie visuelle Zuordnungen verwenden, um eine personalisierte, datengesteuerte Ausgabe zu erzielen. Weitere Informationen finden Sie unter [Datenbindung im Editor für interaktive Kommunikation](/help/forms/interactive-communication/configure-data-binding.md).

* **Regeleditor**: Erstellen Sie dynamische, datengesteuerte Aktionen direkt in Ihren Dokumenten mithilfe einer intuitiven Point-and-Click-Oberfläche. Sie können bedingte Logik einfach definieren, Workflows automatisieren und Inhalte personalisieren, ohne programmieren zu müssen. Weitere Informationen finden Sie unter [Erstellen von Regeln im Editor für interaktive Kommunikation](/help/forms/interactive-communication/use-the-rule-editor.md).

* **Vorlagen und Dokumentfragmente**: Erstellen Sie wiederverwendbare Vorlagen und modulare Inhaltsbausteine (Kopfzeilen, Fußzeilen, Haftungsausschlüsse), um die Konsistenz und Effizienz mehrerer Kommunikationen zu gewährleisten. Weitere Informationen finden Sie unter [Erstellen einer ](/help/forms/interactive-communication/create-interactive-communication-template.md) und [Erstellen eines Fragments](/help/forms/interactive-communication/create-interactive-communication-fragment.md).

* **Vorlagensperrung**: Sperren Sie Inhalte und Layout-Elemente in Vorlagen, um die Markenintegrität zu wahren und nicht autorisierte Änderungen zu verhindern. Weitere Informationen finden Sie unter [Vorlagensperre](/help/forms/interactive-communication/enable-template-lock.md).

* **PDF-Vorschau**: Zeigen Sie eine Vorschau der interaktiven Kommunikation ohne Daten, lokale JSON-Dateien oder Datenmodelle für flexible, datengesteuerte Tests an. Weitere Informationen finden Sie unter [PDF-Vorschau](/help/forms/interactive-communication/generate-pdf-preview.md).

* **Benutzerdefinierte Schriftarten**: Betten Sie benutzerdefinierte oder vom Unternehmen genehmigte Schriftarten ein, um ein konsistentes, markenspezifisches PDF-Rendering auf allen Geräten sicherzustellen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Schriftarten](/help/forms/interactive-communication/add-custom-fonts.md).

* **Importieren und Exportieren**: Nahtlose Migration und Wiederverwendung der interaktiven Kommunikation mit ihren Fragmenten und Datenmodellen über Umgebungen hinweg. Weitere Informationen finden Sie unter [ und Exportieren](/help/forms/interactive-communication/import-and-export-the-interactive-communication.md).

* **Inhaltsüberlauf**: Option „Seitenumbrüche innerhalb von Inhalten zulassen“ für fließende Layouts für eine reibungslose mehrseitige Bearbeitung und eine bessere Textverwaltung für komplexe Dokumente. Weitere Informationen finden Sie unter [Umgang mit Inhaltsüberläufen](/help/forms/interactive-communication/handle-content-overflow.md).

* **XDP-Dateibearbeitung**: Bearbeiten Sie XDP-Dateien in einem Browser anstelle von Forms Designer, das nur auf dem Microsoft Windows-Desktop ausgeführt wird. Weitere Informationen finden Sie unter [Unterstützung der XDP-Bearbeitung](/help/forms/interactive-communication/support-xdp-editing.md).

* **Benutzeroberfläche zuordnen**: Eine vereinfachte Laufzeitschnittstelle für kundenorientierte Mitarbeiter, um Daten einzugeben und personalisierte Kommunikation in Echtzeit zu generieren. Rufen Sie die zugehörige Benutzeroberfläche direkt auf den Veröffentlichungsinstanzen auf, um die Integration zu vereinfachen und die Bereitstellung in allen Umgebungen zu beschleunigen. Weitere Informationen finden Sie unter [Übersicht über die Associate](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md), [Aktivieren und Konfigurieren der Associate](/help/forms/interactive-communication/enable-configure-associate-ui.md) und [Benutzeroberfläche integrieren](/help/forms/interactive-communication/invoke-associate-ui.md).

* **Dynamische Seitennummerierung**: Auf Musterseiten wird automatisch die „Seite ##&quot; angezeigt, um eine klare, konsistente Paginierung über mehrseitige Dokumente hinweg zu gewährleisten. Weitere Informationen finden Sie unter [Dynamische Seitennummerierung](/help/forms/interactive-communication/implement-dynamic-page-numbering.md).

* **Versionierung und Kommentierung im Editor für interaktive Kommunikation**: Der Editor für interaktive Kommunikation unterstützt jetzt die Versionierung und Kommentierung, damit Autoren gekennzeichnete Versionen speichern, das Feedback von Reviewern erfassen, zu früheren Zuständen zurückkehren und ein Audit-Protokoll über den gesamten Inhaltslebenszyklus hinweg beibehalten können. Weitere Informationen finden Sie unter [Versionierung und Kommentare im Editor für interaktive Kommunikation](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md).

* **Überprüfen und Kommentieren einer interaktiven Kommunikation**: Reviewer können jetzt interaktive Kommunikationen in einer dedizierten schreibgeschützten Ansicht mit Anmerkungen versehen, Kommentare an bestimmte Komponenten auf der Arbeitsfläche anheften und Feedback an einer Stelle teilen, ohne das Design zu bearbeiten. Autoren können Anmerkungen direkt im Editor verfolgen und auflösen. Weitere Informationen finden Sie unter [Überprüfen und Kommentieren einer interaktiven Kommunikation](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md).

* **Versionen der interaktiven Kommunikation vergleichen**: Sie können jetzt zwei beliebige gespeicherte Versionen einer interaktiven Kommunikation nebeneinander vergleichen, während PDF-Vorschauen das Layout und statische Inhaltsänderungen vor der Veröffentlichung überprüfen. Weitere Informationen finden Sie unter [Versionen der interaktiven Kommunikation vergleichen](/help/forms/interactive-communication/howto/compare-interactive-communication-versions.md).

* **Zusammenführen und Aufteilen von Tabellenzellen**: Der Editor für interaktive Kommunikation unterstützt jetzt das Zusammenführen benachbarter Tabellenzellen und das Aufteilen zusammengeführter Zellen wieder in einzelne Spalten, was das Überspannen von Kopfzeilen, Zusammenfassungszeilen und flexiblere Tabellen-Layouts ermöglicht. Weitere Informationen finden Sie unter [Zusammenführen und Aufteilen von ](/help/forms/interactive-communication/howto/merge-and-split-table-cells.md).

* **Verschieben einer Komponente auf die Musterseite**: Sie können jetzt mit einer Aktion eine Komponente von einer Designseite auf die Musterseite verschieben, damit sie konsistent auf jeder Seite einer interaktiven Kommunikation angezeigt wird, ohne sie neu zu erstellen. Weitere Informationen finden Sie unter [Verschieben einer Komponente auf die Musterseite](/help/forms/interactive-communication/howto/move-component-to-master-page.md).

* **Konfigurieren von Dropdown-Optionen für die**-Benutzeroberfläche: Dropdown-Felder in der Benutzeroberfläche „Verknüpfen“ verwenden jetzt ein **Binding-**). Autoren konfigurieren **Bindung aus Daten** für dynamische Optionslisten oder manuelle statische Optionen, damit die Verknüpfungen die richtigen Auswahlmöglichkeiten und vorab ausgewählten Werte sehen. **Datenbindung** wird für Dropdown-Felder nicht unterstützt. Weitere Informationen finden Sie unter [Konfigurieren von Dropdown-Optionen für die Benutzeroberfläche „Verknüpfen](/help/forms/interactive-communication/associateui/configure-dropdown-options-binding.md).

* **Konfigurieren von gebundenen und ungebundenen Variablen für die**-Benutzeroberfläche: Gebundene und ungebundene Variablen in **Text**-Komponenten können jetzt für die Benutzeroberfläche „Verknüpfen“ konfiguriert werden. Autoren können auswählen, ob Verknüpfungen den gesamten Textblock in der Dokumentvorschau inline bearbeiten oder Werte für einzelne Variablen im Dateneingabefeld eingeben sollen. Doppelte Variablennamen übertragen Werte auf alle übereinstimmenden Vorkommnisse in der Vorschau. Weitere Informationen finden Sie unter [Konfigurieren von gebundenen und ungebundenen Variablen für die Benutzeroberfläche „Verknüpfen“](/help/forms/interactive-communication/associateui/configure-bound-unbound-variables-associate-ui.md).

#### Zusätzliche CAPTCHA-Optionen für den Bot-Schutz

AEM Forms unterstützt jetzt zusätzlich zum bereits verfügbaren Google reCAPTCHA zwei weitere CAPTCHA-Lösungen zum Schutz von adaptivem Forms vor Bots und Spam-Übermittlungen. Dadurch erhalten Sie mehr Auswahl und Flexibilität beim Schützen Ihrer Formulare.

* **Cloudflare Turnstile**: Ein reibungsloses CAPTCHA, das Benutzer durch eine einfache Herausforderung überprüft, ohne explizite Interaktion zu erfordern, wodurch das Benutzererlebnis verbessert wird. Weitere Informationen finden Sie unter [Verwenden eines Drehkreuzes in einem adaptiven Formular für Kernkomponenten](/help/forms/integrate-adaptive-forms-turnstile-core-components.md) und [Verwenden eines Drehkreuzes in einem adaptiven Formular für Foundation-Komponenten](/help/forms/integrate-adaptive-forms-turnstile.md).
* **hCAPTCHA**: Ein auf Datenschutz fokussiertes CAPTCHA, das eine benutzerfreundliche Alternative bietet, bei der der Schwerpunkt auf Datenschutz, Sicherheit und Anwendererlebnis liegt. Weitere Informationen finden Sie unter [Verwenden von hCAPTCHA in einem adaptiven Formular für Kernkomponenten](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md) und [Verwenden von hCAPTCHA in einem adaptiven Formular für Foundation-Komponenten](/help/forms/integrate-adaptive-forms-hcaptcha.md).

### Early Adopter-Funktionen

#### Datensatzdokument für in AEM Sites eingebettete Formulare

Autorinnen und Autoren können jetzt ein Datensatzdokument (Document of Record, PDF) für adaptive Forms-Kernkomponenten konfigurieren und generieren, die in AEM Sites-Seiten eingebettet sind. Die DoR-Einstellungen, einschließlich der automatischen Generierung, benutzerdefinierter XDP-Vorlagen und des Brandings, sind direkt über den **Container für adaptive Formulare** im Sites-Seiteneditor verfügbar. [Weitere Informationen](/help/forms/generate-document-of-record-core-components.md#configure-document-of-record-for-forms-embedded-in-aem-sites).

#### Gebietsschema-spezifische benutzerdefinierte XDP-Vorlagen für das Datensatzdokument

Wenn Sie eine benutzerdefinierte XDP-Vorlage für DoR zuordnen, können Sie im selben Ordner gebietsschemaspezifische Versionen mithilfe der `basename.<locale>.xdp` bereitstellen (z. B. `a.xdp` und `a.fr.xdp`). AEM Forms wählt beim Generieren der Übermittlungs-PDF automatisch die Vorlage aus, die dem Formulargebietsschema entspricht, mit Fallback auf die Standardvorlage. [Weitere Informationen](/help/forms/generate-document-of-record-core-components.md#locale-specific-custom-xdp-templates-for-document-of-record).

#### Gültigkeit der Adobe Sign-Vereinbarung

Sie können festlegen, wie lange Empfänger das Signieren abschließen müssen, indem Sie **Dokumentenablauf (Tage)** im Abschnitt **Elektronische Signatur** eines adaptiven Formulars angeben. Der Wert wird als `daysUntilSigningDeadline` an Adobe Sign gesendet. Wenn dies leer gelassen wird, läuft die Vereinbarung nicht ab. [Weitere Informationen](/help/forms/working-with-adobe-sign.md#set-document-expiration-for-an-adobe-sign-agreement).

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation - Neue Funktionen {#foundation-new}

#### Conversational AI Interface für Cloud Manager - Fragen {#devagent-cloudmanager}

Der Entwicklungsagent wird erweitert, um Fragen im Zusammenhang mit Cloud Manager über den [Cloud Manager-Auftrag zu ](/help/ai-in-aem/agents/brand-experience/development/development.md#cloud-manager-job). Rufen Sie im KI-Assistenten Informationen zu Programmen, Umgebungen und Pipelines ab (z. B. Ausführungsstatus). Schnelles Auffinden von Links zu Fehlerprotokollen, Zugriffsprotokollen und Build-Protokollen.

#### Verbesserungen bei der Fehlerbehebung bei Pipeline-Agent-Vorgängen {#devagent-pipeline-troubleshooting}

Der Vorgang zur Fehlerbehebung bei [-Pipelines ](/help/ai-in-aem/agents/brand-experience/development/development.md#cloud-manager-pipeline-troubleshooting) Entwicklern, Probleme in AEM as a Cloud Service-Bereitstellungen zu diagnostizieren und zu beheben. Zu den neuen Funktionen gehören:

* Unterstützung für die Web-Stufen-Konfigurations-Pipeline : Zusätzlich zur Unterstützung von Full-Stack-Pipelines (Bereitstellung und Code-Qualität) unterstützt der Entwicklungsagent jetzt die Fehlerbehebung für die **Web-Stufen-Konfigurations-Pipeline**

* Erlebnis-Startseiten-Widget für fehlgeschlagene Pipelines : Für die Rolle „Admin und IT“ wird ein [neues Widget“ angezeigt](/help/ai-in-aem/agents/brand-experience/development/development.md#troubleshoot-from-experience-home) in dem Pipeline-Fehler hervorgehoben werden. Durch Klicken auf eine Schaltfläche wird der Vorgang zur Fehlerbehebung bei der Pipeline im KI-Assistenten gestartet.

#### Verwalten von Ruhezeiten und Aktualisieren von Freizeiten mit dem KI-Assistenten {#quiet-hours-ai}

Sie können jetzt &quot;[ Stunden“ und „Freie Zeiträume aktualisieren“ direkt über ](/help/ai-in-aem/agents/brand-experience/development/development.md#control-updates-job) AEM-KI-Assistenten anzeigen, erstellen und bearbeiten.Der Hauptvorteil liegt in der Verringerung von Zeitplanfehlern. Wenn Sie eine Anfrage stellen, führt Sie der Assistent durch das Mögliche und kennzeichnet die geltenden Beschränkungen, z. B. die Obergrenze für drei Zeiträume, die obligatorische Lücke von einer Woche zwischen Zeiträumen und die geplanten Zeitfenster für Wartungsausschlüsse, für die Sie keinen Zeitplan festlegen können. Anstatt also nach einer fehlgeschlagenen Konfiguration eine Einschränkung zu ermitteln, werden Geschäftsinhaber und Bereitstellungs-Manager im selben Gespräch auf einen gültigen Zeitplan geleitet. Dadurch werden wichtige Geschäftsfenster vor automatischen Wartungs-Updates geschützt und gleichzeitig das Hin- und Herschieben und Fehlkonfigurieren reduziert.

### Wichtige Hinweise zu [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-notices}

#### Rich-Fehler bei der IMS-Authentifizierung {#ims-auth-rich-errors}

Zur Fehlerbehebung bei IMS-Integrationen unterstützt `imsauth` jetzt *Rich-Fehler*.

Anstatt nur einen HTTP-Status-Code zurückzugeben, bieten diese Fehler zusätzlichen Kontext, um Probleme zu diagnostizieren und zu beheben, die die Authentifizierung und den Zugriff blockieren können.

#### Einstellung von Java-APIs {#java-api-deprecation}

Es ist wichtig, die Verwendung veralteter APIs zu entfernen.

Seit dem **14. April 2026** schlagen Cloud Manager-Pipelines, die Code enthalten, der mit APIs zum Entfernen von 2/26/2026 **wurde, während des Code-** fehl. Bereitstellungen werden blockiert, bis die veraltete API-Nutzung entfernt wird. *Dies kann verhindern, dass zeitkritische Updates veröffentlicht werden, und sich auf Ihre Geschäftsabläufe auswirken.*

Ab **23. Juli 2026** Umgebungen, die diese veralteten APIs weiterhin verwenden **erhalten keine wichtigen Adobe-Versions-** mehr und unterliegen nicht den Standardverpflichtungen von Adobe in Bezug auf Leistung und Verfügbarkeit. Infolgedessen erhalten Sie keine neuen Funktionen oder Fehlerbehebungen, die Anwendungsstabilität und -verfügbarkeit kann sich negativ auswirken und das Sicherheitsrisiko kann weiter zunehmen.

Ausführliche Informationen finden Sie im [Artikel zur Einstellung](/help/release-notes/deprecated-removed-features.md#aem-apis). Als Referenz sind diese APIs unten aufgeführt:

+++ Zum Anzeigen der veralteten Java-APIs erweitern

* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.apache.jackrabbit.oak.plugins.memory`

+++

#### Der lokale Dispatcher-MCP-Server ist Teil von AEM SDK {#local-dispatcher-mcp}

Der lokale Dispatcher-MCP-Server ist jetzt in der **AEM-SDK** im [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) enthalten, das in der Zip-Datei der AEM Dispatcher-Tools enthalten ist. Zuvor war der lokale Dispatcher-MCP-Server in einer separaten Beta-Liste von AEM Dispatcher-Tools zusammengefasst.

Der lokale Dispatcher-MCP-Server ermöglicht es KI-Tools, die Dispatcher- und Apache-HTTPD-Konfiguration zu validieren, die Verarbeitung von Trace-Anfragen zu verfolgen und das Cache-Verhalten mit einer Dispatcher-Instanz zu überprüfen, die lokal in Docker ausgeführt wird.

#### Vorbereiten für Java 25: Zeitleiste des Upgrades der AEM Cloud Service-Laufzeit

Java 25 ist die nächste LTS-Version (Long-Term Support) nach Java 21, die Verbesserungen in den Bereichen Leistung, Entwicklerproduktivität und Sicherheit bietet:

- **Leistung** - Verringerter Speicherbedarf, effizientere Speicherbereinigung und schnellere JVM-Aufwärmphase kommen Cloud-nativen Bereitstellungen zugute.
- **Entwicklerproduktivität** - Sauberere Objektinitialisierung, ausdrucksstärkere Musterübereinstimmung und vereinfachte gleichzeitige Aufgabenverwaltung reduzieren Textbausteine und verbessern die Code-Klarheit.
- **Sicherheit** - Modernisierte API für die Ableitung kryptografischer Schlüssel zur Vereinfachung gängiger Sicherheits-Workflows.

Um Unternehmen bei der Planung von Tests und Validierungen vor dem erforderlichen Java 25-Laufzeitupgrade zu unterstützen, stellt Adobe die folgenden Zieldaten bereit. Alle Aktualisierungen dieser Zeitleiste werden über Versionshinweise kommuniziert.

| Zeitraum | Meilenstein |
|---|---|
| **Mitte Oktober 2026** | AEM Cloud Service SDK unterstützt die Java 25-Laufzeitumgebung. Das Java 25-JDK kann vom Adobe Software Distribution-Portal heruntergeladen werden. |
| **November 2026** | Kunden wird empfohlen, optional die Java 25-Laufzeitumgebung in ihren Cloud-Umgebungen zu aktivieren, um ihr Verhalten zu überprüfen. Durch frühzeitige Einführung wird die Zeit für die Aufdeckung und Lösung von Problemen maximiert. |
| **Februar - Mai 2027** | Adobe migriert schrittweise niedrigere Umgebungen (RDE, Dev) zur Java 25-Laufzeitumgebung. Kunden sollten ihr Verhalten überprüfen und unerwartete Probleme melden. Außerdem wird ihnen empfohlen, Staging- und Produktionsumgebungen zu aktivieren. Ein temporäres Rollback zu Java 21 ist verfügbar, während Probleme behoben werden. |
| **Juni 2027** | Alle Umgebungslaufzeiten (einschließlich Staging und Produktion) migrieren auf Java 25. Java 21 Runtime wird eingestellt. Die AEM Cloud Service-SDK unterstützt Java 21 nicht mehr. |

AEM Cloud Service unterstützt weiterhin die Kompilierung von Kunden-Code mit Java 11, Java 17 und Java 21. Adobe empfiehlt jedoch, mit Java 25 zu erstellen (sobald es in AEM verfügbar ist), um die neuesten Sprachfunktionen und Leistungsverbesserungen vollständig nutzen zu können.

### Early-Adopter-Funktionen in [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-early-adopter}

#### AEM Edge-Funktionen (*Public Beta*-Programm) {#edge-functions}

[AEM Edge-Funktionen](/help/implementing/developing/introduction/edge-functions.md) befindet sich jetzt in der öffentlichen Beta-Phase, sodass Sie es selbst ausprobieren können, ohne sich zur Aktivierung an Adobe wenden zu müssen.

Mit dieser Funktion können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher am Endbenutzer rückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge. Sie ist sowohl für AEM Cloud Service Java-Stack- als auch für Edge Delivery Services-Projekte für AEM Sites-Kunden verfügbar.

Häufige Anwendungsszenarien umfassen:

* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden

In [diesem Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/edge-functions/overview) finden Sie eine Anleitung für Edge Delivery Services und AEM as a Cloud Service Java-Stack-Varianten.

*Durch die Verwendung von AEM Edge Functions Beta erkennen Sie an, dass es sich noch in der Entwicklung befindet und Sie sich nicht auf die ordnungsgemäße Funktionsweise der Technologie oder die Verfügbarkeit der Daten verlassen sollten. Diese Funktion wird unverändert bereitgestellt,
können sich ohne Vorankündigung ändern und werden nicht von Produktions-SLAs abgedeckt.*

#### Snapshots für RDEs (*Public Beta*-Programm) {#rde-snapshot-program}

Momentaufnahmen für schnelle Entwicklungsumgebungen (RDEs) befinden sich jetzt in der öffentlichen Beta-Phase, sodass Sie sie selbst ausprobieren können, ohne sich zur Aktivierung an Adobe zu wenden.

RDEs unterstützen jetzt eine Funktion [um einen Schnappschuss zu erstellen](/help/implementing/developing/introduction/rapid-development-environments.md#snapshots) des aktuellen Status von Code und Inhalt, die zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

*Durch die Verwendung der RDE-Snapshots-Beta erkennen Sie an, dass sie sich noch in der Entwicklung befindet und dass Sie sich nicht auf die ordnungsgemäße Funktionsweise der Technologie oder die Verfügbarkeit von Daten verlassen sollten. Obwohl wir diese Funktion ausführlich getestet haben, besteht eine geringe Möglichkeit, dass Ihre RDE instabil wird. In diesem Fall wird sie durch Zurücksetzen wieder in den Betriebszustand versetzt.*

#### Fehlerbehebung bei der Replikations-KI (Beta-Programm) {#replication-ai-troubleshooting-beta}

Mithilfe des KI-Assistenten in der AEM-Autoreninstanz und anderen Benutzeroberflächen können Sie replikationsbezogene Probleme wie blockierte Warteschlangen beheben. Um am Beta-Programm teilzunehmen, senden Sie eine E-Mail an [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com), in der Ihr Interesse beschrieben wird.

#### Canary-Produktionsbereitstellungen zum Testen von Code vor Annahme von Live-Traffic (Beta-Programm) {#canary-beta}

Validieren Sie einen Produktions-Build mit reinem Test-Traffic, bevor Sie ihn für Endbenutzende verfügbar machen. Senden Sie an die Produktion, leiten Sie nur den Canary-Traffic weiter (mithilfe einem speziellen Header) und überwachen Sie das Verhalten. Leiten Sie den Live-Traffic dann entweder weiter oder setzen Sie ihn zurück, ohne dass sich dies auf die Kundinnen und Kunden auswirkt.

Senden Sie eine E-Mail an [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com), um Zugriff anzufordern und Feedback mitzuteilen.

#### AEM-Code-Bewertung und automatische Fehlerbehebung über den IDE AI-Agenten (Beta-Programm) {#ide-ai-aemcode-issues}

Java-Stack-Teams von AEM Cloud Service, die KI-unterstützte Entwicklung in Tools wie Cursor, Claude Code, Visual Studio und IntelliJ verwenden, können jetzt weiter gehen. Eine neue [Code Assessment IDE Agent SKILL](/help/ai-in-aem/local-development-with-ai-tools.md#use-the-code-assessment-skill) erkennt und behebt Probleme direkt in Ihrer AEM-Codebasis, wodurch Überprüfungszyklen reduziert und Probleme in der Entwicklungsphase erkannt werden.

Zu den unterstützten Prüfungen gehören:
* Ersetzen veralteter APIs
* Sling-Modell-Abhängigkeitseinfügung modernisieren
* Aktualisieren veralteter Maven-Abhängigkeiten
* Hinzufügen fehlender Timeouts zu ausgehenden HTTP-Aufrufen
* Ungebundene Abfragen begrenzen
* Sling-Planungen
* Ressourcenänderungs-Listener für die Replikation
* JCR- oder OSGi-Ereignisbehandlung

Diese Funktion befindet sich in der Betaphase. Probieren Sie es aus und teilen Sie Feedback mit dem Team unter [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com).

#### Edge-Authentifizierung für Edge Delivery Services (Beta-Programm) {#edge-authentication}

Mit der Edge-Authentifizierung können Sie den Zugriff auf Edge Delivery Services-Seiten auf diejenigen beschränken, die sich bei Ihrem Identitätsanbieter (IdP) authentifiziert haben. Dies wird durch die Bereitstellung einer YAML-Konfigurationsdatei von OpenID Connect (OIDC) erreicht.

Bei Interesse senden Sie bitte eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls und allen Fragen, die Sie haben.

#### OpenTelemetry für Application Performance Monitoring (APM) (Alpha-Programm) {#apm-alpha}

AEM as a Cloud Service unterstützt jetzt den OpenTelemetry-basierten Telemetrieexport, sodass Sie AEM zusammen mit den anderen Systemen in den APM-Tools überwachen können, die Ihre Teams bereits verwenden.

Verwenden Sie diese Integration für Folgendes:

- Untersuchen langsamer oder fehlgeschlagener Anfragen
- JVM-Status und Ressourcennutzung im Zeitverlauf verfolgen
- Erstellen von Dashboards und Warnhinweisen für Ihre AEM-Ebenen
- Korrelieren des AEM-Verhaltens mit anderen Services während Vorfällen

Um sich der Alpha-Phase anzuschließen, senden Sie eine E-Mail an [](mailto:aemcs-apm-beta@adobe.com)aemcs-apm-beta@adobe.com, in der Ihr Anwendungsfall beschrieben wird.

### Funktionen von [!DNL Experience Manager] as a [!DNL Cloud Service] Assets Beta {#assets-beta-program-features}

#### Erweiterbarkeit der Benutzeroberfläche für die Assets-Ansicht {#ui-extensibility-assets-view-beta}

Assets View unterstützt die Benutzeroberflächen-Erweiterbarkeit, eine Funktion, mit der Kunden das vordefinierte Erlebnis so anpassen können, dass es ihren spezifischen Geschäftsanforderungen entspricht.Kunden können bestehende stabile Erweiterungspunkte nutzen, indem sie der Entwicklerdokumentation von Adobe folgen, um Erweiterungen mit minimalem Aufwand zu erstellen und bereitzustellen. Für Anwendungsfälle, bei denen noch kein erforderlicher Erweiterungspunkt verfügbar ist, arbeitet Adobe direkt mit Kunden zusammen, um die Anforderungen zu untersuchen und die technische Machbarkeit der Bereitstellung neuer Erweiterbarkeits-APIs zu bewerten, die auf ihre Anforderungen zugeschnitten sind, und kann solche neuen APIs wie **Beta-Versionen**.Darüber hinaus hat Adobe ein **GenAI-basiertes Erweiterungsgenerierungstool entwickelt** das derzeit in einer internen frühen Implementierungsphase verfügbar ist. Dieses Tool kann die Entwicklungszeit für Erweiterungen erheblich beschleunigen. Kunden, die an diesem Beta-Programm teilnehmen, erhalten Zugriff auf das Tool und werden ermutigt, Feedback zu geben, um die Entwicklung zu gestalten.Um teilzunehmen oder mehr zu erfahren, senden Sie eine E-Mail an `GRP-ASSETSVIEWUIEXTENSIBILITY@adobe.com`.

#### Markenbewusste Metadaten (BAM) {#brand-aware-metadata-beta}

AEM Assets unterstützt jetzt Brand Aware Metadata, eine KI-gestützte Funktion, mit der beim Hochladen oder erneuten Verarbeiten automatisch benutzerdefinierte Metadaten für Assets generiert werden. Dadurch wird die Notwendigkeit manueller Eingaben um Größenordnungen reduziert, was Teams dabei hilft, Assets zu finden und neue Erlebnisse viel schneller bereitzustellen. Kundinnen und Kunden verwalten eine Bibliothek mit Eingabeaufforderungen, die definieren, wie KI ein bestimmtes Metadatenfeld ausfüllen soll, das auf ihr eigenes Markenvokabular und ihre eigene Taxonomie zugeschnitten ist. Diese Eingabeaufforderungsbibliothek enthält einen Spielplatz für die Vorschau der Ergebnisse und einen Eingabeaufforderungs-Optimierer, der automatisch vorgeschlagene Verbesserungen entwirft.

Adobe erweitert aktiv die Möglichkeiten der BAM durch direkte Co-Innovation mit Kunden. Wenn ein bestimmter Anwendungsfall noch nicht unterstützt wird, arbeitet Adobe mit den teilnehmenden Kundinnen und Kunden zusammen, um deren Anforderungen zu verstehen, und bietet möglicherweise im Laufe der Beta-Phase erweiterte Funktionen. Kunden in diesem Programm erhalten frühzeitigen Zugriff auf neue Funktionen, während sie ausgeliefert werden, und werden ermutigt, Feedback zu geben, das die Roadmap direkt prägt.

Um teilzunehmen oder mehr zu erfahren, senden Sie eine E-Mail an `GRP-AEM-ASSETS-BRANDAWAREMETADATA@adobe.com`.

#### Assets Onboarding Agent {#assets-onboarding-agent-beta}

Wenn Experience Manager Assets für Ihr Unternehmen neu ist, können Sie sich für das **Assets Onboarding Agent Beta-Programm** anmelden, über das Sie Zugriff auf die folgenden AEM Brand Experience AI-Kenntnisse für das Onboarding erhalten:

* Führt Benutzende durch die DAM-Einrichtung und Migrationsplanung, indem ein konversativer Workflow verwendet wird, um Geschäftsanforderungen zu erfassen und Empfehlungen zur Strukturierung einer AEM Assets-Bereitstellung zu geben.

* Erstellt zentrale AEM Assets-Konfigurationsartefakte wie Ordnerhierarchien, Tag-Taxonomien und Metadatenformulare und kann helfen, Massenimportaufträge auszuführen, um das Onboarding zu beschleunigen.

**Warum teilnehmen?**

* Schnellere Live-Schaltung mit einer einsatzbereiten DAM-Umgebung durch Eliminieren sich wiederholender, manueller Schritte mit KI-Unterstützung.

* Geringerer Betriebsaufwand durch automatisierte Konfiguration und Vorbereitung von Ordnern, Tags, Metadaten und Asset-Importen.

* Verbessern Sie die Konsistenz und Governance und stellen Sie die Einhaltung der Best Practices durch ein kuratiertes Einrichtungserlebnis mit intelligenten, auf Ihr Unternehmen zugeschnittenen Empfehlungen sicher.

Um teilzunehmen oder mehr zu erfahren, senden Sie eine E-Mail an `GRP-AEM-ONBOARDING-AGENT@adobe.com`.

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Universeller Editor {#universal-editor}

Eine vollständige Liste der Versionen des universellen Editors finden Sie [hier](/help/release-notes/universal-editor/current.md).

## Generieren von Varianten {#generate-variations}

Eine vollständige Liste der Versionen für das Generieren von Varianten finden Sie [hier](/help/generative-ai/release-notes-generate-variations.md).

## Versionshinweise zu Experience Cloud {#experience-cloud}

Informationen zu Versionen anderer Experience Cloud-Anwendungen finden Sie [hier](https://experienceleague.adobe.com/de/docs/release-notes/experience-cloud/current).

