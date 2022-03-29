---
title: Grundlegendes zur Installation des Reference Demos-Add-ons
description: Erfahren Sie mehr über Cloud Manager und dessen Verwendung für die Installation des Add-ons.
exl-id: 9418aac6-a8c4-43f7-b329-b02149fe2d53
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 100%

---

# Grundlegendes zur Installation des Reference Demos-Add-ons {#understand-installation}

Erfahren Sie mehr über Cloud Manager und dessen Verwendung für die Installation des Add-ons.

>[!TIP]
>
>Wenn Sie bereits mit Cloud Manager vertraut sind oder direkt zur Konfiguration und Verwendung des Add-ons springen möchten, können Sie zu [Erstellen eines Programms und einer Pipeline](create-program.md) wechseln.
>
>Wenn Sie erfahren möchten, wie Cloud Manager und AEM beim Erstellen Ihrer Demo-Umgebungen zusammenarbeiten und wie Sie Ihre eigene Umgebung einrichten und verwenden, lesen Sie bitte weiterhin das aktuelle Dokument.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie der Installationsprozess des Reference Demos-Add-ons funktioniert und wie die verschiedenen Teile zusammenarbeiten. Nach dem Lesen:

* Sollten Sie über grundlegende Kenntnisse zu Cloud Manager verfügen.
* Wissen Sie, wie Pipelines Inhalte und Konfigurationen für AEM bereitstellen.
* Wissen Sie, wie mit Vorlagen mit nur wenigen Klicks neue Sites erstellt werden können, die mit Demo-Inhalten gefüllt sind.

Dieses Dokument konzentriert sich auf das Verständnis dieser grundlegenden Bestandteile des AEM Reference Demos-Add-ons, bevor Sie mit dem nächsten Schritt der Journey fortfahren, in dem Sie mit der Installation beginnen.

Es wird zwar empfohlen, diese Journey Schritt für Schritt durchzuführen. Wenn Sie bereits mit Cloud Manager vertraut sind oder direkt zur Konfiguration und Verwendung des Add-ons springen möchten, können Sie aber zu [Erstellen eines Programms und einer Pipeline](create-program.md) wechseln.

## Verantwortliche Rolle {#responsible-role}

Diese Journey gilt für einen Systemadministrator, der Mitglied der Rolle eines **Unternehmensverantwortlichen** in Cloud Manager für Ihre Organisation ist.

## Anforderungen und Voraussetzungen {#requirements-prerequisites}

Es gibt nur minimale Anforderungen, um mehr über das Reference Demos-Add-on zu erfahren und mit dessen Nutzung zu beginnen.

### Kenntnisse {#knowledge}

* Grundlegende Kenntnisse zu Cloud Manager

### Tools {#tools}

* Sie müssen Mitglied des Rolle eines **Unternehmensverantwortlichen** in Cloud Manager für Ihre Organisation sein

## Grundlegendes zu Cloud Manager {#cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für die Plattform.

Cloud Manager wird verwendet, um die Cloud-Ressourcen zu verwalten, die Ihre AEM-Projekte unterstützen, einschließlich der erforderlichen Umgebungen und Tools. Für diese Journey sind keine vollständigen Kenntnisse zu Cloud Manager erforderlich. Sie müssen jedoch einige grundlegende Konzepte kennen.

>[!TIP]
>
>Wenn Sie mehr über Cloud Manager erfahren möchten, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) dieses Artikels Links zu weiteren Informationen.

### Programme {#programs}

Wenn Sie sich bei Cloud Manager anmelden, haben Sie Zugriff auf ein oder mehrere **Programme**. Ein Programm kann auf viele verschiedene Arten definiert werden, es ist jedoch am einfachsten, sich vorzustellen, dass es mit den Sites und Erlebnissen einer Markenidentität verknüpft ist.

Wenn Sie sich in Cloud Manager bei **WKND Travel and Adventure Enterprises** anmelden, können Sie die Programme **WKND Nightlife** und **WKND Backyard Projects** erstellen. Beide Programme verfügen über AEM-Umgebungen für die Verwaltung der zugehörigen Sites.

### Sandboxes {#sandboxes}

