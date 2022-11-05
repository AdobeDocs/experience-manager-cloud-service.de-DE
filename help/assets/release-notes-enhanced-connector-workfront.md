---
title: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
description: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 1509afad94208e62d5222f4c95c98d90f95be30e
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 69%

---

# Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!DNL Workfront for Experience Manager enhanced connector]

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für die neueste Version 1.9.4 von [!DNL Workfront for Experience Manager enhanced connector] ist der 7. Oktober 2022.

## Die Highlights der Version {#release-highlights}

Die neueste Version von [!DNL Workfront for Experience Manager enhanced connector] enthält die folgenden Verbesserungen und Fehlerbehebungen:

* Aufgrund einer großen Anzahl von Ereignissen kann die Registerkarte &quot;Ereignisabonnements&quot;auf der Seite mit der verbesserten Connector-Konfiguration nicht angezeigt werden.

* Workfront kann die Liste der in einem Projekt vorhandenen Ordner nicht abrufen, was zur Erstellung doppelter Ordner führt.

>[!IMPORTANT]
>
>Adobe empfiehlt eine [Aktualisierung auf die neueste Version 1.9.4](../assets/update-workfront-enhanced-connector.md) des [!DNL Workfront for Experience Manager enhanced connector].

## Bekannte Probleme {#known-issues}

* Beim Konfigurieren von projektverknüpften Ordnern mit AEM 6.4 speichert Experience Manager die Werte für die Felder **[!UICONTROL Unterordner]** und **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** nicht. Der Wert für das Feld **[!UICONTROL Unterordner]** wird auf **[!UICONTROL undefiniert]** und der Wert für das Feld **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** wird nach dem Speichern der Konfiguration automatisch auf **[!UICONTROL Standardportfolio]** aktualisiert.

* Wenn Sie das klassische Workfront-Erlebnis verwenden, können Sie mit der Option **[!UICONTROL Senden an]** in der Dropdown-Liste **[!UICONTROL Mehr]** das Ziel in Experience Manager nicht auswählen. Die Option **[!UICONTROL Senden an]** funktioniert korrekt, wenn sie die Dropdown-Liste **[!UICONTROL Dokumentaktionen]** verwenden. Die Option **[!UICONTROL Senden an]** funktioniert sowohl in der Dropdown-Liste **[!UICONTROL Mehr]** als auch in der Dropdown-Liste **[!UICONTROL Dokumentaktionen]**, die in der neuen Workfront-Version verfügbar ist.

* Workfront zeigt eine `SERVER_ERROR` Meldung beim Verknüpfen von Dokumenten mit AEM nach der Aktualisierung auf Version 8316. Um das Problem zu beheben, weisen Sie `rep:readProperties` nach `content/dam/collections` für `wf-workfront-user` AEM Benutzergruppe.

## Frühere Versionen {#previous-releases}

### Version September 2022 {#september-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.3, veröffentlicht am 16. September, enthält folgende Aktualisierungen:

* Eine Datei mit einer Größe von mehr als 8 GB kann nicht hochgeladen werden.
* Probleme beim automatischen Veröffentlichen von Assets, die von Workfront an AEM gesendet werden.
* Das Feld Stammpfad ist beim Bearbeiten eines standardmäßigen Metadatenschema-Formulars nicht für das Feld Tags verfügbar.
* Probleme beim Hinzufügen neuer Versionen in Workfront mithilfe AEM Workflows.
* Wenn Sie eine AEM Suche nach in Workfront verfügbaren Assets durchführen, zeigt AEM eine Fehlermeldung an.
* Wenn Sie einen AEM Workflow für die Aufgabenerstellung aus einem Asset erstellen und keinen übergeordneten Aufgabennamen definieren, wird die Aufgabe nicht in Workfront erstellt.

### Version August 2022 {#august-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.2, veröffentlicht am 3. August, enthält folgende Aktualisierungen:

* Mit dem Workflow-Schritt **[!UICONTROL Dokument hochladen]** kann kein Dokument an Workfront angehängt werden.

* Mit dem Workflow-Schritt **[!UICONTROL Dokument hochladen]** kann kein Dokument an Aufgaben und Probleme in Workfront angehängt werden. Mit dem Workflow-Schritt kann ein Dokument erfolgreich an Projekte angehängt werden.

### Version vom Juli 2022 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.1 enthält die folgenden Aktualisierungen:

* Die Authentifizierung zwischen Experience Manager und Workfront-Anwendungen mithilfe des Workfront-API-Schlüssels für Instanzen, die zu Adobe IMS migriert wurden, wird nun unterstützt.

* Wenn Sie externe Dateien oder Ordner verknüpfen, zeigt die Workfront-Anwendung die Fehlermeldung `SERVER_ERROR` an. Die Fehlermeldung bezieht sich auf die Ausnahme „Nicht autorisiert“ aufgrund von nicht übereinstimmenden API-Schlüsseln.

* Wenn Sie den Workflow „Aufgabe erstellen“ für ein Asset ausführen, wird die Ausnahme „Null Pointer“ in den Protokollmeldungen angezeigt.

* Wenn Sie die `Replace Spaces with DASH`-Konfigurationsoption unter „Erweiterte Einstellungen“ in Experience Manager aktivieren, führt dies zu einer doppelten Ordnererstellung in Workfront.

### Version vom Juni 2022 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] umfasst jetzt die folgenden Updates:

* Wenn Sie einen Upload über einen verknüpften Ordner durchführen oder die in Workfront verfügbare `Send To`-Aktion verwenden, um Assets in Experience Manager as a Cloud Service hochzuladen, werden die Assets beschädigt und können nicht in Adobe Photoshop geöffnet werden.

### Version vom März 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] umfasst jetzt die folgenden Updates:

* Sie können jetzt zwischen Adobe Workfront und AEM Assets as a Cloud Service verknüpfte Ordner erstellen, auch wenn es mehrere Konfigurationen für verknüpfte Projektordner gibt.

* Es wurde Unterstützung für die Paginierung von Ereignisabonnements hinzugefügt.

* Es wurde Unterstützung für AEM 6.4.x hinzugefügt.

* Es wurde Unterstützung für Proxy-Umgebungen hinzugefügt.

* Verschiedene Fehlerkorrekturen auf der Grundlage von Partner- und Kunden-Feedback.

>[!MORELIKETHIS]
>
>* [Integrieren von [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=de)
>* [Integrieren von [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=de)

