---
title: Aktivieren von Assets Ultimate
description: Erfahren Sie, wie Sie Assets Ultimate für neue und bestehende Kundschaft aktivieren.
feature: Asset Management
role: User, Admin
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 45cd8ccd-e5cf-42cd-aa7f-4ae59d0587f7
source-git-commit: e8d9414c204222cbd1068530cc9329f30c7a9fbe
workflow-type: tm+mt
source-wordcount: '2539'
ht-degree: 55%

---

# Aktivieren von [!DNL Assets] as a Cloud Service Ultimate {#enable-assets-cloud-service-ultimate}

![Aktualisierung auf Asset Cloud Service Ultimate](/help/assets/assets/upgrade-assets-cs-ultimate-package-banner.png)

Mit Assets as a Cloud Service Ultimate können Sie verschiedene wichtige DAM-Funktionen nutzen, z. B. Asset-Management und Bibliotheksdienste, Sicherheit und Rights Management, Creative und Experience Cloud-Verbindungen, Erweiterbarkeit der Benutzeroberfläche, API-gesteuerte Automatisierung, Integrationen in Adobe- und Adobe-fremde Anwendungen oder die Bereitstellung von benutzerdefiniertem Code. Die vollständige Liste finden Sie unter [Überblick über Assets as a Cloud Service Ultimate](/help/assets/assets-ultimate-overview.md).

## Aktivieren von Assets Ultimate {#enable-assets-ultimate}