Programme können entweder Produktionsprogramme oder Sandbox-Programme sein.

* **Ein Produktionsprogramm** wird erstellt, um letztlich Livetraffic zu ermöglichen, wenn Ihr Programm bereit für die Live-Schaltung ist.
* **Ein Sandbox-Programm** wird für Schulung, laufende Demos, Aktivierung, POCs usw. erstellt. Es ist nicht für Livetraffic vorgesehen.

Um das AEM Reference Demos-Add-on zu installieren, müssen Sie ein neues Sandbox-Programm erstellen.

>[!NOTE]
>
>Das AEM Reference Demos-Add-on ist nur in Sandbox-Programmen verfügbar.

## Installation und Nutzungsablauf {#installation-flow}

Nachdem Sie nun einige grundlegende Konzepte von Cloud Manager kennen, ist die Installation des AEM Reference Demos-Add-ons konzeptionell einfach.

1. Melden Sie sich bei Cloud Manager an.
1. Erstellen Sie ein neues Sandbox-AEM-Programm und aktivieren Sie das AEM Reference Demos-Add-on als Option für das Programm.
1. Der Demo-Inhalt und die Konfiguration werden im Programm bereitgestellt. Der Demo-Inhalt enthält Folgendes:
   * Site-Vorlagen, die zur Erstellung verschiedener AEM-Sites mithilfe von Funktionen von AEM verwendet werden und vorab mit Best Practices-Beispielen gefüllt werden.
   * Konfigurations-Tools zur Verwaltung Ihres Demo-Inhalts.
1. Melden Sie sich bei AEM in Ihrem neuen Sandbox-Programm an, verwenden Sie das Tool zur schnellen Site-Erstellung und erstellen Sie Demo-Sites basierend auf den Vorlagen.
1. Verwenden Sie die Konfigurations-Tools, um diese Demo-Sites und -Vorlagen zu verwalten und sie zu löschen, wenn sie nicht mehr benötigt werden.

## AEM-Site-Vorlagen {#site-templates}

AEM-Site-Vorlagen sind Pakete, die vordefinierten Inhalt und eine vordefinierte Struktur für eine Site enthalten. Site-Vorlagen können an die Anforderungen bestimmter Projekte angepasst werden. Wenn AEM-Administratoren also neue Sites erstellen, können sie aus Vorlagen auswählen, die zu ihren Geschäftsszenarien passen.

Das AEM Reference Demos-Add-on enthält mehrere Vorlagen für verschiedene Test- und Demonstrationsanforderungen. Nachdem Sie Ihr Programm erstellt und die Pipeline bereitgestellt haben, um das Add-on zu installieren, können Sie sich bei AEM anmelden und Sites basierend auf vielen Demo-Vorlagen erstellen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Journey für das AEM Reference Demos-Add-on abgeschlossen haben, sollten Sie wie folgt vorgehen:

* Sollten Sie über grundlegende Kenntnisse zu Cloud Manager verfügen.
* Wissen Sie, wie Pipelines Inhalte und Konfigurationen für AEM bereitstellen.
* Wissen Sie, wie mit Vorlagen mit nur wenigen Klicks neue Sites erstellt werden können, die mit Demo-Inhalten gefüllt sind.

Nutzen Sie diese Kenntnisse und fahren Sie mit der AEM-Journey zur schnellen Site-Erstellung fort, indem Sie als Nächstes das Dokument [Erstellen eines Programms und einer Pipeline](create-program.md) lesen. Hier erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, mit dem nächsten Teil der Journey zur schnellen Site-Erstellung fortzufahren, indem Sie das Dokument [Erstellen eines Programms und einer Pipeline](create-program.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Aber sie sind nicht erforderlich, um mit der Journey fortzufahren.

* [Grundlegendes zu Programmen und Programmtypen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/program-types.html?lang=de) – Hier erfahren Sie mehr über die Unterschiede zwischen Live- und Sandbox-Programmen.
* [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) – Wenn Sie mehr über die Struktur von Site-Vorlagen und deren Verwendung zur Erstellung von Sites erfahren möchten, lesen Sie dieses Dokument.
* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=de) – Wenn Sie weitere Details zu den Funktionen von Cloud Manager wünschen, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
