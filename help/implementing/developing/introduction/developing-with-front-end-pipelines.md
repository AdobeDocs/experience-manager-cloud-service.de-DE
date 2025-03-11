---
title: Entwickeln von Sites mit der Frontend-Pipeline
description: Die Frontend-Pipeline verbessert die Unabhängigkeit der Entwickelnden und beschleunigt den Entwicklungsprozess. In diesem Artikel werden wichtige Aspekte zum Frontend-Build-Prozess beschrieben, um eine optimale Leistung und Effizienz zu gewährleisten.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8d21437b56af1d337e20b25b53fdd00ecb856bf1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 100%

---


# Entwickeln von Sites mit der Frontend-Pipeline {#developing-site-with-front-end-pipeline}

Die [Frontend-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) bietet Frontend-Entwickelnden mehr Unabhängigkeit und beschleunigt die Entwicklung erheblich. In diesem Artikel wird erklärt, wie dieser Prozess funktioniert, und es werden wichtige Aspekte hervorgehoben, damit Sie dessen volles Potenzial ausschöpfen können.

>[!TIP]
>
>Wenn Sie noch nicht mit der Verwendung der Frontend-Pipeline und den damit verbundenen Vorteilen vertraut sind, lesen Sie das Handbuch [Tour zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md). Es bietet ein Beispiel dafür, wie eine neue Site schnell bereitgestellt und ihr Design unabhängig von der Backend-Entwicklung angepasst werden kann.

## Grundlegendes zum Einrichten der Frontend-Pipeline und zum Build-Prozess in AEM Cloud Manager {#front-end-build-contract}

Ähnlich wie die [Full-Stack-Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) verfügt die Frontend-Pipeline über eine eigene Umgebung. Entwickelnde haben eine gewisse Flexibilität bei dieser Pipeline, solange sie den Frontend-Build-Vertrag befolgen.

Die Frontend-Pipeline erfordert, dass in `Node.js` des Frontend-Projekts die Skriptanweisung `build` verwendet wird, um den Build zu generieren, den sie bereitstellt. Diese Anforderung besteht, weil Cloud Manager den Befehl `npm run build` verwendet, um das bereitstellbare Projekt für den Frontend-Build zu generieren.

Der resultierende Inhalt des Ordners `dist` ist das, was letztendlich von Cloud Manager bereitgestellt wird und diesem als statische Dateien dient. Diese Dateien werden extern für AEM gehostet, jedoch über eine URL `/content/...` in der bereitgestellten Umgebung zur Verfügung gestellt.

## Unterstützte Node.js-Versionen {#node-versions}

Die Frontend-Build-Umgebung unterstützt die folgenden `Node.js`-Versionen:

<!-- * 23
* 22
* 20 -->
* 18
* 16
* 14 (Standard)
* 12

Mithilfe der `NODE_VERSION` [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md) können Sie die gewünschte Version festlegen.

## Best Practices für das Benennen und Verwalten von Frontend-Pipelines in AEM {#single-source-of-truth}

Eine Best Practice für AEM-Bereitstellungen besteht darin, eine zentrale, eindeutige Datenquelle zu verwenden. Cloud Manager wurde so konzipiert, dass dieses Prinzip noch verstärkt wird. Da die Frontend-Pipeline jedoch die Entkopplung von Teilen des Codes ermöglicht, ist eine ordnungsgemäße Einrichtung unerlässlich. Zur Vermeidung von Konflikten muss sichergestellt werden, dass nicht mehrere Frontend-Pipelines innerhalb derselben Umgebung auf derselben Site bereitgestellt werden.

Aus diesem Grund empfiehlt Adobe insbesondere bei der Erstellung mehrerer Frontend-Pipelines, eine systematische Namenskonvention wie die folgende beizubehalten. Sie können die folgenden Empfehlungen befolgen:

* Der Name des Frontend-Moduls, der durch die `name`-Eigenschaft der Datei `package.json` definiert ist, sollte den Namen der Site enthalten, für die es gilt. Für eine Site, die sich in `/content/wknd` befindet, würde der Name des Frontend-Moduls zum Beispiel `wknd-theme` lauten.
* Wenn ein Frontend-Modul dasselbe Git-Repository mit anderen Modulen teilt, sollte der Name seines Ordners mit dem Namen des Frontend-Moduls übereinstimmen oder denselben Namen enthalten. Wenn beispielsweise das Frontend-Modul `wknd-theme` heißt, würde der umschließende Ordnername in etwa `wknd-theme-sources` lauten.
* Der Name der Frontend-Pipeline von Cloud Manager sollte ebenfalls den Namen des Frontend-Moduls enthalten und die Umgebung hinzufügen, in der es bereitgestellt wird (Produktion oder Entwicklung). Für das Frontend-Modul mit dem Namen `wknd-theme` kann die Pipeline beispielsweise `wknd-theme-prod` benannt werden.

Eine solche Konvention verhindert die folgenden Bereitstellungsfehler:

* Anwenden eines Frontend-Moduls auf die falsche Site.
* Erstellen mehrerer Frontend-Module, die dieselbe Site anwenden und sich gegenseitig überschreiben.
* Erstellen mehrerer Frontend-Pipelines für dieselben Quellen, was zu Race-Bedingungen führen kann, ohne die Reihenfolge der Bereitstellungen zu garantieren.

## Koordinieren der Frontend- und Backend-Entwicklung für eine gute Stabilität in AEM {#separation-of-concerns}

