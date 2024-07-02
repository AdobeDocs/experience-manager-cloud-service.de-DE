---
title: Bereitstellen [!DNL Content Hub]
description: Erfahren Sie, wie Sie Content Hub bereitstellen und aktivieren und Benutzern mit unterschiedlichen Berechtigungstypen Zugriff gewähren (Assets hochladen, Adobe Expreß-Benutzer) und wie Sie Benutzern Administratorberechtigungen gewähren.
role: Admin
source-git-commit: 0d340508823be6a2c6c2beb28c17ddfb2bf6b790
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 3%

---


# Content Hub bereitstellen {#deploy-content-hub}

![Content Hub bereitstellen](assets/deploy-content-hub.png)

Content Hub ist als Teil von Experience Manager Assets as a Cloud Service für die Demokratisierung des Zugriffs auf Markeninhalte für Unternehmen und ihre Geschäftspartner verfügbar.

Die Assets, die in Experience Manager Assets as a Cloud Service als &quot;Genehmigt&quot;markiert sind, stehen für die Asset-Verteilung in Content Hub zur Verfügung.

Dieser Artikel bietet einen durchgängigen Arbeitsablauf, mit dem Content Hub-Zugriff für Benutzer bereitgestellt werden kann, einschließlich der verschiedenen Arten von Berechtigungen je nach Bedarf.

Zu den verschiedenen Berechtigungen für Content Hub gehören:

