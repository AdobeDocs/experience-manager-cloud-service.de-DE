---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen aus Benutzer auf Domänen in AEM as a Cloud Service zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f4c6331491bb08e81964476ad58065c1ee022967
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 20%

---


# Einführung in IP-Zulassungslisten {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist über das Internet zugänglich und durch Benutzerauthentifizierung und -autorisierung gesichert. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzerinnen und -Benutzer mit entsprechenden Berechtigungen können Zulassungslisten mit vertrauenswürdigen IP-Adressen erstellen, von denen aus die Benutzerinnen und Benutzer ihrer Website auf ihre AEM-Domains zugreifen können."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists" text="Anzeigen und Aktualisieren einer IP-Zulassungsliste"

AEM as a Cloud Service ist standardmäßig über das Internet zugänglich. Während die Sicherheit über Benutzerauthentifizierung und Autorisierung gehandhabt wird, ist die IP-Zulassungsauflistung eine Möglichkeit, den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken.

Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf solche vertrauenswürdigen IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) vertrauenswürdiger IP-Adressen erstellen, von denen aus die Benutzer ihrer Website auf ihre AEM zugreifen können.

Nach dem Hinzufügen können [IP-Zulassungslisten mehrmals als Einheit oder Entität auf einen Autoren- oder Herausgeberdienst oder beides in einer Umgebung angewendet oder nicht angewendet werden.](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)

>[!NOTE]
>
>Wenn keine IP-Zulassungsliste angewendet wird, sind standardmäßig alle IP-Adressen zulässig. Wenn eine IP-Zulassungsliste angewendet wird, sind außer für Adressen auf der IP-Zulassungsliste keine IP-Adressen zulässig.

## Einschränkungen {#limitations}

Beachten Sie bei IP-Zulassungslisten verschiedene Einschränkungen.

* In Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Jeder IP-Zulassungsliste können maximal 50 IP/CIDR-Adressen hinzugefügt werden.
* Die Namen von IP-Zulassungslisten werden in Cloud Manager für den Autoren- oder Veröffentlichungsdienst oder beides in einer Umgebung unterstützt.
