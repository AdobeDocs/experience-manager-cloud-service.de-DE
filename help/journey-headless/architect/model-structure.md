---
title: Erfahren Sie mehr über das Erstellen von Inhaltsfragmentmodellen in AEM
description: Erfahren Sie mehr über die Konzepte und Methoden der Modellierung von Inhalten für Ihr Headless-CMS mithilfe von Inhaltsfragmentmodellen.
index: true
hide: false
hidefromtoc: false
exl-id: fdfa79d3-fbed-4467-a898-c1b2678fc0cb
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 16%

---

# Erfahren Sie mehr über das Erstellen von Inhaltsfragmentmodellen in AEM {#architect-headless-content-fragment-models}

## Die Geschichte so weit {#story-so-far}

Zu Beginn der [AEM Headless Content Author-Journey](overview.md) deckten die [Grundlagen zur Inhaltsmodellierung für Headless mit AEM](basics.md) die grundlegenden Konzepte und Terminologie ab, die für das Headless-Authoring relevant sind.

Dieser Artikel baut auf diesen auf, damit Sie verstehen, wie Sie Ihre eigenen Inhaltsfragmentmodelle für Ihr AEM Headless-Projekt erstellen.

## Ziele {#objective}

* **Zielgruppe**: Anfänger
* **Zielsetzung**: Konzepte und Methoden zur Modellierung von Inhalten für Ihr Headless-CMS mithilfe von Inhaltsfragmentmodellen.

<!-- which persona does this? -->
<!-- and who allows the configuration on the folders? -->

<!--
## Enabling Content Fragment Models {#enabling-content-fragment-models}

At the very start you need to enable Content Fragment Models for your site, this is done in the Configuration Browser; under Tools -> General -> Configuration Browser. You can either select to configure the global entry, or create a new configuration. For example:

![Define configuration](/help/assets/content-fragments/assets/cfm-conf-01.png)

>[!NOTE]
>
>See Additional Resources - Content Fragments in the Configuration Browser
-->

## Erstellen von Inhaltsfragmentmodellen {#creating-content-fragment-models}

Anschließend können die Inhaltsfragmentmodelle erstellt und die Struktur definiert werden. Dies kann unter „Tools“ > „Assets“ > „Inhaltsfragmentmodelle“ erfolgen.

![Inhaltsfragmentmodelle in Tools](assets/cfm-tools.png)

Nachdem Sie diese Option ausgewählt haben, navigieren Sie zum Speicherort für Ihr Modell und wählen Sie **Erstellen** aus. Hier können Sie verschiedene Schlüsseldetails eingeben.

Die Option **Modell aktivieren** ist standardmäßig aktiviert. Das bedeutet, dass Ihr Modell zur Verwendung verfügbar ist (beim Erstellen von Inhaltsfragmenten), sobald Sie es gespeichert haben. Sie können dies bei Bedarf deaktivieren - es gibt später Möglichkeiten, ein vorhandenes Modell zu aktivieren (oder zu deaktivieren).

![Inhaltsfragmentmodell erstellen](/help/assets/content-fragments/assets/cfm-models-02.png)

Bestätigen Sie mit **Erstellen** und Sie können **Öffnen Sie** Ihr Modell, um die Struktur zu definieren.

## Definieren von Inhaltsfragmentmodellen {#defining-content-fragment-models}

Wenn Sie ein neues Modell zum ersten Mal öffnen, sehen Sie - einen großen leeren Bereich links und eine lange Liste von **Datentypen** rechts:

![Leeres Modell](/help/assets/content-fragments/assets/cfm-models-03.png)

Was ist also zu tun?

Sie können Instanzen von **Datentypen** auf den linken Bereich ziehen - Sie definieren Ihr Modell bereits!

![Felder definieren](/help/assets/content-fragments/assets/cfm-models-04.png)

Nachdem Sie einen Datentyp hinzugefügt haben, müssen Sie die **Eigenschaften** für dieses Feld definieren. Diese hängen vom verwendeten Typ ab. Zum Beispiel:

