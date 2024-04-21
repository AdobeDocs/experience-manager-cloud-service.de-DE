---
title: Beschränken der Bereitstellung von Assets in Experience Manager
description: Erfahren Sie, wie Sie die Asset-Bereitstellung in einschränken. [!DNL Experience Manager].
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 1%

---

# Beschränken des Zugriffs auf Assets in [!DNL Experience Manager] {#restrict-access-to-assets}

Die zentrale Asset-Verwaltung in Experience Manager ermöglicht es dem DAM-Administrator oder Brand Manager, den Zugriff auf Assets zu verwalten. Sie können den Zugriff einschränken, indem sie Rollen für genehmigte Assets auf der Autorenseite, insbesondere auf der AEM as a Cloud Service Autoreninstanz, konfigurieren.

Benutzer [Suchen](search-assets-api.md) oder Verwendung [Bereitstellungs-URLs](deliver-assets-apis.md) kann nach erfolgreichem Bestehen des Autorisierungsprozesses Zugriff auf eingeschränkte Assets erhalten.

![Beschränkter Zugriff auf Assets](/help/assets/assets/restricted-access.png)

## Eingeschränkter Versand mit einem IMS-Token {#restrict-delivery-ims-token}

Im Experience Manager umfasst der eingeschränkte Versand über IMS zwei wichtige Phasen:

* Authoring
* Bereitstellung

### Authoring {#authoring}

Um die Bereitstellung von Assets zu beschränken, müssen Rollen für die Assets innerhalb der [!DNL Experience Manager] oder [!DNL Experience Manager Assets]. So konfigurieren Sie Rollen in [!DNL Experience Manager]führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu [!DNL Experience Manager] als DAM-Administrator.
1. Wählen Sie das Asset aus, für das Sie die Rolle konfigurieren müssen.
1. Navigieren Sie zu **[!UICONTROL Eigenschaften]** > **[!UICONTROL Erweitert]** und stellen sicher, dass **[!UICONTROL Rollen]** -Feld in vorhanden ist. [!UICONTROL Erweiterte Metadaten] Registerkarte.

   ![Benutzermetadaten](/help/assets/assets/roles_metadata.jpg)
Wenn das Feld nicht verfügbar ist, führen Sie die folgenden Schritte aus, um das Feld hinzuzufügen:

   1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
   1. Wählen Sie das Metadatenschema aus und klicken Sie auf **[!UICONTROL Bearbeiten _e)_]**.
   1. Hinzufügen einer **[!UICONTROL Mehrwerttext]** aus dem **[!UICONTROL Formular erstellen]** rechts neben dem Abschnitt Metadaten im Formular.
   1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im  **[!UICONTROL Einstellungen]** Bereich:
      1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** nach _Rollen_.
      1. Aktualisieren Sie die **[!UICONTROL Zu Eigenschaft zuordnen]** nach _./jcr:content/metadata/dam:roles_.

1. Rufen Sie die IMS-Gruppen ab, die in den Roles-Metadaten des Assets hinzugefügt werden sollen. Gehen Sie wie folgt vor, um die IMS-Gruppen abzurufen:
   1. Melden Sie sich unter https://adminconsole.adobe.com/ an.
   1. Navigieren Sie zu Ihrer jeweiligen Organisation und navigieren Sie zu **[!UICONTROL Benutzergruppen]**.
   1. Wählen Sie die **[!UICONTROL Benutzergruppe]** Sie müssen die **[!UICONTROL orgID]** und **[!UICONTROL userGroupID]** aus der URL aus oder verwenden Sie Ihre Organisations-ID, z. B. `{orgID}@AdobeOrg:{usergroupID}`.

