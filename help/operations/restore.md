---
title: Wiederherstellung von Inhalten in AEM as a Cloud Service
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager AEM as a Cloud Service Inhalte aus einer Sicherungskopie wiederherstellen können.
exl-id: 921d0c5d-5c29-4614-ad4b-187b96518d1f
feature: Operations
role: Admin
source-git-commit: f5dcf76b662e8bec9248ca11f133f9a82142d877
workflow-type: tm+mt
source-wordcount: '1323'
ht-degree: 50%

---


# Wiederherstellung von Inhalten in AEM as a Cloud Service {#content-restore}

Sie können Ihren AEM as a Cloud Service-Inhalt mithilfe von Cloud Manager aus einer Sicherung wiederherstellen.

## Überblick {#overview}

Der Self-Service-Wiederherstellungsprozess von Cloud Manager kopiert Daten aus Adobe-Systemsicherungen und stellt sie in der Originalumgebung wieder her. Eine Wiederherstellung wird durchgeführt, um Daten, die verloren gegangen, beschädigt oder versehentlich gelöscht wurden, in ihren ursprünglichen Zustand zurückzuversetzen.

Der Wiederherstellungsprozess wirkt sich nur auf die Inhalte aus, sodass Ihr Code und Ihre Version von AEM unverändert bleiben. Sie können jederzeit einen Wiederherstellungsvorgang für einzelne Umgebungen starten.

Cloud Manager bietet zwei Arten von Sicherungskopien, mit denen Sie Inhalte wiederherstellen können.

* **Point-in-Time (PIT):** Mit dieser Option werden kontinuierliche Backups wiederhergestellt, die innerhalb der letzten 24 Stunden erfasst wurden.
* **Letzte Woche**: Bei diesem Typ wird aus den Systemsicherungen der letzten sieben Tage vor den letzten 24 Stunden wiederhergestellt.

In beiden Fällen bleiben die Version Ihres benutzerspezifischen Codes und Ihre Version von AEM unverändert.

>[!TIP]
>
>Es ist auch möglich, Sicherungskopien [über die öffentliche API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/) wiederherzustellen.

>[!WARNING]
>
>* Diese Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. 
>* Beim Wiederherstellen eines Backups werden alle Daten gelöscht, die nach diesem Backup hinzugefügt wurden. Die Staging-Umgebung kehrt ebenfalls zur vorherigen Version zurück.
>* Bevor Sie eine Inhaltswiederherstellung starten, sollten Sie andere Optionen zur selektiven Inhaltswiederherstellung in Betracht ziehen.

## Optionen zur selektiven Wiederherstellung von Inhalten {#selective-options}

Bevor Sie eine vollständige Inhaltswiederherstellung vornehmen, sollten Sie diese Optionen in Erwägung ziehen, um Ihre Inhalte leichter wiederherzustellen.

* Wenn ein Paket für den gelöschten Pfad verfügbar ist, installieren Sie das Paket mit dem [Paket-Manager](/help/implementing/developing/tools/package-manager.md) erneut.
* Wenn der gelöschte Pfad eine Seite in Sites war, verwenden Sie die [Funktion „Baum wiederherstellen“](/help/sites-cloud/authoring/sites-console/page-versions.md).
* Wenn der gelöschte Pfad ein Asset-Ordner war und die Originaldateien verfügbar sind, laden Sie sie erneut über die [Assets-Konsole](/help/assets/add-assets.md) hoch.
* Wenn es sich bei dem gelöschten Inhalt um Assets handelt, sollten Sie das [Wiederherstellen früherer Versionen der Assets](/help/assets/manage-digital-assets.md) in Betracht ziehen.

Wenn keine der oben genannten Optionen funktioniert und der Inhalt des gelöschten Pfads signifikant ist, führen Sie eine Inhaltswiederherstellung durch, wie in den folgenden Abschnitten beschrieben.

## Benutzerrolle erstellen {#user-role}

Standardmäßig hat kein Benutzer die Berechtigung, Inhaltswiederherstellungen in Entwicklungs-, Produktions- oder Staging-Umgebungen auszuführen. Um diese Berechtigung an bestimmte Benutzer oder Gruppen zu delegieren, führen Sie die folgenden allgemeinen Schritte aus.

