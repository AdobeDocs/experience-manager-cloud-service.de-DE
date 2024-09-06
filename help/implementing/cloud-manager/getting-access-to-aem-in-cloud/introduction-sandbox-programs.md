---
title: Einführung in Sandbox-Programme
description: Erfahren Sie, was Sandbox-Programme sind und wie sie sich von Produktionsprogrammen unterscheiden.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 17306cf0877513d1412ffba311bd5d601edec062
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 37%

---


# Einführung in Sandbox-Programme {#sandbox-programs}

Erfahren Sie, was Sandbox-Programme sind und wie sie sich von Produktionsprogrammen unterscheiden.

## Einführung {#introduction}

Sandboxes werden normalerweise für Schulungen, Ausführung von Demos, Aktivierungen oder Proof of Concepts (POCs) erstellt. Sie sind nicht dazu gedacht, Live-Traffic zu übertragen.

Ein Sandbox-Programm ist eines der beiden in AEM Cloud Service verfügbaren Programmtypen, das andere ist ein [Produktionsprogramm](introduction-production-programs.md). Weitere Informationen zu Programmtypen finden Sie unter [Grundlegendes zu Programmen und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) .

## Automatische Erstellung {#auto-creation}

Sandbox-Programme ermöglichen die automatische Erstellung. Wenn Sie [ ein Sandbox-Programm ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) erstellen, wird Cloud Manager automatisch:

* Fügt AEM Sites, Assets und Edge Delivery Services als Standardlösungen zu Ihrem Programm hinzu.

  ![Lösungen und Add-ons für eine Sandbox auswählen](assets/sandbox-solutions-add-ons.png)

* Richten Sie ein Projekt-Git-Repository mit einem Beispielprojekt ein, das auf dem [AEM Projektarchetyp](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/overview) basiert.
* Eine Entwicklungsumgebung wird erstellt.
* Eine Nicht-Produktions-Pipeline, die in der Entwicklungsumgebung bereitgestellt wird, wird erstellt.

Ein Sandbox-Programm hat nur eine Entwicklungsumgebung.

## Einschränkungen und Bedingungen {#limitations}

Da Sandbox-Programme nicht für Live-Traffic vorgesehen sind, haben sie bestimmte Einschränkungen und Bedingungen für ihre Verwendung, wodurch sie von Produktionsprogrammen unterschieden werden.

| Begrenzung/Bedingung | Beschreibung |
| --- | --- |
| Kein Live-Traffic | Sandbox-Programme sind nicht für den Live-Traffic vorgesehen und unterliegen daher nicht den [AEM as a Cloud Service-Verpflichtungen](https://www.adobe.com/legal/service-commitments.html). |
| Keine automatische Skalierung | Die in einer Sandbox erstellten Umgebungen sind nicht für automatische Skalierung konfiguriert. Daher sind diese Umgebungen nicht für Leistungs- oder Belastungstests geeignet. |
| Keine benutzerdefinierten Domänen oder IP-Zulassungslisten | [Benutzerdefinierte Domänen](/help/implementing/cloud-manager/custom-domain-names/introduction.md) und [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) sind in Sandbox-Programmen nicht verfügbar. |
| Keine weiteren Veröffentlichungsbereiche | [Zusätzliche Veröffentlichungsregionen](/help/operations/additional-publish-regions.md) sind in Sandbox-Programmen nicht verfügbar. |
| Kein SLA von 99,99 % | Das [SLA von 99,99 %](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) gilt nicht für Sandbox-Programme. |
| Keine erweiterten Netzwerkfunktionen | [Erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) (z. B. Self-Service-Bereitstellung von VPN, nicht standardmäßigen Ports und dedizierten Ausgangs-IP-Adressen) sind in Sandbox-Programmen nicht verfügbar. |
| Keine automatischen AEM | AEM-Updates werden nicht automatisch an Sandbox-Programme gesendet, können aber manuell auf die Umgebungen in Ihrem Sandbox-Programm angewendet werden.<br> ・ Eine manuelle Aktualisierung kann nur ausgeführt werden, wenn die Zielumgebung über eine ordnungsgemäß konfigurierte Pipeline verfügt.<br> ・ Ein manuelles Update einer Produktions- oder Staging-Umgebung aktualisiert die andere automatisch. Der Satz aus Produktions- und Staging-Umgebung muss sich in derselben AEM-Version befinden.Weitere Informationen finden Sie unter [AEM Versionsaktualisierungen](/help/implementing/deploying/aem-version-updates.md) .<br><br>Informationen zum Aktualisieren einer Umgebung finden Sie unter [Aktualisieren der Umgebung](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) . |
| Keine technische Unterstützung | Da ein Sandbox-Programm normalerweise für Schulungen, laufende Demos, Aktivierungen oder POCs (Machbarkeitsstudien) erstellt wird, steht kein technischer Support für Probleme mit Sandbox-Programmen zur Verfügung.<br>Wenn beim Erstellen und Verwalten von Sandbox-Programmen Probleme auftreten, fallen diese Probleme unter den technischen Support. |
| Ruhezustand und Löschen | Umgebungen in einem Sandbox-Programm werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt. Sandbox-Umgebungen werden nach sechsmonatigem kontinuierlichem Ruhezustand gelöscht.<br>Weitere Informationen zum Deaktivieren des Ruhezustands von Umgebungen und zum automatischen Löschen von Sandboxes finden Sie unter [Ruhezustand und Aufheben des Ruhezustands von Sandbox-Umgebungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md) . |
