---
title: Verwenden des Dashboards zur Wertschöpfung zur Analyse der Nutzung von Formularen und Dokumenten
description: Erfahren Sie, wie Sie mit dem Dashboard „Nutzungseinblicke“ in Forms die Leistung Ihrer Formulare und Formularfragmente überwachen und verstehen können.
role: User, Developer
level: Intermediate
feature: Adaptive Forms, Foundation Components, Core Components
hide: true
hidefromtoc: true
source-git-commit: 08db35af78d46db42e6e2b373f7278753529c37e
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 1%

---

# Verwenden des Dashboards zur Wertschöpfung zur Analyse der Nutzung von Formularen und Dokumenten

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an aem-forms-ea@adobe.com. <span>

![Dashboard zur Wertschöpfung](/help/edge/docs/forms/universal-editor/assets/forms-insights-banner.svg)

Durch die regelmäßige Überwachung der im Dashboard „Nutzungseinblicke zu Forms&quot; dargestellten Metriken können Sie wertvolle Einblicke in die Leistung Ihrer Formulare, Dokumente und Formularfragmente gewinnen. Verwenden Sie diese Daten, um fundierte Entscheidungen zum Formularentwurf, zur Fragmentverwaltung und zur allgemeinen Formularstrategie zu treffen.

Dieser Artikel enthält detaillierte Nutzungsanweisungen und Interpretationen der Metriken für das Wertschöpfungs-Dashboard. Einen konzeptionellen Überblick über das Dashboard und seine Vorteile finden Sie unter [Ihr Dashboard zur Wertschöpfung](/help/forms/aem-forms-value-realization-dashboard.md).


## Zugreifen auf das Dashboard für Nutzungseinblicke

So greifen Sie auf das Dashboard Forms Usage Insights zu:

1. Navigieren Sie zu **Forms** > **Forms und Dokumente**
1. Klicken Sie **Insights-Dashboard**. Das Dashboard wird in einem neuen Fenster geöffnet.

   ![Dashboard zur Wertschöpfung](/help/forms/assets/forms-usage-insights.png)

## Überblick

Das Dashboard besteht aus zwei Hauptabschnitten:

- **Formular- und Dokumentaktivität im Zeitverlauf:** Dieser Abschnitt bietet Einblicke in die Verwendung und Entwicklung Ihrer Formulare über einen ausgewählten Zeitraum.
- **Verwendung von Fragmenten** In diesem Abschnitt können Sie die Verwendung und Wiederverwendung von Formularfragmenten überwachen.

## Formular- und Dokumentenaktivität im Zeitverlauf

Dieser Abschnitt enthält vier Diagramme, die jeweils einen anderen Aspekt der Formularaktivität verfolgen. Alle Diagramme haben dieselbe Struktur:

- **Diagrammtyp:** Liniendiagramm und Balkendiagramm
- **X-Achse:** (tägliche Aktivität anzeigen)
- **Y-Achse:** Anzahl (gibt die Anzahl der Vorkommnisse der verfolgten Aktivität an)
- **Zeitraum:** über ein Dropdown-Menü anpassbar (Optionen: „Letzte 30 Tage“, „Letzte 12 Monate„)




### Formularübermittlungen

- **Zweck:** Dieses Diagramm zeigt an, wie oft Formulare im ausgewählten Zeitraum erfolgreich gesendet wurden.

  ![Forms-Einreichungsdiagramm](/help/forms/assets/forms-submissions-vr-dashboard-form-insights.png)
- **Zu extrahierende Informationen:**
   - **Trendanalyse** Beobachten Sie den allgemeinen Trend der Formularübermittlungen. Steigt oder sinkt die Zahl oder bleibt sie relativ konstant?
   - **Spitzenzeiten:** Tage oder Zeiträume mit ungewöhnlich hohen Übermittlungsraten. Untersuchen Sie die möglichen Gründe für diese Spitzen (z. B. Marketing-Kampagnen, bestimmte Ereignisse).
   - **Zeiträume geringer Aktivität:** Sie Zeiträume mit niedrigen Übermittlungsraten auf und untersuchen Sie mögliche Ursachen (z. B. Ausfallzeiten, Probleme mit der Benutzerfreundlichkeit).
   - **Vergleichsanalyse:** Vergleichen der Übermittlungsraten über verschiedene Zeiträume hinweg (z. B. die letzten 30 Tage mit den vorherigen 30 Tagen), um Leistungsänderungen zu bewerten.

### Dokumentausgabedarstellungen

- **Zweck:** Dieses Diagramm verfolgt die Anzahl der Dokumente, die als Ergebnis von Formularübermittlungen generiert wurden. Dies ist relevant, wenn Ihr Formular-Trigger die Erstellung von Dokumenten (z. B. Verträge, Berichte) unterstützt.

  ![Dokument-Rendering-Diagramm](/help/forms/assets/document-rendetions-vr-dashboard-form-insights.png)


