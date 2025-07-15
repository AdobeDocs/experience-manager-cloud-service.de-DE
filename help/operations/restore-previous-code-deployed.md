---
title: Wiederherstellen des vorherigen bereitgestellten Source-Codes
description: Erfahren Sie, wie Sie eine Umgebung ohne Pipeline-Ausführung auf ihren letzten erfolgreichen Build &ndash; zurücksetzen.
feature: Operations
role: Admin
badge: label="Alpha" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
exl-id: 8f804f55-a66d-47ad-a48d-61b861cef4f7
source-git-commit: 72b80f411ee39674530c1c41349329604e127e1e
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 7%

---

# Wiederherstellen des vorherigen Quellcodes, der in AEM as a Cloud Service bereitgestellt wurde {#restore-previous-code-deployed}

>[!NOTE]
>
>Die in diesem Artikel beschriebene Funktion ist nur über das Early-Adopter-Alpha-Programm verfügbar. Informationen zum Anmelden bei der Alpha-Version finden Sie unter [1-Klick-Rollback für Pipeline-Bereitstellungen](/help/implementing/cloud-manager/release-notes/current.md##one-click-rollback).

Verwenden Sie **vorherigen Code bereitstellen** um eine Umgebung sofort auf den letzten erfolgreichen Build zurückzusetzen - keine Pipeline-Ausführung erforderlich.

Sie öffnen einfach das Menü der ausgewählten Umgebung ![Mehr-Symbol oder ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)-Symbol) und wählen **Wiederherstellen** > **Vorheriger Code bereitgestellt**, um den zuletzt bereitgestellten Quellcode in Sekunden zurückzusetzen.

>[!TIP]
>
>Sie können die aktive Quell-Code-Version, die verwendet wird, in der Detailansicht der Umgebung auf der Registerkarte **Allgemein** anzeigen. Siehe [Anzeigen von Details zu einer Umgebung](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).
>
>![Verwendete Source-Code-Version](/help/operations/assets/environments-view-details-sourcecodeversion.png)

Die Funktion **Vorherigen Code bereitgestellt** wiederherstellen“ ist nur verfügbar, wenn **alle** Bedingungen unten erfüllt sind:

* Sie verfügen über **Berechtigungen zum Erstellen der**). Weitere Informationen über die Verwaltung von Berechtigungen finden Sie unter [Benutzerdefinierte Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md).
* Ihre Organisation ist für das Early-Adopter-Programm registriert und das Feature Flag ist aktiviert.
* Das Programm läuft auf AEM as a Cloud Service.
* Die ausgewählte Umgebung ist eine `Development` Umgebung (temporäres Alpha-Limit).
* Die letzte Pipeline für diese Umgebung wurde erfolgreich abgeschlossen und wurde vor **als 30** ausgeführt.
* Der Umgebungsstatus lautet *Wird ausgeführt* und es wird keine Pipeline ausgeführt.

Wenn eine Überprüfung fehlschlägt, öffnet Cloud Manager das folgende Dialogfeld, in dem eine oder mehrere nicht erfüllte Bedingungen aufgelistet und **Bestätigen** deaktiviert werden, um die Wiederherstellung zu verhindern.

![Dialogfeld „Fehler bei Bereitstellung des vorherigen Codes wiederherstellen](/help/operations/assets/restore-previous-code-deployment-not-allowed.png).

Wenn Sie nur Daten, die verloren gegangen, beschädigt oder versehentlich gelöscht wurden, in ihren Originalzustand zurücksetzen möchten, können Sie [Inhalt in AEM as a Cloud Service wiederherstellen](/help/operations/restore.md). Dieser Wiederherstellungsprozess wirkt sich nur auf Inhalte aus, sodass Ihr Quell-Code und Ihre Version von AEM unverändert bleiben.

**So stellen Sie den zuvor bereitgestellten Code wieder her:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie eine Wiederherstellung einleiten möchten.

1. Führen Sie eine der folgenden Aktionen aus, um alle Umgebungen für das Programm aufzulisten:

   * Klicken Sie im linken Menü unter **Services** auf ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Umgebungen**.

     ![Registerkarte „Umgebungen“](assets/environments-1.png)

   * Klicken Sie im linken Menü unter **Programm** auf **Übersicht** und dann auf der Karte **Umgebungen** auf ![Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Alle anzeigen**.

     ![Option „Alle anzeigen“](assets/environments-2.png)

     >[!NOTE]
     >
     >Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken Sie **der Karte** Alle anzeigen“, um *alle* Umgebungen des Programms anzuzeigen.

1. Klicken Sie in der Tabelle Umgebungen rechts neben einer Umgebung, deren Quell-Code Sie wiederherstellen möchten, auf ![Mehr-Symbol oder ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)-Symbol) und dann auf **Wiederherstellen** > **Vorheriger Code bereitgestellt**.

   ![Option „Vorherigen Code bereitgestellt wiederherstellen“ über das Menü mit den Auslassungspunkten](/help/operations/assets/restore-previous-code-deployed-menu.png)

1. Überprüfen **im Dialogfeld „Vorherigen Code bereitgestellt**&quot; die aktuell bereitgestellte Version und die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Bestätigen**.

   ![Dialogfeld „Zugewiesenen Code wiederherstellen“](/help/operations/assets/restore-previous-code-deployed-dialogbox.png)

1. Cloud Manager setzt die Umgebung auf den früheren Build zurück, behält Inhalte und Konfiguration bei und markiert die Umgebung **Wiederherstellen** auf der Seite Umgebungen, bis die Bereitstellung abgeschlossen ist.

   ![Aktivierung wird wiederhergestellt](/help/operations/assets/restore-previous-code-deployed-restoring.png)
