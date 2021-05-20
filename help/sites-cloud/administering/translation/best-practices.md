---
title: Best Practices für die Übersetzung
description: Erfahren Sie mehr über Best Practices, die von Adobe-Engineering- und Beratungsteams zusammengestellt werden, um Sie bei der Einrichtung und Ausführung von Übersetzungsprojekten zu unterstützen.
feature: Sprachkopie
role: Administrator
exl-id: 51b98c24-5566-4088-9010-bd39841a1633
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 71%

---

# Best Practices für die Übersetzung {#translation-best-practices}

## Allgemein {#general}

Das Erstellen bzw. Erweitern einer globalen Webpräsenz kann ein komplexer Prozess sein, aber mit Voraussicht und Planung kann AEM Ihre Bemühungen vereinfachen und Ihre globalen Unternehmensziele unterstützen.

* **Planen Sie die globale** Erweiterung, bevor Sie Ihre erste Site implementieren. Es ist für gewöhnlich schwieriger, eine vorhandene Website für globale Abdeckung anzupassen, wenn die Website kurzfristig implementiert wurde, als wenn Sie von Anfang an auf eine globale Expansion hin planen:
   * Prüfen Sie den aktuellen Status der Lokalisierungsreife Ihrer Organisation. Stellen Sie fest, ob die **Tools**, **Prozesse** und **Ressourcen** vorhanden sind, um die globale Erweiterung zu unterstützen.
   * Achten Sie auf **globale Regulierungen** und **regionale Sprachpräferenzen**. Entwerfen Sie flexible Inhaltsstrukturen und -prozesse, die für eine in ständigem Wandel befindliche globale Geschäftsumgebung geeignet sind.
* Legen Sie ein **Governance**-Modell fest, das Ihr globales Unternehmen unterstützt, und verwenden Sie AEM Mechanismen wie MSM und Benutzerberechtigungen, um Ihr ausgewähltes Modell zu erzwingen. Ermitteln Sie beispielsweise, ob Inhalte zentral verfasst und in Regionen/Länder &quot;verschoben&quot;oder &quot;abgerufen&quot;werden. Legen Sie fest, welche Inhalte in Regionen entsperrt und geändert werden können. Legen Sie fest, wer für das Initiieren und Verwalten von Übersetzungen zuständig ist.
* Falls die Ressourcensituation es erlaubt, sollten Übersetzungsaktivitäten von einem zentralen Team verwaltet werden, das Fachwissen hinsichtlich der nötigen Tools, Prozesse und Lieferantenbeziehungen entwickeln kann.
* **Planen Sie**,  **** erstellen Sie Prototypen und  **** testen Sie Ihre globalen Strukturen und Prozesse, um sicherzustellen, dass sie das Unternehmen unterstützen und dass Sie die erforderliche Unterstützung von Interessengruppen in den Regionen erhalten.

## Site-Struktur  {#site-structure}

