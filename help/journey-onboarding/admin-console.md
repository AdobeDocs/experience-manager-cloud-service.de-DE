---
title: Zugriff auf die Admin Console
description: Sobald Sie die für das Onboarding erforderliche Vorbereitung und die Grundlagen der AEMaaCS-Struktur kennen, können Sie sich erstmals bei der Admin Console anmelden.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 9%

---

# Zugriff auf die Admin Console {#accessing-admin-console}

In diesem Teil des [Onboarding-Journey,](overview.md) Sie erfahren mehr über die erforderliche Vorbereitung, bevor Sie sich zum ersten Mal in das System einloggen.

## Ziel {#objective}

Nachdem Sie den Artikel gelesen haben [AEM as a Cloud Service Terminologie](terminology.md) und die Grundlagen der AEMaaCS-Struktur verstehen, können Sie sich zum ersten Mal bei der Admin Console anmelden!

Als Systemadministrator sind Sie für die Verwaltung von Benutzern in Ihrem Unternehmen verantwortlich. Verwenden Sie dazu die -Admin Console. Nach Lesen dieses Abschnitts sollten Sie Folgendes tun:

* Verstehen Sie, was eine Adobe ID ist.
* Sie können sich bei Admin Console anmelden.
* Erfahren Sie, wie Sie Ihre Berechtigungen als Systemadministrator über Admin Console überprüfen können.
* Erfahren Sie, wie Sie den Support der Adobe kontaktieren können.

## Die Admin Console {#admin-console}

Die Adobe Admin Console ist ein zentraler Ort, um Ihre Adobe-Produktlizenzen und Benutzer zu verwalten. Mit der Admin Console können Sie Benutzer an einem Ort erstellen und verwalten und nicht in Ihren einzelnen Lösungen.

## Adobe ID {#adobe-id}

Um sich bei der Admin Console anzumelden, benötigen Sie eine Adobe ID. Adobe ID ist ein Konto, das an eine bestimmte E-Mail-Adresse gebunden ist, die zum Anmelden und Zugreifen auf AEM as a Cloud Service oder auf Ihre Adobe-Lösungen benötigt wird. Durch die Verwendung Ihrer Adobe ID bleiben alle Ihre Adobe-Pläne und -Produkte mit einem einzigen Konto verknüpft.

Wenn Sie als Systemadministrator Ihr Team in der Admin Console einrichten, geben Sie die E-Mail-Adresse an, die als Adobe ID verwendet werden soll.

Es gibt drei Arten von Adoben-IDs:

* **Persönliche ID**: Dies ist der Standardtyp von Adobe ID und wird unter adobe.com erstellt. Dieses Konto wird von Adobe verwaltet und jeder kann ein Konto dieser Art erstellen.

* **Enterprise ID**: Unternehmen möchten normalerweise die Kontrolle über die Benutzerkonten erhöhen. Nur Systemadministratoren können Enterprise IDs erstellen und die Organisation ist Eigentümer dieser Konten, wobei Adobe nur als Host dient.

* **Federated ID**: Mit Federated IDs übernimmt die Organisation die volle Verantwortung und Kontrolle über die Konten. Dazu muss Ihr Unternehmen die Adobe Experience Cloud in Ihr SAML2 Single Sign-On (SSO)-System integrieren. Auf diese Weise können sich Benutzer beim SSO-System ihres Unternehmens anstatt bei einem von Adobe gehosteten Konto authentifizieren.

Als Systemadministrator können Sie sich entscheiden, sich und Ihr Team mit persönlichen IDs auf AEM as a Cloud Service zu integrieren, bevor Enterprise IDs oder Federated IDs eingerichtet werden. Sobald Enterprise IDs oder Federated IDs eingerichtet sind, können Mitglieder zur Verwendung dieser IDs übergehen.

## Anmelden bei Admin Console {#steps-admin-console}

Bevor Sie die Admin Console zum Verwalten von Benutzern in Ihrem Team verwenden können, müssen Sie sicherstellen, dass Sie selbst ordnungsgemäß darauf zugreifen und über die entsprechenden Berechtigungen verfügen können.

1. Als Systemadministrator erhalten Sie im Rahmen des Onboarding-Prozesses mehrere E-Mails von Adobe. Suchen Sie nach der Begrüßungs-E-Mail mit Informationen zum Organisationsnamen, auf den Sie Zugriff erhalten haben.

