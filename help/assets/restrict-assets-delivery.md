---
title: Beschränken der Bereitstellung von Assets mit Dynamic Media mit OpenAPI-Funktionen
description: Erfahren Sie, wie Sie die Asset-Bereitstellung mit OpenAPI-Funktionen einschränken.
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 6e9fa8301fba9cab1a185bf2d81917e45acfe3a3
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 1%

---

# Beschränken der Bereitstellung von Assets mit Dynamic Media mit OpenAPI-Funktionen {#restrict-access-to-assets}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets-Entwicklerdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Die zentrale Asset-Verwaltung in Experience Manager ermöglicht es DAM-Administratoren oder Brand Manager, den Zugriff auf Assets zu verwalten, die über Dynamic Media mit OpenAPI-Funktionen verfügbar sind. Sie können die Bereitstellung genehmigter Assets (bis hin zu einem einzelnen Asset) auf ausgewählte [Adobe Identity Management-Systembenutzer (IMS) oder -gruppen](https://helpx.adobe.com/in/enterprise/using/users.html#user-mgt-strategy) beschränken, indem sie bestimmte Metadaten für Assets in ihrem AEM as a Cloud Service-Autorendienst konfigurieren.

Sobald ein Asset über Dynamic Media mit OpenAPIs eingeschränkt ist, erhalten nur die (mit Adobe IMS integrierten) Benutzer, die für den Zugriff auf das Asset autorisiert sind, Zugriff. Um auf das Asset zugreifen zu können, muss der Benutzer die Funktionen [Suche](search-assets-api.md) und [Bereitstellung](deliver-assets-apis.md) von Dynamic Media mit OpenAPI nutzen.

![Eingeschränkter Zugriff auf Assets](/help/assets/assets/restricted-access.png)

In Experience Manager Assets umfasst der eingeschränkte Versand über IMS zwei wichtige Phasen:

* Authoring
* Bereitstellung

## Authoring {#authoring}

### Eingeschränkter Versand mit einem IMS-Träger-Token {#restrict-delivery-ims-token}

Sie können die Bereitstellung von Assets innerhalb von [!DNL Experience Manager] basierend auf IMS-Benutzer- und Gruppenidentitäten einschränken.

