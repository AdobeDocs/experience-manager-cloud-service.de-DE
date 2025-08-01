---
title: Wiederherstellen des zuvor bereitgestellten Quell-Codes
description: Erfahren Sie, wie Sie eine Umgebung ohne Pipeline-Ausführung auf den letzten erfolgreichen Build zurücksetzen.
feature: Operations
role: Admin
badge: label="Alpha" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
exl-id: 8f804f55-a66d-47ad-a48d-61b861cef4f7
source-git-commit: f3e31d1f17283086cd6fe9e73d67feac938d6567
workflow-type: ht
source-wordcount: '504'
ht-degree: 100%

---

# Wiederherstellen des zuvor bereitgestellten Quell-Codes in AEM as a Cloud Service {#restore-previous-code-deployed}

>[!NOTE]
>
>Die in diesem Artikel beschriebenen Funktionen sind nur über das Alpha-Programm verfügbar. Informationen zur Anmeldung bei der Alpha-Version finden Sie unter [Rollback mit einem Klick bei Pipeline-Bereitstellungen](/help/implementing/cloud-manager/release-notes/current.md##one-click-rollback).

Verwenden Sie **Zuvor bereitgestellten Code wiederherstellen**, um eine Umgebung sofort – ohne Pipeline-Ausführung – auf den letzten erfolgreichen Build zurückzusetzen.

Öffnen Sie einfach das Menü ![Symbol „Mehr“ oder Ellipsen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der ausgewählten Umgebung und wählen Sie **Wiederherstellen** > **Zuvor bereitgestellter Code**, um den zuletzt bereitgestellten Quell-Code in wenigen Sekunden zurückzusetzen.

>[!TIP]
>
>Sie können die aktive verwendete Quell-Code-Version in der Detailansicht der Umgebung auf der Registerkarte **Allgemein** anzeigen. Siehe [Anzeigen von Details einer Umgebung](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).
>
>![Verwendete Source-Code-Version](/help/operations/assets/environments-view-details-sourcecodeversion.png)

Die Funktion **Zuvor bereitgestellten Code wiederherstellen** ist nur verfügbar, wenn **alle** folgenden Bedingungen erfüllt sind:

* Sie verfügen über die Berechtigung zum Wiederherstellen einer Umgebung ****. Weitere Informationen zum Verwalten von Berechtigungen finden Sie unter [Benutzerdefinierte Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md).
* Ihre Organisation ist für das Alpha-Programm registriert und das Feature Flag ist aktiviert.
* Das Programm läuft auf AEM as a Cloud Service.
* Die ausgewählte Umgebung ist eine `Development`-Umgebung (temporäre Alpha-Einschränkung).
* Die letzte Pipeline für diese Umgebung wurde **innerhalb der letzten 30 Tage** erfolgreich abgeschlossen und ausgeführt.
* Der Umgebungsstatus lautet *Wird ausgeführt* und es wird keine Pipeline ausgeführt.

Sollte eine Überprüfung fehlschlagen, öffnet Cloud Manager das folgende Dialogfeld mit einer Liste der nicht erfüllten Bedingungen. Die Schaltfläche **Bestätigen** ist deaktiviert, um die Wiederherstellung zu verhindern.

![Fehlerdialogfeld bei der Wiederherstellung zuvor bereitgestellten Codes](/help/operations/assets/restore-previous-code-deployment-not-allowed.png).

Wenn Sie nur verloren gegangene, beschädigte oder versehentlich gelöschte Daten auf ihren Originalzustand zurücksetzen möchten, können Sie [Inhalt wiederherstellen](/help/operations/restore.md) in AEM as a Cloud Service verwenden. Der Wiederherstellungsprozess wirkt sich nur auf die Inhalte aus, sodass Ihr Code und Ihre Version von AEM unverändert bleiben. 

**So stellen Sie den zuvor bereitgestellten Code wieder her:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie eine Wiederherstellung einleiten möchten.

1. Führen Sie einen der folgenden Schritte aus, um alle Umgebungen für das Programm aufzulisten:

   * Klicken Sie im linken Seitenmenü unter **Services** auf ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Umgebungen**.

     ![Registerkarte „Umgebungen“](assets/environments-1.png)

   * Klicken Sie im linken Seitenmenü unter **Programm** auf **Überblick** und dann auf der Karte **Umgebungen** auf ![Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Alle anzeigen**.

     ![Option „Alle anzeigen“](assets/environments-2.png)

     >[!NOTE]
     >
     >Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken Sie auf der Karte auf **Alle anzeigen**, um *alle* Umgebungen des Programms anzuzeigen.

1. Klicken Sie in der Tabelle „Umgebungen“ rechts neben einer Umgebung, deren Quell-Code Sie wiederherstellen möchten, auf ![Symbol „Mehr“ oder Ellipsen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **Wiederherstellen** > **Zuvor bereitgestellter Code**.

   ![Option „Zuvor bereitgestellter Code“ im Ellipsen-Menü](/help/operations/assets/restore-previous-code-deployed-menu.png)

1. Überprüfen Sie im Dialogfeld **Zuvor bereitgestellten Code wiederherstellen** die aktuell bereitgestellte Version sowie die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Bestätigen**.

   ![Dialogfeld „Zuvor bereitgestellten Code wiederherstellen“](/help/operations/assets/restore-previous-code-deployed-dialogbox.png)

1. Cloud Manager setzt die Umgebung auf den früheren Build zurück, behält Inhalte und Konfiguration bei und markiert die Umgebung als **Wiederherstellung läuft**, bis die Bereitstellung abgeschlossen ist.

   ![Aktivierung wird wiederhergestellt](/help/operations/assets/restore-previous-code-deployed-restoring.png)
