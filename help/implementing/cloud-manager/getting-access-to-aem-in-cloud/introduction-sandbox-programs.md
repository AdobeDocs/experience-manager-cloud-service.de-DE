---
title: 'Einführung in Sandbox-Programme '
description: Erfahren Sie, welche Sandbox-Programme sich von Produktionsprogrammen unterscheiden.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: b74a0dbb1c9fdb74941f7b71bed9215853b63666
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 14%

---


# Einführung in Sandbox-Programme {#sandbox-programs}

Erfahren Sie, welche Sandbox-Programme sich von Produktionsprogrammen unterscheiden.

## Einführung {#introduction}

Sandbox-Programme werden normalerweise für Schulungen, laufende Demos, Aktivierungen oder Machbarkeitsstudien (POCs) erstellt und sind daher nicht für den Live-Traffic vorgesehen.

Ein Sandbox-Programm ist eines der beiden in AEM Cloud Service verfügbaren Programmtypen, das andere ist ein [Produktionsprogramm.](introduction-production-programs.md) Weitere Informationen finden Sie im Dokument . [Grundlegendes zu Programmen und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) , um mehr über Programmtypen zu erfahren.

## Automatische Erstellung {#auto-creation}

Sandbox-Programme ermöglichen die automatische Erstellung. Bei der automatischen Erstellung eines neuen Sandbox-Programms stellt Cloud Manager Folgendes sicher:

* Fügt AEM Sites und AEM Assets als Lösungen in Ihrem Programm hinzu.
* Richten Sie ein Projekt-Git-Repository mit einem Beispielprojekt ein, das auf dem [AEM Projektarchetyp.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)
* Erstellt eine Entwicklungsumgebung.
* Erstellt eine Nicht-Produktions-Pipeline, die in der Entwicklungsumgebung bereitgestellt wird.

Ein Sandbox-Programm hat nur eine Entwicklungsumgebung.

## Einschränkungen und Bedingungen {#limitations}

Da Sandbox-Programme nicht für Live-Traffic vorgesehen sind, haben sie bestimmte Einschränkungen und Bedingungen für ihre Verwendung, die sie von Produktionsprogrammen unterscheiden.

### Kein Live-Traffic {#live-traffic}

Sandbox-Programme sind nicht dazu bestimmt, Live-Traffic zu übertragen, und unterliegen daher nicht dem [AEM as a Cloud Service Verpflichtungen.](https://www.adobe.com/legal/service-commitments.html)

### Keine automatische Skalierung {#auto-scaling}

In einem Sandbox-Programm erstellte Umgebungen sind nicht für die automatische Skalierung konfiguriert. Daher sind diese Umgebungen nicht für Leistungs- oder Belastungstests geeignet.

### Keine benutzerdefinierten Domänen oder IP-Zulassungslisten {#ip-allow}

Benutzerdefinierte Domänen und IP-Zulassungslisten sind in Sandbox-Programmen nicht verfügbar.

### Manuelle AEM {#updates}

AEM Aktualisierungen werden nicht automatisch an Sandbox-Programme gesendet, können aber manuell auf die Umgebungen in Ihrem Sandbox-Programm angewendet werden.

* Ein manuelles Update ist nur möglich, wenn die Zielumgebung über eine ordnungsgemäß konfigurierte Pipeline verfügt.
* Durch manuelles Update einer Produktions- oder Staging-Umgebung wird die andere automatisch aktualisiert. Der Satz aus Produktions- und Staging-Umgebung muss sich in derselben AEM-Version befinden.

Weitere Informationen finden Sie im Dokument . [AEM](/help/implementing/deploying/aem-version-updates.md) für weitere Details.

Weitere Informationen finden Sie im Dokument . [Umgebung aktualisieren](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) , um zu erfahren, wie Sie eine Umgebung aktualisieren.

### Ruhezustand und Löschung {#hibernation}

Umgebungen in einem Sandbox-Programm werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt. Nach dem Ruhezustand können sie manuell deaktiviert werden.

Sandbox-Programme werden nach 6 Monaten, nachdem sie sich im kontinuierlichen Ruhezustand befinden, gelöscht. Danach können sie neu erstellt werden.

Siehe [Ruhezustand und Deaktivieren des Ruhezustands von Sandbox-Umgebungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md) für weitere Details.
