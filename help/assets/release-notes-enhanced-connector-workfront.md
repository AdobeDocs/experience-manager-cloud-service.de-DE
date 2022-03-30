---
title: Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector]
description: Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector]
source-git-commit: 02df53e47d2b8617c9a81f5c438814996af92340
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 5%

---


# Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector].

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für die neueste Version von [!DNL Workfront for Experience Manager enhanced connector] ist der 28. März 2022.

## Versionshinweise {#release-highlights}

[!DNL Workfront for Experience Manager enhanced connector] umfasst jetzt die folgenden Aktualisierungen:

* Sie können jetzt verknüpfte Ordner zwischen Adobe Workfront und AEM Assets as a Cloud Service erstellen, auch wenn mehrere projektverknüpfte Ordnerkonfigurationen vorhanden sind.

* Unterstützung für die Seitennummerierung bei Ereignisabonnements hinzugefügt.

* Unterstützung für AEM 6.4.x hinzugefügt.

* Unterstützung für Proxy-Umgebungen hinzugefügt.

* Mehrere Fehlerbehebungen basierend auf Partner- und Kunden-Feedback.

## Bekannte Probleme {#known-issues}

* Beim Konfigurieren von projektbezogenen Ordnern mit AEM 6.4 speichern Experience Manager die Werte nicht für **[!UICONTROL Unterordner]** und **[!UICONTROL Verknüpfte Ordner in Projekten mit Portfolio erstellen]** -Felder. Der Wert für **[!UICONTROL Unterordner]** Feldaktualisierungen zu **[!UICONTROL undefined]** und der Wert für **[!UICONTROL Verknüpfte Ordner in Projekten mit Portfolio erstellen]** Feldaktualisierungen zu **[!UICONTROL Standard-Portfolio]** automatisch nach dem Speichern der Konfiguration.

* Wenn Sie das klassische Workfront-Erlebnis verwenden, wird die **[!UICONTROL Senden an]** -Option verfügbar im **[!UICONTROL Mehr]** in der Dropdown-Liste können Sie das Ziel nicht innerhalb von Experience Manager auswählen. Die **[!UICONTROL Senden an]** -Option funktioniert mit der **[!UICONTROL Dokumentaktionen]** Dropdown-Liste. Die **[!UICONTROL Senden an]** -Option funktioniert ordnungsgemäß für **[!UICONTROL Mehr]** sowie **[!UICONTROL Dokumentaktionen]** Dropdown-Liste, die im neuen Workfront-Erlebnis verfügbar ist.

>[!MORELIKETHIS]
>
>* [Integrieren [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
>* [Integrieren [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=en)


