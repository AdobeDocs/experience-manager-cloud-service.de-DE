---
title: Extrahieren von Inhalten über die GraphQL-API
description: Erfahren Sie, wie Sie Inhaltsfragmente und die GraphQL-API als Headless-Content-Management-System verwenden.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
source-git-commit: a33ca1698b30a075d80929b7c59961beecc3a9e0
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---


# Extrahieren von Inhalten über die GraphQL-API {#extract-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql"
>title="Extrahieren von Inhalten mit der GraphQL-API"
>abstract="In diesem Modul erfahren Sie, wie Sie Inhaltsfragmente und die GraphQL-API als Headless-Content-Management-System verwenden können."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide"
>title="GraphQL Explorer starten"
>abstract="GraphQL bietet eine abfragebasierte API, mit der externe Client-Anwendungen mithilfe eines einzigen API-Aufrufs AEM nur nach den benötigten Inhalten abfragen können. In diesem Modul erfahren Sie, wie Sie zwei verschiedene Arten von Abfragen ausführen. Erfahren Sie dann, wie Sie den Inhalt aus dem Inhaltsfragment abrufen, das Sie im vorherigen Modul erstellt haben.<br><br>Starten Sie dieses Modul in einer neuen Registerkarte, indem Sie auf unten klicken."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide_footer"
>title="Gute Arbeit! Sie haben die beiden grundlegenden Arten von Abfragen kennengelernt und erfahren, wie Sie Ihre eigenen Inhalte abfragen können. Jetzt wissen Sie, wie Sie mit der AEM GraphQL API effiziente Abfragen erstellen können, die Inhalte in einem von Ihrer App erwarteten Format bereitstellen."
>abstract=""

## Abfrage nach einer Liste von Beispielinhalten {#list-query}

Sie beginnen mit dem GraphQL Explorer in einer neuen Registerkarte. Hier können Sie Abfragen anhand Ihrer Headless-Inhalte erstellen und validieren, bevor Sie sie verwenden, um Inhalte in Ihrer App oder Website zu optimieren.

1. Ihre AEM Headless-Testversion enthält einen -Endpunkt, der mit Inhaltsfragmenten vorgeladen wird und aus dem Sie Inhalte zu Testzwecken extrahieren können. Stellen Sie sicher, dass die Variable **AEM Demo Assets** Endpunkt wird im **Endpunkt** Dropdown-Menü oben rechts im Editor.

1. Kopieren Sie das folgende Codefragment für eine Listenabfrage des vorab geladenen **AEM Demo Assets** -Endpunkt. Eine Listenabfrage gibt eine Liste aller Inhalte zurück, die ein bestimmtes Inhaltsfragmentmodell verwenden. Inventar- und Kategorieseiten verwenden normalerweise dieses Abfrageformat.

   ```text
   {
    adventureList {
     items {
       _path
       title
       price
       tripLength
       primaryImage {
         ... on ImageRef {
           _path
           mimeType
           width
           height
         }
       }
     }
    }
   }
   ```

1. Ersetzen Sie den vorhandenen Inhalt im Abfrageeditor durch Einfügen des kopierten Codes.

1. Klicken Sie nach dem Einfügen auf die **Play** Schaltfläche oben links im Abfrageeditor, um die Abfrage auszuführen.

1. Die Ergebnisse werden im rechten Bereich neben dem Abfrageeditor angezeigt. Sollte die Abfrage fehlerhaft sein, wird im rechten Bereich ein Fehler angezeigt.

   ![Listenabfrage](assets/do-not-localize/list-query-1-3-4-5.png)

Sie haben gerade eine Listenabfrage für eine vollständige Liste aller Inhaltsfragmente validiert. Dieser Prozess hilft sicherzustellen, dass die Antwort dem entspricht, was Ihre App erwartet, mit Ergebnissen, die veranschaulichen, wie Ihre Apps und Websites die in AEM erstellten Inhalte abrufen.

## Abfrage nach einem bestimmten Element des Beispielinhalts {#bypath-query}

Wenn Sie eine byPath-Abfrage ausführen, können Sie Inhalte für ein bestimmtes Inhaltsfragment abrufen. Für Produktdetailseiten und Seiten, die sich auf einen bestimmten Satz von Inhalten konzentrieren, ist in der Regel diese Art von Abfrage erforderlich.

1. Kopieren Sie das folgende Codefragment für eine byPath-Abfrage des vorab geladenen **AEM Demo Assets** -Endpunkt.

   ```text
    {
     adventureByPath(
       _path: "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp"
     ) {
       item {
         _path
         title
         description {
           json
         }
         primaryImage {
           ... on ImageRef {
             _path
             width
             height
           }
         }
       }
     }
   }
   ```

1. Ersetzen Sie den vorhandenen Inhalt im Abfrageeditor durch Einfügen des kopierten Codes.

1. Klicken Sie nach dem Einfügen auf die **Play** Schaltfläche oben links im Abfrageeditor, um die Abfrage auszuführen.

1. Die Ergebnisse werden im rechten Bereich neben dem Abfrageeditor angezeigt. Sollte die Abfrage fehlerhaft sein, wird im rechten Bereich ein Fehler angezeigt.

   ![byPath-Abfrageergebnisse](assets/do-not-localize/bypath-query-2-3-4.png)

Sie haben gerade eine byPath-Abfrage validiert, um ein bestimmtes Inhaltsfragment abzurufen, das durch den Pfad dieses Fragments identifiziert wurde.

## Abfrage Ihres eigenen Inhalts {#own-queries}

Nachdem Sie nun die beiden primären Abfragetypen ausgeführt haben, können Sie Ihren eigenen Inhalt abfragen.

1. Um Abfragen für Ihre eigenen Inhaltsfragmente auszuführen, ändern Sie den -Endpunkt in der **AEM Demo Assets** Ordner in **Ihr Projekt** Ordner.

1. Löschen Sie alle vorhandenen Inhalte im Abfrageeditor. Geben Sie dann eine offene Klammer ein `{` und drücken Sie Strg+Leertaste oder Option+Leertaste , um eine Liste der in Ihrem Endpunkt definierten Modelle automatisch auszufüllen. Wählen Sie das von Ihnen erstellte Modell aus, das `List` aus den Optionen.

   ![Benutzerdefinierte Abfrage starten](assets/do-not-localize/custom-query-1-2.png)

1. Definieren Sie die Elemente, die die Abfrage für das ausgewählte Inhaltsfragmentmodell enthalten soll. Geben Sie erneut eine geöffnete Klammer ein. `{`und drücken Sie dann Strg+Leertaste oder Option+Leertaste , um eine Liste der automatischen Vervollständigung anzuzeigen. Auswählen `items` aus den Optionen.

1. Tippen oder klicken Sie auf **Pretify** -Schaltfläche, um Ihren Code automatisch zu formatieren, sodass er leichter zu lesen ist.

1. Tippen oder klicken Sie nach Abschluss des Vorgangs auf **Play** Schaltfläche oben links im Editor, um die Abfrage auszuführen. Der Editor schließt die `items` und die Abfrage ausgeführt wird.

1. Die Ergebnisse werden im rechten Bereich neben dem Abfrageeditor angezeigt.

   ![Benutzerdefinierte Abfrage ausführen](assets/do-not-localize/custom-query-3-4-5-6.png)

So können Ihre Inhalte für digitale Omnichannel-Erlebnisse bereitgestellt werden.
