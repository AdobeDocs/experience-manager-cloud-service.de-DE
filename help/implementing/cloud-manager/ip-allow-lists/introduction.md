---
title: Einführung in IP-Zulassungslisten
description: Erfahren Sie, wie IP-Zulassungslisten einschränken können, von welchen Adressen aus Benutzer auf Ihre AEM as a Cloud Service Domänen zugreifen können.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 8d1680fa8dbaaefa297cf8c6698097b3c7acc48d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 11%

---


# Einführung in IP-Zulassungslisten {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist über das Internet zugänglich und durch Benutzerauthentifizierung und -autorisierung gesichert. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können Zulassungslisten vertrauenswürdiger IP-Adressen erstellen, über die die Benutzer ihrer Website auf ihre AEM-Domänen zugreifen können."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=de" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=de" text="IP-Zulassungsliste anzeigen und aktualisieren"

AEM as a Cloud Service ist über das Internet zugänglich und durch Benutzerauthentifizierung und -autorisierung gesichert. Die IP-Zulassungslisten von Cloud Manager können verwendet werden, um den Zugriff nur auf vertrauenswürdige IP-Adressen zu beschränken und zu steuern. Cloud Manager-Benutzer mit entsprechenden Berechtigungen können Zulassungslisten vertrauenswürdiger IP-Adressen erstellen, über die die Benutzer ihrer Website auf ihre AEM-Domänen zugreifen können.

IP-Zulassungslisten können einmal hinzugefügt und mehrmals als Einheit oder Entität auf einen Autoren- und/oder Publisher-Dienst in einer Umgebung angewendet/nicht angewendet werden.

## Beschränkungen {#limitations}

IP-Zulassungslisten dürfen nur eingeschränkt berücksichtigt werden.

* In Ihrem Programm können maximal 50 IP-Zulassungslisten hinzugefügt werden.
* Jeder IP-Zulassungsliste können maximal 50 IP/CIDR-Adressen hinzugefügt werden.
* Die Namen von IP-Zulassungslisten werden in Cloud Manager für Autoren- und/oder Veröffentlichungsdienste in einer Umgebung unterstützt.
