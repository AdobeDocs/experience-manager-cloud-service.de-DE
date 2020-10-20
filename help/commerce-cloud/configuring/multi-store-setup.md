---
title: Multi-Store-Einrichtung
description: Multi-Store-Einrichtung
translation-type: tm+mt
source-git-commit: 69756d6831678151b0e8eb73db81113d49f17447
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 4%

---


# Multi-Store-Einrichtung {#multi-store}

Die AEM CIF Core-Komponenten können auf mehreren AEM Sitestrukturen verwendet werden und die zugrunde liegende GraphQL Client-Implementierung kann mit verschiedenen Magento Stores/Store-Ansichten verbunden werden. Dadurch können Projekte komplexe Multi-Store-/Multi-Site-Setups implementieren.

Eine Videoanleitung mit detaillierten Optionen zur Integration mehrerer Magento Store-Ansichten mit Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM Funktionen zur Verwaltung mehrerer Sites von Live Copy und Sprachkopie werden zusammen mit dem Commerce Integration Framework verwendet, um global Sites über Regionen und Gebietsschemata hinweg zu verwalten.

Es wird empfohlen, eine 1:1-Beziehung zwischen AEM Site- und Magento Store-Ansicht zu verwenden.

Gehen Sie wie folgt vor, um eine AEM-Site zu verbinden und CIF-Kernkomponenten so zu einer dedizierten Store-Ansicht AEM:

## Konfiguration {#configuration}

1. Konfigurieren Sie mehrere Stores und Store-Ansichten nach dem Muster, das in [Magento Websites, Stores und Ansichten beschrieben ist.](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)

2. Stellen Sie sicher, dass die Verbindung zwischen AEM und Magento funktioniert.

3. Erstellen Sie eine untergeordnete Konfiguration der CIF-Cloud Service-Konfiguration wie folgt:

   * Gehen Sie AEM zu Tools -> Allgemein -> [Konfigurationsbrowser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)
   * Wählen Sie die erstellte Basiskonfiguration aus
   * Erstellen Sie eine neue Konfiguration mithilfe der unter Nummer 2 beschriebenen Schritte.

   Diese neue Konfiguration wird als untergeordnete Konfiguration der Basiskonfiguration erstellt. Sie können jetzt unter Tools -> Allgemein -> Konfigurationsbrowser die Konfigurationseinstellungen erstellen.

4. Zuweisen der untergeordneten Konfiguration zu einer AEM Site

   * Zu AEM Sites Console wechseln
   * Navigieren Sie zur Region oder zum Sprachstamm Ihrer Site-Struktur, z. B. /content/venia/us _oder_ /content/venia/us/de für die Venia-Beispielseite
   * Wählen Sie die Seiten aus und öffnen Sie die Seiteneigenschaften
   * Wählen Sie die Registerkarte Erweitert
   * Wählen Sie im `Configuration` Abschnitt die im Schritt erstellte Konfiguration aus.

## Zusätzliche Ressourcen

* [Websites, Stores und Ansichten von Magentos](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [AEM CIF-Kernkomponenten - Konfiguration mehrerer Speicher/Standorte](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Verwenden von Multi-Site-Manager](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/msm.html)
