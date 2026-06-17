---
title: Integrieren von Content Advisor mit Dynamic Media
description: Erfahren Sie, wie Sie Content Advisor mit Dynamic Media integrieren, um Benutzern das Durchsuchen, Anzeigen und Auswählen von Dynamic Media-Ausgabedarstellungen für die Verwendung in ihren Programmen und Workflows zu ermöglichen.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
source-git-commit: 95209a154a0d3208c5fcda8d4117f80d1015d2fe
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 1%

---

# Integration mit Dynamic Media {#integrate-dynamic-media}

Content Advisor kann mit Dynamic Media integriert werden, damit Benutzer Dynamic Media-Ausgabedarstellungen zur Verwendung in ihren Programmen und Workflows durchsuchen, in der Vorschau anzeigen und auswählen können. Benutzer können aus verfügbaren Ausgabedarstellungen, Bildvorgaben und smarten Zuschnitten auswählen und unterstützte Dynamic Media-Modifikatoren anwenden, um die Bereitstellung von Assets anzupassen. In den folgenden Abschnitten wird beschrieben, wie Sie die ausgewählten Ausgabedarstellungsinformationen verarbeiten und URLs für die Bereitstellung von Dynamic Media für Ihre Anwendung generieren.

## Erstellen von Dynamic Media-URLs mit selectedMedia {#build-dynamic-media-urls-selectedmedia}

Wenn ein(e) Benutzende(r) eine Dynamic Media-Ausgabedarstellung im Dynamic Media-Bedienfeld Inhaltsratgeber auswählt, werden die ausgewählten Ausgabedarstellungsinformationen im `selectedMedia` -Objekt zurückgegeben. Die Hostanwendung muss diese Informationen verwenden, um die entsprechende Bereitstellungs-URL für Dynamic Media zu generieren.

>[!NOTE]
>
> Die Hostanwendung muss die in diesem Abschnitt beschriebene Logik zur URL-Generierung implementieren, um die im Inhaltsratgeber ausgewählten Dynamic Media-Ausgabedarstellungen zu verwenden. Die ausgewählten Ausgabedarstellungsinformationen werden als Metadaten zurückgegeben und nicht automatisch in eine Versand-URL konvertiert.

### selectedMedia-Objekt {#selectedmedia-object}

Das `selectedMedia`-Objekt wird dem ausgewählten Asset hinzugefügt und enthält Informationen zur vom Benutzer ausgewählten Dynamic Media-Ausgabedarstellung.

```javascript
'selectedMedia': Array<{
    base?: string;
    preset?: string;
    smartcrop?: string;
    modifiers?: Array<string>;
    apiStyle?: 'scene7' | 'openapi'
}>;
```

Das `selectedMedia`-Objekt enthält die folgenden Eigenschaften:

| Eigenschaft | Beschreibung |
|---|---|
| `base` | Die ausgewählte Basis-Ausgabedarstellung |
| `preset` | Die ausgewählte Bildvorgabe. |
| `smartcrop` | Die ausgewählte Ausgabedarstellung für smartes Zuschneiden. |
| `modifiers` | Ein oder mehrere vom Benutzer hinzugefügte Dynamic Media-Modifikatoren. |
| `apiStyle` | Gibt an, ob die ausgewählte Ausgabedarstellung den Versandstapel Scene7 (`scene7`) oder OpenAPI (`openapi`) verwendet. |

Wenn ein(e) Benutzende(r) beispielsweise eine Basisausgabe auswählt und den `rotate=90` anwendet, sieht das zurückgegebene -Objekt wie folgt aus:

```javascript
selectedMedia: {
    apiStyle: "scene7",
    base: "scene7company/image",
    modifiers: ["rotate=90"]
}
```

![Anzeigen von Dynamic Media-Ausgabedarstellungen](assets/content-advisor-dm-renditions.png)

### Zugriff auf selectedMedia im handleSelection-Rückruf {#access-selectedmedia}

