---
title: Einführung in Sandbox-Programme
description: Erfahren Sie, was Sandbox-Programme sind und wie sie sich von Produktionsprogrammen unterscheiden.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: ht
source-wordcount: '464'
ht-degree: 100%

---


# Einführung in Sandbox-Programme {#sandbox-programs}

Erfahren Sie, was Sandbox-Programme sind und wie sie sich von Produktionsprogrammen unterscheiden.

## Einführung {#introduction}

Sandboxes werden normalerweise für Schulungen, Ausführung von Demos, Aktivierungen oder Proof of Concepts (POCs) erstellt. Sie sind nicht dazu gedacht, Live-Traffic zu übertragen.

Ein Sandbox-Programm ist einer von zwei Programmtypen, die in AEM as a Cloud Service verfügbar sind; der andere ist ein [Produktionsprogramm.](introduction-production-programs.md) Weitere Informationen zu den Programmtypen finden Sie in den [Grundlagen zu Programmen und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

## Automatische Erstellung {#auto-creation}

Sandbox-Programme ermöglichen die automatische Erstellung. Bei der Erstellung eines Sandbox-Programms führt Cloud Manager Folgendes automatisch aus:

* AEM Sites und AEM Assets werden als Lösungen in Ihrem Programm hinzugefügt.
* Ein Projekt-Git-Repository mit einem Beispielprojekt, das auf dem [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) basiert, wird eingerichtet.
* Eine Entwicklungsumgebung wird erstellt.
* Eine Nicht-Produktions-Pipeline, die in der Entwicklungsumgebung bereitgestellt wird, wird erstellt.

Ein Sandbox-Programm hat nur eine Entwicklungsumgebung.

## Einschränkungen und Bedingungen {#limitations}

Da Sandbox-Programme nicht für Live-Traffic vorgesehen sind, haben sie bestimmte Einschränkungen und Bedingungen für ihre Verwendung, die sie von Produktionsprogrammen unterscheiden.

### Kein Live-Traffic {#live-traffic}

Sandbox-Programme sind nicht dazu bestimmt, Live-Traffic zu übertragen, und unterliegen daher nicht den [AEM as a Cloud Service-Verpflichtungen](https://www.adobe.com/legal/service-commitments.html).

### Keine automatische Skalierung {#auto-scaling}

Die in einer Sandbox erstellten Umgebungen sind nicht für automatische Skalierung konfiguriert. Daher sind diese Umgebungen nicht für Leistungs- oder Belastungstests geeignet.

### Keine benutzerdefinierten Domains oder IP-Zulassungslisten {#ip-allow}

Benutzerdefinierte Domains und IP-Zulassungslisten sind in Sandbox-Programmen nicht verfügbar.

### Keine erweiterten Netzwerkfunktionen {#advanced-networking}

[Erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) (z. B. Self-Service-Bereitstellung von VPN, nicht standardmäßigen Ports und dedizierten Ausgangs-IP-Adressen) sind in Sandbox-Programmen nicht verfügbar.

### Manuelle AEM-Updates {#updates}

AEM-Updates werden nicht automatisch an Sandbox-Programme gesendet, können aber manuell auf die Umgebungen in Ihrem Sandbox-Programm angewendet werden.

* Ein manuelles Update ist nur möglich, wenn die Zielumgebung über eine ordnungsgemäß konfigurierte Pipeline verfügt.
* Bei einem manuellen Update der Produktions- oder Staging-Umgebung wird jeweils automatisch auch die andere Umgebung aktualisiert. Der Satz aus Produktions- und Staging-Umgebung muss sich in derselben AEM-Version befinden.

Weitere Informationen finden Sie unter [AEM-Versionsaktualisierungen](/help/implementing/deploying/aem-version-updates.md).

Informationen zum Aktualisieren einer Umgebung finden Sie unter [Aktualisieren von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment).

### Ruhezustand und Löschung {#hibernation}

Umgebungen in einem Sandbox-Programm werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt. Sandbox-Umgebungen werden nach sechsmonatigem kontinuierlichem Ruhezustand gelöscht.

Weitere Informationen zum Deaktivieren des Ruhezustands von Umgebungen und zum automatischen Löschen von Sandboxes finden Sie unter [Aktivieren und Deaktivieren des Ruhezustands von Sandbox-Umgebungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md).

### Kein technischer Support {#no-support}

Da Sandbox-Programme normalerweise für Schulungen, Demos, Aktivierungen oder Machbarkeitsnachweise (Proof of Concepts, POCs) erstellt werden, steht kein technischer Support für Probleme mit Sandbox-Programmen zur Verfügung.

Wenn beim Erstellen und Verwalten von Sandbox-Programmen Probleme auftreten, ist dies weiterhin durch den technischen Support abgedeckt.
