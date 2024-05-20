---
title: Einrichten von IMS-Integrationen für AEM as a Cloud Service
description: Erfahren Sie, wie Sie IMS-Integrationen für AEM as a Cloud Service einrichten.
source-git-commit: e6749b9a5e97634a4706db5656b1e11dba4442c9
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 3%

---


# Einrichten von IMS-Integrationen für AEM as a Cloud Service {#setting-up-ims-integrations-for-aemaacs}

Adobe Experience Manager (AEM) as a Cloud Service kann mit vielen anderen Adobe-Lösungen integriert werden. Zum Beispiel Adobe Target, Adobe Analytics und andere.

Die Integrationen verwenden eine IMS-Integration, die mit S2S OAuth konfiguriert ist.

* Nach der Erstellung:

   * [Anmeldedaten in der Developer Console](#credentials-in-the-developer-console)

* Anschließend können Sie:

   * Erstellen Sie eine (neue) [OAuth-Konfiguration](#creating-oauth-configuration)

   * [Migrieren einer vorhandenen JWT-Konfiguration in eine OAuth-Konfiguration](#migrating-existing-JWT-configuration-to-oauth)

>[!CAUTION]
>
>Zuvor wurden Konfigurationen mit [JWT-Anmeldeinformationen, die in der Adobe Developer Console nicht mehr unterstützt werden](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md).
>
>Solche Konfigurationen können nicht mehr erstellt oder aktualisiert werden, können aber zu OAuth-Konfigurationen migriert werden.

## Anmeldedaten in der Developer Console {#credentials-in-the-developer-console}

Als ersten Schritt müssen Sie die OAuth-Anmeldeinformationen in der Adobe Developer Console konfigurieren.

Weitere Informationen dazu finden Sie in der Dokumentation zur Developer Console, abhängig von Ihren Anforderungen:

* Übersicht:

   * [Server-zu-Server-Authentifizierung](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

* Erstellen einer neuen OAuth-Berechtigung:

   * [OAuth-Implementierungshandbuch für Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

* Migration einer vorhandenen JWT-Berechtigung in eine OAuth-Berechtigung:

   * [Migration von JWT-Anmeldedaten (Service Account) zu OAuth-Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)

Zum Beispiel:

![OAuth-Berechtigung in der Developer Console](assets/ims-configuration-developer-console.png)

## OAuth-Konfiguration erstellen {#creating-oauth-configuration}

So erstellen Sie eine neue Adobe IMS-Integration mit OAuth:

1. Navigieren Sie in AEM zu **Instrumente**, **Sicherheit**, **Adobe IMS-Integration**.

1. Wählen Sie **Erstellen** aus.

1. Führen Sie die Konfiguration basierend auf Details aus der [Entwicklerkonsole](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/). Zum Beispiel:

   ![OAuth-Konfiguration erstellen](assets/ims-create-oauth-configuration.png)

1. **Speichern** Sie Ihre Änderungen.

## Migration einer vorhandenen JWT-Konfiguration zu einer OAuth-Konfiguration {#migrating-existing-JWT-configuration-to-oauth}

So migrieren Sie eine vorhandene Adobe IMS-Integration basierend auf JWT-Anmeldeinformationen:

>[!NOTE]
>
>Dieses Beispiel zeigt eine IMS-Konfiguration für Launch.

1. Navigieren Sie in AEM zu **Instrumente**, **Sicherheit**, **Adobe IMS-Integration**.

1. Wählen Sie die zu migrierende JWT-Konfiguration aus. JWT-Konfigurationen sind mit einer Warnung gekennzeichnet **JWT-Anmeldeinformationen (nicht mehr unterstützt)**.

1. Auswählen **Eigenschaften**:

   ![JWT-Konfiguration auswählen](assets/ims-migrate-jwt-select-configuration.png)

1. Die Konfiguration wird als schreibgeschützt geöffnet:

   ![Konfigurationseigenschaften - schreibgeschützt](assets/ims-migrate-jwt-properties-read-only.png)

1. Auswählen **OAuth** aus dem **Authentifizierungstyp** Dropdown-Liste:

   ![Authentifizierungstyp auswählen](assets/ims-migrate-jwt-authentication-type.png)

1. Die verfügbaren Eigenschaften werden aktualisiert. Verwenden Sie Details aus der Developer Console, um sie abzuschließen:

   ![Vollständige OAuth-Details](assets/ims-migrate-jwt-complete-oauth-details.png)

1. Verwendung **Speichern und schließen** um Ihre Aktualisierungen beizubehalten.
Wenn Sie zur Konsole zurückkehren, wird die **JWT-Anmeldeinformationen (nicht mehr unterstützt)** -Warnhinweis entfernt.