1. Klicken Sie auf **Erste Schritte** in Ihrer Begrüßungs-E-Mail klicken, um zur Admin Console zu navigieren. Wenn Sie die E-Mail nicht finden können, öffnen Sie einen Browser direkt zur Admin Console unter [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

   ![Begrüßungs-E-Mail](/help/journey-onboarding/assets/get-started-email.png)

1. Melden Sie sich mit Ihrer Adobe ID an. Nach erfolgreicher Anmeldung wird die **Übersicht** Seite der Adobe Admin Console.

   ![Die Admin Console](/help/journey-onboarding/assets/get-started1.png)

1. Wenn Sie Zugriff auf mehrere Organisationen haben, stellen Sie sicher, dass Sie sich bei der richtigen Organisation angemeldet haben. Um Ihre Organisation zu ändern, klicken Sie oben rechts auf den Organisationsnamen und wählen Sie die gewünschte Organisation aus, auf die Sie Zugriff benötigen.

   ![Organisation ändern](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. Auswählen **Administratoren** von **Benutzer** -Karte, um zu überprüfen, ob Sie Systemadministrator sind.

   ![Überprüfen von Administratoren](/help/journey-onboarding/assets/get-started2.png)

1. Sobald Sie auf **Administratoren** von **Benutzer** -Karte, können Sie suchen, indem Sie Ihre Adobe ID-E-Mail-Adresse, Ihren Benutzernamen, Vor- oder Nachnamen eingeben.

   ![Benutzer suchen](/help/journey-onboarding/assets/get-started3.png)

1. Wenn alles ordnungsgemäß funktioniert, gibt die Suche Ihren Datensatz zurück. Wenn der Wert in der Variablen **ADMINISTRATORROLLE** Spalten anzeigen **System**, wissen Sie, dass Sie (oder der angezeigte Benutzer) ein Systemadministrator sind.

   ![Systemstatus](/help/journey-onboarding/assets/get-started4.png)

Herzlichen Glückwunsch, Systemadministrator!

## Adobe Identity Management System {#ims}

AEM as a Cloud Service ist mit Adobe Identity Management System (auch IMS genannt) zur Authentifizierung vorkonfiguriert. Es gibt nichts, was Sie als Systemadministrator tun müssen, um dies zu aktivieren.

Durch die Verwendung von IMS konsolidiert AEM as a Cloud Service das Anmeldeerlebnis zwischen AEM und dem Rest der Adobe Experience Cloud. Unternehmen mit mehreren Adobe-Produkten profitieren insbesondere von der Erstellung rollenbasierter Gruppen in der Admin Console und der Zuweisung des Zugriffs auf mehrere Produkte, einschließlich AEM über IMS as a Cloud Service.

Weitere Informationen zu Produktprofilen und der Zuweisung von Benutzern finden Sie im nächsten Teil dieser Onboarding-Journey.

## Kontaktaufnahme mit dem Adobe-Support {#support}

Sollten Sie Probleme haben, können Sie über die Admin Console auf die Adobe-Unterstützung zugreifen. Die **Support** -Tab bietet Zugriff auf verschiedene Funktionen zur Adobe-Unterstützung über eine einfache und benutzerfreundliche Oberfläche.

![Support-Tab](/help/journey-onboarding/assets/support-menu.png)

Im Tab können Sie Fälle erstellen und verwalten, direkt mit Support-Mitarbeitern der Adobe chatten und Sitzungen mit Experten planen. Systemadministratoren und Support-Administratoren müssen sich anmelden, um auf Support-Fälle und Expertensitzungsoptionen zugreifen zu können.

## Wie geht es weiter {#whats-next}

Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* Verstehen Sie, was und Adobe ID ist.
* Sie können sich bei Admin Console anmelden.
* Erfahren Sie, wie Sie Ihre Berechtigungen als Systemadministrator über Admin Console überprüfen können.
* Erfahren Sie, wie Sie den Support der Adobe kontaktieren können.

Sie können Ihre Onboarding-Journey fortsetzen, indem Sie lernen, wie Sie [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](assign-profiles-cloud-manager.md) damit Ihre Kollegen auch auf AEMaaCS zugreifen können.

## Zusätzliche Ressourcen {#additional-resources}

* [Übersicht über Admin Consolen](https://helpx.adobe.com/de/enterprise/using/admin-console.html) - Ein umfassender Überblick über die Admin Console
* [Erstellen oder Aktualisieren von Adobe ID](https://helpx.adobe.com/de/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) - Erfahren Sie, wie Sie eine Adobe ID erstellen, ändern und mehrere Adoben-IDs verwalten.
* [SAML 2.0-Authentifizierungs-Handler](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html) - AEM wird mit einem SAML-Authentifizierungs-Handler geliefert. Dieser Handler unterstützt das SAML 2.0-Authentifizierungsanforderungsprotokoll (Web-SSO-Profil), das die HTTP POST-Bindung verwendet.
* [Administratorrollen](https://helpx.adobe.com/de/enterprise/using/admin-roles.ug.html) - Mithilfe der Adobe Admin Console können Unternehmen eine flexible Verwaltungshierarchie definieren, die eine differenzierte Verwaltung des Produktzugriffs und der Verwendung von Adobe ermöglicht.
* [Support- und Expertensitzungen](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) - Erfahren Sie, wie Sie auf die Support-Optionen in der Admin Console zugreifen, Ihre Support-Anfragen verwalten, eine Expertensitzung planen und vieles mehr.
