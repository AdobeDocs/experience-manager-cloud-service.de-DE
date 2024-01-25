---
title: Metadatenverwaltung und Best Practices
description: Erfahren Sie mehr über die Best Practices für Metadaten zur effektiven Verwaltung Ihrer digitalen Assets.
role: User, Admin
exl-id: d90519df-55a6-4e23-81ad-ff2365d71c0d
source-git-commit: 2526bc491f079d0dfafaa7aad0d240ff64109591
workflow-type: tm+mt
source-wordcount: '1384'
ht-degree: 0%

---

<!-- Keywords to focus on:
metadata best practices
aem metadata 
experience manager metadata-->

# Metadatenverwaltung und Best Practices {#metadata-best-practices}

Damit Ihr Unternehmen sich auszeichnet und mehr Kunden anspricht, ist die Verwendung hochwertiger Visualisierungen wie Bilder, Videos und andere digitale Assets von entscheidender Bedeutung. Dazu benötigen Sie einen Prozess, der es Ihnen ermöglicht, allen digitalen Assets Metadaten hinzuzufügen, damit sie leicht durchsucht werden können. Metadaten sind die Daten, die wichtige Details zu digitalen Assets bereitstellen, einschließlich Name, Typ, Speicherort in einem Repository, Änderungsdatum und zugehörigen Tags des Assets. Metadaten optimieren die Asset-Verwaltung, verbessern die Suchbarkeit und Barrierefreiheit und ermöglichen eine effektive Versionskontrolle.

Erfahren Sie, wie Sie Metadaten im Digital Asset Management (DAM)-System effektiv verwenden können. [Verwalten von Metadaten für digitale Assets](manage-metadata.md).

## Metadatentypen

Anhand der verschiedenen Aspekte von Daten werden Metadaten als technische Metadaten, Informations-Metadaten und Verwaltungsmetadaten kategorisiert.

### Technische Metadaten

Technische Metadaten umfassen die technischen Aspekte eines Assets. Diese Art von Metadaten ist für die Benutzer von entscheidender Bedeutung, um die inhärenten Merkmale digitaler Assets zu verstehen und so eine effiziente Verarbeitung und Nutzung zu ermöglichen.
Er enthält Details wie:

* Dateigröße
* Format
* Auflösung
* Dimensionen
* Farbmodus

### Informative Metadaten

Informationsmetadaten umfassen beschreibende Informationen, die das Verständnis des Inhalts eines Assets verbessern. Diese Metadaten sind von entscheidender Bedeutung für die Inhaltserkennung, die Suchbarkeit und das Verständnis der Bedeutung des Assets. Informationsmetadaten umfassen Suchbegriffe, Beschriftungen und Beschreibungen.

Wenn Sie beispielsweise ein Video in Experience Manager Assets verwalten, können wir die folgenden Informationsmetadaten einbeziehen:

* **Schlüsselwörter**: Marketing, Produktstart, Promo
* **Beschriftung**: Einführung unseres neuesten Produkts mit spannenden Funktionen
* **Beschreibung**: Eine detaillierte Übersicht über den Videoinhalt.

Benutzer, die nach Marketing-bezogenen Inhalten suchen, können die Bedeutung des obigen Videos einfach finden und verstehen.

### Administrative Metadaten

Administrative Metadaten behandeln die Managementaspekte digitaler Assets. Sie stellt die Zugriffskontrolle, die Compliance und die Verwaltung des gesamten Lebenszyklus von Assets innerhalb des Digital Asset Management-Systems sicher. Er enthält Informationen zu:

* Asset-Besitz
* Nutzungsrechte
* Berechtigungen
* Weitere Verwaltungsdetails

Administrative Metadaten gewährleisten die korrekte Asset-Verwaltung, die Steuerung des Zugriffs und die Einhaltung von Vorschriften innerhalb des Digital Asset Management-Systems.

## Best Practices für Metadaten

