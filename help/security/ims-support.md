---
title: IMS-Unterstützung für Adobe Experience Manager as a Cloud Service
description: IMS-Unterstützung für Adobe Experience Manager as a Cloud Service
exl-id: fb563dbd-a761-4d83-9da1-58f8e462b383
translation-type: tm+mt
source-git-commit: 75071cb1793b9b670ebbc029bf9fb41f4de119f9
workflow-type: tm+mt
source-wordcount: '2009'
ht-degree: 92%

---

# IMS-Unterstützung für Adobe Experience Manager as a Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Einführung {#introduction}

* AEM as a Cloud Service umfasst die Unterstützung der Admin Console für AEM-Instanzen und die auf dem Adobe Identity Management System (kurz IMS) basierende Authentifizierung.
* Die Admin Console ermöglicht Administratoren die zentrale Verwaltung aller Experience Cloud-Benutzer.
* Benutzer und Gruppen können Produktprofilen zugeordnet werden, die mit AEM as a Cloud Service-Instanzen verknüpft sind, sodass sie sich bei dieser Instanz anmelden können.

>[!TIP]
>
>In unserem Experience League-Kurs [Zugriff auf AEM für Administratoren konfigurieren](https://experienceleague.adobe.com/?recommended=ExperienceManager-A-1-2020.1.aem) erhalten Sie eine Einführung dazu, wie sich Benutzer mithilfe von Adobe IMS als Cloud Service authentifizieren und wie Adobe IMS-Benutzer, -Benutzergruppen und -Produkt-Profil verwendet werden, um den Zugriff auf AEM und deren Funktionen zu steuern. Adobe ID erforderlich.

## Wichtige Highlights {#key-highlights}

AEM as a Cloud Service bietet IMS-Authentifizierungsunterstützung nur für Autoren-, Admin- und Entwicklungsbenutzer. Es bietet keine Unterstützung für externe Endbenutzer von Kunden-Sites wie Site-Besucher.

* Die Admin Console repräsentiert Kunden als IMS-Organisationen, Autoren- und Veröffentlichungsinstanzen in einer Umgebung als Produktkontextinstanzen. Dadurch können System- und Produktadministratoren den Zugriff auf Instanzen verwalten.
* Produktprofile in der Admin Console legen fest, auf welche Instanzen ein Benutzer zugreifen kann.
* Kunden können ihre eigenen SAML 2-kompatiblen Identitätsanbieter (kurz IDP) für Single-Sign-On verwenden.
* Nur Enterprise IDs oder Federated IDs (für Single Sign-On beim Kunden) werden unterstützt, jedoch keine persönlichen Adobe IDs.

## Architektur {#architecture}

Die IMS-Authentifizierung verwendet das OAuth-Protokoll zwischen AEM und dem Adobe IMS-Endpunkt. Wenn Benutzer zu IMS hinzugefügt wurden und eine Adobe ID haben, können sie sich mit den IMS-Anmeldeinformationen bei AEM-Autorendiensten anmelden.

Die Schritte zur Benutzeranmeldung werden unten gezeigt. Der Benutzer wird zu IMS und optional zum Kunden-IDP für SSO und anschließend zurück zu AEM weitergeleitet.

![IMS-Architektur](/help/security/assets/ims1.png)

## Einrichtung {#how-to-set-up}

### Onboarding von Organisationen zur Admin Console {#onboarding-orgs-to-adobe-admin-console}

Das Onboarding von Kunden zur Adobe Admin Console ist eine Voraussetzung für die Verwendung von Adobe IMS zur AEM-Authentifizierung.

Als ersten Schritt müssen Kunden eine Organisation in Adobe IMS bereitstellen. Adobe Enterprise-Kunden werden in der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) als IMS-Organisationen angezeigt. Dies ist das Portal, das Adobe-Kunden verwenden, um ihre Produktberechtigungen für ihre Benutzer und Gruppen zu verwalten.

Für AEM-Kunden sollte bereits eine Organisation bereitgestellt sein. Im Rahmen der IMS-Bereitstellung werden die Kundeninstanzen zur Verwaltung der Benutzerberechtigungen und -zugriffe in der Admin Console bereitgestellt.

Sobald ein Kunde als IMS-Organisation existiert, muss er sein System wie folgt konfigurieren:

![IMS-Onboarding](/help/security/assets/ims2.png)

1. Der festgelegte Systemadministrator erhält eine Einladung zur Anmeldung bei Cloud Manager. Nach der Anmeldung bei Cloud Manager können die Systemadministratoren entweder AEM-Programme und -Umgebungen bereitstellen oder für Verwaltungsaufgaben zur Admin Console navigieren.
1. Der Systemadministrator beansprucht eine Domäne, um die Eigentümerschaft der Domäne zu bestätigen (beispielsweise acme.com).
1. Der Systemadministrator richtet die Benutzerverzeichnisse ein.
1. Der Systemadministrator führt die IDP-Konfiguration in der Admin Console aus, um Single-Sign-On einzurichten.
1. Der AEM-Administrator verwaltet die lokalen Gruppen, Berechtigungen und Zugriffsrechte wie gewohnt.

