---
title: Wiederherstellung von Inhalten in AEM as a Cloud Service
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager AEM as a Cloud Service Inhalte aus einer Sicherungskopie wiederherstellen können.
exl-id: 921d0c5d-5c29-4614-ad4b-187b96518d1f
feature: Operations
role: Admin
source-git-commit: fee4921b7087fd64b2f65b086998aedde8aaafb0
workflow-type: ht
source-wordcount: '1339'
ht-degree: 100%

---


# Wiederherstellung von Inhalten in AEM as a Cloud Service {#content-restore}

Erfahren Sie, wie Sie mithilfe von Cloud Manager AEM as a Cloud Service Inhalte aus einer Sicherungskopie wiederherstellen können.

## Überblick {#overview}

Der Self-Service-Wiederherstellungsprozess von Cloud Manager kopiert Daten aus Adobe-Systemsicherungen und stellt sie in der Originalumgebung wieder her. Eine Wiederherstellung wird durchgeführt, um Daten, die verloren gegangen, beschädigt oder versehentlich gelöscht wurden, in ihren ursprünglichen Zustand zurückzuversetzen.

Der Wiederherstellungsprozess wirkt sich nur auf die Inhalte aus, sodass Ihr Code und Ihre Version von AEM unverändert bleiben. Sie können jederzeit einen Wiederherstellungsvorgang für einzelne Umgebungen starten.

Cloud Manager bietet zwei Arten von Sicherungskopien, mit denen Sie Inhalte wiederherstellen können.

* **Point-in-Time (PIT)**: Bei diesem Typ wird aus kontinuierlichen Systemsicherungen der letzten 24 Stunden vor der aktuellen Zeit wiederhergestellt.
* **Letzte Woche**: Bei diesem Typ wird aus den Systemsicherungen der letzten sieben Tage vor den letzten 24 Stunden wiederhergestellt.

In beiden Fällen bleiben die Version Ihres benutzerspezifischen Codes und Ihre Version von AEM unverändert.

>[!TIP]
>
>Es ist auch möglich, Sicherungskopien [über die öffentliche API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/) wiederherzustellen.

>[!WARNING]
>
>* Diese Funktion sollte nur verwendet werden, wenn schwerwiegende Probleme mit Code oder Inhalt aufgetreten sind. 
>* Das Wiederherstellen eines Backups führt zum Verlust der aktuellen Daten zwischen dem Zeitpunkt des Backups und dem aktuellen Zeitpunkt. Die Staging-Umgebung wird ebenfalls in der alten Version wiederhergestellt.
>* Bevor Sie eine Inhaltswiederherstellung starten, sollten Sie andere Optionen zur selektiven Inhaltswiederherstellung in Betracht ziehen.

## Optionen zur selektiven Inhaltswiederherstellung {#selective-options}

Bevor Sie eine vollständige Inhaltswiederherstellung vornehmen, sollten Sie diese Optionen in Erwägung ziehen, um Ihre Inhalte leichter wiederherzustellen.

* Wenn ein Paket für den gelöschten Pfad verfügbar ist, installieren Sie das Paket mit dem [Paket-Manager](/help/implementing/developing/tools/package-manager.md) erneut.
* Wenn der gelöschte Pfad eine Seite in Sites war, verwenden Sie die [Funktion „Baum wiederherstellen“](/help/sites-cloud/authoring/sites-console/page-versions.md).
* Wenn der gelöschte Pfad ein Asset-Ordner war und die Originaldateien verfügbar sind, laden Sie sie erneut über die [Assets-Konsole](/help/assets/add-assets.md) hoch.
* Wenn es sich bei dem gelöschten Inhalt um Assets handelt, sollten Sie das [Wiederherstellen früherer Versionen der Assets](/help/assets/manage-digital-assets.md) in Betracht ziehen.

Wenn keine der oben genannten Optionen funktioniert und der Inhalt des gelöschten Pfads signifikant ist, führen Sie eine Inhaltswiederherstellung durch, wie in den folgenden Abschnitten beschrieben.

## Erstellen einer Benutzerrolle {#user-role}

Standardmäßig ist keine Benutzerin und kein Benutzer berechtigt, Inhaltswiederherstellungen in Entwicklungs-, Produktions- oder Staging-Umgebungen auszuführen. Gehen Sie wie folgt vor, um diese Berechtigung bestimmten Benutzenden oder Gruppen zuzuweisen.

