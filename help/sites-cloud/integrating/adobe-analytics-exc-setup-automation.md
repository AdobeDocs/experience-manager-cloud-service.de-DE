---
title: Integrieren von Adobe Analytics mit Experience Cloud Setup Automation
description: Experience Cloud Setup Automation bietet eine einfache und automatisierte Möglichkeit, Experience Manager Sites mit Experience Platform Launch und Adobe Analytics über eine einfache Benutzeroberfläche zu integrieren und zu instrumentieren. Erfahren Sie, wie Sie das automatisierte Setup mit Ihrer eigenen Site verwenden.
feature: Administering
role: Admin
hide: true
hidefromtoc: true
index: false
exl-id: 351ead2c-7b0d-4bd9-a020-47516948d467
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 100%

---

# Integrieren von Adobe Analytics mit Experience Cloud Setup Automation {#integrate-adobe-analytics-automation-setup}

>[!CAUTION]
>
> Diese Funktion befindet sich derzeit in der internen Betaphase. Die Veröffentlichung ist für das 1. Quartal 2022 geplant.

Experience Cloud Setup Automation bietet eine einfache und automatisierte Möglichkeit, Experience Manager Sites mit Experience Platform Launch und Adobe Analytics über eine einfache Benutzeroberfläche zu integrieren und zu instrumentieren. 

Die Integration von Adobe Analytics in Adobe Experience Manager Sites war noch nie einfacher. Dank der Automatisierung des Einrichtens von Experience Cloud können Sie Ihre Site mit nur wenigen Klicks einrichten, integrieren und instrumentieren, um Leistungsanalysen zu erfassen und zu verstehen, wie gut Ihre Kunden interagieren und wie sich die Konversion gestaltet.

In diesem Video wird gezeigt, wie eine AEM-Site anhand der Automatisierung des Einrichtens von Experience Cloud in Experience Platform Launch und Analytics integriert wird:

>[!VIDEO](https://video.tv.adobe.com/v/339605/?quality=12)

## Voraussetzungen

Die automatisierte Einrichtung ist so konzipiert, dass sie sofort mit einer AEM-Site funktioniert, die mit den [AEM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und aktivierter [Adobe-Client-Datenschicht](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=de) erstellt wurde. Sie können eine neue Site erstellen, bei der diese Funktionen automatisch aktiviert sind, indem Sie den [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) verwenden oder eine Site mithilfe einer [Site-Vorlage](/help/journey-sites/quick-site/create-site.md) erstellen.

## Einrichtung

1. Navigieren Sie zu **Sites** und wählen Sie den Stamm der Site aus, die in Adobe Analytics integriert werden soll.
1. Erweitern Sie das Menü der Seitenleiste und tippen Sie auf **Analytics einrichten**.

   Dies ist eine neue Option in der Seitenleiste, durch die sich ein Bedienfeld öffnet, das Steuerelemente und Status für die Automatisierung der Experience Cloud-Einrichtung bereitstellt.
1. Tippen Sie auf die Schaltfläche **Analytics integrieren**.
1. Geben Sie im daraufhin angezeigten Dialogfeld einen Namen für die **Report Suite-ID** ein.

   Diese Zeichenfolge wird verwendet, um in Adobe Analytics eine neue [Report Suite-ID](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en?lang=de) als Datenspeicher für die Analysedaten für die ausgewählte AEM-Site zu erstellen. An die angegebene Zeichenfolge werden Umgebungs- und Ebenen-IDs angehängt, um die Eindeutigkeit sicherzustellen.

1. Aktualisieren Sie die Seite und das Bedienfeld und tippen Sie auf **Integrationsstatus überprüfen**, um den Status der Automatisierung zu überprüfen.

   Die automatisierte Einrichtung erfolgt asynchron. Das **Überprüfen des Integrationsstatus** zeigt den aktuellen Status der Integration an.

   * **In Bearbeitung**: gibt an, dass der Vorgang läuft.
   * **Integration abgeschlossen**: gibt an, dass der Vorgang des Integrierens von Analytics und Launch, des Einrichtens von Launch-Erweiterungen und Launch-Regeln und des Erstellens der neuen Report Suite in Adobe Analytics abgeschlossen ist.
   * **Fehlgeschlagen**: gibt an, dass der automatisierte Vorgang nicht erfolgreich abgeschlossen werden konnte. Überprüfen Sie die Protokolldateien für diesen Vorgang, indem Sie auf den Link „Protokolle“ klicken.

## Validieren der AEM-Einrichtung

Überprüfen Sie nach Abschluss der Automatisierung, ob Ihre Site jetzt die Analytics-Ereignisse auslöst.

1. Öffnen Sie eine Seite auf Ihrer Site mit dem **Sites-Editor**.
1. Verwenden Sie die Option **Als veröffentlicht anzeigen** zum Laden einer veröffentlichten Version der Seite.
1. Verwenden Sie die Entwickler-Tools des Browsers, um den Netzwerk-Traffic zu untersuchen und festzustellen, ob **Launch** und `AppMeasurement.js`-Dateien jetzt geladen werden.
1. Überprüfen Sie in der Konsole des Browsers, dass Ereignisse auf Seiten- und Komponentenebene ausgelöst und von der Adobe-Client-Datenschicht erfasst werden.

## Validieren der Analytics-Einrichtung

Navigieren Sie dann zu Adobe Analytics, um die Daten anzuzeigen, die von den Ereignissen auf der AEM-Site übertragen werden.

1. Navigieren Sie in derselben IMS-Organisation wie Ihre AEM-Site zu Adobe Analytics.
1. Erstellen Sie einen neuen Übersichtsbericht für AEM Sites, indem Sie zu **Berichte** > **Interaktion** > **Adobe Experience Manager** > **Site-Leistungsübersicht** navigieren.
1. Tippen Sie auf **Bericht öffnen**.
1. Wählen Sie die **Report Suite-ID**, die zu dem Namen der in der vorherigen Übung verwendeten Report Suite gehört.
1. Sehen Sie sich an, wie die Analysedaten im Laufe der Zeit in die neue Vorlage fließen.

   >[!NOTE]
   >
   > Bei einer neuen Integration kann es einige Stunden dauern, bis der Bericht mit Daten gefüllt wird.
