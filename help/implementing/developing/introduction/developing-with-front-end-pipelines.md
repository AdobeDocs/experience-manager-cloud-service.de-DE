---
title: Entwickeln von Sites mit der Frontend-Pipeline
description: Mit der Frontend-Pipeline erhalten Frontend-Entwickler mehr Unabhängigkeit und der Entwicklungsprozess wird erheblich beschleunigt. In diesem Dokument werden einige besondere Überlegungen zum Frontend-Build-Prozess beschrieben, die berücksichtigt werden sein sollten.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
source-git-commit: a6b228023d7bd2a40e4db3a1d2c3900a5c24031c
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 100%

---


# Entwickeln von Sites mit der Frontend-Pipeline {#developing-site-with-front-end-pipeline}

[Mit der Frontend-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) erhalten Frontend-Entwickler mehr Unabhängigkeit und der Entwicklungsprozess kann erheblich an Geschwindigkeit gewinnen. In diesem Dokument wird beschrieben, wie dieser Prozess funktioniert, sowie einige Überlegungen, die Sie beachten sollten, um das ganze Potenzial dieses Prozesses zu auszuschöpfen.

>[!TIP]
>
>Wenn Sie noch nicht mit der Verwendung der Frontend-Pipeline und den damit verbundenen Vorteilen vertraut sind, finden Sie im Abschnitt [Weg zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) ein Beispiel dafür, wie Sie eine neue Site schnell implementieren und ihr Design ganz unabhängig von der Backend-Entwicklung anpassen können.

## Frontend-Build-Vertrag {#front-end-build-contract}

Ähnlich wie die [Full-Stack-Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) verfügt die Frontend-Pipeline über eine eigene Umgebung. Entwickelnde haben eine gewisse Flexibilität bei dieser Pipeline, solange der folgende Frontend-Build-Vertrag eingehalten wird.

Die Frontend-Pipeline erfordert, dass das Frontend-Node.js-Projekt die `build`-Skriptanweisung verwendet, um den Build zu generieren, der von der Frontend-Pipeline bereitgestellt wird. Cloud Manager verwendet den Befehl `npm run build`, um das bereitstellbare Projekt für den `dist`-Ordner zu generieren.

Der Inhalt des Ordners `dist` wird schließlich für AEM as a Cloud Service von der Cloud Manager-Pipeline bereitgestellt.

### Knotenversionen {#node-versions}

Standardmäßig verwendet die Frontend-Pipeline den Knoten 14, aber auch 12 und 16 sind verfügbar.

Mithilfe der Umgebungsvariable `CM_CUSTOM_VAR_NODE_VERSION` können Sie die gewünschte Version festlegen.

## Zentrale Datenquelle {#single-source-of-truth}

Ein allgemein bewährtes Verfahren besteht darin, für das, was in AEM implementiert ist, eine zentrale Datenquelle zu haben. Das Ziel von Cloud Manager besteht darin, diese zentrale Datenquelle offensichtlich zu machen. Da die Frontend-Pipeline jedoch die Entkopplung des Speicherorts für Teile des Codes ermöglicht, liegt eine zusätzliche Verantwortung in der korrekten Einrichtung der Frontend-Pipelines. Es muss darauf geachtet werden, dass nicht mehrere Frontend-Pipelines erstellt werden, die auf derselben Site in derselben Umgebung implementiert werden.

Aus diesem Grund und insbesondere bei der Erstellung mehrerer Frontend-Pipelines wird empfohlen, eine systematische Benennungskonvention wie die folgende beizubehalten:

* Der Name des Frontend-Moduls, der durch die `name`-Eigenschaft der Datei `package.json` definiert ist, sollte den Namen der Site enthalten, für die es gilt. Für eine Site, die sich in `/content/wknd` befindet, würde der Name des Frontend-Moduls zum Beispiel `wknd-theme` lauten.
* Wenn ein Frontend-Modul dasselbe Git-Repository mit anderen Modulen teilt, sollte der Name seines Ordners mit dem Namen des Frontend-Moduls übereinstimmen oder denselben Namen enthalten. Wenn beispielsweise das Frontend-Modul `wknd-theme` heißt, würde der umschließende Ordnername in etwa `wknd-theme-sources` lauten.
* Der Name der Frontend-Pipeline von Cloud Manager sollte ebenfalls den Namen des Frontend-Moduls enthalten und die Umgebung hinzufügen, in der es implementiert wird (Produktion oder Entwicklung). Für das Frontend-Modul mit dem Namen `wknd-theme` kann die Pipeline beispielsweise `wknd-theme-prod` benannt werden.

Eine solche Konvention sollte die folgenden Implementierungsfehler wirksam verhindern:

* Anwenden eines Frontend-Moduls auf die falsche Site
* Erstellen mehrerer Frontend-Module, die dieselbe Site anwenden und sich gegenseitig überschreiben
* Erstellen mehrerer Frontend-Pipelines für dieselben Quellen, was zu Race-Bedingungen führen kann, ohne die Reihenfolge der Implementierungen zu garantieren

## Trennung der Zuständigkeiten {#separation-of-concerns}

