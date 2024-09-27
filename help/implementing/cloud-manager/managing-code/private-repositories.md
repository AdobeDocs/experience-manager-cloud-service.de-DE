---
title: Hinzufügen privater GitHub-Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: eb2e1555f684a68807b0b3764cd1be03c2d439ab
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 37%

---

# Hinzufügen von privaten Repositorys in Cloud Manager {#private-repositories}

Durch die Einrichtung von Cloud Manager zur Integration in Ihre privaten GitHub-Repositorys können Sie Ihren Code direkt in GitHub mithilfe von Cloud Manager validieren. Durch diese Konfiguration wird die Anforderung entfernt, Ihren Code regelmäßig mit dem Adobe-Repository zu synchronisieren.

<!-- CONSIDER ADDING MORE DETAIL... THE WHY. Some key points about this capability include the following:

* **Direct Integration**: With this setup, you can directly link your private GitHub repositories to Cloud Manager, allowing for seamless code validation, deployment, and CI/CD (Continuous Integration/Continuous Deployment) pipelines without needing to maintain a separate sync process with Adobe's default Git repository.

* **Customization and Autonomy**: Companies often prefer managing their own source code repositories for security, control, and integration purposes. "Build your own GitHub" allows organizations to maintain their internal development processes while leveraging the full functionality of Cloud Manager for building, testing, and deploying AEM (Adobe Experience Manager) applications.

* **Simplified Workflow**: It reduces the overhead of synchronizing code between multiple repositories by allowing Cloud Manager to access the organization's private repository directly, making the development cycle faster and more efficient.

* **CI/CD Pipelines**: Teams can still benefit from Adobe Cloud Manager's automated build, test, and deployment processes, as the integration allows the CI/CD pipelines to pull code from the organization's own GitHub repository.

In essence, a "Build your own GitHub" in Adobe Cloud Manager empowers teams to manage their own GitHub repositories while still using the robust deployment and validation capabilities of Cloud Manager. -->

>[!NOTE]
>
>Diese Funktion ist nur für öffentliche GitHub-Repositorys verfügbar. Unterstützung für selbstgehostetes GitHub-Repositorys ist nicht verfügbar.

## Konfiguration {#configuration}

Die Konfiguration eines privaten Repositorys in Cloud Manager erfolgt in zwei Schritten:

