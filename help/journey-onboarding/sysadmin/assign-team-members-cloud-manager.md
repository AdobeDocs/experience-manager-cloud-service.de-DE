---
title: Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder den Cloud Manager-Produktprofilen zuordnen können.
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: ht
source-wordcount: '1440'
ht-degree: 100%

---

# Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen {#assign-team-members}

Nachdem Sie gelernt haben, wie Sie sich bei [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=de) anmelden und Ihre Berechtigungen als [Systemadministrator](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/system-administrator.html?lang=de) gesehen haben, können Sie jetzt Team-Mitglieder zu Cloud Manager-Produktprofilen zuweisen.

## Ziel {#objective}

In diesem Dokument wird zusammengefasst, wie Sie von der Adobe Admin Console aus Cloud Manager-Produktprofilen Team-Mitglieder zuweisen.

Nach dem Lesen dieses Abschnitts sollten Sie zu Folgendem in der Lage sein:

* Verstehen, warum und wie Sie Team-Mitglieder hinzufügen müssen.
* Drei verschiedene Cloud Manager-Produktprofile wie Geschäftsinhaber, Implementierungs-Manager und Entwickler kennen.
* Team-Mitglieder den Cloud Manager-Produktprofilen zuweisen, z. B. Geschäftsinhaber, Implementierungs-Manager und Entwickler.

## Voraussetzungen {#prerequisites}

Vor dem Start dieses Abschnitts sollten die folgenden Voraussetzungen berücksichtigt werden. Sie müssen:

* Systemadministrator sein und [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles) verstehen.
* Mit den Grundlagen zur [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=de) vertraut sein.
* Informationen über Ihre Team-Mitglieder haben. Ein Systemadministrator muss über die Namen und E-Mail-Adressen sowie die Rollen und Zuständigkeiten der Team-Mitglieder verfügen, die Zugriff auf AEM as a Cloud Service benötigen.

   >[!NOTE]
   >Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später die Anzahl von Benutzern ausweiten.

## Überprüfen von Cloud Manager-Produktprofilen {#review-product-profiles}

In der Adobe Admin Console wird die Liste der Cloud Manager-Profile angezeigt.

>[!NOTE]
>Bevor Sie die Cloud Manager-Produktprofile von der Admin Console aus überprüfen, sollten Sie die verfügbaren [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles) überprüfen.

Gehen Sie wie folgt vor, um eine Liste der Cloud Manager-Profile anzuzeigen:

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) an. Wählen Sie auf der Seite **Überblick** die Option **Adobe Experience Manager as a Cloud Service** aus der Karte **Produkte und Services**.

   ![](/help/journey-onboarding/assets/assign-team1.png)

   >[!NOTE]
   >Informationen zur Verwendung der Admin Console finden Sie unter „Anmelden bei der Admin Console“.


1. Gehen Sie in der Liste aller Instanzen zur Instanz **Cloud Manager**.

   ![](/help/journey-onboarding/assets/assign-team2.png)

1. Sie sehen die Liste der vorkonfigurierten [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles).

   ![](/help/journey-onboarding/assets/assign-team3.png)


## Zuweisen von Benutzern zum Produktprofil „Geschäftsinhaber“ {#assign-users-business-owner}

Sie können jetzt Benutzer hinzufügen und sie dem Cloud Manager-Produktprofil „Geschäftsinhaber“ zuweisen.

>[!NOTE]
>Um dies erfolgreich zu tun, müssen Sie in der Adobe Admin Console einen Benutzer zum Produkt (hier AEM as a Cloud Service) und zum Produktprofil [Cloud Manager-Geschäftsinhaber](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles) hinzufügen.

Die folgenden Schritte führen Sie durch diesen Prozess:

1. Ermitteln Sie den/die Benutzer, der/die Cloud Manager-Programme verwalten wird/werden, und fügen Sie ihn/sie dem Produktprofil „Geschäftsinhaber“ hinzu. Der Systemadministrator muss die erste Person sein, die auf Cloud Manager zugreift und sich dort anmeldet. Sie müssen sich selbst (Systemadministrator) zuerst zum Produktprofil „Geschäftsinhaber“ hinzufügen.

1. Wählen Sie in der [Admin Console](https://adminconsole.adobe.com/enterprise/overview) auf der Seite **Überblick** die Option **Adobe Experience Manager as a Cloud Service** aus der Karte **Produkte und Services** aus, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zu Ihrem Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den Kennungs-Typ Adobe ID aus, wenn die Federated ID für Ihre Team-Mitglieder noch nicht eingerichtet wurde.

   ![](/help/journey-onboarding/assets/assign-team5.png)

1. Wählen Sie in der Produktauswahl **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Geschäftsinhaber** wie unten dargestellt zu.

   >[!NOTE]
   >Lesen Sie [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles), um sicherzustellen, dass in der Admin Console den richtigen Benutzern die richtigen Rollen zugewiesen werden, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/assign-team6.png)

   >[!NOTE]
   >Weisen Sie den Benutzer mindestens einem Produktprofil zu, damit der Benutzer auf Cloud Manager zugreifen kann. Denken Sie daran, sich selbst (Systemadministrator) der Rolle „Geschäftsinhaber“ zuzuweisen.