1. Fügen Sie die Gruppen-ID zum **[!UICONTROL Rollen]** -Feld der Asset-Eigenschaften. <br>
Die in der Variablen **[!UICONTROL Rollen]** -Feld sind die einzigen Benutzer, die auf das Asset zugreifen können. Sie können auch die IMS-Client-ID und die IMS-Profil-ID im **[!UICONTROL Rollen]** -Feld. Zum Beispiel: `{orgId}@AdobeOrg:{profileId}`.

   >[!NOTE]
   >
   >Für die neue Asset-Ansicht können Sie nur Zugriff auf die Ordnerebene und ausschließlich Gruppen und nicht einzelnen Benutzern gewähren. Weitere Informationen [Berechtigungen in Experience Manager Assets verwalten](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

### Bereitstellung von beschränkten Assets {#delivery-restricted-assets}

Die Bereitstellung eingeschränkter Assets basiert auf einer erfolgreichen Autorisierung für den Zugriff auf Assets. Die Autorisierung basiert entweder auf einem IMS-Token, wenn die Anfrage von einer AEM-Autoreninstanz oder einem Asset-Selektor gesendet wird, oder sie basiert auf einem speziellen Cookie, wenn Sie benutzerdefinierte Identitätsanbieter in Ihrer Veröffentlichungs- oder Vorschau-Instanz eingerichtet haben.

#### Bereitstellung für AEM Autor oder Asset-Auswahl {#delivery-aem-author-asset-selector}

Um die Bereitstellung eingeschränkter Assets zu aktivieren, wenn die Anfrage von AEM Autoreninstanz oder Asset-Selektor gesendet wird, ist ein gültiges IMS-Token erforderlich. Führen Sie die folgenden Schritte aus:

1. [Zugriffstoken generieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * Melden Sie sich bei der Entwicklerkonsole Ihrer AEM as a Cloud Service Umgebung an.

   * Navigieren Sie zu **[!UICONTROL Umgebung]** > **[!UICONTROL Integrationen]** > **[!UICONTROL Lokaler Token]** > **[!UICONTROL Abrufen des lokalen Entwicklungstokens]** > **[!UICONTROL Kopieren des accessToken-Werts]**. Weitere Informationen [Zugriff auf Token und zugehörige Aspekte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. Integrieren Sie das erhaltene Zugriffstoken in das **[!UICONTROL Autorisierung]** -Kopfzeile, die sicherstellt, dass ihr Wert mit dem Präfix **[!UICONTROL Bearer]**.

1. Validieren Sie die Funktionalität des Zugriffstokens durch Initiieren einer Anfrage. Es sollte einen 404-Fehler geben, wenn kein IMS-Zugriffstoken vorhanden ist oder das bereitgestellte Zugriffstoken nicht dieselben Prinzipale oder Gruppen wie die in den Metadaten des Assets hinzugefügten aufweist.

#### Bereitstellung für benutzerdefinierte Identitätsanbieter {#delivery-custom-identity-provider}

Bei einem benutzerdefinierten Identitäts-Provider, der in Ihrer Veröffentlichungs- oder Vorschauinstanz eingerichtet ist, können Sie die Gruppe erwähnen, die Zugriff auf gesicherte Assets in `groupMembership` -Attribut während des Einrichtungsprozesses hinzugefügt werden. Bei der Anmeldung bei einem benutzerdefinierten Identitätsanbieter über [SAML-Integration](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0), die `groupMembership` -Attribut gelesen und verwendet wird, um ein Cookie zu erstellen, das in allen Authentifizierungsanfragen gesendet wird, ähnlich wie ein IMS-Token bei einer Anfrage von AEM Autor oder Asset-Selektor.

Wenn ein sicheres Asset auf einer Seite verfügbar ist und eine Anfrage an die Bereitstellungs-URL gesendet wird, um das Asset zu rendern, AEM überprüft die im Cookie oder im IMS-Token vorhandenen Rollen und stimmt es mit dem `dam:roles property` wird beim Authoring des Assets angewendet. Wenn eine Übereinstimmung vorliegt, wird das Asset angezeigt.
