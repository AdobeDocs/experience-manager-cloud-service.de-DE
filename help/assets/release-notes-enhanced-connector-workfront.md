---
title: Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector]
description: Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 081f7ed8c39382408285887928163e2569c5cbfe
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 4%

---

# Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector].

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für die neueste Version 1.9.0 von [!DNL Workfront for Experience Manager enhanced connector] ist der 16. Juni 2022.

## Versionshinweise {#release-highlights}

Die neueste Version der [!DNL Workfront for Experience Manager enhanced connector] umfasst die folgende Fehlerbehebung:

* Wenn Sie den Upload über einen verknüpften Ordner durchführen oder die `Send To` -Aktion, die in Workfront verfügbar ist, um Assets in Experience Manager as a Cloud Service hochzuladen, werden die Assets beschädigt und können nicht in Adobe Photoshop geöffnet werden.

>[!IMPORTANT]
>
>Adobe empfiehlt, [Aktualisierung auf die neueste Version 1.9.0](../assets/update-workfront-enhanced-connector.md) des [!DNL Workfront for Experience Manager enhanced connector].

## Bekannte Probleme {#known-issues}

* Beim Konfigurieren von projektbezogenen Ordnern mit AEM 6.4 speichern Experience Manager die Werte nicht für **[!UICONTROL Unterordner]** und **[!UICONTROL Verknüpfte Ordner in Projekten mit Portfolio erstellen]** -Felder. Der Wert für **[!UICONTROL Unterordner]** Feldaktualisierungen zu **[!UICONTROL undefined]** und der Wert für **[!UICONTROL Verknüpfte Ordner in Projekten mit Portfolio erstellen]** Feldaktualisierungen zu **[!UICONTROL Standard-Portfolio]** automatisch nach dem Speichern der Konfiguration.

* Wenn Sie das klassische Workfront-Erlebnis verwenden, wird die **[!UICONTROL Senden an]** -Option verfügbar im **[!UICONTROL Mehr]** in der Dropdown-Liste können Sie das Ziel nicht innerhalb von Experience Manager auswählen. Die **[!UICONTROL Senden an]** -Option funktioniert mit der **[!UICONTROL Dokumentaktionen]** Dropdown-Liste. Die **[!UICONTROL Senden an]** -Option funktioniert ordnungsgemäß für **[!UICONTROL Mehr]** sowie **[!UICONTROL Dokumentaktionen]** Dropdown-Liste, die im neuen Workfront-Erlebnis verfügbar ist.

## Frühere Versionen {#previous-releases}

### Version März 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] umfasst jetzt die folgenden Aktualisierungen:

* Sie können jetzt verknüpfte Ordner zwischen Adobe Workfront und AEM Assets as a Cloud Service erstellen, auch wenn mehrere projektverknüpfte Ordnerkonfigurationen vorhanden sind.

* Unterstützung für die Seitennummerierung bei Ereignisabonnements hinzugefügt.

* Unterstützung für AEM 6.4.x hinzugefügt.

* Unterstützung für Proxy-Umgebungen hinzugefügt.

* Mehrere Fehlerbehebungen basierend auf Partner- und Kunden-Feedback.

>[!MORELIKETHIS]
>
>* [Integrieren [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
>* [Integrieren [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=en)

