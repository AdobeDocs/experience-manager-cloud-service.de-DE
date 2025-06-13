---
title: Abschaffung der JWT-Anmeldedaten in Adobe Developer Console
description: Erhalten Sie weitere Informationen zu den Auswirkungen der Einstellung der JWT-Anmeldedaten in Adobe Developer Console auf AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
feature: Security
role: Admin
source-git-commit: 5db419e674ceb3c861f53a19e7b852c89ebd3702
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 99%

---

# Abschaffung der JWT-Anmeldedaten in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM 6.5-Kundinnen und -Kunden sollten für weitere Informationen [die vergleichbare Dokumentation für AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) referenzieren.

Mit der [Adobe Developer Console](https://developer.adobe.com/console) können Kundinnen und Kunden von Adobe Anmeldedaten generieren, die den Zugriff auf verschiedene APIs ermöglichen. Dabei können sie unter verschiedenen Anmeldedatentypen wählen, von OAuth Server-zu-Server bis zu Single-Page-App. Einer dieser Anmeldedatentypen, Anmeldedaten für Dienstkonten (JWT), wurde zugunsten der OAuth Server-zu-Server-Anmeldedaten eingestellt. Neue Dienstkonten(JWT)-Anmeldedaten können seit dem 3. Juni 2024 nicht mehr erstellt werden, und vorhandene JWT-Anmeldedaten funktionieren ab dem 30. Juni 2025 nicht mehr. [Weitere Information zur Einstellung der JWT-Anmeldedaten finden Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dieser Artikel bietet zusätzliche Informationen dazu, wie Kundinnen und Kunden von AEM as a Cloud Service auf diese Einstellung reagieren sollten.

Die wichtigste Neuerung ist, dass AEM jetzt die neuen OAuth-Server-zu-Server-Anmeldedaten für AEM as a Cloud Service unterstützt. Möglicherweise haben Sie eine E-Mail mit Anweisungen zum Migrieren Ihrer JWT-Anmeldedaten erhalten. Diese Migration kann jetzt durchgeführt werden.

In den folgenden Abschnitten werden die Szenarien aufgeführt, in denen Kundinnen und Kunden ihre Dienstkonten(JWT)-Anmeldedaten durch OAuth Server-zu-Server-Anmeldedaten ersetzen müssen (oder in einigen Fällen dies nicht tun sollten), jetzt da AEM sie unterstützt. [Hier finden Sie weitere Informationen dazu](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration#migration-overview), wie Sie die Anmeldedaten migrieren.

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

Kundinnen und Kunden erstellen Adobe Developer Console-Projekte, damit sie die [Cloud Manager-APIs](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aufrufen können. Die Anmeldedaten im Adobe Developer-Projekt müssen zum OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, bevor die veralteten JWT-Anmeldedaten im Juni 2025 ablaufen.

## Automatisch generierte Projekte {#autogen-projects}

**Aktion**: Führen Sie die Migration nicht eigenständig durch, da Adobe die Migration in Ihrem Namen durchführen wird.

**Relevante AEM-Versionen**: AEM as a Cloud Service.

Wenn Cloud Manager AEM as a Cloud Service-Umgebungen bereitstellt, wird automatisch ein Adobe Developer Console-Projekt mit JWT-Anmeldedaten generiert. Dieses Projekt ist als schreibgeschützt markiert, wie im folgenden Screenshot dargestellt. Kundinnen und Kunden können und sollten nicht versuchen, diese Projekte auf OAuth-Server-zu-Server-Anmeldedaten zu migrieren. Stattdessen migriert Adobe diese Projekte selbstständig, bevor die Anmeldedaten nicht mehr verwendbar sind.

![Automatisch generierte Projekte](/help/security/assets/jwt-deprecation-autogen-projects.png)

## Automatisch erstellte Projekte – Häufig gestellte Fragen {#autogen-projects-faqs}

Dieser Abschnitt enthält Antworten auf die am häufigsten gestellten Fragen zur Abschaffung der JWT-Anmeldedaten für automatisch erstellte Projekte in AEM as a Cloud Service.

**Wie weiß ich, welche Projekte automatisch generiert werden?**

Navigieren Sie zur Adobe Developer Console | Abschnitt „Projekte“.  Automatisch erstellte Projekte in AEM as a Cloud Service verfügen über ein Sperrsymbol mit der Kennung „Automatisch erstellt“.  Automatisch erstellte Projekte folgen dem Format „AEM-P#####-e#######“ und werden von Benutzenden des technischen Kontos erstellt.

![Automatisch erstellte Projekte](/help/security/assets/jwt-alert.png)

**Was ist, wenn Probleme mit unseren automatisch erstellten Projekten auftreten?**

Wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html?lang=de).

**Sollte ich unsere automatisch erstellten Projekte migrieren?**

Es ist kein Handeln erforderlich, da Adobe alle automatisch erstellten Projekte für Umgebungen mit AEM-Version 17258 (August 2024) und höher für Sie migriert.

**Welche Zeitpläne gelten für die Migration automatisch erstellter Projekte?**

Adobe wird im ersten Quartal 2025 eine Migration in Phasen einleiten, beginnend mit Entwicklungsumgebungen.

**Wie wird es sich auf unsere AEM as a Cloud Service-Instanz auswirken, wenn wir eine AEM-Version haben, die älter als die AEM-Version 17258 (August 2024) ist?**

Integrationen von automatisch erstellten Projekten werden nicht mehr funktionieren, wenn sie nicht bis Juni 2025 zu OAuth migriert worden sind.

Um einen reibungslosen Übergang sicherzustellen, sollten sich Kundinnen und Kunden umgehend an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html?lang=de) wenden und mit der Aktualisierung auf die [neueste AEM-Version](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest) beginnen. So bleibt ausreichend Zeit für Regressionstests, und Adobe kann die Migration von Projekten effizient verwalten.

**Kann ich auf eine unterstützte OAuth-Version aktualisieren, ohne meine AEM-Version AEM as a Cloud Service zu aktualisieren?**

Nein. Um einen reibungslosen Übergang sicherzustellen, sollten sich Kundinnen und Kunden umgehend an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html?lang=de) wenden und mit der Aktualisierung auf die [neueste AEM-Version](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest) beginnen. So bleibt ausreichend Zeit für Regressionstests, und Adobe kann die Migration von Projekten effizient verwalten.
