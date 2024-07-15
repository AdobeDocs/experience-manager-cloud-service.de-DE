---
title: Beschränken der Bereitstellung von Assets in Experience Manager
description: Erfahren Sie, wie Sie die Asset-Bereitstellung in [!DNL Experience Manager] einschränken.
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 1%

---

# Beschränken des Zugriffs auf Assets in [!DNL Experience Manager] {#restrict-access-to-assets}

Die zentrale Asset-Verwaltung in Experience Manager ermöglicht es dem DAM-Administrator oder Brand Manager, den Zugriff auf Assets zu verwalten. Sie können den Zugriff einschränken, indem sie Rollen für genehmigte Assets auf der Autorenseite, insbesondere auf der AEM as a Cloud Service-Autoreninstanz, konfigurieren.

Benutzer, die [ nach ](search-assets-api.md) suchen oder die [Versand-URLs](deliver-assets-apis.md) verwenden, können nach erfolgreicher Übergabe des Autorisierungsprozesses Zugriff auf eingeschränkte Assets erhalten.

![Eingeschränkter Zugriff auf Assets](/help/assets/assets/restricted-access.png)

## Eingeschränkter Versand mit einem IMS-Token {#restrict-delivery-ims-token}

Im Experience Manager umfasst der eingeschränkte Versand über IMS zwei wichtige Phasen:

* Authoring
* Bereitstellung

### Authoring {#authoring}

Sie können die Bereitstellung von Assets innerhalb von [!DNL Experience Manager] je nach Rollen einschränken. Führen Sie die folgenden Schritte aus, um Rollen zu konfigurieren:

1. Wechseln Sie zu &quot;[!DNL Experience Manager]&quot;als DAM-Administrator.
1. Wählen Sie das Asset aus, für das Sie die Rolle konfigurieren müssen.
1. Navigieren Sie zu **[!UICONTROL Eigenschaften]** > **[!UICONTROL Erweitert]** und stellen Sie sicher, dass das Feld **[!UICONTROL Rollen]** auf der Registerkarte [!UICONTROL Erweiterte Metadaten] vorhanden ist.

   ![Roles metadata](/help/assets/assets/roles_metadata.jpg)
