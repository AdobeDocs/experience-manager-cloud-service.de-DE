---
title: Entwickeln von Sites mit der Frontend-Pipeline
description: Die Frontend-Pipeline verbessert die Unabhängigkeit der Entwickler und beschleunigt den Entwicklungsprozess. In diesem Artikel werden wichtige Aspekte für den Frontend-Build-Prozess beschrieben, um eine optimale Leistung und Effizienz zu gewährleisten.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8bda36d7aa86bd6b26ecaff9831f29d9e847837f
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 30%

---


# Entwickeln von Sites mit der Frontend-Pipeline {#developing-site-with-front-end-pipeline}

Die [Frontend-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) gibt Frontend-Entwicklern größere Unabhängigkeit und beschleunigt die Entwicklung erheblich. In diesem Artikel wird erläutert, wie der -Prozess funktioniert und welche wichtigen Aspekte es zu beachten gilt, damit Sie ihn optimal nutzen können.

>[!TIP]
>
>Wenn Sie noch nicht mit der Verwendung der Frontend-Pipeline und den damit verbundenen Vorteilen vertraut sind, lesen Sie das Handbuch [Quick Site Creation Journey](/help/journey-sites/quick-site/overview.md) . Es bietet ein Beispiel dafür, wie eine neue Site schnell bereitgestellt und ihr Design unabhängig von der Backend-Entwicklung angepasst werden kann.

## Grundlegendes zum Einrichten und Erstellen von Frontend-Pipelines in AEM Cloud Manager {#front-end-build-contract}

Ähnlich wie die [Full-Stack-Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) verfügt die Frontend-Pipeline über eine eigene Umgebung. Entwickler haben eine gewisse Flexibilität bei dieser Pipeline, vorausgesetzt, sie befolgen den Frontend-Build-Vertrag.

Die Frontend-Pipeline erfordert, dass das Frontend-`Node.js`-Projekt die `build`-Skriptanweisung verwendet, um den Build zu generieren, den es bereitstellt. Diese Anforderung besteht, weil Cloud Manager das bereitstellbare Projekt für den Frontend-Build mithilfe der `npm run build` generiert.

Der resultierende Inhalt des `dist`-Ordners wird schließlich von Cloud Manager bereitgestellt und dient als statische Dateien. Diese Dateien werden extern in AEM gehostet, aber über eine `/content/...` URL in der bereitgestellten Umgebung bereitgestellt.

## Unterstützte Node.js-Versionen {#node-versions}

Die Frontend-Build-Umgebung unterstützt die folgenden `Node.js`:

* 23
* 22
* 20
* 18
* 16
* 14 (Standard)
* 12

Mithilfe der `NODE_VERSION` [Umgebungsvariante](/help/implementing/cloud-manager/environment-variables.md) können Sie die gewünschte Version festlegen.

## Best Practices für die Benennung und Verwaltung von Frontend-Pipelines in AEM {#single-source-of-truth}

Eine Best Practice für AEM-Bereitstellungen besteht darin, eine zentrale, eindeutige Datenquelle zu verwenden. Cloud Manager soll diesen Grundsatz bekräftigen. Da die Frontend-Pipeline jedoch die Entkopplung von Teilen des Codes ermöglicht, ist eine ordnungsgemäße Einrichtung unerlässlich. Um Konflikte zu vermeiden, stellen Sie sicher, dass nicht mehrere Frontend-Pipelines innerhalb derselben Umgebung auf derselben Site bereitgestellt werden.

Aus diesem Grund und insbesondere bei der Erstellung mehrerer Frontend-Pipelines empfiehlt Adobe die Beibehaltung einer systematischen Namenskonvention. Sie können die folgenden Empfehlungen verwenden:

* Der Name des Frontend-Moduls, der durch die `name`-Eigenschaft der Datei `package.json` definiert ist, sollte den Namen der Site enthalten, für die es gilt. Für eine Site, die sich in `/content/wknd` befindet, würde der Name des Frontend-Moduls zum Beispiel `wknd-theme` lauten.
* Wenn ein Frontend-Modul dasselbe Git-Repository mit anderen Modulen teilt, sollte der Name seines Ordners mit dem Namen des Frontend-Moduls übereinstimmen oder denselben Namen enthalten. Wenn beispielsweise das Frontend-Modul `wknd-theme` heißt, würde der umschließende Ordnername in etwa `wknd-theme-sources` lauten.
* Der Name der Frontend-Pipeline von Cloud Manager sollte ebenfalls den Namen des Frontend-Moduls enthalten und die Umgebung hinzufügen, in der es bereitgestellt wird (Produktion oder Entwicklung). Für das Frontend-Modul mit dem Namen `wknd-theme` kann die Pipeline beispielsweise `wknd-theme-prod` benannt werden.

Eine solche Konvention verhindert die folgenden Bereitstellungsfehler:

* Anwenden eines Frontend-Moduls auf die falsche Site.
* Erstellen mehrerer Frontend-Module, die dieselbe Site anwenden und sich gegenseitig überschreiben.
* Erstellen mehrerer Frontend-Pipelines für dieselben Quellen, was zu Race-Bedingungen führen kann, ohne die Reihenfolge der Bereitstellungen zu garantieren.

## Koordinieren der Frontend- und Backend-Entwicklung für Stabilität in AEM {#separation-of-concerns}

