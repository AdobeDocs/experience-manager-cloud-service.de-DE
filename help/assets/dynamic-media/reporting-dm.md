---
title: Reporting in Dynamic Media
description: Erfahren Sie, wie Sie einen Fehlerbericht für Dynamic Media-Bereitstellungs-URLs anfordern, die fehlschlagen.
contentOwner: Rick Brough
feature: Asset Management
role: User
hide: true
hidefromtoc: true
exl-id: 2488f813-df15-4dbb-8747-f827ee5925e1
source-git-commit: aa7429d9ca9f67979303c0b85c9dbd5b8c74c05c
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 4%

---

# Anfordern eines Fehlerberichts für fehlgeschlagene Dynamic Media-Bereitstellungs-URLs

Sie können einen Fehlerbericht anfordern, der Dynamic Media-URLs angibt, die zum Zeitpunkt der Bereitstellung fehlgeschlagen sind. Der Bericht ist eine Aggregation von Daten bis zu fünf Tagen und im CSV-Format verfügbar. Der Fehlerbericht enthält die folgenden Informationen:

* Fehlgeschlagene Dynamic Media-Bereitstellungs-URL - Eine fehlerhafte URL ist eine von Dynamic Media generierte URL, die zum Zeitpunkt der Bereitstellung keinen Inhalt erstellen kann.
* Referrer-URL - Die Referrer-URL, von der aus die fehlgeschlagene Bereitstellungs-URL aufgerufen wird.
* Anzahl der Fehler - Die Anzahl der Ladevorgänge der Versand-URL, die zu einem Fehler führten.

Wenn Sie den Fehlerbericht anfordern, sendet das Adobe Dynamic Media-Team den Bericht per E-Mail im CSV-Format an Sie. Sie umfasst einen Zeitraum von fünf Tagen ab dem Tag, an dem Ihre Anfrage gestellt wurde.

Sie können einen Fehlerbericht einmal monatlich für ein bestimmtes Unternehmen anfordern.

**So fordern Sie einen Fehlerbericht für fehlgeschlagene Dynamic Media-Bereitstellungs-URLs an:**

1. [E-Mail an reports-dynamic-media@adobe.com senden](mailto:reports-dynamic-media@adobe.com) mit dem Unternehmensnamen, der mit Ihrem Dynamic Media-Konto verknüpft ist.

   Wenn Sie den Unternehmensnamen nicht kennen, lesen Sie den Abschnitt [Dynamic Media-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html?lang=de#configuring-dynamic-media-cloud-services) Seite in **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Dynamic Media-Konfiguration]**. Klicken Sie auf der Seite Dynamic Media Configuration Browser auf **[!UICONTROL global]**, wählen Sie die *[Dynamic_Media_folder_icon]* Kontrollkästchen aktivieren und dann **[!UICONTROL Bearbeiten]**. Sie müssen über Administratorrechte in AEM verfügen, um auf die Seite &quot;Dynamic Media-Konfiguration&quot;zugreifen zu können.

   ![Zugriff auf die Seite Dynamic Media-Konfiguration .](/help/assets/dynamic-media/assets/reporting-accessdmconfig.png)
