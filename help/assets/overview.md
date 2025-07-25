---
title: Einführung in Assets as a Cloud Service für Digital Asset Management in AEM
description: Einführung in Assets as a Cloud Service für Digital Asset Management in AEM
source-git-commit: 707c2125b3a5401cd5b0ebe19f3bc9c46302b697
workflow-type: tm+mt
source-wordcount: '5032'
ht-degree: 38%

---


# Einführung in Assets as a Cloud Service für Digital Asset Management in AEM {#assets-as-cloud-service-digital-asset-management-aem}

Adobe Experience Manager Assets as a Cloud Service bietet eine Cloud-native PaaS-Lösung für Unternehmen, mit der sie nicht nur ihre Vorgänge in Digital Asset Management und Dynamic Media schnell und effektiv durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie künstliche Intelligenz und maschinelles Lernen nutzen können, und zwar innerhalb eines Systems, das immer aktuell, verfügbar und lernbereit ist.

Adobe bietet stabile DAM-Lösungen (Digital Asset Management), mit denen Sie Ihre digitalen Assets optimal nutzen können. Adobe Experience Manager Assets verfügt über zwei separate Erlebnisse, die dasselbe Cloud Services-Repository verwenden, um Ihre Anforderungen zu erfüllen. Informationen zu personabasierten Erlebnissen für AEM Assets finden Sie unter [Verfügbare personabasierte Erlebnisse für Digital Asset Management](#persona-based-experiences).

Informationen zu den Angeboten von AEM Assets Ultimate und AEM Assets Prime finden Sie unter [Assets as a Cloud Service Ultimate](/help/assets/assets-ultimate-overview.md) und [Assets as a Cloud ServicePrime ](/help/assets/assets-prime.md).

Zu den wichtigsten Funktionen von Adobe Digital Asset Management gehören:

![add-tags](assets/aem-assets-features-landing-page.png)


>[!BEGINTABS]

>[!TAB Asset-Aufnahme]

## Asset-Aufnahme {#asset-ingestion}

Verwenden Sie die Massenimportfunktion, um eine große Anzahl von Assets direkt aus einer Datenquelle wie Azure, AWS, Google Cloud, Dropbox und OneDrive in Assets as a Cloud Service zu importieren.

Sie können den Massenimportvorgang mit der Admin- oder Assets-Ansicht durchführen. Die Assets-Ansicht bietet mehr Datenquellenoptionen als die Admin-Ansicht.

Zusätzlich zur Webbrowser-Benutzeroberfläche unterstützt Experience Manager auch andere Clients auf dem Desktop. Sie bieten außerdem ein Upload-Erlebnis, ohne dass der Browser aufgerufen werden muss.

* Adobe Asset Link bietet Zugriff auf Assets aus Experience Manager in Adobe Photoshop-, Adobe Illustrator- und Adobe InDesign-Desktop-Programmen. Sie können das aktuell geöffnete Dokument direkt über die Adobe Asset Link-Benutzeroberfläche in diesen Desktop-Programmen in Experience Manager hochladen.

* Das Experience Manager-Desktop-Programm vereinfacht die Arbeit mit Assets auf dem Desktop, unabhängig vom Dateityp oder dem nativen Programm, das diese verarbeitet. Es ist nützlich, um Dateien in verschachtelten Ordnerhierarchien aus Ihrem lokalen Dateisystem hochzuladen, da der Browser-Upload nur das Hochladen flacher Dateilisten unterstützt.

Verwenden Sie diese Links, um auf eine detaillierte Dokumentation zu diesen Tools zur Asset-Aufnahme zuzugreifen:

<table>
<td>
   <a href="/help/assets/bulk-import-assets-view.md">
   <img alt="Tool für den Massenimport" src="./assets/bulk-images.jpeg" />
   </a>
   <div>
      <a href="/help/assets/bulk-import-assets-view.md">
      <strong>Verwenden des Tools für den Massenimport</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie eine große Anzahl von Assets direkt aus einer Datenquelle importieren</em>
   </p>
</td>


<td>
   <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/using">
   <img alt="Verwenden des AEM-Desktop-Programms" src="./assets/desktop-app-upload.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/using">
      <strong>Verwenden des AEM-Desktop-Programms</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie mit dem AEM-Desktop-Programm Dateien in verschachtelten Ordnerhierarchien von Ihrem lokalen Dateisystem hochladen.</em>
   </p>
</td>
<td>
   <a href="https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html">
   <img alt="Verwenden von Adobe Asset Link" src="./assets/adobe-asset-link.jpeg" />
   </a>
   <div>
      <a href="https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html">
      <strong>Adobe Asset Link verwenden</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Assets mithilfe von Creative Cloud-Programmen in Experience Manager hochladen.</em>
   </p>
</td>
</table>

>[!TAB KI-gestützte Funktionen]

**Smart-Tags**: Smart-Tags verwenden das KI-Framework von Adobe Sensei, um den Bilderkennungsalgorithmus auf Ihre Tag-Struktur und Ihre Unternehmenstaxonomie zu trainieren. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden. AEM wendet standardmäßig automatisch Smart-Tags auf hochgeladene Assets an.

**Intelligentes farbbasiertes Tagging und Suche**: AEM Assets verwendet Adobe Sensei-KI-Funktionen, um zwischen Farben in einem Bild zu unterscheiden und diese bei der Aufnahme automatisch als Tags anzuwenden. Diese Tags ermöglichen ein verbessertes Sucherlebnis, das auf der Farbkomposition des Bildes basiert.

**KI-generierte Metadaten**: AEM Assets verwendet KI zum automatischen Generieren von Metadaten, einschließlich Titel, Beschreibung und Schlüsselwörtern. Diese KI-generierten Felder verbessern die Genauigkeit von Metadaten und erleichtern die Suche, Kategorisierung und Empfehlung von Assets. Dieser Ansatz verbessert nicht nur die Effizienz durch die Eliminierung des manuellen Taggings, sondern stellt auch Konsistenz und Skalierbarkeit über große Mengen digitaler Inhalte hinweg sicher.

**KI-gestützte Massenumbenennung von Assets**: Mit der [Assets-Ansicht können Sie mithilfe von künstlicher Intelligenz mehrere Assets gleichzeitig umbenennen](/help/assets/bulk-rename-assets-view.md). Sie können mehrere Dateien gleichzeitig auswählen und sie alle gemeinsam umbenennen. Einige der Eingabeaufforderungen zum Umbenennen der Konversation umfassen *Ändern aller Dateien in &#39;meine-Datei&#39; und Anhängen einer inkrementellen Zahl* und *Präfix für die Dateien mit 001, 002 usw. und ins Englische*.

<table>
<td>
   <a href="/help/assets/smart-tags.md">
   <img alt="Smart-Tags in AEM Assets" src="./assets/smart-tags-ai.jpeg" />
   </a>
   <div>
      <a href="/help/assets/smart-tags.md">
      <strong>Hinzufügen von KI-Smart-Tags zu Assets</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie automatisch Smart-Tags auf hochgeladene Assets anwenden.</em>
   </p>
</td>


<td>
   <a href="/help/assets/color-tag-images.md">
   <img alt="Hinzufügen intelligenter farbbasierter Tags" src="./assets/color-tags.jpg" />
   </a>
   <div>
      <a href="/help/assets/manage-notifications-assets-view.md">
      <strong>Hinzufügen intelligenter farbbasierter Tags</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie farbbasierte Tags bei der Aufnahme automatisch anwenden.</em>
   </p>
</td>
<td>
   <a href="/help/assets/metadata-assets-view.md">
   <img alt="KI-generierte Metadaten" src="./assets/ai-generated-metadata-landing.jpg" />
   </a>
   <div>
      <a href="/help/assets/metadata-assets-view.md">
      <strong>KI-generierte Metadaten</strong>
      </a>
   </div>
   <p>
      <em>Verwenden von KI zum Generieren von Asset-Metadaten wie Titel und Beschreibung. </em>
   </p>
</td>
</table>

**Kontextuelle Suche**: Mit AEM Assets können Sie nach im Repository verfügbaren Assets suchen, indem Sie Textaufforderungen definieren. Experience Manager Assets wandelt diese Text-Prompts automatisch in Suchfilter um und zeigt die Suchergebnisse an. Sie können die automatischen Filter über den Bereich Filter anzeigen und ändern, um die Suchergebnisse weiter einzugrenzen. Zu den Beispielen für Gesprächsaufforderungen gehören *Bilder von mindestens 200 Pixel Höhe und 100 Pixel Breite mit Strand und klarem Himmel* und *Ich benötige Bilder von blauem Himmel mit einer Höhe von 1500 und 2500 Pixel, die im letzten Monat erstellt wurden und nicht abgelaufen sind und genehmigt wurden*.

**Generieren von Assets mit Adobe Firefly in AEM**: Mit AEM Assets können Sie ein Asset mithilfe von Adobe Firefly in Echtzeit generieren, wenn Ihre Suchanfrage keine Ergebnisse zurückgibt. AEM Assets ermöglicht es Ihnen dann auch, das generierte Bild aus der AEM Assets-Benutzeroberfläche in das AEM Assets-Repository hochzuladen.

**Integration mit Adobe Express**: AEM Assets integriert sich nativ mit Adobe Express, wodurch Sie direkt über die Adobe Express-Benutzeroberfläche auf die in AEM Assets gespeicherten Assets zugreifen können. Sie können in Express auch die künstliche Intelligenz von Adobe Firefly verwenden, um Bilder mithilfe einfacher Textaufforderungen zu generieren und sie auf der Express-Arbeitsfläche zu platzieren. Sie können dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern.

<table>
<td>
   <a href="/help/assets/search-assets-view.md#contextual-search">
   <img alt="Kontextsuche" src="./assets/ai-based-search.jpg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md#contextual-search">
      <strong>Kontextuelle Suche</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie mit einfachen Textaufforderungen nach Assets suchen.</em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-view.md#search-firefly">
   <img alt="Generieren von Assets mit Adobe Firefly" src="./assets/adobe-firefly.jpg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md#search-firefly">
      <strong>Generieren von Assets mit Adobe Firefly</strong>
      </a>
   </div>
   <p>
      <em>Generieren von Assets in Echtzeit mit Adobe Firefly.</em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Integration mit Adobe Express" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong>Integration mit Adobe Express</strong>
      </a>
   </div>
   <p>
      <em>Verwenden von Adobe Express-KI-Funktionen in der Benutzeroberfläche von AEM Assets.</em>
   </p>
</td>
</table>

**Intelligente Bildbearbeitung**: Die intelligente Bildbearbeitung sorgt für eine noch bessere Leistung bei der Bereitstellung von Bild-Assets, indem sie das Format und die Dateigröße eines Bildes automatisch auf der Grundlage der Browser-Funktionen eines Kunden optimiert. Es funktioniert mit Ihren vorhandenen Bildvorgaben und verwendet Intelligenz bei der Bereitstellung. Diese Intelligenz reduziert die Größe von Bilddateien je nach Browser und Geschwindigkeit der Netzwerkverbindung weiter.

**Smartes Zuschneiden**: Eine Adobe Sensei-KI-Funktion, mit der der Fokus in einem Bild oder Video automatisch erkannt und zugeschnitten wird, um ihn beizubehalten. Es erfasst den gewünschten Blickpunkt unabhängig von der Bildschirmgröße und beseitigt somit mühsame manuelle Aufgaben und liefert hochwertige, schnell ladende Bilder und Videos, die auf jedem Gerät oder Bildschirm gut aussehen.

**KI-generierte**: KI-generierte Videountertitel in Adobe Dynamic Media verwenden künstliche Intelligenz, um Untertitel automatisch für Videoinhalte zu generieren. Diese Funktion soll die Barrierefreiheit und das Anwendererlebnis verbessern, indem akkurate Untertitel bereitgestellt werden. Beschriftungen werden aus dem Originalaudio generiert, zusätzliche Audiospuren oder zusätzliche Beschriftungen werden auf der Registerkarte `Captions and Audio` auf der Seite Videoeigenschaften bereitgestellt. Es werden mehr als 60 Sprachen unterstützt. Die Untertitel können dabei vor der Veröffentlichung des Videos überprüft und in einer Vorschau angezeigt werden.
<table>
<td>
   <a href="/help/assets/dynamic-media/imaging-faq.md">
   <img alt="Intelligente Bildbearbeitung" src="./assets/smart-imaging.jpg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/imaging-faq.md">
      <strong>Intelligente Bildbearbeitung</strong>
      </a>
   </div>
   <p>
      <em>Optimieren Sie das Format und die Dateigröße eines Bildes auf der Grundlage der Browser-Fähigkeiten und der Netzwerkgeschwindigkeit eines Benutzers.</em>
   </p>
</td>


<td>
   <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use.html">
   <img alt="Smartes Zuschneiden" src="./assets/smart-cropping.jpg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use.html">
      <strong>Smartes Zuschneiden</strong>
      </a>
   </div>
   <p>
      <em>Verwenden Sie KI, um den Fokus in einem Bild oder Video automatisch zu erkennen und zuzuschneiden, um ihn beizubehalten</em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media/video.md">
   <img alt="KI-generierte Videountertitel" src="./assets/videos-with-captions.jpg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/video.md">
      <strong>KI-generierte Videountertitel</strong>
      </a>
   </div>
   <p>
      <em>Verwenden Sie künstliche Intelligenz, um Untertitel automatisch für Videoinhalte zu generieren. </em>
   </p>
</td>
</table>

>[!TAB Asset-Erkennung]

## Asset-Erkennung {#asset-discovery}

Nachdem Sie Ihre Assets in AEM Assets importiert haben, müssen Sie die richtigen Assets schnell aus einer so umfangreichen Sammlung finden.

AEM Assets bietet Funktionen, die Ihnen den schnellen Zugriff auf das richtige Asset erleichtern, wie KI-generiertes Tagging (Smart-Tags), benutzerdefinierte Metadaten und Funktionen, die das Sucherlebnis für Sie optimieren.

**Metadatenverwaltung**: Metadaten sind der wichtigste Aspekt beim Starten Ihrer Asset-Management-Journey. Die Verwaltung von Metadaten entzieht sich komplett der Kontrolle der Administratoren, sobald die Assets an die Benutzer verteilt werden. Effektive Asset-Metadaten sorgen für eine bessere Suche, die das letztendliche Ziel für jedes DAM-Tool ist.


**Metadaten-Forms**: Assets as a Cloud Service bietet standardmäßig viele Standard-Metadatenfelder. Wenn Sie zusätzliche Metadatenanforderungen haben und mehr Metadatenfelder benötigen, um geschäftsspezifische Metadaten hinzuzufügen. Mit Metadatenformularen können Unternehmen benutzerdefinierte Metadatenfelder zur Seite „Details“ eines Assets hinzufügen. Die geschäftsspezifischen Metadaten verbessern die Verwaltung und Erkennung der Assets. Sie können Formulare von Grund auf neu erstellen oder ein vorhandenes Formular wiederverwenden.

<table>
<td>
   <a href="/help/assets/metadata-assets-view.md">
   <img alt="Ansicht „Metadaten-Assets verwalten“" src="./assets/manage-metadata-assets-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/metadata-assets-view.md">
      <strong>Verwalten von Metadaten in der Assets-Ansicht</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Metadaten und Metadatenformulare mithilfe der Assets-Ansicht verwalten.</em>
   </p>
</td>


<td>
   <a href="https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager-blogs/how-to-manage-metadata-before-and-after-migrating-to-aem-assets/ba-p/744298">
   <img alt="Best Practices für die Metadatenverwaltung" src="./assets/metadata-best-practices.jpeg" />
   </a>
   <div>
      <a href="https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager-blogs/how-to-manage-metadata-before-and-after-migrating-to-aem-assets/ba-p/744298">
      <strong>Best Practices für die Metadatenverwaltung</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Metadaten vor und nach der Migration Ihrer Assets zu AEM verwalten.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-metadata.md">
   <img alt="Verwenden von Adobe Asset Link" src="./assets/metadata-management-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-metadata.md">
      <strong>Verwalten von Metadaten in der Admin-Ansicht</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Metadaten und Metadatenformulare mithilfe der Admin-Ansicht verwalten.</em>
   </p>
</td>
</table>

**Smart-Tags**: Smart-Tags verwenden das KI-Framework von Adobe Sensei, um den Bilderkennungsalgorithmus auf Ihre Tag-Struktur und Ihre Unternehmenstaxonomie zu trainieren. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden. AEM wendet standardmäßig automatisch Smart-Tags auf hochgeladene Assets an.

**Suche nach Assets**: Sobald Sie die richtigen Metadaten eingerichtet haben, können Sie mit AEM Assets mithilfe verschiedener Operatoren, Platzhalter, erweiterter Abfragen und benutzerdefinierter Filter suchen.

**Kontextuelle Suche**: AEM Assets bietet auch die Funktion „Kontextuelle Suche“, mit der Sie nach im Repository verfügbaren Assets suchen können, indem Sie Textaufforderungen definieren. Experience Manager Assets wandelt diese Text-Prompts automatisch in Suchfilter um und zeigt die Suchergebnisse an. Im Bereich „Filter“ können Sie automatische Filter anzeigen und ändern, um die Suchergebnisse weiter einzugrenzen.

<table>
<td>
   <a href="/help/assets/smart-tags.md">
   <img alt="Smart-Tags in AEM Assets" src="./assets/smart-tags-ai.jpeg" />
   </a>
   <div>
      <a href="/help/assets/smart-tags.md">
      <strong>Hinzufügen von Smart-Tags zu Assets</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie automatisch Smart-Tags auf hochgeladene Assets anwenden.</em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-view.md">
   <img alt="Assets-Ansicht durchsuchen" src="./assets/search-assets-view-landing.jpeg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md">
      <strong>Suche nach Assets in der Assets-Ansicht</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie die kontextbezogene Suche und andere Suchfunktionen in der Assets-Ansicht effektiv verwenden können.</em>
   </p>
</td>
<td>
   <a href="/help/assets/search-best-practices.md">
   <img alt="Best Practices für die Suche" src="./assets/search-best-practices.jpeg" />
   </a>
   <div>
      <a href="/help/assets/search-best-practices.md">
      <strong>Best Practices für die Suche</strong>
      </a>
   </div>
   <p>
      <em>Beschreibt verschiedene Szenarien, die AEM-Benutzenden dabei helfen, einfache bis erweiterte Suchen durchzuführen.</em>
   </p>
</td>
</table>

>[!TAB Asset-Governance]

## Asset-Management und Governance {#asset-management-governance}

Nachdem Sie Ihre Assets in AEM Assets hochgeladen und die Metadaten festgelegt haben, um eine bessere Auffindbarkeit zu gewährleisten, können Sie über die benutzerfreundliche Oberfläche der Assets-Ansicht verschiedene Aufgaben zur Verwaltung digitaler Assets ausführen.

**Asset-Management-**: Zu den grundlegenden Aufgaben gehören Suchen, Herunterladen, Verschieben, Kopieren, Umbenennen, Löschen, Aktualisieren und Bearbeiten.

Sie können auch Asset-Versionen verwalten, den Asset-Status festlegen und den Asset-Ablauf festlegen.

**Meine Workspace**: Die Assets-Ansicht enthält auch einen anpassbaren Arbeitsbereich, der Widgets für den bequemen Zugriff auf wichtige Bereiche der Assets-Benutzeroberfläche und Informationen bereitstellt, die für Sie am relevantesten sind. Diese Seite ist eine zentrale Anlaufstelle, die einen Überblick über Ihre Arbeitselemente und schnellen Zugriff auf wichtige Workflows bietet.

**Content Credentials**: Eine weitere leistungsstarke Funktion, die AEM Assets unterstützt, ist Content Credentials. Marken machen sich mehr denn je Gedanken um die Transparenz von Inhalten, die Offenlegung von KI und die Verhinderung der Manipulation von Assets. Die Content Authenticity Initiative (CAI) von Adobe erstellt Tools, die dem technischen Standard der Coalition for Content Provenance and Authenticity (C2PA) entsprechen. Content Credentials sind eine neue Art verschlüsselter, manipulationssicherer Metadaten. Sie können Betrachtende dabei unterstützen, die Herkunft von Inhalten zu verstehen und dazu beitragen, die Integrität von Marken-Assets sicherzustellen. Sie können eine breite Palette von Herkunftsdaten enthalten, die Einblicke in den Verlauf eines digitalen Assets bieten.

<table>
<td>
   <a href="/help/assets/manage-organize-assets-view.md">
   <img alt="Asset-Management-Aufgaben" src="./assets/asset-management.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-organize-assets-view.md">
      <strong>Asset-Management-Aufgaben</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie einige grundlegende und erweiterte Asset-Management-Aufgaben ausführen.</em>
   </p>
</td>


<td>
   <a href="/help/assets/my-workspace-assets-view.md">
   <img alt="MT WORKSPACE" src="./assets/my-workspace.jpeg" />
   </a>
   <div>
      <a href="/help/assets/my-workspace-assets-view.md">
      <strong>Mein Workspace</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie mit My Workspace arbeiten können, um schnell auf wichtige Bereiche der Assets-Benutzeroberfläche zuzugreifen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/content-credentials.md">
   <img alt="Content Credentials" src="./assets/content-credentials.jpeg" />
   </a>
   <div>
      <a href="/help/assets/content-credentials.md">
      <strong>Content Credentials</strong>
      </a>
   </div>
   <p>
      <em>Gewinnen Sie Einblicke in den Verlauf eines digitalen Assets mit Content Credentials.</em>
   </p>
</td>
</table>

**Sammlungen**: Mit AEM Assets können Sie Ihre Assets auch in Sammlungen organisieren. Eine Sammlung ist ein Satz von Assets, Ordnern oder sonstigen Sammlungen in der Adobe Experience Manager Assets-Ansicht. Anhand von Sammlungen können Assets von mehreren Benutzenden gemeinsam verwendet werden. Im Gegensatz zu Ordnern kann eine Sammlung Assets von verschiedenen Speicherorten enthalten. Sie können mehrere Sammlungen für eine Benutzerin bzw. einen Benutzer freigeben. Jede Sammlung enthält Verweise auf Assets. Die referenzielle Integrität von Assets wird sammlungsübergreifend aufrechterhalten.

**Benachrichtigungen**: Assets-Ansichtsbenachrichtigungen ermöglichen es Ihnen, die Vorgänge zu überwachen, die mit den im Repository verfügbaren Assets, Ordnern oder Sammlungen durchgeführt werden. Sie müssen den Inhalt auswählen und abonnieren, für den die Benachrichtigungen an Sie gesendet werden sollen. Sie können auch die Kategorien konfigurieren, für die die Benachrichtigungen an Sie gesendet werden.

**Doppelte Assets erkennen**: AEM Assets unterstützt auch die Erkennung doppelter Assets. Wenn ein DAM-Benutzer ein oder mehrere Assets hochlädt, die bereits im Repository vorhanden sind, erkennt Experience Manager die Duplizierung und benachrichtigt den Benutzer.



<table>
<td>
   <a href="/help/assets/manage-collections-assets-view.md">
   <img alt="Verwalten von Sammlungen" src="./assets/manage-collections.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-collections-assets-view.md">
      <strong>Sammlungen verwalten</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Ihre Assets in Sammlungen organisieren können, um Assets effizient freizugeben.</em>
   </p>
</td>


<td>
   <a href="/help/assets/manage-notifications-assets-view.md">
   <img alt="Benachrichtigungen festlegen" src="./assets/manage-notifications.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-notifications-assets-view.md">
      <strong>Benachrichtigungen festlegen</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Benachrichtigungen festlegen, um die Vorgänge zu überwachen, die mit Assets, Ordnern oder Sammlungen durchgeführt werden.</em>
   </p>
</td>
<td>
   <a href="/help/assets/detect-duplicate-assets.md">
   <img alt="Erkennen doppelter Assets" src="./assets/duplicate-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/detect-duplicate-assets.md">
      <strong>Erkennen doppelter Assets</strong>
      </a>
   </div>
   <p>
      <em>Erkennen doppelter Assets, die in AEM Assets hochgeladen wurden, und Benachrichtigen der Benutzer.</em>
   </p>
</td>
</table>

>[!TAB Integrationen]

## Integration mit Adobe und Nicht-Adobe-Programmen {#integration-adobe-non-adode-apps}

AEM Assets kann nahtlos mit verschiedenen Adobe- und Nicht-Adobe-Anwendungen integriert werden. Im Folgenden finden Sie eine Zusammenfassung der verfügbaren Integrationen:

+++**Integration mit Adobe und Nicht-Adobe-Programmen**

* **Dynamic Media mit OpenAPI-Funktionen**: [Dynamic Media mit OpenAPI](/help/assets/dynamic-media-open-apis-overview.md)Funktionen bietet einen umfassenden Satz von [Suche](/help/assets/search-assets-api.md) und [Bereitstellung](/help/assets/deliver-assets-apis.md)-APIs. Damit können Entwickler die Bereitstellung von Assets einfach in ihre Programme integrieren. Zu den Anwendungen gehören Adobe sowie Anwendungen von Drittanbietern. Es bietet eine Benutzeroberfläche für den Micro Frontend-Asset-Wähler zum Suchen und Auswählen genehmigter Assets. Die Auswahl kann mühelos in jede Anwendung integriert werden, die auf JavaScript-Frameworks wie React JS, Angular JS und Vanilla JS basiert.

* **Micro-Frontend-Asset-Selektor**: Der Micro-Frontend-Asset-Selektor bietet eine Benutzeroberfläche, die sich problemlos in das Experience Manager Assets-Repository integrieren lässt, sodass Sie die im Repository verfügbaren digitalen Assets durchsuchen und für die Erstellung von Applikationen verwenden können.
Sie können den Asset-Wähler in eine Adobe oder ein Nicht-Adobe-Programm integrieren.

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="Übersicht über Dynamic Media mit OpenAPI-Funktionen" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong>Übersicht über die Funktionen von Dynamic Media mit OpenAPI</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie mehr über die wichtigsten Vorteile und wie Sie diese aktivieren können. </em>
   </p>
</td>


<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Beschränken des Zugriffs auf Assets in Experience Manager" src="./assets/restrict-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Beschränken des Zugriffs auf Assets in Experience Manager</strong>
      </a>
   </div>
   <p>
      <em> Konfigurieren Sie Rollen, um den Zugriff auf genehmigte Assets zu beschränken.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="Asset-Wähler" src="./assets/integration-asset-selector.jpeg" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong>Micro-Front-End-Asset-Selektor</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie den Micro-Frontend-Asset-Wähler mit einer Adobe- oder Nicht-Adobe-Anwendung integrieren.</em>
   </p>
</td>
</table>

+++

+++**Native Integration mit Adobe-Programmen**

* **Integration mit Adobe Workfront**: [!DNL Adobe Workfront] ist ein Programm für das Arbeits-Management, mit dem Sie den gesamten Arbeitszyklus an einem Ort verwalten können. Die Integration von [!DNL Workfront] und [!DNL Adobe Experience Manager Assets] ermöglicht es Unternehmen, die Geschwindigkeit von Inhalten und die Zeit bis zur Markteinführung zu verbessern, indem sie Workfront und Digital Asset Management miteinander verbinden. Im Rahmen der Verwaltung ihrer Arbeit in Workfront haben Benutzer Zugriff auf die erforderlichen Dokumente und Bilder.

  Adobe bietet die [ &quot; [!DNL Workfront] &quot;  [!DNL Adobe Experience Manager Assets]  „nativ](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html?lang=de).

* **Integration mit Figma**: AEM Assets integriert sich nativ mit Figma, wodurch Designer direkt auf die in AEM Assets gespeicherten Assets in der Figma-Benutzeroberfläche zugreifen können. Sie können in AEM Assets verwaltete Inhalte auf der Figma-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern. Um auf den auf der Figma Community-Seite verfügbaren AEM Assets-Connector zuzugreifen, klicken Sie [hier](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector).

* **Native Integration mit Adobe Express**: AEM Assets integriert sich nativ mit Adobe Express, wodurch Sie direkt über die Adobe Express-Benutzeroberfläche auf die in AEM Assets gespeicherten Assets zugreifen können. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern.

* **AEM Assets mit Creative Cloud verbinden**: Experience Manager Assets kann eine Verbindung zu einer Creative Cloud-Berechtigung herstellen, die einer anderen IMS-Organisation bereitgestellt wird, um die neuesten Creative Cloud-Integrationen in AEM Assets, einschließlich Express und Creative Cloud Libraries, einfach zu verwenden. Wenn Ihre Creative Cloud-Produkte und AEM Assets für verschiedene IMS-Organisationen bereitgestellt werden, können Sie eine Verbindung zu einer anderen Creative Cloud-Organisation herstellen, um integrierte Workflows zwischen den beiden Lösungen ausführen zu können.

<table>
<td>
   <a href="/help/assets/workfront-integrations.md">
   <img alt="Integration mit Adobe Workfront" src="./assets/integration-adobe-workfront.jpeg" />
   </a>
   <div>
      <a href="/help/assets/workfront-integrations.md">
      <strong>Integration mit Adobe Workfront</strong>
      </a>
   </div>
   <p>
      <em>Integration mit Adobe Workfront, um den gesamten Arbeitszyklus an einem Ort zu verwalten.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-collections-assets-view.md">
   <img alt="Integration mit Figma" src="./assets/integration-commerce.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-collections-assets-view.md">
      <strong>Integration mit Figma</strong>
      </a>
   </div>
   <p>
      <em>Greifen Sie über die Figma-Benutzeroberfläche auf die in AEM Assets gespeicherten Assets zu</em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Native Integration in Adobe Express" src="./assets/integration-adobe-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong>Native Integration mit Adobe Express</strong>
      </a>
   </div>
   <p>
      <em>Platzieren Sie in AEM Assets verfügbare Assets auf der Express-Arbeitsfläche und speichern Sie aktualisierte Assets in AEM. </em>
   </p>
</td>


</table>


* **Integration mit Adobe Journey Optimizer**: Zusammenführen von Marketing- und Kreativ-Workflows mithilfe von Adobe Experience Manager Assets. Greifen Sie auf Assets as a Cloud Service zu, das nativ mit Adobe Journey Optimizer integriert ist, um digitale Assets zu speichern, zu verwalten, zu erkunden und zu verteilen. Es bietet ein zentrales Repository mit Assets, die Sie für Ihre Nachrichten verwenden können.

* **Integration mit Commerce**: Adobe Experience Manager (AEM) Assets Integration für Commerce kombiniert die leistungsstarken Funktionen von AEM as a Digital Asset Management (DAM) mit Adobe Commerce, um E-Commerce-Erlebnisse zu verbessern. Diese Funktionen werden bereitgestellt, indem Commerce-Projekte mit der leistungsstarken Asset-Management-Umgebung von AEM verbunden werden, um eine nahtlose, skalierbare und effiziente Möglichkeit zur Verwaltung und Bereitstellung von Assets in Commerce-Storefronts zu bieten.
* **Integrieren von AEM Assets mit dokumentbasierten Authoring-Flüssen für Edge Delivery Services**: Wenn [!DNL AEM Assets] mit Ihren dokumentbasierten Authoring-Tools wie [!DNL Microsoft Word] oder [!DNL Google Docs] integriert ist, steht eine Asset-Auswahl in Ihrem Authoring-Tool zur Verfügung. Verwenden Sie diesen Asset-Wähler, um auf [!DNL AEM Assets] zuzugreifen und genehmigte Assets in Ihren Inhalt einzufügen.
Wenn Sie bereits über eine [!DNL Edge Delivery Services]-Website verfügen, finden Sie in der [[!DNL AEM Assets] Plug-in](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md)-Dokumentation Informationen zur Integration von [!DNL AEM Assets] in Ihr vorhandenes [!DNL AEM].

* **Integrieren von [!DNL AEM Assets] mit [!DNL Universal Editor]-basierten Authoring-Flüssen für[!DNL Edge Delivery Services]**: Richten Sie die [!DNL Universal Editor] für die Integration mit [!DNL AEM Assets] ein. Durch diese Integration können Sie [!DNL Dynamic Media with OpenAPI capabilities] verwenden, um Assets bereitzustellen.

   * Unter [Konfiguration in [!DNL Edge Delivery] Site](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) erfahren Sie, wie Sie eine benutzerdefinierte Asset-Auswahlfunktion in [!DNL Universal Editor] hinzufügen. Mit der benutzerdefinierten Asset-Auswahl können Sie Assets direkt in Ihre [!DNL Universal Editor] einfügen.
   * Unter [Übersicht über Erweiterungen](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) erfahren Sie, wie Sie beim Authoring in [!DNL AEM Assets] auf [!DNL Universal Editor] zugreifen und die Assets einfügen können.

<table>
<td>
   <a href="https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/combine/assets">
   <img alt="Integration mit Adobe Journey Optimizer" src="./assets/integration-figma.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/combine/assets">
      <strong>Integration mit Adobe Journey Optimizer</strong>
      </a>
   </div>
   <p>
      <em>Zusammenführen von Marketing- und Kreativ-Workflows mithilfe der Integration mit AJO</em>
   </p>
</td>
<td>
   <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/aem-asset-management/aem-assets-integration">
   <img alt="Integration mit Commerce" src="./assets/integration-ajo.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/aem-asset-management/aem-assets-integration">
      <strong>Integration mit Commerce</strong>
      </a>
   </div>
   <p>
      <em>Integration von AEM Assets mit Commerce zur Verbesserung von eCommerce-Erlebnissen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
   <img alt="Integrieren von AEM Assets mit EDS" src="./assets/integrate-ue-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
      <strong>Integrieren von AEM Assets mit EDS</strong>
      </a>
   </div>
   <p>
      <em>Integrieren von AEM Assets mit dokumentbasierten und universellen Editor-basierten Authoring-Flüssen.</em>
   </p>
</td>
</table>

+++

>[!TAB Asset-Aktivierung]

## Asset-Aktivierung {#asset-activation}

Erschließen Sie das volle Potenzial Ihrer digitalen Assets mit AEM Assets mithilfe von Content Hub zu Dynamic Media - einschließlich leistungsstarker OpenAPI-Funktionen. AEM Assets bietet ein umfassendes Lösungspaket, mit dem die Asset-Umwandlung optimiert und die Bereitstellung kanalübergreifend optimiert werden kann.

+++**Content Hub**

Content Hub ist als Teil von Experience Manager Assets as a Cloud Service für die Demokratisierung des Zugriffs auf Markeninhalte für Unternehmen und ihre Geschäftspartner verfügbar. Der Schwerpunkt liegt auf der Verteilung von Assets zur skalierten Aktivierung und der Erstellung von Markeninhaltsvarianten, um die Marketing-Agilität zu verbessern.

Content Hub bietet die folgenden Hauptvorteile:

* **Suchen und Freigeben aller markenbestätigten Assets in einem intuitiven Portal**: AEM Assets dient als zentrale Datenquelle, und alle genehmigten Assets sind automatisch in Content Hub in einer flachen Hierarchie verfügbar, um das Sucherlebnis zu verbessern.

* **Konfigurierbare Benutzeroberfläche**: Die gängigsten Eigenschaften in Content Hub, wie Suchfilter, Felder, die beim Hinzufügen oder Importieren von Assets verfügbar sind, Asset-Eigenschaften, Bannerinhalte für das Branding, sind konfigurierbar und ein Administrator kann die Content Hub-Benutzeroberfläche einfach entsprechend seinen Anforderungen konfigurieren.

* **Nicht-Kreativen die Möglichkeit geben, Inhalte zu bearbeiten und neu zu mischen, während sie bei der Marke bleiben**: Mit Content Hub können Sie neue Inhalte mit Adobe Express erstellen (wenn Sie über Adobe Express-Berechtigungen verfügen). Sie können vorhandene Inhalte mit anwenderfreundlichen Tools bearbeiten, Markenvarianten mit Vorlagen und Markenelementen erstellen und neue Inhalte mit den neuesten GenAI-Funktionen von Adobe Firefly erstellen.

* **Gewinnen Sie Erkenntnisse darüber, wie Inhalte teamübergreifend verwendet werden**: [!DNL Content Hub] bietet wertvolle Einblicke in Assets, indem Sie eine gängige Herausforderung bewältigen, der Marketing-Stakeholder häufig begegnen - Asset-Nutzungsstatistiken, die in Marketing-Kampagnen, Kanälen und verschiedenen Regionen verwendet werden. Durch das Erlangen eines klaren Verständnisses der Leistung und Beliebtheit der Assets, liefert es verwertbare Einblicke, die für die Verbesserung des Benutzererlebnisses unerlässlich sind.

<table>
<td>
   <a href="/help/assets/product-overview.md">
   <img alt="Überblick über Content Hub" src="./assets/content-hub-overview.jpeg" />
   </a>
   <div>
      <a href="/help/assets/product-overview.md">
      <strong>Übersicht über Content Hub</strong>
      </a>
   </div>
   <p>
      <em> Erfahren Sie mehr über Content Hub, seine wichtigsten Vorteile und wie Sie darauf zugreifen können. </em>
   </p>
</td>


<td>
   <a href="/help/assets/configure-content-hub-ui-options.md">
   <img alt="Konfigurieren der Benutzeroberfläche von Content Hub" src="./assets/content-hub-configuration.jpeg" />
   </a>
   <div>
      <a href="/help/assets/configure-content-hub-ui-options.md">
      <strong>Konfigurieren der Benutzeroberfläche von Content Hub</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie die in der Benutzeroberfläche von Content Hub verfügbaren Optionen konfigurieren.</em>
   </p>
</td>
<td>
   <a href="/help/assets/edit-images-content-hub.md">
   <img alt="Bearbeiten mit Adobe Express" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/edit-images-content-hub.md">
      <strong>Bearbeiten mit Adobe Express</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Bilder in Content Hub mithilfe von Adobe Express bearbeiten.</em>
   </p>
</td>
</table>

+++

+++**Dynamic Media**

Mit Dynamic Media können Sie visuell ansprechende Merchandising- und Marketing-Assets nach Bedarf bereitstellen. Außerdem können Sie damit interaktive Anzeigeerlebnisse wie Zoom, Drehen um 360 Grad und Videos erstellen und bereitstellen. Ihre Assets werden für die Verwendung auf Web-, Mobile- und Social-Media-Websites dynamisch skaliert. Mit einer Reihe von Assets aus Primärquellen – wie Bildern, Videos und 3D – generiert und liefert Dynamic Media mehrere Varianten dieser vielfältigen Inhalte in Echtzeit über sein globales, skalierbares, leistungsoptimiertes Content Delivery Network (CDN).

Dynamic Media bietet die folgenden Hauptfunktionen:

* **Intelligente Bildbearbeitung**: Die intelligente Bildbearbeitung sorgt für eine noch bessere Leistung bei der Bereitstellung von Bild-Assets, indem sie das Format und die Dateigröße eines Bildes automatisch auf der Grundlage der Browser-Funktionen eines Kunden optimiert. Es funktioniert mit Ihren vorhandenen Bildvorgaben und verwendet Intelligenz bei der Bereitstellung. Diese Intelligenz reduziert die Größe von Bilddateien je nach Browser und Geschwindigkeit der Netzwerkverbindung weiter.

* **Adaptive Videosets**: Ein adaptives Videoset gruppiert Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert sind. Sie beginnen mit Ihrem ursprünglichen, primären Video, das Sie in das System hochladen. Dynamic Media skaliert bzw. transkodiert dieses Video automatisch in mehrere Videos. Zum Zeitpunkt der Bereitstellung wird dann auf intelligente Weise bestimmt, welcher Videobildschirm, welche Qualität und welches Format verwendet werden soll, und die Daten werden entweder an das Smartphone, das Tablet oder den Desktop-Computer übertragen.

* **Smartes Zuschneiden**: Eine Adobe Sensei-KI-Funktion, mit der der Fokus in einem Bild oder Video automatisch erkannt und zugeschnitten wird, um ihn beizubehalten. Es erfasst den gewünschten Blickpunkt unabhängig von der Bildschirmgröße und beseitigt somit mühsame manuelle Aufgaben und liefert hochwertige, schnell ladende Bilder und Videos, die auf jedem Gerät oder Bildschirm gut aussehen.

* **Dynamic Media-Vorlagen**: Erstellen Sie mit Dynamic Media-Vorlagen, einem Vorlagen-Editor von WYSIWYG, in Echtzeit anpassbare Vorlagen für Ihre Banner und Flyer. Veröffentlichen Sie Ihre Dynamic Media-Vorlage und verwenden Sie sie in nachgelagerten Anwendungen. Eine Dynamic Media-Vorlage enthält Bild- und Textebenen. Fügen Sie den Bild- und Textebenen der Vorlage Parameter hinzu und verwenden Sie Dynamic Media-URLs, um die Ebene neu zu positionieren, ihre Größe zu ändern und ihren Inhalt in Echtzeit zu aktualisieren.

* **Multi-Audio und**: Hinzufügen mehrerer Untertitel und Audiospuren zu einem primären Video. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

* **Unterstützung von Dynamic Adaptive Streaming über HTTP (DASH)**: Dynamic Media unterstützt adaptives Streaming bei der Dynamic Media-Videobereitstellung (mit aktiviertem CMAF), wodurch eine bessere Benutzerfreundlichkeit bei der Videoanzeige gewährleistet ist. DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weitläufig verwendet.

* **KI-generierte**: KI-generierte Videountertitel in Adobe Dynamic Media verwenden künstliche Intelligenz, um Untertitel automatisch für Videoinhalte zu generieren. Es werden mehr als 60 Sprachen unterstützt. Die Untertitel können dabei vor der Veröffentlichung des Videos überprüft und in einer Vorschau angezeigt werden.

Informationen zu den verfügbaren Dynamic Media-Angeboten finden Sie unter [Dynamic Media Prime und Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md).



<table>
<td>
   <a href="/help/assets/dynamic-media/dynamic-media.md">
   <img alt="Arbeiten mit Dynamic Media" src="./assets/work-with-dynamic-media.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dynamic-media.md">
      <strong>Arbeiten mit Dynamic Media</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Assets für den Verbrauch auf Web-, Mobile- und Social-Media-Sites bereitstellen. </em>
   </p>
</td>


<td>
   <a href="/help/assets/dynamic-media/dm-journey-part1.md">
   <img alt="Dynamic Media-Journey" src="./assets/dm-journey.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dm-journey-part1.md">
      <strong>Dynamic Media-Journey</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Dynamic Media Ihrer Arbeit einen Mehrwert bringt.</em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media/dm-best-practices.md">
   <img alt="Verbinden von AEM Assets mit Creative Cloud" src="./assets/dm-best-practices.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dm-best-practices.md">
      <strong>Best Practices für Dynamic Media</strong>
      </a>
   </div>
   <p>
      <em>Best Practices beim Arbeiten mit Bildern, Videos und Viewern.</em>
   </p>
</td>
</table>

+++

+++**Dynamic Media mit OpenAPI-Funktionen**

In der modernen digitalen Welt ist die Erschließung des vollen Potenzials der digitalen Assets Ihrer Marke von entscheidender Bedeutung, um den Wettbewerb anzuführen. Eine ganzheitliche Digital Assets Management(DAM)-Lösung erleichtert die Governance von Assets, fördert die Markenkonsistenz und beschleunigt die Bereitstellung von Inhalten bei gleichzeitiger Gewährleistung von Markenintegrität und außergewöhnlichen Kundenerlebnissen.

Dynamic Media mit OpenAPI-Funktionen stellt das DAM in den Mittelpunkt eines agilen und effizienten Content-Lieferkettenökosystems, um die Governance und Bereitstellung von Assets sicherzustellen.

Dynamic Media mit OpenAPI-Funktionen bietet die folgenden zentralen Vorteile:

* **Nahtlose Integrationen**: Dynamic Media mit OpenAPI-Funktionen bietet einen umfassenden Satz von Such- und Bereitstellungs-APIs. Dadurch können Ihre Entwickelnden die [Bereitstellung von Assets ganz einfach in ihre Anwendungen integrieren](/help/assets/integrate-dynamic-media-open-apis.md). Zu den Anwendungen gehören Adobe sowie Anwendungen von Drittanbietern. Es bietet eine [Benutzeroberfläche für die Auswahl der Mikro-Frontend-Assets](/help/assets/overview-asset-selector.md) zum Suchen und Auswählen genehmigter Assets. Die Auswahl kann mühelos in jede Anwendung integriert werden, die auf JavaScript-Frameworks wie React JS, Angular JS und Vanilla JS basiert.

* **Zentralisierte Verwaltung digitaler Assets**: DAM ist die zentrale Datenquelle für alle digitalen Assets. Ihre digitalen Assets werden zentral in AEM Assets verwaltet und verarbeitenden Anwendungen durch Verweise über Bereitstellungs-URLs bereitgestellt, ohne Asset-Binärdateien zu kopieren.

* **Echtzeit-Aktualisierungen**: Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem niedrigen Time-to-Live(TTL)-Wert von 10 Minuten für die Dynamic Media mit OpenAPI-Funktion per CDN werden Aktualisierungen in weniger als 10 Minuten in allen Authoring- und Publishing-Oberflächen sichtbar.

* **Markenkonsistenz**: Nur [markenkonforme Assets](/help/assets/approve-assets.md) werden nachgelagerten Anwendungen offengelegt. [Markenverantwortliche und Marketing-Fachleute behalten die strenge Kontrolle über Marken-Assets](/help/assets/restrict-assets-delivery.md). Es können nur genehmigte und neueste Versionen des Assets verwendet werden. Dadurch wird die Markenkonsistenz in allen Kanälen und Anwendungen sichergestellt.

* **Web-optimierte Bereitstellung**: Digitale Assets werden in Web-optimierten Formaten bereitgestellt, um die Core Web Vitals Ihrer digitalen Erlebnisse zu verbessern. Dazu gehören die Unterstützung von WebP-Ausgabedarstellungen für Bilder, das adaptive Streaming über HLS- oder DASH-Protokolle für Videos und Original-Ausgabedarstellungen für Dokumente.

* **Dynamische Asset-Transformation**: Unser System ermöglicht die direkte Bildumwandlung mithilfe von URL-Parametern, die als Bildmodifikatoren bezeichnet werden. [Zum Beispiel Breite, Höhe, Drehung, Spiegelung, Qualität, Zuschnitt, Format und intelligenter Zuschnitt](/help/assets/deliver-assets-apis.md). Umgewandelte Ausgabedarstellungen werden dynamisch generiert und nahtlos über das CDN bereitgestellt.

* **Sichere Bereitstellung von Assets**: Dynamic Media mit OpenAPI-Funktionen bietet einen Mechanismus zur Steuerung des Zugriffs auf Ihre digitalen Assets. Sie können Benutzerrollen oder Gruppen als Metadaten für zu sichernde Assets angeben und einen vordefinierten Zeitraum festlegen, in dem [nur autorisierte Benutzende auf diese Assets zugreifen können](/help/assets/restrict-assets-delivery.md). Während des eingeschränkten Zeitraums werden die Bereitstellungs-URLs für gesicherte Assets für nicht autorisierte Benutzende nicht aufgelöst.

Informationen zu den verfügbaren Dynamic Media-Angeboten finden Sie unter [Dynamic Media Prime und Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md).

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="Übersicht über Dynamic Media mit OpenAPI-Funktionen" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong>Übersicht über die Funktionen von Dynamic Media mit OpenAPI</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie mehr über die wichtigsten Vorteile und wie Sie diese aktivieren können. </em>
   </p>
</td>


<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Beschränken des Zugriffs auf Assets in Experience Manager" src="./assets/restrict-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Beschränken des Zugriffs auf Assets in Experience Manager</strong>
      </a>
   </div>
   <p>
      <em> Konfigurieren Sie Rollen, um den Zugriff auf genehmigte Assets zu beschränken.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
   <img alt="Integrieren der Remote-Version von AEM Assets mit AEM Sites" src="./assets/integration-aem-sites.jpeg" />
   </a>
   <div>
      <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
      <strong>Integrieren der Remote-Version von AEM Assets mit AEM Sites</strong>
      </a>
   </div>
   <p>
      <em>Integrieren Sie Remote AEM Assets in die AEM Sites-Umgebung. </em>
   </p>
</td>
</table>

+++

>[!TAB Erkenntnisse]

## Asset Insights {#asset-insights}

Das Asset-Reporting bietet Admins Einblicke in die Aktivitäten in der Ansichtsumgebung von Adobe Experience Manager Assets. Diese Daten liefern nützliche Informationen darüber, wie Benutzende mit Inhalten und dem Produkt interagieren. Alle Benutzenden können auf das Insights-Dashboard zugreifen, und diejenigen, die dem Produktprofil der Admins zugewiesen sind, können benutzerdefinierte Berichte erstellen.

Sie können verschiedene Berichtstypen generieren, z. B. Hochladen, Herunterladen und Bereitstellen von Dynamic Media.

* **Einblicke in der Assets-Ansicht**: Die Assets-Ansicht ermöglicht es Ihnen, Echtzeitdaten für Ihre Assets-Ansichtsumgebung mit dem Insights-Dashboard anzuzeigen. Sie können Echtzeit-Ereignismetriken während der letzten 30 Tage oder für die letzten 12 Monate anzeigen. Zu den Ereignissen gehören Downloads, Uploads, Speichernutzung, Top-Suchen, Asset-Anzahl nach Größe und Asset-Anzahl nach Asset-Typ.

* **Adobe Analytics-Integration in der Admin-**: Mit der Funktion &quot;Assets Insights“ können Sie Benutzerbewertungen und Nutzungsstatistiken von Bildern nachverfolgen, die auf Drittanbieter-Websites, in Marketing-Kampagnen und in den Kreativlösungen von Adobe verwendet werden. Dies hilft, Einblicke in die Leistung und Beliebtheit der Bilder zu erhalten. Assets Insights hält Details zu Benutzeraktivitäten wie Anzahl der Bildbewertungen, Klickraten und Impressionen (Häufigkeit des Ladens eines Bildes auf einer Website) fest. Basierend auf diesen Statistiken werden Bildern Bewertungen zugewiesen. Sie können Bewertungs- und Leistungsstatistiken nutzen, um beliebte Bilder für Kataloge, Marketing-Kampagnen usw. auszuwählen. Sie können auf Grundlage dieser Statistiken sogar Richtlinien zur Archivierung und Lizenzverlängerung formulieren. Damit Assets Insights Nutzungsstatistiken für Assets anzeigen kann, konfigurieren Sie zunächst die Funktion für den Abruf von Berichtsdaten aus Adobe Analytics.

* **Content Hub Insights**: Content Hub bietet wertvolle Einblicke in Assets, indem es eine gängige Herausforderung angeht, der Marketing-Stakeholder häufig begegnen - Asset-Nutzungsstatistiken, die in Marketing-Kampagnen, Kanälen und verschiedenen Regionen verwendet werden. Durch das Erlangen eines klaren Verständnisses der Leistung und Beliebtheit der Assets, liefert es verwertbare Einblicke, die für die Verbesserung des Benutzererlebnisses unerlässlich sind.

<table>
<td>
   <a href="/help/assets/manage-reports-assets-view.md">
   <img alt="Verwalten von Berichten in Assets-Ansicht" src="./assets/assets-insights-assets-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-reports-assets-view.md">
      <strong>Verwalten von Berichten in der Assets-Ansicht</strong>
      </a>
   </div>
   <p>
      <em>Mithilfe der Assets-Ansicht Erkenntnisse zu wichtigen Erfolgsmetriken gewinnen. </em>
   </p>
</td>


<td>
   <a href="/help/assets/asset-reports.md">
   <img alt="Verwalten von Berichten in der Administratoransicht" src="./assets/assets-insights-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/asset-reports.md">
      <strong>Verwalten von Berichten in der Admin-Ansicht</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie in der Admin-Ansicht integrierte Berichte in Adobe Analytics verwalten.</em>
   </p>
</td>
<td>
   <a href="/help/assets/insights-content-hub.md">
   <img alt="Assets Insights in Content Hub" src="./assets/asset-insights-content-hub.jpeg" />
   </a>
   <div>
      <a href="/help/assets/insights-content-hub.md">
      <strong>Assets Insights in Content Hub</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Asset Insights in Content Hub anzeigen.</em>
   </p>
</td>
</table>

>[!ENDTABS]

## Verfügbare Persona-basierte Erlebnisse für Digital Asset Management {#persona-based-experiences}

Adobe bietet stabile DAM-Lösungen (Digital Asset Management), mit denen Sie Ihre digitalen Assets optimal nutzen können. Adobe Experience Manager Assets verfügt über zwei separate Erlebnisse, die dasselbe Cloud Services-Repository verwenden:

* **Admin-Ansicht**: Die bestehende Assets as a Cloud Service-Benutzeroberfläche. Verwenden Sie die Admin-Ansicht für alle erweiterten Digital Asset Management-Funktionen, einschließlich Integrationen, Workflows, Inhaltsautomatisierung, Veröffentlichung usw.

* **Assets-Ansicht**: Das einfache Asset-Management-Erlebnis von Adobe zum Speichern, Verwalten, Entdecken und Verwenden digitaler Assets. Es handelt sich um eine optimierte Benutzeroberfläche mit den wesentlichen Digital Asset Management-Funktionen. Entwickelt für Benutzerinnen und Benutzer eines einfachen DAM mit Schwerpunkt auf Upload, Metadatenverwaltung, Suche, Download und Freigabe.

![add-tags](assets/newui-overview.svg)

Benutzerinnen und Benutzer mit Zugriff auf die Admin-Ansicht können auch auf die Asset-Ansicht zugreifen. Die vereinfachte Benutzeroberfläche der Assets-Ansicht erleichtert das Verwalten, Erkennen und Verteilen digitaler Assets. Ein breites Spektrum von Benutzerinnen und Benutzern aus verschiedenen Funktionen, einschließlich Kreativ-, Marketing- und Branchen-Teams, kann an Assets zusammenarbeiten und auf die richtigen, genehmigten Assets zugreifen, wo und wann immer sie benötigt werden. Viele gelegentliche DAM-Benutzerinnen und -Benutzer bevorzugen die Asset-Ansicht, da sie nur eine Teilmenge der Funktionen enthält. Das Erlebnis richtet sich an Kreative, Nutzerinnen und Nutzer von schreibgeschützten Assets und einfache DAM-Benutzerinnen und -Benutzer.

DAM-Bibliothekarinnen und -Bibliothekare, -Entwicklungspersonen sowie -Superbenutzerinnen und -Superbenutzer können die Admin-Ansicht weiterhin verwenden oder bei Bedarf zwischen den Benutzeroberflächen wechseln. Sie können das Erlebnis auswählen, das für Ihre Rolle am besten geeignet ist.

Informationen zum Zugriff auf die Assets-Ansicht und einige der Vereinfachungen, die sie gegenüber der Admin-Ansicht bietet, finden Sie unter [Einführung in die Assets-Ansicht](/help/assets/assets-view-introduction.md).


