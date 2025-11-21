---
title: Governance Agent - Übersicht
description: Erfahren Sie, wie der AEM Governance Agent die Markenintegrität und -konformität in AEM schützt
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 9b26cd1f30ad6fa23e28c9f36fe48091e069962e
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Governance Agent - Übersicht {#governance-agent}

Der **Governance Agent** ist eine Lösung, mit der die Markenintegrität und -konformität in Adobe Experience Manager sichergestellt werden soll. Sie erzwingt Sicherheits-, Regulierungs- und Markenrichtlinien, um sicherzustellen, dass jede Interaktion und Aktivierung den etablierten Standards entspricht. Der Governance Agent ist vollständig in den KI-Assistenten integriert und für einen nahtlosen Betrieb in Unternehmensumgebungen konzipiert, indem die Tools **A2A (Agent-zu-Agent)** und **MCP (Model Control Protocol)** genutzt werden. Diese Integrationen ermöglichen es dem Agenten, eine Verbindung mit erweiterten KI-Orchestrierern wie ChatGPT, Claude und anderen externen KI-Systemen herzustellen und so eine flexible und skalierbare Intelligenz über Plattformen hinweg sicherzustellen.

Zu den wichtigsten Funktionen gehören:

* **Markenverwaltung:** Sie die Markenkonsistenz und reduzieren Sie die manuelle Überprüfung durch die Automatisierung von Markenüberprüfungen für Inhalte und Assets
* **Berechtigungen und Digital Rights Management (DRM):** Gewährleistet eine sichere und konforme Zusammenarbeit durch die Kontrolle von Berechtigungen und Nutzungsrechten für digitale Assets.

Durch die Kombination dieser Funktionen reduziert der Governance Agent Risiken und ermöglicht eine skalierte schnelle, sichere und markeninterne Bereitstellung.

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Kenntnisse im AEM Governance Agent {#skills-in-aem-governance-agent}

### Marken-Governance {#brand-governance}

Der Governance-Agent kann Inhalte anhand von Markenrichtlinien validieren, um die Konsistenz über alle digitalen Erlebnisse hinweg sicherzustellen. Es verwendet vorab aufgenommene Markenregeln wie Ton, Behauptungen, Logo-Nutzung, Typografie und Bilder. Die Lösung arbeitet im Chat-, Editor- und Batch-Modus in Experience Hub in Echtzeit und eignet sich daher ideal für KI-generierte Inhalte, Site-Migrationen und die kurzbasierte Site-Erstellung.

![Übersicht über die Markenverwaltung](/help/ai-in-aem/agents/governance/assets/brand-governance.png)

**Eingabeaufforderungsbeispiele:**

* *Ist diese Seite mit meiner Marke abgestimmt?`https://www.website/en.html`*
* *Entspricht dies `https://www.website/en.html` den Richtlinien für Markenbotschaften?*
* *Überprüfen Sie, ob `https://www.website/homepage` den Markenrichtlinien entspricht*
* *Zeige mir meine Markenrichtlinien*

### Berechtigung und Digital Rights Management {#permission-and-digital-rights-management}

#### Berechtigungsverwaltung in Content Hub {#permission-management-in-content-hub}

In Content Hub stellt der Governance Agent sicher, dass nur die richtigen Personen zum richtigen Zeitpunkt auf die richtigen Assets zugreifen. Durch die Anwendung granularer, attributbasierter Steuerelemente und Verwendungsrechte schützt sie sensible Inhalte und ermöglicht gleichzeitig eine sichere Zusammenarbeit. Dies bedeutet weniger Compliance-Risiken, eine stärkere Markenintegrität und schnellere Workflows. Teams können Assets sicher freigeben und wiederverwenden, ohne sich über den unbefugten Zugriff oder Missbrauch Gedanken machen zu müssen. Dieses Gleichgewicht aus Sicherheit und Flexibilität führt zu einer höheren betrieblichen Effizienz und zu mehr Vertrauen im gesamten Unternehmen.

![Übersicht über die Berechtigungsverwaltung](/help/ai-in-aem/agents/governance/assets/permission-management.png)

**Eingabeaufforderungsbeispiele:**

* *Alle vorhandenen Content Hub ABAC-Regeln anzeigen.*
* *Erstellen Sie eine Regel, die der Gruppe „Marketing“ Zugriff auf alle Assets gewährt.*
* *Gewähren Sie der Vertriebsgruppe Zugriff auf Assets, bei denen Marketing :segment EMEA entspricht.*
* *Löschen Sie alle Regeln, die externen Agenturen Zugriff gewähren*
* *Was ist ABAC in Content Hub und was können Sie mir helfen?*

#### Assets Digital Rights Management {#assets-digital-rights-management}

Mit dem Agenten können Sie Ihre digitalen Assets-Rechte in Ihrem gesamten Content-Ökosystem verwalten. Es steuert Berechtigungen und Nutzungsrechte auf einer granularen Ebene und stellt sicher, dass Assets nur innerhalb definierter Compliance-Grenzen aufgerufen und verwendet werden. So können Sie beruhigt sein, geistiges Eigentum schützen, regulatorische Risiken reduzieren und die Markenintegrität aufrechterhalten. Durch die Automatisierung der Durchsetzung von Rechten können Teams sicher und vertrauensvoll zusammenarbeiten und so die Inhaltsverteilung beschleunigen, ohne die Sicherheit oder Compliance zu beeinträchtigen.

![DRM-Management - Übersicht](/help/ai-in-aem/agents/governance/assets/drm-management.png)

**Eingabeaufforderungsbeispiele:**

* *Laufen einige meiner Assets bald aus?*
* *Finde alle Bike-Assets, die im letzten Monat abgelaufen sind.*
* *Welche Assets sind kürzlich abgelaufen?*
* *Finde ich Assets ohne Ablaufdatum*
* *Zeigen Sie mir alle Assets in /content/dam/products, die in den nächsten 14 Tagen ablaufen werden*

