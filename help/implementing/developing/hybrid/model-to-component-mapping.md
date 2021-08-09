---
title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
description: In diesem Artikel wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für AEM erfolgt.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: ht
source-wordcount: '322'
ht-degree: 100%

---

# Zuordnung dynamischer Modelle zu Komponenten für SPAs {#dynamic-model-to-component-mapping-for-spas}

In diesem Dokument wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für AEM erfolgt.

## ComponentMapping-Modul {#componentmapping-module}

Das `ComponentMapping`-Modul wird dem Frontend-Projekt als NPM-Paket bereitgestellt. Es speichert Frontend-Komponenten und bietet der Single Page Application die Möglichkeit, Frontend-Komponenten AEM-Ressourcentypen zuzuordnen. Dies ermöglicht beim Parsen des JSON-Modells des Programms eine dynamische Auflösung von Komponenten.

Alle im Modell vorhandenen Elemente enthalten ein Feld `:type`, das einen AEM-Ressourcentyp verfügbar macht. Bei der Implementierung kann sich die Frontend-Komponente mit dem Fragment des Modells, das sie von den zugrunde liegenden Bibliotheken erhalten hat, selbst rendern.

Weitere Informationen zum Parsen von Modellen und zum Zugriff der Frontend-Komponenten auf das Modell finden Sie im Dokument [SPA-Blueprint](blueprint.md).

Weitere Informationen finden Sie im npm-Paket: [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping).

## Modellgesteuerte Single Page Application {#model-driven-single-page-application}

Single Page Applications, die das JavaScript SPA SDK für AEM nutzen, sind modellgesteuert:

1. Frontend-Komponenten registrieren sich im [Komponentenzuordnungs-Store](#componentmapping-module).
1. Anschließend durchläuft der [Container](blueprint.md#container), sobald ihm ein Modell vom [Modellanbieter](blueprint.md#the-model-provider) zur Verfügung gestellt wurde, seinen Modellinhalt (`:items`).

1. Im Fall einer Seite erhalten die untergeordneten Elemente (`:children`) zunächst eine Komponentenklasse aus der [Komponentenzuordnung](blueprint.md#componentmapping) und instanziieren sie dann.

## App-Initialisierung {#app-initialization}

Jede Komponente wird um die Funktionen des [`ModelProvider`](blueprint.md#the-model-provider) erweitert. Die Initialisierung hat daher die folgende allgemeine Form:

1. Jeder Modellanbieter initialisiert sich selbst und wartet auf Änderungen, die an dem Modell vorgenommen wurden, das seiner inneren Komponente entspricht.
1. [`PageModelManager`](blueprint.md#pagemodelmanager) muss gemäß dem [Initialisierungsfluss](blueprint.md) initialisiert werden.

1. Nach dem Speichern gibt der Seitenmodell-Manager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Frontend-Stamm-[Container](blueprint.md#container)-Komponente der App übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![Initialisierung des App-Modells](assets/app-model-initialization.png)
