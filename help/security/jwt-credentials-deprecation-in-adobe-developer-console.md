---
title: Einstellung der JWT-Anmeldedaten in Adobe Developer Console
description: Weitere Informationen zu den Auswirkungen der Einstellung der JWT-Anmeldedaten in Adobe Developer Console auf AEM
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
source-git-commit: b8749f7b907e098d23c1cda57930b835f03e3580
workflow-type: ht
source-wordcount: '576'
ht-degree: 100%

---

# Einstellung der JWT-Anmeldedaten in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>Kundinnen und Kunden von AEM 6.5 finden in [diesem Artikel](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) weitere Informationen.

Mit der [Adobe Developer Console](https://developer.adobe.com/console) können Kundinnen und Kunden von Adobe Anmeldedaten generieren, die den Zugriff auf verschiedene APIs ermöglichen. Dabei können sie unter verschiedenen Anmeldedatentypen wählen, von OAuth Server-zu-Server bis zu Single-Page-App. Einer dieser Anmeldedatentypen, Anmeldedaten für Dienstkonten (JWT), wurde zugunsten der OAuth Server-zu-Server-Anmeldedaten eingestellt. Neue Anmeldedaten für Dienstkonten (JWT) können ab dem 3. Juni 2024 nicht mehr erstellt werden und vorhandene JWT-Anmeldedaten funktionieren ab dem 27. Januar 2025 nicht mehr. [Weitere Information zur Einstellung der JWT-Anmeldedaten finden Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dieser Artikel bietet zusätzliche Informationen dazu, wie Kundinnen und Kunden von AEM as a Cloud Service auf diese Einstellung reagieren sollten.

Die wichtigste Information ist derzeit, dass AEM-Funktionen die neuen OAuth Server-zu-Server-Anmeldedaten noch nicht unterstützen. Unterstützung wird bald verfügbar sein. Bis Ende April 2024 ist eine Unterstützung durch eine AEM-Version für AEM as a Cloud Service geplant. Möglicherweise haben Sie eine E-Mail mit Anweisungen zum Migrieren Ihrer JWT-Anmeldedaten erhalten. Bitte warten Sie jedoch mit der Migration der Anmeldedaten bis AEM den neuen OAuth-Server-zu-Server-Anmeldedatentyp unterstützt.

In den folgenden Abschnitten werden die Szenarien aufgeführt, in denen Kundinnen und Kunden ihre Anmeldedaten für Dienstkonten (JWT) durch OAuth-Server-zu-Server-Anmeldedaten ersetzen müssen (oder dies in einigen Fällen nicht tun sollten), sobald AEM sie ab Ende April unterstützt. Weitere Informationen dazu, wie die Anmeldedaten in Zukunft ersetzt werden können, finden Sie [hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview).

>[!NOTE]
>
>Die [**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (Beachten Sie **AEM** im Namen, was die AEM Developer Console von der **Adobe** Developer Console unterscheidet) bietet ein Dienstprogramm zum Generieren von [JWT-Token](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md), die für Server-zu-Server-APIs verwendet werden. Diese Anmeldedaten sind nicht veraltet und können weiterhin verwendet werden.


## Integrieren von AEM mit anderen Adobe-Lösungen {#integrating-aem-with-other-adobe-solutions}

**Aktion**: Warten Sie mit einer Migration bis Ende April 2024, wenn AEM sie unterstützt (dieser Artikel wird dann aktualisiert).

**Relevante AEM-Versionen**: AEM as a Cloud Service

Mit der AEM Author-Benutzeroberfläche können Kundinnen und Kunden von AEM Integrationen mit allen anderen Adobe-Lösungen konfigurieren. Unter anderem Adobe Target, Adobe Analytics, Adobe Launch, AFCS und viele weitere.

![Integrieren von AEM mit anderen Lösungen](/help/security/assets/jwt-deprecation.png)

Zum Beispiel finden Sie [hier](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=de) die Anweisungen zum Konfigurieren der Integration mit Adobe Target. Der API-Schlüssel im Abschnitt [Abschließen der IMS-Konfiguration in AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=de#completing-the-ims-configuration-in-aem) sollte in den OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, sobald AEM diese Anmeldedaten Ende April unterstützt. Diese Anweisungen werden Ende April überarbeitet, damit Sie die neuen OAuth-Server-zu-Server-Anmeldedaten anwenden können.

## Cloud Manager-APIs {#cloud-manager-apis}

**Aktion**: Warten Sie mit einer Migration bis Ende April 2024, wenn AEM sie unterstützt (dieser Artikel wird dann aktualisiert).

**Relevante AEM-Versionen**: AEM as a Cloud Service

Kundinnen und Kunden erstellen Adobe Developer Console-Projekte, damit sie die [Cloud Manager-APIs](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aufrufen können. Die Anmeldedaten im Adobe Developer-Projekt sollten in den OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, sobald sie von AEM und Cloud Manager unterstützt werden.

## Automatisch generierte Projekte {#autogen-projects}

**Aktion**: Führen Sie die Migration nicht eigenständig durch, da Adobe die Migration in Ihrem Namen durchführen wird.

**Relevante AEM-Versionen**: AEM as a Cloud Service.

Wenn Cloud Manager AEM as a Cloud Service-Umgebungen bereitstellt, wird automatisch ein Adobe Developer Console-Projekt mit JWT-Anmeldedaten generiert. Dieses Projekt ist als schreibgeschützt markiert, wie im folgenden Screenshot dargestellt. Kundinnen und Kunden können und sollten nicht versuchen, diese Projekte zu OAuth-Server-zu-Server-Anmeldedaten zu migrieren. Stattdessen migriert Adobe diese Projekte von sich aus, bevor die Anmeldedaten nicht mehr verwendet werden können.

![Automatisch generierte Projekte](/help/security/assets/jwt-deprecation-autogen-projects.png)