Eine der wichtigsten Best Practices für jede Trennung der Zuständigkeiten ist die Sorgfalt bei der Gestaltung und Verwaltung der Richtlinien, die die Grenzen zwischen ihnen definieren. Bei der Frontend-Pipeline handelt es sich bei den Richtlinien um die von der Site gerenderte HTML- und JSON-Ausgabe. Die Aufrechterhaltung der Stabilität dieser Ausgabe stellt sicher, dass die Frontend-Pipeline einen maximalen Wert liefert, sodass das Frontend-Team unabhängig arbeiten kann.

Es gibt derzeit keine integrierte Funktion, um die Full-Stack-Pipeline synchron mit den Frontend-Pipelines auszuführen. Aus diesem Grund ist es bei der Trennung der Frontend-Entwicklung von der Full-Stack-Pipeline wichtig, die Richtlinien sorgfältig zu verwalten, die ihre Grenzen definieren. Diese Richtlinien bestehen normalerweise aus der HTML und/oder JSON, die von Experience Manager gerendert werden. Alle Änderungen an diesen Richtlinien sollten sorgfältig zwischen den Teams, die verschiedene Pipelines verwalten, koordiniert werden, um einen reibungslosen Übergang und eine ordnungsgemäße Abfolge der Aktualisierungen sicherzustellen.

Die folgenden Schritte werden im Allgemeinen für Änderungen an der HTML- oder JSON-Ausgabe empfohlen. Dies gilt insbesondere, wenn beide Bereiche betroffen sind.

1. Das Backend-Team richtet zunächst eine Entwicklungsumgebung mit der neuen HTML- oder JSON-Ausgabe ein.
   1. Über die Full-Stack-Pipeline stellt es den Code bereit, der zum Rendern der gewünschten neuen HTML- und/oder JSON-Ausgabe erforderlich ist.
   1. Wenn dies eine Umgebung ist, auf die das Frontend-Team zuvor keinen Zugriff hatte, müssen die folgenden Schritte ausgeführt werden.
      1. URL: Das Frontend-Team muss die URL dieser Entwicklungsumgebung kennen.
      1. ACL: Dem Frontend-Team muss ein lokaler AEM-Benutzer mit Berechtigungen wie „Mitwirkende“ zugewiesen werden.
      1. Git: Das Frontend-Team muss über einen separaten Git-Speicherort für das Frontend-Modul verfügen, der speziell auf diese Entwicklungsumgebung ausgerichtet ist.

         Eine gängige Praxis ist die Erstellung einer `dev`-Verzweigung, um die in der Entwicklungsumgebung vorgenommenen Änderungen zu verwalten. Diese Vorgehensweise ermöglicht eine problemlose Rückführung in die `main`-Verzweigung, die für die Bereitstellung in der Produktionsumgebung verwendet wird.

      1. Pipeline: Das Frontend-Team muss über eine Frontend-Pipeline verfügen, die in der Entwicklungsumgebung bereitgestellt wird. Diese Pipeline stellt das Frontend-Modul bereit, das sich normalerweise in der `dev`-Verzweigung befindet, wie im vorherigen Punkt beschrieben.
1. Das Frontend-Team sorgt dann dafür, dass der CSS- und JS-Code sowohl mit der alten als auch mit der neuen Ausgabe funktioniert.
   1. Gehen Sie wie üblich zur lokalen Entwicklung wie folgt vor:
      1. Mit dem Befehl `npx aem-site-theme-builder proxy` wird ein Proxy-Server gestartet, der Inhalte aus einer AEM-Umgebung abruft. Er ersetzt die CSS- und JS-Dateien des Frontend-Moduls durch diese Dateien aus dem lokalen Ordner `dist`.
      1. Wenn Sie die Variable `AEM_URL` in der versteckten Datei `.env` konfigurieren, können Sie kontrollieren, von welcher AEM-Umgebung der lokale Proxy-Server den Inhalt verwendet.
      1. Das Ändern des Werts `AEM_URL` ermöglicht daher den Wechsel zwischen der Produktions- und Entwicklungsumgebung, um CSS und JS so anzupassen, dass sie zu beiden Umgebungen passen.
      1. Dies muss mit der Entwicklungsumgebung, die die neue Ausgabe rendert, und mit der Produktionsumgebung funktionieren, die die alte Ausgabe rendert.
   1. Die Frontend-Arbeit ist abgeschlossen, wenn das aktualisierte Frontend-Modul für beide Umgebungen funktioniert und bereitgestellt wird.
1. Das Backend-Team kann dann die Produktionsumgebung aktualisieren, indem es den Code bereitstellt, der die neue HTML- und/oder JSON-Ausgabe über die Full-Stack-Pipeline rendert.
1. Das Frontend-Team kann seine CSS- und JS-Dateien bereinigen, Elemente entfernen, die nur von der alten Ausgabe benötigt wurden, und das letzte Update über die Frontend-Pipeline in der Produktion bereitstellen.

## Zusätzliche Ressourcen {#additional-resources}

* Erfahren Sie, wie Sie AEM-Site-Designs verwenden, um den Stil und das Design Ihrer Site anzupassen.

  Siehe [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md).

* Adobe bietet einen AEM-Site-Design-Assistenten als Satz von Skripten zum Erstellen neuer Site-Designs.

  Siehe [AEM-Site-Design-Builder](https://github.com/adobe/aem-site-theme-builder)



