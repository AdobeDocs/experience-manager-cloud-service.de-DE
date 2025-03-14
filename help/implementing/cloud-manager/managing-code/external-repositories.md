---
title: Hinzufügen externer Repositorys in Cloud Manager - Eingeschränkte Betaversion
description: Erfahren Sie, wie Sie in Cloud Manager ein externes Repository hinzufügen. Cloud Manager unterstützt die Integration mit GitHub Enterprise Server-, GitLab- und Bitbucket-Repositorys.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: aebda813-2eb0-4c67-8353-6f8c7c72656c
source-git-commit: bfa059ed4e3f04ae6ee1e07910edc62635b03e5a
workflow-type: tm+mt
source-wordcount: '1597'
ht-degree: 44%

---

# Hinzufügen externer Repositorys in Cloud Manager - Eingeschränkte Betaversion {#external-repositories}

Erfahren Sie, wie Sie in Cloud Manager ein externes Repository hinzufügen. Cloud Manager unterstützt die Integration mit GitHub Enterprise Server-, GitLab- und Bitbucket-Repositorys.

>[!NOTE]
>
>Diese Funktion ist nur für das Early-Adopter-Programm verfügbar. Weitere Informationen und die Möglichkeit, sich als Early Adopter anzumelden, finden Sie unter [Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket](/help/implementing/cloud-manager/release-notes/2024/2024-10-0.md#gitlab-bitbucket).

## Konfigurieren eines externen Repositorys

Die Konfiguration eines externen Repositorys in Cloud Manager erfolgt in drei Schritten:

1. Fügen Sie einem ausgewählten Programm [ein externes Repository hinzu](#add-external-repo).
1. Stellen Sie ein Zugriffs-Token für das externe Repository bereit.
1. Überprüfen Sie die Eigentümerschaft des privaten GitHub-Repositorys.



## Hinzufügen eines externen Repositorys {#add-ext-repo}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus, mit dem Sie ein externes Repository verknüpfen möchten.

1. Klicken Sie im Seitenmenü unter **Dienste** auf ![Ordnergliederungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorys**.

   ![Die Seite „Repositorys“](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Klicken Sie oben rechts auf der Seite **Repositorys** auf **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** die Option **Privates Repository** aus, um ein externes Git-Repository mit Ihrem Programm zu verknüpfen.

   ![Eigenes Repository hinzufügen](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png)

1. Geben Sie in jedem Feld jeweils die folgenden Details zu Ihrem Repository an:

   | Feld | Beschreibung |
   | --- | --- |
   | **Repository-Name** | Erforderlich. Ein aussagekräftiger Name für Ihr neues Repository. |
   | **Repository-URL** | Erforderlich. Die URL des Repositorys.<br><br>Wenn Sie ein von GitHub gehostetes Repository verwenden, muss der Pfad mit `.git` enden.<br>Beispiel: *`https://github.com/org-name/repo-name.git`* (URL-Pfad dient nur zu Illustrationszwecken).<br><br>Wenn Sie ein externes Repository verwenden, muss es das folgende URL-Pfadformat verwenden:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> oder <br>`https://self-hosted-domain/org-name/repo-name.git`<br>. Außerdem muss es mit Ihrem Git-Anbieter übereinstimmen. |
   | **Repository-Typ auswählen** | Erforderlich. Wählen Sie den verwendeten Repository-Typ aus:<ul><li>**GitHub** (GitHub Enterprise Server und die selbst gehostete Version von GitHub)</li><li>**GitLab** (sowohl `gitlab.com` als auch die selbst gehostete Version von GitLab) </li><li>**Bitbucket** (sowohl `bitbucket.org` als auch Bitbucket Server und die selbst gehostete Version von Bitbucket)</li></ul>Wenn der obige Repository-URL-Pfad den Namen des Git-Anbieters enthält, z. B. GitLab oder Bitbucket, ist der Repository-Typ bereits für Sie vorausgewählt. |
   | **Beschreibung** | Optional. Eine längere Beschreibung des Repositorys. |

1. Wählen Sie **Speichern**, um das Repository hinzuzufügen.

1. Geben Sie im Dialogfeld **Validierung der Eigentümerschaft eines privaten Repositorys** ein Zugriffs-Token an, um die Eigentümerschaft des externen Repositorys zu validieren, sodass Sie darauf zugreifen können.

   ![Auswählen eines vorhandenen Zugriffs-Tokens für ein Repository](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *Auswählen eines vorhandenen Zugriffstokens für ein Bitbucket-Repository.*

   | Token-Typ | Beschreibung |
   | --- | --- |
   | **Vorhandenes Zugriffs-Token verwenden** | Wenn Sie bereits ein Repository-Zugriffs-Token für Ihre Organisation bereitgestellt haben und Zugriff auf mehrere Repositorys haben, können Sie ein vorhandenes Token auswählen. Verwenden Sie die Dropdown-Liste **Tokenname**, um das Token auszuwählen, das Sie auf das Repository anwenden möchten. Fügen Sie andernfalls ein neues Zugriffs-Token hinzu. |
   | **Neues Zugriffs-Token hinzufügen** | **Repository-Typ: GitHub**<br>• Geben Sie im Textfeld **Tokenname** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<br>• Erstellen Sie ein persönliches Zugriffs-Token, indem Sie die Anweisungen in der [GitHub-Dokumentation](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) befolgen.<br>・ Die erforderlichen Berechtigungen finden Sie in den folgenden Informationen: ![Neuen PFAD für GitHub erstellen](/help/implementing/cloud-manager/managing-code/assets/webhook-github-enterprise-server.png)<br>・ Fügen Sie im Feld **Zugriffstoken** das soeben erstellte Token ein. |
   |  | **Repository-Typ: GitLab**<br>• Geben Sie im Textfeld **Tokenname** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<br>• Erstellen Sie ein persönliches Zugriffs-Token, indem Sie die Anweisungen in der [GitLab-Dokumentation](https://docs.gitlab.com/user/profile/personal_access_tokens/) befolgen.<br>・ Die erforderlichen Berechtigungen finden Sie in den folgenden Informationen: ![Erstellen eines neuen PFADS für GitLab](/help/implementing/cloud-manager/managing-code/assets/webhook-gitlab.png)<br>・ Fügen Sie im Feld **Zugriffstoken** das soeben erstellte Token ein. |
   |  | **Repository-Typ: Bitbucket**<br>• Geben Sie im Textfeld **Tokenname** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<br>• Erstellen Sie ein Repository-Zugriffs-Token mithilfe der [Bitbucket-Dokumentation](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>・ Die erforderlichen Berechtigungen finden Sie in den folgenden Informationen ![Erstellen eines neuen PATH für Bitbucket](/help/implementing/cloud-manager/managing-code/assets/webhook-bitbucket.png). |

   >[!NOTE]
   >
   >Die Funktion „**Neues Zugriffs-Token hinzufügen**“ befindet sich derzeit in der Early-Adopter-Phase. Zusätzliche Funktionen sind in Planung. Daher können sich die erforderlichen Berechtigungen für Zugriffs-Token ändern. Darüber hinaus kann die Benutzeroberfläche für die Verwaltung von Token aktualisiert werden, möglicherweise einschließlich Funktionen wie Ablaufdaten von Token. Dazu gehören auch automatisierte Prüfungen, um sicherzustellen, dass mit Repositorys verknüpfte Token gültig bleiben.

1. Klicken Sie auf **Überprüfen**.

Nach der Überprüfung kann das externe Repository verwendet und mit einer Pipeline verknüpft werden.

## Verknüpfen eines validierten externen Repositorys mit einer Pipeline {#validate-ext-repo}

1. Hinzufügen oder Bearbeiten einer Pipeline:
   * [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * [Bearbeiten einer Pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#editing-pipelines)

   ![Quell-Code-Repository der Pipeline und Git-Verzweigung](/help/implementing/cloud-manager/managing-code/assets/pipeline-repo-gitbranch.png)
   *Dialogfeld „Produktionsfremde Pipeline hinzufügen“ mit ausgewähltem Repository und Git-Verzweigung*

1. Wählen Sie beim Hinzufügen oder Bearbeiten einer Pipeline zum Angeben des **Quell-Code**-Speicherorts für die neue oder vorhandene Pipeline das zu verwendende externe Repository aus der Dropdown-Liste **Repository** aus.

1. Wählen Sie in der Dropdown-Liste **Git-Verzweigung** die Verzweigung als Quelle für die Pipeline aus.

1. Klicken Sie auf **Speichern**.


>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

## Webhook für ein externes Repository konfigurieren {#configure-webhook}

Mit Cloud Manager können Sie Webhooks für externe Git-Repositorys konfigurieren, die Sie hinzugefügt haben. Siehe [Externes Repository hinzufügen](#add-ext-repo). Diese Webhooks ermöglichen es Cloud Manager, Ereignisse zu empfangen, die sich auf verschiedene Aktionen in Ihrer Git-Anbieterlösung beziehen.

Webhooks ermöglichen es Cloud Manager beispielsweise, Trigger auf der Grundlage von Ereignissen wie den folgenden auszuführen:

* Erstellung einer Pull-Anfrage (PR) - Startet die PR-Validierungsfunktion.
* Push-Ereignisse : Startet Pipelines, wenn der Trigger „Bei Git-Commit“ aktiviert ist.
* Künftige kommentarbasierte Aktionen - Ermöglicht Workflows, z. B. die direkte Bereitstellung aus einer PR in einer schnellen Entwicklungsumgebung (RDE).

Die Webhook-Konfiguration ist für auf `GitHub.com` gehostete Repositorys nicht erforderlich, da Cloud Manager direkt über die GitHub-App integriert wird.
Für alle anderen externen Repositorys, die mit einem Zugriffstoken integriert sind, wie GitHub Enterprise Server, GitLab und Bitbucket, ist eine Webhook-Konfiguration verfügbar und muss manuell eingerichtet werden.

**So konfigurieren Sie einen Webhook für ein externes Repository:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in **[Konsole &quot;](/help/implementing/cloud-manager/navigation.md#my-programs)**&quot; das Programm aus, für das Sie einen Webhook für ein externes Git-Repository konfigurieren möchten.

1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.

1. Klicken Sie im linken Menü unter der Überschrift **Programm** auf ![Ordnergliederungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorys**.

1. Suchen Sie auf der **Repositorys** mithilfe der Spalte **Typ** das gewünschte Repository und klicken Sie dann neben ![ Symbol Auslassungspunkte - Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![Webhook-Option im Dropdown-Menü für ein ausgewähltes Repository konfigurieren](/help/implementing/cloud-manager/managing-code/assets/repository-config-webhook.png)

1. Klicken Sie im Dropdown-Menü auf **Webhook**.

   ![Dialogfeld „Webhook konfigurieren“](/help/implementing/cloud-manager/managing-code/assets/config-webhook.png)

1. Gehen Sie **Dialogfeld** Webhook konfigurieren“ wie folgt vor:

   1. Klicken Sie neben dem Feld **Webhook** URL) auf ![Symbol „Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Fügen Sie die URL in eine Textdatei ein. Die kopierte URL ist für die Webhook-Einstellungen Ihres Git-Anbieters erforderlich.
   1. Klicken Sie neben dem Feld **Webhook** Geheimnis) auf **Generieren** und dann auf ![Symbol „Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Fügen Sie die geheimen Daten in eine Textdatei ein. Das kopierte Geheimnis ist für die Webhook-Einstellungen Ihres Git-Anbieters erforderlich.
1. Klicken Sie auf **Schließen**.
1. Navigieren Sie zu Ihrer Git-Anbieterlösung (GitHub Enterprise, GitLab oder Bitbucket).

   Alle Details zur Webhook-Konfiguration und die für jeden Anbieter erforderlichen Ereignisse finden Sie unter „Hinzufügen [ externen Repositorys](#add-ext-repo). Beachten Sie unter Schritt 8 die Tabelle.

1. Suchen Sie den Abschnitt **Webhook**-Einstellungen der Lösung.
1. Fügen Sie die zuvor kopierte Webhook-URL in das Textfeld URL ein.
   1. Ersetzen Sie den `api_key` Abfrageparameter in der Webhook-URL durch Ihren eigenen echten API-Schlüssel.

      Um einen API-Schlüssel zu generieren, müssen Sie ein Integrationsprojekt in Adobe Developer Console erstellen. Ausführliche [ finden Sie unter „Erstellen ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) API-Integrationsprojekts“.

1. Fügen Sie das zuvor kopierte Webhook-Geheimnis in das Textfeld **Geheimnis** (oder **Geheimer Schlüssel** oder **Geheimer**) ein.
1. Konfigurieren Sie den Webhook so, dass die von Cloud Manager erwarteten Ereignisse gesendet werden.


### Validierung von Pull Requests mit Webhooks

Wenn Webhooks korrekt konfiguriert sind, führt Cloud Manager Trigger automatisch Pipeline-Ausführungen oder PR-Validierungsprüfungen für Ihr Repository durch.

Es gelten die folgenden Verhaltensweisen:

* **GitHub Enterprise Server**

  Wenn die Prüfung erstellt wird, sieht sie wie der folgende Screenshot aus. Der wesentliche Unterschied zu `GitHub.com` besteht darin, dass `GitHub.com` einen Check-Run verwendet, während GitHub Enterprise Server (unter Verwendung von persönlichen Zugriffstoken) einen Commit-Status generiert:

  ![Commit-Status, um den PR-Validierungsprozess auf GitHub Enterprise Server anzugeben](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-github-pr-validation.png)

* **Bitbucket**

  Wenn die Überprüfung der Code-Qualität ausgeführt wird:

  ![Status während der Überprüfung der Code-Qualität](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket1.png)

  Verwendet Commit-Status zum Verfolgen des PR-Validierungsfortschritts. Im folgenden Fall zeigt der Screenshot, was passiert, wenn eine Code-Qualitätsprüfung aufgrund eines Kundenproblems fehlschlägt. Es wird ein Kommentar mit detaillierten Fehlerinformationen hinzugefügt und eine Commit-Prüfung erstellt, die den Fehler anzeigt (rechts sichtbar):

  ![Validierungsstatus der Pull-Anfrage für Bitbucket](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket2.png)

* **GitLab**

  GitLab-Interaktionen basieren ausschließlich auf Kommentaren. Wenn die Validierung beginnt, wird ein Kommentar hinzugefügt. Nach Abschluss der Validierung (ob erfolgreich oder fehlgeschlagen) wird der ursprüngliche Kommentar entfernt und durch einen neuen Kommentar mit Validierungsergebnissen oder Fehlerdetails ersetzt.

  Wenn die Überprüfung der Code-Qualität ausgeführt wird:

  ![Wenn die Überprüfung der Code-Qualität ausgeführt wird](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab1.png)

  Wenn die Validierung der Kaltqualität abgeschlossen ist:

  ![Wenn die Validierung der Kaltqualität abgeschlossen ist](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab2.png)

  Wenn die Überprüfung der Code-Qualität mit einem Fehler fehlschlägt:

  ![Wenn die Überprüfung der Code-Qualität mit einem Fehler fehlschlägt](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab3.png)

  Wenn die Überprüfung der Code-Qualität aufgrund von Kundenproblemen fehlschlägt:

  ![Wenn die Überprüfung der Code-Qualität aufgrund von Kundenproblemen fehlschlägt](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab4.png)


## Fehlerbehebung bei Webhook-Problemen

* Stellen Sie sicher, dass die Webhook-URL einen gültigen API-Schlüssel enthält.
* Vergewissern Sie sich, dass Webhook-Ereignisse in Ihren Git-Anbietereinstellungen korrekt konfiguriert sind.
* Wenn die PR-Validierung oder die Pipeline-Trigger nicht funktionieren, stellen Sie sicher, dass das Webhook-Geheimnis sowohl in Cloud Manager als auch bei Ihrem Git-Anbieter auf dem neuesten Stand ist.








## Einschränkungen

* Externe Repositorys können nicht mit Konfigurations-Pipelines verknüpft werden.
* Pipelines mit externen Repositorys (die nicht von GitHub gehostet werden) und der Auslöser „Bei Git-Änderungen“ starten nicht automatisch. Sie können nur manuell gestartet werden.


<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


