---
title: Einrichten der Enterprise Team-Entwicklung - Cloud Services
description: Auf dieser Seite erfahren Sie mehr über die Einrichtung des Enterprise-Teams
translation-type: tm+mt
source-git-commit: ad72ea45681169551f5ce6801cec59d6c106b346
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 0%

---

# Enterprise Team Development Setup for AEM as Cloud Service {#enterprise-setup}

## Einführung {#introduction}

AEM als Cloud Service bietet ein Cloud-natives Angebot, das AEM als Dienst bereitstellt, ab 10 Jahren Unternehmenssoftware an Unternehmensteams mit deren spezifischen Anforderungen an. Obwohl es AEM in die Cloud-native Welt katapultiert, mit neuen Werten wie immer on, immer aktuell, immer sicher und immer im Maßstab, behält es das Hauptwertprinzip bei, das AEM unseren Kunden als anpassbare Plattform bietet und es Teams der Unternehmensklasse ermöglicht, sich in ihre Entwicklungs- und Versand-Verfahren zu integrieren.

Zur Unterstützung unserer Kunden mit Unternehmensentwicklungs-Setups integriert AEM als Cloud Service Cloud Manager vollständig in die speziell für die Unternehmensentwicklung konzipierten CI/CD-Pipelines, die mit Best Practices und Erfahrungen aus mehrjährigen Erfahrungen mit Unternehmensentwicklung und -bereitstellung ausgestattet sind. So werden gründliche Tests und höchste Codequalität gewährleistet, um außergewöhnliche Erlebnisse zu bieten.

## Unterstützung von Cloud Manager bei der Entwicklung von Unternehmensteams {#cloud-manager}

Um Kunden eine schnelle Onboarding-Arbeit zu ermöglichen, bietet Cloud Manager alles, was Sie für den sofortigen Einstieg in die Entwicklung von Erlebnissen benötigen, einschließlich eines Git-Repositorys zum Speichern von Anpassungen, die dann von Cloud Manager erstellt, überprüft und bereitgestellt werden.
Mithilfe von Cloud Manager können Entwicklungsteams häufig daran arbeiten, Änderungen zu übernehmen, ohne dabei auf Mitarbeiter der Adobe angewiesen zu sein.

In Cloud Manager stehen drei Umgebung zur Verfügung:

* Entwicklung
* Staging
* Produktion

Der Code kann in Entwicklungs-Umgebung mithilfe einer Nicht-Produktionspipeline bereitgestellt werden. Für Stage und Produktion, die immer zusammenpassen und so eine Validierung vor der Bereitstellung der Produktion als Best Practice sicherstellen, verwendet eine Produktions-Pipeline Qualitätsdaten, um den Anwendungscode und die Konfigurationsänderungen zu validieren.

Die Produktionsleitung stellt den Code und die Konfiguration zunächst für die Staging-Umgebung bereit, testet die Anwendung und stellt schließlich für die Produktion bereit.
Ein Cloud Service-SDK, das immer mit den neuesten Cloud Service-Verbesserungen aktualisiert wird, ermöglicht die lokale Entwicklung direkt mit der lokalen Hardware des Entwicklers. Dies ermöglicht eine schnelle Entwicklung mit sehr niedrigen Bearbeitungszeiten. So können Entwickler in ihrer vertrauten lokalen Umgebung bleiben und aus einer Vielzahl von Entwicklungstools wählen und auf Umgebung oder Produktionsabläufe drängen, wenn sie es für richtig halten.

Cloud Manager unterstützt flexible Multi-Team-Setups, die an die Anforderungen eines Unternehmens angepasst werden können. Dies gilt sowohl für Cloud Service als auch für AMS. Um stabile Bereitstellungen mit mehreren Teams sicherzustellen und zu vermeiden, dass ein Team die Produktion für alle Teams beeinflusst, validiert und testet die Cloud Manager-Pipeline den Code aller Teams zusammen.


## Real World Example {#real-world-example}

Jedes Unternehmen hat unterschiedliche Anforderungen, einschließlich der Einrichtung, der Prozesse und der Workflows. Das unten beschriebene Setup wird von der Adobe für mehrere Projekte verwendet, die Erlebnisse zusätzlich zu AEM als Cloud Service bereitstellen.

