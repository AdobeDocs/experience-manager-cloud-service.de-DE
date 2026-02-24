---
title: Verwalten von Aktivitäten
description: Mithilfe der Aktivitätskonsole können Sie die Marketing-Aktivitäten Ihrer Marken erstellen, organisieren und verwalten
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: e7cab16d-7678-472d-b75f-7f67b303ba8d
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '1964'
ht-degree: 99%

---

# Verwalten von Aktivitäten {#managing-activities}

Mithilfe der Aktivitätskonsole können Sie die [Marketing-Aktivitäten](/help/sites-cloud/authoring/personalization/overview.md#activities) Ihrer Marken erstellen, organisieren und verwalten:

* Fügen Sie Marken hinzu.
* Fügen Sie jeder Marke Aktivitäten hinzu und konfigurieren Sie diese.
* Verwalten Sie Aktivitäten.

>[!TIP]
>
>Wenn Sie Adobe Target als Zielgruppenbestimmungs-Engine verwenden, können Sie auch [Leistungsdaten Ihrer Aktivitäten anzeigen](#viewing-performance-and-converting-winning-experiences-a-b-test). Wenn Sie A/B-Tests verwenden, können Sie [Gewinner konvertieren](#viewing-performance-and-converting-winning-experiences-a-b-test).

In der Aktivitätskonsole sind die Aktivitäten nach Marken organisiert. Sie können Marken und Ordner verwenden, um die Organisation Ihrer Aktivitäten zu strukturieren. Sie können zur Aktivitätskonsole navigieren, indem Sie auf **Personalisierung** und auf **Aktivitäten** tippen/klicken.

Aktivitäten stehen im Targeting-Modus für das [Verfassen zielgerichteter Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) zur Verfügung, wobei Sie in diesem Modus auch Aktivitäten erstellen können. Aktivitäten, die Sie im Targeting-Modus erstellen, werden in der Aktivitätskonsole angezeigt.

Aktivitäten werden mit einem Titel angezeigt, der beschreibt, welche Art von Aktivität definiert ist:

* XT – Experience Targeting mit Adobe Target
* A/B – A/B-Tests mit Adobe Target
* AEM – Adobe Experience Manager-Targeting (d. h. ContextHub-gesteuert)

![Aktivitätstypen](/help/sites-cloud/authoring/assets/activities-types.png)

>[!NOTE]
>
>Welche Aktivitätstypen zur Verfügung stehen, hängt von folgenden Faktoren ab:
>
>* Bei Aktivierung der Option `xt_only` im Adobe Target-Mandanten (Client-Code), der auf AEM-Seite für die Verbindung zu Adobe Target verwendet wird, können Sie in AEM ausschließlich **XT-Aktivitäten** erstellen.
>
>* Ist die Option `xt_only` im Adobe Target-Mandanten (Client-Code) **nicht** aktiviert, können Sie in AEM **sowohl** XT- als auch A/B-Aktivitäten erstellen.
>
>**Zusätzlicher Hinweis:** Bei der Option `xt_only` handelt es sich um eine Einstellung, die auf einen bestimmten Target-Mandanten (Clientcode) angewendet wird und nur in Adobe Target bearbeitet werden kann. Die Option kann in AEM nicht aktiviert oder deaktiviert werden.

>[!CAUTION]
>
>Sie müssen den Aktivitätseinstellungsknoten `cq:ActivitySettings` in der Veröffentlichungsinstanz sichern, sodass dieser für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Service zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.
>
>Detaillierte Informationen finden Sie unter „Voraussetzungen für die Integration mit Adobe Target“.
<!--
>See [Prerequisites for Integrating with Adobe Target](/help/sites-administering/target-requirements.md#securingtheactivitysettings) for detailed information.
-->

## Erstellen von Marken mithilfe der Aktivitätskonsole {#creating-a-brand-using-the-activities-console}

Erstellen Sie eine Marke, deren Marketing-Aktivitäten Sie verwalten möchten.

Wenn Sie mithilfe der Aktivitätskonsole eine Marke erstellen, erscheint diese ebenfalls in der [Angebotskonsole](/help/sites-cloud/authoring/personalization/offers.md), in der Sie Angebote für die Erlebnisse Ihrer Aktivitäten erstellen können.

1. Wählen Sie in der Navigationskonsole **Personalisierung** aus. Wählen Sie **Aktivitäten** aus.

   ![Navigieren zu Aktivitäten](/help/sites-cloud/authoring/assets/activities-navigation.png)

1. Wählen Sie in der Aktivitätskonsole **Erstellen** und dann **Marke erstellen** aus.
1. Wählen Sie die Markenvorlage und dann **Weiter** aus.
1. Geben Sie einen Titel für die Marke ein, wie er in Aktivitäts- und Angebots-Konsole angezeigt werden soll. Optional können Sie eins oder mehrere Tags eingeben oder auswählen, die mit der Marke verknüpft werden sollen.
1. Wählen Sie **Erstellen** aus. Ihre Marke wird in der Aktivitätskonsole angezeigt.

## Hinzufügen/Bearbeiten von Aktivitäten mithilfe der Aktivitätskonsole {#adding-editing-an-activity-using-the-activities-console}

Fügen Sie eine Aktivität hinzu oder bearbeiten Sie eine vorhandene Aktivität, um Ihre Marketing-Maßnahmen auf bestimmte Zielgruppen zu konzentrieren. Beim Erstellen/Bearbeiten einer Aktivität geben Sie die folgenden Informationen an:

* **Name:** Der Name der Aktivität.
* **Targeting-Engine:** Entweder [AEM](/help/sites-cloud/authoring/personalization/overview.md#aem) oder [Adobe Target](/help/sites-cloud/authoring/personalization/overview.md#adobe-target) als Engine für zielgerichtete Inhalte.
* **Auswählen einer Target-Konfiguration:** (Nur Adobe Target) Die Cloud-Konfiguration, mit der diese Aktivität eine Verbindung zu Adobe Target herstellen soll. Diese Option wird nur angezeigt, wenn Adobe Target für die Targeting-Engine ausgewählt wurde.
* **Aktivitätstyp**: der Aktivitätstyp – A/B-Test oder Erlebnis-Targeting.
* **Ziele:** (Optional) Eine Beschreibung der Aktivität.
* **Erlebnisse:** Zuordnungen zwischen Zielgruppennamen und den Marketingsegmenten, die Sie als Ziel auswählen.
* **Traffic-Anteile**: wurde A/B-Test ausgewählt, können Sie festlegen, welcher Anteil des Traffics (in Prozent) an die verschiedenen Erlebnisse weitergeleitet wird.
* **Dauer:** Der Zeitraum, in dem die Aktivität angewendet wird.
* **Priorität:** Die relative Priorität der Aktivität. Wenn Aktivitäten Inhalte für dieselben Benutzersegmente bereitstellen, hat die Aktivität mit höherer Priorität Vorrang.
* **Zielmetrik**: wurde Adobe Target als Targeting-Engine ausgewählt, können Sie der Aktivität Erfolgsmetriken hinzufügen. Eine Erfolgsmetrik ist erforderlich.

>[!NOTE]
>
>Um eine **Zielkonfiguration auswählen** zu können, müssen Sie sich in der **Autorenbenutzergruppe für Target-Aktivitäten** befinden.

>[!NOTE]
>
>Neue Adobe Target-Aktivitäten müssen im Editor für zielgerichtete Inhalte *erstellt* werden, nicht in der Konsole **Aktivitäten**, da die Synchronisierung mit Adobe Target fehlschlägt.
>
>Sie können jedoch vorhandene Adobe Target-Aktivitäten in der Konsole bearbeiten.

So fügen Sie eine Aktivität hinzu:

1. Wählen Sie die Marke aus, für die Sie eine Aktivität erstellen möchten, und wählen Sie dann **Erstellen** und anschließend **Aktivität erstellen** aus. Wenn Sie eine Aktivität bearbeiten möchten, wählen Sie sie im Bildschirm „Primäres Gebiet“ aus und klicken oder tippen Sie auf **Aktivität bearbeiten**.
1. Geben Sie die folgenden Informationen ein und wählen Sie dann **Weiter** aus:
   * Ein Name für die Aktivität.
   * Die zu verwendende Zielgruppenbestimmungs-Engine. ContextHub (AEM) ist standardmäßig ausgewählt. Wenn Sie Adobe Target verwenden müssen, erstellen Sie die Aktivität im entsprechenden Inhaltseditor.
   * Wenn Sie Adobe Target als Zielgruppenbestimmungs-Engine ausgewählt haben, wählen/bearbeiten Sie die Cloud-Konfiguration, die für die Verbindung mit Adobe Target verwendet werden soll. (Achten Sie darauf, dass Sie kein Framework auswählen, das Sie für Ihre Cloud-Konfiguration erstellt haben.)
   * (Optional) Das Ziel oder eine Beschreibung der Aktivität.
   * Wählen Sie den Aktivitätstyp aus.
1. Fügen Sie der Aktivität mindestens ein Erlebnis hinzu. Wählen Sie **Erlebnis hinzufügen** aus.
1. Wenn Sie AEM-Targeting oder Experience Targeting in Adobe Target verwenden:
   1. Wählen Sie **Zielgruppe wählen** und das Segment aus, auf das Ihr Erlebnis abgestimmt ist.
   1. Wählen Sie **Erlebnis hinzufügen** aus, geben Sie einen Namen ein und wählen Sie **OK** aus.
   1. Wählen Sie **Weiter** aus.
Wenn Sie A/B-Tests in Adobe Target verwenden:
   1. Wählen Sie das Stiftsymbol im Feld für die Zielgruppe aus, um eine Zielgruppe auszuwählen.
   1. Wählen Sie **Erlebnis hinzufügen** aus, geben Sie einen Namen ein und wählen Sie **OK** aus.
   1. Geben Sie den prozentualen Anteil des Traffics ein, der auf die jeweiligen Erlebnisse umgelenkt werden soll.
   1. Wählen Sie **Weiter** aus.
1. Um den Beginn der Aktivität festzulegen, wählen Sie im Dropdown-Menü **Start** einen der folgenden Werte:
   * **Wenn aktiviert**: Beginnt die Aktivität, wenn die Seite, die den zielgerichteten Inhalt enthält, aktiviert wird.
   * **Angegebenes Datum und Uhrzeit**: Ein bestimmter Zeitpunkt. Wenn Sie diese Option auswählen, wählen Sie das Kalendersymbol, wählen Sie ein Datum aus und geben Sie die Zeit an, zu der die Aktivität gestartet werden soll.
1. Verwenden Sie das Dropdown-Menü „Ende“, um festzulegen, wann die Aktivität beendet werden soll. Wählen Sie einen der folgenden Werte aus:
   * **Wenn deaktiviert**: Beendet die Aktivität, wenn die Seite, die den zielgerichteten Inhalt enthält, deaktiviert wird.
   * **Angegebenes Datum und Uhrzeit:** Ein bestimmter Zeitpunkt. Wenn Sie diese Option wählen, wählen Sie das Kalendersymbol, wählen Sie ein Datum und geben Sie die Zeit für das Ende der Aktivität an.
1. Um eine Priorität für die Aktivität festzulegen, wählen Sie mit dem Schieberegler entweder **Niedrig**, **Normal** oder **Hoch**.
1. Wenn Sie Adobe Target als Targeting-Engine verwenden, wählen Sie aus, was mit dieser Aktivität gemessen werden soll. Weitere Informationen zu verfügbaren Erfolgsmetriken finden Sie unter [Konfigurieren der Aktivität und Festlegen von Zielen](/help/sites-cloud/authoring/personalization/targeted-content.md). Wählen Sie mindestens ein Ziel aus.
1. Wählen Sie **Speichern** aus.

   >[!NOTE]
   >
   >Nach der Erstellung einer Aktivität müssen Sie sie veröffentlichen, damit sie verfügbar ist.

## Veröffentlichen von Aktivitäten und Aufheben der Veröffentlichung von Aktivitäten {#publishing-and-unpublishing-activities}

Sie müssen Aktivitäten veröffentlichen, um sie verfügbar zu machen. Auf der anderen Seite möchten Sie die Verfügbarkeit von Aktivitäten möglicherweise verhindern, was durch das Aufheben einer Veröffentlichung erzielt wird.

>[!NOTE]
>
>Wenn Sie das Veröffentlichen einer Aktivität aufheben, ändert sich der Status der Aktivität nicht, es sei denn, Sie aktualisieren die Seite.

So veröffentlichen Sie Aktivitäten oder heben deren Veröffentlichung auf:

1. Wählen Sie die Marke und anschließend das Gebiet aus, das die Aktivität enthält, die veröffentlicht bzw. deren Veröffentlichung aufgehoben werden soll.
1. Wählen Sie das Symbol neben jeder Aktivität aus, die veröffentlicht bzw. deren Veröffentlichung aufgehoben werden soll.

   ![Veröffentlichen über die Aktivitätskonsole](/help/sites-cloud/authoring/assets/activities-console.png)

1. Wählen Sie zum Veröffentlichen die Option **Veröffentlichen** aus. Wählen Sie zum Aufheben der Veröffentlichung die Option **Veröffentlichung aufheben** aus. Ihre Aktivitäten werden veröffentlicht bzw. ihre Veröffentlichung wird rückgängig gemacht, und ihr Status ändert sich in der Aktivitätskonsole (möglicherweise ist eine Aktualisierung erforderlich).

## Aktivitäten in der Autoren- und Veröffentlichungsinstanz {#activities-on-author-and-publish-instances}

Wenn eine Aktivität aktiviert wird, die die Zielgruppenbestimmungs-Engine von Adobe Target verwendet, wird eine zweite Aktivität in der Veröffentlichungsinstanz erstellt:

* Mit der Aktivität in der Autoreninstanz wird die Aktivität in der Autoreninstanz verfolgt, was sich für die Simulation des Besuchererlebnisses oft als sehr nützlich erweist. Die für diese Aktivität aufgezeichneten Analysen spiegeln nur die Ereignisse in der Autoreninstanz wider.
* Die Aktivität auf der Veröffentlichungsinstanz spiegelt die Aktivität auf dem Veröffentlichungs-Server wider und reagiert auf diese. Dies ist die Aktivität, die auf der öffentlichen Website ausgeführt wird. Nur die Veröffentlichungsaktivität ist für das Tracking und die Analyse der Nutzung der tatsächlichen öffentlichen Site relevant.

## Anzeigen der Performance und Konvertieren von Gewinnererlebnissen (A/B-Tests) {#viewing-performance-and-converting-winning-experiences-a-b-test}

Sie können die Leistung jeder beliebigen Adobe Target-Aktivität (XT oder A/B) anzeigen. Wenn Sie A/B-Tests verwenden, können Sie das erfolgreichste Erlebnis auch konvertieren, sodass es zum Standarderlebnis wird.

So prüfen Sie die Leistung und konvertieren Gewinnererlebnisse:

1. Wählen Sie unter **Personalisierung** die Option **Aktivitäten** aus, um zur **Aktivitätskonsole** zu navigieren.
1. Wählen Sie die Marke aus, deren Aktivitäten Sie anzeigen möchten.
1. Wählen Sie die Aktivität und die Option **Eigenschaften anzeigen** aus, klicken Sie auf die Registerkarte **Berichte** und wählen Sie die Aktivität aus, deren Leistung Sie anzeigen/deren Gewinnererlebnisse Sie konvertieren möchten. Die Leistungsdaten werden nun angezeigt.

   ![Überprüfen der Aktivitätsleistung](/help/sites-cloud/authoring/assets/activities-performance.png)

1. Wählen Sie den Link **Gewinner pushen** aus, um das Erlebnis als Standarderlebnis festzulegen.

   Durch die Konvertierung des Gewinners geschieht Folgendes:

   * Die aktuelle Aktivität wird deaktiviert.
   * Es werden alle Seiten modifiziert und zielgerichtete Inhalte durch die Inhalte des Gewinnererlebnisses ersetzt. Der Inhalt des Gewinnererlebnisses wird Teil der normalen Seite **ohne** Targeting.

   ![Konvertieren des Gewinners](/help/sites-cloud/authoring/assets/activities-reports.png)

   Ein erfolgreichstes Erlebnis ist das Erlebnis, das in den Berichten die höchste Steigerung generiert, welche auf der Konversionsrate basiert.

1. Wählen Sie **Ja** aus, um zu bestätigen, dass das Gewinnererlebnis konvertiert werden soll. Dies führt zur Deaktivierung der aktuellen Aktivität, die durch die Inhalte des Gewinnererlebnisses ersetzt wird.

## Synchronisieren von Aktivitäten mit Adobe Target {#synchronizing-activities-with-adobe-target}

Aktivitäten, die die Zielgruppenbestimmungs-Engine von Adobe Target verwenden, werden mit Adobe Target-Kampagnen synchronisiert. Eine Aktivität wird automatisch mit Adobe Target synchronisiert, wenn die folgenden Bedingungen erfüllt sind:

* Die Aktivität enthält mindestens ein Erlebnis.
* Mindestens ein Erlebnis enthält ein zugeordnetes Segment und ein Angebot.
* Jedes Erlebnis in der Aktivität muss über dieselbe Anzahl von Angeboten verfügen.

Diese Bedingungen gelten für Aktivitäten in Autoren- und Veröffentlichungsinstanzen.

Wenn eine Aktivität synchronisiert wird, wird eine entsprechende Kampagne in Adobe Target erstellt:

* Aktivitäten in der Veröffentlichungsinstanz haben denselben Namen wie die entsprechende Adobe Target-Kampagne.
* Aktivitäten in der Autoreninstanz entsprechen Target-Kampagnen mit dem gleichen Namen sowie dem Nachsatz `_author`.

![Synchronisierung mit Adobe Target](/help/sites-cloud/authoring/assets/activities-synch.png)

Die Autorenaktivitäten werden unmittelbar bei Bearbeitung der Aktivität synchronisiert. Diese sofortige Synchronisierung ermöglicht eine Simulation der Aktivitäten mit ContextHub.

Veröffentlichte Aktivitäten werden zum Zeitpunkt ihrer Veröffentlichung mit der AEM-Veröffentlichungsinstanz synchronisiert.

## Fehlerbehebung bei der Aktivitätssynchronisierung {#troubleshooting-activity-synchronization}

Bei der Synchronisierung von Aktivitäten mit Adobe Target durch AEM fügt AEM eine Eigenschaft mit der Bezeichnung `thirdPartyId` hinzu. Der Wert dieser Eigenschaft basiert auf dem Aktivitätenpfad im AEM-Verzeichnis. In Adobe Target dürfen unterschiedliche Kampagnen für `thirdPartyId` keinesfalls denselben Wert aufweisen. Somit schlägt die Synchronisierung von Aktivitäten fehl, wenn eine bestehende Kampagne (mit einem anderen Aktivitätstyp A/B, XT) in Adobe Target über denselben Wert für `thirdPartyId` verfügt.

Diese Situation kann unter folgenden Umständen eintreten:

1. Eine Aktivität wird erstellt und mit Adobe Target synchronisiert.
1. Auf einer anderen AEM-Instanz wird eine Aktivität unter derselben Marke und unter Verwendung desselben Namens erstellt. Die versuchte Synchronisierung dieser Aktivität schlägt fehl.

Diese Situation kann auch unter folgenden Umständen eintreten:

1. Eine Aktivität wird erstellt und mit Adobe Target synchronisiert. Die Aktivität wird anschließend aus AEM gelöscht.
1. Eine Aktivität wird unter derselben Marke und unter Verwendung des gleichen Namens wie die gelöschte Aktivität erstellt. Die versuchte Synchronisierung dieser Aktivität schlägt fehl.

Um Synchronisierungsprobleme zu vermeiden, verwenden Sie stets eindeutige Namen für Aktivitäten. Wenn sich eine Aktivität nicht synchronisieren lässt, können Sie die Kampagne in Adobe Target löschen, die denselben Namen aufweist, sofern diese Kampagne nicht verwendet wird.

>[!NOTE]
>
>Wenn Sie eine Kampagne in Adobe Target erstellen, wird jeder Kampagne eine Eigenschaft mit dem Namen `thirdPartyId` hinzugefügt. Wenn Sie die Kampagne in Adobe Target löschen, wird `thirdPartyId` nicht gelöscht. Die `thirdPartyId` kann nicht für Kampagnen unterschiedlicher Typen (A/B, XT) wiederverwendet werden und lässt sich nicht manuell löschen. Möchten Sie dieses Problem umgehen, geben Sie jeder Kampagne einen eindeutigen Namen. Kampagnennamen lassen sich nicht für verschiedene Kampagnentypen wiederverwenden.
>
>Wenn Sie denselben Namen im selben Kampagnentyp verwenden, wird die vorhandene Kampagne überschrieben.
>
>Sollte Ihnen beim Synchronisieren die Fehlermeldung „Anforderung fehlgeschlagen. `thirdPartyId` ist bereits vorhanden“ angezeigt werden, ändern Sie den Kampagnennamen und synchronisieren Sie erneut.
