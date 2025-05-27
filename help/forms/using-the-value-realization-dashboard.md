---
title: Verwenden des Dashboards zur Wertentwicklung zur Analyse der Nutzungs-Trends von Formularen und Dokumenten
description: Erfahren Sie, wie Sie mit dem Dashboard „Erkenntnisse zur Formularnutzung“ die Leistung Ihrer Formulare und Formularfragmente überwachen und verstehen können.
role: User, Developer
level: Intermediate
feature: Adaptive Forms, Foundation Components, Core Components
hide: true
hidefromtoc: true
exl-id: f58aa2df-dfb6-4eb4-b20d-e81bb01be8a7
source-git-commit: 3bc967bc2b6584abbd73e3456e123ed76a8959b6
workflow-type: ht
source-wordcount: '873'
ht-degree: 100%

---

# Verwenden des Dashboards zur Wertentwicklung zur Analyse der Nutzungs-Trends von Formularen und Dokumenten

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an aem-forms-ea@adobe.com. <span>

![Dashboard zur Wertentwicklung](/help/edge/docs/forms/universal-editor/assets/forms-insights-banner.svg)

Durch die regelmäßige Überwachung der im Dashboard „Erkenntnisse zur Formularnutzung“ dargestellten Metriken können Sie wertvolle Erkenntnisse zur Leistung Ihrer Formulare, Dokumente und Formularfragmente gewinnen. Verwenden Sie diese Daten, um fundierte Entscheidungen zum Formular-Design, zur Fragmentverwaltung und zur allgemeinen Formularstrategie zu treffen.

Dieser Artikel enthält detaillierte Nutzungsanweisungen und Interpretationen der Metriken für das Dashboard zur Wertentwicklung. Einen konzeptionellen Überblick über das Dashboard und seine Vorteile finden Sie unter [Verstehen des Dashboards zur Wertentwicklung](/help/forms/aem-forms-value-realization-dashboard.md).


## Zugreifen auf das Dashboard zu Nutzungserkenntnissen

So greifen Sie auf das Dashboard „Erkenntnisse zur Formularnutzung“ zu:

1. Navigieren Sie zu **Formulare** > **Formulare und Dokumente**.
1. Klicken Sie auf **InProduct-Dashboard**. Das Dashboard wird in einem neuen Fenster geöffnet.

   ![Dashboard zur Wertentwicklung](/help/forms/assets/forms-usage-insights.png)

## Überblick

Das Dashboard besteht aus zwei Hauptabschnitten:

- **Formular- und Dokumentaktivität im Zeitverlauf:** Dieser Abschnitt bietet Erkenntnisse zur Verwendung und Entwicklung Ihrer Formulare über einen ausgewählten Zeitraum.
- **Verwendung von Fragmenten:** In diesem Abschnitt können Sie die Einführung und Wiederverwendung von Formularfragmenten überwachen.

## Formular- und Dokumentaktivität im Zeitverlauf

Dieser Abschnitt enthält vier Diagramme, die jeweils einen anderen Aspekt der Formularaktivität verfolgen. Alle Diagramme haben dieselbe Struktur:

- **Diagrammtyp:** Linien- und Balkendiagramm
- **X-Achse:** Datum (Anzeige der täglichen Aktivität)
- **Y-Achse:** Anzahl (Angabe der Anzahl der Vorkommnisse der verfolgten Aktivität)
- **Zeitraum:** Über ein Dropdown-Menü anpassbar (Optionen: „Letzte 30 Tage“, „Letzte 12 Monate“)




### Formularübermittlungen

- **Zweck:** Dieses Diagramm zeigt an, wie oft Formulare im ausgewählten Zeitraum erfolgreich gesendet wurden.

  ![Diagramm „Formularübermittlungen“](/help/forms/assets/forms-submissions-vr-dashboard-form-insights.png)
- **Zu extrahierende Informationen:**
   - **Trend-Analyse:** Beobachten Sie den allgemeinen Trend der Formularübermittlungen. Wird die Zahl größer bzw. kleiner oder bleibt sie relativ konstant?
   - **Spitzenzeiten:** Identifizieren Sie Tage oder Zeiträume mit ungewöhnlich hohen Übermittlungsraten. Untersuchen Sie die möglichen Gründe für diese Spitzen (z. B. Marketing-Kampagnen, bestimmte Ereignisse).
   - **Zeiträume geringer Aktivität:** Identifizieren Sie Zeiträume mit niedrigen Übermittlungsraten und untersuchen Sie mögliche Ursachen (z. B. Ausfallzeiten des Formulars, Probleme mit der Benutzerfreundlichkeit).
   - **Vergleichsanalyse:** Vergleichen Sie Übermittlungsraten über verschiedene Zeiträume hinweg (z. B. die letzten 30 Tage mit den vorherigen 30 Tagen), um Leistungsänderungen zu bewerten.

### Dokumentausgabedarstellungen

- **Zweck:** Dieses Diagramm verfolgt die Anzahl der Dokumente, die aufgrund der Formularübermittlungen generiert wurden. Dies ist relevant, wenn Ihr Formular die Erstellung von Dokumenten (z. B. Verträgen, Berichten) auslöst.

  ![Diagramm „Dokumentausgabedarstellungen“](/help/forms/assets/document-rendetions-vr-dashboard-form-insights.png)


