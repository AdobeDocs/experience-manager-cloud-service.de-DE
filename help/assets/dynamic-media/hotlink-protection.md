---
title: Aktivieren des Hotlink-Schutzes in Dynamic Media
description: Erfahren sie, wie Sie den Hotlink-Schutz in Dynamic Media aktivieren.
contentOwner: Rick Brough
feature: Asset Management
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 0198b3a3-173e-46ca-a845-3f58f8eab769
source-git-commit: a641933d1049cd07ee8935672c8ef357a5bbf18c
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 97%

---

# Aktivieren des Hotlink-Schutzes in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

Von Hotlinking spricht man, wenn eine Drittanbieter-Website HTML-Code verwendet, um ein Bild von Ihrer Website anzuzeigen. Sie beanspruchen bei jedem Aufruf des Bildes Ihre Bandbreite, da der Browser des Besuchers direkt über Ihren Server darauf zugreift. Der Hotlink-*Schutz* ist eine Methode, um das direkte Verknüpfen anderer Websites mit Bildern, CSS oder JavaScript auf Ihren Web-Seiten zu verhindern. Dadurch können Sie unnötige Bandbreitennutzung in Ihrem Dynamic Media-Konto reduzieren.

[Der Adobe-Support](https://experienceleague.adobe.com/de?support-solution=Experience+Manager&lang=de#home) kann einen Referrer-Filter auf CDN-Ebene konfigurieren. Dadurch wird sichergestellt, dass Dynamic Media-Inhalte nur Websites zur Verfügung gestellt werden, die auf Ihrer Liste der zulässigen Websites für die Domain stehen.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt. Um den Hotlink-Schutz zu aktivieren, muss ein Administrator ein Support-Ticket erstellen, um die Konfigurationsänderung an Ihrem Dynamic Media-Konto anzufordern. Mit der Aktivierung des Hotlink-Schutzes sind keine zusätzlichen Kosten verbunden.
