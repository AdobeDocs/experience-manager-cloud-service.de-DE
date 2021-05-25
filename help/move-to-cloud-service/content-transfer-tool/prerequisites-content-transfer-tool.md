---
title: Voraussetzungen für das Content Transfer Tool
description: Voraussetzungen für das Content Transfer Tool
source-git-commit: c760b97cdb565244cf20f5193de3e3ebab1579ad
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---

# Voraussetzungen für das Content Transfer Tool {#prerequisites}

Die folgende Tabelle fasst die Voraussetzungen vor der Verwendung des Content Transfer Tool zusammen. Überprüfen Sie alle unten aufgeführten Aspekte:

| Besonderheiten | Derzeit unterstützte Funktionen |
|--- |--- |
| AEM-Version | Das Content Transfer Tool kann nur mit AEM 6.3 oder höheren Versionen ausgeführt werden. Um das Content Transfer Tool mit AEM 6.2 oder älteren Versionen verwenden zu können, ist eine ersetzende Aktualisierung des Inhalts-Repositorys auf AEM 6.5 erforderlich. Dazu ist es nicht erforderlich, den Code auf AEM 6.5 zu aktualisieren. |
| Größe des Segmentspeichers | Das Content Transfer Tool unterstützt derzeit bis zu 83 GB unter *Autor* und 31 GB unter *Publish*. |
| Gesamtgröße des Inhalts-Repositorys (Inhaltsspeicher + Datenspeicher) | Das Content Transfer Tool wurde entwickelt, um Inhalte bis zu 10 TB zu übertragen. Mehr als 10 TB werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, um Optionen für Inhalte zu besprechen, die größer als 10 TB sind. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool funktioniert nicht für die Migration des Inhalts in unveränderlichen Pfaden wie `“/etc”`. Weitere Informationen zur Repository-Umstrukturierung und zu Workflow-Modellen finden Sie unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) . |