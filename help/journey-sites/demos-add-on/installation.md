---
title: Grundlegendes zur Installation des Referenz-Demo-Add-ons
description: Erfahren Sie mehr über Cloud Manager und dessen Verwendung für die Installation des Add-ons.
exl-id: 9418aac6-a8c4-43f7-b329-b02149fe2d53
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---

# Grundlegendes zur Installation des Referenz-Demo-Add-ons {#understand-installation}

Erfahren Sie mehr über Cloud Manager und dessen Verwendung für die Installation des Add-ons.

>[!TIP]
>
>Wenn Sie bereits mit Cloud Manager vertraut sind oder direkt zur Konfiguration und Verwendung des Add-ons springen möchten, können Sie zu [Erstellen eines Programms und einer Pipeline](create-program.md)
>
>Wenn Sie erfahren möchten, wie Cloud Manager und AEM beim Erstellen Ihrer Demoumgebungen zusammenarbeiten und wie Sie Ihre eigene Umgebung einrichten und verwenden, lesen Sie bitte weiterhin das aktuelle Dokument.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie der Installationsprozess des Referenz-Demos-Add-ons funktioniert, und wie die verschiedenen Teile zusammenarbeiten. Nach dem Lesen sollten Sie:

* Sie verfügen über grundlegende Kenntnisse zu Cloud Manager.
* Erfahren Sie, wie Pipelines Inhalte und Konfigurationen für AEM bereitstellen.
* Erfahren Sie, wie mit Vorlagen neue Sites erstellt werden können, die mit Demoinhalten vorbelegt sind, aber nur wenige Klicks erfordern.

Dieses Dokument konzentriert sich auf das Verständnis dieser grundlegenden Bestandteile des AEM Referenz-Demo-Add-ons, bevor Sie mit dem nächsten Schritt der Journey fortfahren, in dem Sie mit der Installation beginnen.

Es wird zwar empfohlen, diese Journey Schritt für Schritt durchzuführen. Wenn Sie bereits mit Cloud Manager vertraut sind oder direkt zur Konfiguration und Verwendung des Add-ons wechseln möchten, können Sie zu [Erstellen eines Programms und einer Pipeline](create-program.md)

## Verantwortliche Rolle {#responsible-role}

Diese Journey gilt für einen Systemadministrator, der Mitglied der **Business Owner** Rolle in Cloud Manager für Ihr Unternehmen.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Es gibt nur minimale Anforderungen, um mehr über das Referenz-Demos-Add-On zu erfahren und damit zu beginnen.

### Kenntnisse {#knowledge}

* Grundlegendes zu Cloud Manager

### Tools {#tools}

* Seien Sie Mitglied von **Business Owner** Rolle in Cloud Manager für Ihre Organisation

## Grundlegendes zu Cloud Manager {#cloud-manager}

Cloud Manager ist eine wesentliche Komponente AEM as a Cloud Service und dient als zentraler Einstiegspunkt für die Plattform.

Cloud Manager wird verwendet, um die Cloud-Ressourcen zu verwalten, die Ihre AEM-Projekte unterstützen, einschließlich der erforderlichen Umgebungen und Tools. Für diese Journey ist kein vollständiges Verständnis von Cloud Manager erforderlich. Sie müssen jedoch einige grundlegende Konzepte kennen.

>[!TIP]
>
>Ausführliche Informationen zu Cloud Manager finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) für Links zu weiteren Informationen.

### Programme {#programs}

Wenn Sie sich bei Cloud Manager anmelden, haben Sie Zugriff auf eine oder mehrere **Programme**. Ein Programm kann auf viele verschiedene Arten definiert werden, es ist jedoch am einfachsten, davon auszugehen, dass es mit den Sites und Erlebnissen verknüpft ist, die mit einer Markenidentität verknüpft sind.

Wenn Sie sich bei Cloud Manager anmelden und **WKND Travel and Adventure Enterprises**, können Sie eine **WKND Nightlife** und **WKND-Hinterhofprojekte** Programm. Beide Programme verfügen über AEM Umgebungen für die Verwaltung der zugehörigen Sites.

