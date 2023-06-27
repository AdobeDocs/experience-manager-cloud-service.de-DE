---
title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
description: In diesem Artikel wird beschrieben, wie das dynamische Modell für die Komponentenzuordnung im JavaScript SPA SDK für AEM erfolgt.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 61%

---

# Zuordnung dynamischer Modelle zu Komponenten für SPAs {#dynamic-model-to-component-mapping-for-spas}

In diesem Dokument wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript-SPA-SDK für AEM erfolgt.

## ComponentMapping-Modul {#componentmapping-module}

Das `ComponentMapping`-Modul wird dem Frontend-Projekt als NPM-Paket bereitgestellt. Es speichert Frontend-Komponenten und bietet der Single Page Application die Möglichkeit, Frontend-Komponenten AEM-Ressourcentypen zuzuordnen. Das Modul ermöglicht eine dynamische Auflösung von Komponenten beim Analysieren des JSON-Modells der Anwendung.

Jedes im Modell vorhandene Element enthält eine `:type` -Feld, das einen AEM Ressourcentyp verfügbar macht. Bei der Implementierung kann sich die Frontend-Komponente mit dem Fragment des Modells, das sie von den zugrunde liegenden Bibliotheken erhalten hat, selbst rendern.

Siehe [SPA Blueprint](blueprint.md) Dokument finden Sie weitere Informationen zum Parsen von Modellen und zum Zugriff der Frontend-Komponenten auf das Modell.

Weitere Informationen finden Sie im npm-Paket: [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping).

## Modellgesteuerte Single Page Application {#model-driven-single-page-application}

Einzelseiten-Apps, die das JavaScript SPA SDK für AEM verwenden, sind modellgesteuert:

1. Frontend-Komponenten registrieren sich im [Komponentenzuordnungs-Store](#componentmapping-module).
1. Anschließend durchläuft der [Container](blueprint.md#container), sobald ihm ein Modell vom [Modellanbieter](blueprint.md#the-model-provider) zur Verfügung gestellt wurde, seinen Modellinhalt (`:items`).

1. Wenn eine Seite vorhanden ist, werden die untergeordneten Elemente (`:children`) erhalten Sie zunächst eine Komponentenklasse aus der [Komponentenzuordnung](blueprint.md#componentmapping) und dann instanziieren.

## App-Initialisierung {#app-initialization}

Jede Komponente wird um die Funktionen des [`ModelProvider`](blueprint.md#the-model-provider) erweitert. Die Initialisierung hat daher folgende allgemeine Form:

1. Jeder Modellanbieter initialisiert sich selbst und wartet auf Änderungen, die an dem Modell vorgenommen wurden, das seiner inneren Komponente entspricht.
1. [`PageModelManager`](blueprint.md#pagemodelmanager) muss gemäß dem [Initialisierungsfluss](blueprint.md) initialisiert werden.

1. Nach dem Speichern gibt der Seitenmodell-Manager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Frontend-Stamm-[Container](blueprint.md#container)-Komponente der App übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![Initialisierung des App-Modells](assets/app-model-initialization.png)
