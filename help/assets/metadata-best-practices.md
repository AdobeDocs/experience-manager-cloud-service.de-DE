---
title: Metadatenverwaltung und Best Practices
description: Erfahren Sie mehr über die Best Practices für Metadaten zur effektiven Verwaltung Ihrer digitalen Assets.
role: User, Admin
exl-id: d90519df-55a6-4e23-81ad-ff2365d71c0d
feature: Metadata, Best Practices
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '1384'
ht-degree: 100%

---

<!-- Keywords to focus on:
metadata best practices
aem metadata 
experience manager metadata-->

# Metadatenverwaltung und Best Practices {#metadata-best-practices}

Damit Ihr Unternehmen sich auszeichnet und mehr Kundinnen und Kunden anspricht, ist die Verwendung hochwertiger Visualisierungen wie Bilder, Videos und andere digitale Assets von entscheidender Bedeutung. Dazu benötigen Sie einen Prozess, der es Ihnen ermöglicht, allen digitalen Assets Metadaten hinzuzufügen, damit sie leicht durchsucht werden können. Metadaten sind die Daten, die wichtige Details zu digitalen Assets bereitstellen, einschließlich Name, Typ, Speicherort in einem Repository, Änderungsdatum und der zugehörigen Tags des Assets. Metadaten optimieren das Asset-Management, verbessern die Suchbarkeit und Barrierefreiheit und ermöglichen eine effektive Versionskontrolle.

Lernen Sie, wie Sie Metadaten im Digital Asset Management(DAM)-System nutzen können, [um die Metadaten Ihrer digitalen Assets effektiv zu verwalten](manage-metadata.md).

## Metadatentypen

Basierend auf den verschiedenen Aspekten von Daten werden Metadaten als technische, informative oder administrative Metadaten kategorisiert.

### Technische Metadaten

Technische Metadaten umfassen die technischen Aspekte eines Assets. Diese Art von Metadaten ist für Benutzende entscheidend, um die inhärenten Merkmale digitaler Assets zu verstehen und so eine effiziente Verarbeitung und Nutzung zu ermöglichen.
Sie enthalten Details wie:

* Dateigröße
* Format
* Auflösung
* Abmessungen
* Farbmodus

### Informative Metadaten

Informative Metadaten umfassen beschreibende Informationen, die das Verständnis des Inhalts eines Assets verbessern. Diese Metadaten sind wichtig für die Inhaltserkennung und -suche und dafür, die Bedeutung des Assets zu verstehen. Informative Metadaten umfassen Suchbegriffe, Beschriftungen und Beschreibungen.

Beispielsweise können beim Verwalten eines Videos in Experience Manager Assets die folgenden informativen Metadaten einbezogen werden:

* **Suchbegriffe**: Marketing, Produktstart, Promo
* **Beschriftung**: Einführung unseres neuesten Produkts mit überzeugenden Funktionen
* **Beschreibung**: Ein detaillierter Überblick über den Videoinhalt.

Benutzende, die nach Marketing-Inhalten suchen, können das obige Video einfach finden und seine Bedeutung verstehen.

### Administrative Metadaten

Administrative Metadaten behandeln die verwaltungstechnischen Aspekte digitaler Assets. Sie stellen die Zugriffssteuerung, die Compliance und die Verwaltung des gesamten Lebenszyklus von Assets innerhalb des Digital Asset Management-Systems sicher. Sie umfassen Informationen zu Folgendem:

* Asset-Eigentümerschaft
* Verwendungsrechte
* Berechtigungen
* Weitere administrative Details

Administrative Metadaten sorgen für das richtige Asset-Management. Sie steuern den Zugriff und die Compliance innerhalb des Digital Asset Management-Systems.

## Best Practices für Metadaten

### Definieren der Metadatenstrategie schon zu Beginn

Die Metadatenverwaltung beginnt mit der Definition einer Metadatenstrategie, die eine Grundlage für die Bewertung des langfristigen Werts bietet.