Eine weitere bewährte Methode, die sich auf die Trennung der Zuständigkeiten bezieht, ist die besondere Sorgfalt bei der Gestaltung und der Verwaltung der Richtlinien zu den getrennten Zuständigkeiten. Bei der Frontend-Pipeline handelt es sich bei den Richtlinien, die diesen Code vom Rest trennen, um die von der Site gerenderte HTML und JSON. Wenn diese HTML und JSON stabil bleiben, liefert die Frontend-Pipeline ihren maximalen Wert, indem sie das Frontend-Team komplett unabhängig macht.

Es gibt derzeit keine spezielle Funktion, um die Full-Stack-Pipeline synchron mit der/den Frontend-Pipeline(s) auszuführen. Aus diesem Grund muss bei der Entkopplung der Frontend-Entwicklung von der Full-Stack-Pipeline besondere Sorgfalt in den Richtlinien, die die beiden Problembereiche trennen, angewendet werden. Diese Richtlinien sind im Allgemeinen die HTML und/oder JSON, die Experience Manager rendert. Änderungen an diesen Richtlinien müssen daher zwischen den Teams, die die verschiedenen Pipelines betreiben, gut geplant werden, damit sie sich über die Reihenfolge der entsprechenden Änderungen einigen können.

Die folgenden Schritte werden im Allgemeinen empfohlen, wenn es notwendig ist, Änderungen an der HTML- und/oder JSON-Ausgabe vorzunehmen, die beide Zuständigkeiten betreffen.

1. Das Backend-Team richtet zunächst eine Entwicklungsumgebung mit der neuen HTML- und/oder JSON-Ausgabe ein.
   1. Über die Full-Stack-Pipeline stellen sie den Code bereit, der zum Rendern der gewünschten neuen HTML- und/oder JSON-Ausgabe erforderlich ist.
   1. Wenn dies eine Umgebung ist, auf die das Frontend-Team zuvor keinen Zugriff hatte, müssen die folgenden Schritte ausgeführt werden.
      1. URL: Das Frontend-Team muss die URL dieser Entwicklungsumgebung kennen.
      1. ACL: Dem Frontend-Team muss ein lokaler AEM-Benutzer mit Berechtigungen wie „Mitwirkende“ zugewiesen werden.
      1. Git: Das Frontend-Team muss über einen separaten Git-Speicherort für das Frontend-Modul verfügen, der speziell auf diese Entwicklungsumgebung ausgerichtet ist.
         * Üblicherweise wird eine `dev`-Verzweigung erstellt, damit die für die Entwicklungsumgebung vorgenommenen Änderungen wieder problemlos in die `main`-Verzweigung zurückgeführt werden können, die in der Produktionsumgebung bereitgestellt werden soll.
      1. Pipeline: Das Frontend-Team muss über eine Frontend-Pipeline verfügen, die in der Entwicklungsumgebung bereitgestellt wird. Diese Pipeline stellt das Frontend-Modul bereit, das sich normalerweise in der `dev`-Verzweigung befindet, wie im vorherigen Punkt beschrieben.
1. Das Frontend-Team sorgt dann dafür, dass der CSS- und JS-Code sowohl mit der alten als auch mit der neuen Ausgabe funktioniert.
   1. Wie üblich zur lokalen Entwicklung:
      1. Der Befehl `npx aem-site-theme-builder proxy`, der innerhalb des Frontend-Moduls ausgeführt wird, startet einen Proxy-Server, der den Inhalt von einer AEM-Umgebung anfordert, während die CSS- und JS-Dateien des Frontend-Moduls durch die Dateien des lokalen Ordners `dist` ersetzt werden.
      1. Wenn Sie die Variable `AEM_URL` in der ausgeblendeten Datei `.env` konfigurieren, können Sie kontrollieren, von welcher AEM-Umgebung der lokale Proxy-Server den Inhalt verwendet.
      1. Das Ändern des Werts `AEM_URL` ermöglicht daher den Wechsel zwischen der Produktions- und Entwicklungsumgebung, um CSS und JS so anzupassen, dass sie zu beiden Umgebungen passen.
      1. Dies muss mit der Entwicklungsumgebung, die die neue Ausgabe rendert, und mit der Produktionsumgebung funktionieren, die die alte Ausgabe rendert.
   1. Die Frontend-Arbeit ist abgeschlossen, wenn das aktualisierte Frontend-Modul für beide Umgebungen funktioniert und bereitgestellt wird.
1. Das Backend-Team kann dann die Produktionsumgebung aktualisieren, indem es den Code bereitstellt, der die neue HTML- und/oder JSON-Ausgabe über die Full-Stack-Pipeline rendert.
1. Das Frontend-Team kann dann seine CSS- und JS-Dateien bereinigen und das entfernen, was nur von der alten Ausgabe benötigt wurde, und dieses letzte Update über die Frontend-Pipeline in der Produktion bereitstellen.

## Zusätzliche Ressourcen {#additional-resources}

* [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) - Erfahren Sie, wie AEM-Site-Designs verwendet werden können, um den Stil und das Design Ihrer Site anzupassen.
* [AEM-Site-Design-Builder](https://github.com/adobe/aem-site-theme-builder): Adobe bietet einen AEM-Site-Design-Builder als Skriptsatz zum Erstellen neuer Site-Designs.
