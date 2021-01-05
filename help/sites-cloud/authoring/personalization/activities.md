---
title: 'Verwalten von Aktivitäten '
description: Mithilfe der Aktivitätskonsole können Sie die Marketing-Aktivitäten Ihrer Marken erstellen, organisieren und verwalten
translation-type: tm+mt
source-git-commit: dba848cb8d7bc42f37fb64131150c136e07dd24e
workflow-type: tm+mt
source-wordcount: '2002'
ht-degree: 100%

---


# Verwalten von Aktivitäten  {#managing-activities}

Mithilfe der Aktivitätskonsole können Sie die Marketing-[Aktivitäten](/help/sites-cloud/authoring/personalization/overview.md#activities) Ihrer Marken erstellen, organisieren und verwalten:

* Fügen Sie Marken hinzu.
* Fügen Sie jeder Marke Aktivitäten hinzu und konfigurieren Sie diese.
* Verwalten Sie Aktivitäten.

>[!TIP]
>
>Verwenden Sie Adobe Target als Targeting-Engine, können Sie die [Leistungsdaten Ihrer Aktivitäten anzeigen](#viewing-performance-and-converting-winning-experiences-a-b-test). Wenn Sie mit A/B-Tests arbeiten, können Sie die [Gewinner konvertieren](#viewing-performance-and-converting-winning-experiences-a-b-test).

Aktivitäten lassen sich in der Aktivitätskonsole nach Marke sortieren. Verwenden Sie Marken und Ordner, um Aktivitäten zu strukturieren und organisieren. Navigieren Sie durch die Aktivitätskonsole, indem Sie auf **Personalisierung** klicken oder tippen und **Aktivitäten** auswählen.

Aktivitäten stehen im Targeting-Modus für das [Verfassen zielgerichteter Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) zur Verfügung, wobei Sie in diesem Modus auch Aktivitäten erstellen können. Im Targeting-Modus erstellte Aktivitäten werden in der Aktivitätskonsole aufgeführt.

Aktivitäten werden mit einer Beschriftung versehen, die beschreibt, um welche Aktivitätsart es sich handelt:

* XT – Erlebnis-Targeting in Adobe Target
* A/B – A/B-Tests in Adobe Target
* AEM – Adobe Experience Manager-Targeting (d. h. ContextHub-gesteuert)

![Aktivitätstypen](/help/sites-cloud/authoring/assets/activities-types.png)

>[!NOTE]
>
>Welche Aktivitätstypen zur Verfügung stehen, hängt von folgenden Faktoren ab:
>
>* Bei Aktivierung der Option `xt_only` im Adobe Target-Mandanten (Client-Code), der auf AEM-Seite für die Verbindung zu Adobe Target verwendet wird, können Sie in AEM ausschließlich **XT-Aktivitäten** erstellen.
   >
   >
* Ist die Option `xt_only` im Adobe Target-Mandanten (Client-Code) **nicht** aktiviert, können Sie in AEM **sowohl** XT- als auch A/B-Aktivitäten erstellen.
>
>
**Zusätzlicher Hinweis:** Bei der Option `xt_only` handelt es sich um eine Einstellung, die auf einen bestimmten Target-Mandanten (Clientcode) angewendet wird und nur in Adobe Target bearbeitet werden kann. Die Option kann in AEM nicht aktiviert oder deaktiviert werden.

>[!CAUTION]
>
>Sie müssen den Aktivitätseinstellungsknoten `cq:ActivitySettings` in der Veröffentlichungsinstanz sichern, sodass dieser für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Dienst zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.
>
>Detaillierte Informationen finden Sie unter „Voraussetzungen für die Integration mit Adobe Target“.
<!--
>See [Prerequisites for Integrating with Adobe Target](/help/sites-administering/target-requirements.md#securingtheactivitysettings) for detailed information.
-->

## Erstellen von Marken mithilfe der Aktivitätskonsole {#creating-a-brand-using-the-activities-console}

Erstellen Sie eine Marke, deren Marketing-Aktivitäten Sie verwalten möchten.

Wenn Sie mithilfe der Aktivitätskonsole eine Marke erstellen, erscheint diese ebenfalls in der [Angebotskonsole](/help/sites-cloud/authoring/personalization/offers.md), in der Sie Angebote für die Erlebnisse Ihrer Aktivitäten erstellen können.

1. Klicken oder tippen Sie in der Navigationskonsole auf **Personalisierung**. Klicken oder tippen Sie auf **Aktivitäten**.

   ![Navigieren zu Aktivitäten](/help/sites-cloud/authoring/assets/activities-navigation.png)

1. Klicken oder tippen Sie in der Aktivitätskonsole auf **Erstellen** und anschließend auf **Marke erstellen**.
1. Wählen Sie die Markenvorlage aus und klicken oder tippen Sie auf **Weiter**.
1. Geben Sie den Namen der Marke an, der in den Konsolen „Aktivitäten“ und „Angebote“ angezeigt werden soll. Wenn gewünscht, können Sie zudem einen oder mehrere Tags auswählen, um diese mit der Marke zu verknüpfen.
1. Klicken oder tippen Sie auf **Erstellen**. Die Marke erscheint nun in der Aktivitätskonsole.

## Hinzufügen/Bearbeiten von Aktivitäten mithilfe der Aktivitätskonsole      {#adding-editing-an-activity-using-the-activities-console}

Fügen Sie eine Aktivität hinzu oder bearbeiten Sie eine bestehende Aktivität, um Ihre Marketinganstrengungen auf bestimmte Zielgruppen abzustimmen. Beim Erstellen oder Bearbeiten von Aktivitäten werden folgende Daten festgelegt:

* **Name:** Der Name der Aktivität.
* **Targeting-Engine:** Entweder [AEM](/help/sites-cloud/authoring/personalization/overview.md#aem) oder [Adobe Target](/help/sites-cloud/authoring/personalization/overview.md#adobe-target) als Engine für zielgerichtete Inhalte.
* **Auswählen einer Target-Konfiguration:** (Nur Adobe Target) Die Cloud-Konfiguration, mit der diese Aktivität eine Verbindung zu Adobe Target herstellen soll. Diese Option wird nur angezeigt, wenn Adobe Target für die Targeting-Engine ausgewählt wurde.
* **Aktivitätstyp**: der Aktivitätstyp – A/B-Test oder Erlebnis-Targeting.
* **Zielsetzung:** (Optional) Eine Beschreibung der Aktivität.
* **Erlebnisse:** Zuordnungen zwischen Zielgruppennamen und den Marketingsegmenten, die Sie als Ziel auswählen.
* **Traffic-Anteile**: wurde A/B-Test ausgewählt, können Sie festlegen, welcher Anteil des Traffics (in Prozent) an die verschiedenen Erlebnisse weitergeleitet wird.
* **Dauer:** Der Zeitraum, in dem die Aktivität angewendet wird.
* **Priorität:** Die relative Priorität der Aktivität. Wenn Aktivitäten Inhalte für dieselben Benutzersegmente bereitstellen, hat die Aktivität mit höherer Priorität Vorrang.
* **Zielmetrik**: wurde Adobe Target als Targeting-Engine ausgewählt, können Sie der Aktivität Erfolgsmetriken hinzufügen. Eine Erfolgsmetrik ist erforderlich.

>[!NOTE]
>
>Neue Adobe Target-Aktivitäten müssen im Editor für zielgerichtete Inhalte *erstellt* werden, nicht in der Konsole **Aktivitäten**, da die Synchronisierung mit Adobe Target fehlschlägt.
>
>Bestehende Adobe Target-Aktivitäten können jedoch in der Konsole bearbeitet werden.

So fügen Sie eine Aktivität hinzu:

1. Klicken oder tippen Sie auf die Marke, für die Sie eine Aktivität erstellen möchten, klicken oder tippen Sie auf **Erstellen** und anschließend auf **Aktivität erstellen**. Wenn Sie eine Aktivität bearbeiten möchten, wählen Sie sie im Master-Gebiet-Bildschirm aus und klicken oder tippen Sie auf **Aktivität bearbeiten**.
1. Machen Sie folgende Angaben und klicken oder tippen Sie dann auf **Weiter**:
   * Der Name der Aktivität.
   * Die zu verwendende Targeting-Engine. Standardmäßig ist ContextHub (AEM) ausgewählt. Sollten Sie Adobe Target verwenden, erstellen Sie die Aktivität im Editor für zielgerichtete Inhalte.
   * Haben Sie Adobe Target als Targeting-Engine ausgewählt, wählen Sie die Cloud-Konfiguration aus, die für die Verbindung mit Adobe Target verwendet werden soll, oder bearbeiten Sie diese. (Achten Sie darauf, kein Framework auszuwählen, das für die Cloud-Konfiguration erstellt wurde.)
   * (Optional) Das Ziel oder die Beschreibung der Aktivität.
   * Wählen Sie den Aktivitätstyp aus.
1. Fügen Sie der Aktivität mindestens ein Erlebnis hinzu. Tippen/Klicken Sie auf **Erlebnis hinzufügen**.
1. Wenn Sie AEM-Targeting oder Adobe Target (Erlebnis-Targeting) verwenden:
   1. Klicken oder tippen Sie auf **Zielgruppe wählen** und wählen Sie das Segment aus, auf das Ihr Erlebnis abgestimmt ist.
   1. Klicken oder tippen Sie auf **Erlebnis hinzufügen**, geben Sie einen Namen ein und klicken oder tippen Sie auf **OK**. 
   1. Klicken oder tippen Sie auf **Weiter**.
Wenn Sie A/B-Tests in Adobe Target verwenden:
   1. Klicken oder tippen Sie auf den Stift im Zielgruppenfeld, um eine Zielgruppe auszuwählen.
   1. Klicken oder tippen Sie auf **Erlebnis hinzufügen**, geben Sie einen Namen ein und klicken oder tippen Sie auf **OK**.
   1. Geben Sie den prozentualen Anteil des Traffics ein, der auf die jeweiligen Erlebnisse umgelenkt wird.
   1. Klicken oder tippen Sie auf **Weiter**.
1. Verwenden Sie das Dropdown-Menü **Start**, um festzulegen, wann die Aktivität beginnen soll. Wählen Sie einen der folgenden Werte aus:
   * **Ist diese Option aktiviert**, beginnt die Aktivität, sobald die Seite aktiviert wird, auf der sich der zielgerichtete Inhalt befindet.
   * **Angegeb. Datum und Zeit**: ein bestimmter Zeitpunkt. Wenn Sie diese Option auswählen, tippen/klicken Sie auf das Kalendersymbol, wählen Sie ein Datum aus und geben Sie die Zeit an, zu der die Aktivität gestartet werden soll.
1. Verwenden Sie das Dropdown-Menü „Ende“, um festzulegen, wann die Aktivität beendet werden soll. Wählen Sie einen der folgenden Werte aus:
   * **Ist diese Option deaktiviert**, endet die Aktivität, sobald die Seite deaktiviert wird, auf der sich der Targeting-Inhalt befindet.
   * **Angegeb. Datum und Zeit**: ein bestimmter Zeitpunkt. Wurde diese Option ausgewählt, klicken oder tippen Sie auf das Kalendersymbol, wählen Sie ein Datum aus und geben Sie die Uhrzeit an, zu der die Aktivität beendet werden soll.
1. Soll die Aktivität eine Priorität erhalten, wählen Sie mit dem Schieberegler entweder **Niedrig**, **Normal** oder **Hoch** aus.
1. Wenn Sie Adobe Target als Targeting-Engine verwenden, wählen Sie aus, was mit dieser Aktivität gemessen werden soll. Weitere Informationen zu verfügbaren Erfolgsmetriken finden Sie unter [Konfigurieren der Aktivität und Festlegen von Zielen](/help/sites-cloud/authoring/personalization/targeted-content.md). Sie müssen mindestens ein Ziel auswählen.
1. Klicken oder tippen Sie auf **Speichern**.

   >[!NOTE]
   >
   >Nach dem Erstellen einer Aktivität muss diese zunächst veröffentlicht werden, damit sie verfügbar ist.

## Veröffentlichen von Aktivitäten und Rückgängigmachen der Veröffentlichung von Aktivitäten {#publishing-and-unpublishing-activities}

Sollen Aktivitäten verfügbar sein, müssen diese zunächst veröffentlicht werden. Auf der anderen Seite möchten Sie die Verfügbarkeit von Aktivitäten möglicherweise verhindern, was durch das Rückgängigmachen einer Veröffentlichung erzielt wird.

>[!NOTE]
>
>Wenn Sie die Veröffentlichung einer Aktivität rückgängig machen,   ändert sich der Status der Aktivität nur, wenn Sie die Seite aktualisieren.

So veröffentlichen Sie Aktivitäten oder machen deren Veröffentlichung rückgängig:

1. Klicken oder tippen Sie auf die Marke und anschließend auf das Gebiet, das die Aktivität enthält, die veröffentlicht bzw. deren Veröffentlichung rückgängig gemacht werden soll.
1. Klicken oder tippen Sie auf das Symbol neben der Aktivität oder den Aktivitäten, die Sie veröffentlichen bzw. deren Veröffentlichung Sie rückgängig machen möchten.

   ![Veröffentlichen über die Aktivitätskonsole](/help/sites-cloud/authoring/assets/activities-console.png)

1. Soll die Aktivität veröffentlicht werden, klicken oder tippen Sie auf **Veröffentlichen**. Soll die Veröffentlichung der Aktivität rückgängig gemacht werden, klicken oder tippen Sie auf **Veröffentlichung rückgängig machen**. Die jeweilige Aktion wird durchgeführt und der Status der Aktivitäten in der Aktivitätskonsole angepasst (möglicherweise muss die Seite hierzu aktualisiert werden).

## Aktivitäten in der Autoren- und Veröffentlichungsinstanz     {#activities-on-author-and-publish-instances}

Wird eine Aktivität aktiviert, deren Targeting-Engine Adobe Target ist, wird in der Autoreninstanz eine zweite Aktivität erstellt:

* Mit der Aktivität in der Autoreninstanz wird die Aktivität in der Autoreninstanz verfolgt, was sich für die Simulation des Besuchererlebnisses oft als sehr nützlich erweist. Die für diese Aktivität aufgezeichneten Analysedaten spiegeln lediglich wider, was in der Autoreninstanz geschieht.
* Die Aktivität in der Veröffentlichungsinstanz spiegelt die Aktivität auf dem Veröffentlichungsserver wider und reagiert auf Serveranfragen. Hierbei handelt es sich um die Aktivität, die auf der öffentlichen Website angezeigt wird. Für die Verfolgung und Analyse der Verwendung der online befindlichen Site wird nur die Aktivität der Veröffentlichungsinstanz benötigt.

## Anzeigen der Performance und Konvertieren von Gewinnererlebnissen (A/B-Tests)      {#viewing-performance-and-converting-winning-experiences-a-b-test}

Sie können die Leistung beliebiger Adobe Target-Aktivitäten (XT oder A/B) anzeigen. Wenn Sie A/B-Tests verwenden, können Sie zudem die Gewinnererlebnisse in Standarderlebnisse konvertieren.

So prüfen Sie die Leistung und konvertieren Gewinnererlebnisse:

1. Klicken Sie unter **Personalisierung** auf **Aktivitäten**, um zur **Aktivitätskonsole** zu navigieren.
1. Klicken oder tippen Sie auf die Marke, deren Aktivitäten Sie anzeigen möchten.
1. Wählen Sie eine Aktivität aus, klicken oder tippen Sie auf **Eigenschaften anzeigen** und klicken Sie auf die Registerkarte **Berichte**, um die Aktivität auszuwählen, deren Leistung Sie prüfen/deren Gewinnererlebnisse Sie konvertieren möchten. Die Leistungsdaten werden nun angezeigt.

   ![Überprüfen der Aktivitätsleistung](/help/sites-cloud/authoring/assets/activities-performance.png)

1. Klicken oder tippen Sie auf den Link **Gewinner pushen**, um das Erlebnis als Standarderlebnis festzulegen.

   Durch die Konvertierung des Gewinners geschieht Folgendes:

   * Die aktuelle Aktivität wird deaktiviert.
   * Es werden alle Seiten modifiziert und zielgerichtete Inhalte durch die Inhalte des Gewinnererlebnisses ersetzt. Der Inhalt des Gewinnererlebnisses wird Teil der normalen Seite **ohne** Targeting.

   ![Konvertieren des Gewinners](/help/sites-cloud/authoring/assets/activities-reports.png)

   Gewinnererlebnisse sind diejenigen Erlebnisse, die in den Berichten größere Steigerungen als andere erzielen. Diese Steigerungen werden aus der Konversionsrate errechnet.

1. Klicken oder tippen Sie auf **Ja**, um zu bestätigen, dass das Gewinnererlebnis konvertiert werden soll. Dies führt zur Deaktivierung der aktuellen Aktivität, die durch die Inhalte des Gewinnererlebnisses ersetzt wird.

## Synchronisieren von Aktivitäten mit Adobe Target      {#synchronizing-activities-with-adobe-target}

Aktivitäten, deren Targeting-Engine Adobe Target ist, werden mit Adobe Target-Kampagnen synchronisiert. Eine Aktivität wird automatisch mit Adobe Target synchronisiert, wenn folgende Bedingungen erfüllt sind:

* Die Aktivität weist mindestens ein Erlebnis auf.
* Mindestens ein Erlebnis enthält ein ihm zugewiesenes Segment und ein Angebot.
* Jedes Erlebnis der Aktivität muss die gleiche Anzahl Angebote enthalten.

Diese Bedingungen gelten für Aktivitäten in den Autoren- und Veröffentlichungsinstanzen.

Bei der Synchronisierung einer Aktivität wird in Adobe Target eine entsprechende Kampagne erstellt:

* Aktivitäten in der Veröffentlichungsinstanz tragen den gleichen Namen wie die entsprechende Adobe Target-Kampagne.
* Aktivitäten in der Autoreninstanz entsprechen Target-Kampagnen mit dem gleichen Namen sowie dem Nachsatz `_author`.

![Synchronisierung mit Adobe Target](/help/sites-cloud/authoring/assets/activities-synch.png)

Die Autorenaktivitäten werden unmittelbar bei Bearbeitung der Aktivität synchronisiert. Diese sofortige Synchronisierung ermöglicht eine Simulation der Aktivitäten mit ContextHub.

Veröffentlichte Aktivitäten werden zum Zeitpunkt ihrer Veröffentlichung mit der AEM-Veröffentlichungsinstanz synchronisiert.

## Fehlerbehebung bei der Aktivitätssynchronisierung      {#troubleshooting-activity-synchronization}

Bei der Synchronisierung von Aktivitäten mit Adobe Target durch AEM fügt AEM eine Eigenschaft mit der Bezeichnung `thirdPartyId` hinzu. Der Wert dieser Eigenschaft basiert auf dem Aktivitätenpfad im AEM-Verzeichnis. In Adobe Target dürfen unterschiedliche Kampagnen für `thirdPartyId` keinesfalls denselben Wert aufweisen. Somit schlägt die Synchronisierung von Aktivitäten fehl, wenn eine bestehende Kampagne (mit einem anderen Aktivitätstyp A/B, XT) in Adobe Target über denselben Wert für `thirdPartyId` verfügt.

Dies kann unter folgenden Umständen auftreten:

1. Eine Aktivität wird erstellt und mit Adobe Target synchronisiert.
1. Auf einer anderen AEM-Instanz wird für die gleiche Marke und unter dem gleichen Namen eine weitere Aktivität erstellt. Wird versucht, diese Aktivität zu synchronisieren, schlägt der Vorgang fehl.

Dies kann zudem auch unter den folgenden Umständen auftreten:

1. Eine Aktivität wird erstellt und mit Adobe Target synchronisiert. Die Aktivität wird anschließend aus AEM gelöscht.
1. Eine Aktivität wird in der gleichen Marke erstellt und erhält den gleichen Namen wie die gelöschte Aktivität. Wird versucht, diese Aktivität zu synchronisieren, schlägt der Vorgang fehl.

Um Synchronisierungsprobleme zu vermeiden, verwenden Sie stets eindeutige Namen für Aktivitäten. Wenn sich eine Aktivität nicht synchronisieren lässt, können Sie die Kampagne in Adobe Target löschen, die denselben Namen aufweist, sofern diese Kampagne nicht verwendet wird.

>[!NOTE]
>
>Wenn Sie eine Kampagne in Adobe Target erstellen, wird jeder Kampagne eine Eigenschaft mit dem Namen `thirdPartyId` hinzugefügt. Wenn Sie die Kampagne in Adobe Target löschen, wird `thirdPartyId` nicht gelöscht. Die `thirdPartyId` kann nicht für Kampagnen unterschiedlicher Typen (A/B, XT) wiederverwendet werden und lässt sich nicht manuell löschen. Möchten Sie dieses Problem umgehen, geben Sie jeder Kampagne einen eindeutigen Namen. Kampagnennamen lassen sich somit nicht für verschiedene Kampagnentypen wiederverwenden.
>
>Wenn Sie denselben Namen im selben Kampagnentyp verwenden, wird die vorhandene Kampagne überschrieben.
>
>Sollte Ihnen beim Synchronisieren die Fehlermeldung „Anforderung fehlgeschlagen. `thirdPartyId` ist bereits vorhanden“ angezeigt werden, ändern Sie den Kampagnennamen und synchronisieren Sie erneut.