![Dateneigenschaften](/help/assets/content-fragments/assets/cfm-models-05.png)

Sie können beliebig viele Felder hinzufügen. Beispiel:

![Inhaltsfragmentmodell](/help/assets/content-fragments/assets/cfm-models-07.png)

### Ihre Inhaltsautoren {#your-content-authors}

Ihre Inhaltsautoren sehen nicht die tatsächlichen Datentypen und -eigenschaften, die Sie zum Erstellen Ihrer Modelle verwendet haben. Dies bedeutet, dass Sie möglicherweise Hilfe und Informationen dazu bereitstellen müssen, wie bestimmte Felder ausgefüllt werden. Für grundlegende Informationen können Sie die Feldbeschriftung und den Standardwert verwenden. Komplexere Fälle können jedoch bedacht werden, um eine projektspezifische Dokumentation zu erhalten.

>[!NOTE]
>
>Siehe „Zusätzliche Ressourcen – Inhaltsfragmentmodelle“.

## Verwalten von Inhaltsfragmentmodellen {#managing-content-fragment-models}

<!-- needs more details -->

Die Verwaltung Ihrer Inhaltsfragmentmodelle umfasst Folgendes:

* Aktivieren (oder Deaktivieren) dieser Funktionen - Dadurch werden sie für Autoren beim Erstellen von Inhaltsfragmenten verfügbar.
* Löschen - Das Löschen ist immer erforderlich, Sie müssen jedoch wissen, dass Sie ein Modell löschen, das bereits für Inhaltsfragmente verwendet wird, insbesondere für bereits veröffentlichte Fragmente.

## Veröffentlichung {#publishing}

<!-- needs more details -->

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

>[!NOTE]
>
>Wenn ein Autor versucht, ein Inhaltsfragment zu veröffentlichen, für das das Modell noch nicht veröffentlicht wurde, wird dies in einer Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

Sobald ein Modell veröffentlicht wird, ist es *locked* in einem schreibgeschützten Modus auf der Autoreninstanz. Dadurch soll verhindert werden, dass Änderungen zu Fehlern an vorhandenen GraphQL-Schemas und -Abfragen führen, insbesondere in der Veröffentlichungsumgebung. Dies wird in der Konsole durch **Gesperrt** angezeigt.

Wenn das Modell **Gesperrt** ist (im schreibgeschützten Modus), können Sie den Inhalt und die Struktur der Modelle anzeigen, sie jedoch nicht direkt bearbeiten. Sie können die **gesperrten**-Modelle entweder über die Konsole oder den Modell-Editor verwalten.

## Wie geht es weiter {#whats-next}

Nachdem Sie die Grundlagen gelernt haben, besteht der nächste Schritt darin, Ihre eigenen Inhaltsfragmentmodelle zu erstellen.

## Zusätzliche Ressourcen {#additional-resources}

* [Authoring – Konzepte](/help/sites-cloud/authoring/getting-started/concepts.md)

* [Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md)  - Diese Seite basiert in erster Linie auf der  **** Sites-Konsole. Viele/die meisten Funktionen sind jedoch auch für die Navigation zu  **Inhaltsfragmentmodellen und deren Bearbeitung** unter der  **** Asset-Konsole relevant.

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

      * [Definieren des Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#defining-your-content-fragment-model)

      * [Aktivieren oder Deaktivieren von Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md#enabling-disabling-a-content-fragment-model)

      * [Zulassen von Inhaltsfragmentmodellen im Asset-Ordner](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

      * [Löschen eines Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#deleting-a-content-fragment-model)

      * [Veröffentlichen eines Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model)

      * [Rückgängigmachen der Veröffentlichung eines Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#unpublishing-a-content-fragment-model)

      * [Gesperrte (veröffentlichte) Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md#locked-published-content-fragment-models)

* Anleitungen für den Einstieg

   * [Schnellstartanleitung zum Erstellen von Inhaltsfragmentmodellen per Headless-Implementierung](/help/implementing/developing/headless/getting-started/create-content-model.md)
