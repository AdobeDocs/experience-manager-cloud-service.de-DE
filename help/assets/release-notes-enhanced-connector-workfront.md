---
title: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
description: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: f49ac67b7a90d638e266b9f7f5bf5ac9d7f78e3a
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 52%

---

# Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!DNL Workfront for Experience Manager enhanced connector]

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für die neueste Version 1.9.2 von [!DNL Workfront for Experience Manager enhanced connector] ist der 3. August 2022.

## Die Highlights der Version {#release-highlights}

Die neueste Version der [!DNL Workfront for Experience Manager enhanced connector] umfasst die folgenden Verbesserungen und Fehlerbehebungen:

* Die **[!UICONTROL Dokument hochladen]** Workflow-Schritt kann ein Dokument nicht an Workfront anhängen.

* Die **[!UICONTROL Dokument hochladen]** Workflow-Schritt kann ein Dokument nicht an Aufgaben und Probleme in Workfront anhängen. Der Workflow-Schritt hängt ein Dokument erfolgreich an Projekte an.

>[!IMPORTANT]
>
>Adobe empfiehlt, [Aktualisierung auf die neueste Version 1.9.2](../assets/update-workfront-enhanced-connector.md) des [!DNL Workfront for Experience Manager enhanced connector].

## Bekannte Probleme {#known-issues}

* Beim Konfigurieren von projektverknüpften Ordnern mit AEM 6.4 speichert Experience Manager die Werte für die Felder **[!UICONTROL Unterordner]** und **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** nicht. Der Wert für das Feld **[!UICONTROL Unterordner]** wird auf **[!UICONTROL undefiniert]** und der Wert für das Feld **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** wird nach dem Speichern der Konfiguration automatisch auf **[!UICONTROL Standardportfolio]** aktualisiert.

* Wenn Sie das klassische Workfront-Erlebnis verwenden, können Sie mit der Option **[!UICONTROL Senden an]** in der Dropdown-Liste **[!UICONTROL Mehr]** das Ziel in Experience Manager nicht auswählen. Die Option **[!UICONTROL Senden an]** funktioniert korrekt, wenn sie die Dropdown-Liste **[!UICONTROL Dokumentaktionen]** verwenden. Die Option **[!UICONTROL Senden an]** funktioniert sowohl in der Dropdown-Liste **[!UICONTROL Mehr]** als auch in der Dropdown-Liste **[!UICONTROL Dokumentaktionen]**, die in der neuen Workfront-Version verfügbar ist.

## Frühere Versionen {#previous-releases}

### Version Juli 2022 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.1 enthält folgende Aktualisierungen:

* Unterstützung für die Authentifizierung zwischen Experience Manager- und Workfront-Anwendungen mit dem Workfront-API-Schlüssel für Instanzen hinzugefügt, die in Adobe IMS migriert werden.

* Wenn Sie externe Dateien oder Ordner verknüpfen, zeigt das Workfront-Programm die `SERVER_ERROR` Fehlermeldung. Die Fehlermeldung bezieht sich auf eine nicht autorisierte Ausnahme aufgrund einer Inkongruenz in API-Schlüsseln.

* Wenn Sie einen Workflow &quot;Aufgabe erstellen&quot;für ein Asset ausführen, wird in den Protokollmeldungen die Ausnahme &quot;Nullzeiger&quot;angezeigt.

* Wenn Sie die `Replace Spaces with DASH` Konfigurationsoption unter Erweiterte Einstellungen in Experience Manager verwendet, führt dies zur Erstellung doppelter Ordner in Workfront.

### Version Juni 2022 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] umfasst jetzt die folgenden Updates:

* Wenn Sie den Upload über einen verknüpften Ordner durchführen oder die `Send To` -Aktion, die in Workfront verfügbar ist, um Assets in Experience Manager as a Cloud Service hochzuladen, werden die Assets beschädigt und können nicht in Adobe Photoshop geöffnet werden.

### Version März 2022 {#march-2022-release}

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