Beim Planen Ihrer Metadatenstrategie ist es entscheidend, ein benutzerdefiniertes Metadatenschema zu erstellen, das Ihren Anforderungen entspricht. Ein gut konzipiertes Schema bietet ein strukturiertes Framework zum Kategorisieren und Organisieren von Assets in Experience Manager.

#### Video: Hinzufügen benutzerdefinierter Felder zum Metadatenschema

>[!VIDEO](https://video.tv.adobe.com/v/3425977)

Ihre Metadatenstrategie kann die Definition folgender Elemente umfassen:

* **Ziele:** Beschreiben Sie klar die Ziele und erwarteten Ergebnisse der Metadaten. Ermitteln Sie, was Sie durch das Hinzufügen der Metadaten erreichen möchten.

* **Zweck:** Definieren Sie, warum Sie Metadaten erfassen. Geben Sie an, welchen Mehrwert sie für Ihre Prozesse, Systeme oder Organisation bieten.

* **Zugänglichkeitsplan:** Erstellen Sie einen Plan, um die Metadaten leicht zugänglich und auffindbar zu machen. Erklären Sie, wer sie verwenden wird und welche Tools oder Methoden verwendet werden sollen.

* **Metadateneigenschaften:** Identifizieren und definieren Sie jede Metadateneigenschaft sorgfältig. Stellen Sie sicher, dass jede Eigenschaft aus einem klaren Grund einbezogen wird und dass sie mit den Zielen und dem Zweck verbunden ist.

Um konsistente Ergebnisse im gesamten Repository sicherzustellen, planen Sie die Strategie sorgfältig. Hier finden Sie weitere Informationen zu [Metadatenschemata](metadata-schemas.md).

### Erstellen eines Metadaten-Governance-Plans

Data Governance stellt sicher, dass die Metadatenverwaltung des Unternehmens auf die allgemeinen Geschäftsziele abgestimmt ist.
Die Governance-Strategie kann Folgendes umfassen:

* Festlegen von Richtlinien und Verfahren für die Daten- und Metadatenverwaltung.
* Festlegen von Standards für Datenqualität und -integrität.
* Definieren von Rollen und Zuständigkeiten im Daten-Management.

Ermitteln Sie, woher die Informationen stammen, und untersuchen Sie die Details der Metadatenstrategie, einschließlich der Eigenschaften und deren Quellen. Je nach Komplexität der Strategie ist eine Skalierung möglich. In größeren Unternehmen gibt es ein übergeordnetes System zur Verwaltung von Metadaten, das mehrere Systeme im Primär-Stapel überwacht.

>[!NOTE]
>
>Erfahren Sie, wie das [Verwalten von Metadaten für digitale Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html?lang=de) abläuft.

### Konsistente Metadatenstrategie

Eine konsistente Metadatenstrategie sorgt dafür, dass digitale Assets effektiv organisiert und abgerufen werden können. Verfolgen Sie beim Erfassen und Implementieren von Metadatenwerten einen strategischen Ansatz, sodass eine Weiterentwicklung ohne unnötige Änderungen möglich ist. <br>

Bei der unternehmensweiten Metadatenverwaltung ist es wichtig, Assets konsistent zu benennen und konsistent darauf zu verweisen. Wenn Sie beispielsweise mehrere Assets gleichzeitig verwalten, sollten Sie erwägen, Metadaten massenweise hinzuzufügen. <br>

Im Folgenden sind einige Best Practices aufgeführt, die Sie befolgen sollten:

* **Vermeiden Sie duplizierte Werte:** Wenn Sie über eine Sammlung von Bildern aus einer Marketing-Kampagne verfügen, verwenden Sie konsistente Namen und vermeiden Sie Duplikate.<br>
Anstatt beispielsweise duplizierte Namen wie *Kampagne_Bild_001* und *Kampagne_Bild_002* zu verwenden, implementieren Sie eine systematische Namenskonvention wie *Angebotswerbung* und *Produktstart*, um eine eindeutige und geordnete Identifizierung zu gewährleisten.

* **Setzen Sie kontrolliertes Vokabular effektiv ein:** Implementieren Sie kontrolliertes Vokabular durch die Verwendung standardisierter Begriffe für Tags. Erfahren Sie, wie Sie das [AEM-Tagging-Framework](/help/implementing/developing/introduction/tagging-framework.md) effektiv implementieren.  <br>
Verwenden Sie beispielsweise beim Taggen von Bildern mit Designs konsistent Begriffe wie *Produktstart* oder *Angebotswerbung*, um eine systematische Sequenz beizubehalten.

* **Achten Sie stets auf richtige und vollständige Angaben:** Damit Metadaten konsistent bleiben, ist es entscheidend, über verschiedene Quellen hinweg richtige, vollständige und aufeinander ausgerichtete Angaben zu machen.
Überprüfen Sie beispielsweise beim Hinzufügen von Metadaten zu einem PDF-Dokument, ob Details wie Autorennamen und Suchbegriffe richtig und vollständig sind.

#### Video: Hinzufügen von Massenmetadaten zu Assets

>[!VIDEO](https://video.tv.adobe.com/v/3425978)

### Bewerten und Optimieren der Durchsuchbarkeit von Metadaten

Bewerten Sie Ihre Metadatenstrategie, um die Durchsuchbarkeit der Metadaten zu optimieren. Vereinfachen Sie Workflows und verbessern Sie die Suchfunktionen, um eine effiziente Wiederverwendung zu ermöglichen. Vermeiden Sie den Umgang mit Metadaten, die keinen eindeutigen Zweck erfüllen.

Berücksichtigen Sie die folgenden Best Practices, um die Durchsuchbarkeit Ihrer Metadaten zu optimieren:

* **Suchbegriffoptimierung:** Verbessern Sie die Durchsuchbarkeit von Metadaten, indem Sie Suchbegriffe für Assets optimieren. Sie können die Relevanz von Suchbegriffen für bestimmte Assets im [!UICONTROL Assets-Manager] verbessern, indem Sie die folgenden Schritte ausführen:

   1. Navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Datei]** > **[!UICONTROL [Asset-Ordner]]**.
   1. Wählen Sie das Asset aus, für das Sie die Metadaten aktualisieren möchten, und klicken Sie auf **[!UICONTROL Eigenschaften]**.
   1. Navigieren Sie zur Registerkarte **[!UICONTROL Erweitert]** und klicken Sie unter **[!UICONTROL Für Suchbegriffe erhöhen]** auf **[!UICONTROL Hinzufügen]**. <br>Sie müssen das Standard-Metadatenschema verwenden, um die Suchbegriffe zu erhöhen.
   1. Geben Sie den Suchbegriff ein, für den Sie die Suche optimieren möchten, und klicken Sie auf **[!UICONTROL Hinzufügen]**.<br>
Sie können mehrere Suchbegriffe hinzufügen und sie so anordnen, dass sie Ihrer Priorität entsprechen.
   1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
Verwenden Sie die hinzugefügten Suchbegriffe, um nach dem Asset zu suchen. Das Asset wird unter den obersten Suchergebnissen angezeigt.

  Informieren Sie sich über das [Optimieren der Suche in Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html?lang=de).

* **Benutzerdefinierte Metadatenfelder:** Passen Sie Ihre Metadatenfelder an, um zusätzliche Informationen zu Assets zu erfassen. Fügen Sie beispielsweise bestimmte Felder für Projektdetails, Copyright-Informationen oder andere relevante Daten hinzu, die die Suchfunktionen verbessern. Erlernen Sie das [Bearbeiten oder Hinzufügen benutzerdefinierter Metadaten](meta-edit.md) in Experience Manager Assets.


* **Metadatenvalidierung:** Implementieren Sie Validierungsprüfungen für Metadateneinträge, um Konsistenz und Genauigkeit sicherzustellen. Die Verwendung von kontrolliertem Vokabular macht den Validierungsprozess reibungsloser und verringert die Wahrscheinlichkeit unklarer oder inkonsistenter Einträge. Dazu kann es gehören, Richtlinien für bestimmte Metadateneigenschaften festzulegen, um mehrdeutige oder inkonsistente Informationen zu vermeiden.

* **Nutzungsverfolgung:** Bewerten Sie die Relevanz und Verwendung verschiedener Metadateneigenschaften im Zeitverlauf. Identifizieren und priorisieren Sie häufig verwendete Metadaten oder tragen Sie wesentlich zu Such- und Abrufprozessen bei.

#### Video: Hinzufügen von Suchbegriffen, um die Suchbarkeit zu verbessern

>[!VIDEO](https://video.tv.adobe.com/v/3425979)

### Einfache und leicht verständliche Metadaten

Vereinfachen Sie Metadaten für eine bessere Governance und Benutzerakzeptanz. Halten Sie sie einfach und leicht verständlich und fordern Sie die Benutzenden auf, wichtige Informationen hinzuzufügen.
Probieren Sie die folgenden Best Practices aus, um die Metadaten zu vereinfachen:

* **Optimieren Sie die Eigenschaftsoptionen:** Konzentrieren Sie sich auf die Hervorhebung wichtiger Eigenschaften, ohne die Benutzenden mit zu vielen auszufüllenden Metadatenfeldern zu belasten. Nehmen Sie beispielsweise beim Hinzufügen von Metadaten für ein Bild nur Schlüsselfelder wie Titel, Beschreibung und Tags auf, um eine effektive Kategorisierung zu ermöglichen.

* **Beseitigen Sie unnötige Standardeigenschaften:** Vereinfachen Sie das Metadatenformular, indem Sie standardmäßige, aber für Ihren Anwendungsfall irrelevante Eigenschaften eliminieren. Entfernen Sie selten verwendete Standardeigenschaften für eine übersichtlichere Benutzeroberfläche und ein klareres Erlebnis.

* **Überprüfen und aktualisieren Sie Metadaten regelmäßig:** Aktualisieren Sie Metadaten regelmäßig und passen Sie sich an die sich ändernden Anforderungen und Technologien an, um sicherzustellen, dass die Benutzenden im Laufe der Zeit wertvolle Informationen bereitstellen.

### Analysieren der Inhalts-Journey

Untersuchen Sie die Content-Lieferkette, um Metadatenquellen zu finden und alle Beteiligten, angefangen bei den Führungskräften, an einem gründlichen Best-Practice-Ansatz zu beteiligen. Beziehen Sie verschiedene Mitarbeiterinnen und Mitarbeiter ein, um eine umfassende Unterstützung innerhalb der Organisation sicherzustellen. <br>Integrieren Sie Metadaten in verschiedenen Phasen, um die Verantwortung für die Bereitstellung von Asset-Details während des Hochladens zu teilen. Beispielsweise bietet die Integration von [!DNL Experience Manager Assets] und [!DNL Workfront] wesentliche Vorteile im Hinblick auf die Metadatenverwaltung und verbessert Effizienz und Zusammenarbeit bei der Erstellung und Verwaltung von Inhalten. Diese Integration stellt eine effektive Metadatensynchronisierung für verknüpfte Assets sicher und aktualisiert automatisch Projektdetails, wenn Änderungen in [!DNL Workfront] vorgenommen werden.

Vermitteln Sie Ziele, Fortschritte, Meilensteine und Herausforderungen frühzeitig, um Beiträge und die Zusammenarbeit aller Beteiligten zu ermöglichen. Fördern Sie die Zusammenarbeit im gesamten Unternehmen, um effiziente Prozesse und wertvolle Metadaten zu erstellen.

Erfahren Sie mehr über [Metadaten und zugehörige Konzepte](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-concepts.html?lang=de) zur effektiven Verwaltung Ihrer Experience Manager-Metadaten.
