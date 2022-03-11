---
title: Entwickeln von Sites mit der Frontend-Pipeline
description: Mit der Front-End-Pipeline erhalten Frontend-Entwickler mehr Unabhängigkeit, und der Entwicklungsprozess kann erheblich an Geschwindigkeit gewinnen.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 0%

---

# Entwickeln von Sites mit der Frontend-Pipeline {#developing-site-with-front-end-pipeline}

[Mit der Front-End-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) mehr Unabhängigkeit wird den Frontend-Entwicklern gegeben und der Entwicklungsprozess kann erheblich schneller werden. In diesem Dokument wird beschrieben, wie dieser Prozess funktioniert, sowie einige Überlegungen, die Sie beachten sollten, um das Potenzial dieses Prozesses voll auszuschöpfen.

>[!TIP]
>
>Wenn Sie noch nicht wissen, wie die Front-End-Pipeline verwendet werden kann und welche Vorteile sie bringen kann, finden Sie im Abschnitt [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) ein Beispiel dafür, wie Sie eine neue Site schnell bereitstellen und ihr Design vollständig unabhängig von der Backend-Entwicklung anpassen können.

## Einzelne Quelle der Wahrheit {#single-source-of-truth}

Eine allgemeine bewährte Praxis besteht darin, eine einzige Quelle der Wahrheit für das zu AEM bereitgestellte zu erhalten. Das Ziel von Cloud Manager besteht darin, diese einzige Quelle der Wahrheit deutlich zu machen. Da die Front-End-Pipeline jedoch die Entkopplung des Standorts für Teile des Codes ermöglicht, liegt eine zusätzliche Verantwortung in der korrekten Einrichtung der Front-End-Pipelines. Es muss darauf geachtet werden, dass nicht mehrere Frontend-Pipelines erstellt werden, die auf derselben Site in derselben Umgebung bereitgestellt werden.

Aus diesem Grund und insbesondere bei der Erstellung mehrerer Front-End-Pipelines wird empfohlen, eine systematische Benennungskonvention wie die folgende beizubehalten:

* Der Name des Front-End-Moduls, definiert durch die `name` -Eigenschaft der `package.json` sollte den Namen der Site enthalten, für die sie gilt. Beispiel: für eine Site unter `/content/wknd`, lautet der Name des Front-End-Moduls ungefähr `wknd-theme`.
* Wenn ein Frontend-Modul dasselbe Git-Repository mit anderen Modulen teilt, sollte der Name seines Ordners mit dem Namen des Front-End-Moduls übereinstimmen oder denselben Namen enthalten. Wenn beispielsweise das Front-End-Modul `wknd-theme`, würde der umschließende Ordnername ungefähr so aussehen: `wknd-theme-sources`.
* Der Name der Frontend-Pipeline von Cloud Manager sollte auch den Namen des Front-End-Moduls enthalten und auch die Umgebung hinzufügen, in der es bereitgestellt wird (Produktion oder Entwicklung). Beispielsweise für das Front-End-Modul mit dem Namen `wknd-theme`kann die Pipeline etwa wie folgt benannt werden: `wknd-theme-prod`.

Ein solches Übereinkommen sollte wirksam die folgenden Implementierungsfehler verhindern:

* Anwenden eines Front-End-Moduls auf die falsche Site
* Erstellen mehrerer Front-End-Module, die dieselbe Site anwenden und sich gegenseitig überschreiben
* Erstellen mehrerer Front-End-Pipelines für dieselben Quellen, was zu Race-Bedingungen führen kann, ohne die Reihenfolge der Implementierungen zu garantieren

## Problemtrennung {#separation-of-concerns}

Eine weitere bewährte Methode, die sich auf die Trennung von Anliegen bezieht, ist die besondere Sorgfalt bei der Gestaltung und der Verwaltung des Vertrags, der die Bedenken trennt. Bei der Frontend-Pipeline ist der Vertrag, der diesen Code vom Rest trennt, die von der Site gerenderte HTML und JSON. Wenn diese HTML und JSON stabil bleiben, liefert die Front-End-Pipeline ihren maximalen Wert, indem sie das Front-End-Team vollständig unabhängig macht.

