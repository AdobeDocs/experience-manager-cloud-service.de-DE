---
title: Umfasst Multi-Site-Management
description: Erfahren Sie Best Practice-Empfehlungen dazu, wie Sie ein Projekt mit mehrsprachigen Sites einrichten, wobei Sie eine einzige Codebasis auf eine replizierte Weise nutzen.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 02957fb8671d953a683ebd6e168979b11ad391c4
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Umfasst Multi-Site-Management {#repoless-msm}

In diesem Dokument wird davon ausgegangen, dass Sie bereits eine Basis-Site mit dem Namen `my-aem-site` für Ihr Projekt erstellt haben und diese mithilfe AEM MSM-Funktion lokalisieren möchten.

Wenn Sie Ihr Projekt bereits für das Anwendungsbeispiel &quot;Antworten&quot;eingerichtet haben, wird die Cloud-Konfiguration auf der Ebene der Stammseite &quot;`/content/my-aem-site`&quot;zugewiesen. Bei mehrsprachigen Sites muss diese Konfigurationszuweisung in den Sprachstamm wie `/content/my-aem-site/language-master/de` geändert werden.

