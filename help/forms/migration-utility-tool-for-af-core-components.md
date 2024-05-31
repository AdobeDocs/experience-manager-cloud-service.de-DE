---
title: Migrationsdienstprogramm zum Konvertieren von Adaptive Forms basierend auf Foundation-Komponenten in auf Kernkomponenten basierende Formulare
description: Erfahren Sie, wie Sie das Migrationsdienstprogramm installieren und verwenden, um Adaptive Forms basierend auf Foundation-Komponenten in auf Kernkomponenten basierende Formulare zu konvertieren.
Keywords: Migration Utility tool, Convert Adaptive Forms based on foundation components to core component based forms, Convert Foundation forms to Core components forms, Using Modernizer tool to convert Foundation Components to Core components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 6%

---


# Einführung

Sie können das Migrationsdienstprogramm verwenden, um Adaptive Forms basierend auf Foundation-Komponenten in komponentenbasierte Formulare zu konvertieren. Sie können die [Tool AEM Modernität](https://opensource.adobe.com/aem-modernize-tools/) als Migrationsdienstprogrammwerkzeug. Die [AEM Tools modernisieren](https://opensource.adobe.com/aem-modernize-tools/) stellen eine Suite von Hilfsprogrammen bereit, die verwendet werden, um Adaptive Forms basierend auf Foundation-Komponenten in die modernen und unterstützten Funktionen von Kernkomponenten zu konvertieren.

## Was ist AEM &quot;Tools modernisieren&quot;?

[AEM Tools modernisieren](https://opensource.adobe.com/aem-modernize-tools/) bezeichnet eine Reihe von Hilfsprogrammen oder Softwareanwendungen, die die Modernisierung oder Aktualisierung von Adobe Experience Manager-Projekten (AEM) erleichtern sollen. Diese Tools helfen in der Regel beim Konvertieren älterer Komponenten oder Funktionen innerhalb von AEM in neuere, effizientere und unterstützte Alternativen.

AEM Modernize Tools konvertiert adaptive Forms, die auf älteren Foundation-Komponenten basieren, in neuere, komponentenbasierte Formulare. Dieser Konvertierungsprozess stellt sicher, dass die Formulare modernen Standards und Funktionen entsprechen, was die Leistung, Kompatibilität und Wartungsfreundlichkeit in der AEM potenziell verbessert.

![AEM Tools modernisieren](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> Es wird empfohlen, die AEM Modernize Tools in Ihrem lokalen AEM-Setup zu installieren. Migrieren Sie die Foundation-basierten Formulare in komponentenbasierte Formulare. Laden Sie das Formular zusammen mit seinen Assets herunter. Laden Sie dann das Formular und seine Assets in die erforderliche Umgebung hoch.

## Voraussetzungen für die Verwendung AEM Tools zur Modernisierung

* [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md)
* [Aktivieren Sie die adaptiven Forms-Kernkomponenten für Ihre Umgebung.](/help/forms/enable-adaptive-forms-core-components.md)

* Fügen Sie Ihre Benutzer zu [!DNL forms-users] hinzugefügt. Die Mitglieder der Gruppe [!DNL forms-users] sind berechtigt, ein adaptives Formular zu erstellen.

* Benutzer mit den folgenden Rollen sind berechtigt, die AEM Modernize Tools in einer AEM zu installieren:
   * Entwicklerrolle
   * Administratorrolle Eine detaillierte Liste formularspezifischer Benutzergruppen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

## Installieren und Konfigurieren AEM Tools für die Modernisierung

Schritte zum Installieren und Konfigurieren AEM Tools zur Modernisierung:

1. [Installieren AEM Modernisierungs-Tools in Ihrer lokalen AEM Forms-Umgebung](#install-aem-modernize-tools)
2. [Aktivieren Sie AEM Modernisierungs-Tools für Ihre lokale AEM Forms-Umgebung](#enable-aem-modernize-tools)

### Installieren AEM Modernisierungs-Tools in Ihrer lokalen AEM Forms-Umgebung {#install-aem-modernize-tools}

Führen Sie die folgenden Schritte aus, um AEM Modernize Tools in Ihrer lokalen AEM Forms-Umgebung zu installieren:

1. Starten Sie den lokalen AEM-Author-Service, indem Sie Folgendes über die Befehlszeile ausführen:

   `java -jar aem-author-p4502.jar`

   >[!NOTE]
   >
   > Geben Sie das Admin-Passwort als `admin` an. Jedes Administratorkennwort ist akzeptabel. Es wird jedoch empfohlen, den Standard für die lokale Entwicklung zu verwenden, um eine Neukonfiguration zu vermeiden.

1. Klonen Sie die [AEM Tools modernisieren](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) Repository in Ihrem lokalen System.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tools]
   ```
   Ersetzen Sie die [Pfad des Git-Repositorys der AEM Modernisierungs-Tools] mit der tatsächlichen URL des entsprechenden Git-Repositorys der AEM Modernize Tools.
Nachdem Sie den Befehl erfolgreich ausgeführt haben, steht auf Ihrem Computer eine lokale Kopie des AEM Modernize Tools-Repositorys zur Verfügung.

1. Navigieren Sie zum`[AEM Modernize Tools Repository]`  in Ihrem lokalen System.
1. Führen Sie den folgenden Befehl aus:

   ```Shell
       mvn clean install 
   ```
![Erfolgreiches Installationsbild](/help/forms/assets/aem-modernize-install-steps.png)

Nach erfolgreicher Installation stehen AEM &quot;Modernisierungs-Tools&quot;für Ihre Umgebung zur Verfügung.

![Aktivieren AEM Tools zur Modernisierung](/help/forms/assets/enable-aem-modernizer-tools.png)


### Aktivieren Sie AEM Modernisierungs-Tools für Ihre lokale AEM Forms-Umgebung{#enable-aem-modernize-tools}

Um die AEM Modernisierungs-Tools für Ihre AEM-Umgebung zu aktivieren und zu verwenden, müssen Sie die Regeln für die Migration von Foundation-Komponenten zu Kernkomponenten zuordnen:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Navigieren Sie zu `http://[host]:[port]/system/console/configMgr`
1. Suchen und Bearbeiten der `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Fügen Sie die `Component Rule Paths` as `/apps/forms-modernizer/rules`.
1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

![AEM Modernieren der Komponentenregel](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Führen Sie AEM Modernisierungs-Tools aus, um auf Foundation-Komponenten basierende Formulare in auf Kernkomponenten basierende Formulare zu konvertieren

1. Navigieren Sie zu **[!UICONTROL Tools > AEM Tools modernisieren > Forms-Konversion]**.

   ![Auswahl AEM Tools zur Modernisierung](/help/forms/assets/aem-modernize-tools-select.png)

1. Wählen Sie die **[!UICONTROL Forms-Konversion]** -Option.

   ![Forms-Konvertierungsoption auswählen](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klicks **Erstellen** , um einen neuen Auftrag zu erstellen.

   ![AEM Modernere Tools - Auftrag erstellen](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Geben Sie die **[!UICONTROL Auftragsname]**.
1. Im **[!UICONTROL Formular]** eine der folgenden Optionen auswählen:
   * **Keines** : Wählen Sie diese Option, wenn keine Formularverarbeitung erforderlich ist.
   * **Wiederherstellen** : Wählen Sie diese Option, um das Formular vor der letzten Konvertierung in den Status wiederherzustellen.
   * **In Target kopieren**: Wählen Sie diese Option, um das Formular vor der Konvertierung zu kopieren.
In unserem Fall wird die **In Target kopieren** ausgewählt ist. Wenn die Variable **In Target kopieren** ausgewählt ist, wird die **[!UICONTROL Quellpfad]** und **[!UICONTROL Zielpfad]** -Optionen angezeigt werden.

1. Geben Sie die `source folder` im Namen **[!UICONTROL Quellpfad]**.
1. Geben Sie die `target folder` im Namen **[!UICONTROL Zielpfad]**.
1. Wählen Sie **[!UICONTROL Weiter]** aus.
1. Klicken Sie auf **[!UICONTROL Forms hinzufügen]**. Alle Formulare in der `source folder` auf dem Bildschirm angezeigt.
1. Wählen Sie das Formular basierend auf Foundation-Komponenten aus, um es basierend auf Kernkomponenten in Formulare zu konvertieren. Sie können auch mehrere Formulare auswählen.

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

Sie können jetzt sehen, dass sich das auf Foundation-Komponenten erstellte adaptive Formular in das adaptive Formular umwandelt, das auf Kernkomponenten basiert.

## Überlegungen zur Verwendung des Migrationsdienstprogramms {#considerations}

* Wenn das auf Foundation-Komponenten erstellte Formular benutzerdefinierte Funktionsregeln enthält, müssen Sie diese Regeln für das konvertierte Formular auf der Grundlage von Kernkomponenten neu schreiben.
* Das konvertierte Formular enthält keine Regeln im Regeleditor, weshalb Regeln für das konvertierte Formular neu geschrieben werden müssen.
* Sie müssen den Übersetzungsauftrag für das konvertierte Formular neu erstellen.

## Best Practices {#best-practices}

* Das auf Foundation-Komponenten erstellte Formular enthält nur die Komponenten, die in den auf Kernkomponenten basierenden Komponenten enthalten sind.
* Stellen Sie sicher, dass die Regeln in XML formatiert sind.


