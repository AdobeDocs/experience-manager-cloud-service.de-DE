---
title: Universal Editor-Aufrufe
description: Erfahren Sie mehr über die verschiedenen Arten von Aufrufen, die der universelle Editor an Ihre App sendet, um Sie beim Debugging zu unterstützen.
exl-id: 00d66e59-e445-4b5c-a5b1-c0a9f032ebd9
source-git-commit: 1fc53e726f3a15c9ac7d772b4c181a7877e417af
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 1%

---


# Universal Editor-Aufrufe {#calls}

Erfahren Sie mehr über die verschiedenen Arten von Aufrufen, die der universelle Editor an Ihre App sendet, um Sie beim Debugging zu unterstützen.

{{universal-editor-status}}

## Übersicht {#overview}

Der Universal Editor kommuniziert mit Ihrer instrumentierten App über eine Reihe definierter Aufrufe. Dies ist für transparent und hat keine Auswirkungen auf das Endbenutzererlebnis.

Für den Entwickler kann es jedoch nützlich sein, diese Aufrufe zu verstehen und zu verstehen, was sie tun, wenn Sie Ihre Anwendung mit dem universellen Editor debuggen. Wenn Sie Ihre App instrumentiert haben und sie sich nicht wie erwartet verhält, kann es hilfreich sein, die **Netzwerk** Registerkarte der Entwicklertools in Ihrem Browser und überprüfen Sie die Aufrufe beim Bearbeiten von Inhalten in Ihrer App.

![Beispiel eines Detailaufrufs auf der Registerkarte &quot;Netzwerk&quot;der Entwicklertools des Browsers](assets/calls-network-tab.png)

* Die **Nutzlast** enthält Details dazu, was der Editor aktualisiert, einschließlich der Angabe, was aktualisiert werden soll und wie es aktualisiert werden soll.
* Die **Reaktion** enthält Details dazu, was vom Editor-Dienst genau aktualisiert wurde. Dadurch soll die Aktualisierung des Inhalts im Editor erleichtert werden. In bestimmten Fällen kann die `move` aufrufen, muss die gesamte Seite aktualisiert werden.

Nachdem ein Aufruf erfolgreich abgeschlossen wurde, werden Ereignisse ausgelöst, die die Payload der Anfrage und der Antwort enthalten, die für Ihre eigene App angepasst werden können. Lesen Sie das Dokument . [Universelle Editor-Ereignisse](/help/implementing/universal-editor/events.md) für weitere Details.

Im Folgenden finden Sie eine Liste der Aufruftypen, die der Universal Editor an Ihre App sendet, sowie Beispiel-Payloads und -Antworten.

## Aktualisieren {#update}

Ein `update` wird aufgerufen, wenn Sie Inhalte in Ihrer App mit dem universellen Editor bearbeiten. Die `update` behält die Änderungen bei.

Die Payload enthält Details dazu, was an das JCR zurückgeschrieben werden soll.

* `resource`: Der zu aktualisierende JCR-Pfad
* `prop`: Die aktualisierte JCR-Eigenschaft
* `type`: Der JCR-Werttyp der zu aktualisierenden Eigenschaft
* `value`: Die aktualisierten Daten

>[!BEGINTABS]

>[!TAB Beispiel-Payload]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "text",
    "prop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

>[!TAB Beispielantwort]

```json
{
  "updates": [
    {
      "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
      "prop": "jcr:title",
      "type": "text"
    }
  ]
}
```

>[!ENDTABS]

## Details {#details}

A `details` wird aufgerufen, wenn Ihre App im universellen Editor geladen wird, um den App-Inhalt abzurufen.

Die Payload enthält die zu rendernden Daten sowie Details dazu, was die Daten darstellen (das Schema), damit sie im universellen Editor gerendert werden können.

* Für eine Komponente ruft der universelle Editor nur eine `data` -Objekt, da das Schema der Daten in der App definiert ist.
* Bei Inhaltsfragmenten ruft der universelle Editor auch eine `schema` -Objekt, da das Inhaltsfragmentmodell im JCR definiert ist.

>[!BEGINTABS]

