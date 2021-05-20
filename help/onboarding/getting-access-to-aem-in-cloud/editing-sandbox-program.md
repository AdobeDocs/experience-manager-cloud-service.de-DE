---
title: 'Bearbeiten eines Sandbox-Programms '
description: Bearbeiten eines Sandbox-Programms
exl-id: e4545f7e-5329-40ad-81bb-a383c68f5d66
source-git-commit: ee12a6a81a6852d9ffff674cea69e36c37c0ea65
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Bearbeiten eines Sandbox-Programms {#create-sandbox-program}

Benutzer mit entsprechender Berechtigung können jetzt ein Produktionsprogramm bearbeiten, sodass sie Folgendes selbstständig erledigen können:

* Fügen Sie Sites-Lösungen zu einem vorhandenen Programm mit Assets hinzu (oder umgekehrt).
* Entfernen Sie Sites (oder Assets) aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
* Fügen Sie eine zweite, nicht verwendete Lösungsberechtigung hinzu, entweder zu einem vorhandenen Programm oder als neues Programm.

   >[!NOTE]
   >Ein Benutzer mit der Rolle &quot;Business Owner&quot;muss angemeldet sein, um das Programm erfolgreich bearbeiten zu können.

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu bearbeiten:

1. Klicken Sie auf der Seite *Überblick* von Cloud Manager auf die Option **Programm bearbeiten** .

   ![](assets/edit-program-overview.png)

1. Auf der Seite **Programm bearbeiten** werden zwei Registerkarten **Allgemein** und **Lösungen und Add-ons** angezeigt.

   Navigieren Sie zur Registerkarte **Allgemein** , um die Programmbeschreibung zu bearbeiten.

   ![](assets/edit-program-general.png)

   Auf der Registerkarte **Lösungen und Add-ons** werden zwei Optionen angezeigt, z. B. **Sites** und **Assets** für Produktions- und Sandbox-Programme. Sie können auch die Add-On-Option **Commerce** auswählen, die unter **Sites** verfügbar ist, wie in der folgenden Abbildung dargestellt.

   ![](assets/edit-prg.png)

   >[!NOTE]
   >Mindestens eine Lösung muss für ein Programm ausgewählt sein, d. h. der Benutzer darf die Auswahl nicht für alle Lösungen während des Bearbeitungs-Programm-Workflows aufheben.

1. Klicken Sie auf **Save** , um den Workflow des Bearbeitungsprogramms abzuschließen.


## Überlegungen beim Bearbeiten eines Programms {#considerations-editing}

Beim Bearbeiten eines Programms sollten einige Überlegungen überprüft werden:

* Mindestens eine Lösung muss für ein Programm ausgewählt sein, d. h. der Benutzer darf die Auswahl nicht für alle Lösungen während des Bearbeitungs-Programm-Workflows aufheben.

* Wenn Sie auf die Schaltfläche **Speichern** klicken, werden Lösungsaktualisierungen für Umgebungen nach der nächsten Implementierung wirksam, wenn sich die ausgewählten Lösungen geändert haben.
