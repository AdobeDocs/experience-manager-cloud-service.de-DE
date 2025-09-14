---
title: Kaskadierende Dropdown-Liste
description: Verwenden der API-Integration zum dynamischen Füllen der Dropdown-Liste
feature: Edge Delivery Services
role: User,Developer
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 4%

---

# Anwendungsfall – Beschreibung

Beim Erstellen von Formularen oder Anwendungen ist es oft nützlich, Benutzende strukturiert durch die Standortauswahl zu führen. Eine kaskadierende Dropdown-Liste macht dies einfach und benutzerfreundlich: Der Benutzer wählt zunächst ein Land aus, das die Liste der verfügbaren Bundesstaaten/Provinzen filtert, und dann eine endgültige Auswahl von Städten basierend auf dem Bundesland. Dieser Ansatz sorgt nicht nur für eine sauberere Gestaltung der Formulare, sondern verhindert auch ungültige Kombinationen (z. B. die Auswahl einer Stadt, die in einem gewählten Status nicht existiert).

Für diesen Anwendungsfall sind die folgenden Schritte erforderlich

- API-Integration erstellen
- Formular mit Feldern zur Erfassung von Land/Staat/Stadt erstellen
- Erstellen einer Regel, um die Dropdown-Listen mithilfe der API-Integration zu füllen