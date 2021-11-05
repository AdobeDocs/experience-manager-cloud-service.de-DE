---
title: Gewähren des Zugriffs für den Frontend-Entwickler
description: Integrieren Sie die Frontend-Entwickler in Cloud Manager, damit sie Zugriff auf Ihr Git-Repository und Ihre AEM-Pipeline haben.
source-git-commit: 7c70be541e811e1be236763081d5571db4269b7a
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 4%

---


# Gewähren des Zugriffs für den Frontend-Entwickler {#grant-fed-access}

Integrieren Sie die Frontend-Entwickler in Cloud Manager, damit sie Zugriff auf Ihr Git-Repository und Ihre AEM-Pipeline haben.

>[!CAUTION]
>
>Das Tool für die schnelle Site-Erstellung ist derzeit eine technische Vorschau. Sie wird zu Test- und Evaluierungszwecken bereitgestellt und ist nicht zur Verwendung in der Produktion bestimmt, es sei denn, sie wurde mit der Adobe Support vereinbart.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Schnellsite-Journey [Einrichten der Pipeline,](pipeline-setup.md) Sie haben gelernt, wie Sie eine Front-End-Pipeline erstellen, um die Anpassung des Designs Ihrer Site zu verwalten, und sollten jetzt:

* Erfahren Sie, was eine Front-End-Pipeline ist.
* Erfahren Sie, wie Sie eine Front-End-Pipeline in Cloud Manager einrichten.

Sie müssen Ihrem Frontend-Entwickler jetzt über den Integrationsprozess Zugriff auf Cloud Manager gewähren, damit der Frontend-Entwickler auf das AEM Git-Repository und die von Ihnen erstellte Pipeline zugreifen kann.

## Ziel {#objective}

Der Prozess der Gewährung des Zugriffs auf Cloud Manager und der Zuweisung von Benutzerrollen an Ihre Benutzer wird als Onboarding bezeichnet. In diesem Dokument erhalten Sie einen Überblick über die wichtigsten Schritte zum Onboarding eines Frontend-Entwicklers. Nach der Lektüre werden Sie Folgendes wissen:

* So fügen Sie einen Frontend-Entwickler als Benutzer hinzu.
* So gewähren Sie dem Frontend-Entwickler die erforderlichen Rollen.

>[!TIP]
>
>Es gibt eine vollständige Journey zur der Dokumentation, mit der Sie Ihr Team in AEM as a Cloud Service integrieren können. [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources) dieses Dokuments, wenn Sie zusätzliche Details zum Prozess benötigen.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt für den Cloud Manager-Administrator.

## Voraussetzungen {#requirements}

* Sie müssen Mitglied von **Business Owner** Rolle in Cloud Manager.
* Sie müssen ein **Sys Admin** in Cloud Manager.
* Sie müssen Zugriff auf die Admin Console haben.

## Frontend-Entwickler als Benutzer hinzufügen {#add-fed-user}

Zuerst müssen Sie den Frontend-Entwickler mithilfe der Admin Console als Benutzer hinzufügen.

1. Melden Sie sich bei der Admin Console an unter [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).

1. Nach der Anmeldung erhalten Sie eine Übersichtsseite, die dem folgenden Bild ähnelt.

   ![Übersicht über die Admin Console](assets/admin-console.png)

1. Stellen Sie sicher, dass Sie sich in der entsprechenden Organisation befinden, indem Sie den Organisationsnamen in der oberen rechten Ecke des Bildschirms überprüfen.

   ![Überprüfen des Organisationsnamens](assets/correct-org.png)

1. Auswählen **Adobe Experience Manager as a Cloud Service** von **Produkte und Dienstleistungen** Karte.

   ![Auswählen von AEMaaCS](assets/select-aemaacs.png)

1. Sie sehen die Liste der vorkonfigurierten Cloud Manager-Produktprofile. Wenn diese Profile nicht angezeigt werden, wenden Sie sich an Ihren Cloud Manager-Administrator, da Sie möglicherweise nicht über die richtigen Berechtigungen in Ihrer Organisation verfügen.

   ![Produktprofile](assets/product-profiles.png)

1. Um den Frontend-Entwickler den richtigen Profilen zuzuweisen, tippen oder klicken Sie auf die **Benutzer** und dann die **Benutzer hinzufügen** Schaltfläche.

   ![Benutzer hinzufügen](assets/add-user.png)

1. Im **Benutzer zu Ihrem Team hinzufügen** Geben Sie die E-Mail-Adresse des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den Kennungs-Typ Adobe ID aus, wenn die Federated ID für Ihre Team-Mitglieder noch nicht eingerichtet wurde.

   ![Benutzer zu Team hinzufügen](assets/add-to-team.png)

1. Im **Produkt** Auswahl, tippen oder klicken Sie auf das Pluszeichen und wählen Sie **Adobe Experience Manager as a Cloud Service** und weisen Sie die **Bereitstellungsmanager** und **Entwickler** Produktprofile an den Benutzer.

   ![Zuweisen von Teamprofilen](assets/assign-team.png)

1. Tippen oder klicken Sie auf **Speichern** und eine Begrüßungs-E-Mail an den Frontend-Entwickler gesendet wird, den Sie als Benutzer hinzugefügt haben.

Der eingeladene Frontend-Entwickler kann auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe seiner Adobe ID anmeldet.

## Übergabe an Frontend-Entwickler {#handover}

Mit einer E-Mail-Einladung an Cloud Manager auf dem Weg zum Frontend-Entwickler können Sie und der AEM-Administrator jetzt dem Frontend-Entwickler die erforderlichen Informationen bereitstellen, um mit der Anpassung zu beginnen.

* A [Pfad zum typischen Inhalt](#example-page)
* Die Designquelle, die [heruntergeladen haben](#download-theme)
* Die [Anmeldedaten des Proxybenutzers](#proxy-user)
* Der Name des Programms oder die URL für das Programm [aus Cloud Manager kopiert](pipeline-setup.md#login)
* Die Anforderungen an das Frontend-Design

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der Journey zur AEM SchnellSite-Erstellung abgeschlossen haben, sollten Sie Folgendes wissen:

* So fügen Sie einen Frontend-Entwickler als Benutzer hinzu.
* So gewähren Sie dem Frontend-Entwickler die erforderlichen Rollen.

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit der Journey zur AEM SchnellSite-Erstellung fort, indem Sie das Dokument erneut überprüfen. [Git-Repository-Zugriffsinformationen abrufen,](retrieve-access.md) , der die Perspektive ausschließlich auf den Frontend-Entwickler umstellt und erklärt, wie die Frontend-Entwickler-Benutzer von Cloud Manager auf Git-Repository-Informationen zugreifen können.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zur Schnellseitenerstellung zu wechseln, indem Sie das Dokument lesen [Frontend-Entwickleranmeldeinformationen abrufen,](retrieve-access.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [Onboarding-Journey](/help/journey-onboarding/home.md) - Dieses Handbuch dient als Ausgangspunkt, um sicherzustellen, dass Ihre Teams eingerichtet sind und Zugriff auf AEM as a Cloud Service haben.