### Definieren Ihrer Metadatenstrategie von Anfang an

Das Metadatenmanagement beginnt mit der Definition einer Metadatenstrategie, die eine Grundlage für die Bewertung des langfristigen Werts bietet.

Das Erstellen eines benutzerdefinierten Metadatenschemas entsprechend Ihren Anforderungen ist bei der Planung Ihrer Metadatenstrategie von entscheidender Bedeutung. Ein gut gestaltetes Schema bietet ein strukturiertes Framework für die Kategorisierung und Organisation von Assets in Experience Manager.

#### Video: Hinzufügen benutzerdefinierter Felder zum Metadatenschema

>[!VIDEO](https://video.tv.adobe.com/v/3425977)

Ihre Metadatenstrategie kann die Definition folgender Elemente umfassen:

* **Ziele:** Beschreiben Sie die Ziele und erwarteten Ergebnisse der Metadaten. Ermitteln Sie, was Sie erreichen möchten, indem Sie die Metadaten hinzufügen.

* **Zweck:** Definieren Sie, warum Sie Metadaten erfassen. Geben Sie den Wert an, den Sie Ihren Prozessen, Systemen oder Ihrer Organisation hinzufügen.

* **Zugänglichkeitsplan:** Erstellen Sie einen Plan, um die Metadaten leicht zugänglich und auffindbar zu machen. Erklären Sie, wer es verwenden wird und welche Tools oder Methoden verwendet werden sollen.

* **Metadateneigenschaften:** Sorgfältige Identifizierung und Definition jeder Metadateneigenschaft. Stellen Sie sicher, dass jede Eigenschaft einen klaren Grund für ihre Einbeziehung hat und eine Verbindung zu Zielen und Zweck herstellt.

Um konsistente Ergebnisse im gesamten Repository sicherzustellen, planen Sie die Strategie sorgfältig. Weitere Informationen [Metadatenschemata](metadata-schemas.md).

### Erstellen eines Metadaten-Governance-Plans

Data Governance stellt sicher, dass die Metadatenverwaltungsbemühungen des Unternehmens mit den allgemeinen Geschäftszielen abgestimmt sind.
Die Governance-Strategie kann Folgendes umfassen:

* Festlegung von Richtlinien und Verfahren für die Daten- und Metadatenverwaltung.
* Festlegung von Standards für Datenqualität und -integrität.
* Definition von Rollen und Zuständigkeiten im Datenmanagement.

Ermitteln Sie, woher die Informationen stammen, und untersuchen Sie die Details der Metadatenstrategie, einschließlich der Eigenschaften und deren Quellen. Die Skalierung hängt von der Komplexität der Strategie ab. In größeren Unternehmen gibt es ein Master-Metadatenverwaltungssystem, das mehrere Systeme im Master-Stapel überwacht.

>[!NOTE]
>
>Erfahren Sie, wie [Verwalten von Metadaten für digitale Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html).

### Konsistent mit der Metadatenstrategie sein

Eine konsistente Metadatenstrategie gewährleistet eine effektive Organisation und den Abruf digitaler Assets. Nehmen Sie einen strategischen Ansatz zur Erfassung und Implementierung von Metadatenwerten an, der die Flexibilität der Evolution ohne unnötige Änderungen ermöglicht. <br>

Bei der unternehmensweiten Metadatenverwaltung ist Konsistenz beim Benennen und Referenzieren von Assets wichtig. Wenn Sie beispielsweise mehrere Assets gleichzeitig verwalten, sollten Sie &quot;erwägen, Metadaten stapelweise hinzuzufügen. <br>

Im Folgenden finden Sie einige Best Practices, die Sie befolgen sollten:

* **Vermeiden Sie doppelte Werte:** Wenn Sie über eine Sammlung von Bildern aus einer Marketing-Kampagne verfügen, verwenden Sie konsistente Namen und vermeiden Sie Duplikate.<br>
Anstatt beispielsweise doppelte Namen wie *campaign_image_001* und *campaign_image_002*, implementieren Sie eine systematische Benennungskonvention wie *event_promotion* und *product_launch*, um eine eindeutige und geordnete Identifizierung zu gewährleisten.

* **Verwenden Sie gesteuertes Vokabular effektiv:** Implementieren Sie gesteuerte Vokabular durch Verwendung standardisierter Begriffe für Tags. Erfahren Sie, wie Sie [AEM-Tagging-Framework](/help/implementing/developing/introduction/tagging-framework.md) wirksam sein.  <br>
Zum Beispiel konsistente Verwendung von Begriffen wie *product_launch* oder *event_promotion* beim Taggen von Bildern mit Designs, um eine systematische Sequenz zu gewährleisten.

* **Genauigkeit und Vollständigkeit beibehalten:** Um Metadaten konsistent zu halten, sind Genauigkeit, Vollständigkeit und Ausrichtung über verschiedene Quellen hinweg von entscheidender Bedeutung.
Überprüfen Sie beispielsweise beim Hinzufügen von Metadaten zu einem PDF-Dokument, ob Details wie Autorennamen und Keywords korrekt und vollständig sind.

#### Video: Hinzufügen von Massenmetadaten zu Assets

>[!VIDEO](https://video.tv.adobe.com/v/3425978)

### Prüfen und Verbessern der Suchbarkeit von Metadaten

Bewertung Ihrer Metadatenstrategie zur Verbesserung der Suchbarkeit von Metadaten. Vereinfachung von Workflows und Verbesserung der Suchfunktionen für eine effiziente Wiederverwendung. Vermeiden Sie den Umgang mit Metadaten, denen ein eindeutiger Zweck fehlt.

Sie können die folgenden Best Practices zur Optimierung der Suchbarkeit Ihrer Metadaten berücksichtigen:

* **Suchbegriffoptimierung:** Verbessern Sie die Durchsuchbarkeit von Metadaten, indem Sie Suchbegriffe für Assets optimieren. Sie können die Relevanz von Suchbegriffen für bestimmte Assets im [!UICONTROL Assets Manager] indem Sie die folgenden Schritte ausführen:

   1. Navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Datei]** > **[!UICONTROL [Asset-Ordner]]**.
   1. Wählen Sie das Asset aus, für das Sie die Metadaten aktualisieren möchten, und klicken Sie dann auf **[!UICONTROL Eigenschaften]**.
   1. Navigieren Sie zum **[!UICONTROL Erweitert]** und klicken Sie auf **[!UICONTROL Hinzufügen]** unter **[!UICONTROL Für Suchbegriffe erhöhen]**. <br>Sie müssen das Standard-Metadatenschema verwenden, um die Suchbegriffe zu erhöhen.
   1. Geben Sie den Suchbegriff ein, für den Sie die Suche optimieren möchten, und klicken Sie auf **[!UICONTROL Hinzufügen]**.<br>
Sie können mehrere Suchbegriffe hinzufügen und diese gemäß Ihrer Priorität anordnen.
   1. Klicks **[!UICONTROL Speichern und schließen]**.
Suchen Sie das Asset mithilfe der von Ihnen hinzugefügten Suchbegriffe. Das Asset wird unter den obersten Suchergebnissen angezeigt.

  Erfahren Sie, wie [Suche in Experience Manager optimieren](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html?lang=de).

* **Benutzerdefinierte Metadatenfelder:** Passen Sie Ihre Metadatenfelder an, um zusätzliche Informationen zu Assets zu erfassen. Fügen Sie beispielsweise bestimmte Felder für Projektdetails, Copyright-Informationen oder andere relevante Daten hinzu, die die Suchfunktionen verbessern. Lernen [Bearbeiten oder Hinzufügen benutzerdefinierter Metadaten](meta-edit.md) in Experience Manager Assets.


* **Metadatenvalidierung:** Implementieren Sie Validierungsprüfungen für Metadateneinträge, um Konsistenz und Genauigkeit sicherzustellen. Die Verwendung von kontrolliertem Vokabular macht den Validierungsprozess reibungsloser und verringert die Wahrscheinlichkeit unklarer oder inkonsistenter Einträge. Dazu kann es gehören, Richtlinien für bestimmte Metadateneigenschaften festzulegen, um mehrdeutige oder inkonsistente Informationen zu vermeiden.

* **Nutzungsverfolgung:** Bewertung der Relevanz und Verwendung verschiedener Metadateneigenschaften im Zeitverlauf. Identifizieren und priorisieren häufig verwendete Metadaten oder tragen wesentlich zu Such- und Abrufprozessen bei.

#### Video: Fügen Sie Suchbegriffe hinzu, um die Suchbarkeit zu verbessern

>[!VIDEO](https://video.tv.adobe.com/v/3425979)

### Einfache und leicht verständliche Metadaten

Vereinfachen Sie Metadaten für eine bessere Verwaltung und Benutzerakzeptanz. Halten Sie es einfach und leicht zu verstehen und ermutigen Sie die Benutzer, wichtige Informationen hinzuzufügen.
Versuchen Sie die folgenden Best Practices, um die Metadaten zu vereinfachen:

* **Optimieren Sie die Eigenschaftsoptionen:** Konzentrieren Sie sich auf die Hervorhebung wichtiger Eigenschaften, ohne die Benutzer mit zu vielen Metadatenfeldern zu belasten. Fügen Sie beispielsweise beim Hinzufügen von Metadaten für ein Bild nur Schlüsselfelder wie Titel, Beschreibung und Tags ein, um eine effektive Kategorisierung zu ermöglichen.

* **Beseitigen Sie unnötige Standardeigenschaften:** Vereinfachen Sie das Metadatenformular, indem Sie standardmäßige, für Ihren Anwendungsfall irrelevante Eigenschaften eliminieren. Entfernen Sie selten verwendete Standardeigenschaften für eine sauberere Benutzeroberfläche und ein saubereres Erlebnis.

* **Regelmäßige Überprüfung und Aktualisierung von Metadaten:** Aktualisieren Sie regelmäßig Metadaten und passen Sie sich an die sich ändernden Anforderungen und Technologien an, um sicherzustellen, dass Benutzer wertvolle Informationen im Laufe der Zeit bereitstellen.

### Journey analysieren des Inhalts

Untersuchen Sie die Inhaltslieferkette, um Metadatenquellen zu finden und alle Beteiligten, angefangen bei oben, an einem gründlichen Best-Practice-Ansatz zu beteiligen. Schließen Sie verschiedene Mitarbeiter ein, um eine umfassende Unterstützung innerhalb der Organisation sicherzustellen. <br>Integrieren Sie Metadaten in verschiedene Phasen, um die Verantwortung für die Bereitstellung von Asset-Details während des Hochladens freizugeben. Beispielsweise kann die [!DNL Experience Manager Assets] und [!DNL Workfront] bietet wesentliche Vorteile im Hinblick auf die Metadatenverwaltung, die Steigerung der Effizienz und Zusammenarbeit bei der Erstellung und Verwaltung von Inhalten. Diese Integration stellt eine effektive Metadatensynchronisierung für verknüpfte Assets sicher und aktualisiert automatisch Projektdetails, wenn Änderungen an vorgenommen werden in [!DNL Workfront].

Vermitteln Sie Ziele, Fortschritte, Meilensteine und Herausforderungen frühzeitig, um Beiträge und die Zusammenarbeit aller Beteiligten zu erhalten. Förderung der Zusammenarbeit im gesamten Unternehmen zur Erstellung effizienter Prozesse und wertvoller Metadaten.

Weitere Informationen [Metadaten und zugehörige Konzepte](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-concepts.html) zur effektiven Verwaltung Ihrer Experience Manager-Metadaten.