### Sandboxes {#sandboxes}

Programme können entweder Produktionsprogramme oder Sandbox-Programme sein.

* **Ein Produktionsprogramm** wird erstellt, um schließlich Live-Traffic zuzulassen, wenn Ihr Programm bereit zur Live-Schaltung ist.
* **Sandbox-Programm** wird für Schulung, laufende Demos, Aktivierung, POCs usw. erstellt. und ist nicht für Live-Traffic vorgesehen.

Um das AEM Referenz-Demos-Add-On zu installieren, müssen Sie ein neues Sandbox-Programm erstellen.

>[!NOTE]
>
>Das AEM Referenz-Demos-Add-On ist nur in Sandbox-Programmen verfügbar.

## Installation und Nutzungsablauf {#installation-flow}

Nachdem Sie nun einige grundlegende Konzepte von Cloud Manager kennen, ist die Installation des AEM Referenz-Demos-Add-ons konzeptionell einfach.

1. Melden Sie sich bei Cloud Manager an.
1. Erstellen Sie ein neues Sandbox-AEM-Programm und aktivieren Sie das AEM Referenz-Demos-Add-On als Option für das Programm.
1. Der Demoinhalt und die Konfiguration werden im Programm bereitgestellt. Der Demoinhalt enthält:
   * Site-Vorlagen, die zur Erstellung verschiedener AEM-Sites mithilfe von Funktionen von AEM verwendet werden und vorab mit Best Practices-Beispielen gefüllt werden.
   * Konfigurationstools zur Verwaltung Ihres Demoinhalts.
1. Melden Sie sich bei AEM in Ihrem neuen Sandbox-Programm an, verwenden Sie das Tool zur schnellen Site-Erstellung und erstellen Sie Demosites basierend auf den Vorlagen.
1. Verwenden Sie die Konfigurationstools, um diese Demo-Sites und -Vorlagen zu verwalten und sie zu löschen, wenn sie nicht mehr benötigt werden.

## AEM Site-Vorlagen {#site-templates}

AEM Site-Vorlagen sind Pakete, die vordefinierten Inhalt und eine vordefinierte Struktur für eine Site enthalten. Site-Vorlagen können an die Anforderungen bestimmter Projekte angepasst werden. Wenn AEM Administratoren neue Sites erstellen, können sie aus Vorlagen auswählen, die für ihre Geschäftsfälle gelten.

Das AEM Referenz-Demos-Add-On enthält mehrere Vorlagen für verschiedene Test- und Demonstrationsanforderungen. Nachdem Sie Ihr Programm erstellt und die Pipeline bereitgestellt haben, um das Add-on zu installieren, können Sie sich bei AEM anmelden und Sites basierend auf vielen Demovorlagen erstellen

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der AEM Referenz-Demos-Add-On-Journey abgeschlossen haben, sollten Sie Folgendes tun:

* Sie verfügen über grundlegende Kenntnisse zu Cloud Manager.
* Erfahren Sie, wie Pipelines Inhalte und Konfigurationen für AEM bereitstellen.
* Erfahren Sie, wie mit Vorlagen neue Sites erstellt werden können, die mit Demoinhalten vorbelegt sind, aber nur wenige Klicks erfordern.

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit der Journey zur AEM SchnellSite-Erstellung fort, indem Sie das Dokument erneut überprüfen. [Erstellen eines Programms und einer Pipeline,](create-program.md) Hier erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zur Schnellseitenerstellung zu wechseln, indem Sie das Dokument lesen [Erstellen eines Programms und einer Pipeline,](create-program.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [Grundlegendes zu Programmen und Programmtypen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/understand-program-types.html) - Hier erfahren Sie mehr über die Unterschiede zwischen Live- und Sandbox-Programmen.
* [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) - Wenn Sie mehr über die Struktur von Site-Vorlagen und deren Verwendung zur Erstellung von Sites erfahren möchten, lesen Sie dieses Dokument.
* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Wenn Sie weitere Details zu den Funktionen von Cloud Manager wünschen, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
