---
title: Voraussetzungen für das Content Transfer Tool
description: Voraussetzungen für das Content Transfer Tool
source-git-commit: becb8368af8a8228bf3248bde66ad7164187a9c4
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 1%

---

# Voraussetzungen für das Content Transfer Tool {#prerequisites}

Die folgende Tabelle fasst die Voraussetzungen für die Verwendung des Content Transfer Tool zusammen.

Überprüfen Sie alle unten aufgeführten Aspekte:

| Besonderheiten | Derzeit unterstützte Funktionen |
|--- |--- |
| AEM-Version | Das Content Transfer Tool kann nur mit AEM 6.3 oder höheren Versionen ausgeführt werden. Um das Content Transfer Tool mit AEM 6.2 oder älteren Versionen verwenden zu können, ist eine ersetzende Aktualisierung des Inhalts-Repositorys auf AEM 6.5 erforderlich. Dazu ist es nicht erforderlich, den Code auf AEM 6.5 zu aktualisieren. |
| Größe des Segmentspeichers | Das Content Transfer Tool unterstützt derzeit bis zu 83 GB unter *Autor* und 31 GB unter *Publish*. |
| Gesamtgröße des Inhalts-Repositorys <br>*(Segmentspeicher + Datenspeicher)* | Das Content Transfer Tool wurde entwickelt, um Inhalte bis zu 10 TB zu übertragen. Mehr als 10 TB werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, um Optionen für Inhalte zu besprechen, die größer als 10 TB sind. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool kann nicht verwendet werden, um Inhalte in unveränderlichen Pfaden wie `“/etc”` zu migrieren. Es sind bestimmte `"/etc"` Pfade zulässig, die jedoch nur zur Unterstützung von [AEM Forms zu AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets) verwendet werden. Weitere Informationen zur Repository-Umstrukturierung finden Sie unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) . |

## Wie geht es weiter {#whats-next}

Nachdem Sie die Voraussetzungen geprüft und festgestellt haben, ob Sie das Content Transfer Tool in Ihrem Migrationsprojekt verwenden können, lesen Sie [Weitere Best Practices und Überlegungen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md) bei der Verwendung des Content Transfer Tool.
