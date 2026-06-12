---
title: Hinzufügen eines privaten GitHub-Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 188201dfaececb21d373450711eb206b8e2323e2
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 47%

---

# Hinzufügen eines privaten GitHub-Repositorys in Cloud Manager {#private-repositories}

Durch das Einrichten von Cloud Manager für die Integration mit Ihrem auf `github.com` gehosteten privaten GitHub-Repository können Sie Ihren Code mithilfe von Cloud Manager direkt in GitHub validieren. Diese Seite gilt für alle auf `github.com` gehosteten Repositorys, unabhängig vom GitHub-Plan (kostenlos, Pro, Team oder Enterprise Cloud). Mit dieser Konfiguration müssen Sie Ihren Code nicht mehr regelmäßig mit dem Adobe-Repository synchronisieren.

>[!IMPORTANT]
>Cloud Manager überprüft die Eigentümerschaft am GitHub-Repository auf eine der beiden folgenden Arten, je nachdem, wo das Repository gehostet wird:
>
>* Diese Seite gilt für alle auf `github.com` gehosteten Repositorys, unabhängig vom GitHub-Plan (kostenlos, Pro, Team oder Enterprise Cloud). Diese Repositorys verwenden die Adobe GitHub-App , um die Eigentümerschaft zu überprüfen. Es ist keine Webhook-Konfiguration erforderlich, da Cloud Manager direkt über die App integriert wird.
>* Wenn Sie einen der folgenden Repository-Typen hinzufügen möchten, finden Sie weitere Informationen unter [Hinzufügen externer Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md). Diese Repositorys verwenden einen PAT (Personal Access Token) und einen manuell konfigurierten Webhook , um den Besitz zu überprüfen.
>
>   * GitHub Enterprise Server (selbst gehostete Version von GitHub)-Repositorys.
>   * GitLab-Repositorys (sowohl `gitlab.com` als auch die selbst gehostete Version von GitLab).
>   * Bitbucket-Repositorys (nur `bitbucket.org`, Cloud-Version). Die selbst gehostete Version von Bitbucket wird seit dem 15. Februar 2024 nicht mehr unterstützt.
>   * Azure DevOps (`dev.azure.com`)-Repositorys.

## Konfiguration {#configuration}

Die Konfiguration eines privaten GitHub-Repositorys in Cloud Manager besteht aus zwei Schritten:

