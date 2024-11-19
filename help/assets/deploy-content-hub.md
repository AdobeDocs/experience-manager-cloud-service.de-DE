---
title: Bereitstellen [!DNL Content Hub]
description: Erfahren Sie, wie Sie den Content-Hub bereitstellen und aktivieren sowie Benutzenden mit unterschiedlichen Berechtigungstypen Zugriff (Assets hochladen, Adobe Express-Benutzende) und Administrationsberechtigungen gewähren.
role: Admin
exl-id: 58194858-6e1c-460b-bab3-3496176b2851
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 7%

---

# Bereitstellen von Content-Hub {#deploy-content-hub}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Bereitstellen von Content-Hub](assets/deploy-content-hub.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub Guide PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Content Hub ist als Teil von Experience Manager Assets as a Cloud Service für die Demokratisierung des Zugriffs auf Markeninhalte für Unternehmen und ihre Geschäftspartner verfügbar.

Die Assets, die in Experience Manager Assets as a Cloud Service als &quot;Genehmigt&quot;markiert sind, stehen für die Asset-Verteilung in Content Hub zur Verfügung.

Dieser Artikel bietet einen durchgängigen Arbeitsablauf, mit dem Content Hub-Zugriff für Benutzer bereitgestellt werden kann, einschließlich der verschiedenen Arten von Berechtigungen je nach Bedarf.

Zu den verschiedenen Berechtigungen für Content Hub gehören:

