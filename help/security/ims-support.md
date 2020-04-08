---
title: IMS-Unterstützung für Adobe Experience Manager als Cloud-Dienst
description: IMS-Unterstützung für Adobe Experience Manager als Cloud-Dienst
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# IMS Support for Adobe Experience Manager as a Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Einführung {#introduction}

* AEM als Cloud-Dienst umfasst die Unterstützung der Admin-Konsole für AEM-Instanzen und für die kurze Authentifizierung durch das Adobe Identity Management System (IMS).
* Die Admin-Konsole ermöglicht Administratoren die zentrale Verwaltung aller Experience Cloud-Benutzer.
* Benutzer und Gruppen können Produktinstanzen zugewiesen werden, die mit AEM als Cloud-Dienstinstanzen verknüpft sind, sodass sie sich bei dieser Instanz anmelden können.

## Wichtige Highlights {#key-highlights}

AEM als Cloud-Service-Angebot unterstützt nur die IMS-Authentifizierung von Autoren-, Admin- und Dev-Benutzern. Die Unterstützung externer Endbenutzer von Kundensites wie Site-Besuchern wird dadurch nicht Angebot.

* Die Admin-Konsole repräsentiert Kunden als IMS-Organisationen, Autoren- und Veröffentlichungsinstanzen in einer Umgebung als Produktkontextinstanzen. Dadurch können System- und Produktadministratoren den Zugriff auf Instanzen verwalten.
* Mit den Produkt-Profilen in der Admin-Konsole wird festgelegt, auf welche Instanzen ein Benutzer zugreifen kann.
* Kunden können ihre eigenen SAML 2-kompatiblen Identitätsanbieter (kurz IDP) für Single-Sign-On verwenden.
* Es werden nur Enterprise IDs oder Federated IDs für Single-Sign-On des Kunden unterstützt, keine persönlichen Adobe IDs.

## Architektur {#architecture}

Die IMS-Authentifizierung funktioniert mit dem OAuth-Protokoll zwischen AEM und dem Adobe IMS-Endpunkt. Sobald ein Benutzer zu IMS hinzugefügt wurde und über eine Adobe-Identität verfügt, kann er sich mit den IMS-Anmeldeinformationen beim AEM-Autorendienst anmelden.

Der Anmeldefluss des Benutzers wird unten angezeigt, der Benutzer wird zu IMS und optional zum Kunden-IDP für die einmalige Anmeldung umgeleitet und dann zurück zu AEM weitergeleitet.

![IMS-Architektur](/help/security/assets/ims1.png)

## Einrichtung {#how-to-set-up}

### Onboarding Organizations to Adobe Admin Console {#onboarding-orgs-to-adobe-admin-console}

Der Kunde, der sich bei der Adobe Admin Console anmeldet, ist eine Voraussetzung für die Verwendung von Adobe IMS für die AEM-Authentifizierung.

