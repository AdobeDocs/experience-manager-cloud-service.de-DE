---
title: Einführung – IP-Zulassungslisten in Cloud Manager
description: Einführung – IP-Zulassungslisten in Cloud Manager
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 1875920ae5180074dcad98fb5c10242b6baa76c7
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 100%

---

# Einführung {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Verwalten von IP-Zulassungslisten"
>abstract="AEM as a Cloud Service ist für das Internet offen und die Sicherheit wird durch Benutzerauthentifizierung und -autorisierung gewährleistet. Die IP-Zulassungsliste ist eine Funktion in Cloud Manager, mit der der Zugriff auf vertrauenswürdige Benutzer beschränkt und gesteuert werden kann. Mit dieser Funktion können berechtigte Benutzer Zulassungslisten vertrauenswürdiger IP-Adressen erstellen, über die Website-Benutzer auf ihre AEM-Domains zugreifen können."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=de" text="Hinzufügen einer IP-Zulassungsliste"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=de" text="IP-Zulassungsliste anzeigen und aktualisieren"

AEM as a Cloud Service ist für das Internet offen und die Sicherheit wird durch Benutzerauthentifizierung und -autorisierung gewährleistet. Die IP-Zulassungsliste ist eine Funktion in Cloud Manager, mit der der Zugriff auf vertrauenswürdige Benutzer beschränkt und gesteuert werden kann. Mit dieser Funktion können berechtigte Benutzer Zulassungslisten vertrauenswürdiger IP-Adressen erstellen, über die Website-Benutzer auf ihre AEM-Domains zugreifen können.

>[!NOTE]
>Sie können maximal 50 IP-Zulassungslisten in Ihrem Programm hinzufügen und maximal 50 IP/CIDR-Adressen zu jeder IP-Zulassungsliste hinzufügen.

IP-Zulassungslisten können einmal hinzugefügt und mehrmals als Einheit oder Entität auf einen Autoren- und/oder Veröffentlichungs-Service in einer Umgebung angewendet/nicht angewendet werden.

>[!NOTE]
>IP-Zulassungslistennamen werden in Cloud Manager für den Autoren- und/oder Veröffentlichungs-Service in einer Umgebung unterstützt.

Auf der Seite mit der IP-Zulassungsliste der Cloud Manager-Benutzeroberfläche oder der Seite mit den Umgebungsdetails kann ein berechtigter Benutzer verschiedene Aufgaben zum Verwalten von IP-Zulassungslisten für Ihre Umgebungen ausführen, darunter:

* [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md)
   >[!NOTE]
   > Sie können die Regel einmal hinzufügen und die Regel beliebig oft für Umgebungs-Services im Programm wiederverwenden oder anwenden.
* [Anzeigen oder Aktualisieren einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/view-update-ip-allow-list.md)
* [Anwenden oder Aufheben der Anwendung einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)
* [Löschen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/delete-ip-allow-list.md)
