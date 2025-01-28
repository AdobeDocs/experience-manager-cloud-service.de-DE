---
title: Wie können wir die Leistung umfangreicher Formulare durch verzögertes Laden verbessern?
description: Erfahren Sie, wie Sie die Leistung umfangreicher Formulare durch verzögertes Laden verbessern können. Verzögertes Laden (Lazy Loading) verbessert die Performance von umfangreichen und komplexen adaptiven Formularen erheblich, indem Formularfragmente erst dann initialisiert und geladen werden, wenn sie sichtbar werden.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 0cd38edb-2201-4ca6-8b84-6b5b7f76bd90
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 96%

---

# Verbessern der Leistung umfangreicher Formulare durch verzögertes Laden {#improve-performance-of-large-forms-with-lazy-loading}

>[!NOTE]
>
> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zum [Erstellen eines neuen adaptiven Forms](/help/forms/creating-adaptive-form-core-components.md) oder [Hinzufügen von adaptivem Forms zu AEM Sites-Seiten](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Forms mithilfe von Foundation-Komponenten beschrieben.

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/lazy-loading-adaptive-forms.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |


## Einführung in das verzögerte Laden {#introduction-to-lazy-loading}

Wenn Formulare infolge von Hunderten oder Tausenden von Feldern groß und komplex werden, bemerken die Endbenutzer während des Renderns von Formularen zur Laufzeit lange Reaktionszeiten. Um die Reaktionszeiten zu minimieren, können Sie adaptive Formulare in logische Fragmente unterteilen und so konfigurieren, dass die Initialisierung oder das Laden von Fragmenten aufgeschoben wird, bis das jeweilige Fragment sichtbar werden muss. Dies wird als „verzögertes Laden“ bezeichnet. Darüber hinaus werden die für verzögertes Laden konfigurierten Fragmente entladen, sobald der Benutzer zu anderen Abschnitten im Formular navigiert und die Fragmente nicht mehr sichtbar sind.

Im Folgenden werden zunächst die Anforderungen und vorbereitenden Schritte vor dem Konfigurieren des verzögerten Ladens erklärt.

## Vorbereiten der Konfiguration von verzögertem Laden {#preparing-to-configure-lazy-loading}

Bevor Sie das verzögerte Laden von Fragmenten in Ihrem adaptiven Formular konfigurieren, müssen Sie Strategien für das Erstellen von Fragmenten entwickeln, Werte, die in den Skripten verwendet oder in anderen Fragmenten referenziert werden, identifizieren und Regeln, die die Sichtbarkeit von Feldern in verzögert geladenen Fragmenten steuern, definieren.

* **Identifizieren und Erstellen von Fragmenten**
Sie können nur adaptive Formularfragmente für das verzögerte Laden konfigurieren. Ein Fragment ist ein unabhängiges Segment, das sich außerhalb eines adaptiven Formulars befindet und in mehreren Formularen wiederverwendet werden kann. Somit besteht der erste Schritt beim Implementieren des verzögerten Ladens in der Bestimmung der logischen Abschnitte in einem Formular und deren Konvertierung in Fragmente. Sie können ein Fragment von Grund auf neu erstellen oder einen vorhandenen Formularbereich als Fragment speichern.

  <!--For more information about creating fragments, see [Adaptive Form Fragments](adaptive-form-fragments.md).-->

* **Identifizieren und Markieren globaler Werte**
Zu formularbasierten Transaktionen gehören dynamische Elemente, die relevante Daten von Benutzern erfassen und verarbeiten und dadurch das Ausfüllen des Formulars vereinfachen. Beispiel: Ihr Formular enthält Feld A in Fragment X, dessen Wert die Gültigkeit von Feld B in einem anderen Fragment bestimmt. Wenn in diesem Fall Fragment X für verzögertes Laden markiert ist, muss der Wert von Feld A verfügbar sein, um Feld B zu validieren, selbst wenn Fragment X nicht geladen wird. Um dies zu erreichen, können Sie Feld A als global markieren, wodurch sichergestellt wird, dass der zugehörige Wert für die Validierung von Feld B verfügbar ist, selbst wenn Fragment X noch nicht geladen ist.

  Weitere Informationen dazu, wie Sie einen Feldwert als „global“ kennzeichnen, finden Sie unter [Konfigurieren von verzögertem Laden](lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Erstellen von Regeln zur Steuerung der Sichtbarkeit von Feldern**
Formulare enthalten Felder und Abschnitte, die nicht für alle Benutzer und Bedingungen gelten. Menschen, die Formulare verfassen und entwickeln, verwenden Regeln für Sichtbarkeit oder Ein- und Ausblenden, um die Sichtbarkeit der Formulare anhand von Benutzereingaben zu steuern. Beispielsweise wird das Feld „Büroadresse“ nicht den Benutzenden angezeigt, die im Feld „Beschäftigungsstatus“ in einem Formular die Option „Arbeitslos“ auswählen. Weitere Informationen zum Erstellen von Regeln finden Sie unter [Verwenden des Regeleditors](rule-editor.md).

  Sie können Sichtbarkeitsregeln in verzögert geladenen Fragmenten so nutzen, dass bedingte Felder nur angezeigt werden, wenn sie benötigt werden. Markieren Sie außerdem das bedingte Feld als „global“, um im Ausdruck für die Sichtbarkeit des verzögert geladenen Fragments darauf zu verweisen.

## Konfigurieren von verzögertem Laden {#configuring-lazy-loading}

Führen Sie zum Aktivieren des verzögerten Ladens in einem adaptiven Formularfragment folgende Schritte durch:

1. Öffnen Sie im Bearbeitungsmodus das adaptive Formular, das das Fragment enthält, für das Sie verzögertes Laden aktivieren möchten.
1. Wählen Sie das adaptive Formularfragment und anschließend die Option ![Konfigurieren](assets/configure-icon.svg) aus.
1. Aktivieren Sie in der Seitenleiste die Option **[!UICONTROL Fragment verzögert laden]** und wählen Sie **Fertig** aus.

   ![Verzögertes Laden für das adaptive Formularfragment aktivieren](assets/lazy-loading-fragment.png)

   Das Fragment ist jetzt für verzögertes Laden aktiviert.

Sie können die Werte von Objekten im verzögert geladenen Fragment als global markieren, damit sie in Skripten verwendet werden können, wenn das übergeordnete Fragment nicht geladen wird. Gehen Sie folgendermaßen vor:

1. Öffnen Sie das adaptive Formularfragment im Bearbeitungsmodus.
1. Wählen Sie das Feld aus, dessen Wert Sie als global markieren möchten, und anschließend die Option ![Konfigurieren](assets/configure-icon.svg).
1. Aktivieren Sie in der Randleiste **[!UICONTROL Wert bei verzögertem Laden verwenden]**.

   ![Feld „Verzögertes Laden“ in der Randleiste](assets/enable-lazy-loading.png)

   Der Wert ist jetzt als „global“ markiert und ist für die Verwendung in Skripten verfügbar, selbst wenn das enthaltende Fragment entladen wird.

## Aspekte und empfohlene Vorgehensweisen beim Konfigurieren von verzögertem Laden {#considerations-and-best-practices-for-configuring-lazy-loading}

Einige der folgenden Einschränkungen, Empfehlungen und wichtigen Aspekte sind beim Arbeiten mit verzögertem Laden zu beachten:

* Bei umfangreichen Formularen empfiehlt Adobe, XSD-schemabasierte statt XFA-basierte adaptive Formulare für die Konfiguration von verzögertem Laden zu verwenden. Die Leistungsverbesserung aufgrund von verzögertem Laden ist in XFA-basierten adaptiven Formularen verhältnismäßig geringer als in XSD-basierten adaptiven Formularen.
* Konfigurieren Sie kein verzögertes Laden für Fragmente in einem adaptiven Formular, die das Layout **[!UICONTROL Responsive – alles auf einer Seite ohne Navigation]** für den Stammbereich verwenden. Aufgrund der Konfiguration des responsiven Layouts werden in einem adaptiven Formular alle Fragmente gleichzeitig geladen. Dies kann ebenfalls die Performance beeinträchtigen.
* Es wird empfohlen, verzögertes Laden nicht für Fragmente im ersten Bereich, der beim Laden des adaptiven Formulars angezeigt wird, zu konfigurieren.
* Verzögertes Laden wird für bis zu zwei Ebenen in der Fragmenthierarchie unterstützt.
* Vergewissern Sie sich, dass als „global“ markierte Felder im gesamten adaptiven Formular eindeutig sind.
* Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen. Beispielsweise können Sie je nach dem vom Benutzer angegebenen Familienstand das Fragment zum Ehepartner ein- oder ausblenden.
* In verzögert geladenen Fragmenten werden keine Komponenten für Dateianhänge und Geschäftsbedingungen unterstützt.

### Empfohlene Vorgehensweisen für das Entwerfen von Skripten von verzögertem Laden {#scripting-best-practices-for-configuring-lazy-loading}

Weiterhin sollten Sie Folgendes beim Entwickeln von Skripten für das verzögerte Laden beachten:

* Stellen Sie sicher, dass die initialisierten und berechneten Skripte, die in den Feldern des verzögert geladenen Fragments verwendet werden, idempotent sind. Idempotente Skripte sind diejenigen, die den gleichen Effekt auch nach mehreren Implementierungen haben.
* Verwenden Sie die global verfügbare Eigenschaft von Feldern, um den Wert von Feldern in einem Bereich für verzögertes Laden für alle anderen Bereiche eines Formulars verfügbar zu machen.
* Leiten Sie den Referenzwert eines Felds in einem verzögerten Bereich nicht weiter, unabhängig davon, ob das Feld global über Fragmente hinweg markiert ist oder nicht.
* Verwenden Sie die Funktion zum Zurücksetzen des Bedienfelds, um alle im Bedienfeld sichtbaren Elemente mithilfe des folgenden Ausdrucks für ein Klickereignis zurückzusetzen.\
  guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()


## Siehe auch {#see-also}

{{see-also}}