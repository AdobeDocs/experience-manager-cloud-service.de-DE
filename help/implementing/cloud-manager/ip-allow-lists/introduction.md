---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen Benutzerinnen und Benutzer auf Ihre AEM as a Cloud Service-Domains zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 18ecf3394ff575213756fced84a3b08795188240
workflow-type: ht
source-wordcount: '319'
ht-degree: 100%

---


# Einführung in IP-Zulassungslisten {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist für das Internet offen und die Sicherheit wird durch Benutzerauthentifizierung und -autorisierung gewährleistet. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen einzuschränken und zu kontrollieren. Cloud Manager-Benutzerinnen und -Benutzer mit entsprechenden Berechtigungen können Listen mit vertrauenswürdigen IP-Adressen erstellen, von denen aus die Benutzerinnen und Benutzer ihrer Website auf ihre AEM-Domains zugreifen können."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=de" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=de" text="IP-Zulassungsliste anzeigen und aktualisieren"

AEM as a Cloud Service ist standardmäßig über das Internet zugänglich. Während die Sicherheit über Benutzerauthentifizierung und Autorisierung gehandhabt wird, ist die IP-Zulassungsauflistung eine Möglichkeit, den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken.

Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff zu kontrollieren und nur auf solche vertrauenswürdigen IP-Adressen zu beschränken. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können [Listen mit vertrauenswürdigen IP-Adressen erstellen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md), von denen aus die Benutzer ihrer Website auf ihre AEM-Domains zugreifen können.

Wenn sie einmal hinzugefügt wurden, können [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) als Einheit oder als Entität auf einen Autoren- und/oder Publisher-Service in einer Umgebung mehrmals angewendet bzw. nicht angewendet werden.

>[!NOTE]
>
>Wenn keine IP-Zulassungsliste angewendet wird, sind standardmäßig alle IP-Adressen zulässig. Sobald eine IP-Zulassungsliste angewendet wird, sind außer den IP-Adressen der Zulassungsliste keine IP-Adressen zulässig.

## Beschränkungen {#limitations}

Es gibt eine Reihe von Einschränkungen, die bei IP-Zulassungslisten zu beachten sind.

* In Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Jeder IP-Zulassungsliste können maximal 50 IP/CIDR-Adressen hinzugefügt werden.
* Die Namen von IP-Zulassungslisten werden in Cloud Manager für den Autoren- und/oder Veröffentlichungs-Service in einer Umgebung unterstützt.
