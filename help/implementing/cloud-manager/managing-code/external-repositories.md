---
title: Hinzufügen von externen Repositorys in Cloud Manager (Early Adopter)
description: Erfahren Sie, wie Sie in Cloud Manager ein externes Repository hinzufügen. Cloud Manager unterstützt die Integration mit GitHub-, GitLab- und Bitbucket-Repositorys.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: aebda813-2eb0-4c67-8353-6f8c7c72656c
source-git-commit: bd05433bb4d92a4120b19ad99d211a4a5e1f06ca
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 95%

---

# Hinzufügen von externen Repositorys in Cloud Manager {#external-repositories}

Erfahren Sie, wie Sie in Cloud Manager ein externes Repository hinzufügen. Cloud Manager unterstützt die Integration mit GitHub-, GitLab- und Bitbucket-Repositorys.

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

1. Wählen Sie im Seitenmenü unter **Services** ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorys** aus.

   ![Die Seite „Repositorys“](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Klicken Sie oben rechts auf der Seite **Repositorys** auf **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** die Option **Privates Repository** aus, um ein externes Git-Repository mit Ihrem Programm zu verknüpfen.

   ![Eigenes Repository hinzufügen](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png)

1. Geben Sie in jedem Feld jeweils die folgenden Details zu Ihrem Repository an:

   | Feld | Beschreibung |
   | --- | --- |
   | **Repository-Name** | Erforderlich. Ein aussagekräftiger Name für Ihr neues Repository. |
   | **Repository-URL** | Erforderlich. Die URL des Repositorys.<br><br>Wenn Sie ein von GitHub gehostetes Repository verwenden, muss der Pfad auf `.git` enden.<br>Beispiel: *`https://github.com/org-name/repo-name.git`* (URL-Pfad dient nur zu Illustrationszwecken).<br><br>Wenn Sie ein externes Repository verwenden, muss es das folgende URL-Pfadformat verwenden:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> oder <br>`https://self-hosted-domain/org-name/repo-name.git`<br>. Außerdem muss es mit Ihrem Git-Anbieter übereinstimmen. |
   | **Repository-Typ auswählen** | Erforderlich. Wählen Sie den von Ihnen verwendeten Repository-Typ aus: **GitHub**, **GitLab** oder **BitBucket**. Wenn der obige Repository-URL-Pfad den Namen des Git-Anbieters enthält, z. B. GitLab oder Bitbucket, ist der Repository-Typ bereits für Sie vorausgewählt. |
   | **Beschreibung** | Optional. Eine längere Beschreibung des Repositorys. |

1. Wählen Sie **Speichern**, um das Repository hinzuzufügen.

1. Geben Sie im Dialogfeld **Validierung der Eigentümerschaft eines privaten Repositorys** ein Zugriffs-Token an, um die Eigentümerschaft des externen Repositorys zu validieren, sodass Sie darauf zugreifen können.

   ![Auswählen eines vorhandenen Zugriffs-Tokens für ein Repository](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *Auswählen eines vorhandenen Zugriffs-Tokens für ein BitBucket-Repository.*

   | Token-Typ | Beschreibung |
   | --- | --- |
   | **Vorhandenes Zugriffs-Token verwenden** | Wenn Sie bereits ein Repository-Zugriffs-Token für Ihre Organisation bereitgestellt haben und Zugriff auf mehrere Repositorys haben, können Sie ein vorhandenes Token auswählen. Verwenden Sie die Dropdown-Liste **Tokenname**, um das Token auszuwählen, das Sie auf das Repository anwenden möchten. Fügen Sie andernfalls ein neues Zugriffs-Token hinzu. |
   | **Neues Zugriffs-Token hinzufügen** | **Repository-Typ: GitHub**<br>• Geben Sie im Textfeld **Tokenname** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<br>• Erstellen Sie ein persönliches Zugriffs-Token, indem Sie die Anweisungen in der [GitHub-Dokumentation](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) befolgen.<br>• Erforderliche Berechtigungen:<br>  • `Read access to metadata`.<br>  • `Read and write access to code and pull requests`.<br>• Fügen Sie im Feld **Zugriffs-Token** das soeben erstellte Token ein. |
   |  | **Repository-Typ: GitLab**<br>• Geben Sie im Textfeld **Tokenname** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<br>• Erstellen Sie ein persönliches Zugriffs-Token, indem Sie die Anweisungen in der [GitLab-Dokumentation](https://docs.gitlab.com/user/profile/personal_access_tokens/) befolgen.<br>• Erforderliche Berechtigungen:<br>  • `api`<br>  • `read_api`<br>  • `read_repository`<br>  • `write_repository`<br>• Fügen Sie im Feld **Zugriffs-Token** das soeben erstellte Token ein. |
   |  | **Repository-Typ: Bitbucket**<br>• Geben Sie im Textfeld **Tokenname** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<br>• Erstellen Sie ein Repository-Zugriffs-Token mithilfe der [Bitbucket-Dokumentation](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>• Erforderliche Berechtigungen:<br>  • `Read and write access to code and pull requests`. |

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


## Einschränkungen

* Externe Repositorys können nicht mit Konfigurations-Pipelines verknüpft werden.
* Pipelines mit externen Repositorys (nicht auf GitHub gehostet) und dem Trigger „Bei Git-Änderungen“ werden nicht automatisch gestartet. Sie können nur manuell initiiert werden.


<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->