- **Zu extrahierende Informationen:**
   - **Korrelation mit Formularübermittlungen:** Vergleichen Sie den Trend der Dokumentausgabedarstellungen mit dem Trend der Formularübermittlungen. Idealerweise sollten diese eng miteinander korrelieren. Diskrepanzen können auf Probleme bei der Dokumenterstellung hinweisen.
   - **Volumen der Dokumenterstellung:** Bewerten Sie das Gesamtvolumen der generierten Dokumente, um die Arbeitslast auf Ihrem Dokumenterstellungssystem zu verstehen.

### Erstellte Formulare


- **Zweck** Dieses Diagramm zeigt die Anzahl der neuen Formulare an, die innerhalb des ausgewählten Zeitraums erstellt wurden.

  ![Diagramm „Erstellte Formulare“](/help/forms/assets/forms-created-vr-dashboard-form-insights.png)

- **Zu extrahierende Informationen:**
   - **Rate der Formularerstellung:** Verfolgen Sie die Rate, mit der neue Formulare erstellt werden. Dies bietet Erkenntnisse bezüglich der Nachfrage nach neuen Formularen innerhalb der Organisation.
   - **Spitzen bei der Erstellung:** Identifizieren Sie Zeiträume mit ungewöhnlich hoher Aktivität bei der Formularerstellung. Dies kann auf bestimmte Projekte oder Initiativen hinweisen, die neue Formulare erfordern.

### Veröffentlichte Formulare

- **Zweck** Dieses Diagramm verfolgt die Anzahl der Formulare, die innerhalb des ausgewählten Zeitraums veröffentlicht (für die Verwendung zur Verfügung gestellt) wurden.

  ![Diagramm „Veröffentlichte Formulare“](/help/forms/assets/forms-publish-vr-dashboard-form-insights.png)


- **Zu extrahierende Informationen:**
   - **Rate der Formularbereitstellung:** Überwachen Sie die Rate, mit der neue Formulare für Benutzende bereitgestellt werden.
   - **Verzögerung zwischen Erstellung und Veröffentlichung:** Analysieren Sie den Zeitunterschied zwischen dem Diagramm „Erstellte Formulare“ und dem Diagramm „Veröffentlichte Formulare“. Eine erhebliche Verzögerung kann auf Engpässe im Formulargenehmigungs- oder -bereitstellungsprozess hinweisen.

## Verwendung von Fragmenten

Dieser Abschnitt bietet Erkenntnisse bezüglich der Verwendung von Formularfragmenten, bei denen es sich um wiederverwendbare Komponenten handelt, die in mehrere Formulare integriert werden können.

![Diagramm „Veröffentlichte Formulare“](/help/forms/assets/fragment-usage-vr-dashboard-form-insights.png)

### Anzahl der verwendeten Formularfragmente

- **Diagrammtyp:** Numerische Anzeige (mit einem einzelnen Wert)
- **Zweck:** Zeigt die Gesamtzahl der eindeutigen Formularfragmente an, die derzeit in aktiven Formularen verwendet werden.
- **Zu extrahierende Informationen:**
   - **Fragmenteinführung** Bewerten Sie die generelle Einführung von Formularfragmenten innerhalb der Organisation. Eine höhere Anzahl deutet auf eine stärkere Verwendung wiederverwendbarer Komponenten hin.

### Wiederverwenden von Formularfragmenten

- **Diagrammtyp:** Numerische Anzeige (mit einem einzelnen Wert)
- **Zweck:** Zeigt an, wie oft Formularfragmente in verschiedenen Formularen insgesamt wiederverwendet wurden. Diese Metrik gibt an, wie effektiv Fragmente genutzt werden, um Duplizierungen zu vermeiden und die Konsistenz zu wahren.
- **Zu extrahierende Informationen:**
   - **Rate der Fragmentwiederverwendung:** Überwachen Sie die Rate, mit der vorhandene Fragmente in neuen Formularen wiederverwendet werden. Eine höhere Zahl deutet auf eine bessere Nutzung wiederverwendbarer Komponenten und eine optimierte Effizienz hin.

## Beispielszenarien:

- **Szenario:** Sie bemerken einen plötzlichen Rückgang in „Formularübermittlungen“.
   - **Aktion:** Untersuchen Sie potenzielle Ursachen wie Ausfallzeiten von Formularen, Probleme mit der Benutzerfreundlichkeit oder einen Rückgang des Traffics zur Landingpage des Formulars.
- **Szenario:** Der Wert „Wiederverwenden von Formularfragmenten“ ist niedrig.
   - **Aktion:** Bewerben Sie die Vorteile der Verwendung von Formularfragmenten in Ihrem Team. Stellen Sie sicher, dass Fragmente gut organisiert und einfach zu finden sind, und bieten Sie Schulungen zum effektiven Erstellen und Wiederverwenden von Fragmenten an.
- **Szenario:** Es gibt eine signifikante Verzögerung zwischen „Erstellte Formulare“ und „Veröffentlichte Formulare“. 
   - **Aktion:** Überprüfen Sie Ihren Formulargenehmigungs- und -bereitstellungsprozess, um Engpässe zu identifizieren und zu beseitigen.



## Siehe auch

- [Verstehen des Dashboards zur Wertentwicklung](/help/forms/aem-forms-value-realization-dashboard.md)
