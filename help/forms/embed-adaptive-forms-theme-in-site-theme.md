---
title: Einbetten eines adaptiven Forms-Designs in ein AEM Sites-Design
description: Erfahren Sie, wie Sie ein adaptives Forms-Design (z. B. Arbeitsfläche) in ein AEM Sites-Design integrieren, sodass Sites-Seiten und eingebettete adaptive Forms ein einheitliches Design und eine einheitliche Bereitstellung gemeinsam nutzen.
keywords: Design für adaptive Formulare, Site-Design, AEM Sites-Design, Formulardesignintegration, Frontend-Pipeline, Design-Einbettung
feature: Adaptive Forms, Core Components
role: Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 0607e11c-84d2-42cb-be9f-acd7c328a342
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 1%

---

# Einbetten eines adaptiven Forms-Designs in ein AEM Sites-Design

Sie können ein adaptives Forms-Design (z. B. das [AEM Forms Canvas-Design](https://github.com/adobe/aem-forms-theme-canvas)) in Ihr AEM Sites-Design einbetten. Auf diese Weise steuert ein einzelnes Design sowohl Ihre Website-Seiten als auch alle adaptiven Forms, die auf diesen Seiten eingebettet sind, mit einem Build und einer Bereitstellung über die [AEM-Frontend-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=de).

Dieser Artikel richtet sich an Entwicklerinnen und Entwickler, die das standardmäßige (oder benutzerdefinierte) AEM Sites-Design verwalten oder anpassen und adaptive Formularstile einbeziehen möchten, ohne eine separate Forms-Design-Bereitstellung verwalten zu müssen.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* **AEM as a Cloud Service** mit der [Frontend-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=de) konfiguriert für Ihr Site-Design.
* **Site-Design** Quellen - z. B. das [Standard-Site-Vorlagen-Design](https://github.com/adobe/aem-site-template-standard) (das Repository, das `theme/` mit `src/theme.scss`, `src/components/` usw. enthält).
* **Forms-Design-**: Das [AEM Forms Canvas-Design](https://github.com/adobe/aem-forms-theme-canvas) (oder ein anderes kompatibles adaptives Forms-Design) wurde lokal geklont oder heruntergeladen.
* **Node.js und npm** - zum Erstellen des Site-Designs (unterstützte Versionen finden Sie in der README-Datei zum Design).
* **Maven** - wenn Sie das vollständige Site-Vorlagenpaket erstellen (optional für Arbeit nur für Designs).

## Schritt 1: Erstellen des Ordners für adaptive Formularkomponenten {#step-1-create-folder}

Erstellen Sie im Site-Design-Repository den Ordner, in dem sich das Forms-Design befinden soll:

```text
theme/src/components/adaptiveform/
```

Alle Forms-Design-Assets befinden sich in diesem Ordner, sodass sie von den vorhandenen Site-Komponenten getrennt bleiben.

## Schritt 2: Forms-Design-Komponenten und -Bilder kopieren {#step-2-copy-components-and-images}

Verwenden Ihres **Forms** Designs (z. B. `aem-forms-theme-canvas`) und Ihrer **Site** Designpfade:

1. **Kopieren von Komponentenordnern**\
   Kopieren Sie aus dem Forms-Design den gesamten Inhalt von `src/components/` in das Site-Design als:

   ```text
   theme/src/components/adaptiveform/
   ```

   So erhalten Sie Pfade wie:

   ```text
   theme/src/components/adaptiveform/button/
   theme/src/components/adaptiveform/checkbox/
   theme/src/components/adaptiveform/container/
   … (one folder per component)
   ```

   ![Hinzufügen von Komponenten adaptiver Formulare](/help/forms/assets/theme-add-adaptiveform-component.png)

2. **Bilder kopieren**\
   Kopieren Sie die Forms-Design-Bilder in das Site-Design:

   ```text
   Forms theme:  src/resources/images/*
   Site theme:   theme/src/components/adaptiveform/resources/images/
   ```

   Erstellen Sie `theme/src/components/adaptiveform/resources/images/`, wenn es nicht vorhanden ist, und kopieren Sie alle Bild-Assets (z. B. `question.svg`, `Chevron-Left.svg`, `busy-state.gif` usw.).

   ![Bilder hinzufügen](/help/forms/assets/theme-add-images.png)

## Schritt 3: Kopieren von Variablen und Mixins {#step-3-copy-variables-and-mixins}

Das Forms-Design verwendet freigegebene Variablen und Mixins unter `src/site/`. Kopieren Sie nur diese beiden Dateien in das **Stammverzeichnis** von `adaptiveform/` (nicht in einen `site` Unterordner):

| Source (Forms-Design) | Ziel (Site-Design) |
|---------------------------|---------------------------------------------------|
| `src/site/_variables.scss` | `theme/src/components/adaptiveform/_variables.scss` |
| `src/site/_mixin.scss` | `theme/src/components/adaptiveform/_mixin.scss` |

Kopieren **nicht** den Rest des `src/site/` des Forms-Designs. Für die eingebetteten Formularstile sind nur diese beiden Dateien erforderlich.

![Variablen und Mixins hinzufügen](/help/forms/assets/theme-add-mixin-variable.png)

## Schritt 4: Korrigieren von Bildpfaden in SCSS {#step-4-fix-image-paths}

Im Forms-Design verweisen Komponenten-SCSS-Dateien häufig auf Bilder mit Pfaden wie `./resources/` oder `url(resources/`. Nach dem Kopieren in das Site-Design müssen diese Pfade auf `theme/src/components/adaptiveform/resources/images/` verweisen.

Das **Standard-Site-Vorlagendesign** verwendet Parcel, das `url()` Pfade aus `theme/src/` auflöst. Wenn sich also Bilder in `theme/src/components/adaptiveform/resources/images/` befinden, verwenden Sie den **`components/adaptiveform/resources/images/`** Pfad (relativ zu `theme/src/`).

**Suchen und Ersetzen** in jedem `.scss` unter `theme/src/components/adaptiveform/`:

| Suchen | Ersetzen durch |
|------|------------------|
| `./resources/` | `components/adaptiveform/resources/` |
| `url(resources/` | `url(components/adaptiveform/resources/` |
| `url('resources/` | `url('components/adaptiveform/resources/` |
| `url(../resources/` | `url(components/adaptiveform/resources/` |

**Beispiel** - vor (Forms-Design):

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(./resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

**Nachher** (Site-Design, Bilder in `adaptiveform/resources/images/`):

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(components/adaptiveform/resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

![Ändern der Bild-URL](/help/forms/assets/theme-change-url.png)

Wiederholen Sie diesen Vorgang für jede SCSS-Datei unter `adaptiveform/`, die auf Bilder verweist (Schaltfläche, Akkordeon, Assistent, Container, Freihandsignatur usw.). Es wird empfohlen, in Ihrer IDE ein projektweites Suchen/Ersetzen über `theme/src/components/adaptiveform/` durchzuführen.

## Schritt 5: Erstellen des Einstiegspunkt-SCSS für adaptive Formulare {#step-5-create-adaptiveform-scss}

Erstellen Sie **`theme/src/components/adaptiveform/_adaptiveform.scss`** im Site-Design. Diese Datei muss:

1. Importieren Sie die freigegebenen Variablen und Mixins.
2. Importieren Sie die SCSS-Hauptdatei jeder Komponente des adaptiven Formulars.

Verwenden Sie Folgendes als vollständigen Einstiegspunkt (stimmt mit der Standardintegration für alle auf Kernkomponenten basierenden Formularkomponenten überein):

```scss
//== Adaptive Form components (forms theme integration)
// Variables and mixins for adaptive form components
@import 'variables';
@import 'mixin';

//== Core adaptive form components
@import './button/_button.scss';
@import './checkboxgroup/_checkboxgroup.scss';
@import './container/_container.scss';
@import './datepicker/_datepicker.scss';
@import './dropdown/_dropdown.scss';
@import './fileinput/_fileinput.scss';
@import './footer/_footer.scss';
@import './image/_image.scss';
@import './numberinput/_numberinput.scss';
@import './panelcontainer/_panelcontainer.scss';
@import './radiobutton/_radiobutton.scss';
@import './text/_text.scss';
@import './textinput/_textinput.scss';
@import './accordion/_accordion.scss';
@import './tabsontop/_tabsontop.scss';
@import './pageheader/_pageheader.scss';
@import './wizard/_wizard.scss';
@import './title/_title.scss';
@import './telephoneinput/_telephoneinput.scss';
@import './emailinput/_emailinput.scss';
@import './recaptcha/_recaptcha.scss';
@import './verticaltabs/_verticaltabs.scss';
@import './checkbox/_checkbox.scss';
@import './termsandconditions/_termsandconditions.scss';
@import './switch/_switch.scss';
@import './hcaptcha/_hcaptcha.scss';
@import './turnstile/_turnstile.scss';
@import './review/_review.scss';
@import './scribble/_scribble.scss';
@import './datetime/_datetime.scss';
```

![Adaptives Formular - SCSS](/help/forms/assets/theme-adaptive-form-scss.png)

Wenn in Ihrem Forms-Design einige Komponenten weggelassen werden (z. B. kein Scribble oder CAPTCHA), entfernen oder kommentieren Sie die entsprechenden `@import` aus, um Build-Fehler zu vermeiden. Die obige Liste entspricht der [Canvas-Design](https://github.com/adobe/aem-forms-theme-canvas)-Struktur.

## Schritt 6: Adaptives Formulardesign in das Site-Design importieren {#step-6-import-in-theme-scss}

Fügen Sie **`theme/src/theme.scss`** einen einzelnen Import am **Ende** der Datei hinzu (nach anderen Komponentenimporten):

```scss
//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

**Beispiel** - Ende der `theme.scss`:

```scss
// ... existing site component imports ...
@import './components/embed/_embed.scss';
@import './components/pdfviewer/_pdfviewer.scss';
@import './components/socialmediasharing/_social_media_sharing.scss';

//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

![Hinzufügen von adaptivem Formular-SCSS](/help/forms/assets/theme-add-adaptive-form-scss-theme.png)

Dies ist die einzige Änderung, die in der vorhandenen Site-Design-Struktur erforderlich ist. Der gesamte formularspezifische Code bleibt unter `src/components/adaptiveform/`.

## Schritt 7: Erstellen und Bereitstellen {#step-7-build-and-deploy}

1. Erstellen Sie das Site-Design aus dem Design-Stamm:

   ```bash
   cd theme
   npm install
   npm run build
   ```

   ![Build ausführen](/help/forms/assets/theme-mpm-run-build.png)

2. Bereitstellen über Ihre vorhandene [Frontend-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=de). Nach der Bereitstellung gilt dasselbe Design-CSS sowohl für Sites-Seiten als auch für eingebettete adaptive Forms.

## Fehlerbehebung {#troubleshooting}

| Problem | Was zu überprüfen ist |
|-------|-------------------------------|
| Build schlägt fehl: „Datei nicht gefunden“ für ein Bild | Stellen Sie sicher, dass alle Formularbilder `theme/src/components/adaptiveform/resources/images/` sind. Verwenden Sie in jedem `.scss` unter `adaptiveform/` &quot;`url(components/adaptiveform/resources/images/...)`&quot;, damit der Pfad von `theme/src/` aufgelöst wird (erforderlich für den standardmäßigen Site-Design-Build mit „Paket„). Verwenden Sie `../resources/` oder `resources/` nur, wenn Ihr Bundler die Pfade pro Datei auflöst. Verwenden Sie dann den Pfad, der Ihrem Bildordner entspricht. |
| Build schlägt fehl: „Datei nicht gefunden“ für `_variables.scss` oder `_mixin.scss` | Kopieren Sie beide Dateien aus dem Forms-Design-`src/site/` in `theme/src/components/adaptiveform/` (den Stamm des adaptiven Formulars), nicht in einen `site` Unterordner. |
| Build schlägt fehl: „Datei nicht gefunden“ für eine Komponente (z. B. `_scribble.scss`) | Ihr Forms-Design darf diese Komponente nicht enthalten. Entfernen Sie `theme/src/components/adaptiveform/_adaptiveform.scss` die `@import` für diese Komponente oder kommentieren Sie sie aus. |
| Formular wird gerendert, hat aber keine Stile | Bestätigen Sie, dass die Seite die Client-Bibliothek verwendet, die das erstellte Design-CSS enthält und dass `theme.scss` die `@import './components/adaptiveform/_adaptiveform.scss';` Zeile enthält und das Design neu erstellt und bereitgestellt wurde. |
| Stile stehen im Konflikt zwischen Site- und Formularkomponenten | Klassen von Formularkomponenten haben einen Namespace (z. B. `cmp-adaptiveform-button`). Wenn Konflikte auftreten, überprüfen Sie, ob benutzerdefiniertes Site-CSS diese Klassen überschreibt, und passen Sie die Spezifität oder Reihenfolge an. |

## Siehe auch {#see-also}

* [Verwenden Sie Designs, um auf Kernkomponenten basierende adaptive Forms zu gestalten](/help/forms/using-themes-in-core-components.md)
* [Entwickeln mit Frontend-Pipelines](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=de)
