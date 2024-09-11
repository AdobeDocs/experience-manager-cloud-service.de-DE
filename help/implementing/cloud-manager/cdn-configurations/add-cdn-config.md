---
title: Hinzufügen einer CDN-Konfiguration
description: Erfahren Sie, wie Sie eine CDN-Konfiguration für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung hinzufügen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: dd696580758e7ab9a5427d47fda4275f9ad7997f
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 18%

---

# Hinzufügen einer CDN-Konfiguration {#add-cdn}

Das Hinzufügen einer CDN-Konfiguration muss abgeschlossen sein, um eine Domäne mit SSL zu konfigurieren.

>
>
>Bei von Adobe verwalteten CDNs sind bei Verwendung von DV-Zertifikaten nur Sites mit ACME-Validierung zulässig.

**Hinzufügen einer CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf **CDN-Konfigurationen**.

1. Klicken Sie in der rechten oberen Ecke der Seite &quot;CDN-Konfigurationen&quot;auf **Hinzufügen**.

   ![CDN-Dialogfeld konfigurieren](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

1. Geben Sie im Dialogfeld **CDN konfigurieren** die erforderlichen Informationen ein.

   * Führen Sie in der Dropdownliste **Origin** einen der folgenden Schritte aus:
      * **Sites:** Wählen Sie eine Edge Delivery Services-Site aus.
      * **Umgebungen:** Wählen Sie eine Cloud Service-Umgebung aus.
         * **Ebene:** Wählen Sie eine **Publish** - oder eine **Vorschau** -Webstufe für die ausgewählte Umgebung aus.
   * Wählen Sie Ihren CDN-Typ aus: **Adobe verwaltetes CDN** oder **Andere CDN-Anbieter**.
   * Wählen Sie die Domain aus.
   * Wählen Sie das SSL-Zertifikat aus. Nur erforderlich, wenn Sie **Adobe verwaltetes CDN** als CDN-Typ ausgewählt haben.

1. Klicken Sie auf **Speichern**.