1. Erstellen Sie ein Produktprofil mit einem ausdrucksstarken Namen, der auf die Inhaltswiederherstellung verweist.
1. Stellen Sie die **Programmzugriff**-Berechtigung für das erforderliche Programm bereit.
1. Stellen Sie die Berechtigung **Umgebungswiederherstellung erstellen** je nach Anwendungsfall für die erforderliche Umgebung oder für alle Umgebungen des Programms bereit.
1. Weisen Sie dem Profil Benutzende zu.

Weitere Informationen zum Verwalten von Berechtigungen finden Sie in der Dokumentation [Benutzerdefinierte Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md).

## Wiederherstellen von Inhalten {#restoring-content}

Bestimmen Sie zunächst den Zeitrahmen der Inhalte, die Sie wiederherstellen möchten. Führen Sie die folgenden Schritte aus, um den Inhalt Ihrer Umgebung aus einer Sicherungskopie wiederherzustellen.

>[!NOTE]
>
>Benutzende müssen über [geeignete Berechtigungen](#user-role) verfügen, um einen Wiederherstellungsvorgang zu starten.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie eine Wiederherstellung einleiten möchten.

1. Klicken Sie auf der Seite **Programmübersicht** in der Karte **Umgebungen** auf die Schaltfläche mit den Auslassungspunkten neben der Umgebung, für die Sie eine Wiederherstellung einleiten möchten, und wählen Sie **Inhalt wiederherstellen**.

   ![Option zum Wiederherstellen](assets/backup-option.png)

   * Alternativ können Sie auch direkt zur Registerkarte **Inhalt wiederherstellen** auf der Seite mit den Umgebungsdetails einer bestimmten Umgebung navigieren.

1. Wählen Sie zunächst auf der Registerkarte **Inhalt wiederherstellen** der Seite mit den Umgebungsdetails den Zeitrahmen der Wiederherstellung unter der Dropdown-Liste **Wiederherstellungszeit**.

   1. Wenn Sie **Letzte 24 Stunden** auswählen, können Sie im benachbarten Feld **Zeit** den genauen Zeitpunkt innerhalb der letzten 24 Stunden für die Wiederherstellung angeben.

      ![Letzte 24 Stunden](assets/backup-time.png)

   1. Wenn Sie **Letzte Woche** wählen, können Sie im benachbarten Feld **Tag** ein Datum innerhalb der letzten sieben Tage auswählen, wobei die vergangenen 24 Stunden ausgeschlossen sind.

      ![Letzte Woche](assets/backup-date.png)

1. Sobald Sie ein Datum oder eine Uhrzeit ausgewählt haben, zeigt der Abschnitt **Verfügbare Sicherungskopien** unten eine Liste der verfügbaren Sicherungskopien, die wiederhergestellt werden können

   ![Verfügbare Sicherungskopien](assets/backup-available.png)

1. Suchen Sie die Sicherungskopie, die Sie wiederherstellen möchten, indem Sie das Informationssymbol verwenden, um Informationen über die in dieser Sicherungskopie enthaltene Version des Codes und der AEM-Version anzuzeigen, und berücksichtigen Sie die Auswirkungen einer Wiederherstellung bei der [Auswahl der Sicherungskopie](#choosing-the-right-backup).

   ![Sicherungsinformationen](assets/backup-info.png)

   * Der für die Wiederherstellungsoptionen angezeigte Zeitstempel beruht auf der Zeitzone des Computers der Person.

1. Um den Wiederherstellungsprozess zu starten, klicken Sie auf das Symbol **Wiederherstellen** am rechten Ende der Zeile, die die wiederherzustellende Sicherungskopie darstellt.

1. Überprüfen Sie die Details im Dialogfeld **Inhalt wiederherstellen**, bevor Sie Ihre Anfrage durch Klicken auf **Wiederherstellen** bestätigen.

   ![Wiederherstellen bestätigen](assets/backup-restore.png)

Der Sicherungsprozess wird eingeleitet und Sie können den Status in der Tabelle **[Wiederherstellungsaktivität](#restore-activity)** einsehen. Die Dauer des Wiederherstellungsvorgangs hängt von der Größe und dem Profil des wiederherzustellenden Inhalts ab.

Wenn die Wiederherstellung erfolgreich abgeschlossen wurde, wird die Umgebung wie folgt aussehen:

* Sie führt denselben Code und dieselbe AEM-Version aus wie zum Zeitpunkt der Initiierung des Wiederherstellungsvorgangs.
* Sie verfügt über denselben Inhalt, der beim Zeitstempel des ausgewählten Snapshots verfügbar war, wobei die Indizes neu erstellt wurden, damit sie dem aktuellen Code entsprechen.

## Auswahl der richtigen Sicherungskopie {#choosing-backup}

Der Self-Service-Wiederherstellungsprozess von Cloud Manager stellt nur Inhalte in AEM wieder her. Aus diesem Grund müssen Sie Code-Änderungen, die zwischen dem gewünschten Wiederherstellungspunkt und der aktuellen Zeit vorgenommen wurden, sorgfältig prüfen, indem Sie das Protokoll zwischen der aktuellen und der wiederhergestellten Commit-ID überprüfen.

Es gibt verschiedene Szenarien.

* Der benutzerdefinierte Code in der Umgebung und die Wiederherstellung befinden sich im selben Repository und in derselben Verzweigung.
* Der benutzerdefinierte Code in der Umgebung und die Wiederherstellung befinden sich im selben Repository, jedoch in einer anderen Verzweigung mit einem gemeinsamen Commit.
* Der benutzerdefinierte Code in der Umgebung und die Wiederherstellung befinden sich in verschiedenen Repositorys.
   * In diesem Fall wird keine Commit-ID angezeigt.
   * Es wird dringend empfohlen, beide Repositorys zu klonen und ein Vergleichs-Tool zu verwenden, um die Verzweigungen zu vergleichen.

Beachten Sie außerdem, dass eine Wiederherstellung dazu führen kann, dass Ihre Produktions- und Staging-Umgebungen nicht mehr synchronisiert sind. Sie sind für die Folgen der Wiederherstellung von Inhalten verantwortlich.

## Wiederherstellungsaktivität {#restore-activity}

Die Tabelle **Wiederherstellungsaktivität** zeigt den Status der zehn letzten Wiederherstellungsanfragen einschließlich aller aktiven Wiederherstellungsvorgänge an.

![Wiederherstellungsaktivität](assets/backup-activity.png)

Wenn Sie auf das Informationssymbol für ein Backup klicken, können Sie Protokolle für dieses Backup herunterladen und die Code-Details einschließlich der Unterschiede zwischen dem Snapshot und den Daten zum Zeitpunkt der Wiederherstellung überprüfen.

## Offsite-Sicherung {#offsite-backup}

Regelmäßige Backups decken das Risiko von versehentlichen Löschungen oder technischen Fehlern in AEM Cloud Services ab, aber es können zusätzliche Risiken durch das Fehlschlagen bezüglich einer Region entstehen. Neben der Verfügbarkeit besteht das größte Risiko bei Ausfällen in solchen Regionen in erster Linie in Datenverlust.

AEM as a Cloud Service deckt dieses Risiko für alle AEM-Produktionsumgebungen ab, indem der gesamte AEM-Inhalt kontinuierlich in eine entfernte Region kopiert und für einen Zeitraum von drei Monaten für die Wiederherstellung zur Verfügung gestellt wird. Diese Funktion wird als Offsite-Backup bezeichnet.

Die Wiederherstellung von AEM Cloud Services für Staging- und Produktionsumgebungen erfolgt im Fall von Ausfällen in der Datenregion durch AEM Service Reliability Engineering.

## Einschränkungen {#limitations}

Die Verwendung des Self-Service-Wiederherstellungsmechanismus unterliegt den folgenden Einschränkungen.

* Wiederherstellungsvorgänge sind auf sieben Tage beschränkt, d. h. es ist nicht möglich, einen Snapshot wiederherzustellen, der älter als sieben Tage ist.
* Pro Kalendermonat sind maximal zehn erfolgreiche Wiederherstellungen in allen Umgebungen eines Programms zulässig.
* Nach der Erstellung der Umgebung dauert es sechs Stunden, bis der erste Snapshot für die Sicherung erstellt wird. Solange dieser Snapshot nicht erstellt ist, kann keine Wiederherstellung in der Umgebung durchgeführt werden.
* Ein Wiederherstellungsvorgang wird nicht initiiert, wenn gerade eine Konfigurations-Pipeline (Full-Stack oder Web-Stufe) für die Umgebung ausgeführt wird.
* Eine Wiederherstellung kann nicht initiiert werden, wenn bereits eine andere Wiederherstellung in derselben Umgebung ausgeführt wird.
* In seltenen Fällen kann es vorkommen, dass aufgrund der Beschränkung von 24 Stunden bzw. 7 Tagen für Sicherungskopien die ausgewählte Sicherungskopie aufgrund einer Verzögerung zwischen dem Zeitpunkt der Auswahl und dem Beginn der Wiederherstellung nicht mehr verfügbar ist.
* Daten gelöschter Umgebungen sind dauerhaft verloren und können nicht wiederhergestellt werden.