* [Content Hub-Benutzer](#onboard-content-hub-users): Greifen Sie auf markenbestätigte Assets im Content Hub-Portal zu.

* [Content Hub-Administratoren](#onboard-content-hub-administrator): Zugriff auf die [Konfigurationsoberfläche](/help/assets/configure-content-hub-ui-options.md) in Content Hub neben dem Zugriff auf markengenehmigte Assets, dem Hochladen von Assets in Content Hub, der Bildintegration zum Bearbeiten von Adobe Expressen (wenn Sie über Adobe Expreß-Berechtigungen verfügen).

* [Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets](#onboard-content-hub-users-add-assets): Fähigkeit, [Hochladen von Assets in Content Hub](/help/assets/upload-brand-approved-assets.md) nicht nur auf markengenehmigte Assets im Content Hub-Portal zugreifen.

* [Content Hub-Benutzer mit Berechtigungen zum Remix von Assets in neue Varianten](#onboard-content-hub-users-remix-assets): [Adobe Express-Integration](/help/assets/edit-images-content-hub.md) (wenn Sie über Adobe Expreß-Berechtigungen verfügen) sowie auf markengenehmigte Assets im Content Hub-Portal zugreifen.

* [Experience Manager Assets-Benutzer](#experience-manager-assets-users): Möglichkeit zur Genehmigung von Assets in Experience Manager Assets as a Cloud Service, um diese Assets in Content Hub verfügbar zu machen.

## Schritt 1: Aktivieren von Content Hub für Experience Manager Assets mithilfe von Cloud Manager {#enable-content-hub}

Um auf das Content Hub-Portal zugreifen zu können, müssen Administratoren zunächst Content Hub für Experience Manager Assets as a Cloud Service mithilfe von Cloud Manager aktivieren. Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Cloud Manager an. Stellen Sie sicher, dass Sie beim Anmelden die richtige Organisation auswählen. Die Cloud Manager listet alle Ihre Programme auf.

1. Navigieren Sie zum Programm Experience Manager Assets as a Cloud Service , klicken Sie auf das Symbol Weitere Optionen (...) und wählen Sie **[!UICONTROL Programm bearbeiten]**.

   ![Programm in Cloud Manager bearbeiten](assets/edit-program-cloud-manager.png)

1. Im [!UICONTROL Programm bearbeiten] wählen Sie das **[!UICONTROL Lösungen und Add-ons]** Registerkarte.

1. Erweitern **[!UICONTROL Assets]** und wählen **[!UICONTROL Content Hub]**.
   ![Content Hub in Cloud Manager auswählen](assets/edit-program-cloud-manager-content-hub.png)

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**.

Content Hub ist jetzt für Experience Manager Assets as a Cloud Service aktiviert.

>[!NOTE]
>
>Sie können auf Content Hub mit bis zu 250 Content Hub-Benutzern zugreifen und es verwenden. Wenden Sie sich bei weiteren Fragen an Ihren Adobe-Support-Mitarbeiter.


Wenn Sie neu bei Experience Manager Assets sind, klicken Sie auf **[!UICONTROL Programm hinzufügen]** und geben Sie dann die Programmdetails an (Programmname, für die Produktion eingerichtet) und klicken Sie auf **[!UICONTROL Weiter]**. Sie können dann **[!UICONTROL Assets]** und **[!UICONTROL Content Hub]** im **[!UICONTROL Lösungen und Add-ons]** Registerkarte.

### Content Hub-Instanz und -Produktprofil auf Admin Console{#content-hub-instance-product-profile}

Nachher [Aktivieren von Content Hub für Assets as a Cloud Service mithilfe von Cloud Manager](#enable-content-hub), gibt es eine neue Instanz, die in der as a Cloud Service Admin Console von AEM Assets mit `contenthub` als Suffix:

![Neue Instanz für Content Hub](assets/new-instance-content-hub.png)

Beachten Sie, dass es keine `author` oder `publish` im Instanznamen für Content Hub.

Klicken Sie auf den Instanznamen, um das Content Hub-Produktprofil anzuzeigen.

![Content Hub-Produktprofil](assets/content-hub-product-profile.png)

## Schritt 2: Integrierter Content Hub-Administrator {#onboard-content-hub-administrator}

Content Hub-Administratoren können auf die [Konfigurationsoberfläche](/help/assets/configure-content-hub-ui-options.md) in Content Hub neben dem Zugriff auf markengenehmigte Assets, dem Hochladen von Assets in Content Hub, der Bildintegration zum Bearbeiten von Adobe Expressen (wenn Sie über Adobe Expreß-Berechtigungen verfügen).

So integrieren Sie den Content Hub-Administrator:

1. [Auf das Content Hub-Benutzerproduktprofil zugreifen und darauf klicken](#content-hub-instance-product-profile).

1. Klicks **[!UICONTROL Benutzer hinzufügen]** , um dem Produktprofil Benutzer oder Benutzergruppen hinzuzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

1. Nachdem Sie den Benutzer zum Content Hub-Produktprofil hinzugefügt haben, greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Produktprofil Administratoren und dann auf **[!UICONTROL Benutzer hinzufügen]** , um den Benutzer zum Produktprofil hinzuzufügen.
   ![Administratorproduktprofil](assets/aem-cs-admin-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

## Schritt 3: Onboard Content Hub-Benutzer {#onboard-content-hub-users}

Content Hub-Benutzer können auf Assets zugreifen, die im Portal verfügbar sind, jedoch keine neuen Assets hinzufügen oder vorhandene Assets ändern.

So integrieren Sie Content Hub-Benutzer:

1. [Auf das Content Hub-Benutzerproduktprofil zugreifen und darauf klicken](#content-hub-instance-product-profile).

1. Klicks **[!UICONTROL Benutzer hinzufügen]** , um dem Produktprofil Benutzer oder Benutzergruppen hinzuzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Diese Benutzer können jetzt auf die im Content Hub-Portal verfügbaren Assets zugreifen.

>[!NOTE]
>
>Sie können alle erweiterten Unternehmensfunktionen wie die Synchronisierung mit externen Identitätsanbietern verwenden.

Nachdem die entsprechenden Benutzer mithilfe von Admin Console hinzugefügt wurden, können sie über den folgenden Link auf Content Hub zugreifen:

`https://experience.adobe.com/#/assets/contenthub`

### E-Mail-Benachrichtigungen für Benutzer deaktivieren {#disable-email-notifications}

Wenn Administratoren E-Mail-Benachrichtigungen deaktivieren müssen, die an Benutzer gesendet werden, wenn sie zum Content Hub-Produktprofil hinzugefügt werden:

Klicken Sie auf das Suchsymbol neben dem Produktprofilnamen und deaktivieren Sie die **[!UICONTROL Benutzer per E-Mail benachrichtigen]** umschalten.

![E-Mail-Benachrichtigungen deaktivieren](assets/disable-email-notifications.png)


## Schritt 4: Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets einbinden (optional) {#onboard-content-hub-users-add-assets}

Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets können [Hochladen neuer markengenehmigter Assets in Content Hub](/help/assets/upload-brand-approved-assets.md).

So integrieren Sie Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Benutzern:

1. [Nach dem Hinzufügen des Benutzers zum Content Hub-Produktprofil](#onboard-content-hub-users), greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Benutzerproduktprofil und dann auf **[!UICONTROL Benutzer hinzufügen]** , um den Benutzer zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-cs-user-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

## Schritt 4: Integrieren von Content Hub-Benutzern mit Berechtigungen zum Neumischen von Assets in neue Varianten (optional) {#onboard-content-hub-users-remix-assets}

Content Hub-Benutzer mit Berechtigungen zum Remix von Assets in neue Varianten können [Ändern vorhandener Assets mit Adobe Express und Speichern des Assets im Repository](/help/assets/edit-images-content-hub.md). Die Bearbeitung von Assets mit Adobe Express ist nur verfügbar, wenn der Benutzer über Adobe Expreß-Berechtigungen verfügt.

So integrieren Sie Content Hub-Benutzer mit Berechtigungen zum Remix von Assets in neue Varianten:

1. [Nach dem Hinzufügen des Benutzers zum Content Hub-Produktprofil](#onboard-content-hub-users), greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Benutzerproduktprofil und dann auf **[!UICONTROL Benutzer hinzufügen]** , um den Benutzer zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-cs-user-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

## Experience Manager Assets-Benutzer {#experience-manager-assets-users}

Experience Manager Assets-Benutzer können Assets in AEM as a Cloud Service genehmigen, damit sie in Content Hub verfügbar sind.

So konfigurieren Sie Experience Manager Assets-Benutzer:

1. Greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktionserstellungsinstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console zeigt zwei Produktprofile für AEM as a Cloud Service an: Administratoren und Benutzer.
1. Klicken Sie auf das Benutzerproduktprofil und dann auf **[!UICONTROL Benutzer hinzufügen]** , um den Benutzer zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-cs-user-product-profile.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

   >[!NOTE]
   >
   > Sie müssen nicht zum [Content Hub-Produktprofil](#onboard-content-hub-users) für die Experience Manager Assets-Benutzer.



