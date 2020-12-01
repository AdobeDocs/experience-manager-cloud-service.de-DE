---
title: Zuordnung dynamischer Modelle zu Komponenten für SPA
description: In diesem Artikel wird beschrieben, wie das dynamische Modell zur Komponentenzuordnung im JavaScript SPA SDK für AEM erfolgt.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 21%

---


# Zuordnung dynamischer Modelle zu Komponenten für SPA {#dynamic-model-to-component-mapping-for-spas}

In diesem Dokument wird beschrieben, wie das dynamische Modell zur Komponentenzuordnung im JavaScript-SPA-SDK für AEM ausgeführt wird.

## ComponentMapping-Modul {#componentmapping-module}

Das `ComponentMapping`-Modul wird dem Frontend-Projekt als NPM-Paket bereitgestellt. Es speichert Front-End-Komponenten und bietet der Einzelseitenanwendung die Möglichkeit, Frontend-Komponenten AEM Ressourcentypen zuzuordnen. Dies ermöglicht beim Parsen des JSON-Modells der Anwendung eine dynamische Auflösung von Komponenten.

Alle im Modell vorhandenen Elemente enthalten ein `:type`-Feld, das einen AEM-Ressourcentyp verfügbar macht. Bei der Implementierung kann sich die Frontend-Komponente mit dem Fragment des Modells, das sie von den zugrunde liegenden Bibliotheken erhalten hat, selbst rendern.

Weitere Informationen zur Modellanalyse und zum Zugriff auf die Front-End-Komponenten finden Sie im Dokument [SPA Blueprint](blueprint.md).

Weitere Informationen finden Sie im npm-Paket: [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modellgetriebene Einzelseitenanwendung {#model-driven-single-page-application}

Einzelseitenanwendungen, die das JavaScript SPA SDK für AEM nutzen, werden modellgesteuert:

1. Front-End-Komponenten registrieren sich beim [Component Mapping Store](#componentmapping-module).
1. Anschließend durchläuft der [Container](blueprint.md#container), sobald er vom [Modellanbieter](blueprint.md#the-model-provider) mit einem Modell geliefert wird, den Inhalt des Modells (`:items`).

1. Bei einer Seite erhalten die untergeordneten Elemente (`:children`) zunächst eine Komponentenklasse von [Komponentenzuordnung](blueprint.md#componentmapping) und instanziieren sie dann.

## App-Initialisierung {#app-initialization}

Jede Komponente wird mit den Funktionen von [`ModelProvider`](blueprint.md#the-model-provider) erweitert. Die Initialisierung erfolgt daher in folgender allgemeiner Form:

1. Jeder Modellanbieter initialisiert sich selbst und überwacht Änderungen, die an dem Teil des Modells vorgenommen wurden, der seiner inneren Komponente entspricht.
1. Das [`PageModelManager`](blueprint.md#pagemodelmanager) muss initialisiert werden, wie es durch den [Initialisierungsfluss](blueprint.md) dargestellt wird.

1. Nach dem Speichern gibt der Seitenmodellmanager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Front-End-Stammkomponente [Container](blueprint.md#container) der Anwendung übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![Initialisierung des App-Modells](assets/app-model-initialization.png)
