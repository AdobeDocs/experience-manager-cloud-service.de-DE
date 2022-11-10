---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen Benutzerinnen und Benutzer auf Ihre AEM as a Cloud Service-Domains zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 18ecf3394ff575213756fced84a3b08795188240
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 56%

---


# Einführung in IP-Zulassungslisten {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist für das Internet offen und die Sicherheit wird durch Benutzerauthentifizierung und -autorisierung gewährleistet. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen einzuschränken und zu kontrollieren. Cloud Manager-Benutzerinnen und -Benutzer mit entsprechenden Berechtigungen können Listen mit vertrauenswürdigen IP-Adressen erstellen, von denen aus die Benutzerinnen und Benutzer ihrer Website auf ihre AEM-Domains zugreifen können."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=de" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=de" text="IP-Zulassungsliste anzeigen und aktualisieren"

AEM as a Cloud Service ist standardmäßig über das Internet zugänglich. Während die Sicherheit durch Benutzerauthentifizierung und Autorisierung erfolgt, ist die IP-Zulassungsauflistung eine Möglichkeit, den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken.

Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf solche vertrauenswürdigen IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können [Zulassungslisten erstellen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) der vertrauenswürdigen IP-Adressen, von denen aus die Benutzer ihrer Site auf ihre AEM-Domänen zugreifen können.

Nach dem Hinzufügen [IP-Zulassungslisten können angewendet/nicht angewendet werden](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) mehrmals als Einheit oder Entität an einen Autoren- und/oder Herausgeberdienst in einer Umgebung gesendet.

>[!NOTE]
>
>Wenn keine IP-Zulassungsliste angewendet wird, sind standardmäßig alle IP-Adressen zulässig. Sobald eine IP-Zulassungsliste angewendet wird, sind außer den IP-Adressen keine IP-Adressen zulässig.

## Beschränkungen {#limitations}

Es gibt eine Reihe von Einschränkungen, die bei IP-Zulassungslisten zu beachten sind.

* In Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Jeder IP-Zulassungsliste können maximal 50 IP/CIDR-Adressen hinzugefügt werden.
* Die Namen von IP-Zulassungslisten werden in Cloud Manager für den Autoren- und/oder Veröffentlichungs-Service in einer Umgebung unterstützt.
