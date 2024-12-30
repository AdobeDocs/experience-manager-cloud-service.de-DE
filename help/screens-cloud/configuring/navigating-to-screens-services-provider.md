---
title: Navigieren zu Screens Services Provider
description: Auf dieser Seite wird beschrieben, wie Sie zu Screens Services Provider navigieren.
exl-id: 9eff6fe8-41d4-4cf3-b412-847850c4e09c
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 100%

---

# Navigieren zu Screens Services Provider {#setup-screens-services-provider}

## Einführung {#introduction}

Mit **Screens Services Provider** können Inhaltsautor, Entwickler und Administratoren Displays und Player für die Inhaltswiedergabe verwalten, sobald die Inhalte zu den Kanälen hinzugefügt wurden. Sobald Benutzer Zugriff auf AEM as a Cloud Service erhalten, sollten sie sich bei Screens Services Provider anmelden können.

In diesem Abschnitt wird beschrieben, wie Sie Screens Services Provider einrichten.


## Ziel {#objective}

Im folgenden Abschnitt erfahren Sie, wie Sie Screens Services Provider konfigurieren und einrichten.

## Schritte zum Einrichten von Screens Services Provider {#screens-services-provider}

Gehen Sie wie folgt vor, um Screens Services Provider einzurichten:

1. Navigieren Sie zu [Screens Services Provider](https://experience.adobe.com/screens).

   >[!CAUTION]
   >Wenn Sie Zugriff auf mehrere Organisationen haben, stellen Sie sicher, dass Sie sich bei der richtigen Organisation angemeldet haben. Um Ihre Organisation zu ändern, klicken Sie oben rechts im Bildschirm auf den Organisationsnamen und wählen Sie die gewünschte Organisation aus, auf die Sie Zugriff benötigen.

1. Klicken Sie auf das Zahnradsymbol rechts neben „Projekt“ (obere linke Ecke).

   ![image](/help/screens-cloud/assets/configure/configure-screens0.png)

1. Geben Sie die folgenden Details im Dialogfeld „Einstellungen bearbeiten“ ein.
   * **Veröffentlichungs-URL**: AEM-Veröffentlichungs-URL (z. B. `https://publish-p12345-e12345.adobeaemcloud.com`)
   * **Autoren-URL**: AEM-Autoren-URL (z. B. `https://author-p12345-e12345.adobeaemcloud.com`)

   >[!NOTE]
   >Stellen Sie sicher, dass Sie mindestens einen AEM Screens-Kanal erstellen und veröffentlichen, bevor Sie AEM unter Screens Service Provider konfigurieren. Um einen Kanal zu erstellen, navigieren Sie zu /screens.html in Ihrem Content Provider.

   ![Bild](/help/screens-cloud/assets/configure/configure-screens4.png)

1. Klicken Sie auf **Speichern**, um eine Verbindung zum Screens-Inhaltsanbieter herzustellen.

1. Wenn Sie die AEM-Veröffentlichungsinstanz so konfiguriert haben, dass durch die IP-Zulassungslisten-Funktion von Cloud Manager nur der Zugriff auf vertrauenswürdige IP-Adressen zugelassen wird, müssen Sie im Dialogfeld „Einstellungen“ eine Kopfzeile mit einem Schlüsselwert konfigurieren, wie unten dargestellt.
Die IP-Adressen, die auf die Zulassungsliste gesetzt werden müssen, müssen ebenfalls in die Konfigurationsdatei verschoben werden, und ihre Anwendung muss in den Cloud Manager-Einstellungen [aufgehoben](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/apply-allow-list) werden.

   ![Bild](/help/screens-cloud/assets/configure/configure-screens20b.png)
Derselbe Schlüssel muss in der AEM CDN-Konfiguration konfiguriert werden. Es wird empfohlen, den Kopfzeilenwert nicht direkt in GITHub zu platzieren, sondern einen [geheimen Verweis](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-credentials-authentication#rotating-secrets) zu verwenden.
Nachfolgend finden Sie ein Beispiel für [CDN config](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/traffic-filter-rules-including-waf):

   ```kind: "CDN"
       version: "1"
       metadata:
         envTypes: ["dev", "stage", "prod"]
       data:
         trafficFilters:
           rules:
             - name: "block-request-from-not-allowed-ips"
               when:
                 allOf:
                   - reqProperty: clientIp
                     notIn: ["101.41.112.0/24"]
                    reqProperty: tier
                     equals: publish
               action: block
             - name: "allow-requests-with-header"
               when:
                 allOf:
                   - reqProperty: tier
                     equals: publish
                   - reqProperty: path
                     equals: /screens/channels.json
                   - reqHeader: x-screens-allowlist-key
                     equals: $\
       {CDN_HEADER_KEY}
               action:
                 type: allow
   ```

1. Wählen Sie in der linken Navigationsleiste **Kanäle** aus und klicken Sie auf **In Content Provider öffnen**.

   ![Bild](/help/screens-cloud/assets/configure/configure-screens1.png)

1. Screens Content Provider wird in einer anderen Registerkarte geöffnet, auf der Sie Inhalte erstellen können.

   ![image](/help/screens-cloud/assets/configure/configure-screens2.png)





## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie den Screens Services Provider einrichten, navigieren Sie zu [Verwenden von Screens Content Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=de#screens-content-provider) für weitere Details.
