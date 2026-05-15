---
title: Projektdokumentations-Kenntnisse
description: Erfahren Sie, wie Sie mit den Dokumentationsfähigkeiten des Experience Modernization Agents die Projektübergabe beschleunigen können.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 111cc47d-085f-4cf4-81bc-332e6a31bbeb
source-git-commit: c2b849ef25afd0809891a822a99ddd3059bf1919
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 1%

---

# Projektdokumentations-Kenntnisse {#project-documentation}

Erfahren Sie, wie Sie mit den Dokumentationsfähigkeiten des Experience Modernization Agents die Projektübergabe beschleunigen können.

## Beschleunigen der Projektübergabe {#project-handovers}

[Der Experience Modernization Agent](/help/ai-in-aem/agents/brand-experience/modernization/overview.md) kann automatisch Projektdokumentationshandbücher für AEM Edge Delivery Services-Projekte generieren, die Folgendes enthalten:

* **Projekteinführung** - Erläuterung der Projekteinrichtung, -struktur und -konventionen, die ohne manuellen Aufwand erstellt werden
* **Organisation von Modulen und Komponenten** - Klare Dokumentation der Organisation von Blöcken, Modulen und Komponenten und ihrer Beziehung zueinander
* **Rollenbasierte Handbücher** - Zielgerichtete Dokumentation für Autoren, Entwickler und Administratoren, damit jedes Teammitglied genau das erhält, was es benötigt

Dies vereinfacht die Projektübergabe für AEM Edge Delivery Services-Projekte.

## Voraussetzungen {#prerequisites}

Stellen Sie Folgendes sicher, bevor Sie diese Kenntnisse verwenden.

* Ihr Projekt muss in den -Arbeitsbereich in der Konsole ausgecheckt sein.
* Sie müssen über Administratorberechtigungen für das Projekt verfügen, für das Sie die Dokumentation erstellen.
* Agent-Berechtigungen müssen in der Konsole zulässig sein.
   * Wählen Sie in **Einstellungen der Konsole die Option „LLM erlauben, in meinem** auf [.hlx.page zuzugreifen](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view)
   * Wenn diese Option nicht aktiviert ist, generiert der Agent die Dokumentation basierend auf der Code-Basis, auf die er zugreifen kann.

## Erstellen der Projektdokumentation {#creating-documentation}

Sobald die Voraussetzungen erfüllt sind, müssen Sie den Agenten einfach bitten, eine Dokumentation für Ihr Projekt zu erstellen.

1. In der Chat-Aufgabe „Dokumentation zu diesem Projekt erstellen“.
1. Geben Sie den Organisationsnamen des Projekts an, wenn der Agent danach fragt.
1. Der Agent fragt, welche Dokumentation Sie erstellen möchten. Normalerweise würden Sie &quot;**&quot;**.

   ![Dokumentation erstellen](assets/select-documentation.png)

1. Nach der Erstellung werden die Handbücher in Ihrem Arbeitsbereich platziert. Wählen Sie eine aus, um eine Beschreibung anzuzeigen, und klicken Sie auf den Link, um die vollständige PDF herunterzuladen.

   ![Dokumentation erstellt](assets/documentation-created.png)

Sie können die PDF direkt speichern, um sie Ihren Teams bereitzustellen, oder sie als Teil des restlichen DA-Inhalts hochladen.

![Administratorhandbuch](assets/admin-guide.png)

>[!NOTE]
>
>Wenn Sie nicht berechtigt sind, auf die Edge Delivery Services Admin-API zuzugreifen oder die Option **LLM erlauben, in meinem Namen auf admin.hlx.page zuzugreifen** [&#x200B; in den Einstellungen der Konsole.](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view) nicht aktiviert ist, erstellt der Agent die Dokumentation basierend auf der Code-Basis, auf die er zugreifen kann.

## Fehlerbehebung {#troubleshooting}

Im Folgenden finden Sie häufige Fehlermeldungen bei der Verwendung der Projektdokumentations-Kenntnisse und wie Sie diese beheben können.

### „Zugriff verweigert“ oder „Nicht autorisiert“ {#unauthorized}

* **Ursache:** Fehlende Administratorberechtigungen oder Agentenberechtigungen nicht aktiviert
* **Lösung:**
   1. Überprüfen Sie, ob Sie Administratorzugriff auf das Projekt haben
   1. Wählen Sie in **Einstellungen der Konsole die Option „LLM erlauben, in meinem** auf [.hlx.page zuzugreifen](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view)

### „Projekt nicht gefunden“ {#not-found}

* **Ursache:** Repository ist in Workspace nicht ausgecheckt
* **Lösung:**
   1. Überprüfen des Projekt-Repositorys
   1. Stellen Sie sicher, dass Sie sich im richtigen Arbeitsbereich befinden

### „API-Konfigurationsfehler“ {#api-error}

* **Ursache:** Zugriff auf die Edge Delivery Services-Konfigurations-Service-API nicht möglich
* **Lösung:**
   1. Wählen Sie in **Einstellungen der Konsole die Option „LLM erlauben, in meinem** auf [.hlx.page zuzugreifen](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view)
   1. Überprüfen der Netzwerk-/VPN-Verbindung
   1. Administratorzugriff auf das Projekt bestätigen
