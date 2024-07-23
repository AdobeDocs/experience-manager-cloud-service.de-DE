---
title: Navigieren zu Screens Services Provider
description: Auf dieser Seite wird beschrieben, wie Sie zu Screens Services Provider navigieren.
exl-id: 9eff6fe8-41d4-4cf3-b412-847850c4e09c
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: 093cd62f282bd9842ad74124bb9bd4d5a33ef1c5
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 63%

---

# Navigieren zu Screens Services Provider {#setup-screens-services-provider}

## Einführung {#introduction}

Mit **Screens Services Provider** können Inhaltsautor, Entwickler und Administratoren Displays und Player für die Inhaltswiedergabe verwalten, sobald die Inhalte zu den Kanälen hinzugefügt wurden. Sobald Benutzer Zugriff auf AEM as a Cloud Service erhalten, sollten sie sich bei Screens Services Provider anmelden können.

In diesem Abschnitt wird beschrieben, wie Sie Screens Services Provider einrichten.


## Ziel {#objective}

Im folgenden Abschnitt erfahren Sie, wie Sie Screens Services Provider konfigurieren und einrichten.

## Schritte zum Einrichten von Screens Services Provider {#screens-services-provider}

Gehen Sie wie folgt vor, um Screens Services Provider einzurichten:

1. Gehen Sie von [hier](https://experience.adobe.com/screens) zu Screens Services Provider.

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

1. Klicken Sie auf **Speichern** , um eine Verbindung zum Screens Content Provider herzustellen.

1. Wenn Sie die AEM Veröffentlichungsinstanz so konfiguriert haben, dass nur der Zugriff auf vertrauenswürdige IP-Adressen durch die IP--Funktion von Cloud Manager zugelassen wird, müssen Sie eine Kopfzeile mit einem Schlüsselwert im Einstellungsdialogfeld konfigurieren, wie unten dargestellt.
Die IP-Adressen, die auf die Whitelist gesetzt werden müssen, müssen ebenfalls in die Konfigurationsdatei verschoben werden und aus den Cloud Manager-Einstellungen [nicht angewendet](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/apply-allow-list) werden.

   ![image](/help/screens-cloud/assets/configure/configure-screens20.png)
Derselbe Schlüssel muss in AEM CDN-Konfiguration konfiguriert werden.  Es wird empfohlen, den Kopfzeilenwert nicht direkt in GITHub zu platzieren und einen [geheimen Verweis](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-credentials-authentication#rotating-secrets) zu verwenden.
Nachfolgend finden Sie ein Beispiel für [CDN config](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/traffic-filter-rules-including-waf):
type: &quot;CDN&quot;
version: &quot;1&quot;
Metadaten:
envTypes: [&quot;dev&quot;, &quot;stage&quot;, &quot;prod&quot;]
data:
trafficFilters:
Regeln:
- name: &quot;block-request-from-not-allowed-ips&quot;
wenn:
allOf:
- reqProperty: clientIp
notIn: [&quot;101.41.112.0/24&quot;]
reqProperty: tier
gleich: publish
Aktion: block
- name: &quot;allow-requests-with-header&quot;
wenn:
allOf:
- reqProperty: tier
gleich: publish
- reqProperty: path
gleich: /screens/channels.json
- reqHeader: x-screens-Zulassungsliste-key
gleich: $\
   {CDN_HEADER_KEY}
Aktion:
Typ: allow

1. Wählen Sie in der linken Navigationsleiste **Kanäle** aus und klicken Sie auf **In Content Provider öffnen**.

   ![Bild](/help/screens-cloud/assets/configure/configure-screens1.png)

1. Screens Content Provider wird in einer anderen Registerkarte geöffnet, auf der Sie Inhalte erstellen können.

   ![image](/help/screens-cloud/assets/configure/configure-screens2.png)





## Wie es weitergeht: {#whats-next}

Nachdem Sie gelernt haben, wie Sie den Screens Services Provider einrichten, navigieren Sie zu [Verwenden von Screens Content Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=de#screens-content-provider) für weitere Details.