>[!TAB Beispiel-Payload]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "component",
    "prop": ""
  }
}
```

>[!TAB Beispielantwort]

```json
{
  "data": {
    "jcr:primaryType": "nt:unstructured",
    "jcr:title": "Tiny Toon Adventures",
    "fileReference": "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/adobestock-216674449.jpeg",
    "cq:panelTitle": "WKND Adventures",
    "actionsEnabled": "true",
    "jcr:lastModifiedBy": "admin",
    "titleFromPage": "false",
    "jcr:description": "<p>With WKND Adventures, you don't just see the world you experinece it.</p>\r\n",
    "jcr:lastModified": "Fri Jan 19 2024 11:05:59 GMT+0100",
    "descriptionFromPage": "true",
    "sling:resourceType": "wknd/components/teaser",
    "textIsRich": "true",
    "cq:styleIds": [
      "1555543212672"
    ],
    "actions": {
      "jcr:primaryType": "nt:unstructured",
      "item0": {
        "jcr:primaryType": "nt:unstructured",
        "link": "/content/wknd/language-masters/en/adventures",
        "text": "View Trips"
      }
    }
  }
}
```

>[!ENDTABS]

## Hinzufügen {#add}

Ein `add` wird aufgerufen, wenn Sie mit dem universellen Editor eine neue Komponente in Ihrer App platzieren.

Die Payload enthält eine `path` -Objekt, das enthält, wo der Inhalt hinzugefügt werden soll.

Er umfasst auch `content` -Objekt mit zusätzlichen Objekten für endpunktspezifische Details des zu speichernden Inhalts [für jedes Plug-in.](/help/implementing/universal-editor/architecture.md) Wenn Ihre App beispielsweise auf Inhalten von AEM und Magento basiert, enthält die Payload ein Datenobjekt für jedes System.

>[!BEGINTABS]

>[!TAB Beispiel-Payload]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  },
  "content": {
    "name": "text",
    "aem": {
      "page": {
        "resourceType": "wknd/components/text",
        "template": {
          "text": "Default Text"
        }
      }
    }
  }
}
```

>[!TAB Beispielantwort]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ],
  "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521"
}
```

>[!ENDTABS]

## Verschieben {#move}

A `move` -Aufruf tritt auf, wenn Sie eine Komponente mit dem universellen Editor in Ihrer App verschieben.

Die Payload enthält eine `from` Objekt, das definiert, wo die Komponente war, und ein `to` -Objekt, das definiert, wo es verschoben wurde.

>[!BEGINTABS]

>[!TAB Beispiel-Payload]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "from": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    },
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847",
      "type": "media",
      "prop": "fileReference"
    }
  },
  "to": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB Beispielantwort]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## Remove {#remove}

A `remove` wird aufgerufen, wenn Sie eine Komponente in Ihrer App mit dem universellen Editor löschen.

Die Payload enthält den Pfad des entfernten Objekts.

>[!BEGINTABS]

>[!TAB Beispiel-Payload]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_593170193",
      "type": "text",
      "prop": "text"
    },
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB Beispielantwort]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "prop": "",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## Publish {#publish}

A `publish` wird aufgerufen, wenn Sie auf **Veröffentlichen** im universellen Editor, um den bearbeiteten Inhalt zu veröffentlichen.

Der Universal Editor durchläuft den Inhalt und generiert eine Liste von Verweisen, die ebenfalls veröffentlicht werden müssen.

>[!BEGINTABS]

>[!TAB Beispiel-Payload]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "references": [
    "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking/jcr:content/data/master",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/title",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/title",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_229050934",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_2123678383",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1668104604",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847"
  ]
}
```

>[!TAB Beispielantwort]

```json
{
  "publishes": [
    "/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway",
    "/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp",
    "/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand",
    "/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah",
    "/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany",
    "/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming",
    "/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting",
    "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia",
    "/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc",
    "/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica",
    "/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing",
    "/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling",
    "/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking",
    "/content/wknd/us/en/newsletter",
    "/content/wknd/language-masters/en/universal-editor-container"
  ]
}
```

>[!ENDTABS]

## Zusätzliche Ressourcen {#additional-resources}

* [Universelle Editor-Ereignisse](/help/implementing/universal-editor/events.md)
