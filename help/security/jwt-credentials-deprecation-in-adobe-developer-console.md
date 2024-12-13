---
title: Einstellung der JWT-Anmeldedaten in Adobe Developer Console
description: Erhalten Sie weitere Informationen zu den Auswirkungen der Einstellung der JWT-Anmeldedaten in Adobe Developer Console auf AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
feature: Security
role: Admin
source-git-commit: d3c00c33925a23ad5b1080c1e864cfdb5a8d1c1b
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 63%

---

# Einstellung der JWT-Anmeldedaten in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM 6.5-Kundinnen und -Kunden sollten für weitere Informationen [die vergleichbare Dokumentation für AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) referenzieren.

Mit der [Adobe Developer Console](https://developer.adobe.com/console) können Kundinnen und Kunden von Adobe Anmeldedaten generieren, die den Zugriff auf verschiedene APIs ermöglichen. Dabei können sie unter verschiedenen Anmeldedatentypen wählen, von OAuth Server-zu-Server bis zu Single-Page-App. Einer dieser Anmeldedatentypen, Anmeldedaten für Dienstkonten (JWT), wurde zugunsten der OAuth Server-zu-Server-Anmeldedaten eingestellt. Neue Anmeldedaten für Dienstkonten (JWT) können ab dem 3. Juni 2024 nicht mehr erstellt werden und vorhandene JWT-Anmeldedaten funktionieren ab dem 27. Januar 2025 nicht mehr. [Weitere Information zur Einstellung der JWT-Anmeldedaten finden Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dieser Artikel bietet zusätzliche Informationen dazu, wie Kundinnen und Kunden von AEM as a Cloud Service auf diese Einstellung reagieren sollten.

Die wichtigste Neuerung ist, dass AEM jetzt die neuen OAuth-Server-zu-Server-Anmeldedaten für AEM as a Cloud Service unterstützt. Möglicherweise haben Sie eine E-Mail mit Anweisungen zum Migrieren Ihrer JWT-Anmeldedaten erhalten. Diese Migration kann jetzt durchgeführt werden.

In den folgenden Abschnitten werden die Szenarien aufgeführt, in denen Kundinnen und Kunden ihre Dienstkonten(JWT)-Anmeldedaten durch OAuth Server-zu-Server-Anmeldedaten ersetzen müssen (oder in einigen Fällen dies nicht tun sollten), jetzt da AEM sie unterstützt. [Hier finden Sie weitere Informationen dazu](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview), wie Sie die Anmeldedaten migrieren.

>[!NOTE]
>
>Die [**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (Beachten Sie **AEM** im Namen, was die AEM Developer Console von der **Adobe** Developer Console unterscheidet) bietet ein Dienstprogramm zum Generieren von [JWT-Token](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md), die für Server-zu-Server-APIs verwendet werden. Diese Anmeldedaten sind nicht veraltet und können weiterhin verwendet werden.

## Integrieren von AEM mit anderen Adobe-Lösungen {#integrating-aem-with-other-adobe-solutions}

**Aktion**: Migrieren Sie Ihre Konfiguration, da AEM jetzt OAuth-Anmeldedaten unterstützt.

**Relevante AEM-Versionen**: AEM as a Cloud Service

Kundinnen und Kunden von AEM können AEM verwenden, um Integrationen mit vielen anderen Adobe-Lösungen zu konfigurieren. Zum Beispiel Adobe Target, Adobe Analytics und vielen weiteren.

Siehe [Einrichten von IMS-Integrationen für AEM as a Cloud Service](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) für Details zu folgenden Vorgehensweisen:

* Erstellen von Konfigurationen mit OAuth-Anmeldedaten
* Migrieren von Konfigurationen, die mit JWT-Anmeldedaten erstellt wurden, zur Verwendung von OAuth-Anmeldedaten

## Cloud Manager-APIs {#cloud-manager-apis}

**Aktion**: Migrieren Sie Ihre JWT-Anmeldedaten zu OAuth-Anmeldedaten, die jetzt von Cloud Manager unterstützt werden.

**Relevante AEM-Versionen**: AEM as a Cloud Service

Kundinnen und Kunden erstellen Adobe Developer Console-Projekte, damit sie die [Cloud Manager-APIs](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aufrufen können. Die Anmeldedaten im Adobe Developer-Projekt sollten in den OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, bevor die veralteten JWT-Anmeldedaten im Januar 2025 ablaufen.

## Automatisch generierte Projekte {#autogen-projects}

**Aktion**: Führen Sie die Migration nicht eigenständig durch, da Adobe die Migration in Ihrem Namen durchführen wird.

**Relevante AEM-Versionen**: AEM as a Cloud Service.

Wenn Cloud Manager AEM as a Cloud Service-Umgebungen bereitstellt, wird automatisch ein Adobe Developer Console-Projekt mit JWT-Anmeldedaten generiert. Dieses Projekt ist als schreibgeschützt markiert, wie im folgenden Screenshot dargestellt. Kundinnen und Kunden können und sollten nicht versuchen, diese Projekte auf OAuth-Server-zu-Server-Anmeldedaten zu migrieren. Stattdessen migriert Adobe diese Projekte selbstständig, bevor die Anmeldedaten nicht mehr verwendbar sind.

![Automatisch generierte Projekte](/help/security/assets/jwt-deprecation-autogen-projects.png)

## Automatisch erstellte Projekte - FAQs {#autogen-projects-faqs}

Dieser Abschnitt enthält Antworten auf die am häufigsten gestellten Fragen zur Einstellung von JWT-Anmeldeinformationen für automatisch generierte Projekte in AEM as a Cloud Service.

**Wie erstelle ich, welche Projekte automatisch generiert werden?**
Navigieren Sie zur Adobe Developer Console | Abschnitt „Projekte“.  Automatisch erstellte AEM as a Cloud Service-Projekte verfügen über ein Sperrsymbol mit der Kennung „Automatisch generiert“.  Automatisch erstellte Projekte folgen dem Format AEM-P#####-e####### und werden vom Benutzer des technischen Kontos erstellt.

<img width="439" alt="image" src="https://git.corp.adobe.com/storage/user/16149/files/6b20a8a3-3711-4741-8f2c-ec5e36fe97cc">


**Was ist, wenn Probleme mit unseren automatisch generierten Projekten auftreten?**

[Adobe-Kundenunterstützung kontaktieren](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

**Sollte ich unsere automatisch generierten Projekte migrieren?**

Es ist keine Aktion erforderlich, da Adobe in Ihrem Auftrag automatisch generierte Umgebungen mit AEM-Version 17258 (24. August) und höher migriert.

**Welche Zeitpläne gelten für die Migration automatisch generierter Projekte?**

Adobe wird im ersten Quartal 2025 einen stufenweisen Migrationsansatz einleiten, beginnend mit Entwicklungsumgebungen.

**Wie wird sich auf unsere AEM as a Cloud Service-Instanz auswirken, wenn wir eine AEM-Version haben, die älter als die AEM-Version 17258 (24. August) ist?**

Automatisch generierte Projektintegrationen funktionieren nicht mehr, wenn sie nicht bis Juni 2025 zu OAuth migriert werden.

Um einen reibungslosen Übergang sicherzustellen, sollten sich Kunden umgehend an die [Adobe](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html)Kundenunterstützung wenden und mit der Aktualisierung auf die [neueste AEM-Version](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest) beginnen. Dadurch bleibt ausreichend Zeit für Regressionstests, und das Adobe kann die Projektmigration effizient verwalten.

**Kann ich auf eine unterstützte OAuth-Version aktualisieren, ohne meine AEM as a Cloud Service AEM-Version zu aktualisieren?**

Nein. Um einen reibungslosen Übergang sicherzustellen, sollten sich Kunden umgehend an die [Adobe](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html)Kundenunterstützung wenden und mit der Aktualisierung auf die [neueste AEM-Version](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest) beginnen. Dadurch bleibt ausreichend Zeit für Regressionstests, und das Adobe kann die Projektmigration effizient verwalten.
