---
title: Zugang zur Admin Console
description: Sobald Sie mit den erforderlichen Vorbereitungsschritten für das Onboarding und die Grundlagen der AEM as a Cloud Service-Struktur vertraut sind, können Sie sich erstmals bei der Admin Console anmelden.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 8ed13eb6f476bab07da07549a83ab9ac16bdea72
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 55%

---

# Zugang zur Admin Console {#accessing-admin-console}

In diesem Teil der [Onboarding-Tour](overview.md) erfahren Sie mehr über die erforderlichen Vorbereitungsmaßnahmen, bevor Sie sich erstmals in das System einloggen können.

## Ziel {#objective}

Nachdem Sie nun den Artikel zur [Terminologie von AEM as a Cloud Service](terminology.md) gelesen haben und die Grundlagen der AEMaaCS-Struktur kennen, sind Sie bereit, sich zum ersten Mal bei der Admin Console anzumelden!

Als System-Admin sind Sie für die Benutzerverwaltung innerhalb Ihres Unternehmens mithilfe der Admin Console verantwortlich. Nach dem Lesen dieses Abschnitts sollten Sie Folgendes können:

* Sie verstehen, was eine Adobe ID ist.
* Möglichkeit zur Anmeldung bei der Admin Console.
* Erfahren Sie, wie Sie Ihre Berechtigungen als Systemadministrator mit der Admin Console überprüfen können.
* Sie wissen, wie Sie den Adobe-Support um Hilfe bitten können.

## Über die Admin Console {#admin-console}

Die Adobe Admin Console ist ein zentraler Ort, um Ihre Adobe-Produktlizenzen und Benutzende zu verwalten. Mit der Admin Console können Sie Benutzende an einem zentralen Ort anstatt in jeder einzelnen Lösung erstellen und verwalten.

### Adobe ID {#adobe-id}

Um sich bei der Admin Console anzumelden, benötigen Sie eine Adobe ID. Ein Adobe ID ist ein Konto, das an eine bestimmte E-Mail-Adresse gebunden ist. Dieses Konto ist für die Anmeldung und den Zugriff auf AEM as a Cloud Service oder eine Ihrer Adobe-Lösungen erforderlich. Durch die Verwendung Ihrer Adobe ID bleiben alle Ihre Adobe-Pläne und -Produkte mit einem einzigen Konto verknüpft.

Wenn Sie als System-Admin Ihr Team in der Admin Console einrichten, geben Sie die E-Mail-Adresse an, die als Adobe ID verwendet wird.

Es gibt drei Arten von Adobe IDs:

* **Persönliche ID**: Der Standardtyp von Adobe ID und wird unter adobe.com erstellt. Verwaltet von Adobe und jeder kann ein solches Konto erstellen.

* **Enterprise ID**: Unternehmen wünschen in der Regel mehr Kontrolle über Benutzerkonten. Nur System-Admins können Enterprise IDs erstellen, wobei die Organisation Eigentümerin dieser Konten ist und Adobe nur als Host dient.

* **Federated ID**: Mit Federated IDs übernimmt das Unternehmen die volle Verantwortung und Kontrolle über seine Konten. Ihr Unternehmen muss die Adobe Experience Cloud mit Ihrem SAML2 Single Sign-on (SSO)-System integrieren. Auf diese Weise können sich Benutzer beim SSO-System ihres Unternehmens anstatt bei einem von Adobe gehosteten Konto authentifizieren.

Als System-Admin können Sie sich und Ihr Team mit persönlichen IDs zu AEM as a Cloud Service hinzufügen. Führen Sie diese Aufgabe aus, bevor Enterprise IDs oder Federated IDs eingerichtet sind. Sobald Enterprise IDs oder Federated IDs eingerichtet sind, können Mitglieder zur Verwendung dieser IDs registriert werden.

### Direktes Anmelden bei Admin Console {#steps-admin-console}

Bevor Sie die Admin Console zum Verwalten von Benutzenden in Ihrem Team verwenden können, müssen Sie sicherstellen, dass Sie selbst ordnungsgemäß darauf zugreifen können und über die entsprechenden Berechtigungen verfügen.

1. Als System-Admin erhalten Sie im Rahmen des Onboarding-Prozesses mehrere E-Mails von Adobe. Suchen Sie nach der Begrüßungs-E-Mail mit Informationen zum Organisationsnamen, auf den Sie Zugriff erhalten haben.

1. Klicken Sie auf **Link** Erste Schritte“ in Ihrer Begrüßungs-E-Mail, um zur Admin Console zu navigieren. Wenn Sie die E-Mail nicht finden können, navigieren Sie in einem Browser unter [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) direkt zur Admin Console.

   ![Begrüßungs-E-Mail](/help/journey-onboarding/assets/get-started-email.png)

1. Melden Sie sich mit Ihrer Adobe ID an. Nach erfolgreicher Anmeldung sehen Sie die Seite **Übersicht** der Adobe Admin Console.

   ![Die Admin Console](/help/journey-onboarding/assets/get-started1.png)