1. [Fügen Sie ein privates Repository hinzu](#add-repo), um es einem ausgewählten Programm hinzuzufügen.
1. Dann validieren Sie [ das Eigentum des privaten Repositorys.](#validate-ownership)

### Hinzufügen eines privaten Repositorys zu einem Programm {#add-repo}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus, mit dem Sie ein privates Git-Repository verknüpfen möchten.

1. Wählen Sie im Seitenmenü unter **Dienste** das Symbol ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorys**.

   ![Die Seite &quot;Repositorys&quot;](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Klicken Sie in der rechten oberen Ecke der Seite **Repositorys** auf **Repository hinzufügen**.

1. Legen Sie im Dialogfeld **Repository hinzufügen** die Option **Privates Repository** als Repository-Typ fest.

   ![Eigenes Repository hinzufügen](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. Geben Sie in jedem Feld die folgenden Details zu Ihrem Repository an:

   | Feld | Beschreibung |
   | --- | --- |
   | Repository-Name | Ein ausdrucksstarker Name für Ihr neues Repository. |
   | Repository-URL | Die URL des privaten Repositorys, die in `.git` enden muss.<br>Beispiel: *`https://github.com/org-name/repo-name.git`* (URL-Pfad dient nur zu Veranschaulichungszwecken). |
   | Beschreibung (optional) | Eine detaillierte Beschreibung des Repositorys. |

1. Wählen Sie **Speichern** aus.
Jetzt können Sie [das Eigentum des privaten Repositorys überprüfen](#validate-ownership).

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

### Überprüfen des Eigentums am privaten Repository {#validate-ownership}

Cloud Manager kennt jetzt Ihr GitHub-Repository, benötigt aber noch den Zugriff darauf. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümerin bzw. Eigentümer des angegebenen Repositorys sind.

**Überprüfen des Eigentums am privaten Repository:**

1. Nachdem Sie Ihr eigenes Repository hinzugefügt haben, führen Sie die verbleibenden Schritte im Dialogfeld **Validierung der privaten Repository-Eigentümerschaft** aus.

   ![Validierung der Eigentümerschaft eines privaten Repositorys](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

   |  | Beschreibung |
   | --- | --- |
   | **Schritt 1: GitHub-App** | Cloud Manager verwendet eine GitHub-App, um sicher mit Ihrem privaten Repository zu interagieren.<br> ・ Ein Eigentümer Ihrer GitHub-Organisation muss die App unter `https://github.com/apps/cloud-manager-for-aem` installieren und Zugriff auf das Repository gewähren.<br> ・ Einzelheiten zur Installation und Gewährung des Zugriffs finden Sie in der GitHub-Dokumentation. |
   | **Schritt 2: Geheime Datei** | Um die Sicherheit zu erhöhen, müssen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys erstellen.<br> ・ auf **Erzeugen** und klicken Sie dann auf **Bestätigen**. Cloud Manager generiert den Inhalt der privaten Datei im Textfeld **Geheimer Dateiinhalt** .<br> ・ Klicken Sie auf das Symbol ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) , um den Inhalt aus diesem Feld zu kopieren. Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht kopieren, bevor Sie dieses Dialogfeld schließen, generieren Sie den geheimen Schlüssel erneut. |

1. Erstellen Sie im Standardzweig Ihres GitHub-Repositorys eine neue Datei mit dem Namen:

   `.well-known/adobe/cloud-manager-challenge`

1. Fügen Sie den geheimen Dateiinhalt in die soeben erstellte Datei ein und speichern Sie sie.

   Sobald die App installiert ist und die geheime Datei im Repository vorhanden ist, fahren Sie mit dem Schritt fort.

1. Klicken Sie im Dialogfeld **Validierung der Eigentümerschaft des privaten Repositorys** auf **Validieren**.

Die App kann installiert und eine geheime Datei kann in beliebiger Reihenfolge erstellt werden. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung ist das Repository mit einem roten Symbol gekennzeichnet. Dies bedeutet, dass es noch nicht validiert wurde und noch nicht verwendet werden kann.

![Nicht validiertes Repo](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

Die Spalte **Typ** in der Tabelle auf der Seite **Repositorys** gibt Adobe-bereitgestellte Repositorys (**Adobe**) und Ihre eigenen privaten Repositorys (**GitHub**) an.

Wenn Sie später zum Repository zurückkehren müssen, um die Überprüfung abzuschließen, klicken Sie auf der Seite **Repositorys** in der Zeile, die das gerade hinzugefügte GitHub-Repository darstellt, auf das Symbol ![Mehr ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) . Wählen Sie in der Dropdown-Liste **Besitzvalidierung** aus.

## Verwenden privater Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen. Sie können das Repository mit Cloud Manager verwenden.

**So verwenden Sie ein privates Repository mit Cloud Manager:**

1. Beim Erstellen einer Pull-Anfrage wird automatisch eine GitHub-Prüfung ausgeführt.

   ![GitHub-Prüfungen](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Für jede Pull-Anfrage wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

1. Die GitHub-Prüfung verbleibt im Status &quot;Wird ausgeführt&quot;, bis die Code-Qualitätsprüfung abgeschlossen ist. Die Code-Qualitätsergebnisse werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Wenn die Pull-Anforderung zusammengeführt oder geschlossen wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

>[!TIP]
>
>Weitere Informationen zu den Informationen, die von GitHub bereitgestellt werden, wenn Prüfungen von Pull-Anforderungen ausgeführt werden, finden Sie unter [GitHub-Prüfungen für Anmerkungen](github-annotations.md) .

>[!TIP]
>
>Sie können die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren. Weitere Informationen finden Sie unter [Konfiguration der GitHub-Prüfung für private Repositorys](github-check-config.md).

## Zuordnen von privaten Repositorys zu Pipelines {#pipelines}

Validierte private Repositorys können [Full-Stack- und Frontend-Pipelines zugeordnet werden](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

>[!NOTE]
>
>Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt.

## Einschränkungen {#limitations}

Bei der Verwendung privater Repositorys mit Cloud Manager gelten bestimmte Einschränkungen.

* Sie können die Überprüfung der Pull-Anforderung nicht mithilfe der GitHub-Prüfung von Cloud Manager anhalten.
Wenn das GitHub-Repository in Cloud Manager validiert wird, versucht Cloud Manager immer, die für dieses Repository erstellten Pull-Anforderungen zu überprüfen.
* Wenn die Adobe GitHub-App aus Ihrer GitHub-Organisation entfernt wird, wird die Überprüfungsfunktion für Pull-Anforderungen für alle Repositorys entfernt.
* Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt.
* Bei Verwendung privater Repositorys in Full-Stack-Produktions-Pipelines wird kein Git-Tag erstellt und gesendet.
* Pipelines, die private Repositorys und den On-Commit-Build-Trigger verwenden, werden nicht automatisch gestartet, wenn ein neues Commit in die ausgewählte Verzweigung verschoben wird.
* Die [Funktion zur Wiederverwendung von Artefakten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) gilt nicht für private Repositorys.
