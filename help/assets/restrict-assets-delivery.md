---
title: Beschränken der Bereitstellung von Assets mit Dynamic Media mit OpenAPI-Funktionen
description: Erfahren Sie, wie Sie die Asset-Bereitstellung mit OpenAPI-Funktionen einschränken können.
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 97%

---

# Beschränken der Bereitstellung von Assets mit Dynamic Media mit OpenAPI-Funktionen {#restrict-access-to-assets}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>Das Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch zu Dynamic Media mit OpenAPI-Funktionen als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Die zentrale Asset-Governance in Experience Manager ermöglicht es DAM-Admins oder Markenverantwortlichen, den Zugriff auf verfügbare Assets mithilfe von Dynamic Media mit OpenAPI-Funktionen zu verwalten. Sie können die Bereitstellung genehmigter Assets (bis hin zu einem einzelnen Asset) auf ausgewählte [Adobe Identity Management System(IMS)-Benutzende oder -Gruppen](https://helpx.adobe.com/de/enterprise/using/users.html#user-mgt-strategy) beschränken, indem sie bestimmte Metadaten für Assets in ihrem AEM as a Cloud Service-Autorendienst konfigurieren.

Sobald ein Asset über Dynamic Media mit OpenAPIs eingeschränkt ist, erhalten nur die (in Adobe IMS integrierten) Benutzenden Zugriff, die für den Zugriff auf das besagte Asset autorisiert sind. Um auf das Asset zugreifen zu können, muss die Person die Funktionen [Suchen](search-assets-api.md) und [Bereitstellen](deliver-assets-apis.md) von Dynamic Media mit OpenAPI nutzen.

![Eingeschränkter Zugriff auf Assets](/help/assets/assets/restricted-access.png)

In Experience Manager Assets umfasst die eingeschränkte Bereitstellung per IMS zwei wichtige Phasen:

* Authoring
* Bereitstellung

## Authoring {#authoring}

### Eingeschränkte Bereitstellung mit einem IMS-Bearer-Token {#restrict-delivery-ims-token}

Sie können die Bereitstellung von Assets innerhalb von [!DNL Experience Manager] basierend auf IMS-Benutzer- und Gruppenidentitäten einschränken.