Als ersten Schritt müssen Kunden eine Organisation in Adobe IMS bereitstellen. Adobe Enterprise-Kunden werden als IMS-Organisationen in der [Adobe Admin-Konsole](https://helpx.adobe.com/de/enterprise/using/admin-console.html) dargestellt. Dies ist das Portal, das Adobe-Kunden verwenden, um ihre Produktberechtigungen für ihre Benutzer und Gruppen zu verwalten.

AEM-Kunden sollten bereits über eine Organisation verfügen. Im Rahmen der IMS-Bereitstellung werden die Kundeninstanzen in der Admin-Konsole zur Verwaltung von Benutzerberechtigungen und zum Zugriff bereitgestellt.

Sobald ein Kunde als IMS-Organisation existiert, muss er sein System wie folgt konfigurieren:

![IMS-Einstieg](/help/security/assets/ims2.png)

1. Der festgelegte Systemadministrator erhält eine Einladung zur Anmeldung bei Cloud Manager. Nach der Anmeldung beim Cloud Manager können die Systemadministratoren entweder AEM-Programm und -Umgebung bereitstellen oder für administrative Aufgaben zur Admin-Konsole navigieren.
1. Der Systemadministrator beansprucht eine Domäne, um das Eigentum an der jeweiligen Domäne zu bestätigen (z. B. acme.com)
1. Der Systemadministrator richtet Benutzerverzeichnisse ein
1. Der Systemadministrator führt die IDP-Konfiguration in der Admin-Konsole aus, um Single-Sign-On einzurichten.
1. Der AEM-Administrator verwaltet die lokalen Gruppen und Berechtigungen wie gewohnt.

Die Grundlagen des Adobe-Identitätsmanagements einschließlich der IDP-Konfiguration werden [hier](https://helpx.adobe.com/de/enterprise/using/set-up-identity.html)behandelt.

Die Verwendung von Enterprise Administration und Admin Console wird [hier](https://helpx.adobe.com/de/enterprise/managing/user-guide.html)behandelt.

### Onboarding Users in Admin Console {#onboarding-users-in-admin-console}

Es gibt drei Möglichkeiten, Benutzer an Bord zu nehmen, je nach Größe des Kunden und dessen Präferenz: Erstellen Sie Benutzer manuell in der Admin-Konsole, laden Sie eine CSV-Datei hoch oder synchronisieren Sie Benutzer aus dem Unternehmensverzeichnis des Kunden.

**Manuelles Hinzufügen über die Admin Console-Benutzeroberfläche**

Benutzer und Gruppen können manuell in der Admin Console-Benutzeroberfläche erstellt werden. Diese Methode kann verwendet werden, wenn nicht viele Benutzer zu verwalten sind. Beispielsweise weniger als 50 AEM-Benutzer oder wenn Sie diese Methode bereits zur Verwaltung anderer Adobe-Produkte wie Analytics-, Zielgruppe- oder Creative Cloud-Anwendungen verwenden.

![Benutzeranmeldung](/help/security/assets/ims3.png)

**Datei-Upload in der Admin-Konsole**

For easy handling of user creation, a `.csv` file can be uploaded for adding users in bulk.

![Datei-Upload](/help/security/assets/ims4.png)

**Tool zur Benutzersynchronisierung**

Mit User Sync Tool (UST kurz) können unsere Unternehmenskunden Adobe-Benutzer mithilfe von Active Directory erstellen und verwalten. Dies funktioniert auch bei anderen getesteten OpenLDAP-Ordnerdiensten. Die Zielgruppe-Benutzer sind IT-Identitätsadministratoren (Enterprise Directory oder System Admins), die das Tool installieren und konfigurieren können. Das Open-Source-Tool ist anpassbar, sodass Sie es an Ihre eigenen Anforderungen anpassen können.

Wenn die Benutzersynchronisierung ausgeführt wird, ruft sie eine Liste von Benutzern aus dem Active Directory des Unternehmens ab und vergleicht sie mit der Liste der Benutzer in der Admin-Konsole.  Anschließend ruft es die Adobe User Management-API auf, damit die Admin Console mit dem Verzeichnis der Organisation synchronisiert wird. Der Änderungsfluss ist nur eine Möglichkeit. Änderungen, die in der Admin-Konsole vorgenommen wurden, werden nicht in den Ordner verschoben.

Das Tool ermöglicht es dem Systemadministrator, Benutzergruppen im Kundenverzeichnis der Produktkonfiguration und Benutzergruppen in der Admin-Konsole zuzuordnen.

To set up User Sync, the organization needs to create a set of credentials in the same way they would use the [User Management API](https://www.adobe.io/apis/experienceplatform/umapi-new.html).

![Tool zur Benutzersynchronisierung](/help/security/assets/ims5.png)

User Sync Tool is distributed through the Adobe Github repository [at this location](https://github.com/adobe-apiplatform/user-sync.py/releases/latest).

>[!NOTE]
>
> Eine Vorabversion **2.4RC1** ist mit Unterstützung der dynamischen Gruppenbildung verfügbar und kann [hier](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1)gefunden werden.

Die wichtigsten Funktionen dieser Version sind die Möglichkeit, neue LDAP-Gruppen für die Benutzermitgliedschaft in der Admin Console dynamisch zuzuordnen und dynamische Benutzergruppen zu erstellen.

Weitere Informationen zu den neuen Gruppenfunktionen finden Sie [hier](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options).

**Dokumentation zur Benutzersynchronisierung**

Weitere Informationen finden Sie in der [UST-Dokumentation](https://adobe-apiplatform.github.io/user-sync.py/en/) .

The User Sync Tool needs to register as an Adobe I/O client UMAPI using the procedure [here](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html).

Adobe I/O Console Documentation can be found [here](https://www.adobe.io/apis/cloudplatform/console.html).

The User Management API that is used by the User Sync Tool is covered [here](https://www.adobe.io/apis/cloudplatform/umapi-new.html).

## Konfiguration von Adobe Experience as a Cloud Service {#aem-configuration}

>[!NOTE]
>
>Die erforderliche AEM IMS-Konfiguration wird automatisch konfiguriert, wenn die AEM-Umgebung und -Instanzen bereitgestellt werden. Der Administrator kann ihn jedoch entsprechend seinen Anforderungen nach der [hier](/help/implementing/deploying/overview.md)beschriebenen Methode ändern.

Die erforderliche AEM IMS-Konfiguration wird automatisch konfiguriert, wenn die AEM-Umgebung und -Instanzen bereitgestellt werden.  Kundenadministratoren können einen Teil der Konfiguration gemäß ihren Anforderungen ändern

Der allgemeine Ansatz besteht darin, Adobe IMS als OAuth-Anbieter zu konfigurieren. Der **Standard-Synchronisations-Handler für Apache Jackrabbit Oak** kann wie bei der LDAP-Synchronisierung geändert werden.

Nachfolgend sind die wichtigsten OSGI-Konfigurationen aufgeführt, die geändert werden müssen, um Eigenschaften wie die automatische Mitgliedschaft für Benutzer oder Gruppenzuordnungen zu ändern.

<!-- Arun to provide list of osgi configs -->

## Verwendung {#how-to-use}

### Verwalten von Produkten und Benutzerzugriff in der Admin Console {#managing-products-and-user-access-in-admin-console}

Wenn sich der Produktadministrator bei der Admin-Konsole anmeldet, sehen sie mehrere Instanzen des AEM Managed Services-Produktkontexts wie unten dargestellt:

![Instanzanmeldung](/help/security/assets/ims6.png)

In diesem Beispiel umfasst die Organisation **AEM-MS-Onboard** 32 Instanzen, die verschiedene Topologien und Umgebungen wie „Stage“ oder „Prod“ umfassen.

![Instanzen login2](/help/security/assets/ims7.png)

Unter jeder Produktkontextinstanz werden zugehörige Produkt-Profil angezeigt. Mit diesen Profilen wird Benutzern und Gruppen der Zugriff mit den erforderlichen Berechtigungen zugewiesen.

Das Profil **Administrator_xxx** wird verwendet, um Administratorberechtigungen in der zugehörigen AEM-Instanz zu gewähren, während das Profil **User_xxx** zum Hinzufügen regulärer Benutzer verwendet wird.

Alle Benutzer und Gruppen, die im Rahmen dieses Profils hinzugefügt werden, können sich wie im folgenden Beispiel bei dieser Instanz anmelden:

![Produkt-Profil](/help/security/assets/ims8.png)

### Anmelden bei Adobe Experience Manager als Cloud-Dienst (#login-to-aem)

**Anmeldung beim lokalen Administrator**

AEM kann weiterhin lokale Anmeldungen für Admin-Benutzer unterstützen. Auf dem Anmeldebildschirm können Sie sich lokal anmelden:

![Lokale Anmeldung](/help/security/assets/ims9.png)

<!-- the above image needs to be updated for skyline -->

**IMS-basierte Anmeldung**

Für andere Benutzer kann die IMS-basierte Anmeldung verwendet werden, sobald IMS für die Instanz konfiguriert wurde. Benutzer klicken wie unten gezeigt auf die Schaltfläche Mit Adobe anmelden:

![IMS-Anmeldung](/help/security/assets/ims10.png)

Sie werden dann zum IMS-Anmeldebildschirm umgeleitet und müssen ihre Anmeldeinformationen eingeben:

![IMS-Anmeldung2](/help/security/assets/ims11.png)

![IMS-Anmeldung3](/help/security/assets/ims12.png)

Wenn während der Ersteinrichtung der Admin Console Federated IDP konfiguriert wurde, wird der Benutzer zum Kunden-IDP für die einmalige Anmeldung weitergeleitet:

![IMS-Anmeldung4](/help/security/assets/ims13.png)

Sobald die Authentifizierung abgeschlossen ist, wird der Benutzer zurück zu AEM weitergeleitet und angemeldet:

![IMS-Anmeldung5](/help/security/assets/ims14.png)

### Verwalten von Berechtigungen und Zugriffssteuerungslisten in Adobe Experience Manager als Cloud-Dienst {#managing-permissions-in-aem}

Die Zugriffssteuerungslisten und Berechtigungen werden weiterhin in AEM verwaltet. Die vom IMS synchronisierten Benutzergruppen können lokalen Gruppen zugewiesen werden, in denen ACLs und Berechtigungen definiert sind.

Im Beispiel unten werden der lokalen Gruppe **Dam_Users** synchronisierte Gruppen hinzugefügt.

Der Benutzer ist Teil der folgenden Gruppen in IMS:

![ACL1](/help/security/assets/ims15.png)

Wenn sich der Benutzer anmeldet, werden die Gruppenmitgliedschaften wie unten dargestellt synchronisiert:

![ACL2](/help/security/assets/ims16.png)

In AEM können die mit IMS synchronisierten Benutzergruppen als Mitglieder zu bestehenden lokalen Gruppen wie **DAM-Benutzern** hinzugefügt werden.

![ACL3](/help/security/assets/ims17.png)

Wie unten gezeigt, erbt die Gruppe **AEM-GRP_008** die Berechtigungen von **DAM-Benutzern**. So können Berechtigungen für synchronisierte Gruppen effektiv verwaltet werden. Diese Option wird häufig auch bei der LDAP-basierten Authentifizierungsmethode verwendet.

![ACL3](/help/security/assets/ims18.png)