Die Grundlagen von Adobe Identity Management einschließlich der IDP-Konfiguration werden [hier](https://helpx.adobe.com/de/enterprise/using/set-up-identity.html) behandelt.

Die Verwaltung von Unternehmen und die Verwendung der Admin Console werden [hier](https://helpx.adobe.com/de/enterprise/managing/user-guide.html) behandelt.

### Onboarding von Benutzern zur Admin Console {#onboarding-users-in-admin-console}

Je nach der Größe des Kunden und den bevorzugten Einstellungen gibt es drei Möglichkeiten, Benutzer hinzuzufügen: Manuelles Erstellen von Benutzern in der Admin Console, Hochladen einer .csv-Datei oder Synchronisieren von Benutzern aus dem Active Directory des Unternehmens des Kunden.

**Manuelles Hinzufügen über die Admin Console-Benutzeroberfläche**

Benutzer und Gruppen können manuell in der Admin Console-Benutzeroberfläche erstellt werden. Diese Methode kann verwendet werden, wenn nur wenige Benutzer verwaltet werden müssen. Zum Beispiel bei weniger als 50 AEM-Benutzern oder wenn Sie die Methode bereits zur Verwaltung anderer Adobe-Produkte wie Analytics, Target oder Creative Cloud-Programmen verwenden.

![Onboarding von Benutzern](/help/security/assets/ims3.png)

**Datei-Upload in der Admin Console-Benutzeroberfläche**

Zur einfachen Handhabung der Benutzererstellung können Sie eine `.csv`-Datei hochladen, um eine große Anzahl von Benutzern hinzuzufügen.

![Datei-Upload](/help/security/assets/ims4.png)

**Tool zur Benutzersynchronisierung**

Mit dem Tool zur Benutzersynchronisierung (kurz UST) können unsere Unternehmenskunden Adobe-Benutzer mithilfe von Active Directory erstellen und verwalten. Dies funktioniert auch für andere getestete OpenLDAP-Verzeichnisdienste. Die Zielbenutzer sind IT-Identitätsadministratoren (Enterprise-Verzeichnis- oder Systemadministratoren), die das Tool installieren und konfigurieren können. Das Open Source-Tool ist anpassbar, sodass Sie das Tool an die eigenen Anforderungen anpassen können.

Wenn die Benutzersynchronisierung ausgeführt wird, ruft das Tool eine Liste der Benutzer aus dem Active Directory des Unternehmens ab und vergleicht sie mit der Liste der Benutzer in der Admin Console.  Anschließend ruft es die Adobe User Management-API auf, damit die Admin Console mit dem Verzeichnis der Organisation synchronisiert wird. Der Änderungsfluss ist einseitig. Änderungen, die in der Admin Console vorgenommen wurden, werden nicht in das Verzeichnis übertragen.

Das Tool ermöglicht es dem Systemadministrator, Benutzergruppen im Kundenverzeichnis mit der Produktkonfiguration und den Benutzergruppen in der Admin Console abzubilden.

Um die Benutzersynchronisierung einzurichten, muss die Organisation Anmeldeinformationen erstellen. Die Schritte hierfür sind dieselben wie bei der [User Management-API](https://www.adobe.io/apis/experienceplatform/umapi-new.html).

![Tool zur Benutzersynchronisierung](/help/security/assets/ims5.png)

Das Tool zur Benutzersynchronisierung steht über das Adobe Github-Repository [an diesem Speicherort](https://github.com/adobe-apiplatform/user-sync.py/releases/latest) zur Verfügung.

>[!NOTE]
>
>Eine Vorabversion **2.4RC1** ist mit Unterstützung der dynamischen Gruppenbildung verfügbar und kann [hier](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1) gefunden werden.

Die wichtigsten Funktionen dieser Version sind die Möglichkeit, neue LDAP-Gruppen für die Benutzermitgliedschaft in der Admin Console dynamisch zuzuordnen und dynamische Benutzergruppen zu erstellen.

Weitere Informationen zu den neuen Gruppenfunktionen finden Sie [hier](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options).

**Dokumentation zur Benutzersynchronisierung**

Weitere Informationen finden Sie in der [UST-Dokumentation](https://adobe-apiplatform.github.io/user-sync.py/en/).

Das Tool zur Benutzersynchronisierung muss mit dem Verfahren [hier](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html) als Adobe I/O-Client-UMAPI registriert werden.

Die Dokumentation zur Adobe I/O-Konsole finden Sie [hier](https://www.adobe.io/apis/cloudplatform/console.html).

Die User Management-API, die vom Tool zur Benutzersynchronisierung verwendet wird, wird [hier](https://www.adobe.io/apis/cloudplatform/umapi-new.html) erläutert.

## Konfiguration von Adobe Experience as a Cloud Service {#aem-configuration}

>[!NOTE]
>
>Die erforderliche AEM-IMS-Konfiguration wird automatisch konfiguriert, wenn die AEM-Umgebungen und -Instanzen bereitgestellt werden. Der Administrator kann sie jedoch entsprechend seinen Anforderungen nach der [hier](/help/implementing/deploying/overview.md) beschriebenen Methode ändern.

Die erforderliche AEM-IMS-Konfiguration wird automatisch konfiguriert, wenn die AEM-Umgebungen und -Instanzen bereitgestellt werden.  Kundenadministratoren können einen Teil der Konfiguration gemäß ihren Anforderungen ändern.

Der allgemeine Ansatz besteht darin, Adobe IMS als OAuth-Anbieter zu konfigurieren. Der **Apache Jackrabbit Oak Standard Sync Handler** kann wie bei der LDAP-Synchronisierung geändert werden.

Nachfolgend sind die wichtigsten OSGI-Konfigurationen aufgeführt, die geändert werden müssen, um Eigenschaften wie die automatische Mitgliedschaft für Benutzer oder Gruppenzuordnungen zu ändern.

<!-- Arun to provide list of osgi configs -->

## Verwendung {#how-to-use}

### Verwalten von Produkten und Benutzerzugriff in der Admin Console {#managing-products-and-user-access-in-admin-console}

Wenn sich der Produktadministrator bei der Admin Console anmeldet, werden mehrere Instanzen des AEM als Produktkontext des Cloud Service angezeigt, wie unten dargestellt. Wählen Sie beispielsweise eines der Produkte auf der Seite **Übersicht** aus:

![Anmeldung von Instanzen](/help/security/assets/ims6.png)

Es wird eine Liste der vorhandenen Instanzen angezeigt:

![Anmeldung von Instanzen2](/help/security/assets/ims7.png)

Unter jeder Produktkontextinstanz gibt es Instanzen, die die Authoring- oder Veröffentlichungsdienste über Produktions-, Stage- oder Entwicklungs-Umgebung verteilen. Jede Instanz wird Produkt- oder Cloud Manager-Profilen zugeordnet. Mit diesen Profilen wird Benutzern und Gruppen mit den erforderlichen Berechtigungen der Zugriff zugewiesen.

Das Profil **Administrator_xxx** wird verwendet, um Administratorberechtigungen in der zugehörigen AEM-Instanz zu gewähren, während das Profil **User_xxx** zum Hinzufügen regulärer Benutzer verwendet wird.

Alle unter diesem Produktprofil hinzugefügten Benutzer und Gruppen können sich wie im Beispiel unten gezeigt bei dieser Instanz anmelden:

![Produktprofil](/help/security/assets/ims8.png)

### Anmelden bei Adobe Experience Manager as a Cloud Service {#logging-in-to-aem}

**Lokale Administratoranmeldung**

AEM kann lokale Anmeldungen für Administratoren weiterhin unterstützen. Der Anmeldebildschirm bietet eine Option zur lokalen Anmeldung:

![Lokale Anmeldung](/help/security/assets/ims9.png)

<!-- the above image needs to be updated for skyline -->

**IMS-basierte Anmeldung**

Für andere Benutzer kann die IMS-basierte Anmeldung verwendet werden, sobald IMS für die Instanz konfiguriert wurde. Benutzer klicken wie unten gezeigt auf die Schaltfläche „Mit Adobe anmelden“:

![IMS-Anmeldung](/help/security/assets/ims10.png)


>[!NOTE]
>
>Jeder Benutzer, der in IMS erstellt wurde, kann mit einer Adobe ID oder einer Federated ID erstellt werden. Wenn ein Benutzer mit der Adobe ID eingerichtet wird, wird er mithilfe des Identitätsanbieters seiner Firma für die Anmeldung authentifiziert.

Anschließend werden sie zum IMS-Anmeldebildschirm weitergeleitet und müssen ihre Anmeldeinformationen eingeben:

![IMS Login2](/help/security/assets/ims11.png)

![IMS Login3](/help/security/assets/ims12.png)

Wenn während der Ersteinrichtung der Admin Console Federated IDP konfiguriert wurde, wird der Benutzer zum Kunden-IDP für die einmalige Anmeldung weitergeleitet:

![IMS Login4](/help/security/assets/ims13.png)

Sobald die Authentifizierung abgeschlossen ist, wird der Benutzer zurück zu AEM weitergeleitet und angemeldet:

![IMS Login5](/help/security/assets/ims14.png)

### Verwalten von Berechtigungen und Zugriffssteuerungslisten (ACLs) in Adobe Experience Manager as a Cloud Service {#managing-permissions-in-aem}

Die Zugriffssteuerungslisten (ACLs) und Berechtigungen werden weiterhin in AEM verwaltet. Die vom IMS synchronisierten Benutzergruppen können lokalen Gruppen zugewiesen werden, in denen ACLs und Berechtigungen definiert sind.

Im Beispiel unten werden der lokalen Gruppe **Dam_Users** synchronisierte Gruppen hinzugefügt.

Der Benutzer ist Teil der folgenden Gruppen in IMS:

![ACL1](/help/security/assets/ims15.png)

Wenn sich der Benutzer anmeldet, werden die Gruppenmitgliedschaften wie unten dargestellt synchronisiert:

![ACL2](/help/security/assets/ims16.png)

In AEM können die aus IMS synchronisierten Benutzergruppen vorhandenen lokalen Gruppen (z. B. **DAM-Benutzer**) als Mitglieder hinzugefügt werden.

![ACL3](/help/security/assets/ims17.png)

Wie unten gezeigt, erbt die Gruppe **AEM-GRP_008** die Berechtigungen und Rechte von **DAM-Benutzer**. Dies ist eine effektive Möglichkeit zur Verwaltung von Berechtigungen für synchronisierte Gruppen und wird häufig auch in der LDAP-basierten Authentifizierungsmethode verwendet.

![ACL3](/help/security/assets/ims18.png)


### Zugriff auf Cloud Manager {#accessing-cloud-manager}

Um auf Cloud Manager oder AEM as a Cloud Service-Umgebungen zugreifen zu können, müssen Sie Profilen des Cloud Manager-Produkts zugewiesen sein.

Unter Rollendefinitionen finden Sie weitere Informationen zu Rollen von Benutzern, die die Verfügbarkeit bestimmter Funktionen in Cloud Manager steuern.

>[!NOTE]
>Cloud Manager verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Informationen zu den einzelnen Rollen mit den entsprechenden Berechtigungen, vorkonfigurierten Aufgaben oder dem Berechtigungen, die mit den einzelnen Rollen verknüpft sind, finden Sie unter [Rollenbasierte Berechtigungen](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/onboarding/what-is-required/role-based-permissions.html).

**Schritte zum Hinzufügen eines Benutzers**

1. Fügen Sie einem bestimmten Profil einen Benutzer hinzu, entweder über den Bildschirm eines vorhandenen Benutzers oder über einen Bildschirm für neue Benutzer.

1. Sie können einen Benutzer auch über den Bildschirm **Übersicht** hinzufügen, wie in der folgenden Abbildung dargestellt.

   ![ACL3](/help/security/assets/ims23.png)

   >[!NOTE]
   >Sie können einem Benutzer mehr als ein Profil zuweisen, wie in der folgenden Abbildung dargestellt.

   ![ACL3](/help/security/assets/ims22.png)


1. Nachdem Sie dem entsprechenden Profil hinzugefügt wurden, sollten Sie über [Adobe Experience Cloud](http://my.cloudmanager.adobe.com) oben rechts in der Benutzeroberfläche auf die entsprechenden Mandanten in Cloud Manager zugreifen können.


### Zugriff auf eine Instanz in AEM as a Cloud Service {#accessing-instance-cloud-service}

>[!IMPORTANT]
>Die im vorherigen Abschnitt erwähnten Schritte müssen bereits abgeschlossen sein, bevor Sie Zugriff auf eine Instanz in AEM as a Cloud Service erhalten.

Um auf eine AEM-Instanz in der **Admin Console** zugreifen zu können, sollten Sie das Cloud Manager-Programm und die Umgebungen innerhalb des Programms in der Produktliste in der **Admin Console** ansehen.

Im folgenden Screenshot sehen Sie beispielsweise zwei verfügbare Umgebungen: *dev author* und *publish*.

![ACL3](/help/security/assets/ims19.png)

Um Zugriff auf AEM-Instanzen zu erhalten, muss der Benutzer einer Gruppe des entsprechenden Cloud Service-Produkts hinzugefügt werden.

Jede Autoreninstanz verfügt über einen AEM-Administrator und ein AEM-Benutzerprofil und jede Veröffentlichungsinstanz über ein AEM-Profil. Sie können bei Bedarf weitere Profile hinzufügen.

Um Zugriff auf die AEM-Instanz auf Administratorebene zu erhalten, fügen Sie den Benutzer dem AEM-Administratorprofil für das jeweilige Produkt hinzu.