* Beginnen Sie den Entwurf der Site-Struktur mit der Untersuchung Ihrer Inhalte und stellen Sie fest, wo und in welcher Sprache Inhalte verfasst werden. Dieser Ort muss die höchste Ebene Ihrer Website darstellen.
* Bewährt und empfohlen ist eine **sprachbasierte Struktur** mit höchstens drei Ebenen zwischen den Autorenaktivitäten auf höchster Ebene und den landesspezifischen Websites.
* Verwenden Sie eine Sprache/Land-Site-Namenskonvention, die **[W3C-Standards entspricht.](/help/sites-cloud/authoring/fundamentals/accessible-content.md)**
* Legen Sie fest, wie Inhalte nach Regionen und Ländern verteilt werden. Berücksichtigen Sie Länder, in denen dieselbe Sprache gesprochen wird. Es wird empfohlen, Sprach-Master zu erstellen, eine Ebene nicht aktivierter Seiten, auf denen übersetzte Inhalte überprüft und geändert und dann an eine länderspezifische Website mit der jeweiligen Sprache verteilt oder von ihr abgerufen werden können.
* Zum Erstellen von Sprach-Mastern gibt es zwei Ansätze, einen mit Sprachkopien und einen mit MSM-/Live Copies.
   * Der Ansatz mit den Sprachkopien wird vom standardmäßigen Übersetzungsintegrations-Framework von AEM verwendet und stellt daher die einfachste Methode für den Anfang dar. Das Framework bietet eine Benutzeroberfläche, die es zunächst einfach macht, inhaltliche Änderungen vom Master der Hauptsprache an Sprach-Master weiterzugeben und zu übersetzen. Mit dem Wachstum des Projekts wird die Workflow-Automatisierung jedoch immer notwendiger für die Verwaltung der Übersetzung der steigenden Anzahl von Seiten und/oder Sprachen.
   * Der Ansatz mit MSM/Live Copies ist möglicherweise eine Alternative für fortgeschrittene Anwendungsfälle mit größeren, komplexeren Websites. Zur Verwaltung der komplexen Vererbungsverhältnisse zwischen der Hauptsprache und den Sprach-Mastern sowie zur Verringerung des Risikos, bestehende Übersetzungen zu überschreiben, sind starke Governance und effiziente Workflow-Automatisierung erforderlich. Diese Verwaltung ist mithilfe von Übersetzungs-Connectors möglich. Weitere Informationen finden Sie unter [MSM und mehrsprachige Sites](/help/sites-cloud/administering/msm/best-practices.md#msm-and-multilingual-websites) .
* Wenn bei der Master-Sprache globale Varianten vorliegen, ist eine Option, mit MSM eine Live Copy vom globalen Master zur Übersetzung zu erstellen. Wenn beispielsweise in einem Master in amerikanischem Englisch eine Bearbeitung durchgeführt wird, erstellen Sie einen Master in internationalem Englisch als Live Copy und Grundlage für die Übersetzung in andere Sprachen.
* Verwenden Sie MSM zur Erstellung von länderspezifischen Websites aus den übersetzten Sprach-Mastern und für den Rollout von Inhalten an Websites mit derselben Sprache. Beispielsweise kann der französische Sprach-Master an die Websites von Frankreich, Belgien und die Schweiz bereitgestellt werden.
* Planen Sie, erstellen Sie Prototypen und führen Sie Tests durch, bevor Sie die Implementierung beginnen.

## Übersetzungsprozesse und -methoden  {#translation-processes-and-methods}

* Engagieren Sie einen **Lokalisierungsdienstleister (LSP)** mit Erfahrung in der Übersetzung und damit verbundenen Lokalisierungstätigkeiten. Lokalisierungsdienstleister helfen bei der Skalierung Ihres globalen Unternehmens, indem sie ein Spektrum an Ressourcen und Technologien zur Verfügung stellen, welche die Effizienz verbessern und Übersetzungskosten sparen:
   * Einige Lokalisierungsdienstleister sind auch Technologieanbieter. Es gibt auch eigenständige Technologieanbieter, die vielen Lokalisierungsdienstleistern die Arbeit auf ihren Übersetzungsplattformen ermöglichen.
   * Das **AEM Translation Framework** unterstützt die Integration mit einer Vielzahl von Übersetzungstechnologieanbietern für maschinelle und menschliche Übersetzung.
   * Erfahren Sie, wie Sie [Connectors für Lokalisierungsdienstleister in Ihr AEM-System integrieren](integration-framework.md), um die Übersetzung von Inhalten zu automatisieren, bzw. wie Sie zum Testen oder in Fällen, wo kein Lokalisierungsdienstleister bzw. Übersetzungstechnologieanbieter vorhanden ist, Übersetzungsprojekte erstellen, exportieren und importieren.
* Wählen Sie eine **Übersetzungsmethode**, die dem Inhalt am besten entspricht.
   * **Menschliche** Übersetzungen eignen sich am besten für Inhalte, bei denen Messaging und Qualitätsanforderungen hoch sind und der Inhalt einige Zeit auf der Site live sein wird, z. B. Marketingseiten.
   * **Die maschinelle** Übersetzung kann eine gute Wahl für große Übersetzungsvolumen sein, wenn die Veröffentlichungszeit kritisch ist, die Qualitätsanforderungen entspannt sind oder die Kosten für die menschliche Übersetzung untragbar sind. Support-Wissensdatenbanken und benutzergenerierte Inhalte werden üblicherweise maschinell übersetzt.
* Nutzen Sie die Fachkenntnisse von Lokalisierungsdienstleistern, Adobe Consulting und Systemintegratoren zum Planen Ihrer multilingualen Site-Struktur sowie zum Erstellen von Prototypen und zum Testen davon.
