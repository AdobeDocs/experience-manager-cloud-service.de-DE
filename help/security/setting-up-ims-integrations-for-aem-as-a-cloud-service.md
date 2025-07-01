---
title: Einrichten von IMS-Integrationen für AEM as a Cloud Service
description: Erfahren Sie, wie Sie eine IMS-Integration für AEM as a Cloud Service einrichten
exl-id: 72fb1ea1-355c-4faa-a733-77bc7de75ed5
feature: Security
role: Admin
source-git-commit: 00a05b3bdc1a689947c1507847da99b54c94dcac
workflow-type: ht
source-wordcount: '386'
ht-degree: 100%

---

# Einrichten von IMS-Integrationen für AEM as a Cloud Service {#setting-up-ims-integrations-for-aemaacs}

>[!NOTE]
>
>Automatisch bereitgestellte JWT-Konfigurationen sollten nicht manuell migriert werden, da sie automatisch von Adobe verarbeitet werden.

Adobe Experience Manager (AEM) as a Cloud Service kann mit vielen anderen Adobe-Lösungen integriert werden. Zum Beispiel Adobe Target, Adobe Analytics und vielen weiteren.

Die Integrationen verwenden eine IMS-Integration, die mit S2S OAuth konfiguriert ist.

* Nach der Erstellung:

   * [Anmeldedaten in der Developer Console](#credentials-in-the-developer-console)

* Anschließend können Sie:

   * Eine (neue) [OAuth-Konfiguration](#creating-oauth-configuration) erstellen

   * [Eine vorhandene JWT-Konfiguration in eine OAuth-Konfiguration migrieren](#migrating-existing-JWT-configuration-to-oauth)

>[!CAUTION]
>
>Zuvor wurden Konfigurationen mit [JWT-Anmeldedaten erstellt, die in der Adobe Developer Console nicht mehr unterstützt werden](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md).
>
>Solche Konfigurationen können nicht mehr erstellt oder aktualisiert werden, können aber zu OAuth-Konfigurationen migriert werden.

## Anmeldedaten in der Developer Console {#credentials-in-the-developer-console}

Als ersten Schritt müssen Sie die OAuth-Anmeldedaten in der Adobe Developer Console konfigurieren.

Weitere Informationen dazu finden Sie in der Dokumentation zur Developer Console, abhängig von Ihren Anforderungen:

* Übersicht:

   * [Server-zu-Server-Authentifizierung](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

* Erstellen von neuen OAuth-Anmeldedaten:

   * [OAuth-Implementierungshandbuch für Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)

* Migration von vorhandenen JWT-Anmeldedaten zu OAuth-Anmeldedaten:

   * [Migration von JWT-Anmeldedaten (Service Account) zu OAuth-Server-zu-Server-Anmeldedaten](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)

Zum Beispiel:

![OAuth-Anmeldedaten in der Developer Console](assets/ims-configuration-developer-console.png)

## Erstellen einer OAuth-Konfiguration {#creating-oauth-configuration}

So erstellen Sie eine neue Adobe IMS-Integration mithilfe von OAuth:

1. Navigieren Sie in AEM zu **Tools** > **Sicherheit** > **Adobe IMS-Integration**.

1. Wählen Sie **Erstellen** aus.

1. Schließen Sie die Konfiguration basierend auf Details aus der [Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) ab. Zum Beispiel:

   ![Erstellen einer OAuth-Konfiguration](assets/ims-create-oauth-configuration.png)

1. **Speichern** Sie Ihre Änderungen.

## Migration einer vorhandenen JWT-Konfiguration zu einer OAuth-Konfiguration {#migrating-existing-JWT-configuration-to-oauth}

So migrieren Sie eine vorhandene Adobe IMS-Integration basierend auf JWT-Anmeldedaten:

>[!NOTE]
>
>Dieses Beispiel zeigt eine IMS-Konfiguration für Launch.

1. Navigieren Sie in AEM zu **Tools** > **Sicherheit** > **Adobe IMS-Integration**.

1. Wählen Sie die zu migrierende JWT-Konfiguration aus. JWT-Konfigurationen sind mit einer Warnung gekennzeichnet: **JWT-Anmeldedaten (nicht mehr unterstützt)**.

1. Wählen Sie **Eigenschaften** aus.

   ![Auswählen der JWT-Konfiguration](assets/ims-migrate-jwt-select-configuration.png)

1. Die Konfiguration wird als schreibgeschützt geöffnet:

   ![Konfigurationseigenschaften – Schreibgeschützt](assets/ims-migrate-jwt-properties-read-only.png)

1. Wählen Sie **OAuth** aus der Dropdown-Liste **Authentifizierungstyp** aus:

   ![Auswählen des Authentifizierungstyps](assets/ims-migrate-jwt-authentication-type.png)

1. Die verfügbaren Eigenschaften werden aktualisiert. Verwenden Sie Details aus der Developer Console, um sie zu vervollständigen:

   ![Vervollständigen von OAuth-Details](assets/ims-migrate-jwt-complete-oauth-details.png)

1. Verwenden Sie **Speichern und schließen**, um Ihre Aktualisierungen beizubehalten.
Wenn Sie zur Konsole zurückkehren, ist die Warnung **JWT-Anmeldedaten (nicht mehr unterstützt)** verschwunden.