Beispielsweise enthalten die Adobe Creative Cloud-Anwendungen wie Adobe Photoshop oder Adobe Illustrator Inhaltsressourcen wie Tutorials, Beispiele und Leitfäden, die den Endbenutzern zur Verfügung stehen. Diese Inhalte werden von den Clientanwendungen verwendet, die AEM als Cloud Service auf eine *kopflose*-Weise verwenden, indem API-Aufrufe an die AEM Cloud-Veröffentlichungsstufe gesendet werden, um den strukturierten Inhalt als JSON-Streams abzurufen, und indem das AEM Cloud Service-CDN genutzt wird, um strukturierte und unstrukturierte Inhalte mit optimaler Leistung bereitzustellen.

Die an diesem Projekt beteiligten Teams folgen dem nachstehend beschriebenen Prozess.

>[!NOTE]
>Weitere Informationen zum Setup finden Sie unter [Arbeiten mit mehreren Quell-Git-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html#managing-code).

Jedes Team verwendet seinen eigenen Entwicklungsarbeitsablauf und verfügt über ein separates Git-Repository. Ein zusätzliches freigegebenes Git-Repository wird für die Überwachung von Projekten verwendet. Dieses Git-Repository enthält die Stammstruktur des Git-Repositorys von Cloud Manager einschließlich der Konfiguration des freigegebenen Dispatchers. Für die Inbetriebnahme eines neuen Projekts ist die Aufnahme in die Projektdatei des Reaktors Maven im Stammverzeichnis des gemeinsamen Git-Repositorys erforderlich. Für die Dispatcher-Konfiguration wird innerhalb des Dispatcher-Projekts eine neue Konfigurationsdatei erstellt. Diese Datei wird dann von der Hauptauslöserkonfiguration eingeschlossen. Jedes Team ist für seine eigene Dispatcher-Konfigurationsdatei verantwortlich. Änderungen am freigegebenen Git-Repository sind selten und in der Regel nur erforderlich, wenn ein neues Projekt an Bord ist. Die Hauptarbeit wird von jedem Projektteam im eigenen Git-Repository ausgeführt.

![](assets/team-setup1.png)

Das git Repository für jedes Team wurde mit dem AEM Maven Archetype eingerichtet und befolgt somit die Best Practices für die Einrichtung AEM Projekte. Die einzige Ausnahme ist die Verarbeitung der Dispatcher-Konfiguration, die wie oben beschrieben im freigegebenen Git-Repository durchgeführt wird.
Jedes Team verwendet einen vereinfachten Git-Arbeitsablauf mit zwei + N-Zweigen nach dem Git-Flussmodell:

* Eine Stable-Release-Verzweigung enthält den Produktionscode

* Eine Entwicklungsabteilung enthält die neueste Entwicklung

* Für jede Funktion wird eine neue Verzweigung erstellt


Die Entwicklung erfolgt in einem Funktionszweig, wenn die Funktion reif ist, wird sie in den Entwicklungszweig zusammengeführt. Abgeschlossene und validierte Funktionen werden aus dem Entwicklungszweig ausgewählt und in den stabilen Zweig zusammengeführt. Alle Änderungen werden durch Pull Requests (PR) vorgenommen. Jeder PR wird automatisch durch Qualitätstore validiert. Sonar wird zur Qualitätskontrolle des Codes verwendet und eine Reihe von Testsuiten werden ausgeführt, um sicherzustellen, dass der neue Code keine Regression einleitet.

Das Setup im Git-Repository von Cloud Manager besteht aus zwei Zweigen:

* Eine *Stable-Release-Verzweigung*, die den Produktionscode aller Teams enthält
* Eine *Entwicklungsabteilung*, die den Entwicklungscode aller Teams enthält

Jeder Push an das Git-Repository eines Teams in der Entwicklungs- oder stabilen Verzweigung löst eine [github-Aktion](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=en#managing-code) aus. Alle Projekte folgen dem gleichen Setup für den stabilen Zweig. Ein Push-Vorgang auf den stabilen Zweig eines Projekts wird automatisch an die stabile Zweigstelle im Git-Repository von Cloud Manager gesendet. Die Produktionsleitung in Cloud Manager ist so konfiguriert, dass sie durch einen Push an den stabilen Zweig ausgelöst wird. Die Produktionsleitung wird daher von jedem Push eines Teams in einen stabilen Zweig ausgeführt und die Produktionsbereitstellung wird aktualisiert, wenn alle Qualitätstore bestehen.

![](assets/team-setup2.png)

Schubsen in den Entwicklungszweig werden anders behandelt. Während ein Push an eine Entwicklerzweigung im Git-Repository eines Teams auch eine Git-Aktion auslöst und der Code automatisch in die Entwicklungsabteilung im Git-Repository von Cloud Manager verschoben wird, wird die Nicht-Produktion-Pipeline nicht automatisch durch den Code-Push ausgelöst. Sie wird durch einen Aufruf der API von Cloud Manager ausgelöst.
Das Ausführen der Produktionsleitung beinhaltet die Überprüfung des Codes aller Teams über die bereitgestellten Qualitätsgates. Sobald der Code für stage bereitgestellt wurde, werden die Tests und Prüfungen durchgeführt, um sicherzustellen, dass alles wie erwartet funktioniert. Sobald alle Tore übergeben sind, werden die Änderungen ohne Unterbrechung oder Ausfallzeiten in die Produktion übernommen.
Für die lokale Entwicklung wird das SDK für Cloud Service verwendet. Das SDK ermöglicht die Einrichtung eines lokalen Autors, Veröffentlichungs- und Dispatchers. Dies ermöglicht die Offline-Entwicklung und schnelle Bearbeitungszeiten. Manchmal wird nur der Autor für die Entwicklung verwendet, aber die schnelle Einrichtung des Dispatchers und der Veröffentlichung erlaubt es, alles lokal zu testen, bevor in das git-Repository gedrängt wird. Mitglieder der einzelnen Teams checken in der Regel den Code aus der freigegebenen Git sowie ihren eigenen Projektcode ein. Es besteht keine Notwendigkeit, andere Projekte auszuchecken, da die Projekte unabhängig sind.

![](assets/team-setup3.png)

Diese Einrichtung in der realen Welt kann als Entwurf verwendet und dann an die Bedürfnisse eines Unternehmens angepasst werden. Das flexible Verzweigungs- und Zusammenführungskonzept von git ermöglicht Variationen der oben genannten Workflows, die auf die Anforderungen jedes Teams zugeschnitten sind. AEM als Cloud Service unterstützt alle diese Varianten, ohne den Hauptwert der optimierten Cloud Manager-Pipeline zu opfern.

### Überlegungen zu einem Multi-Team-Setup {#considerations}

>[!NOTE]
>Für jedes Multi-Team-Setup ist es von entscheidender Bedeutung, ein Governance-Modell und eine Reihe von Standards festzulegen, die alle Teams einhalten müssen. Der oben skizzierte Entwurf für ein Multi-Team-Setup ermöglicht die Skalierung über eine größere Anzahl von Teams und Sie können diesen Entwurf als Ausgangspunkt verwenden.

Mit dem Git-Repository von Cloud Manager und der Produktions-Pipeline wird immer der gesamte Produktionscode durch alle Qualitätstore ausgeführt und als eine Bereitstellungseinheit behandelt. Auf diese Weise wird das Produktionssystem *immer auf* ohne Unterbrechung oder Ausfallzeiten gehalten.
Ohne ein solches System dagegen besteht die Gefahr, dass ein Update eines einzelnen Teams zu Problemen mit der Produktionsstabilität führen kann, da jedes Team separat bereitstellen kann. Darüber hinaus sind Koordination und geplante Ausfallzeiten erforderlich, um Updates bereitzustellen. Mit zunehmender Anzahl von Teams werden die Koordinierungsanstrengungen viel komplexer und schnell unkontrollierbar.

Wenn ein Problem in den Qualitätsräumen erkannt wird, ist die Produktion nicht betroffen, und das Problem kann ohne Adobe erkannt und behoben werden. Ohne Cloud Service und ohne immer die gesamte Bereitstellung zu testen, können partielle Bereitstellungen zu Ausfällen führen, die eine Rollback-Anforderung oder sogar eine vollständige Wiederherstellung aus einer Sicherung erfordern. Die partielle Prüfung kann auch zu anderen Problemen führen, die dann nach der erneuten Abstimmung und Unterstützung durch das Personal der Adobe behoben werden müssen.