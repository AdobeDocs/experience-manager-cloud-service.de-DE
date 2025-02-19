---
title: Aufrufe im universellen Editor
description: Erfahren Sie mehr über die verschiedenen Arten von Aufrufen, die der universelle Editor an Ihre App sendet, um Sie beim Debuggen zu unterstützen.
exl-id: 00d66e59-e445-4b5c-a5b1-c0a9f032ebd9
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '615'
ht-degree: 100%

---


# Aufrufe im universellen Editor {#calls}

Erfahren Sie mehr über die verschiedenen Arten von Aufrufen, die der universelle Editor an Ihre App sendet, um Sie beim Debuggen zu unterstützen.

## Überblick {#overview}

Der universelle Editor kommuniziert mit Ihrer instrumentierten App über eine Reihe definierter Aufrufe. Dies ist für die Endbenutzenden transparent und hat keine Auswirkungen auf ihr Anwendererlebnis.

Für die Entwickelnden kann es jedoch nützlich sein, diese Aufrufe zu verstehen und zu wissen, was sie tun, wenn sie Ihre Anwendung mit dem universellen Editor debuggen. Wenn Sie Ihre Anwendung instrumentiert haben und sie sich nicht wie erwartet verhält, kann es hilfreich sein, die Registerkarte **Netzwerk** der Entwickler-Tools in Ihrem Browser zu öffnen und die Aufrufe zu inspizieren, während Sie Inhalte in Ihrer Anwendung bearbeiten.

![Beispiel für einen Detailaufruf auf der Netzwerk-Registerkarte der Entwickler-Tools des Browsers](assets/calls-network-tab.png)

* Die **Payload** des Aufrufs enthält Details zu dem, was vom Editor aktualisiert wird, einschließlich der Angabe, was zu aktualisieren ist und wie es zu aktualisieren ist.
* Die **Antwort** enthält Details darüber, was genau vom Editor-Dienst aktualisiert wurde. Dadurch soll die Aktualisierung des Inhalts im Editor erleichtert werden. In bestimmten Fällen, wie bei einem `move`-Aufruf, muss die gesamte Seite aktualisiert werden.

Nachdem ein Aufruf erfolgreich abgeschlossen wurde, werden Ereignisse mit der Anfrage- und Antwort-Payload ausgelöst, die für Ihre eigene App angepasst werden kann. Weitere Informationen finden Sie unter [Ereignisse des universellen Editors](/help/implementing/universal-editor/events.md).

Im Folgenden finden Sie eine Liste der Arten von Aufrufen, die der universelle Editor an Ihre App richtet, sowie Beispiele für Payloads und Antworten.

## Update {#update}

Ein `update`-Aufruf erfolgt, wenn Sie Inhalte in Ihrer App mit dem universellen Editor bearbeiten. `update` behält die Änderungen bei.

Die Payload enthält Details dazu, was an das JCR zurückgeschrieben werden soll.

* `resource`: Der zu aktualisierende JCR-Pfad
* `prop`: Die JCR-Eigenschaft, die aktualisiert werden soll
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

Ein `details`-Aufruf erfolgt beim Laden Ihrer App im universellen Editor, um den Inhalt der App abzurufen.

Die Payload enthält die Daten, die gerendert werden sollen, sowie Details darüber, was die Daten darstellen (das Schema), damit sie im universellen Editor gerendert werden können.

* Für eine Komponente ruft der universelle Editor nur ein `data`-Objekt ab, da das Schema der Daten in der App definiert ist.
* Für Inhaltsfragmente ruft der universelle Editor ebenfalls ein `schema`-Objekt ab, da das Inhaltsfragmentmodell im JCR definiert ist.

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

Ein `add`-Aufruf erfolgt, wenn Sie mit dem universellen Editor eine neue Komponente in Ihrer App platzieren.

Die Payload enthält ein `path`-Objekt, das den Pfad enthält, wo der Inhalt hinzugefügt werden soll.

Es enthält auch ein `content`-Objekt mit zusätzlichen Objekten für endpunktspezifische Details des zu speichernden Inhalts [für jedes Plug-in](/help/implementing/universal-editor/architecture.md). Wenn Ihre App beispielsweise auf Inhalten von AEM und Magento basiert, enthält die Payload ein Datenobjekt für jedes System.

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

Ein `move`-Aufruf erfolgt, wenn Sie eine Komponente innerhalb Ihrer App mit dem universellen Editor verschieben.

Die Payload enthält ein `from`-Objekt, das angibt, wo sich die Komponente befand, und ein `to`-Objekt, das angibt, wohin sie verschoben wurde.

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

Ein `remove`-Aufruf erfolgt, wenn Sie mit dem universellen Editor eine Komponente innerhalb Ihrer App löschen.

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

## Veröffentlichen {#publish}

Ein `publish`-Aufruf erfolgt, wenn Sie im universellen Editor auf die Schaltfläche **Veröffentlichen** klicken, um den von Ihnen bearbeiteten Inhalt zu veröffentlichen.

Der universelle Editor durchläuft den Inhalt und generiert eine Liste von Verweisen, die ebenfalls veröffentlicht werden müssen.

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

* [Ereignisse des universellen Editors](/help/implementing/universal-editor/events.md)