1. Wenn Sie Zugriff auf mehrere Organisationen haben, stellen Sie sicher, dass Sie sich bei der richtigen Organisation angemeldet haben. Um Ihre Organisation zu ändern, klicken Sie oben rechts im Bildschirm auf den Organisationsnamen und wählen Sie die gewünschte Organisation aus, auf die Sie Zugriff benötigen.

   ![Ändern der Organisation](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. Wählen Sie **Administratoren** auf der Karte **Benutzer**, um zu überprüfen, ob Sie ein System-Admin sind.

   ![Überprüfen von Administratoren](/help/journey-onboarding/assets/get-started2.png)

1. Nachdem Sie in der Karte **Benutzer** auf **Administratoren** geklickt haben, können Sie eine Suche durchführen, indem Sie die E-Mail-Adresse Ihrer Adobe ID, Ihren Benutzernamen, Vor- oder Nachnamen eingeben.

   ![Suchen nach Benutzenden](/help/journey-onboarding/assets/get-started3.png)

1. Wenn alles ordnungsgemäß funktioniert, gibt die Suche Ihren Datensatz zurück. Wenn in der Spalte **ADMIN-ROLLE** der Wert **System** angezeigt wird, bedeutet dies, dass Sie (oder die angezeigte Person) System-Admin sind.

   ![Systemstatus](/help/journey-onboarding/assets/get-started4.png)

Herzlichen Glückwunsch, System-Admin!

## Zugriff auf Admin Console über Experience Hub  {#access-admin-console-via-experience-hub}

[Experience Hub](/help/experience-hub.md) ist die einheitliche, personalisierte Startseite für AEM. Dadurch werden AEM-Tools und Admin Console an einem Ort zusammengeführt.

![Admin Console-Option, wie sie auf der Experience Hub-Startseite angezeigt wird](/help/journey-onboarding/assets/experiencehub-adminconsole1.png)

**So greifen Sie über Experience Hub auf die Admin Console zu:**

1. Klicken Sie auf [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home), um die Startseite von Experience Hub zu öffnen.

1. Klicken Sie in **Schnellzugriff**-Gruppierung auf [**Admin Console**](https://experience.adobe.com).

## Adobe Identity Management System {#ims}

AEM as a Cloud Service wird vorkonfiguriert mit Adobe Identity Management System (IMS) bereitgestellt, über das die Authentifizierung erfolgt. Es gibt nichts, was Sie als Systemadministrator tun müssen, um diese Funktion zu aktivieren.

Durch die Verwendung von IMS kann die Anmeldung bei AEM as a Cloud Service und dem Rest von Adobe Experience Cloud gemeinsam ausgeführt werden. Unternehmen mit vielen Adobe-Produkten profitieren am meisten. Erstellen Sie rollenbasierte Gruppen in der Admin Console und gewähren Sie Produktzugriff über IMS, z. B. AEM as a Cloud Service.

Weitere Informationen zu Produktprofilen und der Zuweisung von Benutzenden finden Sie im nächsten Teil dieser Onboarding-Tour.

## Adobe-Support kontaktieren {#support}

Sollten Sie Probleme haben, erhalten Sie über die Admin Console Zugang zum Adobe-Support. Auf der Registerkarte **Support** können Sie über eine einfache und anwenderfreundliche Oberfläche auf verschiedene Support-Funktionen zugreifen.

![Registerkarte „Support“](/help/journey-onboarding/assets/support-menu.png)

Über die Registerkarte können Sie Fälle erstellen und verwalten, direkt mit dem Support-Personal von Adobe chatten und Sitzungen mit Expertinnen und Experten arrangieren. System- und Support-Administratoren müssen sich anmelden, um Zugriff auf die Funktionen zur Verwaltung von Support-Fällen und Expertensitzungen zu erhalten.

## Wie geht es weiter {#whats-next}

Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* Verstehen, was eine Adobe ID ist.
* Möglichkeit zur Anmeldung bei der Admin Console.
* Erfahren Sie, wie Sie Ihre Berechtigungen als Systemadministrator mit der Admin Console überprüfen können.
* Sie wissen, wie Sie den Adobe-Support um Hilfe bitten können.

Jetzt können Sie Ihre Onboarding-Journey fortsetzen, indem Sie lernen, wie Sie [Team-Mitglieder den Cloud Manager-Produktprofilen zuweisen](assign-profiles-cloud-manager.md) sodass Ihre Kolleginnen und Kollegen auch auf AEMaaCS zugreifen können.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Übersicht über die Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) – ein umfassender Überblick
* [Erstellen oder Aktualisieren der Adobe ID](https://helpx.adobe.com/de/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) – Erfahren Sie, wie Sie eine Adobe ID erstellen, ändern und mehrere Adobe-IDs verwalten.
* [SAML 2.0-Authentifizierungs-Handler](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/security/saml-2-0-authenticationhandler#) – AEM wird mit einem SAML-Authentifizierungs-Handler geliefert. Dieser Handler unterstützt das SAML 2.0-Authentifizierungsanfrageprotokoll (Web-SSO-Profil), das die HTTP POST-Bindung verwendet.
* [Administratorrollen](https://helpx.adobe.com/de/enterprise/using/admin-roles.html) – Mithilfe der Adobe Admin Console können Unternehmen eine flexible Verwaltungshierarchie definieren, die eine differenzierte Verwaltung des Zugriffs und der Verwendung von Adobe-Produkten ermöglicht.
* [Support und Expertensitzungen](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.html) - Erfahren Sie, wie Sie auf die Support-Optionen in der Admin Console zugreifen, Ihre Support-Anfragen verwalten, eine Expertensitzung planen und vieles mehr.
