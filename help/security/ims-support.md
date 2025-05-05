---
title: IMS-Unterstützung für Adobe Experience Manager as a Cloud Service
description: Unterstützung von Bildverwaltungssystemen für Adobe Experience Manager as a Cloud Service.
exl-id: fb563dbd-a761-4d83-9da1-58f8e462b383
feature: Security
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 100%

---

# IMS-Unterstützung für Adobe Experience Manager as a Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Einführung {#introduction}

* AEM as a Cloud Service umfasst die Unterstützung der Admin Console für AEM-Instanzen und die auf dem Adobe Identity Management System (kurz IMS) basierende Authentifizierung.
* Die Admin Console ermöglicht Administratoren die zentrale Verwaltung aller Experience Cloud-Benutzer.
* Benutzende und Gruppen können Produktprofilen zugeordnet werden, die mit einer AEM as a Cloud Service-Instanz verknüpft sind, sodass sie sich bei dieser Instanz anmelden können.

>[!TIP]
>
>Unter [Zugriff auf AEM für Admins konfigurieren](https://experienceleague.adobe.com/?lang=de&recommended=ExperienceManager-A-1-2020.1.aem?lang=de) finden Sie eine Einführung in die Authentifizierung von Benutzenden über Adobe IMS bei AEM as a Cloud Service. Erfahren Sie außerdem, wie Adobe IMS-Benutzende, Benutzergruppen und Produktprofile verwendet werden, um den Zugriff auf AEM und dessen Funktionen zu steuern. Adobe ID ist erforderlich.

## Wichtige Highlights {#key-highlights}

AEM as a Cloud Service bietet IMS-Authentifizierungsunterstützung nur für Autoren-, Admin- und Entwicklungsbenutzende. Es bietet keine Unterstützung für externe Endbenutzende von Kunden-Sites wie Site-Besuchende.

* Die Admin Console repräsentiert Kundinnen und Kunden als IMS-Organisationen, Authoring- und Publishing-Instanzen in einer Umgebung als Produktkontextinstanzen. Diese Darstellung ermöglicht es System- und Produktadmins, den Zugriff auf Instanzen zu verwalten.
* Produktprofile in der Admin Console legen fest, auf welche Instanzen Benutzende zugreifen können.
* Die Kundschaft kann ihre eigenen SAML 2-kompatiblen Identitätsanbieter (kurz IDP) für Single-Sign-On verwenden.
* Nur Enterprise IDs oder Federated IDs (für Single Sign-On bei der Kundschaft) werden unterstützt, jedoch keine persönlichen Adobe IDs.

## Architektur {#architecture}

Die IMS-Authentifizierung verwendet das OAuth-Protokoll zwischen AEM und dem Adobe IMS-Endpunkt. Wenn Benutzer zu IMS hinzugefügt wurden und eine Adobe ID haben, können sie sich mit den IMS-Anmeldeinformationen bei AEM-Autoren-Services anmelden.

Die Schritte zur Benutzeranmeldung werden unten gezeigt. Die Benutzerin bzw. der Benutzer wird zu IMS und optional zum Kunden-IDP für SSO und anschließend zurück zu AEM weitergeleitet.

![IMS-Architektur](/help/security/assets/ims1.png)

## Einrichtung {#how-to-set-up}

### Onboarding von Organisationen zur Admin Console {#onboarding-orgs-to-adobe-admin-console}

Das Onboarding von Kunden zur Adobe Admin Console ist eine Voraussetzung für die Verwendung von Adobe IMS zur AEM-Authentifizierung.

Der erste Schritt besteht darin, dass die Kundschaft über eine Organisation verfügt, die in Adobe IMS eingerichtet ist. Adobe Enterprise-Kundschaft wird in der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) als IMS-Organisation angezeigt. In diesem Bereich verwaltet Adobe-Kundschaft ihre Produktberechtigungen für ihre Benutzenden und Gruppen.