1. [Privates GitHub-Repository hinzufügen](#add-repo) zu einem ausgewählten Programm hinzufügen.
1. Überprüfen Sie dann [die Eigentümerschaft des privaten GitHub-Repositorys](#validate-ownership).



### Hinzufügen eines privaten GitHub-Repositorys zu einem Programm {#add-repo}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus, mit dem Sie ein privates Git-Repository verknüpfen möchten.

1. Wählen Sie im Seitenmenü unter **Services** ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorys** aus.

   ![Die Seite „Repositorys“](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Klicken Sie oben rechts auf der Seite **Repositorys** auf **Repository hinzufügen**.

1. Legen Sie im Dialogfeld **Repository hinzufügen** die Option **Privates Repository** als Repository-Typ fest.

   ![Eigenes Repository hinzufügen](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. Geben Sie in jedem Feld jeweils die folgenden Details zu Ihrem Repository an:

   | Feld | Beschreibung |
   | --- | --- |
   | Repository-Name | Ein aussagekräftiger Name für Ihr neues Repository. |
   | Repository-URL | Die URL des privaten Repositorys, die auf `.git` enden muss (<br>. B. *`https://github.com/org-name/repo-name.git`* (URL-Pfad dient nur zu Veranschaulichungszwecken). |
   | Beschreibung (optional) | Eine längere Beschreibung des Repositorys. |

1. Wählen Sie **Speichern** aus.
Jetzt können Sie [den Besitz des privaten Repositorys überprüfen](#validate-ownership).

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).


### Überprüfen der Eigentümerschaft des privaten GitHub-Repositorys {#validate-ownership}

Cloud Manager ist jetzt mit Ihrem GitHub-Repository konfiguriert, erfordert jedoch weiterhin eine Autorisierung für den Zugriff auf das Repository. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümerin bzw. Eigentümer des angegebenen Repositorys sind.

**So überprüfen Sie die Eigentümerschaft eines privaten GitHub-Repositorys:**

1. Nachdem Sie Ihr Repository hinzugefügt haben, führen Sie die verbleibenden Schritte im Dialogfeld **Validierung des privaten Repositorys** aus.

   ![Validierung der Eigentümerschaft eines privaten Repositorys](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

   |  | Beschreibung |
   | --- | --- |
   | **Schritt 1: GitHub-App** | Cloud Manager verwendet eine GitHub-App, um sicher mit Ihrem privaten Repository zu interagieren.<br>・ Der Eigentümer Ihres GitHub-Unternehmens muss die App unter `https://github.com/apps/cloud-manager-for-aem` installieren und Zugriff auf das Repository gewähren.<br>・ Einzelheiten zur Installation und Gewährung des Zugriffs finden Sie in der GitHub-Dokumentation. |
   | **Schritt 2: Geheime Datei** | Zur Erhöhung der Sicherheit müssen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys erstellen.<br>・ Klicken Sie auf **Generieren** und dann auf **Bestätigen**. Cloud Manager generiert den Inhalt der privaten Datei im Textfeld **Geheime Dateiinhalte**.<br>・ Klicken Sie auf ![Symbol „Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Inhalt aus diesem Feld zu kopieren. Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht kopieren, bevor Sie dieses Dialogfeld schließen, müssen Sie die geheime Datei neu generieren. |

1. Erstellen Sie eine neue Datei mit dem Namen in der Standardverzweigung Ihres GitHub-Repositorys

   `.well-known/adobe/cloud-manager-challenge`

1. Fügen Sie den Inhalt der geheimen Datei in die neue Datei ein und speichern Sie sie.

   Nachdem die App installiert wurde und die geheime Datei im Repository vorhanden ist, fahren Sie mit den Schritten fort.

1. Klicken Sie im Dialogfeld **Validierung der Eigentümerschaft des privaten Repositorys** auf **Überprüfen**.

Die App kann installiert und eine geheime Datei in jeder beliebigen Reihenfolge erstellt werden. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung wird das Repository mit einem roten Symbol angezeigt, was darauf hinweist, dass es noch nicht validiert wurde und nicht zur Verwendung verfügbar ist.

![Nicht validiertes Repo](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

Die Spalte **Typ** in der Tabelle auf der Seite **Repositorys** kennzeichnet die von Adobe bereitgestellten Repositorys (**Adobe**) und Ihre eigenen privaten Repositorys (**GitHub**) entsprechend.

Um später auf das Repository zuzugreifen und die Validierung abzuschließen, klicken Sie auf der Seite **Repositorys** auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) in der Zeile, die das hinzugefügte GitHub-Repository darstellt. Wählen Sie in der Dropdown-Liste **Validierung der Eigentümerschaft** aus.


## Verwenden privater GitHub-Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen. Sie können jetzt das Repository mit Cloud Manager verwenden.

**So verwenden Sie private GitHub-Repositorys mit Cloud Manager:**

1. Beim Erstellen einer Pull-Anfrage wird automatisch eine GitHub-Prüfung ausgeführt.

   ![GitHub-Prüfungen](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Für jede Pull-Anfrage wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

1. Die GitHub-Prüfung verbleibt im Status „Wird ausgeführt“, bis die Code-Qualitätsprüfungen abgeschlossen sind. Die Code-Qualitätsergebnisse werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Wenn die Pull-Anfrage zusammengeführt oder geschlossen wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

>[!TIP]
>
>Siehe [GitHub-Check](github-annotations.md)Anmerkungen) für Details zu den Informationen, die über GitHub bereitgestellt werden, wenn Pull-Anfrage-Prüfungen ausgeführt werden.

>[!TIP]
>
>Sie können die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren. Weitere Informationen finden Sie unter [Konfiguration der GitHub-Prüfung für private Repositorys](github-check-config.md).


## Verknüpfen privater GitHub-Repositorys mit Pipelines {#pipelines}

Validierte private Repositorys können [Full-Stack- und Frontend-Pipelines zugeordnet werden](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).



## Einschränkungen {#limitations}

Die folgenden Einschränkungen gelten für die Verwendung privater Repositorys mit Cloud Manager.

* Bei Verwendung privater Repositorys in Full-Stack-Produktions-Pipelines wird kein Git-Tag erstellt und gepusht.
* Wenn die Adobe-GitHub-App aus Ihrer GitHub-Organisation entfernt wird, wird die Pull-Anforderung-Validierungsfunktion für alle Repositorys entfernt.
* Pipelines, die private GitHub-Repositorys verwenden und den Build-Trigger „on-commit“ verwenden, werden nicht automatisch gestartet, wenn ein neuer Commit in die ausgewählte Verzweigung gepusht wird.
* Die [Funktion zur Wiederverwendung von Artefakten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) gilt nicht für private Repositorys.
* Sie können die Validierung der Pull-Anfrage nicht mithilfe der GitHub-Prüfung über Cloud Manager anhalten. Während der Validierung des GitHub-Repositorys in Cloud Manager versucht Cloud Manager immer, die für dieses Repository erstellten Pull-Anfragen zu validieren.
* Wenn Ihre GitHub-Organisation IP-Einschränkungen durchsetzt, erstellen Sie einen Support-Fall, um die Liste der zuzulassen IP-Adressen zu erhalten.
