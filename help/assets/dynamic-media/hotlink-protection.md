---
title: 'Aktivieren des Hotlink-Schutzes in Dynamic Media  '
description: Erfahren Sie, wie Sie den Hotlink-Schutz in Dynamic Media aktivieren.
feature: Asset-Verwaltung
role: Business Practitioner
exl-id: 0198b3a3-173e-46ca-a845-3f58f8eab769
source-git-commit: 1ad89be4ebddec0705c6f557fed3d697b9f1f3a7
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 26%

---

# Aktivieren des Hotlink-Schutzes in Dynamic Media   {#activating-hotlink-protection-in-dynamic-media}

Bei der Hotlink-Verknüpfung verwendet eine Drittanbieter-Website HTML-Code, um ein Bild von Ihrer Website anzuzeigen. Sie beanspruchen bei jedem Aufruf des Bildes Ihre Bandbreite, da der Browser des Besuchers direkt über Ihren Server darauf zugreift. Hotlink *protection* ist eine Methode, um zu verhindern, dass andere Websites direkt auf Bilder, CSS oder JavaScript™ auf Ihren Webseiten verlinken. Dadurch können Sie unnötige Bandbreitennutzung in Ihrem Dynamic Media-Konto reduzieren.

[Adobe-Kundenunterstützung ](https://helpx.adobe.com/de/support.html) kann einen Referrer-Filter auf CDN-Ebene konfigurieren. Dadurch wird sichergestellt, dass Dynamic Media-Inhalte nur für Websites bereitgestellt werden, die auf Ihrer Liste der zulässigen Websites für die Domäne stehen.

>[!NOTE]
>
>Für diese Funktion müssen Sie das vordefinierte CDN verwenden, das im Lieferumfang von Adobe Experience Manager Dynamic Media enthalten ist. Mit dieser Funktion werden keine anderen benutzerdefinierten CDNs unterstützt. Um den Schutz von Hotlinks zu aktivieren, muss ein Administrator ein Support-Ticket erstellen, um die Konfigurationsänderung für Ihr Dynamic Media-Konto anzufordern. Für die Aktivierung des Schutzes von Hotlinks fallen keine zusätzlichen Kosten an.
