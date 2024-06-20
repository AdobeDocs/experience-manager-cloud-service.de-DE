---
title: Hinzufügen von privaten Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 100%

---

# Hinzufügen von privaten Repositorys in Cloud Manager {#private-repositories}

Indem Sie Cloud Manager für die Verwendung mit Ihren eigenen privaten GitHub-Repositorys konfigurieren, können Sie Ihren Code über Cloud Manager direkt in Ihrem GitHub-Repository validieren, sodass Sie ihn nicht ständig mit dem Adobe-Repository synchronisieren müssen.

>[!NOTE]
>
>Diese Funktion ist nur für öffentliche GitHub-Repositorys verfügbar. Unterstützung für selbstgehostetes GitHub-Repositorys ist nicht verfügbar.

## Konfiguration {#configuration}

Die Konfiguration erfolgt in zwei Hauptschritten:

1. [Repository hinzufügen](#add-repo)
1. [Validierung der Eigentümerschaft eines privaten Repositorys](#validate-ownership)

### Repository hinzufügen {#add-repo}

1. Wählen Sie in Cloud Manager auf der Seite **Programmübersicht** die Registerkarte **Repositorys**, um zur Seite **Repositorys** zu wechseln, und wählen Sie dann **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** als Repository-Typ **Privates Repository**.

1. Angabe von Details zu Ihrem Repository

   * **Repository-Name** – Ein aussagekräftiger Name
   * **Repository-URL** – Die URL des Repositorys, die mit `.git` enden muss
   * **Beschreibung** (optional) – Eine längere Beschreibung des Repositorys nach Bedarf

   ![Eigenes Repository hinzufügen](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. Wählen Sie **Speichern** aus.

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

### Validierung der Eigentümerschaft eines privaten Repositorys {#validate-ownership}

Cloud Manager kennt jetzt Ihr GitHub-Repository, benötigt aber noch den Zugriff darauf. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümerin bzw. Eigentümer des angegebenen Repositorys sind.

1. Nachdem Sie Ihr eigenes Repository hinzugefügt haben, wird der Dialog **Validierung der Eigentümerschaft eines privaten Repositorys** geöffnet.

   ![Validierung der Eigentümerschaft eines privaten Repositorys](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

1. Zur sicheren Interaktion mit Ihrem Repository verwendet Cloud Manager eine GitHub-App.
   * Eine Eigentümerin bzw. ein Eigentümer Ihrer GitHub-Organisation muss die App unter `https://github.com/apps/cloud-manager-for-aem` installieren und Zugriff auf das Repository gewähren.
   * Weitere Informationen dazu finden Sie in der GitHub-Dokumentation.

1. Um die Sicherheit zu erhöhen, müssen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys erstellen. Wählen Sie **Generieren**.

1. Bestätigen Sie die Generierung der geheimen Datei, indem Sie auf **Bestätigen** klicken.

   ![Geheimnisgenerierung bestätigen](/help/implementing/cloud-manager/assets/repos/confirm-generation.png)

1. Im Fenster **Validierung der Eigentümerschaft eines privaten Repositorys** hat Cloud Manager den Inhalt der privaten Datei im Feld **Geheimer Dateiinhalt** generiert. Kopieren Sie den Inhalt aus diesem Feld.

   * Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht kopieren, bevor Sie dieses Fenster schließen, müssen Sie das Geheimnis neu generieren.

   ![Inhalt der geheimen Datei kopieren](/help/implementing/cloud-manager/assets/repos/new-secret.png)

1. Erstellen Sie in der Standardverzweigung Ihres GitHub-Repositorys eine neue Datei mit dem Namen `.well-known/adobe/cloud-manager-challenge`, fügen Sie den geheimen Dateiinhalt in diese Datei ein und speichern Sie sie.

1. Sobald die App installiert ist und sich die geheime Datei im Repository befindet, können Sie im Dialogfeld **Validierung der Eigentümerschaft eines privaten Repositorys** die Option **Bestätigen** wählen.

Die Installation der App und die Erstellung der geheimen Datei kann in jeder beliebigen Reihenfolge erfolgen. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung ist das Repository mit einem roten Symbol gekennzeichnet, das angibt, dass es noch nicht validiert wurde und noch nicht verwendet werden kann.

![Nicht validiertes Repo](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

In der Spalte **Typ** können Sie ganz einfach die von Adobe bereitgestellten Repositorys (**Adobe**) und Ihre eigenen GitHub-Repositorys (**GitHub**) erkennen.

Wenn Sie zu einem späteren Zeitpunkt zum Repository zurückkehren müssen, um die Validierung abzuschließen, wählen Sie auf der Seite **Repositorys** die Schaltfläche mit den Auslassungspunkten in der Zeile mit dem soeben von Ihnen hinzugefügten GitHub-Repository und wählen Sie dann **Eigentümervalidierung** aus dem Dropdown-Menü.

## Verwenden von privaten Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen und Sie können das Repository mit Cloud Manager verwenden.

1. Beim Erstellen einer Pull-Anfrage wird automatisch eine GitHub-Prüfung ausgeführt.

   ![GitHub-Prüfungen](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Für jede Pull-Anfrage wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

1. Die GitHub-Prüfung verbleibt im Status „Wird ausgeführt“, bis die Code-Qualitätsprüfungen abgeschlossen sind. Die Ergebnisse der Code-Qualität werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Wenn die Pull-Anfrage geschlossen oder zusammengeführt wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

>[!TIP]
>
>Im Dokument [Anmerkungen zur GitHub-Prüfung](github-annotations.md) finden Sie Details zu den Informationen, die bei der Ausführung von Pull-Anfrageprüfungen über GitHub bereitgestellt werden.

>[!TIP]
>
>Sie können die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren. Weitere Informationen finden Sie im Dokument [Konfiguration der GitHub-Prüfung für private Repositorys](github-check-config.md).

## Zuordnen von privaten Repositorys zu Pipelines {#pipelines}

Validierte private Repositorys können [Full-Stack- und Frontend-Pipelines zugeordnet werden.](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)

>[!NOTE]
>
>Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt.

## Einschränkungen {#limitations}

Bei der Verwendung privater Repositorys mit Cloud Manager gelten bestimmte Einschränkungen.

* Sie können die Überprüfung der Pull-Anfrage nicht mithilfe der GitHub-Prüfung über Cloud Manager anhalten.
   * Während der Validierung des GitHub-Repositorys versucht Cloud Manager immer, die für dieses Repository erstellten Pull-Anfragen zu validieren.
* Wenn die Adobe GitHub-App aus Ihrer GitHub-Organisation entfernt wird, wird dadurch auch die Überprüfungsfunktion für Pull-Anfragen für alle Repositorys entfernt.
* Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt.
* Bei Verwendung privater Repositorys in Full-Stack-Produktions-Pipelines wird kein Git-Tag erstellt und gesendet.
* Pipelines, die private Repositorys und den On-Commit-Build-Trigger verwenden, werden nicht automatisch gestartet, wenn ein neues Commit in die ausgewählte Verzweigung verschoben wird.
* Die [Funktion zur Wiederverwendung von Artefakten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) gilt nicht für private Repositorys.
