---
title: Multi-Store-Einrichtung in Commerce
description: Erfahren Sie, wie Sie mehrere Store-Ansichten von Adobe Commerce zu Adobe Experience Manager zuordnen. Dadurch können Projekte auch mehrinstanzenfähige und mehrsprachige Anwendungsfälle unterstützen.
sub-product: Commerce
version: Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
exl-id: 4385c9e5-2b25-4f95-952f-72349431cf94
source-git-commit: 97a6a7865f696f4d61a1fb4e25619caac7b68b51
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 47%

---

# Commerce    Multi-Store-Setup {#multi-store}

Die Adobe Experience Manager (AEM) CIF Kernkomponenten können auf mehreren AEM Site-Strukturen verwendet werden und die zugrunde liegende GraphQL-Client-Implementierung kann eine Verbindung zu verschiedenen Adobe Commerce Stores/Store-Ansichten herstellen. Dadurch können Projekte komplexe Multi-Store-/Multi-Site-Setups implementieren.

Videoeinführung mit detaillierten Optionen zur Integration mehrerer Adobe Commerce-Store-Ansichten mit Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM Funktionen für die Verwaltung mehrerer Sites von Live Copy und Sprachkopie werden mit dem Commerce Integration Framework verwendet, um global Sites über Regionen und Gebietsschemata hinweg zu verwalten.

Es wird empfohlen, eine 1:1-Beziehung zwischen der AEM Site und der Adobe Commerce Store-Ansicht zu verwenden.

Gehen Sie wie folgt vor, um eine AEM Site zu verbinden und AEM Kernkomponenten mit einer dedizierten Store-Ansicht zu verbinden:

## Konfiguration {#configuration}

1. Konfigurieren Sie mehrere Stores und Store-Ansichten nach dem Muster, das unter [Websites, Stores und Ansichten in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) beschrieben ist.

2. Stellen Sie sicher, dass die Verbindung zwischen AEM und Adobe Commerce funktioniert.

3. Erstellen Sie eine untergeordnete Konfiguration der CIF-Cloud Service-Konfiguration wie folgt:

   * Wechseln Sie in AEM zu „Tools“ > „Allgemein“ > [Konfigurations-Browser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).
   * Wählen Sie die von Ihnen erstellte Basiskonfiguration aus
   * Erstellen Sie eine Konfiguration anhand der unter Nummer 2 beschriebenen Schritte.

   Diese neue Konfiguration wird als untergeordnete Konfiguration der Basiskonfiguration erstellt. Sie können nun die Konfigurationseinstellungen unter „Tools“ -> „Allgemein“ -> „Konfigurationsbrowser“ erstellen.

   >[!TIP]
   >
   > Commerce-Kataloge können mit IDs oder UIDs adressiert werden. Die Unterstützung für UIDs wurde in Adobe Commerce 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.

4. Weisen Sie die untergeordnete Konfiguration zu einer AEM-Site zu.

   * Navigieren Sie zur AEM Sites-Konsole
   * Navigieren Sie zum Regions- oder Sprachstamm Ihrer Site-Struktur. Beispiel: `/content/venia/us _or_ /content/venia/us/en` für die Venia-Beispielseite
   * Wählen Sie die Seite aus und öffnen Sie die Seiteneigenschaften
   * Wählen Sie die Registerkarte „Erweitert“ aus.
   * Im `Configuration` wählen Sie die Konfiguration aus, die Sie in Schritt 3 erstellt haben.

## Zusätzliche Ressourcen

* [Websites, Stores und Ansichten in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)
* [AEM-CIF-Kernkomponenten – Multi-Store-/Multi-Site-Konfiguration](https://github.com/adobe/aem-core-cif-components#multi-store--site-configuration)
* [Verwenden von Multi Site Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html?lang=de)
* [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](/help/sites-cloud/administering/msm/overview.md)
