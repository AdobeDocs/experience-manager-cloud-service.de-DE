---
title: Hinzufügen eines privaten GitHub-Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 7ce39020870943243e2d48aa66370f2cca9c2ac0
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 81%

---

# Hinzufügen eines privaten GitHub-Cloud-Repositorys in Cloud Manager {#private-repositories}

Durch die Einrichtung von Cloud Manager für die Integration mit Ihrer privaten GitHub-Cloud (auf `github.com` gehostete Repositorys) können Sie Ihren Code mithilfe von Cloud Manager direkt in GitHub validieren. Mit dieser Konfiguration müssen Sie Ihren Code nicht mehr regelmäßig mit dem Adobe-Repository synchronisieren.

>[!NOTE]
>
>Sie können auch die folgenden Repository-Typen mit Webhooks hinzufügen:
>
>* GitHub Enterprise Server (selbst gehostete Version von GitHub)-Repositorys
>* GitLab-Repositorys (sowohl `gitlab.com` als auch selbst gehostete Versionen von GitLab)
>* Bitbucket-Repositorys (sowohl `bitbucket.org` als auch Bitbucket Server, die selbst gehostete Version von BitBucket)
>
>Siehe [Hinzufügen externer Repositorys in Cloud Manager - Eingeschränkte Beta-Version](/help/implementing/cloud-manager/managing-code/external-repositories.md).

<!-- CONSIDER ADDING MORE DETAIL... THE WHY. Some key points about this capability include the following:

* **Direct Integration**: With this setup, you can directly link your private GitHub repositories to Cloud Manager, allowing for seamless code validation, deployment, and CI/CD (Continuous Integration/Continuous Deployment) pipelines without needing to maintain a separate sync process with Adobe's default Git repository.

* **Customization and Autonomy**: Companies often prefer managing their own source code repositories for security, control, and integration purposes. "Build your own GitHub" allows organizations to maintain their internal development processes while leveraging the full functionality of Cloud Manager for building, testing, and deploying AEM (Adobe Experience Manager) applications.

* **Simplified Workflow**: It reduces the overhead of synchronizing code between multiple repositories by allowing Cloud Manager to access the organization's private repository directly, making the development cycle faster and more efficient.

* **CI/CD Pipelines**: Teams can still benefit from Adobe Cloud Manager's automated build, test, and deployment processes, as the integration allows the CI/CD pipelines to pull code from the organization's own GitHub repository.

In essence, a "Build your own GitHub" in Adobe Cloud Manager empowers teams to manage their own GitHub repositories while still using the robust deployment and validation capabilities of Cloud Manager.

>[!NOTE]
>
>This feature is exclusive to public GitHub. Support for self-hosted GitHub is not available. -->

## Konfiguration {#configuration}

Die Konfiguration eines privaten GitHub-Cloud-Repositorys in Cloud Manager besteht aus zwei Schritten:

1. [Privates GitHub-Cloud-Repository hinzufügen](#add-repo) zu einem ausgewählten Programm hinzufügen.
1. Überprüfen Sie dann [die Eigentümerschaft des privaten GitHub-Cloud-Repositorys](#validate-ownership).



### Hinzufügen eines privaten GitHub-Cloud-Repositorys zu einem Programm {#add-repo}

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
   | Repository-URL | Die URL des privaten Repositorys, die mit `.git` enden muss.<br>Beispiel: *`https://github.com/org-name/repo-name.git`* (URL-Pfad dient nur zu Illustrationszwecken). |
   | Beschreibung (optional) | Eine längere Beschreibung des Repositorys. |

1. Wählen Sie **Speichern** aus.
Jetzt können Sie [die Eigentümerschaft des privaten Repositorys validieren](#validate-ownership).

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).


### Überprüfen der Eigentümerschaft des privaten GitHub-Repositorys {#validate-ownership}

Cloud Manager kennt jetzt Ihr GitHub-Repository, benötigt aber noch den Zugriff darauf. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümerin bzw. Eigentümer des angegebenen Repositorys sind.

**So überprüfen Sie die Eigentümerschaft eines privaten GitHub-Repositorys:**

1. Nachdem Sie Ihr eigenes Repository hinzugefügt haben, führen Sie die verbleibenden Schritte im Dialogfeld **Validierung der Eigentümerschaft eines privaten Repositorys** aus.

   ![Validierung der Eigentümerschaft eines privaten Repositorys](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

   |  | Beschreibung |
   | --- | --- |
   | **Schritt 1: GitHub-App** | Zur sicheren Interaktion mit Ihrem privaten Repository verwendet Cloud Manager eine GitHub-App.<br>• Eine Eigentümerin bzw. ein Eigentümer Ihrer GitHub-Organisation muss die App unter `https://github.com/apps/cloud-manager-for-aem` installieren und Zugriff auf das Repository gewähren.<br>• Einzelheiten zur Installation und Gewährung des Zugriffs finden Sie in der GitHub-Dokumentation. |
   | **Schritt 2: Geheime Datei** | Um die Sicherheit zu erhöhen, müssen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys erstellen. <br>• Klicken Sie auf **Generieren** und klicken Sie dann auf **Bestätigen**. Cloud Manager generiert den Inhalt der privaten Datei im Textfeld **Inhalt der geheimen Datei**.<br>• Klicken Sie auf das Symbol ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Inhalt aus diesem Feld zu kopieren. Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht kopieren, bevor Sie dieses Dialogfeld schließen, müssen Sie die geheime Datei neu generieren. |

1. Erstellen Sie in der Standardverzweigung Ihres GitHub-Repositorys eine neue Datei mit dem Namen:

   `.well-known/adobe/cloud-manager-challenge`

1. Fügen Sie den Inhalt der geheimen Datei in die soeben erstellte, neue Datei ein und speichern Sie sie.

   Sobald die App installiert und die geheime Datei im Repository vorhanden ist, fahren Sie mit dem Schritt fort.

1. Klicken Sie im Dialogfeld **Validierung der Eigentümerschaft des privaten Repositorys** auf **Überprüfen**.

Die Installation der App und die Erstellung der geheimen Datei kann in jeder beliebigen Reihenfolge erfolgen. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung ist das Repository mit einem roten Symbol gekennzeichnet. Dies bedeutet, dass es noch nicht validiert wurde und noch nicht verwendet werden kann.

![Nicht validiertes Repo](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

Die Spalte **Typ** in der Tabelle auf der Seite **Repositorys** kennzeichnet die von Adobe bereitgestellten Repositorys (**Adobe**) und Ihre eigenen privaten Repositorys (**GitHub**) entsprechend.

Wenn Sie später zum Repository zurückkehren müssen, um die Validierung abzuschließen, klicken Sie auf der Seite **Repositorys** in der Zeile, die das gerade hinzugefügte GitHub-Repository enthält, auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg). Wählen Sie in der Dropdown-Liste **Validierung der Eigentümerschaft** aus.



## Verwenden privater GitHub-Cloud-Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen. Sie können jetzt das Repository mit Cloud Manager verwenden.

**So verwenden Sie private GitHub-Cloud-Repositorys mit Cloud Manager:**

1. Beim Erstellen einer Pull-Anfrage wird automatisch eine GitHub-Prüfung ausgeführt.

   ![GitHub-Prüfungen](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Für jede Pull-Anfrage wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

1. Die GitHub-Prüfung verbleibt im Status „Wird ausgeführt“, bis die Code-Qualitätsprüfungen abgeschlossen sind. Die Code-Qualitätsergebnisse werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Wenn die Pull-Anfrage zusammengeführt oder geschlossen wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

>[!TIP]
>
>Im Dokument [Anmerkungen zur GitHub-Prüfung](github-annotations.md) finden Sie Details zu den Informationen, die bei der Ausführung von Pull-Anfrageprüfungen über GitHub bereitgestellt werden.

>[!TIP]
>
>Sie können die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren. Weitere Informationen finden Sie unter [Konfiguration der GitHub-Prüfung für private Repositorys](github-check-config.md).



## Verknüpfen privater GitHub-Cloud-Repositorys mit Pipelines {#pipelines}

Validierte private Repositorys können [Full-Stack- und Frontend-Pipelines zugeordnet werden](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).



## Einschränkungen {#limitations}

Bei der Verwendung privater GitHub-Cloud-Repositorys mit Cloud Manager gelten bestimmte Einschränkungen.

* Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt.
* Bei Verwendung privater Repositorys in Full-Stack-Produktions-Pipelines wird kein Git-Tag erstellt und gepusht.
* Wenn die Adobe-GitHub-App aus Ihrer GitHub-Organisation entfernt wird, wird dadurch die Funktion zur Validierung von Pull-Anfragen für alle Repositorys entfernt.
* Pipelines, die private GitHub-Cloud-Repositorys verwenden und den Build-Trigger „on-commit“ verwenden, werden nicht automatisch gestartet, wenn ein neuer Commit in die ausgewählte Verzweigung gepusht wird.
* Die [Funktion zur Wiederverwendung von Artefakten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) gilt nicht für private Repositorys.
* Sie können die Überprüfung der Pull-Anfrage nicht mithilfe der GitHub-Prüfung über Cloud Manager anhalten.
Während der Validierung des GitHub-Repositorys in Cloud Manager versucht Cloud Manager immer, die für dieses Repository erstellten Pull-Anfragen zu validieren.