1. Erstellen Sie ein Produktprofil mit einem ausdrucksstarken Namen, der auf die Inhaltswiederherstellung verweist.
1. Stellen Sie die **Programmzugriff**-Berechtigung für das erforderliche Programm bereit.
1. Stellen Sie die Berechtigung **Umgebungswiederherstellung erstellen** je nach Anwendungsfall für die erforderliche Umgebung oder für alle Umgebungen des Programms bereit.
1. Weisen Sie diesem Profil Benutzer zu.

Weitere Informationen über die Verwaltung von Berechtigungen finden Sie unter [Benutzerdefinierte Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md).

## Wiederherstellen des Inhalts einer Umgebung {#restoring-content}

>[!NOTE]
>
>Benutzende müssen über [geeignete Berechtigungen](#user-role) verfügen, um einen Wiederherstellungsvorgang zu starten.

**So stellen Sie den Inhalt einer Umgebung wieder her:**

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

1. Klicken Sie in der Tabelle Umgebungen rechts neben einer Umgebung, deren Inhalt Sie wiederherstellen möchten, auf ![Mehr-](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **Inhalt wiederherstellen**.

   ![Option „Inhalt wiederherstellen“ über das Menü mit den Auslassungspunkten](/help/operations/assets/environments-ellipsis-menu.png)

1. Wählen Sie auf der Registerkarte **Inhalt wiederherstellen** der Seite der Umgebung in **Dropdown-Liste Wiederherstellungszeit** den Zeitrahmen der Wiederherstellung aus.

   ![Registerkarte „Inhalt wiederherstellen“ einer Umgebung](/help/operations/assets/environments-content-restore-tab.png)

   * Wenn Sie **Letzte 24 Stunden** im angrenzenden Feld **Zeit** ausgewählt haben, geben Sie den genauen Zeitpunkt innerhalb der letzten 24 Stunden für die Wiederherstellung an.
   * Wenn Sie **Letzte Woche** im angrenzenden Feld **Tag** auswählen, wählen Sie ein Datum innerhalb der letzten sieben Tage aus, wobei die letzten 24 Stunden ausgeschlossen sind.

1. Sobald Sie ein Datum oder eine Uhrzeit ausgewählt haben, zeigt der Abschnitt **Verfügbare Sicherungskopien** unten eine Liste der verfügbaren Sicherungskopien, die wiederhergestellt werden können

1. Klicken Sie auf ![Informationssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) neben einem Backup, um dessen Code-Version und AEM-Version anzuzeigen, und wiegen Sie dann die Auswirkungen auf die Wiederherstellung, bevor Sie ein Backup auswählen (siehe [Auswahl des richtigen Backups](#choosing-backup)).

   ![Sicherungsinformationen](assets/backup-info.png)

   Der für die Wiederherstellungsoptionen angezeigte Zeitstempel basiert auf der Zeitzone des Computers des Benutzers.

1. Klicken Sie am rechten Ende der Zeile, die die wiederherzustellende Sicherungskopie darstellt, auf ![Rotieren von CCW fett oder Wiederherstellen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_RotateCCWBold_18_N.svg), um den Wiederherstellungsprozess zu starten.

1. Überprüfen Sie die Details im Dialogfeld **Inhalt wiederherstellen** und klicken Sie dann auf **Wiederherstellen**.

   ![Wiederherstellen bestätigen](assets/backup-restore.png)

Der Sicherungsprozess wird gestartet. Sie können den Status der Aktivität in der Liste **[Aktivität wiederherstellen](#restore-activity)** anzeigen. Die Dauer des Wiederherstellungsvorgangs hängt von der Größe und dem Profil des wiederherzustellenden Inhalts ab.

Wenn die Wiederherstellung erfolgreich abgeschlossen wurde, führt die Umgebung Folgendes aus:

* Führt denselben Code und dieselbe AEM-Version aus wie zum Zeitpunkt der Initiierung des Wiederherstellungsvorgangs.
* Er enthält denselben Inhalt, der zum Zeitstempel des ausgewählten Snapshots verfügbar war, wobei die Indizes neu erstellt wurden, damit sie dem aktuellen Code entsprechen.

## Auswahl der richtigen Sicherungskopie {#choosing-backup}

Der Self-Service-Wiederherstellungsprozess von Cloud Manager stellt nur Inhalte in AEM wieder her. Aus diesem Grund müssen Sie Code-Änderungen, die zwischen dem gewünschten Wiederherstellungspunkt und der aktuellen Zeit vorgenommen wurden, sorgfältig prüfen. Überprüfen Sie den Commit-Verlauf zwischen der aktuellen Commit-ID und der ID, zu der wiederhergestellt wird.

Es gibt verschiedene Szenarien.

* Der benutzerdefinierte Umgebungs-Code und die Wiederherstellung befinden sich im selben Repository und in derselben Verzweigung.
* Der benutzerdefinierte Code der Umgebung und die Wiederherstellung teilen sich ein Repository, verwenden eine separate Verzweigung und stammen aus einem gemeinsamen Commit.
* Der benutzerdefinierte Umgebungs-Code und die Wiederherstellung befinden sich in verschiedenen Repositorys.
   * In diesem Fall wird keine Commit-ID angezeigt.
   * Adobe empfiehlt dringend, beide Repositorys zu klonen und ein Vergleichs-Tool zu verwenden, um die Verzweigungen zu vergleichen.

Beachten Sie außerdem, dass eine Wiederherstellung dazu führen kann, dass Ihre Produktions- und Staging-Umgebungen nicht mehr synchronisiert sind. Sie sind für die Folgen der Wiederherstellung von Inhalten verantwortlich.

## Wiederherstellungsaktivität {#restore-activity}

Die Tabelle **Wiederherstellungsaktivität** zeigt den Status der zehn letzten Wiederherstellungsanfragen einschließlich aller aktiven Wiederherstellungsvorgänge an.

![Wiederherstellungsaktivität](assets/backup-activity.png)

Durch Klicken auf ![Informationssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) für ein Backup können Sie Protokolle für dieses Backup herunterladen und die Code-Details einschließlich der Unterschiede zwischen dem Snapshot und den Daten zum Zeitpunkt der Wiederherstellung überprüfen.

## Offsite-Sicherung {#offsite-backup}

Regelmäßige Backups decken das Risiko von versehentlichen Löschungen oder technischen Fehlern in AEM Cloud Services ab, aber es können zusätzliche Risiken durch das Fehlschlagen bezüglich einer Region entstehen. Neben der Verfügbarkeit besteht das größte Risiko bei Ausfällen in solchen Regionen in erster Linie in Datenverlust.

AEM as a Cloud Service mindert dieses Risiko für alle AEM-Produktionsumgebungen. Das heißt, es kopiert kontinuierlich alle AEM-Inhalte in eine Remote-Region. Durch diesen Prozess steht der Inhalt drei Monate lang zur Wiederherstellung zur Verfügung. Diese Funktion wird als Offsite-Backup bezeichnet.

AEM Service Reliability Engineering stellt Staging- und Produktionsumgebungen in AEM Cloud Service von Offsite-Backups während Ausfällen in der Datenregion wieder her.

## Einschränkungen {#limitations}

Die Verwendung des Self-Service-Wiederherstellungsmechanismus unterliegt den folgenden Einschränkungen.

* Wiederherstellungsvorgänge sind auf sieben Tage beschränkt, d. h. es ist nicht möglich, einen Snapshot wiederherzustellen, der älter als sieben Tage ist.
* Pro Kalendermonat sind maximal zehn erfolgreiche Wiederherstellungen in allen Umgebungen eines Programms zulässig.
* Nach der Erstellung der Umgebung dauert es sechs Stunden, bis der erste Snapshot für die Sicherung erstellt wird. Solange dieser Snapshot nicht erstellt ist, kann keine Wiederherstellung in der Umgebung durchgeführt werden.
* Ein Wiederherstellungsvorgang wird nicht initiiert, wenn derzeit eine Konfigurations-Pipeline für den Full-Stack oder die Web-Stufe für die Umgebung ausgeführt wird.
* Eine Wiederherstellung kann nicht initiiert werden, wenn bereits eine andere Wiederherstellung in derselben Umgebung ausgeführt wird.
* In seltenen Fällen kann es vorkommen, dass aufgrund der Beschränkung von 24 Stunden bzw. 7 Tagen für Sicherungskopien die ausgewählte Sicherungskopie aufgrund einer Verzögerung zwischen dem Zeitpunkt der Auswahl und dem Beginn der Wiederherstellung nicht mehr verfügbar ist.
* Daten gelöschter Umgebungen sind dauerhaft verloren und können nicht wiederhergestellt werden.
