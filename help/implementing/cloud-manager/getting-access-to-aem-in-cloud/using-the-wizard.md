---
title: Assistent zur Projekterstellung
description: Erfahren Sie mehr über den Assistenten zur Projekterstellung, mit dem Sie Ihr Projekt nach der Erstellung Ihres Produktionsprogramms schnell einrichten können.
exl-id: 03736ca7-1345-4faf-a61a-f9213ab5c89a
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 6%

---

# Assistent zur Projekterstellung {#project-creation-wizard}

Nachdem Sie Ihr Produktionsprogramm erstellt haben, bietet Cloud Manager einen Assistenten, um ein AEM Projekt mit minimalem Volumen auf der Grundlage der [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) um schnell zu beginnen.

Führen Sie diese Schritte aus, um mithilfe des Assistenten ein AEM Anwendungsprojekt in Cloud Manager zu erstellen.

1. Erstellen Sie ein Produktionsprogramm, indem Sie die im Dokument beschriebenen Schritte befolgen [Erstellen von Produktionsprogrammen](creating-production-programs.md)

1. Sobald die Programmeinrichtung abgeschlossen ist, rufen Sie die **Übersicht** Bildschirm Ihres Programms anzeigen und die **Verzweigung und Projekt erstellen** Aktionsaufruf-Karte oben.

   ![Aktionsaufruf für den Assistenten](assets/create-wizard1.png)

1. Klicken **Erstellen** , um den Assistenten zu starten und die **Titel** und **Neuer Verzweigungsname** im **Erstellen einer Verzweigung und eines Projekts** Fenster.

   ![Erstellen einer Verzweigung und eines Projekts](assets/create-wizard2.png)

1. Optional können Sie auf die Trennlinie klicken, um die zusätzlichen Parameter Ihres Projekts anzuzeigen. Die Standardwerte werden vom AEM Projektarchetyp bereitgestellt und müssen im Allgemeinen nicht geändert werden.

   ![Zusätzliche Projektparameter](assets/create-wizard5.png)

1. Klicken **Erstellen** , um den Projekterstellungsprozess zu starten.


A **Projekterstellung läuft** -Karte ersetzt jetzt die **Verzweigung und Projekt erstellen** Aktionsaufruf-Karte oben im **Programmübersicht** angezeigt.

![Projekterstellung läuft](assets/create-wizard3.png)

Sobald die Erstellung des Programms abgeschlossen ist, wird ein **Umgebung hinzufügen** -Karte ersetzt die **Projekterstellung läuft** -Karte am oberen Rand des **Programmübersicht** angezeigt.

![Umgebung hinzufügen](assets/create-wizard4.png)

Sie haben jetzt ein AEM Projekt, das auf dem AEM Archetyp basiert, der Ihrem Git-Repository hinzugefügt wurde, um als Grundlage für die Entwicklung Ihres eigenen Projekts zu dienen. Als Nächstes können Sie Ihre Umgebungen erstellen, in denen Sie den Projektcode bereitstellen können.

Siehe [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md) , um zu erfahren, wie Sie Umgebungen hinzufügen oder verwalten.

>[!NOTE]
>
>Der Assistent ist nur für Produktionsprogramme verfügbar. weil [Sandbox-Programme](introduction-sandbox-programs.md#auto-creation) automatische Projekterstellung einschließen, ist der Assistent nicht erforderlich.