---
title: Pfadzuordnung für Edge Delivery Services
description: Erfahren Sie, wie Sie in der AEM-Autoreninstanz genutzte Seitenpfade öffentlichen Seitenpfaden zuordnen, die auf der Website verwendet werden, und wie Sie steuern, welcher Inhalt in Edge Delivery Services veröffentlicht wird.
feature: Edge Delivery Services
role: User
exl-id: 3d68135d-e84c-4bf4-93d1-38a0be70ce4a
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 100%

---

# Pfadzuordnung für Edge Delivery Services {#path-mapping}

Erfahren Sie, wie Sie in der AEM-Autoreninstanz genutzte Seitenpfade öffentlichen Seitenpfaden zuordnen, die auf der Website verwendet werden, und wie Sie steuern, welcher Inhalt in Edge Delivery Services veröffentlicht wird.

## Überblick {#overview}

Um WYSIWYG-Inhalte mithilfe von AEM erstellen und in Edge Delivery Services veröffentlichen zu können, müssen Sie die Pfadzuordnung Ihres Projekts einrichten. Diese Zuordnung dient zwei Zwecken.

* Sie ordnet die in Ihrer AEM-Autoreninstanz genutzten Seitenpfade den öffentlichen Seitenpfaden zu, die auf Ihrer Website verwendet werden, und stellt eine Beziehung zwischen ihnen her.
* Sie steuert, welche Inhalte (Seiten, Blätter, Assets usw.) in Edge Delivery Services veröffentlicht werden.

Die Pfadzuordnung muss für jedes Projekt einzeln und entsprechend den Inhalten und der URL-Struktur des Projekts konfiguriert werden. Sie wird von AEM während der Veröffentlichung von Inhalten und während der Bearbeitung von Inhalten im [universellen Editor](/help/sites-cloud/authoring/universal-editor/navigation.md) verwendet.

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

### mappings {#mappings}

Die Konfiguration `mappings` enthält ein Array von internen Pfaden (in der AEM-Autoreninstanz) und externen URL-Pfaden (auf der öffentlichen Website).

Das Format lautet `<internal paths>:<external path>`. Sie besteht normalerweise aus mindestens zwei Einträgen.

1. Der erste Eintrag aus dem Beispiel ist die Pfadzuordnung der Website-Seiten.
1. Der zweite Eintrag steuert die Zuordnung von `.helix/config.json` zur entsprechenden Tabellenseite im AEM-Authoring-Repository.

In diesem Beispiel sind alle unter `/content/aem-boilerplate/...` gespeicherten Seiten auf der Edge Delivery Services-Site direkt unter `https://main--my-site--org.aem.live/....` öffentlich zugänglich.

>[!TIP]
>
>Alle Tabellendaten, die als Tabellen verwaltet werden (z. B. Metadaten, Umleitungen und Taxonomien), werden normalerweise als `.json`-API-URLs in Edge Delivery Services veröffentlicht. Dazu müssen sie einzeln in der Zuordnungskonfiguration aufgeführt sein.
>
>Weitere Informationen finden Sie im Dokument [Verwenden von Tabellen zum Verwalten von Tabellendaten](/help/edge/wysiwyg-authoring/tabular-data.md).

### includes {#includes}

Die Konfiguration `includes` steuert, welche Inhaltspfade tatsächlich in Edge Delivery Services repliziert werden. Sie kann auch ein beliebiges Array von Pfaden enthalten und umfasst normalerweise die Stammseite der Sites auf oberster Ebene.

Auf Edge Delivery Services-Seiten verwendete Assets werden normalerweise neben der Web-Seite veröffentlicht. Sie werden automatisch aus der AEM-Autoreninstanz in Edge Delivery Services exportiert.

>[!TIP]
>
>Wenn Sie Assets direkt in Edge Delivery Services veröffentlichen möchten (z. B. Bilder oder PDF-Dateien über ihre URLs außerhalb eines Seitenkontexts direkt zugänglich sein sollen), müssen Sie die DAM-Pfade auch zum Abschnitt `includes` der Konfiguration hinzufügen.
>
>Wenn beispielsweise ein Asset-Stammordner wie `/content/dam/my-site/documents`, der einen Satz PDF-Dateien enthält, über `/assets/...` öffentlich zugänglich sein soll, muss ein Eintrag zum Abschnitt `includes` der Konfiguration hinzugefügt werden.

## Vorgehensweise bei der Konfiguration {#how-to-configure}

Ihre Pfadzuordnungen können je nach Einrichtung Ihres Projekts auf zwei Arten konfiguriert werden.

1. Wenn das Projekt für `aem.live` konfiguriert ist und den [Konfigurationsdienst](https://www.aem.live/docs/config-service-setup) für zentrale Konfigurationen verwendet, wird die Pfadzuordnung für jede Site über diesen Konfigurationsdienst konfiguriert.

   * Dies ist eine beispielhafte cURL-Anfrage zum Konfigurieren von Pfadzuordnungen:

   ```text
   curl --request POST \
     --url https://admin.aem.page/config/{org}/sites/{site}/public.json \
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

1. Wenn das Projekt den Konfigurationsdienst nicht verwendet, wird die Pfadzuordnung über eine `paths.json`-Datei im GitHub-Repository Ihres Projekts konfiguriert.

   * Ein Beispiel finden Sie unter [`https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json).

In beiden Fällen können Sie die Konfiguration nach der Konfiguration der Pfadzuordnungen über die öffentlich zugängliche Konfigurations-URL `https://<branch>--<site>--<org>.aem.page/config.json` überprüfen.