Neue Kundinnen und Kunden von Assets as a Cloud Service müssen zunächst Assets Ultimate aktivieren, indem sie mit Cloud Manager ein neues Programm erstellen.

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich als Systemadmin bei Cloud Manager an. Stellen Sie sicher, dass Sie beim Anmelden die richtige Organisation auswählen.

   >[!NOTE]
   >
   >Achten Sie darauf, dass Sie zum richtigen Cloud Manager-Produktprofil hinzugefügt wurden, um ein neues Programm hinzuzufügen. Weitere Informationen finden Sie unter [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

1. [Erstellen Sie ein neues Programm](/help/journey-onboarding/create-program.md) und [fügen Sie ihm Umgebungen hinzu](/help/journey-onboarding//create-environments.md).

   Wählen Sie beim Erstellen des neuen Programms auf der Registerkarte **[!UICONTROL Lösungen und Add-ons]** die Option **[!UICONTROL Assets Ultimate]** aus. Sie können auch **[!UICONTROL Assets Ultimate]** erweitern und **[!UICONTROL Content Hub]** auswählen, um [Content Hub](/help/assets/product-overview.md) für die Asset-Verteilung zu aktivieren.

   ![AEM Assets Ultimate](assets/aem-assets-ultimate-solutions.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**, um das Programm zu erstellen. Assets Ultimate ist jetzt für Experience Manager Assets as a Cloud Service aktiviert.

Die Systemadmins sind automatisch berechtigte AEM-Admins für Assets Ultimate und erhalten eine E-Mail, um für das Verwalten von Produktprofilen zur Admin Console zu navigieren.

Ihre Instanz von AEM as a Cloud Service in der Admin Console umfasst die folgenden Produktprofile:

* AEM-Admins

* AEM-Benutzende

* [AEM Assets-Mitarbeiter-Benutzende](#onboard-collaborator-users)

* [AEM Assets-Power-Benutzende](#onboard-power-users)

  ![AEM Assets-Produktprofile](assets/aem-assets-product-profiles.png)

Wenn Sie Content Hub für Assets as a Cloud Service aktiviert haben, wird in AEM Assets as a Cloud Service eine neue Instanz für die Admin Console mit dem Suffix `delivery` erstellt:

![Neue Instanz für Content Hub](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Wenn Sie Content Hub vor dem 14. August 2024 bereitgestellt haben, wird die neue Instanz mit `contenthub` als Suffix erstellt.

Beachten Sie, dass der Instanzname für Content Hub weder `author` noch `publish` enthält.

Klicken Sie auf den Instanznamen, um das Content Hub-Produktprofil `AEM Assets Limited Users` anzuzeigen.

![Content Hub-Produktprofil](assets/content-hub-product-profile.png)

Sie können diesem Produktprofil Benutzende oder Benutzergruppen hinzufügen, um ihnen Zugriff auf Content Hub zu gewähren.

>[!NOTE]
>
>Wenn Sie Content Hub vor dem 14. August 2024 bereitgestellt haben, wird für das Content Hub-Produktprofil nach `Limited Users` anstelle von `delivery` `contenthub` angegeben.

## Aktivieren von Assets Ultimate für bestehende Kundschaft {#enable-assets-ultimate-existing-customers}

Bestehende Kundinnen und Kunden von Assets as a Cloud Service können eine Aktualisierung auf Assets Ultimate durchführen, indem sie zwei einfache Schritte ausführen. Sie können zum Assets as a Cloud Service-Programm in Cloud Manager navigieren und sich den Aktualisierungsstatus basierend auf der Verfügbarkeit von Assets Ultimate-Credits auf der Programmkarte ansehen. Wenn ausreichend Credits für die Aktualisierung auf Assets Ultimate verfügbar sind, wird Ihnen als Status `Assets license upgrade required` angezeigt, wie in der folgenden Abbildung dargestellt:

![AEM Assets-Aktualisierung auf Assets Ultimate](assets/aem-assets-upgrade-status-ultimate.png)

Wenn eine Bestandskundin oder ein Bestandskunde eine neue Lizenz für Assets Ultimate erwirbt, wird als Aktualisierungsstatus `Assets license upgrade available` angezeigt.

### Voraussetzungen für die Aktualisierung {#prerequisites-assets-upgrade}

Alle Umgebungen müssen auf die neueste Release-Version von AEM as a Cloud Service oder zumindest auf die Release-Version `2024.10.18175` aktualisiert sein. Wenn Sie die Mindestanforderungen nicht erfüllen, wenden Sie sich an den Adobe-Support, um zur gewünschten AEM-Release-Version zu wechseln.

### Auf Assets Ultimate aktualisieren {#upgrade-assets-ultimate}

Führen Sie die folgenden Schritte aus:

1. Nachdem Sie zu den Mindestanforderungen für die AEM-Release-Version gewechselt haben, klicken Sie auf den Namen des Programms. Eine Aktualisierungskarte wird direkt über dem Abschnitt **[!UICONTROL Umgebungen]** angezeigt, wie in der folgenden Abbildung dargestellt:

   ![AEM Assets-Aktualisierung auf Assets Ultimate](assets/aem-assets-upgrade-card.png)

1. Klicken Sie auf **[!UICONTROL Produktprofile hinzufügen]**. Cloud Manager zeigt Optionen zum Hinzufügen neuer Produktprofile zu allen im Programm verfügbaren Umgebungen oder zu individuellen Umgebungen an.

   ![Optionen für die AEM Assets-Aktualisierung](assets/aem-assets-upgrade-options.png)

1. Klicken Sie auf **[!UICONTROL Alle Umgebungen]**, um die neuen Produktprofile zu allen Umgebungen im Programm hinzuzufügen, oder auf **[!UICONTROL Individuelle Umgebungen]**, um die neuen Produktprofile zu ausgewählten Umgebungen hinzuzufügen.

   Durch Klicken auf **[!UICONTROL Individuelle Umgebungen]** wird die Liste aller im Programm verfügbaren Umgebungen angezeigt.

1. Klicken Sie auf das zu einer Umgebung gehörende Symbol „Weitere Optionen“, und wählen Sie **[!UICONTROL Produktprofile hinzufügen]** aus, um die neuen Produktprofile zur ausgewählten Umgebung hinzuzufügen.

   ![AEM Assets – Auswählen einzelner Umgebungen](assets/aem-assets-individual-environments.png)

   Sie können Produktprofile auch zu ausgewählten Umgebungen hinzufügen, indem Sie zum Abschnitt **[!UICONTROL Umgebungen]** navigieren, auf das zu einer Umgebung gehörende Symbol „Weitere Optionen“ klicken und **[!UICONTROL Produktprofile hinzufügen]** auswählen.

   Während die neuen Produktprofile hinzugefügt werden, wird als Status der Umgebung `Adding Product Profiles` angezeigt. Nach Abschluss des Vorgangs wird dann `Running` angezeigt.

   Bevor Sie den nächsten Schritt ausführen können, müssen Sie zu allen im Programm verfügbaren Umgebungen Produktprofile hinzufügen. Sie können dies für individuelle Umgebungen oder für alle Umgebungen zusammen tun.

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**. Die Option **[!UICONTROL Aktualisieren]** wird erst angezeigt, wenn Sie allen verfügbaren Umgebungen Produktprofile hinzufügen.

   ![Letzter Schritt im Aktualisierungsprozess](assets/aem-assets-upgrade-button.png)

   Der Aktualisierungsprozess ist abgeschlossen und Sie haben Assets as a Cloud Service erfolgreich auf Assets Ultimate aktualisiert. Als Status des Programms wird `Assets Ultimate` angezeigt.

   ![Programmstatus nach der Aktualisierung](assets/program-status-post-upgrade.png)

Ihre Instanz von AEM as a Cloud Service in der Admin Console umfasst jetzt die folgenden Produktprofile:

* AEM-Admins

* AEM-Benutzende

* [AEM Assets-Mitarbeiter-Benutzende](#onboard-collaborator-users)

* [AEM Assets-Power-Benutzende](#onboard-power-users)

![AEM Assets-Produktprofile](assets/aem-assets-product-profiles.png)

Wenn Content Hub aktiviert sein muss, klicken Sie auf Weitere Optionen (…) auf dem Programmnamen in Cloud Manager und wählen Sie **[!UICONTROL Programm bearbeiten]**. Erweitern Sie **[!UICONTROL Assets Ultimate]** und klicken Sie auf **[!UICONTROL Content Hub]**. Dieser Schritt aktiviert den Content Hub für Assets Ultimate. Es wird eine neue Instanz in AEM Assets as a Cloud Service für die Admin Console mit dem Suffix `delivery` erstellt:

![Neue Instanz für Content Hub](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Wenn Sie Content Hub vor dem 14. August 2024 bereitgestellt haben, wird die neue Instanz mit `contenthub` als Suffix erstellt.

Beachten Sie, dass der Instanzname für Content Hub weder `author` noch `publish` enthält.

Klicken Sie auf den Instanznamen, um das Content Hub-Produktprofil `AEM Assets Limited Users` anzuzeigen.

![Content Hub-Produktprofil](assets/content-hub-product-profile.png)

Sie können diesem Produktprofil Benutzende oder Benutzergruppen hinzufügen, um ihnen Zugriff auf Content Hub zu gewähren.

>[!NOTE]
>
>Wenn Sie Content Hub vor dem 14. August 2024 bereitgestellt haben, wird für das Content Hub-Produktprofil nach `Limited Users` anstelle von `delivery` `contenthub` angegeben.

## Onboarding von AEM Assets-Mitarbeiter-Benutzenden {#onboard-collaborator-users}

AEM Assets-Mitarbeiter-Benutzende können mit Assets aus Experience Manager über Integrationen von Assets arbeiten, die für Ihr Unternehmen in anderen Adobe-Produkten und Adobe-fremden Anwendungen zur Verfügung stehen, Assets mit dem integrierten Adobe Express und Firefly erstellen und bearbeiten, indem sie professionell entwickelte Vorlagen, Marken-Kits und Adobe Stock-Assets nutzen und mithilfe des AEM Assets Content Hub-Portals auf genehmigte Assets in Ihrem Unternehmen zugreifen und diese nutzen.

So führen Sie das Onboarding von Mitarbeiter-Benutzenden durch:

1. Greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste in der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktions-Autoreninstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

1. Klicken Sie auf das Produktprofil „Mitarbeiter-Benutzende“ und klicken Sie auf **[!UICONTROL Benutzende hinzufügen]**, um Benutzende oder Benutzergruppen zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-assets-collaborator-user-permissions.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Sie können auch auf die den Mitarbeiter-Benutzenden zugewiesenen Dienste zugreifen und diese anzeigen, wie in der folgenden Abbildung dargestellt:

![Dienste für Mitarbeiter-Benutzende](assets/aem-assets-collaborator-users.png)

Die Dienste `Adobe Express` und `AEM Assets Collaborator Users` sind standardmäßig aktiviert.

>[!NOTE]
>
>Sie können mit den Umschaltern die verfügbaren Dienste entsprechend Ihren Anforderungen aktivieren oder deaktivieren. Adobe empfiehlt jedoch, die standardmäßig für die Produktprofile aktivierten Dienste beizubehalten.


## Onboarding von AEM Assets Power-Benutzenden {#onboard-power-users}

AEM Assets-Power-Benutzende können auf alle AEM Assets-Funktionen zugreifen, einschließlich dem Verwalten von Assets, Berechtigungen, Metadaten und der allgemeinen Governance und Automatisierung von digitalen Assets. Sie können mit Assets aus Experience Manager über Integrationen von Assets arbeiten, die für Ihr Unternehmen in anderen Adobe-Produkten und Adobe-fremden Anwendungen zur Verfügung stehen, Assets mit dem integrierten Adobe Express und Firefly erstellen und bearbeiten, indem sie professionell entwickelte Vorlagen, Marken-Kits und Adobe Stock-Assets nutzen und mithilfe des AEM Assets Content Hub-Portals auf genehmigte Assets in Ihrem Unternehmen zugreifen und diese nutzen.

So führen Sie das Onboarding von Power-Benutzenden durch:

1. Greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste in der Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Klicken Sie auf die Produktions-Autoreninstanz für AEM as a Cloud Service:
   ![Produktprofile für AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

1. Klicken Sie auf das Produktprofil „Power-Benutzende“ und dann auf **[!UICONTROL Benutzende hinzufügen]**, um Benutzende oder Benutzergruppen zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-assets-power-user-permissions.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Sie können auch auf die den Power-Benutzenden zugewiesenen Dienste zugreifen und diese anzeigen, wie in der folgenden Abbildung dargestellt:

![Dienste für Power-Benutzende](assets/aem-assets-power-users.png)

Die Dienste `Adobe Express` und `AEM Assets Power Users` sind standardmäßig aktiviert.

>[!NOTE]
>
>Sie können mit den Umschaltern die verfügbaren Dienste entsprechend Ihren Anforderungen aktivieren oder deaktivieren. Adobe empfiehlt jedoch, die standardmäßig für die Produktprofile aktivierten Dienste beizubehalten.

## Häufig gestellte Fragen {#frequently-asked-questions-enable-assets-ultimate}

### Wie aktivieren neue Kunden AEM Assets Ultimate? {#enable-assets-ultimate-new-customers}

Neue AEM Assets as a Cloud Service-Kunden aktivieren Assets Ultimate, indem sie ein neues Programm in Cloud Manager erstellen. Melden Sie sich bei Cloud Manager als Systemadministrator an, erstellen Sie ein neues Programm und wählen Sie auf der Registerkarte Lösungen und Add-ons die Option Assets Ultimate aus. Erweitern Sie optional Assets Ultimate und wählen Sie Content Hub aus, um die Asset-Verteilung zu aktivieren. Klicken Sie auf Erstellen , um die Programmeinrichtung abzuschließen. Assets Ultimate wird dann für die AEM Assets as a Cloud Service-Instanz aktiviert und der Systemadministrator erhält eine E-Mail zur Verwaltung von Produktprofilen in Admin Console.

### Kann Content Hub für neue Kunden gleichzeitig mit AEM Assets Ultimate aktiviert werden? {#enable-content-hub-new-customers}

Content Hub kann während der Ersteinrichtung des Assets Ultimate-Programms in Cloud Manager aktiviert werden. Wählen Sie beim Erstellen des neuen Programms Assets Ultimate auf der Registerkarte Lösungen und Add-ons aus, erweitern Sie die Option Assets Ultimate und wählen Sie Content Hub aus. Durch Abschluss der Programmerstellung können Assets Ultimate und Content Hub gleichzeitig aktiviert werden. In Admin Console wird eine neue Instanz mit dem Versand-Suffix erstellt, die das Content Hub-Produktprofil AEM Assets Eingeschränkte Benutzer enthält, mit dem Benutzenden Zugriff auf Content Hub gewährt wird.

### Welche Produktprofile sind nach der Aktivierung von AEM Assets Ultimate in Admin Console verfügbar? {#product-profiles-assets-ultimate}

Nach der Aktivierung von AEM Assets Ultimate umfasst die AEM as a Cloud Service-Instanz in Adobe Admin Console vier Produktprofile: AEM-Administratoren, AEM-Benutzer, AEM Assets-Mitwirkende und AEM Assets-Hauptbenutzer. Wenn auch Content Hub aktiviert ist, wird in Admin Console eine separate Versandinstanz erstellt, die das Produktprofil AEM Assets Eingeschränkte Benutzer enthält. Benutzende und Benutzergruppen werden jedem Produktprofil hinzugefügt, um die entsprechende Zugriffsebene innerhalb von AEM Assets Ultimate zu gewähren.

### Was sind die Voraussetzungen für Bestandskunden, ein Upgrade auf AEM Assets Ultimate durchzuführen? {#upgrade-assets-ultimate-prerequisites}

Bestehende AEM Assets as a Cloud Service-Kunden müssen sicherstellen, dass in allen Umgebungen die neueste AEM as a Cloud Service-Version oder mindestens die Version 2024.10.18175 ausgeführt wird, bevor sie ein Upgrade auf Assets Ultimate durchführen. Wenn die Mindestanforderung an die Versionsnummer nicht erfüllt wird, wenden Sie sich an den Adobe-Support-Mitarbeiter, um zur erforderlichen AEM-Versionsnummer zu wechseln, bevor Sie mit dem Upgrade fortfahren.

### Wie können Bestandskunden überprüfen, ob sie für ein Upgrade auf AEM Assets Ultimate berechtigt sind? {#check-upgrade-eligibility-assets-ultimate}

Bestehende AEM Assets as a Cloud Service-Kunden können die Upgrade-Eignung überprüfen, indem sie zum Assets as a Cloud Service-Programm in Cloud Manager navigieren und den Status auf der Programmkarte anzeigen. Wenn ausreichend Assets Ultimate-Credits verfügbar sind, wird der Status als &quot;Assets-Lizenzaktualisierung erforderlich“ angezeigt. Wenn eine neue Lizenz für Assets Ultimate erworben wurde, wird der Status als &quot;Assets License Upgrade Available“ (-Lizenzaktualisierung verfügbar) angezeigt. Beide Status geben an, dass der Aktualisierungspfad für das Programm verfügbar ist.

### Wie führen Bestandskunden ein Upgrade auf AEM Assets Ultimate durch? {#upgrade-steps-assets-ultimate}

Nachdem Sie die Mindestanforderung an die AEM-Versionsversion erfüllt haben, klicken Sie in Cloud Manager auf den Programmnamen, um die Karte Upgrade über dem Abschnitt Umgebungen anzuzeigen. Klicken Sie auf Produktprofile hinzufügen und wählen Sie das Hinzufügen neuer Produktprofile zu allen Umgebungen oder zu einzelnen Umgebungen aus. Produktprofile müssen allen verfügbaren Umgebungen hinzugefügt werden, bevor Sie fortfahren. Sobald alle Umgebungen den Status „Wird ausgeführt“ aufweisen, klicken Sie auf Upgrade , um den Vorgang abzuschließen. Der Programmstatus wird auf Assets Ultimate aktualisiert und bestätigt, dass das Upgrade abgeschlossen ist.

### Wie aktiviere ich Content Hub nach dem Upgrade eines bestehenden Programms auf AEM Assets Ultimate? {#enable-content-hub-existing-customers}

Nachdem Sie ein vorhandenes Programm in Cloud Manager auf AEM Assets Ultimate aktualisiert haben, klicken Sie auf das Symbol Weitere Optionen im Programmnamen und wählen Sie Programm bearbeiten aus. Erweitern Sie Assets Ultimate und klicken Sie auf Content Hub , um es zu aktivieren. In Adobe Admin Console wird eine neue Versandinstanz erstellt, die das Content Hub-Produktprofil AEM Assets Eingeschränkte Benutzende enthält. Benutzende und Benutzergruppen können dann zu diesem Produktprofil hinzugefügt werden, um Zugriff auf das Content Hub-Portal zu gewähren.

### Wie integriere ich Mitarbeiter-Benutzer in AEM Assets Ultimate? {#onboard-collaborator-users-aem-assets}

Um Mitarbeiter in AEM Assets Ultimate zu integrieren, rufen Sie Adobe Admin Console auf und klicken Sie auf den AEM as a Cloud Service-Produktnamen in der Produktliste. Klicken Sie auf die Produktionsautoreninstanz, wählen Sie das Produktprofil AEM Assets Collaborator-Benutzer aus und klicken Sie auf Benutzer hinzufügen , um Benutzer oder Benutzergruppen hinzuzufügen. Klicken Sie auf Speichern , um die Änderungen anzuwenden. Die Benutzerdienste für Adobe Express und AEM Assets Collaborator sind standardmäßig für dieses Produktprofil aktiviert und können bei Bedarf ein- oder ausgeschaltet werden. Adobe empfiehlt, die Standarddienstkonfiguration beizubehalten.

### Welche Services sind für AEM Assets Collaborator-Benutzer standardmäßig aktiviert? {#collaborator-user-default-services}

Für das Produktprofil AEM Assets Collaborator Users in Adobe Admin Console sind standardmäßig zwei Services aktiviert: Adobe Express und AEM Assets Collaborator Users. Diese Services bieten Mitwirkenden Zugriff auf die Erstellung und Bearbeitung von Assets mit Adobe Express und Firefly, Integrationen mit Adobe und Nicht-Adobe-Anwendungen sowie genehmigten Asset-Zugriff über das AEM Assets Content Hub-Portal. Einzelne Services können in Admin Console aktiviert oder deaktiviert werden. Adobe empfiehlt jedoch die Verwendung der Standardkonfiguration.

### Wie integriere ich Power Users in AEM Assets Ultimate? {#onboard-power-users-aem-assets}

Um Power Users in AEM Assets Ultimate zu integrieren, rufen Sie Adobe Admin Console auf und klicken Sie auf den AEM as a Cloud Service Produktnamen in der Liste der Produkte. Klicken Sie auf die Produktionsautoreninstanz, wählen Sie das Produktprofil AEM Assets Power Users aus und klicken Sie auf Add Users (Benutzer hinzufügen), um Anwender oder Benutzergruppen hinzuzufügen. Klicken Sie auf Speichern , um die Änderungen anzuwenden. Adobe Express und AEM Assets Power Users Services sind standardmäßig für dieses Produktprofil aktiviert und können ein- oder ausgeschaltet werden. Adobe empfiehlt, die standardmäßige Service-Konfiguration beizubehalten.

### Welche Services sind für AEM Assets Power Users standardmäßig aktiviert? {#power-user-default-services}

Für das AEM Assets Power Users-Produktprofil in Adobe Admin Console sind standardmäßig zwei Services aktiviert: Adobe Express und AEM Assets Power Users. Diese Services bieten Power-Benutzern vollen Zugriff auf AEM Assets DAM-Funktionen, einschließlich Asset-Management, Metadaten-Governance, Berechtigungen und Automatisierung sowie Adobe Express- und Firefly-gestützter Inhaltserstellung, Integrationen mit Adobe- und Nicht-Adobe-Anwendungen und Zugriff auf das AEM Assets Content Hub-Portal. Einzelne Services können in Admin Console aktiviert oder deaktiviert werden. Adobe empfiehlt jedoch die Verwendung der Standardkonfiguration.

### Was ist der Unterschied zwischen dem Versand und dem ContentHub-Suffix in der Content Hub Admin Console-Instanz? {#content-hub-suffix-difference}

Das Suffix der Content Hub-Instanz in Adobe Admin Console hängt davon ab, wann Content Hub bereitgestellt wurde. Kunden, die Content Hub nach dem 14. August 2024 bereitgestellt haben, haben eine -Instanz mit einem Versand-Suffix. Kunden, die Content Hub vor dem 14. August 2024 bereitgestellt haben, haben eine -Instanz mit einem ContentHub-Suffix. Im früheren Bereitstellungsfall zeigt das Content Hub-Produktprofil auch „ContentHub“ nach Eingeschränkten Benutzenden anstelle von „Bereitstellung“ an. Beide Konfigurationen bieten dasselbe Produktprofil für eingeschränkte AEM Assets-Benutzer, um Zugriff auf Content Hub zu gewähren.
