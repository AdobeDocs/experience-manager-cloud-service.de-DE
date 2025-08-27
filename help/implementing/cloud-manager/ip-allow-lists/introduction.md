---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen aus Benutzende auf Domains in AEM as a Cloud Service zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f1e9b76742c8d97f44ff974fb8686fdcb3d804e6
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 99%

---


# Einführung in IP-Zulassungslisten {#introduction}

Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen aus Benutzende auf Domains in AEM as a Cloud Service zugreifen können.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist über das Internet zugänglich und die Sicherheit wird durch Benutzerauthentifizierung und -autorisierung gewährleistet. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff zu kontrollieren und nur auf vertrauenswürdige IP-Adressen zu beschränken. Cloud Manager-Benutzende mit entsprechenden Berechtigungen können Zulassungslisten mit vertrauenswürdigen IP-Adressen erstellen, von denen aus die Benutzenden ihrer Site auf ihre AEM-Domains zugreifen können."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/cicd-pipelines/ip-allow-lists/add-ip-allow-lists" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/cicd-pipelines/ip-allow-lists/managing-ip-allow-lists" text="Anzeigen und Aktualisieren einer IP-Zulassungsliste"

## Überblick {#overview}

AEM as a Cloud Service ist standardmäßig über das Internet zugänglich. Während die Sicherheit über die Benutzerauthentifizierung und -autorisierung gehandhabt wird, ist die IP-Zulassungsauflistung eine Möglichkeit, den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken.

Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff zu kontrollieren und nur auf solche vertrauenswürdigen IP-Adressen zu beschränken. Cloud Manager-Benutzende mit entsprechenden Berechtigungen können [Listen mit vertrauenswürdigen IP-Adressen erstellen und hinzufügen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md), von denen aus die Benutzenden ihrer Site auf ihre AEM-Domains zugreifen können.

Nach dem Hinzufügen können [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) als Einheit oder als Entität auf einen Autoren- und/oder Veröffentlichungs-Service in einer Umgebung mehrmals angewendet bzw. ihre Anwendung aufgehoben werden.

>[!NOTE]
>
>Wenn keine IP-Zulassungsliste angewendet wird, sind standardmäßig alle IP-Adressen zulässig. Wenn eine IP-Zulassungsliste angewendet wird, sind keine IP-Adressen außer den Adressen auf der IP-Zulassungsliste zulässig.

## Nutzungshinweise {#usage-notes}

* Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Jeder IP-Zulassungsliste können maximal 50 IP/CIDR-Adressen hinzugefügt werden.
* IP-Zulassungslistennamen werden in Cloud Manager für Autoren- und/oder Veröffentlichungs-Services in einer Umgebung unterstützt.

### Frontend-Pipelines und IP-Zulassungslisten {#front-end-pipeline}

Wenn Sie die [Frontend-Pipeline zur Entwicklung von Sites](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) verwenden bzw. verwenden möchten, muss zuvor die folgende Cloud Manager-IP-Zulassungsliste hinzugefügt werden.

Wenn Sie die [IP-Zulassungsliste hinzufügen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md#add-cm-allowlist), geben Sie ihr den Namen *`Cloud Manager`*. Kopieren Sie dann die Adressliste unten und fügen Sie sie in das Dialogfeld „IP-Zulassungsliste“ ein.

```text
52.254.106.192/28
20.186.185.181
52.254.106.240/28
52.254.107.128/28
52.254.105.192/28
52.254.106.176/28
20.186.185.227
52.254.106.144/28
52.254.107.64/28
20.186.185.239
20.22.83.112
52.254.107.80/28
52.254.107.144/28
52.254.106.224/28
20.14.241.153
52.254.107.0/28
52.254.107.32/28
52.254.106.208/28
40.70.154.136/29
52.254.106.160/28
52.254.107.16/28
52.254.106.0/28
4.152.211.251
```

Stellen Sie sicher, dass diese Cloud Manager-IP-Zulassungsliste hinzugefügt wird, um Störungen bei der Ausführung der Frontend-Pipeline zu vermeiden. Wenden Sie dann die Liste auf die Autorenumgebung an, *bevor* Sie die Pipeline aktivieren.

Weitere Informationen finden Sie unter [Anwenden von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) und [Aktivieren der Frontend-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

### Der universelle Editor und IP-Zulassungslisten {#universal-editor}

Wenn Sie den universellen Editor zum Erstellen Ihrer Inhalte verwenden möchten, müssen Sie die IP-Adressen, die der Dienst „Universeller Editor“ verwendet, zu einer Zulassungsliste hinzufügen und anwenden.

1. Rufen Sie die vom Dienst „Universeller Editor“ verwendeten IP-Adressen vom folgenden API-Endpunkt ab: `http://universal-editor-service.adobe.io/ip-ranges`.
1. Erstellen Sie eine Zulassungsliste mit diesen IP-Adressen und nennen Sie sie „`Universal Editor Service`“ oder ähnlich.
1. Wenden Sie die Zulassungsliste „`Universal Editor Service`“ an.

Die Liste der vom Dienst „Universeller Editor“ verwendeten IP-Adressen kann sich ändern und Sie müssen Ihre Zulassungsliste entsprechend aktualisieren.
