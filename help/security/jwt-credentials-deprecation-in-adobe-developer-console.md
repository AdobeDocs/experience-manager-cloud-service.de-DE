---
title: Einstellung der JWT-Anmeldedaten in Adobe Developer Console
description: Weitere Informationen zu den Auswirkungen der Einstellung der JWT-Anmeldedaten in Adobe Developer Console auf AEM
source-git-commit: a354786f1ddfe50b01def85d3c83da09c6a35d2f
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 86%

---


# Einstellung der JWT-Anmeldedaten in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM as a Cloud Service-Kunden sollten auf Folgendes verweisen [diesem Artikel](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html) für weitere Informationen.

Mit der [Adobe Developer Console](https://developer.adobe.com/console) können Kundinnen und Kunden von Adobe Anmeldedaten generieren, die den Zugriff auf verschiedene APIs ermöglichen. Dabei können sie unter verschiedenen Anmeldedatentypen wählen, von OAuth Server-zu-Server bis zu Single-Page-App. Einer dieser Anmeldedatentypen, Anmeldedaten für Dienstkonten (JWT), wurde zugunsten der OAuth Server-zu-Server-Anmeldedaten eingestellt. Neue Dienstkonten(JWT)-Anmeldedaten können ab dem 1. Mai 2024 nicht mehr erstellt werden und vorhandene JWT-Anmeldedaten funktionieren ab dem 1. Januar 2025 nicht mehr. [Weitere Information zur Einstellung der JWT-Anmeldedaten finden Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dieser Artikel bietet einen zusätzlichen Kontext dazu, wie AEM as a Cloud Service die Einstellung handhaben sollte.

Die wichtigste Information ist derzeit, dass AEM-Funktionen die neuen OAuth Server-zu-Server-Anmeldedaten noch nicht unterstützen. Der Support wird bald kommen - bis Mitte April 2024 durch eine AEM Veröffentlichung für AEM as a Cloud Service. Möglicherweise haben Sie eine E-Mail mit Anweisungen zum Migrieren Ihrer JWT-Anmeldedaten erhalten. Bitte warten Sie jedoch mit der Migration der Anmeldedaten bis AEM den neuen OAuth-Server-zu-Server-Anmeldedatentyp unterstützt.

In den folgenden Abschnitten werden die Szenarien aufgeführt, in denen Kundinnen und Kunden ihre Dienstkonten(JWT)-Anmeldedaten durch OAuth Server-zu-Server-Anmeldedaten ersetzen müssen (oder in einigen Fällen dies nicht tun sollten), sobald AEM sie ab Mitte April unterstützt. Weitere Informationen dazu, wie die Anmeldedaten in Zukunft ersetzt werden können, finden Sie [hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview).

>[!NOTE]
>
>Die [**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (Beachten Sie **AEM** im Namen, was die AEM Developer Console von der **Adobe** Developer Console unterscheidet) bietet ein Dienstprogramm zum Generieren von [JWT-Token](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md), die für Server-zu-Server-APIs verwendet werden. Diese Anmeldedaten sind nicht veraltet und können weiterhin verwendet werden.


## Integrieren von AEM mit anderen Adobe-Lösungen {#integrating-aem-with-other-adobe-solutions}

**Aktion**: Warten Sie bis nach der Migration Mitte April 2024, wenn AEM dies unterstützen wird.

**Relevante AEM**: AEM AS A CLOUD SERVICE

Mit der AEM Author-Benutzeroberfläche können Kundinnen und Kunden von AEM Integrationen mit allen anderen Adobe-Lösungen konfigurieren. Unter anderem Adobe Target, Adobe Analytics, Adobe Launch, AFCS und viele weitere.

![Integrieren von AEM mit anderen Lösungen](/help/security/assets/jwt-deprecation.png)

Zum Beispiel finden Sie [hier](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=de) die Anweisungen zum Konfigurieren der Integration mit Adobe Target. Der API-Schlüssel im Abschnitt [Abschließen der IMS-Konfiguration in AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=de#completing-the-ims-configuration-in-aem) sollte in den OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, sobald AEM diese Anmeldedaten Mitte April unterstützt. Diese Anweisungen werden Mitte April überarbeitet, damit Sie die neuen OAuth Server-zu-Server-Anmeldedaten anwenden können.

## Cloud Manager-APIs {#cloud-manager-apis}

**Aktion**: Warten Sie bis zur Migration Mitte April 2024, wenn AEM dies unterstützen wird.

**Relevante AEM**: AEM AS A CLOUD SERVICE

Kundinnen und Kunden erstellen Adobe Developer Console-Projekte, damit sie die [Cloud Manager-APIs](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aufrufen können. Die Anmeldedaten im Adobe Developer-Projekt sollten in den OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, sobald sie von AEM und Cloud Manager unterstützt werden.

## Automatisch generierte Projekte {#autogen-projects}

**Aktion**: Führen Sie die Migration nicht eigenständig durch, da Adobe die Migration in Ihrem Namen durchführen wird.

**Relevante AEM**: AEM as a Cloud Service.

Wenn Cloud Manager AEM as a Cloud Service-Umgebungen bereitstellt, wird automatisch ein Adobe Developer Console-Projekt mit JWT-Anmeldedaten generiert. Dieses Projekt ist als schreibgeschützt markiert, wie im folgenden Screenshot dargestellt. Kundinnen und Kunden können und sollten nicht versuchen, diese Projekte zu OAuth-Server-zu-Server-Anmeldedaten zu migrieren. Stattdessen migriert Adobe diese Projekte von sich aus, bevor die Anmeldedaten nicht mehr verwendet werden können.

![Automatisch generierte Projekte](/help/security/assets/jwt-deprecation-autogen-projects.png)

