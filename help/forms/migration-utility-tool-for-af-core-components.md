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
source-git-commit: c52d649e569ef427e70c85a88fa0f48fcc534e9e
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 7%

---

# Einführung

<span class="preview"> Die Funktion ist im Programm für frühe Anwender verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

Mit dem Forms-Konvertierungsprogramm, das Teil der Suite &quot;[AEM Modernisierungstool](https://opensource.adobe.com/aem-modernize-tools/)&quot;ist, können Sie das adaptive Forms, das mit älteren Foundation-Komponenten erstellt wurde, einfach in Formulare konvertieren, die die modernen, unterstützten Funktionen der Kernkomponenten nutzen.

## Was ist AEM &quot;Tools modernisieren&quot;?

[AEM Tools modernisieren](https://opensource.adobe.com/aem-modernize-tools/) bezieht sich auf eine Reihe von Hilfsprogrammen oder Softwareanwendungen, die die Modernisierung oder Aktualisierung von Adobe Experience Manager-Projekten (AEM) erleichtern sollen. Diese Tools unterstützen in der Regel bei der Konvertierung älterer Komponenten oder Funktionen innerhalb von AEM in neuere, effizientere und unterstützte Alternativen. Das Forms-Konvertierungsprogramm wird unter AEM &quot;Modernisierungs-Tools&quot;installiert, um das adaptive Forms, das auf Foundation-Komponenten basiert, in auf Kernkomponenten basierende Formulare zu konvertieren.

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

* Fügen Sie Ihre Benutzer zur Gruppe [!DNL forms-users] hinzu. Die Mitglieder der Gruppe [!DNL forms-users] sind berechtigt, ein adaptives Formular zu erstellen.

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

1. Klonen Sie das Repository [AEM Modernisierungs-Tool](/help/journey-migration/refactoring-tools/aem-modernization-tools.md) in Ihrem lokalen System.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Nachdem Sie den Befehl erfolgreich ausgeführt haben, steht auf Ihrem Computer eine lokale Kopie des AEM Modernize Tool-Repositorys zur Verfügung.

1. Navigieren Sie in Ihrem lokalen System zu &quot;`[AEM Modernize Tool Repository]`&quot;.
1. Führen Sie den folgenden Befehl aus:

   ```Shell
       mvn clean install 
   ```
![Erfolgreiches Installationsbild](/help/forms/assets/aem-modernize-install-steps.png)

Nach erfolgreicher Installation stehen die AEM Modernisierungs-Tools für Ihre Umgebung zur Verfügung.

![Aktivieren Sie AEM Migrationsdienstprogramm-Tool](/help/forms/assets/enable-aem-modernizer-tools.png)


### Aktivieren Sie AEM Modernisierungs-Tools für Ihre lokale AEM Forms-Umgebung{#enable-aem-modernize-Tools}

Um die AEM Modernisierungs-Tools für Ihre AEM Umgebung zu aktivieren und zu verwenden, müssen Sie die Regeln für die Migration von Foundation-Komponenten zu Kernkomponenten zuordnen:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Navigieren Sie zu `http://[host]:[port]/system/console/configMgr`
1. Suchen und bearbeiten Sie die `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Fügen Sie die `Component Rule Paths` als `/apps/forms-modernizer/rules` hinzu.
1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

![AEM Modernize Component Rule](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Führen Sie das Formularkonvertierungsdienstprogramm aus, um auf Foundation-Komponenten basierende Formulare in auf Kernkomponenten basierende Formulare zu konvertieren.

1. Navigieren Sie zu **[!UICONTROL Tools > AEM &quot;Modernisierungs-Tools&quot;> Forms-Konversion]**.

   ![AEM Tools modernisieren](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Wählen Sie die Option **[!UICONTROL Forms-Konversion]** aus.

   ![Forms-Konvertierungsoption auswählen](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klicken Sie auf **Erstellen** , um einen neuen Auftrag zu erstellen.

   ![AEM &quot;Auftrag zum Modernieren von Werkzeugen erstellen&quot;](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Geben Sie den **[!UICONTROL Auftragsnamen]** an.
1. Auf der Registerkarte **[!UICONTROL Formular]** können Sie eine der folgenden Optionen auswählen:
   * **None** : Wählen Sie die Option aus, wenn Sie keine Kopie der auf der Foundation-Komponente basierenden Formulare erstellen möchten, bevor Sie mit der Formularkonvertierung beginnen.
   * **Wiederherstellen** : Wählen Sie die Option, um das Formular wieder in den Zustand zu versetzen, in dem es sich vor dem Starten der Formularumwandlung befand.
   * **In Target kopieren**: Wählen Sie die Option, um eine Kopie der auf der Foundation-Komponente basierenden Formulare zu erstellen, bevor Sie mit der Formularkonvertierung beginnen.
In unserem Fall ist die Option **In Target kopieren** ausgewählt. Wenn die Option **In Target kopieren** ausgewählt ist, werden die Optionen **[!UICONTROL Source-Pfad]** und **[!UICONTROL Zielpfad]** angezeigt.

1. Geben Sie den `source folder`-Namen im **[!UICONTROL Source-Pfad]** an.
1. Geben Sie den Namen `target folder` im **[!UICONTROL Zielpfad]** an.
1. Wählen Sie **[!UICONTROL Weiter]** aus.
1. Klicken Sie auf **[!UICONTROL Forms hinzufügen]**. Alle Formulare im Feld `source folder` werden auf dem Bildschirm angezeigt.
1. Wählen Sie Adaptive Forms basierend auf Foundation-Komponenten aus, um sie in auf Kernkomponenten basierende Formulare zu konvertieren. Sie können auch mehrere Formulare auswählen.

   ![AEM Tools modernisieren, Formular auswählen](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Klicken Sie auf **[!UICONTROL Select]**.
1. Klicken Sie auf **[!UICONTROL Auftrag planen]** , um den Konvertierungsprozess zu starten.
1. Klicken Sie im Dialogfeld **[!UICONTROL Seiten konvertieren]** auf **[!UICONTROL Konvertieren]** .

   ![AEM Modernize Tools Convert Pages](/help/forms/assets/aem-modernize-tools-convert-form.png)

   Wenn der Status des Prozesses in `success` geändert wird. Navigieren Sie zu &quot;`target folder`&quot;, um das konvertierte Formular anzuzeigen.

   ![AEM Erfolg der Modernisierung der Tools](/help/forms/assets/aem-modernize-tools-success.png)

1. Wählen Sie das adaptive Formular aus und wählen Sie > **[!UICONTROL Eigenschaften]** aus. Die Seite mit den Formulareigenschaften wird geöffnet.
   ![AEM Modernize Tools Destination Folder](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Wählen Sie **[!UICONTROL Speichern und schließen]** aus, um die Eigenschaften des konvertierten Formulars erneut zu speichern.
   ![AEM Modernize Tools Adpative Form Properties](/help/forms/assets/aem-modernize-tools-af-properties.png)

Sie können jetzt sehen, dass sich das auf Foundation-Komponenten aufbauende adaptive Formular in das auf Kernkomponenten aufbauende adaptive Formular umwandelt.

## Best Practices {#best-practices}

* Stellen Sie sicher, dass Ihre auf Foundation-Komponenten basierenden Formulare nur die Komponenten verwenden, für die eine entsprechende [Kernkomponenten](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) verfügbar ist. In Fällen, in denen Sie Foundation-Komponenten verwenden, die keine äquivalente Kernkomponente haben, wird die Foundation-Komponente nicht konvertiert. Daher funktioniert sie beim Authoring eines Formulars nicht ordnungsgemäß
* Stellen Sie sicher, dass die Regeln zum Konvertieren der Foundation-Komponenten in Kernkomponenten in XML formatiert sind.