* [Content Hub-Benutzer](#onboard-content-hub-users): Greifen Sie auf markengenehmigte Assets im Content Hub-Portal zu.

* [Content Hub-Administratoren](#onboard-content-hub-administrator): Zugriff auf die [Konfigurations-Benutzeroberfläche](/help/assets/configure-content-hub-ui-options.md) in Content Hub, zusätzlich zum Zugriff auf markengenehmigte Assets, zum Hochladen von Assets in Content Hub, zur Bildintegration (wenn Sie über Adobe Expreß-Berechtigungen verfügen).

* [Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets](#onboard-content-hub-users-add-assets): Möglichkeit, Assets in Content Hub](/help/assets/upload-brand-approved-assets.md) zu laden, zusätzlich zum Zugriff auf markengenehmigte Assets im Content Hub-Portal.[

* [Content Hub-Benutzer mit Berechtigungen zum Remix von Assets in neue Varianten](#onboard-content-hub-users-remix-assets): [Adobe Express-Integration](/help/assets/edit-images-content-hub.md) (wenn Sie über Adobe Expreß-Berechtigungen verfügen), die nicht nur auf markengenehmigte Assets im Content Hub-Portal zugreifen, sondern auch darauf zugreifen können.

* [Experience Manager Assets-Benutzer](#experience-manager-assets-users): Möglichkeit, Assets in Experience Manager Assets as a Cloud Service zu genehmigen, um diese Assets in Content Hub verfügbar zu machen.

In der folgenden Tabelle sind die verfügbaren Content Hub-Benutzertypen, ihre Berechtigungen und die Produktprofile zusammengefasst, die zum Erhalt dieser Berechtigungen erforderlich sind:

| Benutzerrolle | Content Hub-Benutzer | Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets | Content Hub-Benutzer mit Berechtigungen zum Remix von Assets | Content Hub-Administratoren |
|---------------|----------|----------|-------------------------|---|
| **Funktionen** |
| Zugriff auf markenbestätigte Assets im Content Hub-Portal | ✓ | ✓ | ✓ | ✓ |
| Hochladen von Assets aus dem Content Hub-Portal | − | ✓ | ✓ | ✓ |
| Adobe Expreß-Integration zum Bearbeiten von Bildern verwenden | − | − | ✓ | − |
| Zugriff auf die Benutzeroberfläche der Content Hub-Konfiguration | − | − | − | ✓ |
| **Benutzer muss sich in diesen Produktprofilen befinden (Admin Console)** |
| AEM > Versandinstanz > AEM Assets Limited Users | ✓ | ✓ | ✓ | ✓ |
| AEM > Produktions-Autoreninstanz > AEM Benutzer | − | ✓ | ✓ | − |
| AEM > Produktions-Autoreninstanz > AEM Administratoren | − | − | − | ✓ |
| Adobe Express | − | − | ✓ | − |
| **Weitere Informationen** | Siehe [Content Hub-Benutzer](#onboard-content-hub-users) | Siehe [Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets](#onboard-content-hub-users-add-assets) | Siehe [Content Hub-Benutzer mit Berechtigungen zum Remix von Assets in neue Varianten](#onboard-content-hub-users-remix-assets) | Siehe [Content Hub-Administratoren](#onboard-content-hub-administrator) |

>[!NOTE]
>
[Experience Manager Assets-Benutzer](#experience-manager-assets-users) haben die Möglichkeit, Assets in einer Experience Manager Assets as a Cloud Service-Umgebung zu genehmigen, um diese Assets in Content Hub verfügbar zu machen. Diese Benutzer müssen über die Admin Console zu AEM > Produktions-Autoreninstanz > AEM Benutzerprofil hinzugefügt werden.

## Schritt 1: Aktivieren von Content Hub für Experience Manager Assets mithilfe von Cloud Manager {#enable-content-hub}

Um auf das Content Hub-Portal zugreifen zu können, müssen Administratoren zunächst Content Hub für Experience Manager Assets as a Cloud Service mithilfe von Cloud Manager aktivieren. Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Cloud Manager an. Stellen Sie sicher, dass Sie beim Anmelden die richtige Organisation auswählen. Die Cloud Manager listet alle Ihre Programme auf.

1. Navigieren Sie zum Programm Experience Manager Assets as a Cloud Service , klicken Sie auf das Symbol Weitere Optionen (...) und wählen Sie **[!UICONTROL Programm bearbeiten]** aus.

   ![Programm in Cloud Manager bearbeiten](assets/edit-program-cloud-manager.png)

1. Wählen Sie im Dialogfeld [!UICONTROL Programm bearbeiten] die Registerkarte **[!UICONTROL Lösungen und Add-ons]** aus.

1. Erweitern Sie **[!UICONTROL Assets]** und wählen Sie **[!UICONTROL Content Hub]** aus.
   ![Content Hub in Cloud Manager auswählen](assets/edit-program-cloud-manager-content-hub.png)

   >[!NOTE]
   >
   Wenn **[!UICONTROL Aktualisieren]** nach Auswahl von Content Hub nicht für Sie aktiviert ist, stellen Sie sicher, dass Sie die Go-Live-Einstellungen für das Programm festgelegt haben.

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**.

Content Hub ist jetzt für Experience Manager Assets as a Cloud Service aktiviert. Nachdem Sie Content Hub in einer Produktionsumgebung aktiviert haben, können Sie es nicht in einer Self-Service-Umgebung deaktivieren.

>[!NOTE]
>
Sie können auf Content Hub mit bis zu 250 Content Hub-Benutzern zugreifen und es verwenden. Wenden Sie sich bei weiteren Fragen an Ihren Adobe-Support-Mitarbeiter.


Wenn Sie neu bei Experience Manager Assets sind, klicken Sie auf **[!UICONTROL Programm hinzufügen]**, geben Sie dann Programmdetails an (Programmname, für die Produktion eingerichtet) und klicken Sie auf **[!UICONTROL Weiter]**. Anschließend können Sie auf der Registerkarte **[!UICONTROL Lösungen und Add-ons]** die Optionen **[!UICONTROL Assets]** und **[!UICONTROL Content Hub]** auswählen.

### Content Hub-Instanz und -Produktprofil auf Admin Console{#content-hub-instance-product-profile}

Nach der [Aktivierung von Content Hub für Assets as a Cloud Service mithilfe von Cloud Manager](#enable-content-hub) wird in AEM Assets as a Cloud Service eine neue Instanz mit dem Suffix `delivery` erstellt:

![Neue Instanz für Content Hub](assets/new-instance-content-hub.png)

>[!NOTE]
>
Wenn Sie Content Hub vor dem 14. August 2024 bereitgestellt haben, wird die neue Instanz mit `contenthub` als Suffix erstellt.

Beachten Sie, dass der Instanzname für Content Hub nicht `author` oder `publish` enthält.

Klicken Sie auf den Instanznamen, um das Content Hub-Produktprofil anzuzeigen.

![Content Hub-Produktprofil](assets/content-hub-product-profile.png)

>[!NOTE]
>
Wenn Sie Content Hub vor dem 14. August 2024 bereitgestellt haben, wird für das Content Hub-Produktprofil nach `Limited Users` anstelle von `delivery` `contenthub` angegeben.

## Schritt 2: Integrierter Content Hub-Administrator {#onboard-content-hub-administrator}

Content Hub-Administratoren können auf die [Konfigurations-Benutzeroberfläche](/help/assets/configure-content-hub-ui-options.md) in Content Hub zugreifen, zusätzlich zum Zugriff auf markengenehmigte Assets, zum Hochladen von Assets in Content Hub und zur Bildintegration (wenn Sie über Adobe Expreß-Berechtigungen verfügen).

So integrieren Sie den Content Hub-Administrator:

1. [Greifen Sie auf das Content Hub-Benutzerproduktprofil zu und klicken Sie darauf.](#content-hub-instance-product-profile)

1. Klicken Sie auf **[!UICONTROL Benutzer hinzufügen]** , um dem Produktprofil Benutzer oder Benutzergruppen hinzuzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

1. Nachdem Sie den Benutzer zum Content Hub-Produktprofil hinzugefügt haben, greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Produktprofil Administratoren und dann auf **[!UICONTROL Benutzer hinzufügen]** , um den Benutzer zum Produktprofil hinzuzufügen.
   ![Administrator-Produktprofil](assets/aem-cs-admin-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

## Schritt 3: Onboard Content Hub-Benutzer {#onboard-content-hub-users}

Content Hub-Benutzer können auf Assets zugreifen, die im Portal verfügbar sind, jedoch keine neuen Assets hinzufügen oder vorhandene Assets ändern.

So integrieren Sie Content Hub-Benutzer:

1. [Greifen Sie auf das Content Hub-Benutzerproduktprofil zu und klicken Sie darauf.](#content-hub-instance-product-profile)

1. Klicken Sie auf **[!UICONTROL Benutzer hinzufügen]** , um dem Produktprofil Benutzer oder Benutzergruppen hinzuzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Diese Benutzer können jetzt auf die im Content Hub-Portal verfügbaren Assets zugreifen.

>[!NOTE]
>
Sie können alle erweiterten Unternehmensfunktionen wie die Synchronisierung mit externen Identitätsanbietern verwenden.

### Zugriff auf Content Hub {#access-content-hub}

Der Zugriff auf Content Hub erfolgt auf folgende Weise:

* Greifen Sie über den folgenden Link auf Content Hub zu:

  `https://experience.adobe.com/#/assets/contenthub`

* Melden Sie sich bei `experience.adobe com` an und klicken Sie auf **[!UICONTROL Experience Manager Assets Content Hub]** , der im Abschnitt **[!UICONTROL Schnellzugriff]** verfügbar ist:
  ![Content Hub-Zugriff](assets/access-content-hub.png)

* Melden Sie sich bei &quot;`experience.adobe com`&quot;an und klicken Sie im Produktschalter auf &quot;**[!UICONTROL Experience Manager Assets Content Hub]**&quot;:
  ![Content Hub-Zugriffsmethode 3](assets/access-content-hub-alternate.png)

### E-Mail-Benachrichtigungen für Benutzer deaktivieren {#disable-email-notifications}

Wenn Administratoren E-Mail-Benachrichtigungen deaktivieren müssen, die an Benutzer gesendet werden, wenn sie zum Content Hub-Produktprofil hinzugefügt werden:

Klicken Sie auf das Suchsymbol neben dem Produktprofilnamen und deaktivieren Sie den Umschalter **[!UICONTROL Benutzer per E-Mail benachrichtigen]** .

![E-Mail-Benachrichtigungen deaktivieren](assets/disable-email-notifications.png)


## Schritt 4: Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets einbinden (optional) {#onboard-content-hub-users-add-assets}

Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets können [neue markengenehmigte Assets in Content Hub hochladen](/help/assets/upload-brand-approved-assets.md).

So integrieren Sie Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Benutzern:

1. [ Nachdem Sie den Benutzer zum Content Hub-Produktprofil hinzugefügt haben, greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.](#onboard-content-hub-users)

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Benutzerproduktprofil und dann auf &quot;**[!UICONTROL Benutzer hinzufügen]**&quot;, um den Benutzer zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-cs-user-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

## Schritt 4: Integrieren von Content Hub-Benutzern mit Berechtigungen zum Neumischen von Assets in neue Varianten (optional) {#onboard-content-hub-users-remix-assets}

Content Hub-Benutzer mit der Berechtigung zum Neumischen von Assets in neue Varianten können [vorhandene Assets mithilfe von Adobe Express ändern und das Asset im Repository speichern](/help/assets/edit-images-content-hub.md). Die Bearbeitung von Assets mit Adobe Express ist nur verfügbar, wenn der Benutzer über Adobe Expreß-Berechtigungen verfügt.

So integrieren Sie Content Hub-Benutzer mit Berechtigungen zum Remix von Assets in neue Varianten:

1. [ Nachdem Sie den Benutzer zum Content Hub-Produktprofil hinzugefügt haben, greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.](#onboard-content-hub-users)

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Benutzerproduktprofil und dann auf &quot;**[!UICONTROL Benutzer hinzufügen]**&quot;, um den Benutzer zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-cs-user-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

## Experience Manager Assets-Benutzer {#experience-manager-assets-users}

Experience Manager Assets-Benutzer können Assets in AEM as a Cloud Service genehmigen, damit sie in Content Hub verfügbar sind.

So konfigurieren Sie Experience Manager Assets-Benutzer:

1. Greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Benutzerproduktprofil und dann auf &quot;**[!UICONTROL Benutzer hinzufügen]**&quot;, um den Benutzer zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-cs-user-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

   >[!NOTE]
   >
   Sie müssen nicht zum [Content Hub-Produktprofil](#onboard-content-hub-users) für Experience Manager Assets-Benutzer hinzugefügt werden.
