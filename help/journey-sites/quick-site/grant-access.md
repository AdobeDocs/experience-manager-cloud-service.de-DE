---
title: Gewähren des Zugriffs für den Frontend-Entwickler
description: Integrieren Sie die Frontend-Entwickler in Cloud Manager, damit sie Zugriff auf das Git-Repository und die Pipeline der AEM-Site haben.
exl-id: 58e95c92-b859-4bb9-aa62-7766510486fd
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 100%

---

# Gewähren des Zugriffs für den Frontend-Entwickler {#grant-fed-access}

Integrieren Sie die Frontend-Entwickler in Cloud Manager, damit sie Zugriff auf das Git-Repository und die Pipeline der AEM-Site haben.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Tour zu AEM Quick Site Creation, [Einrichten der Pipeline](pipeline-setup.md), haben Sie gelernt, wie Sie eine Frontend-Pipeline erstellen, um die Anpassung des Designs Ihrer Site zu verwalten, und sollten jetzt:

* Wissen, was eine Front-End-Pipeline ist.
* Erfahren Sie, wie Sie eine Frontend-Pipeline in Cloud Manager einrichten.

Sie müssen Ihrem Frontend-Entwickler jetzt über den Onboarding-Prozess Zugriff auf Cloud Manager gewähren, damit der Frontend-Entwickler auf das AEM-Git-Repository und die von Ihnen erstellte Pipeline zugreifen kann.

## Ziel {#objective}

Der Prozess zum Gewähren von Zugriff auf Cloud Manager und zum Zuweisen von Benutzerrollen zu Ihren Benutzern wird als Onboarding bezeichnet. In diesem Dokument erhalten Sie einen Überblick über die wichtigsten Schritte für das Onboarding eines Frontend-Entwicklers. Nach der Lektüre wissen Sie Folgendes:

* Wie ein Front-End-Entwickler als Benutzer hinzugefügt wird.
* Wie dem Front-End-Entwickler die erforderlichen Rollen zugewiesen werden.

>[!TIP]
>
>Es gibt in der Dokumentation eine vollständige Tour, die sich mit dem Onboarding eines Teams in AEM as a Cloud Service beschäftigt. Sie ist im Abschnitt [Zusätzliche Ressourcen](#additional-resources) dieses Dokuments aufgeführt, falls Sie zusätzliche Details zum Prozess benötigen.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Tour gilt für den Cloud Manager-Administrator.

## Voraussetzungen {#requirements}

* Sie müssen Mitglied der Rolle **Geschäftsinhaber** in Cloud Manager sein.
* Sie müssen **Systemadministrator** in Cloud Manager sein.
* Sie müssen Zugriff auf die Admin Console haben.

## Hinzufügen des Frontend-Entwicklers als Benutzer {#add-fed-user}

Zuerst müssen Sie den Frontend-Entwickler mithilfe der Admin Console als Benutzer hinzufügen.

1. Melden Sie sich bei der Admin Console unter [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/) an.

1. Nach der Anmeldung wird eine Übersichtsseite angezeigt, die der folgenden Abbildung ähnelt.

   ![Übersicht in der Admin Console](assets/admin-console.png)

1. Stellen Sie sicher, dass Sie sich in der richtigen Organisation befinden, indem Sie den Organisationsnamen oben rechts auf dem Bildschirm überprüfen.

   ![Organisationsnamen überprüfen](assets/correct-org.png)

1. Wählen Sie **Adobe Experience Manager as a Cloud Service** auf der Karte **Produkte und Dienste** aus.

   ![AEMaaCS auswählen](assets/select-aemaacs.png)

1. Sie sehen die Liste der vorkonfigurierten Cloud Manager-Produktprofile. Wenn diese Profile nicht angezeigt werden, wenden Sie sich an Ihren Cloud Manager-Administrator, da Sie möglicherweise nicht über die richtigen Berechtigungen in Ihrer Organisation verfügen.

   ![Produktprofile](assets/product-profiles.png)

1. Um den Frontend-Entwickler den richtigen Profilen zuzuweisen, tippen oder klicken Sie auf die Registerkarte **Benutzer** und dann auf die Schaltfläche **Benutzer hinzufügen**.

   ![Benutzer hinzufügen](assets/add-user.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den Kennungs-Typ Adobe ID aus, wenn die Federated ID für Ihre Team-Mitglieder noch nicht eingerichtet wurde.

   ![Benutzer zu Team hinzufügen](assets/add-to-team.png)

1. Tippen oder klicken Sie in der Auswahl **Produkt** auf das Pluszeichen und wählen Sie **Adobe Experience Manager as a Cloud Service** aus. Weisen Sie dann dem Benutzer die Produktprofile **Implementierungs-Manager** und **Entwickler** zu.

   ![Teamprofile zuweisen](assets/assign-team.png)

1. Tippen oder klicken Sie auf **Speichern** und eine Begrüßungs-E-Mail wird an den Frontend-Entwickler gesendet, den Sie als Benutzer hinzugefügt haben.

Der eingeladene Frontend-Entwickler kann jetzt auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe seiner Adobe ID anmeldet.

## Übergabe an den Frontend-Entwickler {#handover}

Mit einer E-Mail-Einladung zu Cloud Manager an den Frontend-Entwickler können Sie und der AEM-Administrator dem Frontend-Entwickler jetzt die erforderlichen Informationen bereitstellen, um mit der Anpassung zu beginnen.

* Ein [Pfad zu typischen Inhalten](#example-page)
* Die Design-Quelle, die [Sie heruntergeladen haben](#download-theme)
* Die [Anmeldeinformationen des Proxy-Benutzers](#proxy-user)
* Der Name des Programms oder die URL für das Programm [kopiert aus Cloud Manager](pipeline-setup.md#login)
* Die Anforderungen an das Frontenddesign

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Tour zu AEM Quick Site Creation abgeschlossen haben, sollten Sie:

* Wie ein Front-End-Entwickler als Benutzer hinzugefügt wird.
* Wie dem Front-End-Entwickler die erforderlichen Rollen zugewiesen werden.

Nutzen Sie dieses Wissen und fahren Sie mit der Tour zu AEM Quick Site Creation fort, indem Sie das Dokument [Abrufen von Git-Repository-Zugriffsinformationen](retrieve-access.md) lesen. Hier wird die Perspektive ausschließlich auf den Frontend-Entwickler gelegt und erklärt, wie die Frontend-Entwickler Cloud Manager verwenden, um auf Git-Repository-Informationen zuzugreifen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, mit dem nächsten Teil der Tour zu Quick Site Creation fortzufahren, indem Sie das Dokument [Abrufen von Git-Repository-Zugriffsinformationen](retrieve-access.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Aber sie sind nicht erforderlich, um mit der Tour fortzufahren.

* [Onboarding-Tour](/help/journey-onboarding/home.md) – Dieses Handbuch dient als Ausgangspunkt, um sicherzustellen, dass Ihre Teams eingerichtet sind und Zugriff auf AEM as a Cloud Service haben.
