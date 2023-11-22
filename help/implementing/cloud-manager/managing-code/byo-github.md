---
title: Arbeiten mit Ihren eigenen GitHub-Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen GitHub-Repositorys einrichten.
feature: Release Information
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 237b4a8e01af74dbaac0ba1715b5fa95c931be7c
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 70%

---

# Arbeiten mit Ihren eigenen GitHub-Repositorys in Cloud Manager {#byo-github}

Indem Sie Cloud Manager für die Verwendung mit Ihren eigenen GitHub-Repositorys konfigurieren, können Sie Ihren Code über Cloud Manager direkt in Ihrem GitHub-Repository validieren, sodass Sie ihn nicht ständig mit dem Adobe-Repository synchronisieren müssen.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/implementing/cloud-manager/release-notes/current.md#early-adoption) verfügbar.

## Konfiguration {#configuration}

Die Konfiguration erfolgt in zwei Hauptschritten:

1. [Repository hinzufügen](#add-repo)
1. [Validierung der Eigentümerschaft eines privaten Repositorys](#validate-ownership)

### Repository hinzufügen {#add-repo}

1. In Cloud Manager über die **Programmübersicht** Seite, wählen Sie die **Repositorys** Registerkarte, um zu der **Repositorys** Seite und klicken Sie auf **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** als Repository-Typ **Privates Repository**.

1. Angabe von Details zu Ihrem Repository

   * **Repository-Name** – Ein aussagekräftiger Name
   * **Repository-URL** – Die URL des Repositorys, die mit `.git` enden muss
   * **Beschreibung** (optional) – Eine längere Beschreibung des Repositorys nach Bedarf

   ![Eigenes Repository hinzufügen](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. Wählen Sie **Speichern** aus.

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

### Validierung der Eigentümerschaft eines privaten Repositorys {#validate-ownership}

Cloud Manager kennt jetzt Ihr GitHub-Repository, benötigt aber noch den Zugriff darauf. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümerin bzw. Eigentümer des angegebenen Repositorys sind.

1. Nachdem Sie Ihr eigenes Repository hinzugefügt haben, wird die **Validierung des Eigentums an privaten Repositorys** wird geöffnet.

   ![Validierung der Eigentümerschaft eines privaten Repositorys](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

1. Zur sicheren Interaktion mit Ihrem Repository verwendet Cloud Manager eine GitHub-App.
   * Eine Eigentümerin bzw. ein Eigentümer Ihrer GitHub-Organisation muss die App unter `https://github.com/apps/cloud-manager-for-aem-stage` installieren und Zugriff auf das Repository gewähren.
   * Weitere Informationen dazu finden Sie in der GitHub-Dokumentation .

1. Um die Sicherheit zu erhöhen, müssen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys erstellen. Auswählen **Erzeugen**.

1. Bestätigen Sie die Generierung der geheimen Datei, indem Sie auf **Bestätigen** klicken.

   ![Geheimnisgenerierung bestätigen](/help/implementing/cloud-manager/assets/repos/confirm-generation.png)

1. Im Fenster **Validierung der Eigentümerschaft eines privaten Repositorys** hat Cloud Manager den Inhalt der privaten Datei im Feld **Geheimer Dateiinhalt** generiert. Kopieren Sie den Inhalt aus diesem Feld.

   * Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht vor dem Schließen dieses Fensters kopieren, generieren Sie den geheimen Schlüssel erneut.

   ![Inhalt der geheimen Datei kopieren](/help/implementing/cloud-manager/assets/repos/new-secret.png)

1. Erstellen Sie in der Standardverzweigung Ihres GitHub-Repositorys eine neue Datei mit dem Namen `.well-known/adobe/cloud-manager-challenge`, fügen Sie den geheimen Dateiinhalt in diese Datei ein und speichern Sie sie.

1. Sobald die App installiert ist und die geheime Datei im Repository vorhanden ist, können Sie **Bestätigen** im **Validierung des Eigentums an privaten Repositorys** angezeigt.

Die Installation der App und die Erstellung der geheimen Datei kann in jeder beliebigen Reihenfolge erfolgen. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung wird das Repository mit einem roten Symbol aufgeführt, das angibt, dass es noch nicht validiert wurde und noch nicht verwendet werden kann.

![Nicht validiertes Repo](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

Die **Typ** -Spalte identifiziert einfach von Adobe bereitgestellte Repositorys (**Adobe**) und Ihre eigenen GitHub-Repositorys (**GitHub**).

Wenn Sie zu einem späteren Zeitpunkt zum Repository zurückkehren müssen, um die Validierung abzuschließen, wird im **Repositorys** die Suchschaltfläche in der Zeile, die das soeben hinzugefügte GitHub-Repository darstellt, auswählen **Validierung des Eigentums** aus dem Dropdown-Menü.

## Verwenden eigener GitHub-Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen und Sie können das Repository mit Cloud Manager verwenden.

1. Beim Erstellen einer Pull-Anfrage wird automatisch eine GitHub-Prüfung ausgeführt.

   ![GitHub-Prüfungen](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Für jede Pull-Anfrage wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

1. Die GitHub-Prüfung verbleibt im Status „Wird ausgeführt“, bis die Code-Qualitätsprüfungen abgeschlossen sind. Die Ergebnisse der Code-Qualität werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Wenn die Pull-Anfrage geschlossen oder zusammengeführt wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

## Einschränkungen {#limitations}

Einschränkungen bei der Verwendung Ihrer eigenen GitHub-Repositorys mit Cloud Manager.

* Sie können die GitHub-Repositorys nicht als direkte Repository-Quelle für die von Ihnen verwalteten Pipelines verwenden.
   * Diese Funktionalität ist geplant.
* Sie können die Überprüfung der Pull-Anforderung nicht mithilfe der GitHub-Prüfung vom Cloud Manager anhalten.
   * Während der Validierung des GitHub-Repositorys versucht Cloud Manager immer, die für dieses Repository erstellten Pull-Anfragen zu validieren.
Wenn die Adobe GitHub-App aus Ihrer GitHub-Organisation entfernt wird, wird dadurch auch die Überprüfungsfunktion für Pull-Anfragen für alle Repositorys entfernt.