Sobald eine Ausgabedarstellung ausgewählt ist, wird das `selectedMedia` Objekt in der `selectedAssets` Payload verfügbar, die vom `handleSelection`-Callback zurückgegeben wird.

```javascript
async function handleSelection(assets) {

    const dmUrls = [];

    assets.forEach((asset) => {

        if(asset?.selectedMedia){

            const dmUrl = createDMUrlFromSelectedMedia(
                asset.selectedMedia,
                asset
            );

            dmUrls.push({ asset, dmUrl });

        }

    });
}
```

Der Rückruf iteriert durch die ausgewählten Assets. Für jedes Asset, das ein `selectedMedia` enthält, generiert die Anwendung eine Dynamic Media-URL unter Verwendung der ausgewählten Ausgabedarstellungsinformationen.

## Generieren einer Dynamic Media-URL {#generate-dynamic-media-url}

Die folgende Funktion validiert die ausgewählten Ausgabedarstellungsinformationen und bestimmt, welcher Dynamic Media-Bereitstellungsstapel verwendet werden soll.

```javascript
const DM_OPENAPI_API_STYLE = 'openapi';
const DM_SCENE7_API_STYLE = 'scene7';
const ASSET_REPO_NAME_KEY = 'repo:name';
const ASSET_REPO_ID_KEY = 'repo:id';
const REPO_ID_KEY = 'repo:repositoryId';

export const createDMUrlFromSelectedMedia = (
    selectedMedia,
    repoMetadata
) => {
    if (!selectedMedia || !selectedMedia?.apiStyle) {
        throw new Error(
            'Selected media or api style is not valid'
        );
    }

    if (
        selectedMedia?.apiStyle === DM_OPENAPI_API_STYLE
    ) {
        return buildDMOpenApiUrl(
            selectedMedia,
            repoMetadata
        );
    } else if (
        selectedMedia?.apiStyle === DM_SCENE7_API_STYLE
    ) {
        return buildDMScene7Url(
            selectedMedia,
            repoMetadata
        );
    }
};
```

Diese Funktion führt die folgenden Aktionen aus:

* Überprüft, ob die ausgewählte Ausgabedarstellung einen `apiStyle` enthält.
* Legt fest, ob die ausgewählte Ausgabedarstellung Dynamic Media mit OpenAPI-Funktionen oder Dynamic Media Scene7 verwendet.
* Ruft die entsprechende URL-Generierungsfunktion basierend auf dem ausgewählten Versandstapel auf.

### Erstellen einer OpenAPI-URL für Dynamic Media {#build-openapi-url}

Die folgende Funktion generiert eine Dynamic Media OpenAPI-URL unter Verwendung der ausgewählten Ausgabedarstellungsinformationen und Repository-Metadaten.

