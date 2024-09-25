---
title: Pfadzuordnung für Edge Delivery Services
description: Erfahren Sie, wie Sie in der AEM-Autoreninstanz verwendete Seitenpfade öffentlichen Seitenpfaden zuordnen, die auf der Website verwendet werden, und steuern, welcher Inhalt in Edge Delivery Services veröffentlicht wird.
feature: Edge Delivery Services
role: User
source-git-commit: 51a2b453ccce39cb42c927a088bc088083545542
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---


# Pfadzuordnung für Edge Delivery Services {#path-mapping}

Erfahren Sie, wie Sie in der AEM-Autoreninstanz verwendete Seitenpfade öffentlichen Seitenpfaden zuordnen, die auf der Website verwendet werden, und steuern, welcher Inhalt in Edge Delivery Services veröffentlicht wird.

## Übersicht {#overview}

Um WYSIWYG-Inhalte mithilfe von AEM erstellen und in Edge Delivery Services veröffentlichen zu können, müssen Sie die Pfadzuordnung Ihres Projekts einrichten. Diese Zuordnung hat zwei Zwecke.

* Sie ordnet Seitenpfade, die in Ihrer AEM-Autoreninstanz verwendet werden, zu und erstellt eine Beziehung zu den öffentlichen Seitenpfaden, die auf Ihrer Website verwendet werden.
* Sie steuert, welche Inhalte (Seiten, Blätter, Assets usw.) werden in Edge Delivery Services veröffentlicht.

Die Pfadzuordnung muss für jedes Projekt einzeln und entsprechend dem Inhalt und der URL-Struktur des Projekts konfiguriert werden. Sie wird von AEM während der Veröffentlichung von Inhalten und während der Bearbeitung von Inhalten im [universellen Editor](/help/sites-cloud/authoring/universal-editor/navigation.md) verwendet.

## Konfigurationsformat {#configuration-format}

Das Format der Pfadzuordnungskonfiguration enthält zwei Abschnitte (`mappings` und `includes`), die dem folgenden Beispiel ähneln.

```json
{
  "mappings": [
    "/content/aem-boilerplate/:/",
    "/content/aem-boilerplate/configuration:/.helix/config.json"
  ],
  "includes:" [
    "/content/aem-boilerplate/"
  ]
}
```

### Zuordnungen {#mappings}

Die Konfiguration `mappings` enthält eine Reihe von internen Pfaden (in der AEM-Autoreninstanz) und externen URL-Pfaden (auf der öffentlichen Website).

Das Format ist `<internal paths>:<external path>`. Sie besteht normalerweise aus mindestens zwei Einträgen.

1. Der erste Eintrag aus dem Beispiel ist die Pfadzuordnung der Website-Seiten.
1. Der zweite Eintrag steuert die Zuordnung von `.helix/config.json` zur entsprechenden Tabellenseite im AEM Authoring-Repository.

In diesem Beispiel sind alle unter `/content/aem-boilerplate/...` gespeicherten Seiten auf der Edge Delivery Services-Site direkt unter `https://main--my-site--org.aem.live/....` öffentlich zugänglich.

>[!TIP]
>
>Alle Tabellendaten, die als Tabellen verwaltet werden (z. B. Metadaten, Umleitungen und Taxonomien), werden normalerweise als `.json` API-URLs auf Edge Delivery Services veröffentlicht. Dazu müssen sie einzeln in der Zuordnungskonfiguration aufgeführt sein.
>
>Weitere Informationen finden Sie im Dokument [Verwenden von Tabellenblättern zum Verwalten von Tabellendaten](/help/edge/wysiwyg-authoring/tabular-data.md) .

### include {#includes}

Die `includes` -Konfiguration steuert, welche Inhaltspfade tatsächlich auf Edge Delivery Services repliziert werden. Es kann auch ein beliebiges Array von Pfaden enthalten und enthält normalerweise die Stammseite der Sites auf oberster Ebene.

Auf Edge Delivery Services-Seiten verwendete Assets werden normalerweise neben der Webseite veröffentlicht. Sie werden automatisch aus der AEM-Autoreninstanz in Edge Delivery Services exportiert.

>[!TIP]
>
>Wenn Sie in einem Anwendungsfall möchten, dass Assets direkt auf Edge Delivery Services veröffentlicht werden (z. B. Bilder oder PDF über ihre URLs außerhalb eines Seitenkontexts direkt zugänglich sein sollen), müssen Sie die DAM-Pfade auch zum Abschnitt &quot;`includes`&quot;der Konfiguration hinzufügen.
>
>Wenn beispielsweise ein Asset-Stammordner wie `/content/dam/my-site/documents`, der einen Satz PDF enthält, über `/assets/...` öffentlich zugänglich sein soll, muss ein Eintrag zum Abschnitt `includes` der Konfiguration hinzugefügt werden.

## Anleitung zum Konfigurieren {#how-to-configure}

Ihre Pfadzuordnungen können je nach Einrichtung Ihres Projekts auf zwei Arten konfiguriert werden.

1. Wenn das Projekt für `aem.live` konfiguriert ist und den [Konfigurationsdienst](https://www.aem.live/docs/config-service-setup) für zentralisierte Konfigurationen verwendet, wird die Pfadzuordnung für jede Site über diesen Konfigurationsdienst konfiguriert.

   * Im Folgenden finden Sie eine Beispiel-cURL-Anfrage zum Konfigurieren von Pfadzuordnungen.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/{org}/sites/{site}/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: ......' \
     --data '{
       "paths": {
       "mappings": [
         "/content/aem-boilerplate/:/",
         "/content/aem-boilerplate/configuration:/.helix/config.json"
       ],
       "includes": [
         "/content/aem-boilerplate/"
       ]
   }
   }'
   ```

1. Wenn das Projekt den Konfigurationsdienst nicht verwendet, wird die Pfadzuordnung über eine Datei &quot;paths.json&quot;in Ihren Projekten des GitHub-Repositorys konfiguriert.

   * Ein Beispiel finden Sie unter [`https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json`](/https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json) .

In beiden Fällen können Sie die Konfiguration nach der Konfiguration der Pfadzuordnungen über die öffentlich zugängliche Konfigurations-URL `https://<branch>--<site>--<org>.aem.page/config.json` überprüfen.