Es gibt derzeit keine spezielle Funktion, um die Vollstapel-Pipeline synchron mit den Frontend-Pipeline(en) auszuführen. Aus diesem Grund muss bei der Entkopplung der Frontend-Entwicklung von der Vollstapelpipeline in den Vertrag, der diese beiden Problembereiche trennt, besondere Sorgfalt aufgenommen werden. Dieser Vertrag ist im Allgemeinen die HTML und/oder JSON, die der Experience Manager rendert. Änderungen an diesem Vertrag müssen daher zwischen den Teams, die die verschiedenen Pipelines betreiben, gut geplant werden, damit sie sich darauf einigen können, wie die entsprechenden Änderungen zu ordnen sind.

Die folgenden Schritte werden im Allgemeinen empfohlen, wenn es notwendig ist, Änderungen an der HTML- und/oder JSON-Ausgabe vorzunehmen, die beide Problembereiche betreffen.

1. Das Backend-Team richtet zunächst eine Entwicklungsumgebung mit der neuen HTML- und/oder JSON-Ausgabe ein.
   1. Über die Full-Stack-Pipeline stellen sie den Code bereit, der zum Rendern der gewünschten neuen HTML- und/oder JSON-Ausgabe erforderlich ist.
   1. Wenn dies eine Umgebung ist, auf die das Frontend-Team zuvor keinen Zugriff hatte, müssen die folgenden Schritte ausgeführt werden.
      1. URL: Das Frontend-Team muss die URL dieser Entwicklungsumgebung kennen.
      1. ACL: Dem Frontend-Team muss ein lokaler AEM-Benutzer mit ähnlichen Berechtigungen wie &quot;Mitwirkende&quot;zugewiesen werden.
      1. Git: Das Frontend-Team muss über einen separaten Git-Speicherort für das Frontend-Modul verfügen, der speziell auf diese Entwicklungsumgebung ausgerichtet ist.
         * Üblicherweise wird eine `dev` -Verzweigung, damit die für die Entwicklungsumgebung vorgenommenen Änderungen einfach wieder in die `main` -Verzweigung, die in der Produktionsumgebung bereitgestellt werden soll.
      1. Pipeline: Das Frontend-Team muss über eine Front-End-Pipeline verfügen, die in der Entwicklungsumgebung bereitgestellt wird. Diese Pipeline stellt das Front-End-Modul bereit, das sich normalerweise im `dev` -Verzweigung, wie im vorherigen Punkt beschrieben.
1. Das Frontend-Team sorgt dann dafür, dass der CSS- und JS-Code sowohl mit der alten als auch mit der neuen Ausgabe funktioniert.
   1. Wie üblich zur lokalen Entwicklung:
      1. Die `npx aem-site-theme-builder proxy` -Befehl, der innerhalb des Front-End-Moduls ausgeführt wird, startet einen Proxy-Server, der den Inhalt von einer AEM Umgebung anfordert, während die CSS- und JS-Dateien des Front-End-Moduls durch die Dateien des lokalen ersetzt werden `dist` Ordner.
      1. Konfigurieren der `AEM_URL` -Variable in der ausgeblendeten `.env` -Datei können steuern, von welcher AEM Umgebung der lokale Proxyserver den Inhalt verbraucht.
      1. Ändern des Werts `AEM_URL` ermöglicht daher den Wechsel zwischen der Produktions- und Entwicklungsumgebung, um CSS und JS so anzupassen, dass sie zu beiden Umgebungen passen.
      1. Es muss mit der Entwicklungsumgebung, die die neue Ausgabe rendert, und mit der Produktionsumgebung funktionieren, die die alte Ausgabe rendert.
   1. Die Frontend-Arbeit ist abgeschlossen, wenn das aktualisierte Frontend-Modul für beide Umgebungen funktioniert und für beide bereitgestellt wird.
1. Das Backend-Team kann dann die Produktionsumgebung aktualisieren, indem es den Code bereitstellt, der die neue HTML- und/oder JSON-Ausgabe über die Vollstapelpipeline rendert.
1. Das Front-End-Team kann dann seine CSS- und JS-Dateien bereinigen und entfernen, was nur von der alten Ausgabe benötigt wurde, und dieses letzte Update über die Front-End-Pipeline in der Produktion bereitstellen.

## Zusätzliche Ressourcen {#additional-resources}

* [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) - Erfahren Sie, wie AEM Site-Designs verwendet werden können, um den Stil und das Design Ihrer Site anzupassen.
* [AEM Site-Design-Builder](https://github.com/adobe/aem-site-theme-builder) - Adobe bietet einen AEM Site-Design-Builder als Satz von Skripten zum Erstellen neuer Site-Designs.
