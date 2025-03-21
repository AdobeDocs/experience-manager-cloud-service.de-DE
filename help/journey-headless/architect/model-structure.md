---
title: Erfahren Sie mehr über das Erstellen von Inhaltsfragmentmodellen in AEM
description: Erfahren Sie mehr über die Konzepte und Methoden der Modellierung von Inhalten für Ihr Headless-CMS mithilfe von Inhaltsfragmentmodellen.
exl-id: fdfa79d3-fbed-4467-a898-c1b2678fc0cb
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 6306ad88b889197aff377dc0a72ea232cd76ff9c
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 75%

---

# Erfahren Sie mehr über das Erstellen von Inhaltsfragmentmodellen in AEM {#architect-headless-content-fragment-models}

## Die bisherige Entwicklung {#story-so-far}

Am Anfang der [AEM Headless-Inhaltsautoren-Tour](overview.md) wurden in den [Grundlagen der Inhaltsmodellierung für Headless mit AEM](basics.md) die grundlegenden Konzepte und die Terminologie behandelt, die für das Authoring für Headless relevant sind.

Dieser Artikel baut auf diesen Prinzipien auf, damit Sie verstehen, wie Sie Ihre eigenen Inhaltsfragmentmodelle für Ihr AEM Headless-Projekt erstellen.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Konzepte und Methoden zur Modellierung von Inhalten für Ihr Headless-CMS mithilfe von Inhaltsfragmentmodellen.

<!-- which persona does this? -->
<!-- and who allows the configuration on the folders? -->

<!--
## Enabling Content Fragment Models {#enabling-content-fragment-models}

At the very start you need to enable Content Fragment Models for your site, this is done in the Configuration Browser; under Tools > General > Configuration Browser. You can either select to configure the global entry, or create a configuration. For example:

![Define configuration](/help/sites-cloud/administering/content-fragments/assets/cfm-conf-01.png)

>[!NOTE]
>
>See Additional Resources - Content Fragments in the Configuration Browser
-->

## Erstellen von Inhaltsfragmentmodellen {#creating-content-fragment-models}

Anschließend können die Inhaltsfragmentmodelle erstellt und die Struktur definiert werden.

1. Wählen Sie in der Inhaltsfragmentkonsole das Bedienfeld für Inhaltsfragmentmodelle aus.

1. Navigieren Sie zu dem Ordner, der Ihrer Konfiguration bzw. Unterkonfiguration entspricht.

1. Verwenden **Erstellen** um das Dialogfeld **Neues Inhaltsfragmentmodell** zu öffnen.

   ![Titel und Beschreibung](/help/sites-cloud/administering/content-fragments/assets/cf-managing-content-fragment-models-create.png)

1. Vervollständigen Sie die Details

1. Verwenden Sie **Erstellen**, um das leere Modell zu speichern, oder **Erstellen und öffnen**.

<!--
Then the Content Fragments Models can be created and the structure defined. This can be done under **Tools** > **General** > **Content Fragment Models**. 

![Content Fragment Models in Tools](assets/cfm-tools.png)

After selecting this you navigate to the location for your model and select **Create**. Here you can enter various key details.

The option **Enable model** is activated by default. This means that your model is available for use (in creating Content Fragments) as soon as you have saved it. You can deactivate this if you want - there are opportunities later to enable (or disable) an existing model.

![Create Content Fragment Model](/help/sites-cloud/administering/content-fragments/assets/cfm-models-02.png)

Confirm with **Create** and you can then **Open** your model to start defining the structure.
-->

## Definieren von Inhaltsfragmentmodellen {#defining-content-fragment-models}

Wenn Sie ein neues Modell zum ersten Mal öffnen, sehen Sie einen großen leeren Bereich links und eine lange Liste von **Datentypen** rechts:

![Leeres Modell](/help/sites-cloud/administering/content-fragments/assets/cfm-models-03.png)

Was ist also zu tun?

Sie können Instanzen der **Datentypen** in den linken Bereich ziehen – Sie definieren bereits Ihr Modell!

![Felder definieren](/help/sites-cloud/administering/content-fragments/assets/cfm-models-04.png)

Nachdem Sie einen Datentyp hinzugefügt haben, müssen Sie die **Eigenschaften** für dieses Feld definieren. Diese Eigenschaften hängen vom verwendeten Typ ab. Zum Beispiel:

