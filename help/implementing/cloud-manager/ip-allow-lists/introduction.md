---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen aus Benutzer auf AEM as a Cloud Service Domänen zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 18%

---


# Einführung in IP-Zulassungslisten {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist über das Internet zugänglich und durch Benutzerauthentifizierung und -autorisierung gesichert. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können Zulassungslisten vertrauenswürdiger IP-Adressen erstellen, von denen aus die Benutzer ihrer Website auf ihre AEM-Domänen zugreifen können."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists.html" text="IP-Zulassungsliste anzeigen und aktualisieren"

AEM as a Cloud Service ist standardmäßig über das Internet zugänglich. Während die Sicherheit über Benutzerauthentifizierung und Autorisierung gehandhabt wird, ist die IP-Zulassungsauflistung eine Möglichkeit, den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken.

Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf solche vertrauenswürdigen IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können [Erstellen von Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) der vertrauenswürdigen IP-Adressen, von denen aus die Benutzer ihrer Site auf ihre AEM-Domänen zugreifen können.

Nach dem Hinzufügen [IP-Zulassungslisten können angewendet/nicht angewendet werden](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) mehrmals als Einheit oder Entität an einen Autoren- und/oder Herausgeberdienst in einer Umgebung gesendet.

>[!NOTE]
>
>Wenn keine IP-Zulassungsliste angewendet wird, sind standardmäßig alle IP-Adressen zulässig. Wenn eine IP-Zulassungsliste angewendet wird, sind außer für Adressen auf der IP-Zulassungsliste keine IP-Adressen zulässig.

## Einschränkungen {#limitations}

Es gibt mehrere Einschränkungen bei der IP-Zulassungsliste, um sie zu berücksichtigen.

* In Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Zu jeder IP-Zulassungsliste können maximal 50 IP-/CIDR-Adressen hinzugefügt werden.
* Namen von IP-Zulassungslisten werden in Cloud Manager für Autoren- oder Veröffentlichungsdienste oder beides in einer Umgebung unterstützt.
