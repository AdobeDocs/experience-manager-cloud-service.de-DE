---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen aus Benutzerinnen und Benutzer auf Domains in AEM as a Cloud Service zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 100%

---


# Einführung in IP-Zulassungslisten {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von Listen zugelassener IP-Adressen"
>abstract="AEM as a Cloud Service ist über das Internet zugänglich und die Sicherheit wird durch Benutzerauthentifizierung und -autorisierung gewährleistet. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen einzuschränken und zu kontrollieren. Cloud Manager-Benutzerinnen und -Benutzer mit entsprechenden Berechtigungen können Zulassungslisten mit vertrauenswürdigen IP-Adressen erstellen, von denen aus die Benutzerinnen und Benutzer ihrer Website auf ihre AEM-Domains zugreifen können."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=de" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists.html?lang=de" text="IP-Zulassungsliste anzeigen und aktualisieren"

AEM as a Cloud Service ist standardmäßig über das Internet zugänglich. Während die Sicherheit über Benutzerauthentifizierung und Autorisierung gehandhabt wird, ist die IP-Zulassungsauflistung eine Möglichkeit, den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken.

Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff zu kontrollieren und nur auf solche vertrauenswürdigen IP-Adressen zu beschränken. Cloud Manager-Benutzerinnen und -Benutzer mit entsprechenden Berechtigungen können [Zulassungslisten mit vertrauenswürdigen IP-Adressen erstellen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md), von denen aus die Benutzerinnen und Benutzer ihrer Website auf ihre AEM-Domains zugreifen können.

Nach dem Hinzufügen können [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) als Einheit oder als Entität auf einen Authoring- und/oder Publishing-Service in einer Umgebung mehrmals angewendet bzw. nicht angewendet werden.

>[!NOTE]
>
>Wenn keine IP-Zulassungsliste angewendet wird, sind standardmäßig alle IP-Adressen zulässig. Wenn eine IP-Zulassungsliste angewendet wird, sind keine IP-Adressen außer den Adressen auf der IP-Zulassungsliste zulässig.

## Einschränkungen {#limitations}

Bei IP-Zulassungslisten gibt es einige Einschränkungen zu beachten.

* In Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Jeder IP-Zulassungsliste können maximal 50 IP/CIDR-Adressen hinzugefügt werden.
* IP-Zulassungslistennamen werden in Cloud Manager für Authoring- oder Publishing-Services, oder für beide, in einer Umgebung unterstützt.
