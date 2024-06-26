---
title: Migrationsdienstprogramm Tool/AEM Modernisierungs-Tools zum Konvertieren von Adaptive Forms basierend auf Foundation-Komponenten in auf Kernkomponenten basierende Formulare
description: Erfahren Sie, wie Sie das Migrationsdienstprogramm installieren und verwenden/AEM die Modernisierungs-Tools verwenden, um adaptive Forms basierend auf Foundation-Komponenten in auf Kernkomponenten basierende Formulare zu konvertieren.
Keywords: Migration Utility Tool, Convert Adaptive Forms based on Foundation Components to Core Component based forms, Convert Foundation forms to Core Components forms, Using Modernizer Tool to convert Foundation Components to Core Components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
exl-id: ee71a576-96a7-4c81-b3a3-1d678f010cba
feature: Adaptive Forms, Core Components
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 4%

---

# Einführung

Das Forms Conversion Utility, Teil von [AEM-Modernisierungs-Tool](https://opensource.adobe.com/aem-modernize-Tools/) Mithilfe der Suite können Sie adaptive Forms, die mit veralteten Foundation-Komponenten erstellt wurde, einfach in Formulare konvertieren, die die modernen, unterstützten Funktionen der Kernkomponenten nutzen.

## Was ist AEM &quot;Tools modernisieren&quot;?

[AEM Tools modernisieren](https://opensource.adobe.com/aem-modernize-Tools/) bezeichnet eine Reihe von Hilfsprogrammen oder Softwareanwendungen, die die Modernisierung oder Aktualisierung von Adobe Experience Manager-Projekten (AEM) erleichtern sollen. Diese Tools unterstützen in der Regel bei der Konvertierung älterer Komponenten oder Funktionen innerhalb von AEM in neuere, effizientere und unterstützte Alternativen. Das Forms-Konvertierungsprogramm wird unter AEM &quot;Modernisierungs-Tools&quot;installiert, um das adaptive Forms, das auf Foundation-Komponenten basiert, in auf Kernkomponenten basierende Formulare zu konvertieren.

Das Forms Conversion Utility konvertiert adaptive Forms, die auf älteren Foundation-Komponenten basieren, in neuere, auf Kernkomponenten basierende Formulare. Dieser Konvertierungsprozess stellt sicher, dass die Formulare modernen Standards und Funktionen entsprechen, was die Leistung, Kompatibilität und Wartungsfreundlichkeit in der AEM potenziell verbessert.

![AEM Tools modernisieren](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> Es wird empfohlen, die AEM Modernize Tools in Ihrem lokalen AEM-Setup zu installieren. Migrieren Sie die auf Foundation-Komponenten basierende adaptive Forms in auf Kernkomponenten basierende Formulare. Laden Sie das Formular zusammen mit seinen Assets herunter. Laden Sie dann das Formular und seine Assets in die erforderliche Umgebung hoch.

## Überlegungen bei der Verwendung der AEM Modernize Tools {#considerations}

* Bei erfolgreichen Konvertierungen werden alle auf das Formular angewendeten Regeln entfernt. Regeln werden nicht automatisch migriert. Sie sollten diese Regeln manuell neu erstellen und auf das konvertierte Formular anwenden.
* Die im Originalformular verwendeten Übersetzungsparameter werden nicht übernommen. Konfigurieren Sie die Übersetzung für das konvertierte Formular neu.
  <!-- * If the form built on Foundation Components contains custom function rules, you have to rewrite these rules for the converted form based on Core Components.-->

## Voraussetzungen für die Verwendung AEM Tools zur Modernisierung

* [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md)
* [Aktivieren Sie die adaptiven Forms-Kernkomponenten für Ihre Umgebung.](/help/forms/enable-adaptive-forms-core-components.md)

* Fügen Sie Ihre Benutzer zu [!DNL forms-users] hinzugefügt. Die Mitglieder der Gruppe [!DNL forms-users] sind berechtigt, ein adaptives Formular zu erstellen.

* Benutzer mit den folgenden Rollen sind berechtigt, die AEM Modernize Tools in einer AEM zu installieren:
   * Entwicklerrolle
   * Administratorrolle

Eine detaillierte Liste formularspezifischer Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

## Installieren und Konfigurieren AEM Tools für die Modernisierung

So installieren und konfigurieren Sie die AEM Modernisierungs-Tools:

1. [Installieren AEM Modernisierungs-Tools in Ihrer lokalen AEM Forms-Umgebung](#install-aem-modernize-Tools)
2. [Aktivieren Sie AEM Modernisierungs-Tools für Ihre lokale AEM Forms-Umgebung](#enable-aem-modernize-Tools)

### Installieren AEM Modernisierungs-Tools in Ihrer lokalen AEM Forms-Umgebung {#install-aem-modernize-Tools}

Führen Sie die folgenden Schritte aus, um AEM Modernize Tools in Ihrer lokalen AEM Forms-Umgebung zu installieren:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal.
1. Starten Sie den lokalen AEM-Autorendienst. Führen Sie beispielsweise den folgenden Code aus dem aus, um die lokale AEM-Autoreninstanz zu starten:

   `java -jar aem-author-p4502.jar`

1. Klonen Sie die [AEM-Modernisierungs-Tool](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) Repository in Ihrem lokalen System.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Nachdem Sie den Befehl erfolgreich ausgeführt haben, steht auf Ihrem Computer eine lokale Kopie des AEM Modernize Tool-Repositorys zur Verfügung.

1. Navigieren Sie zum`[AEM Modernize Tool Repository]`  in Ihrem lokalen System.
1. Führen Sie den folgenden Befehl aus:

   ```Shell
       mvn clean install 
   ```
![Erfolgreiches Installationsbild](/help/forms/assets/aem-modernize-install-steps.png)

Nach erfolgreicher Installation stehen die AEM Modernisierungs-Tools für Ihre Umgebung zur Verfügung.

![AEM Migrationsdienstprogramm aktivieren](/help/forms/assets/enable-aem-modernizer-tools.png)


### Aktivieren Sie AEM Modernisierungs-Tools für Ihre lokale AEM Forms-Umgebung{#enable-aem-modernize-Tools}

Um die AEM Modernisierungs-Tools für Ihre AEM Umgebung zu aktivieren und zu verwenden, müssen Sie die Regeln für die Migration von Foundation-Komponenten zu Kernkomponenten zuordnen:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Navigieren Sie zu `http://[host]:[port]/system/console/configMgr`
1. Suchen und Bearbeiten der `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Fügen Sie die `Component Rule Paths` as `/apps/forms-modernizer/rules`.
1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

![AEM Modernieren der Komponentenregel](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Ausführen des Dienstprogramm zur Formularumwandlung, um auf Foundation-Komponenten basierende Formulare in auf Kernkomponenten basierende Formulare zu konvertieren

1. Navigieren Sie zu **[!UICONTROL Tools > AEM Tools modernisieren > Forms-Konversion]**.

   ![Auswählen AEM Tools modernisieren](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Wählen Sie die **[!UICONTROL Forms-Konversion]** -Option.

   ![Forms-Konvertierungsoption auswählen](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klicks **Erstellen** , um einen neuen Auftrag zu erstellen.

   ![AEM Modernere Tools - Auftrag erstellen](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Geben Sie die **[!UICONTROL Auftragsname]**.
1. Im **[!UICONTROL Formular]** eine der folgenden Optionen auswählen:
   * **Keines** : Wählen Sie die Option aus, wenn Sie keine Kopie der auf der Foundation-Komponente basierenden Formulare erstellen möchten, bevor Sie mit der Formularkonvertierung beginnen.
   * **Wiederherstellen** : Wählen Sie die Option aus, um das Formular wieder in den Zustand zu versetzen, in dem es sich vor Beginn der Formularkonvertierung befand.
   * **In Target kopieren**: Wählen Sie die Option, um eine Kopie der auf der Foundation-Komponente basierenden Formulare zu erstellen, bevor Sie mit der Formularkonvertierung beginnen.
In unserem Fall wird die **In Target kopieren** ausgewählt ist. Wenn die Variable **In Target kopieren** ausgewählt ist, wird die **[!UICONTROL Source-Pfad]** und **[!UICONTROL Zielpfad]** -Optionen angezeigt werden.

1. Geben Sie die `source folder` im Namen **[!UICONTROL Source-Pfad]**.
1. Geben Sie die `target folder` im Namen **[!UICONTROL Zielpfad]**.
1. Wählen Sie **[!UICONTROL Weiter]** aus.
1. Klicken Sie auf **[!UICONTROL Forms hinzufügen]**. Alle Formulare in der `source folder` auf dem Bildschirm angezeigt.
1. Wählen Sie Adaptive Forms basierend auf Foundation-Komponenten aus, um sie in auf Kernkomponenten basierende Formulare zu konvertieren. Sie können auch mehrere Formulare auswählen.

   ![AEM &quot;Tools modernisieren&quot;Formular auswählen](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Klicks **[!UICONTROL Auswählen]**.
1. Klicks **[!UICONTROL Auftrag planen]** , um den Konvertierungsprozess zu starten.
1. Klicks **[!UICONTROL Konvertieren]** aus dem **[!UICONTROL Seiten konvertieren]** Dialogfeld.

   ![AEM Modernize Tools Seiten konvertieren](/help/forms/assets/aem-modernize-tools-convert-form.png)

   Wenn der Status des Prozesses in `success`. Navigieren Sie zum `target folder` , um das konvertierte Formular anzuzeigen.

   ![Erfolg der AEM](/help/forms/assets/aem-modernize-tools-success.png)

1. Wählen Sie das adaptive Formular aus und wählen Sie > **[!UICONTROL Eigenschaften]**. Die Seite mit den Formulareigenschaften wird geöffnet.
   ![AEM Zielordner der Tools modernisieren](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Auswählen **[!UICONTROL Speichern und schließen]** , um die Eigenschaften des konvertierten Formulars erneut zu speichern.
   ![AEM Modernieren der Tools für adaptive Formulareigenschaften](/help/forms/assets/aem-modernize-tools-af-properties.png)

Sie können jetzt sehen, dass sich das auf Foundation-Komponenten aufbauende adaptive Formular in das auf Kernkomponenten aufbauende adaptive Formular umwandelt.

## Best Practices {#best-practices}

* Stellen Sie sicher, dass Ihre auf Foundation-Komponenten basierenden Formulare nur die Komponenten verwenden, die eine gleichwertige [Kernkomponenten](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) verfügbar. In Fällen, in denen Sie Foundation-Komponenten verwenden, die keine äquivalente Kernkomponente haben, wird die Foundation-Komponente nicht konvertiert. Daher funktioniert sie beim Authoring eines Formulars nicht ordnungsgemäß
* Stellen Sie sicher, dass die Regeln zum Konvertieren der Foundation-Komponenten in Kernkomponenten in XML formatiert sind.