Eine der wichtigsten Best Practices für jede Trennung von Belangen besteht darin, den Vertrag sorgfältig zu entwerfen und zu verwalten, der die Grenzen zwischen ihnen definiert. In der Frontend-Pipeline ist dieser Vertrag die HTML- und JSON-Ausgabe, die von der Site gerendert wird. Durch die Aufrechterhaltung der Stabilität dieser Ausgabe wird sichergestellt, dass die Frontend-Pipeline einen maximalen Wert liefert, sodass das Frontend-Team unabhängig arbeiten kann.

Es gibt derzeit keine integrierte Funktion, um die Full-Stack-Pipeline synchron mit den Frontend-Pipelines auszuführen. Daher ist es bei der Trennung der Frontend-Entwicklung von der Full-Stack-Pipeline wichtig, den Vertrag sorgfältig zu verwalten, der ihre Grenzen definiert. Dieser Vertrag besteht normalerweise aus der HTML oder JSON oder beiden, die von Experience Manager gerendert werden. Alle Änderungen an diesem Vertrag sollten zwischen den Teams, die verschiedene Pipelines verwalten, sorgfältig koordiniert werden, um einen reibungslosen Übergang und eine ordnungsgemäße Abfolge der Aktualisierungen sicherzustellen.

Die folgenden Schritte werden im Allgemeinen empfohlen, wenn Sie Änderungen an der HTML- oder JSON-Ausgabe vornehmen, insbesondere wenn beide Bereiche betroffen sind.

1. Das Backend-Team richtet zunächst eine Entwicklungsumgebung mit der neuen HTML- oder JSON-Ausgabe ein.
   1. Über die Full-Stack-Pipeline stellen sie den Code bereit, der zum Rendern der gewünschten neuen HTML- oder JSON-Ausgabe oder beider Komponenten erforderlich ist.
   1. Wenn es sich um eine Umgebung handelt, auf die das Frontend-Team zuvor keinen Zugriff hatte, müssen die folgenden Schritte ausgeführt werden.
      1. URL: Das Frontend-Team muss die URL dieser Entwicklungsumgebung kennen.
      1. ACL: Dem Frontend-Team muss ein lokaler AEM-Benutzer mit Berechtigungen wie „Mitwirkende“ zugewiesen werden.
      1. Git: Das Frontend-Team muss über einen separaten Git-Speicherort für das Frontend-Modul verfügen, der speziell auf diese Entwicklungsumgebung ausgerichtet ist.

         Eine gängige Praxis ist die Erstellung einer `dev` Verzweigung, um die in der Entwicklungsumgebung vorgenommenen Änderungen zu verwalten. Dies ermöglicht eine einfachere Zusammenführung zurück in die `main` Verzweigung, die für die Bereitstellung in der Produktionsumgebung verwendet wird.

      1. Pipeline: Das Frontend-Team muss über eine Frontend-Pipeline verfügen, die in der Entwicklungsumgebung bereitgestellt wird. Diese Pipeline stellt das Frontend-Modul bereit, das sich normalerweise in der `dev`-Verzweigung befindet, wie im vorherigen Punkt beschrieben.
1. Das Frontend-Team sorgt dann dafür, dass der CSS- und JS-Code sowohl mit der alten als auch mit der neuen Ausgabe funktioniert.
   1. Gehen Sie wie gewohnt zur lokalen Entwicklung wie folgt vor:
      1. Mit dem Befehl `npx aem-site-theme-builder proxy` wird ein Proxy-Server gestartet, der Inhalte aus einer AEM-Umgebung abruft. Es ersetzt die CSS- und JS-Dateien des Frontend-Moduls durch diese Dateien aus dem lokalen `dist`.
      1. Durch das Konfigurieren der `AEM_URL` in der ausgeblendeten `.env` können Sie steuern, von welcher AEM-Umgebung der lokale Proxy-Server den Inhalt verwendet.
      1. Durch das Ändern des Werts für `AEM_URL` können Sie daher zwischen der Produktions- und Entwicklungsumgebung wechseln, um CSS und JS so anzupassen, dass sie zu beiden Umgebungen passen.
      1. Dies muss mit der Entwicklungsumgebung, die die neue Ausgabe rendert, und mit der Produktionsumgebung funktionieren, die die alte Ausgabe rendert.
   1. Die Frontend-Arbeit ist abgeschlossen, wenn das aktualisierte Frontend-Modul für beide Umgebungen funktioniert und bereitgestellt wird.
1. Das Backend-Team kann dann die Produktionsumgebung aktualisieren, indem es den Code bereitstellt, der die neue HTML- oder JSON-Ausgabe oder beides über die Full-Stack-Pipeline rendert.
1. Das Frontend-Team kann seine CSS- und JS-Dateien bereinigen, Elemente entfernen, die nur für die alte Ausgabe benötigt werden, und das endgültige Update mithilfe der Frontend-Pipeline für die Produktion bereitstellen.

## Zusätzliche Ressourcen {#additional-resources}

* Erfahren Sie, wie Sie AEM-Site-Designs verwenden, um den Stil und das Design Ihrer Site anzupassen.

  Siehe [Site-](/help/sites-cloud/administering/site-creation/site-themes.md).

* Adobe bietet einen AEM-Site-Design-Assistenten als Satz von Skripten zum Erstellen neuer Site-Designs.

  Siehe [AEM-Site-Design-Builder](https://github.com/adobe/aem-site-theme-builder)