- **Zu extrahierende Informationen:**
   - **Korrelation mit Formularübermittlungen:** Vergleichen Sie den Trend der Dokumentwiedergaben mit dem Trend der Formularübermittlungen. Idealerweise sollten diese eng miteinander korrelieren. Diskrepanzen können auf Probleme bei der Dokumenterstellung hinweisen.
   - **Volumen der Dokumenterstellung:** Bewerten Sie das Gesamtvolumen der generierten Dokumente, um die Arbeitslast auf Ihrem Dokumenterstellungssystem zu verstehen.

### Erstellte Formulare


- **Zweck** Dieses Diagramm zeigt die Anzahl der neuen Formulare an, die innerhalb des ausgewählten Zeitraums erstellt wurden.

  ![Diagramm von Forms erstellt](/help/forms/assets/forms-created-vr-dashboard-form-insights.png)

- **Zu extrahierende Informationen:**
   - **Rate der Formularerstellung** Verfolgen Sie die Rate, mit der neue Formulare erstellt werden. Dies bietet Einblicke in die Nachfrage nach neuen Formularen innerhalb der Organisation.
   - **Spitzen bei der Formularerstellung:** Identifizieren Sie Zeiträume mit ungewöhnlich hoher Aktivität bei der Formularerstellung. Dies kann auf bestimmte Projekte oder Initiativen hinweisen, die neue Formulare erfordern.

### Forms Published

- **Zweck:** Dieses Diagramm zeigt die Anzahl der Formulare an, die innerhalb des ausgewählten Zeitraums veröffentlicht (zur Verwendung bereitgestellt) wurden.

  ![Diagramm in Forms veröffentlicht](/help/forms/assets/forms-publish-vr-dashboard-form-insights.png)


- **Zu extrahierende Informationen:**
   - **Rate der Formularbereitstellung** Überwachen Sie die Rate, mit der neue Formulare für Benutzer bereitgestellt werden.
   - **Verzögerung zwischen Erstellung und Veröffentlichung** Analysieren Sie den Zeitunterschied zwischen dem Diagramm &quot;Forms erstellt“ und dem Diagramm &quot;Forms veröffentlicht“. Eine erhebliche Verzögerung kann auf Engpässe im Formulargenehmigungs- oder -bereitstellungsprozess hinweisen.

## Verwendung von Fragmenten

Dieser Abschnitt bietet Einblicke in die Verwendung von Formularfragmenten, bei denen es sich um wiederverwendbare Komponenten handelt, die in mehrere Formulare integriert werden können.

![Diagramm in Forms veröffentlicht](/help/forms/assets/fragment-usage-vr-dashboard-form-insights.png)

### Anzahl der verwendeten Formularfragmente

- **Diagrammtyp:** Numerische Anzeige (mit einem einzelnen Wert)
- **Zweck:** Zeigt die Gesamtzahl der eindeutigen Formularfragmente an, die derzeit in aktiven Formularen verwendet werden.
- **Zu extrahierende Informationen:**
   - **Fragmentakzeptanz** Bewerten Sie die generelle Akzeptanz von Formularfragmenten innerhalb der Organisation. Eine höhere Anzahl deutet auf eine stärkere Verwendung wiederverwendbarer Komponenten hin.

### Wiederverwenden von Formularfragmenten

- **Diagrammtyp:** Numerische Anzeige (mit einem einzelnen Wert)
- **Zweck:** Zeigt an, wie oft Formularfragmente insgesamt in verschiedenen Formularen wiederverwendet wurden. Diese Metrik gibt an, wie effektiv Fragmente genutzt werden, um Duplizierungen zu vermeiden und die Konsistenz zu wahren.
- **Zu extrahierende Informationen:**
   - **Fragmentwiederverwendungsrate:** Überwachen Sie die Rate, mit der vorhandene Fragmente in neuen Formularen wiederverwendet werden. Eine höhere Zahl deutet auf eine bessere Nutzung wiederverwendbarer Komponenten und eine verbesserte Effizienz hin.

## Beispielszenarien

- **Szenario** Sie bemerken einen plötzlichen Rückgang in „Formularübermittlungen“
   - **Aktion** Untersuchen Sie potenzielle Ursachen wie Ausfallzeiten von Formularen, Probleme mit der Benutzerfreundlichkeit oder einen Rückgang des Traffics auf der Landingpage des Formulars.
- **Szenario:** Wert für „Wiederverwendung von Formularfragmenten“ ist niedrig.
   - **Aktion** Werben Sie für die Vorteile der Verwendung von Formularfragmenten für Ihr Team, stellen Sie sicher, dass Fragmente gut organisiert und einfach zu finden sind, und bieten Sie Schulungen zum effektiven Erstellen und Wiederverwenden von Fragmenten an.
- **Szenario:** Es gibt eine erhebliche Verzögerung zwischen &quot;Forms erstellt“ und &quot;Forms veröffentlicht“.
   - **Aktion:** Überprüfen Sie Ihren Formulargenehmigungs- und -bereitstellungsprozess, um Engpässe zu identifizieren und zu beseitigen.



## Siehe auch

- [Ihr Wertschöpfungs-Dashboard](/help/forms/aem-forms-value-realization-dashboard.md)
