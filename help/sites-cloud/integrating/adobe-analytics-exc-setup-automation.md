---
title: Integrieren von Adobe Analytics mit der Automatisierung der Experience Cloud-Einrichtung
description: Die Automatisierung des Experience Cloud-Setups bietet eine einfache und automatisierte Möglichkeit, Experience Manager Sites mit Experience Platform Launch und Adobe Analytics über eine einfache Benutzeroberfläche zu integrieren und zu instrumentieren. Erfahren Sie, wie Sie das automatisierte Setup mit Ihrer eigenen Site verwenden.
feature: Administering
role: Admin
hide: true
hidefromtoc: true
index: false
source-git-commit: 6c84c0eff6392f1f86c18c9daf15c402c4d9e778
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 3%

---


# Integrieren von Adobe Analytics mit der Automatisierung der Experience Cloud-Einrichtung {#integrate-adobe-analytics-automation-setup}

>[!CAUTION]
>
> Diese Funktion befindet sich derzeit in der internen Beta-Phase. Die Target-Version liegt im 1. Quartal 2022 vor.

Die Automatisierung des Experience Cloud-Setups bietet eine einfache und automatisierte Möglichkeit, Experience Manager Sites mit Experience Platform Launch und Adobe Analytics über eine einfache Benutzeroberfläche zu integrieren und zu instrumentieren.

Die Integration von Adobe Analytics in AEM Sites war noch nie einfacher. Mit der Automatisierung des Experience Cloud-Setups können Sie Ihre Site einrichten, integrieren und instrumentieren, um Leistungsanalysen zu erfassen, um zu verstehen, wie gut Ihre Kunden interagieren und wie sich die Konversion gestaltet, und mit nur wenigen Klicks.

In diesem Video wird anhand der Automatisierung des Experience Cloud-Setups untersucht, wie eine AEM Site in Experience Platform Launch und Analytics integriert wird:

>[!VIDEO](https://video.tv.adobe.com/v/339605/?quality=12)

## Voraussetzungen

Die Automatisierungseinrichtung ist so konzipiert, dass sie mit einer AEM Site, die mit [AEM Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) mit dem [Adobe Client-Datenschicht](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=de) aktiviert. Sie können eine neue Site erstellen, für die diese Funktionen automatisch aktiviert werden, indem Sie die [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) oder durch Erstellen einer Site mithilfe einer [Site-Vorlage](/help/journey-sites/quick-site/create-site.md).

## Einrichtung

1. Navigieren Sie zu **Sites** und wählen Sie den Stamm der Website aus, die in Adobe Analytics integriert werden soll.
1. Erweitern Sie das Menü der Seitenleiste und tippen Sie auf **Einrichten von Analytics**.

   Dies ist eine neue Option in der Seitenleiste, mit der ein Bedienfeld geöffnet wird, das Steuerelemente und Status für die Automatisierung der Experience Cloud-Einrichtung bereitstellt.
1. Tippen Sie auf **Integration von Analytics** Schaltfläche.
1. Geben Sie im daraufhin angezeigten Dialogfeld einen Namen für die **Report Suite-ID**.

   Diese Zeichenfolge wird verwendet, um eine neue [Report Suite-ID](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en) in Adobe Analytics als Datenspeicher für die Analysedaten für die ausgewählte AEM Site. Die angegebene Zeichenfolge wird mit Umgebungs- und Tier-IDs angehängt, um die Eindeutigkeit sicherzustellen.

1. Aktualisieren Sie die Seite und das Bedienfeld und tippen Sie auf **Überprüfen des Integrationsstatus** , um den Status der Automatisierung zu überprüfen.

   Die Automatisierung wird asynchron eingerichtet. Die **Überprüfen des Integrationsstatus** zeigt den aktuellen Status der Integration an.

   * **In Bearbeitung** - gibt an, dass der Auftrag ausgeführt wird.
   * **Integration abgeschlossen** - gibt an, dass der Vorgang die Integration von Analytics und Launch, die Einrichtung von Launch-Erweiterungen und Launch-Regeln und die Erstellung der neuen Report Suite in Adobe Analytics abgeschlossen hat.
   * **Fehlgeschlagen** - gibt an, dass der automatisierte Auftrag nicht erfolgreich abgeschlossen werden konnte. Überprüfen Sie die Protokolldateien für diesen Auftrag, indem Sie auf den Link Protokolle klicken.

## AEM überprüfen

Überprüfen Sie nach Abschluss der Automatisierung, ob Ihre Site jetzt die Analytics-Ereignisse auslöst.

1. Öffnen Sie eine Seite auf Ihrer Site mithilfe der **Sites-Editor**.
1. Verwenden Sie die **Als veröffentlicht anzeigen** zum Laden einer veröffentlichten Version der Seite.
1. Verwenden Sie die Entwickler-Tools des Browsers, um den Netzwerk-Traffic zu untersuchen und festzustellen, ob **Launch** und `AppMeasurement.js` -Dateien werden jetzt geladen.
1. Inspect Sie in der Browserkonsole, um zu sehen, dass Ereignisse auf Seiten- und Komponentenebene von der Adobe Client-Datenschicht ausgelöst und erfasst werden.

## Validieren der Analytics-Einrichtung

Navigieren Sie dann zu Adobe Analytics , um die Daten anzuzeigen, die von den Ereignissen auf der AEM Site übertragen werden.

1. Navigieren Sie in derselben IMS-Organisation wie Ihre AEM-Site zu Adobe Analytics.
1. Erstellen Sie einen neuen Übersichtsbericht für AEM Sites, der zu **Berichte** > **Interaktion** > **Adobe Experience Manager** > **Site-Leistungsübersicht**.
1. Tippen **Bericht öffnen**.
1. Wählen Sie die **Report Suite-ID** , der mit dem in der vorherigen Übung verwendeten Report Suite-Namen übereinstimmt.
1. Anzeigen des Datenflusses von Analysedaten in die neue Vorlage im Zeitverlauf.

   >[!NOTE]
   >
   > Bei einer neuen Integration kann es einige Stunden dauern, bis der Bericht mit Daten gefüllt wird.
