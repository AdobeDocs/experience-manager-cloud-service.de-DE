---
title: Kaskadierende Dropdown-Liste
description: Verwenden Sie adaptive Formularausdrücke, um automatische Überprüfung und Berechnung hinzuzufügen sowie die Sichtbarkeit eines Abschnitts zu aktivieren oder zu deaktivieren.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: cc3cd74ad87f4213a200f36745ab3d335edca02d
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 100%

---

# Anwendungsfall – Beschreibung

Beim Erstellen von Formularen oder Anwendungen ist es oft nützlich, Benutzende strukturiert durch die Standortauswahl zu führen. Eine kaskadierende Dropdown-Liste gestaltet dies einfach und benutzerfreundlich. Die Person wählt zunächst ein Land aus, wodurch die Liste nach verfügbaren Regionen/Provinzen gefiltert wird, und nimmt dann eine endgültige Auswahl von Städten basierend auf der Region vor. Dieser Ansatz sorgt nicht nur für eine sauberere Gestaltung der Formulare, sondern verhindert auch ungültige Kombinationen (z. B. die Auswahl einer Stadt, die in einer gewählten Region nicht existiert).

Für diesen Anwendungsfall sind die folgenden Schritte erforderlich

- Erstellen einer API-Integration
- Erstellen eines Formulars mit Feldern zur Erfassung von Land/Region/Stadt
- Erstellen einer Regel zum Befüllen der Dropdown-Listen mithilfe der API-Integration