```javascript
export const buildDMOpenApiUrl = (
    selectedMedia,
    repoMetadata
) => {
    const { base, preset, smartcrop, modifiers }
        = selectedMedia;

    const dmDomain =
        repoMetadata?.[REPO_ID_KEY]
            .replace('author-', 'delivery-');

    const assetName =
        repoMetadata?.[ASSET_REPO_NAME_KEY];

    const assetId =
        repoMetadata?.[ASSET_REPO_ID_KEY];

    const seoName =
        assetName?.split('.')[0];

    const assetFormat =
        repoMetadata?.['dc:format'];

    let dmUrl;

    if (
        assetFormat &&
        assetFormat.startsWith('video/')
    ) {

        dmUrl =
`https://${dmDomain}/adobe/assets/${assetId}/play`;

    } else {

        dmUrl =
`https://${dmDomain}/adobe/assets/${assetId}/as/${seoName}.avif`;

        if (base) {
        } else if (preset) {
            dmUrl =
`${dmUrl}?preset=${preset}`;
        } else if (smartcrop) {
            dmUrl =
`${dmUrl}?smartcrop=${smartcrop}`;
        }
    }

    if (modifiers && dmUrl) {

        const modifierString =
            getModifierString(selectedMedia);

        if(base) {
            dmUrl =
`${dmUrl}?${modifierString}`;
        } else {
            dmUrl =
`${dmUrl}&${modifierString}`;
        }
    }

    return dmUrl;
};
```

Diese Funktion:

* Ruft die zum Erstellen der Versand-URL erforderlichen Repository-Informationen ab.
* Erstellt die OpenAPI-Basis-Bereitstellungs-URL.
* Hängt die ausgewählte Vorgabe oder das ausgewählte smarte Zuschneiden an die URL an, falls zutreffend.
* Fügt alle vom Benutzer ausgewählten Modifikatoren an.
* Gibt die endgültige OpenAPI-Bereitstellungs-URL zurück.

Für Video-Assets generiert die Funktion die Dynamic Media-Video-Player-URL.

### Erstellen einer Dynamic Media Scene7-URL {#build-scene7-url}

Die folgende Funktion generiert eine Dynamic Media Scene7-URL.

```javascript
export const buildDMScene7Url = (
    selectedMedia,
    repoMetadata
) => {

    const {
        base,
        preset,
        smartcrop,
        modifiers
    } = selectedMedia;

    let scene7Domain =
        repoMetadata?.['repo:scene7Domain'];

    const scene7File =
        repoMetadata?.['repo:scene7File'];

    if (!scene7Domain || !scene7File) {
        return null;
    }

    scene7Domain =
        scene7Domain.startsWith('http://')
        ? scene7Domain.replace(
            'http://',
            'https://'
          )
        : scene7Domain;

    scene7Domain =
        scene7Domain?.endsWith('/')
        ? scene7Domain
        : `${scene7Domain}/`;

    let dmUrl;

    if (base) {

        dmUrl =
`${scene7Domain}is/image/${base}`;

    } else if (preset) {

        dmUrl =
`${scene7Domain}is/image/${scene7File}?$${preset}$`;

    } else if (smartcrop) {

        dmUrl =
`${scene7Domain}is/image/${scene7File}:${smartcrop}`;
    }

    if (modifiers && dmUrl) {

        const modifierString =
            getModifierString(selectedMedia);

        if (preset) {
            dmUrl =
`${dmUrl}&${modifierString}`;
        } else {
            dmUrl =
`${dmUrl}?${modifierString}`;
        }
    }

    return dmUrl;
};
```

Diese Funktion:

* Ruft die Scene7-Domain und Asset-Informationen aus den Repository-Metadaten ab.
* Erstellt eine URL für die ausgewählte Basis-Ausgabedarstellung, Bildvorgabe oder das smarte Zuschneiden.
* Fügt alle ausgewählten Modifikatoren an.
* Gibt die endgültige Scene7-Versand-URL zurück.

## Erzeugen der Modifikatorzeichenfolge {#generate-modifiers-string}

Die folgende Hilfsfunktion konvertiert das Modifikator-Array in eine URL-kompatible Abfragezeichenfolge.

```javascript
export const getModifierString = (
    selectedMedia
) => {

    const { modifiers } = selectedMedia;

    if (modifiers) {

        const modifierString =
            modifiers.length > 0
                ? modifiers.join('&')
                : '';

        return modifierString;
    }

    return null;
};
```

Die Funktion kombiniert alle ausgewählten Modifikatoren in einer einzigen Zeichenfolge, die durch kaufmännische Und-Zeichen (`&`) getrennt ist.

Beispiel:

```javascript
[
    'rotate=90',
    'width=1200'
]
```

Rückgabe:

```text
rotate=90&width=1200
```

Die generierte Zeichenfolge wird an die endgültige Dynamic Media-URL angehängt und wendet die ausgewählten Umwandlungen an, wenn das Asset bereitgestellt wird.