AEM-Kundschaft sollte bereits über eine Organisation verfügen, die bereitgestellt wird. Im Rahmen der IMS-Bereitstellung werden die Kundeninstanzen zur Verwaltung der Benutzerberechtigungen und -zugriffe in der Admin Console bereitgestellt.

Sobald die Kundschaft als IMS-Organisation existiert, muss sie ihr System wie folgt konfigurieren:

![IMS-Onboarding](/help/security/assets/ims2.png)

1. Die festgelegten Systemadmins erhalten eine Einladung zur Anmeldung bei Cloud Manager. Nach der Anmeldung bei Cloud Manager können die Systemadmins entweder AEM-Programme und -Umgebungen bereitstellen oder für Verwaltungsaufgaben zur Admin Console navigieren.
1. Der Systemadministrator bzw. die Systemadministratorin beansprucht eine Domain, um die Eigentümerschaft der Domain zu bestätigen (beispielsweise acme.com).
1. Der Systemadministrator bzw. die Systemadministratorin richtet die Benutzerverzeichnisse ein.
1. Die Systemadmins führen die IDP-Konfiguration in der Admin Console aus, um Single Sign-On einzurichten.
1. Die AEM-Admins verwalten die lokalen Gruppen, Berechtigungen und Zugriffsrechte wie gewohnt.

