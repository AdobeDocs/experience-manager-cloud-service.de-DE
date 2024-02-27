---
title: Einstellung von JWT-Anmeldedaten in der Adobe Developer Console
description: Erfahren Sie mehr über die Auswirkungen der Einstellung von JWT-Anmeldedaten in der Adobe Developer Console auf AEM
source-git-commit: e02e38a5267188111f0392a0a5c7b73e6a4f22b5
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# Einstellung von JWT-Anmeldedaten in der Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

Adobe-Kunden verwenden [Adobe Developer-Konsole](https://developer.adobe.com/console) , um Anmeldeinformationen zu generieren, die den Zugriff auf verschiedene APIs ermöglichen. Die Kunden wählen aus verschiedenen Berechtigungstypen, von OAuth Server zu Server bis zu Single Page App. Einer dieser Berechtigungstypen, die Anmeldedaten für Dienstkonten (JWT), wurde zugunsten der OAuth Server-zu-Server-Anmeldedaten eingestellt. Neue Service Account (JWT)-Anmeldeinformationen können am oder nach dem 1. Mai 2024 nicht erstellt werden und vorhandene JWT-Anmeldeinformationen funktionieren am oder nach dem 1. Januar 2025 nicht mehr. Sie können [Informationen zur veralteten Version](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dieser Artikel bietet einen zusätzlichen Kontext dazu, wie AEM as a Cloud Service und AEM 6.5-Kunden die Einstellung handhaben sollten.

Der Hauptvorteil ist derzeit, dass AEM Funktionen die neuen OAuth Server-zu-Server-Anmeldedaten noch nicht unterstützen. Der Support wird bald verfügbar sein - bis Mitte April 2024 durch eine AEM-Version für AEM as a Cloud Service und durch ein spezielles Kompatibilitätspaket, das für AEM 6.5 installiert wird, wenn Sie das neueste Service Pack 20 oder niedriger ausführen (Service Pack 21 und höher wird es automatisch einschließen). Möglicherweise haben Sie eine E-Mail mit Anweisungen zum Migrieren Ihrer JWT-Anmeldeinformationen erhalten. Sie sollten jedoch sicherstellen, dass Sie die Migration der Anmeldeinformationen speichern können und sollten, bis AEM den neuen OAuth-Server-zu-Server-Berechtigungstyp unterstützt.

In den folgenden Abschnitten werden die Szenarien aufgelistet, in denen Kunden ihre JWT-Anmeldeinformationen (Service Account) durch OAuth Server-zu-Server-Anmeldeinformationen ersetzen müssen (oder in einigen Fällen nicht), sobald AEM sie Mitte April unterstützt. [Lesen von](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) , um die Anmeldeinformationen in der Zukunft zu ersetzen.

>[!NOTE]
>
>Die [**AEM** Entwicklerkonsole](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (Beachten Sie die **AEM** im Namen, der ihn von der **Adobe** Developer Console) bietet ein Dienstprogramm zum Generieren von [JWT-Token](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) wird für Server-zu-Server-APIs verwendet. Diese Anmeldeinformationen werden nicht veraltet und können weiterhin verwendet werden.


## Integrieren von AEM mit anderen Adobe-Lösungen {#integrating-aem-with-other-adobe-solutions}

**Aktion**: Warten Sie bis zur Migration Mitte April 2024, wenn AEM dies unterstützt.

**Relevante AEM**: AEM as a Cloud Service und Adobe Managed Services (Service Pack 20 und höher).


AEM Kunden verwenden die AEM Author-Benutzeroberfläche, um Integrationen mit allen anderen Adobe-Lösungen zu konfigurieren. Beispielsweise Adobe Target, Adobe Analytics, Adobe Launch, AFCS und viele andere.

![AEM mit anderen Lösungen integrieren](/help/security/assets/jwt-deprecation.png)

Beispiel: [die Anweisungen](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=en) für die Konfiguration der Integration mit Adobe Target. Der API-Schlüssel im [Abschließen der IMS-Konfiguration in AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html#completing-the-ims-configuration-in-aem) sollte in den OAuth-Server-zu-Server-Berechtigungstyp migriert werden, sobald AEM diese Anmeldeinformationen Mitte April unterstützt. Diese Anweisungen werden Mitte April aktualisiert, damit Sie die neuen OAuth Server-zu-Server-Anmeldedaten anwenden können.

## Cloud Manager-APIs {#cloud-manager-apis}

**Aktion**: Warten Sie bis zur Migration Mitte April 2024, wenn AEM dies unterstützt.

**Relevante AEM**: AEM as a Cloud Service und Adobe Managed Services (Service Pack 20 und höher).

Kunden erstellen Adobe Developer Console-Projekte, damit sie aufrufen können [Cloud Manager-APIs](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). Die Anmeldeinformationen im Adobe Developer-Projekt sollten in den OAuth-Server-zu-Server-Berechtigungstyp migriert werden, sobald sie von AEM und Cloud Manager unterstützt werden.

## Automatisch generierte Projekte {#autogen-projects}

**Aktion**: Migrieren Sie nicht, da Adobe in Ihrem Namen migriert.

**Relevante AEM**: Nur AEM as a Cloud Service.

Wenn Cloud Manager as a Cloud Service Umgebungen AEM, wird automatisch ein Adobe Developer Console-Projekt mit JWT-Anmeldeinformationen generiert. Dieses Projekt ist als schreibgeschützt markiert, wie im folgenden Screenshot dargestellt. Kunden können und sollten nicht versuchen, diese Projekte zu OAuth Server-zu-Server-Anmeldeinformationen zu migrieren. Stattdessen migriert Adobe diese Projekte allein, bevor die Anmeldeinformationen nicht mehr verwendet werden können.

![Automatisch generierte Projekte](/help/security/assets/jwt-deprecation-autogen-projects.png)