1. Klicken Sie auf **Speichern**. Der hinzugefügte Benutzer erhält eine Begrüßungs-E-Mail. Er kann jetzt auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe einer Adobe ID anmeldet.

   Herzlichen Glückwunsch! Jetzt wurde Ihr neu zusammengestelltes Cloud Manager-Team eingerichtet, das auch die Rolle „Business Owner“ beinhaltet. Mitglieder erhalten eine Begrüßungs-E-Mail, in der sie zur Anmeldung und zum Zugriff auf Cloud Manager eingeladen werden. In der Rolle des Geschäftsinhabers sind Sie jetzt nur noch einen Schritt davon entfernt, sich bei Cloud Manager anzumelden und die Erstellung Ihrer Cloud-Ressourcen zu ermöglichen.

## Zuweisen von Benutzern zum Produktprofil „Implementierungs-Manager“ {#assign-users-deployment-manager}

1. Ermitteln Sie die Benutzer, die Cloud Manager-Programme verwalten sollen, und fügen Sie sie zum Produktprofil „Implementierungs-Manager“ hinzu. Der Systemadministrator muss die erste Person sein, die auf Cloud Manager zugreift und sich dort anmeldet. Sie müssen sich selbst (Systemadministrator) zuerst zum Produktprofil „Business Owner“ hinzufügen (wie im vorherigen Abschnitt beschrieben).

1. Wählen Sie in der [Admin Console](https://adminconsole.adobe.com/enterprise/overview) auf der Seite **Überblick** die Option **Adobe Experience Manager as a Cloud Service** aus der Karte **Produkte und Services** aus, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zu Ihrem Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den Kennungs-Typ Adobe ID aus, wenn die Federated ID für Ihre Team-Mitglieder noch nicht eingerichtet wurde.

   ![](/help/journey-onboarding/assets/assign-team5.png)

1. Wählen Sie in der Produktauswahl **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Implementierungs-Manager** wie unten gezeigt zu.

   >[!NOTE]
   >Lesen Sie [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles), um sicherzustellen, dass in der Admin Console den richtigen Benutzern die richtigen Rollen zugewiesen werden, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/assign-team6.png).

   >[!IMPORTANT]
   >Benutzer können zum Produktprofil „Implementierungs-Manager“ hinzugefügt werden, nachdem Cloud Manager-Ressourcen erstellt wurden.

## Zuweisen von Benutzern zum Produktprofil „Entwickler“ {#assign-users-developer}

1. Ermitteln Sie die Benutzer, die Cloud Manager-Programme verwalten sollen, und fügen Sie sie zum Produktprofil „Entwickler“ hinzu. Der Systemadministrator muss die erste Person sein, die auf Cloud Manager zugreift und sich dort anmeldet. Sie müssen sich selbst (Systemadministrator) zuerst zum Produktprofil „Geschäftsinhaber“ hinzufügen.

1. Wählen Sie in der [Admin Console](https://adminconsole.adobe.com/enterprise/overview) auf der Seite **Überblick** die Option **Adobe Experience Manager as a Cloud Service** aus der Karte **Produkte und Services** aus, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zu Ihrem Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den Kennungs-Typ Adobe ID aus, wenn die Federated ID für Ihre Team-Mitglieder noch nicht eingerichtet wurde.

   >[!NOTE]
   >Weitere Informationen zu Identitätstypen in der Adobe Admin Console finden Sie unter [Überblick über Identitäten](https://helpx.adobe.com/de/enterprise/using/identity.html).

   ![](/help/journey-onboarding/assets/assign-team5.png)

1. Wählen Sie in der Produktauswahl **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Entwickler** wie unten gezeigt zu.

   >[!NOTE]
   >Lesen Sie [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles), um sicherzustellen, dass in der Admin Console den richtigen Benutzern die richtigen Rollen zugewiesen werden, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/assign-team6.png).


   >[!IMPORTANT]
   >Benutzer können zum Produktprofil „Entwickler“ hinzugefügt werden, nachdem Cloud Manager-Ressourcen erstellt wurden.

## Wie geht es weiter? {#whats-next}

Sie haben drei verschiedene Cloud Manager-Produktprofile wie „Business Owner“, „Implementierungs-Manager“ und „Entwickler“ kennengelernt. Als Nächstes haben Sie Teammitglieder den Cloud Manager-Produktprofilen zugewiesen, z. B. „Business Owner“, „Implementierungs-Manager“ und „Entwickler“. Sie sind nun bereit, mit der Onboarding-Tour fortzufahren, indem Sie als Nächstes das Dok [ument Einrichten von Cloud-Ressourcen über Cloud Manager](/help/journey-onboarding/sysadmin/setup-cloud-resources-via-cloud-manager.md) lesen, in dem Sie mehr über Folgendes erfahren:

1. Als Systemadministrator, der der Rolle *Geschäftsinhaber* zugewiesen ist, müssen Sie auf Cloud Manager zugreifen und sich dort anmelden.

1. Als Nächstes kann sich ein Cloud Manager-Benutzer mit der Rolle *Geschäftsinhaber* anmelden und Ihre Cloud-Ressourcen einschließlich Ihres Cloud-Programms und Ihrer Umgebungen einrichten. Dadurch wird sichergestellt, dass Ihr Experten-Team so bald wie möglich auf AEM as a Cloud Service zugreifen kann.

1. Nachdem Ihr *Geschäftsinhaber* Ihre Cloud-Ressourcen eingerichtet hat, können *Entwickler* und *Implementierungs-Manager*, die den Cloud Manager-Produktprofilen erfolgreich hinzugefügt wurden, auf Cloud Manager zugreifen und sich selbst darauf vorbereiten, wie sie ihren Lernpfad fortsetzen können.

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=de)
* [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles)
* [Identitätsüberblick für die Admin Console](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