>[!NOTE]
>
> Diese Funktion ist derzeit nicht Self-Service. Um die Asset-Bereitstellung für IMS [Benutzer](https://helpx.adobe.com/in/enterprise/using/manage-directory-users.html) und [Gruppen](https://helpx.adobe.com/in/enterprise/using/user-groups.html) zu beschränken, wenden Sie sich an Ihr Enterprise-Supportteam, um zu erfahren, wie Sie die Informationen abrufen können, die zum Einschränken des Zugriffs vom Portal [Adobe Admin Console](https://adminconsole.adobe.com/) erforderlich sind, und wie Sie den Zugriff im AEM as a Cloud Service-Autorendienst konfigurieren.

### Beschränken der Bereitstellung von Assets mit Ein- und Aus-Datum und -Uhrzeit {#restrict-delivery-assets-date-time}

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



## Bereitstellung von beschränkten Assets {#delivery-restricted-assets}

Die Bereitstellung eingeschränkter Assets basiert auf einer erfolgreichen Autorisierung für den Zugriff auf Assets. Die Autorisierung erfolgt entweder über [IMS-Träger-Token](https://developer.adobe.com/developer-console/docs/guides/authentication/UserAuthentication/IMS/) (Anwendung für Anforderungen, die von der [AEM Asset-Auswahl](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) initiiert werden) oder ein sicheres Cookie (wenn Sie benutzerdefinierte Identitätsanbieter in Ihren AEM Publish-/Vorschau-Diensten eingerichtet haben und die Erstellung und Aufnahme von Cookies auf den Seiten eingerichtet haben).

### Bereitstellung für AEM Autoren- oder Asset-Selektor-Anforderungen {#delivery-aem-author-asset-selector}

Um die Bereitstellung von eingeschränkten Assets zu aktivieren, wenn die Anfrage vom Autoren-Dienst oder AEM Asset-Selektor gesendet wird, ist ein gültiges IMS-Träger-Token erforderlich.\
Bei AEM Cloud Service-Autorendiensten sowie bei der Asset-Auswahl wird das IMS-Träger-Token nach einer erfolgreichen Anmeldung automatisch generiert und für Anfragen verwendet.

>[!NOTE]
>
>Weitere Informationen zum Aktivieren der IMS-Authentifizierung bei AEM Asset Selector-basierten Integrationen erhalten Sie beim Enterprise Support

1. Für Erlebnisse, die nicht auf der Asset-Auswahl basieren, unterstützen AEM as a Cloud Service und Dynamic Media mit OpenAPI-Funktionen derzeit serverseitige API-Integrationen und können IMS-Träger-Token generieren.
   * Befolgen Sie die Anweisungen [hier](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#the-server-to-server-flow) , um Service-to-Server-API-Integrationen durchzuführen, mit denen die IMS-Träger-Token über [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) abgerufen werden können.
   * Für eine begrenzte Dauer kann der lokale Entwicklerzugriff (nicht für Produktionsanwendungsfälle gedacht) kurzlebige IMS-Träger-Token für den Benutzer generiert werden, der für [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) authentifiziert wurde. Befolgen Sie dazu die Anweisungen [hier](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#developer-flow) .

1. Fügen Sie bei der Durchführung von API-Anfragen für [Suche](search-assets-api.md) und [Bereitstellung](deliver-assets-apis.md) das abgerufene IMS-Trägertoken zum Header **[!UICONTROL Autorisierung]** der HTTP-Anforderung hinzu (stellen Sie sicher, dass dessen Wert mit dem Präfix **[!UICONTROL Bearer]** versehen ist).

1. Um die Zugriffsbeschränkung zu überprüfen, initiieren Sie eine Anfrage zur Bereitstellungs-API mit und ohne den Header **[!UICONTROL Autorisierung]** .
   * Die Antwort gibt den Fehlerstatus-Code `404` aus, wenn kein IMS-Träger-Token vorhanden ist oder das bereitgestellte IMS-Träger-Token nicht zum Benutzer gehört, dem Zugriff auf das Asset gewährt wurde (entweder direkt oder über die Gruppenmitgliedschaft).
   * Die Antwort gibt einen &quot;`200`&quot;-Erfolgsstatus-Code mit dem binären Inhalt des Assets aus, wenn das IMS-Träger-Token einer der Benutzer oder Gruppen ist, denen Zugriff auf das Asset gewährt wurde.

### Bereitstellung für benutzerdefinierte Identitätsanbieter im Publish-Dienst {#delivery-custom-identity-provider}

AEM Sites-, AEM Assets- und Dynamic Media-Lizenzen mit OpenAPI-Lizenzen können gemeinsam verwendet werden und die eingeschränkte Bereitstellung von Assets kann auf Websites konfiguriert werden, die über AEM Publish oder Vorschaudienste bereitgestellt werden.
Wenn die Publish- und Vorschaudienste von AEM Sites so konfiguriert sind, dass ein [benutzerdefinierter Identitäts-Provider (IdP)](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) verwendet wird, kann die Gruppe, die Zugriff auf gesicherte Assets in haben muss, während des Einrichtungsprozesses im Attribut `groupMembership` enthalten sein.\
Wenn sich ein Website-Benutzer beim benutzerdefinierten Identitätsanbieter anmeldet und auf die im Publish/Preview-Dienst gehostete Website zugreift, wird das Attribut `groupMembership` gelesen und ein secure-cookie erstellt und auf der Website bereitgestellt, nachdem die Authentifizierung erfolgreich war. Dieses secure-cookie ist in allen nachfolgenden Anfragen enthalten, um den Website-Inhalt an den Benutzer-Agenten bereitzustellen.

Wenn ein sicheres Asset auf einer Seite angefordert wird, extrahieren AEM Publish- und Vorschaustufen das Autorisierungsmaterial aus dem secure-cookie und validieren den Zugriff. Wenn eine Übereinstimmung vorliegt, wird das Asset angezeigt.

>[!NOTE]
>
> Geben Sie im Support-Ticket [Dynamic Media mit OpenAPI-Funktionen aktivieren](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities) im Anwendungsfall die eingeschränkte Bereitstellung an. Adobe Engineering hilft bei der notwendigen Klarstellung und/oder bei der Einrichtung eines Verfahrens für die eingeschränkte Bereitstellung.