>[!NOTE]
>
>Diese Funktion gibt derzeit nicht als Self-Service. Um die Asset-Bereitstellung für IMS-[Benutzende](https://helpx.adobe.com/de/enterprise/using/manage-directory-users.html) und -[Gruppen](https://helpx.adobe.com/de/enterprise/using/user-groups.html) zu beschränken, wenden Sie sich an Ihr Unternehmens-Supportteam, um zu erfahren, wie Sie die Informationen abrufen können, die zum Einschränken des Zugriffs über das [Adobe Admin Console](https://adminconsole.adobe.com/)-Portal erforderlich sind, und wie Sie den Zugriff im Autoren-Service von AEM as a Cloud Service konfigurieren.

### Beschränken der Bereitstellung von Assets mit Datum und Uhrzeit für das Ein- und Ausschalten {#restrict-delivery-assets-date-time}

DAM-Autorinnen bzw. -Autoren können die Bereitstellung von Assets auch einschränken, indem sie eine Ein- oder Ausschaltzeit für die Aktivierung definieren, die in den Asset-Eigenschaften verfügbar ist.

Wenn Sie eine Einschaltzeit für die Aktivierung eines Assets definieren, wird zum festgelegten Zeitpunkt eine Bereitstellungs-URL für das Asset generiert. Vor dem definierten Zeitpunkt bleibt das Asset inaktiv. Wenn Sie eine Ausschaltzeit für ein Asset definieren, wird das Asset zum festgelegten Zeitpunkt deaktiviert und die Bereitstellungs-URL für das Asset zeigt das Asset nicht mehr an.

Führen Sie die folgenden Schritte aus, um die Ein- und Ausschaltzeit für das Asset festzulegen:

1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.

1. Definieren Sie auf der Registerkarte **[!UICONTROL Allgemein]** im Abschnitt **[!UICONTROL Geplante Aktivierung/Deaktivierung]** die Einschaltzeit oder die Ausschaltzeit basierend auf Ihren Anforderungen.

Sie können auch in der Assets-Ansicht das Asset auswählen und auf **[!UICONTROL Details]** klicken, um die Asset-Eigenschaften anzuzeigen und dort die Einschaltzeit und Ausschaltzeit zu definieren.

Das Feld ist im Standard-Metadatenformular verfügbar. Wenn Ihr Asset nicht auf dem Standard-Metadatenschema basiert und die Felder „Einschaltzeit“ und „Ausschaltzeit“ in den Asset-Eigenschaften nicht verfügbar sind, führen Sie die folgenden Schritte in der Admin-Ansicht aus:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
1. Wählen Sie das Metdadatenschema aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Fügen Sie über den Abschnitt **[!UICONTROL Formular erstellen]** auf der rechten Seite ein Feld **[!UICONTROL Datum]** zum Abschnitt „Metadaten“ des Formulars hinzu.
1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** durch:
   1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** in **Einschaltzeit** oder **Ausschaltzeit**.
   1. Setzen Sie **[!UICONTROL Zu Eigenschaft zuordnen]** auf _./jcr:content/onTime_ für das Feld **Einschaltzeit** und auf _./jcr:content/offTime_ für das Feld **Ausschaltzeit**.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

Wenn Ihr Asset in der Assets-Ansicht nicht auf dem Standard-Metadatenschema basiert und die Felder „Einschaltzeit“ und „Ausschaltzeit“ in den Asset-Eigenschaften nicht verfügbar sind, führen Sie die folgenden Schritte aus:

1. Klicken Sie im Abschnitt **[!UICONTROL Einstellungen]** auf **[!UICONTROL Metadatenformulare]**.
1. Wählen Sie das Metadatenformular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Fügen Sie über den Abschnitt **[!UICONTROL Komponenten]** im linken Bereich ein Feld **[!UICONTROL Datum]** zum Formular hinzu.
1. Klicken Sie auf das neu hinzugefügte Feld und ändern Sie die **[!UICONTROL Bezeichnung]** in **Einschaltzeit** oder **Ausschaltzeit**.
1. Aktualisieren Sie die **[!UICONTROL Metadateneigenschaft]** auf _./jcr:content/onTime_ für das Feld **Einschaltzeit** und auf _./jcr:content/offTime_ für das Feld **Ausschaltzeit**.
1. Klicken Sie auf **[!UICONTROL Speichern]**.



## Bereitstellung von beschränkten Assets {#delivery-restricted-assets}

Die Bereitstellung beschränkter Assets basiert auf einer erfolgreichen Autorisierung für den Zugriff auf Assets. Die Autorisierung erfolgt entweder über [IMS-Bearer-Token](https://developer.adobe.com/developer-console/docs/guides/authentication/UserAuthentication/IMS/) (Anwendung für Anfragen, die über den [AEM Asset-Wähler](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) initiiert wird) oder ein sicheres Cookie (wenn Sie benutzerdefinierte Identitätsanbieter in Ihren AEM Veröffentlichungs-/Vorschau-Services eingerichtet haben und die Erstellung und Aufnahme von Cookies auf den Seiten eingerichtet haben).

### Bereitstellung für Anfragen von AEM Author oder vom Asset-Wähler {#delivery-aem-author-asset-selector}

Um die Bereitstellung von beschränkten Assets zu aktivieren, wenn die Anfrage vom AEM Autoren-Service oder vom AEM Asset-Wähler gesendet wird, ist ein gültiges IMS-Bearer-Token erforderlich.\
Bei Autoren-Services von AEM Cloud Service sowie beim Asset-Wähler wird das IMS-Bearer-Token nach einer erfolgreichen Anmeldung automatisch generiert und für Anfragen verwendet.

>[!NOTE]
>
>Wenden Sie sich an den Enterprise Support, um weitere Informationen zum Aktivieren der IMS-Authentifizierung bei Integrationen zu erhalten, die auf dem AEM Asset-Wähler basieren.

1. Für Erlebnisse, die nicht auf dem Asset-Wähler basieren, unterstützen AEM as a Cloud Service und Dynamic Media mit OpenAPI-Funktionen derzeit Server-seitige API-Integrationen und können IMS-Bearer-Token generieren.
   * Befolgen Sie die Anweisungen [hier](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#the-server-to-server-flow), um Service-to-Server-API-Integrationen durchzuführen, mit denen die IMS-Bearer-Token über die [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) abgerufen werden können
   * Für einen zeitlich begrenzten, lokalen Entwicklerzugriff (nicht für Produktionsanwendungen gedacht) können kurzlebige IMS-Bearer-Token für die Person, die in der [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) authentifiziert wurde, generiert werden, indem die Anweisungen [hier](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#developer-flow) befolgt werden

1. Fügen Sie bei der Durchführung der API-Anfragen [Suchen](search-assets-api.md) und [Bereitstellen](deliver-assets-apis.md) das abgerufene IMS-Bearer-Token zum Header **[!UICONTROL Autorisierung]** der HTTP-Anfrage hinzu (stellen Sie sicher, dass dessen Wert mit dem Präfix **[!UICONTROL Bearer]** versehen ist).

1. Um die Zugriffsbeschränkung zu überprüfen, initiieren Sie eine Bereitstellungs-API-Anfrage einmal mit und einmal ohne Header **[!UICONTROL Autorisierung]**.
   * Die Antwort gibt den Fehlerstatus-Code `404` aus, wenn kein IMS-Bearer-Token vorhanden ist oder das bereitgestellte IMS-Bearer-Token nicht zu der Person gehört, der (entweder direkt oder über die Gruppenmitgliedschaft) Zugriff auf das Asset gewährt wurde.
   * Die Antwort gibt einen Erfolgsstatus-Code `200` mit dem binären Inhalt des Assets aus, wenn das IMS-Bearer-Token eine der Personen oder Gruppen ist, denen Zugriff auf das Asset gewährt wurde.

### Bereitstellung für benutzerdefinierte Identitätsanbieter im Veröffentlichungs-Service {#delivery-custom-identity-provider}

Lizenzen für AEM Sites, AEM Assets und Dynamic Media mit OpenAPI können gemeinsam verwendet werden, um die Konfiguration der beschränkten Bereitstellung von Assets auf Websites zu ermöglichen, die auf dem AEM Veröffentlichungs- oder Vorschau-Service gehostet werden. Der sichere Bereitstellungsfluss nutzt Browser-Cookies, um den Zugriff der Person festzustellen und über eine benutzerdefinierte Domain für die Bereitstellungsebene zu verfügen, die eine Subdomain der Veröffentlichungs-Domain ist. Dies ist eine Voraussetzung für die Implementierung dieses Anwendungsfalls. Falls die Veröffentlichungs- und Vorschau-Services von AEM Sites so konfiguriert sind, dass sie einen [benutzerdefinierten Identitätsanbieter (IdP)](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) verwenden, muss nach der Authentifizierung der Person ein neues Cookie mit dem Namen `delivery-token` für die Veröffentlichungs-Domain festgelegt werden, das die Gruppenmitgliedschaft der Person enthält. Die Bereitstellungsebene extrahiert das Autorisierungsmaterial aus dem sicheren Cookie und validiert den Zugriff. Reichen Sie ein [Support-Ticket für Unternehmen](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities) ein, um weitere Informationen zu erhalten.
