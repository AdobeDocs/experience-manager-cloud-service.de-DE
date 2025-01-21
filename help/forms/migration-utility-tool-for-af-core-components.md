---
title: Migrationsdienstprogramm-Tool/AEM-Modernisierungs-Tools , um adaptive Forms basierend auf Foundation-Komponenten in Kernkomponenten-basierte Formulare zu konvertieren
description: Erfahren Sie, wie Sie das Migrationsdienstprogramm/AEM-Modernisierungs-Tools installieren und verwenden, um adaptive Forms-Formulare, die auf Foundation-Komponenten basieren, in Formulare zu konvertieren, die auf Kernkomponenten basieren.
Keywords: Migration Utility Tool, Convert Adaptive Forms based on Foundation Components to Core Component based forms, Convert Foundation forms to Core Components forms, Using Modernizer Tool to convert Foundation Components to Core Components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
exl-id: ee71a576-96a7-4c81-b3a3-1d678f010cba
feature: Adaptive Forms, Core Components
source-git-commit: 92a5599ac94d5bf09311d34dd0287def46b14353
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 8%

---

# Einführung

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

Das Forms Conversion Utility, Teil der [AEM Modernize Tool](https://opensource.adobe.com/aem-modernize-tools/)-Suite, hilft Ihnen bei der einfachen Konvertierung von adaptiven Forms, die mit veralteten Foundation-Komponenten erstellt wurden, in Formulare, die die modernen, unterstützten Funktionen von Kernkomponenten nutzen.

## Was sind AEM-Modernisierungs-Tools?

[AEM-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/) bezieht sich auf eine Reihe von Dienstprogrammen oder Softwareanwendungen, die den Prozess der Modernisierung oder Aktualisierung von Adobe Experience Manager (AEM)-Projekten erleichtern. Diese Tools helfen in der Regel bei der Konvertierung älterer Komponenten oder Funktionen in AEM in neuere, effizientere und unterstützte Alternativen. Das Forms-Konvertierungs-Dienstprogramm wird unter den AEM-Modernisierungs-Tools installiert, um adaptive Forms basierend auf Foundation-Komponenten in Formulare zu konvertieren, die auf Kernkomponenten basieren.

Das Forms-Konvertierungs-Dienstprogramm konvertiert adaptive Forms, die auf älteren Foundation-Komponenten basieren, in neuere Formulare, die auf Kernkomponenten basieren. Durch diesen Konvertierungsprozess wird sichergestellt, dass die Formulare modernen Standards und Funktionen entsprechen, was die Leistung, Kompatibilität und Wartungsfreundlichkeit in der AEM-Umgebung verbessern kann.

![Tools zur AEM-Modernisierung](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
>Es wird empfohlen, die AEM-Modernisierungs-Tools in Ihrem lokalen AEM-Setup zu installieren. Migrieren Sie die auf Foundation-Komponenten basierende adaptive Forms in die auf Kernkomponenten basierenden Formulare. Laden Sie das Formular zusammen mit den Assets herunter. Laden Sie dann das Formular und seine Assets in die erforderliche Umgebung hoch.

## Überlegungen bei Verwendung der AEM-Modernisierungs-Tools {#considerations}

* Bei erfolgreichen Konvertierungen werden alle auf das Formular angewendeten Regeln entfernt. Regeln werden nicht automatisch migriert. Sie sollten diese Regeln manuell neu erstellen und auf das konvertierte Formular anwenden.
* Die im Originalformular verwendeten Übersetzungseinstellungen werden nicht übernommen. Konfigurieren Sie die Übersetzung für das konvertierte Formular neu.
* Wenn das auf Foundation-Komponenten aufbauende Formular Skripte oder benutzerdefinierte Funktionsregeln enthält, müssen Sie diese für das konvertierte Formular auf der Grundlage von Kernkomponenten neu schreiben.
* Die folgenden vorkonfigurierten Foundation-Komponenten werden in Kernkomponenten noch nicht unterstützt und daher in dem konvertierten Formular gelöscht:

   * Adobe Sign Block
   * Diagramm
   * Auflistung der Dateianhänge
   * Fußnoten-Platzhalter
   * Bildauswahl
   * Schaltfläche „Weiter“
   * Schaltfläche „Zurück“
   * Freihändige Unterschrift
   * Zusammenfassungsschritt
   * Symbolleiste

## Voraussetzungen für die Verwendung der AEM-Modernisierungs-Tools

* [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md)
* [Aktivieren der Kernkomponenten für adaptive Forms für Ihre Umgebung.](/help/forms/enable-adaptive-forms-core-components.md)
* Fügen Sie Ihre Benutzer zur [!DNL forms-users] hinzu. Die Mitglieder der Gruppe [!DNL forms-users] sind berechtigt, ein adaptives Formular zu erstellen.
* Benutzende mit den folgenden Rollen sind berechtigt, die AEM-Modernisierungs-Tools in einer AEM-Umgebung zu installieren:

   * Entwicklerrolle
   * Administratorrolle

Eine detaillierte Liste der formularspezifischen Benutzergruppen finden Sie unter [ und Berechtigungen](forms-groups-privileges-tasks.md).

## Installieren und Konfigurieren der AEM-Modernisierungs-Tools

So installieren und konfigurieren Sie die AEM-Modernisierungs-Tools:

1. [Installieren der AEM-Modernisierungs-Tools in Ihrer lokalen AEM Forms-Umgebung](#install-aem-modernize-Tools)
1. [Aktivieren der AEM-Modernisierungs-Tools für Ihre lokale AEM Forms-Umgebung](#enable-aem-modernize-Tools)

### Installieren der AEM-Modernisierungs-Tools in Ihrer lokalen AEM Forms-Umgebung {#install-aem-modernize-Tools}

Führen Sie die folgenden Schritte aus, um die AEM-Modernisierungs-Tools in Ihrer lokalen AEM Forms-Umgebung zu installieren:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal.
1. Starten Sie den lokalen AEM-Autoren-Service. Führen Sie beispielsweise den folgenden Code aus, um die lokale AEM-Autoreninstanz zu starten:

   `java -jar aem-author-p4502.jar`

1. Klonen Sie das Repository [AEM ](https://github.com/adobe/forms-modernizer)Modernisierungs-Tool} in Ihrem lokalen System.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Nach erfolgreichem Ausführen des Befehls steht auf Ihrem Computer eine lokale Kopie des AEM-Modernisierungs-Tool-Repositorys zur Verfügung.

1. Navigieren Sie zu `[AEM Modernize Tool Repository]`in Ihrem lokalen System.
1. Führen Sie den folgenden Befehl aus:

   ```Shell
       mvn clean install 
   ```

![Image für eine erfolgreiche Installation](/help/forms/assets/aem-modernize-install-steps.png)

Nach erfolgreicher Installation werden die AEM-Modernisierungs-Tools für Ihre Umgebung verfügbar.

![AEM-Migrationsdienstprogramm aktivieren](/help/forms/assets/enable-aem-modernizer-tools.png)


### Aktivieren der AEM-Modernisierungs-Tools für Ihre lokale AEM Forms-Umgebung{#enable-aem-modernize-Tools}

Um die AEM-Modernisierungs-Tools für Ihre AEM-Umgebung zu aktivieren und zu verwenden, müssen die Regeln für die Migration von Foundation-Komponenten zu Kernkomponenten zugeordnet werden:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Navigieren Sie zu `http://[host]:[port]/system/console/configMgr`
1. Suchen und Bearbeiten von `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Fügen Sie die `Component Rule Paths` als `/apps/forms-modernizer/rules` hinzu.
1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

![AEM-Modernisierungs-Komponentenregel](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Führen Sie das Dienstprogramm zur Formularkonvertierung aus, um auf Foundation-Komponenten basierende Formulare in auf Kernkomponenten basierende Formulare zu konvertieren

1. Navigieren Sie **[!UICONTROL Tools > AEM-Modernisierungs-Tools > Forms-Konversion]**.

   ![AEM-Modernisierungs-Tools auswählen](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Wählen Sie die Option **[!UICONTROL Forms]** Konversion.

   ![Forms-Konversionsoption auswählen](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klicken Sie **Erstellen**, um einen neuen Auftrag zu erstellen.

   ![AEM-Modernisierungs-Tools - Auftrag erstellen](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Geben Sie den **[!UICONTROL Auftragsnamen]** an.
1. Auf der Registerkarte **[!UICONTROL Formular]** können Sie eine der folgenden Optionen auswählen:

   * **Keine** : Wählen Sie diese Option aus, wenn Sie keine Kopie der auf der Foundation-Komponente basierenden Formulare erstellen möchten, bevor Sie mit der Formularkonvertierung beginnen.
   * **Wiederherstellen** : Wählen Sie diese Option, um das Formular in dem Zustand wiederherzustellen, in dem es sich vor dem Beginn der Formularkonvertierung befand.
   * **In Target kopieren**: Wählen Sie diese Option, um eine Kopie der auf der Foundation-Komponente basierenden Formulare zu erstellen, bevor Sie mit der Formularkonvertierung beginnen.

   In unserem Fall ist die Option **In Target kopieren** ausgewählt. Wenn die Option **In Ziel kopieren** ausgewählt ist, werden die Optionen **[!UICONTROL Source]** und **[!UICONTROL Target Path]** angezeigt.

1. Geben Sie den `source folder` im Pfad **[!UICONTROL Source]** an.
1. Geben Sie den `target folder` im Feld **[!UICONTROL Zielpfad]** an.
1. Wählen Sie **[!UICONTROL Weiter]** aus.
1. Klicken Sie auf **[!UICONTROL Forms]**. Alle Formulare im `source folder` werden auf dem Bildschirm angezeigt.
1. Wählen Sie das auf Foundation-Komponenten basierende adaptive Forms aus, um es in auf Kernkomponenten basierende Formulare zu konvertieren. Sie können auch mehrere Formulare auswählen.

   ![AEM-Modernisierungs-Tools - Formular ](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Klicken Sie **[!UICONTROL Auswählen]**.
1. Klicken Sie **[!UICONTROL Auftrag planen]**, um den Konvertierungsprozess zu starten.
1. Klicken Sie **** Dialogfeld **[!UICONTROL Seiten konvertieren]** auf „Konvertieren“.

   ![AEM-Modernisierungs-Tools konvertieren Seiten](/help/forms/assets/aem-modernize-tools-convert-form.png)

   Wenn der Status des Prozesses in `success` geändert wird. Navigieren Sie zum `target folder`, um das konvertierte Formular anzuzeigen.

   Erfolgreiche Aktualisierung der ![AEM-Tools](/help/forms/assets/aem-modernize-tools-success.png)

1. Wählen Sie das adaptive Formular aus und klicken Sie auf **[!UICONTROL >]**. Die Seite mit den Formulareigenschaften wird geöffnet.

   ![Zielordner der AEM-Modernisierungs-Tools](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Wählen Sie **[!UICONTROL Speichern und schließen]** um die Eigenschaften des konvertierten Formulars erneut zu speichern.
   ![AEM-Modernisierungs-Tools für adaptive Formulareigenschaften](/help/forms/assets/aem-modernize-tools-af-properties.png)

Sie können jetzt sehen, dass das adaptive Formular, das auf Foundation-Komponenten basiert, in das adaptive Formular umgewandelt wird, das auf Kernkomponenten basiert.

## Best Practices {#best-practices}

* Stellen Sie sicher, dass Ihre auf Foundation-Komponenten basierenden Formulare nur die Komponenten verwenden, für die entsprechende [Kernkomponenten](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) verfügbar sind. Wenn Sie Foundation-Komponenten verwenden, die keine entsprechende Kernkomponente haben, wird die Foundation-Komponente nicht konvertiert. Daher funktioniert es beim Erstellen eines Formulars nicht ordnungsgemäß
* Stellen Sie sicher, dass die Regeln zum Konvertieren der Foundation-Komponenten in Kernkomponenten in XML formatiert sind.