Die Adobe Identity Management-Grundlagen, einschließlich der IDP-Konfiguration, werden unter [Einrichten von Identität und Single Sign-on](https://helpx.adobe.com/de/enterprise/using/set-up-identity.html) behandelt.

Die Verwaltung von Unternehmen und die Verwendung der Admin Console werden unter [Willkommen beim Administratorhandbuch für Unternehmen und Teams](https://helpx.adobe.com/de/enterprise/admin-guide.html) erläutert.

### Onboarding von Benutzenden in der Admin Console {#onboarding-users-in-admin-console}

Es gibt drei Möglichkeiten, Benutzende zu integrieren. Jede Methode hängt von der Größe der Kundschaft und ihrer Präferenz ab. Sie können Benutzende in Admin Console manuell erstellen, eine CSV-Datei hochladen oder Benutzende aus dem Active Directory des Unternehmens synchronisieren.

**Manuelles Hinzufügen über die Admin Console-Benutzeroberfläche**

Benutzer und Gruppen können manuell in der Admin Console-Benutzeroberfläche erstellt werden. Diese Methode kann verwendet werden, wenn Sie nicht viele Benutzende zu verwalten haben. Zum Beispiel bei weniger als 50 AEM-Benutzerinnen bzw. -Benutzer oder wenn Sie die Methode bereits zur Verwaltung anderer Adobe-Produkte wie Analytics, Target oder Creative Cloud-Applikationen verwenden.

![Onboarding von Benutzern](/help/security/assets/ims3.png)

**Datei-Upload in der Admin Console-Benutzeroberfläche**

Zur einfachen Handhabung der Benutzererstellung können Sie eine `.csv`-Datei hochladen, um eine große Anzahl von Benutzern hinzuzufügen.

![Datei-Upload](/help/security/assets/ims4.png)

**Tool zur Benutzersynchronisierung**

Mit dem Tool zur Benutzersynchronisierung (kurz UST – User Sync Tool) können Adobe-Unternehmenskunden Adobe-Benutzende mithilfe von Active Directory erstellen und verwalten. UST funktioniert auch für andere getestete OpenLDAP-Verzeichnis-Services. Die Zielgruppe sind IT-Identitätsadmins (Enterprise Directory- oder Systemadmins), die in der Lage sind, das Tool zu installieren und zu konfigurieren. Das Open-Source-Tool ist anpassbar, sodass Sie das Tool an die eigenen Anforderungen anpassen können.

Wenn die Benutzersynchronisierung ausgeführt wird, ruft das Tool eine Liste der Benutzenden aus dem Active Directory des Unternehmens ab und vergleicht sie mit der Liste der Benutzenden in der Admin Console. Anschließend ruft es die Adobe User Management-API auf, damit die Admin Console mit dem Verzeichnis der Organisation synchronisiert wird. Der Änderungsfluss ist einseitig. Änderungen, die in der Admin Console vorgenommen wurden, werden nicht in das Verzeichnis übertragen.

Mit diesem Tool kann der Systemadmin die Benutzergruppen im Kundenverzeichnis mit der Produktkonfiguration und den Benutzergruppen in der Admin Console abgleichen.

Um die Benutzersynchronisierung einzurichten, muss die Organisation Anmeldeinformationen erstellen. Die Schritte hierfür sind dieselben wie bei der [User Management-API](https://developer.adobe.com/umapi/).

![Tool zur Benutzersynchronisierung](/help/security/assets/ims5.png)

Das Tool zur Benutzersynchronisierung steht über das Adobe Github-Repository [an diesem Speicherort](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.9.0rc2) zur Verfügung.

>[!NOTE]
>
>Die Vorabversion **2.4RC1** ist mit Unterstützung für die Erstellung dynamischer Gruppen unter [Tool zur Benutzersynchronisierung v2.4rc1 auf GitHub](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1) verfügbar.

Die wichtigsten Funktionen dieser Version sind die Möglichkeit, neue LDAP-Gruppen für die Benutzermitgliedschaft in der Admin Console dynamisch zuzuordnen und dynamische Benutzergruppen zu erstellen.

Weitere Informationen zu den neuen Gruppenfunktionen finden Sie unter [Tool zur Benutzersynchronisierung von Adobe – Weitere Gruppenoptionen](https://adobe-apiplatform.github.io/user-sync.py/de/user-manual/advanced_configuration.html#additional-group-options).

**Dokumentation zur Benutzersynchronisierung**

Siehe:

* [UST-Dokumentation](https://adobe-apiplatform.github.io/user-sync.py/de/)

* Das Tool zur Benutzersynchronisierung muss mit dem Verfahren der [Authentifizierung für API-Zugriff](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html) als Adobe Developer-Client-UMAPI registriert werden.

* [Adobe Developer Console-Dokumentation](https://developer.adobe.com/developer-console/)

* [User Management-API, die vom Tool zur Benutzersynchronisierung verwendet wird](https://adobe-apiplatform.github.io/user-sync.py/de/)

## Konfiguration von Adobe Experience as a Cloud Service {#aem-configuration}

>[!NOTE]
>
>Die erforderliche AEM-IMS-Konfiguration wird automatisch konfiguriert, wenn die AEM-Umgebungen und -Instanzen bereitgestellt werden. Admins können sie jedoch gemäß den eigenen Anforderungen ändern, siehe [Bereitstellen in AEM as a Cloud Service](/help/implementing/deploying/overview.md).

Die erforderliche AEM-IMS-Konfiguration wird automatisch konfiguriert, wenn die AEM-Umgebungen und -Instanzen bereitgestellt werden. Kundenadministratoren können einen Teil der Konfiguration gemäß ihren Anforderungen ändern.

Der allgemeine Ansatz besteht darin, Adobe IMS als OAuth-Anbieter zu konfigurieren. Der **Apache Jackrabbit Oak Standard Sync Handler** kann wie bei der LDAP-Synchronisierung geändert werden.

Im Folgenden sind die wichtigsten OSGI-Konfigurationen aufgeführt, die geändert werden müssen, um Eigenschaften wie die automatische Benutzerzugehörigkeit oder die Gruppenzuordnung zu ändern.

<!-- Arun to provide list of osgi configs -->

## Verwendung {#how-to-use}

### Verwalten von Produkten und Benutzerzugriff in der Admin Console {#managing-products-and-user-access-in-admin-console}

Wenn sich der Produktadmin der Kundschaft bei der Admin Console anmeldet, sieht er wie unten gezeigt mehrere Instanzen des AEM as a Cloud Service-Produktkontexts. Wählen Sie zum Beispiel eines der Produkte auf der Seite **Übersicht**:

![Anmeldung von Instanzen](/help/security/assets/ims6.png)

Es wird eine Liste der vorhandenen Instanzen angezeigt:

![Anmeldung von Instanzen2](/help/security/assets/ims7.png)

Unter jeder Produktkontext-Instanz gibt es Instanzen, die sich auf Authoring- oder Publishing-Services über Produktions-, Staging- oder Entwicklungs-Umgebungen hinweg erstrecken. Jede Instanz wird Produktprofilen oder Cloud Manager-Rollen zugeordnet. Diese Produktprofile werden für die Zuweisung des Zugriffs an Benutzende und Gruppen mit den erforderlichen Berechtigungen verwendet.

Das Profil **AEM Administrators_xxx** wird verwendet, um Adminrechte in der zugehörigen AEM-Instanz zu gewähren, während das Profil **AEM Users_xxx** verwendet wird, um reguläre Benutzende hinzuzufügen.

Alle unter diesem Produktprofil hinzugefügten Benutzenden und Gruppen können sich wie im Beispiel unten gezeigt bei dieser Instanz anmelden:

![Produktprofil](/help/security/assets/ims8.png)

>[!WARNING]
>
>Ändern Sie nicht den Namen des Produktprofils **AEM Administrators**. Das Ändern des **AEM Administrators**-Produktprofilnamens entfernt Adminrechte von allen Benutzenden, die diesem Profil zugewiesen sind.

### Anmelden bei Adobe Experience Manager as a Cloud Service {#logging-in-to-aem}

**Lokale Administratoranmeldung**

AEM kann lokale Anmeldungen für Admin-Benutzende weiterhin unterstützen. Auf dem Anmeldebildschirm können Sie sich lokal anmelden:

![Lokale Anmeldung](/help/security/assets/ims9.png)

<!-- the above image must be updated for skyline -->

**IMS-basierte Anmeldung**

Für andere Benutzende wird die IMS-basierte Anmeldung verwendet, nachdem IMS in der Instanz konfiguriert wurde. Die Benutzerin bzw. der Benutzer klickt wie unten gezeigt auf die Schaltfläche „Mit Adobe anmelden“:

![IMS-Anmeldung](/help/security/assets/ims10.png)


>[!NOTE]
>
>Jeder Benutzer, der in IMS erstellt wurde, kann mit einer Adobe ID oder einer Federated ID erstellt werden. Wenn eine Benutzerin bzw. ein Benutzer mit Federated ID eingerichtet ist, wird sie/er bei der Anmeldung über den Identitätsanbieter ihres/seines Unternehmens authentifiziert.

Sie werden zum IMS-Anmeldebildschirm umgeleitet und müssen ihre Anmeldeinformationen eingeben:

![IMS Login2](/help/security/assets/ims11.png)

![IMS Login3](/help/security/assets/ims12.png)

Wenn während der Ersteinrichtung der Admin Console Federated IDP konfiguriert wurde, wird die Benutzerin bzw. der Benutzer zum Kunden-IDP für die einmalige Anmeldung (SSO) weitergeleitet:

![IMS Login4](/help/security/assets/ims13.png)

Sobald die Authentifizierung abgeschlossen ist, wird die Person zurück zu AEM weitergeleitet und angemeldet:

![IMS Login5](/help/security/assets/ims14.png)

### Verwalten von Berechtigungen und Zugriffssteuerungslisten (ACLs) in Adobe Experience Manager as a Cloud Service {#managing-permissions-in-aem}

Die Zugriffssteuerungslisten (ACLs) und Berechtigungen werden weiterhin in AEM verwaltet. Die vom IMS synchronisierten Benutzergruppen können lokalen Gruppen zugewiesen werden, in denen ACLs und Berechtigungen definiert sind.

Im folgenden Beispiel werden die synchronisierten Gruppen der lokalen Gruppe **Dam_Users** hinzugefügt, um ein Beispiel zu geben.

Der Benutzer ist Teil der folgenden Gruppen in IMS:

![ACL1](/help/security/assets/ims15.png)

Wenn sich der Benutzer anmeldet, werden die Gruppenmitgliedschaften wie unten dargestellt synchronisiert:

![ACL2](/help/security/assets/ims16.png)

In AEM können die aus IMS synchronisierten Benutzergruppen vorhandenen lokalen Gruppen (z. B. **DAM-Benutzer**) als Mitglieder hinzugefügt werden.

![ACL3](/help/security/assets/ims17.png)

Wie unten dargestellt, erbt die Gruppe **AEM-GRP_008** die Berechtigungen und Privilegien von **DAM Users**. Diese Vererbung ist eine effektive Möglichkeit zur Verwaltung von Berechtigungen für synchronisierte Gruppen und wird häufig in der LDAP-basierten Authentifizierungsmethode verwendet.

![ACL3](/help/security/assets/ims18.png)


### Zugriff auf Cloud Manager {#accessing-cloud-manager}

Um auf Cloud Manager oder Umgebungen in AEM as a Cloud Service zugreifen zu können, müssen Sie den Profilen des Cloud Manager-Produkts zugewiesen werden.

Unter „Rollendefinitionen“ finden Sie weitere Informationen zu Rollen von Benutzenden, die die Verfügbarkeit bestimmter Funktionen in Cloud Manager steuern.

>[!NOTE]
>Cloud Manager verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Informationen zu den einzelnen Rollen mit den entsprechenden Berechtigungen, vorkonfigurierten Aufgaben oder den Berechtigungen, die mit den einzelnen Rollen verknüpft sind, finden Sie unter [Rollenbasierte Berechtigungen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/role-based-permissions).

**Schritte zum Hinzufügen eines Benutzers**

1. Fügen Sie einem bestimmten Profil einen Benutzer hinzu, entweder über den Bildschirm eines vorhandenen Benutzers oder über einen Bildschirm für neue Benutzer.

1. Sie können einen Benutzer auch über den Bildschirm **Übersicht** hinzufügen, wie in der folgenden Abbildung dargestellt.

   ![ACL3](/help/security/assets/ims23.png)

   >[!NOTE]
   >Sie können einem Benutzer mehr als ein Profil zuweisen, wie in der folgenden Abbildung dargestellt.

   ![ACL3](/help/security/assets/ims22.png)


1. Sobald Sie dem entsprechenden Profil hinzugefügt wurden, sollten Sie in der Lage sein, über [Adobe Experience Cloud](https://my.cloudmanager.adobe.com) in der oberen rechten Ecke der Benutzeroberfläche auf die entsprechenden Mandanten im Cloud Manager zuzugreifen.


### Zugriff auf eine Instanz in AEM as a Cloud Service {#accessing-instance-cloud-service}

>[!IMPORTANT]
>Die im vorherigen Abschnitt erwähnten Schritte müssen bereits abgeschlossen sein, bevor Sie Zugriff auf eine Instanz in AEM as a Cloud Service erhalten.

Um auf eine AEM-Instanz in der **Admin Console** zugreifen zu können, sollten Sie das Cloud Manager-Programm und die Umgebungen innerhalb des Programms in der Produktliste in der **Admin Console** ansehen.

Im folgenden Screenshot sehen Sie beispielsweise zwei verfügbare Umgebungen: *dev author* und *publish*.

![ACL3](/help/security/assets/ims19.png)

Um Zugriff auf AEM-Instanzen zu erhalten, muss die Benutzerin bzw. der Benutzer einer Gruppe des entsprechenden Cloud Service-Produkts hinzugefügt werden.

Jede Authoring-Instanz hat ein AEM-Admin- und AEM-Benutzerprofil und jede Veröffentlichungsinstanz hat ein AEM-Benutzerprofil. Sie können bei Bedarf weitere Profile hinzufügen.

Um Zugriff auf die AEM-Instanz auf Administratorebene zu erhalten, fügen Sie den Benutzer dem AEM-Administratorprofil für das jeweilige Produkt hinzu.