Wenn das Feld nicht verfügbar ist, führen Sie die folgenden Schritte aus, um das Feld hinzuzufügen:

   1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
   1. Wählen Sie das Metadatenschema aus und klicken Sie auf **[!UICONTROL Bearbeiten _(e)_]**.
   1. Fügen Sie im Abschnitt **[!UICONTROL Formular erstellen]** rechts zum Abschnitt &quot;Metadaten&quot;des Formulars ein Feld mit mehreren Werten ]**hinzu.**[!UICONTROL 
   1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** durch:
      1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** in _Rollen_.
      1. Aktualisieren Sie die **[!UICONTROL Zuordnung zu Eigenschaft]** auf _./jcr:content/metadata/dam:roles_.

1. Rufen Sie die IMS-Gruppen ab, die in den Roles-Metadaten des Assets hinzugefügt werden sollen. Gehen Sie wie folgt vor, um die IMS-Gruppen abzurufen:
   1. Melden Sie sich unter https://adminconsole.adobe.com/ an.
   1. Wechseln Sie zu Ihrer jeweiligen Organisation und navigieren Sie zu **[!UICONTROL Benutzergruppen]**.
   1. Wählen Sie die **[!UICONTROL Benutzergruppe]** aus, die Sie hinzufügen müssen, extrahieren Sie die **[!UICONTROL orgID]** und die **[!UICONTROL userGroupID]** aus der URL oder verwenden Sie Ihre Organisations-ID, z. B. `{orgID}@AdobeOrg:{usergroupID}`.

1. Fügen Sie die Gruppen-ID zum Feld **[!UICONTROL Rollen]** der Asset-Eigenschaften hinzu. <br>
Die im Feld **[!UICONTROL Rollen]** definierten Gruppen-IDs sind die einzigen Benutzer, die auf das Asset zugreifen können. Sie können auch die IMS-Client-ID und die IMS-Profil-ID im Feld **[!UICONTROL Rollen]** hinzufügen. Zum Beispiel: `{orgId}@AdobeOrg:{profileId}`.

   >[!NOTE]
   >
   >Für die neue Assets-Ansicht können Sie nur Zugriff auf die Ordnerebene und ausschließlich Gruppen und nicht einzelnen Benutzern gewähren. Erfahren Sie mehr über [Verwalten von Berechtigungen in Experience Manager Assets](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

#### Beschränken der Bereitstellung von Assets mit Ein- und Aus-Datum und -Uhrzeit {#restrict-delivery-assets-date-time}

DAM-Autoren können auch die Bereitstellung von Assets einschränken, indem sie eine Ein- oder Ausschaltzeit für die Aktivierung definieren, die in den Asset-Eigenschaften verfügbar ist.

Wenn Sie eine Einschaltzeit für die Aktivierung eines Assets definieren, wird zum festgelegten Zeitpunkt eine Bereitstellungs-URL für das Asset generiert. Das Asset bleibt vor dem definierten Zeitpunkt inaktiv. Wenn Sie eine Ausschaltzeit für ein Asset definieren, wird das Asset zum festgelegten Zeitpunkt deaktiviert und die Bereitstellungs-URL für das Asset wird nicht mehr mit dem Asset angezeigt.

Führen Sie die folgenden Schritte aus, um die Ein- und Ausschaltzeit für das Asset festzulegen:

1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.

1. Definieren Sie im Bereich **[!UICONTROL Geplante (de) Aktivierung]** auf der Registerkarte **[!UICONTROL Einfach]** die Einschaltzeit oder die Ausschaltzeit entsprechend Ihren Anforderungen.

In der Assets-Ansicht können Sie das Asset auswählen und auf **[!UICONTROL Details]** klicken, um die Asset-Eigenschaften anzuzeigen und die Ein- und Ausschaltzeit zu definieren.

Das Feld ist im Standard-Metadatenformular verfügbar. Wenn Ihr Asset nicht auf dem Standard-Metadatenschema basiert und die Felder Einschaltzeit und Ausschaltzeit in den Asset-Eigenschaften nicht verfügbar sind, führen Sie die folgenden Schritte in der Admin-Ansicht aus:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
1. Wählen Sie das Metadatenschema aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Fügen Sie ein Feld **[!UICONTROL Datum]** aus dem Abschnitt **[!UICONTROL Formular erstellen]** rechts zum Abschnitt &quot;Metadaten&quot;im Formular hinzu.
1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** durch:
   1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** in **Einschaltzeit** oder **Ausschaltzeit**.
   1. Aktualisieren Sie die **[!UICONTROL Zuordnung zu Eigenschaft]** auf _./jcr:content/onTime_ für die Felder **Einschaltzeit** und _./jcr:content/offTime_ für das Feld **Ausschaltzeit** verwenden.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

Wenn Ihr Asset in der Assets-Ansicht nicht auf dem Standard-Metadatenschema basiert und die Felder Einschaltzeit und Ausschaltzeit in den Asset-Eigenschaften nicht verfügbar sind, führen Sie die folgenden Schritte aus:

1. Klicken Sie im Abschnitt **[!UICONTROL Einstellungen]** auf **[!UICONTROL Metadaten-Forms]** .
1. Wählen Sie das Metadatenformular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Fügen Sie dem Formular ein Feld **[!UICONTROL Datum]** aus dem Abschnitt **[!UICONTROL Komponenten]** im linken Bereich hinzu.
1. Klicken Sie auf das neu hinzugefügte Feld und ändern Sie die **[!UICONTROL Beschriftung]** in **Einschaltzeit** oder **Ausschaltzeit**.
1. Aktualisieren Sie die Eigenschaft **[!UICONTROL Metadata]** auf _./jcr:content/onTime_ für die Felder **Einschaltzeit** und _./jcr:content/offTime_ für das Feld **Ausschaltzeit** verwenden.
1. Klicken Sie auf **[!UICONTROL Speichern]**.



### Bereitstellung von beschränkten Assets {#delivery-restricted-assets}

Die Bereitstellung eingeschränkter Assets basiert auf einer erfolgreichen Autorisierung für den Zugriff auf Assets. Die Autorisierung basiert entweder auf einem IMS-Token, wenn die Anfrage von einer AEM-Autoreninstanz oder einem Asset-Selektor gesendet wird, oder sie basiert auf einem speziellen Cookie, wenn Sie benutzerdefinierte Identitätsanbieter in Ihrer Publish- oder Vorschau-Instanz eingerichtet haben.

#### Bereitstellung für AEM Autoren- oder Asset-Selektor-Anforderungen {#delivery-aem-author-asset-selector}

Um die Bereitstellung eingeschränkter Assets zu aktivieren, wenn die Anfrage von AEM Autoreninstanz oder Asset-Selektor gesendet wird, ist ein gültiges IMS-Token erforderlich. Führen Sie die folgenden Schritte aus:

1. [Generieren Sie ein Zugriffstoken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * Melden Sie sich bei der Entwicklerkonsole Ihrer AEM as a Cloud Service-Umgebung an.

   * Navigieren Sie zu **[!UICONTROL Umgebung]** > **[!UICONTROL Integrationen]** > **[!UICONTROL Lokales Token]** > **[!UICONTROL Lokales Entwicklungstoken abrufen]** > **[!UICONTROL Wert accessToken kopieren]**. Erfahren Sie mehr über [den Zugriff auf Token und zugehörige Aspekte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. Integrieren Sie das erfasste Zugriffstoken in die Kopfzeile **[!UICONTROL Autorisierung]** und stellen Sie sicher, dass dem Wert **[!UICONTROL Bearer]** vorangestellt ist.

1. Validieren Sie die Funktionalität des Zugriffstokens durch Initiieren einer Anfrage. Es sollte einen 404-Fehler geben, wenn kein IMS-Zugriffstoken vorhanden ist oder das bereitgestellte Zugriffstoken nicht dieselben Prinzipale oder Gruppen wie die in den Metadaten des Assets hinzugefügten aufweist.

#### Bereitstellung für benutzerdefinierte Identitätsanbieter in der Publish-Instanz {#delivery-custom-identity-provider}

Bei einem benutzerdefinierten Identitäts-Provider, der in Ihrer Publish- oder Vorschauinstanz eingerichtet ist, können Sie die Gruppe erwähnen, die während des Einrichtungsprozesses Zugriff auf gesicherte Assets im Attribut `groupMembership` haben muss. Wenn Sie sich über die [SAML-Integration](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) bei einem benutzerdefinierten Identitäts-Provider anmelden, wird das Attribut `groupMembership` gelesen und verwendet, um ein Cookie zu erstellen, das in allen Authentifizierungsanfragen gesendet wird. Dies ähnelt einem IMS-Token bei einer Anfrage von AEM Autor oder Asset-Selektor.

Wenn ein sicheres Asset auf einer Seite verfügbar ist und eine Anfrage an die Bereitstellungs-URL zum Rendern des Assets gesendet wird, prüft AEM die im Cookie oder im IMS-Token vorhandenen Rollen und stimmt sie mit dem beim Authoring des Assets angewendeten `dam:roles property` überein. Wenn eine Übereinstimmung vorliegt, wird das Asset angezeigt.

>[!NOTE]
>
> Geben Sie im Support-Ticket [Dynamic Media mit OpenAPI-Funktionen aktivieren](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities) im Anwendungsfall die eingeschränkte Bereitstellung an. Adobe Engineering hilft bei der notwendigen Klarstellung und/oder bei der Einrichtung eines Verfahrens für die eingeschränkte Bereitstellung.