![Dateneigenschaften](/help/sites-cloud/administering/content-fragments/assets/cfm-models-05.png)

Sie können beliebig viele Felder hinzufügen. Zum Beispiel:

![Inhaltsfragmentmodell](/help/sites-cloud/administering/content-fragments/assets/cfm-models-07.png)

### Ihre Inhaltsautoren {#your-content-authors}

Ihre Inhaltsautorinnen und -autoren sehen nicht die tatsächlichen Datentypen und -eigenschaften, die Sie zum Erstellen Ihrer Modelle verwendet haben. Dies bedeutet, dass Sie möglicherweise Hilfe und Informationen dazu bereitstellen müssen, wie bestimmte Felder ausgefüllt werden. Für grundlegende Informationen können Sie die Feldbeschriftung und den Standardwert verwenden. In komplexeren Fällen sollte jedoch eine projektspezifische Dokumentation in Betracht gezogen werden.

>[!NOTE]
>
>Siehe „Zusätzliche Ressourcen – Inhaltsfragmentmodelle“.

## Verwalten von Inhaltsfragmentmodellen {#managing-content-fragment-models}

<!-- needs more details -->

Die Verwaltung Ihrer Inhaltsfragmentmodelle umfasst Folgendes:

* Aktivieren (oder Deaktivieren) der Modelle – Dadurch werden sie für Autoren beim Erstellen von Inhaltsfragmenten verfügbar.
* Löschen - Eine Löschung ist immer erforderlich, aber Sie müssen sich bewusst sein, ob Sie ein Modell löschen, das bereits für Inhaltsfragmente verwendet wird, insbesondere für Fragmente, die bereits veröffentlicht wurden.

## Veröffentlichung {#publishing}

<!-- needs more details -->

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

>[!NOTE]
>
>Wenn ein Autor versucht, ein Inhaltsfragment zu veröffentlichen, für das das Modell noch nicht veröffentlicht wurde, wird dies in einer Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

Sobald ein Modell veröffentlicht wird, wird es auf der Autoreninstanz in einen SCHREIBGESCHÜTZTEN Modus versetzt und *gesperrt*. Dadurch soll verhindert werden, dass Änderungen zu Fehlern an vorhandenen GraphQL-Schemata und -Abfragen führen, insbesondere in der Veröffentlichungsumgebung. Dies wird in der Konsole durch **Gesperrt** angezeigt.

Wenn das Modell **Gesperrt** ist (im schreibgeschützten Modus), können Sie den Inhalt und die Struktur der Modelle anzeigen, sie jedoch nicht direkt bearbeiten. Sie können **Gesperrte** Modelle aus der Konsole oder dem Modell-Editor heraus verwalten.

## Wie geht es weiter {#whats-next}

Nachdem Sie die Grundlagen gelernt haben, besteht der nächste Schritt darin, Ihre eigenen Inhaltsfragmentmodelle zu erstellen.

## Zusätzliche Ressourcen {#additional-resources}

* [Authoring – Konzepte](/help/sites-cloud/authoring/author-publish.md)

* [Grundlegende Handhabung](/help/sites-cloud/authoring/basic-handling.md) – diese Seite basiert hauptsächlich auf der **Sites**-Konsole, aber viele/die meisten Funktionen sind auch für die Navigation zu und die Ausführung von Aktionen mit **Inhaltsfragmentmodellen** auf der **Allgemein**-Konsole relevant.

* [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

   * [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)

      * [Definieren des Inhaltsfragmentmodells](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)

      * [Aktivieren oder Deaktivieren von Inhaltsfragmentmodellen](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#enabling-disabling-a-content-fragment-model)

      * [Zulassen von Inhaltsfragmentmodellen im Asset-Ordner](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#allowing-content-fragment-models-assets-folder)

      * [Löschen eines Inhaltsfragmentmodells](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#deleting-a-content-fragment-model)

      * [Veröffentlichen eines Inhaltsfragmentmodells](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#publishing-a-content-fragment-model)

      * [Rückgängigmachen der Veröffentlichung eines Inhaltsfragmentmodells](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#unpublishing-a-content-fragment-model)

      * [Gesperrte Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#locked-content-fragment-models)

* Anleitungen für den Einstieg

   * [Erstellen einer Headless-Einrichtung für Inhaltsfragmentmodelle](/help/headless/setup/create-content-model.md)
