---
title: Bildeditor
description: Der Bildeditor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um eine Bearbeitung von Bildern durch Inhaltsautorinnen und -autoren zu erleichtern.
exl-id: c8ae4f59-75b1-49b4-8dd4-957d2e33000b
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 100%

---

# Bildeditor {#image-editor}

Der Bildeditor ist ein Kernstück von AEM und kann von Komponenten genutzt werden, um eine Bearbeitung von Bildern durch Inhaltsautorinnen und -autoren zu erleichtern.

## Relative Einheiten für Imagemap {#relative-units-for-image-map}

Der Bildeditor persistiert Imagemap-Bereiche sowohl als absolute als auch als relative Einheiten. Relative Einheiten sind nützlich, wenn sie in einer interaktiven Bildkomponente Client-seitig als Datenattribute zur dynamischen Größenanpassung einer Imagemap (relativ zur Bildgröße) bereitgestellt werden.

### imageMap-Eigenschaft {#imagemap-property}

Die Imagemap-Koordinaten werden vom Bildeditor als `imageMap`-Eigenschaft im JCR persistiert. Die Eigenschaft weist das folgende Format auf.

Sie speichert Zuordnungsbereiche wie folgt:

`[area1][area2][...]`

Bereichsformat:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Beispiel:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Unterstützung für SVG-Bilder {#support-for-svg-images}

Skalierbare Vektorgrafiken (SVG) werden vom Bildeditor unterstützt.

* Das Drag-and-Drop eines SVG-Assets aus DAM und das Hochladen eines SVG-Datei-Uploads aus einem lokalen Dateisystem werden beide unterstützt.

## Aktivieren von Plug-ins nach MIME-Typ {#enabling-plugins-by-mime-type}

In bestimmten Fällen müssen Erstellungsaktionen für bestimmte MIME-Typen eingeschränkt werden, da die Server-seitige Verarbeitung nicht unterstützt wird. Das Bearbeiten von SVG-Bildern ist beispielsweise nicht zulässig.

Plug-ins im Bildeditor können selektiv nach MIME-Typ aktiviert werden, indem Sie im Konfigurationsknoten des jeweiligen Plug-ins eine `supportedMimeTypes`-Eigenschaft festlegen.

### Beispiel {#example}

Nehmen wir beispielsweise an, die Möglichkeit zum Zuschneiden sollte nur bei GIF-, JPEG-, PNG-, WEBP- und TIFF-Bildern erlaubt sein.

Die `supportedMimeTypes`-Eigenschaft muss dann als Zeichenfolge der zulässigen MIME-Typen im Konfigurationsknoten des Plug-ins im `cq:editConfig`-Knoten der Bildkomponente festgelegt werden.

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```
