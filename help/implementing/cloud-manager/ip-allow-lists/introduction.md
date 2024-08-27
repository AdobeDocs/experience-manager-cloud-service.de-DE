---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen aus Benutzer auf Domänen in AEM as a Cloud Service zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 96179c5f88e8546c12674e34afd0269c1f196d65
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 15%

---


# Einführung in IP-Zulassungslisten {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist über das Internet zugänglich und durch Benutzerauthentifizierung und -autorisierung gesichert. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzerinnen und -Benutzer mit entsprechenden Berechtigungen können Zulassungslisten mit vertrauenswürdigen IP-Adressen erstellen, von denen aus die Benutzerinnen und Benutzer ihrer Website auf ihre AEM-Domains zugreifen können."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists" text="Anzeigen und Aktualisieren einer IP-Zulassungsliste"

AEM as a Cloud Service ist standardmäßig über das Internet zugänglich. Während die Sicherheit über Benutzerauthentifizierung und Autorisierung gehandhabt wird, ist die IP-Zulassungsauflistung eine Möglichkeit, den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken.

Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf solche vertrauenswürdigen IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) vertrauenswürdiger IP-Adressen erstellen und hinzufügen, über die die Benutzer ihrer Website auf ihre AEM-Domänen zugreifen können.

Nach dem Hinzufügen können [IP-Zulassungslisten mehrmals als Einheit oder Entität auf einen Autoren- oder Herausgeberdienst oder beides in einer Umgebung angewendet oder nicht angewendet werden.](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)

>[!NOTE]
>
>Wenn keine IP-Zulassungsliste angewendet wird, sind standardmäßig alle IP-Adressen zulässig. Wenn eine IP-Zulassungsliste angewendet wird, sind außer für Adressen auf der IP-Zulassungsliste keine IP-Adressen zulässig.

## Verwendung der Cloud Manager IP-Zulassungsliste mit der Frontend-Pipeline {#allowlists-frontend-pipeline}

Wenn Sie die Front-End-Pipeline [ zur Entwicklung von Sites verwenden bzw. verwenden möchten, muss zuvor die folgende Cloud Manager IP-Zulassungsliste hinzugefügt werden.](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)

Wenn Sie [die IP-Zulassungsliste hinzufügen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md#add-cm-allowlist), geben Sie ihr den Namen *`Cloud Manager`*. Kopieren Sie dann die Adressenliste unten und fügen Sie sie in das Dialogfeld &quot;IP-Zulassungsliste&quot;ein.

**IP-Zulassungsliste von Cloud Manager**

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

Stellen Sie sicher, dass diese IP-Zulassungsliste von Cloud Manager hinzugefügt wird, um eine Unterbrechung der Ausführung der Front-End-Pipeline zu vermeiden. Wenden Sie dann die Liste auf die Autorenumgebung *vor* an, um die Pipeline zu aktivieren.

Siehe [Anwenden der IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md).
Siehe [Aktivieren der Frontend-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).


## Einschränkungen {#limitations}

Beachten Sie bei IP-Zulassungslisten verschiedene Einschränkungen.

* In Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Jeder IP-Zulassungsliste können maximal 50 IP/CIDR-Adressen hinzugefügt werden.
* Die Namen von IP-Zulassungslisten werden in Cloud Manager für den Autoren- oder Veröffentlichungsdienst oder beides in einer Umgebung unterstützt.
