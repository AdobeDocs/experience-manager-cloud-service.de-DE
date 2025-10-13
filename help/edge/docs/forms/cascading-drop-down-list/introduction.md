---
title: Kaskadierende Dropdown-Liste
description: Verwenden der API-Integration zum dynamischen Befüllen der Dropdown-Liste
feature: Edge Delivery Services
role: User,Developer
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: ht
source-wordcount: '125'
ht-degree: 100%

---

# Anwendungsfall – Beschreibung

Beim Erstellen von Formularen oder Anwendungen ist es oft nützlich, Benutzende strukturiert durch die Standortauswahl zu führen. Eine kaskadierende Dropdown-Liste gestaltet dies einfach und benutzerfreundlich. Die Person wählt zunächst ein Land aus, wodurch die Liste nach verfügbaren Regionen/Provinzen gefiltert wird, und nimmt dann eine endgültige Auswahl von Städten basierend auf der Region vor. Dieser Ansatz sorgt nicht nur für eine sauberere Gestaltung der Formulare, sondern verhindert auch ungültige Kombinationen (z. B. die Auswahl einer Stadt, die in einer gewählten Region nicht existiert).

Für diesen Anwendungsfall sind die folgenden Schritte erforderlich

- Erstellen einer API-Integration
- Erstellen eines Formulars mit Feldern zur Erfassung von Land/Region/Stadt
- Erstellen einer Regel zum Befüllen der Dropdown-Listen mithilfe der API-Integration