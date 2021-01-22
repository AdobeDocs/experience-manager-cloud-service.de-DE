---
title: 'Registrierung, Anmeldung und User Profil '
description: Informationen zu Registrierung, Anmeldung und Profil "Benutzer"auf der Ebene "Veröffentlichen"
translation-type: tm+mt
source-git-commit: 2c00c3723c3c84365044b5cd2fe6779de0360736
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 0%

---


# Registrierung, Anmeldung und Benutzerkonto {#registration-login-and-userprofile}

## Einführung {#introduction}

Webanwendungen bieten häufig Funktionen zur Kontoverwaltung, mit denen sich Endbenutzer auf einer Website registrieren können. Dadurch werden die Benutzerdaten beibehalten, sodass sie sich zukünftig anmelden und eine einheitliche Benutzererfahrung genießen können. In diesem Artikel wird beschrieben:

* Registrierung
* Anmeldung
* Speichern von Benutzerdaten im Profil
* Gruppenmitgliedschaft
* Datensynchronisierung

>[!IMPORTANT]
>
>Damit die in diesem Artikel beschriebene Funktion funktioniert, muss die Funktion zur Synchronisierung von Benutzerdaten aktiviert sein. Zu diesem Zeitpunkt ist eine Anfrage an den Kundensupport erforderlich, in der das entsprechende Programm und die entsprechenden Umgebung angegeben werden. Wenn diese Option nicht aktiviert ist, werden Benutzerinformationen nur für einen kurzen Zeitraum (1 bis 24 Stunden) beibehalten, bevor sie verschwinden.

## Registrierung {#registration}

Wenn sich ein Endbenutzer für ein Konto in einer AEM Anwendung registriert, wird im AEM Publish-Dienst ein Benutzerkonto erstellt, wie in einer Benutzerressource unter `/home/users` im JCR-Repository dargestellt.

Zur Implementierung der Registrierung gibt es zwei Ansätze, wie nachfolgend beschrieben.

### AEM verwaltet {#aem-managed-registration}

Benutzerdefinierter Registrierungscode kann geschrieben werden, der mindestens den Benutzernamen und das Kennwort des Endbenutzers akzeptiert und einen Benutzerdatensatz in AEM erstellt, der dann zur Authentifizierung während der Anmeldung verwendet werden kann. Die folgenden Schritte werden normalerweise zum Aufbau dieses Registrierungsmechanismus verwendet:

1. Eine benutzerdefinierte AEM-Komponente anzeigen, die Registrierungsinformationen erfasst
1. Bei der Übermittlung wird ein ordnungsgemäß bereitgestellter Dienstbenutzer verwendet, um
   1. Überprüfen Sie mithilfe einer der `findAuthorizables()`-Methoden der UserManager-API, ob noch kein Benutzer vorhanden ist.
   1. Erstellen eines Benutzerdatensatzes mithilfe einer der `createUser()`-Methoden der UserManager API
   1. Beständigen Sie alle mit den `setProperty()`-Methoden der Authorizable-Schnittstelle erfassten Profil-Daten.
1. Optionale Textflüsse, z. B. die Anforderung, dass der Benutzer seine E-Mail validieren muss.

### Extern {#external-managed-registration}

In einigen Fällen erfolgte die Registrierung oder Benutzererstellung zuvor in einer Infrastruktur außerhalb von AEM. In diesem Szenario wird der Benutzerdatensatz während der Anmeldung in AEM erstellt.

## Anmeldung {#login}

Sobald ein Endbenutzer beim AEM Publish-Dienst registriert ist, können sich diese Benutzer anmelden, um authentifizierten Zugriff zu haben (mithilfe AEM Autorisierungsmechanismen) und dauerhaft benutzerspezifische Daten wie Profil-Daten zu erhalten.

## Implementierung {#implementation}

Die Anmeldung kann mit den folgenden beiden Methoden implementiert werden:

### AEM verwaltet {#aem-managed-implementation}

Kunden können eigene benutzerdefinierte Komponenten schreiben. Um mehr zu erfahren, sollten Sie sich mit Folgendem vertraut machen:

* [Sling Authentication Framework](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* Überlegen Sie sich, ob Sie sich bei der AEM Community Experts Session ](http://bit.ly/ATACEFeb15) zur Anmeldung fragen möchten.[

### Integration mit einem Identitätsanbieter {#integration-with-an-idp}

Kunden können sich mit einem Identitäts-Provider (IdP) integrieren, der den Benutzer authentifiziert. Zu den Integrationstechnologien zählen SAML und OAuth/SSO, wie nachfolgend beschrieben.

**SAML BASIERT**

Kunden können die SAML-basierte Authentifizierung über ihren bevorzugten SAML IdP verwenden. Bei Verwendung eines IdP mit AEM ist der IdP dafür verantwortlich, die Anmeldeinformationen des Endbenutzers zu authentifizieren und die Authentifizierung des Benutzers mit AEM zu vermitteln, den Benutzerdatensatz nach Bedarf in AEM zu erstellen und die Gruppenmitgliedschaft des Benutzers AEM zu verwalten, wie in der SAML-Zusicherung beschrieben.

>[!NOTE]
>
>Nur die anfängliche Authentifizierung der Anmeldeinformationen des Benutzers wird vom IdP authentifiziert. Nachfolgende Anforderungen an AEM werden mit einem AEM Login-Token-Cookie ausgeführt, solange das Cookie verfügbar ist.

Weitere Informationen zum [SAML 2.0 Authentication Handler](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html?lang=en#saml-authentication-handler) finden Sie in der Dokumentation.

**OAuth/SSO**

Informationen zur Verwendung AEM SSO-Authentifizierungs-Handler-Dienstes finden Sie in der Dokumentation [Single Sign-On (SSO)](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html).

Die `com.adobe.granite.auth.oauth.provider` Schnittstelle kann mit dem OAuth Provider Ihrer Wahl implementiert werden.

### Fixierbare Sitzungen und verkapselte Token {#sticky-sessions-and-encapsulated-tokens}

AEM als Cloud Service sind cookie-basierte persistente Sitzungen aktiviert, wodurch sichergestellt wird, dass ein Endbenutzer bei jeder Anforderung an denselben Veröffentlichungsknoten weitergeleitet wird. Um die Leistung zu erhöhen, ist die Funktion für verkapselte Token standardmäßig aktiviert, sodass der Benutzerdatensatz im Repository nicht bei jeder Anforderung referenziert werden muss. Wenn der Veröffentlichungs-Knoten, für den ein Endbenutzer über eine Affinität verfügt, ersetzt wird, ist der Benutzer-ID-Datensatz auf dem neuen Veröffentlichungsknoten verfügbar, wie im Abschnitt zur Datensynchronisierung unten beschrieben.

## Benutzerprofil {#user-profile}

Es gibt verschiedene Ansätze zum Bestehen von Daten, je nach Art dieser Daten.

### AEM Repository {#aem-repository}

Informationen zum User Profil können auf zwei Arten geschrieben und gelesen werden:

* Serverseitige Verwendung mit der `com.adobe.granite.security.user`-Schnittstelle UserPropertiesManager-Schnittstelle, die Daten unter dem Knoten des Benutzers in `/home/users` platziert. Stellen Sie sicher, dass Seiten, die pro Benutzer eindeutig sind, nicht zwischengespeichert werden.
* Clientseitige Verwendung von ContextHub, wie in [der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=en#personalization) beschrieben.

### Datenspeicher von Drittanbietern {#third-party-data-stores}

Endbenutzerdaten können an Drittanbieter wie z. B. CRMs gesendet und bei der Anmeldung des Benutzers über APIs abgerufen werden. Sie bleiben auf dem Profil-Knoten des AEM und werden nach Bedarf von AEM verwendet.

Der Echtzeitzugriff auf Dienste von Drittanbietern zum Abrufen von Profil-Attributen ist möglich. Es ist jedoch wichtig sicherzustellen, dass dies die Anforderungsverarbeitung in AEM nicht wesentlich beeinflusst.

## Berechtigungen (geschlossene Benutzergruppen) {#permissions-closed-user-groups}

Zugriffsrichtlinien auf Veröffentlichungsebene, auch &quot;geschlossene Benutzergruppen&quot;(CUGs) genannt, werden im AEM-Autor als [hier beschrieben](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=en#applying-your-closed-user-group-to-content-pages) definiert. Um bestimmte Abschnitte oder Seiten einer Website von einigen Benutzern zu beschränken, wenden Sie die CUGs nach Bedarf mit dem AEM Autor an, wie hier beschrieben, und replizieren Sie sie auf die Veröffentlichungsstufe.

* Wenn sich Benutzer mithilfe von SAML bei einem Identitätsanbieter (IdP) anmelden, identifiziert der Authentifizierungshandler die Gruppenmitgliedschaften des Benutzers (die mit den CUGs auf der Veröffentlichungsstufe übereinstimmen sollten) und behält die Verknüpfung zwischen dem Benutzer und der Gruppe über einen Repository-Datensatz bei
* Wenn die Anmeldung ohne IdP-Integration erfolgt, kann der benutzerdefinierte Code dieselben Repository-Strukturbeziehungen anwenden.

Unabhängig von der Anmeldung kann benutzerspezifischer Code auch die Gruppenmitgliedschaften eines Benutzers beibehalten und verwalten, wie es die spezifischen Anforderungen eines Unternehmens erfordern.

## Datensynchronisierung {#data-synchronization}

Website-Endbenutzer erwarten bei jeder Webseitenanforderung ein konsistentes Erlebnis oder auch dann, wenn sie sich mit einem anderen Browser anmelden, selbst wenn sie ihnen nicht bekannt sind, werden sie an verschiedene Server-Knoten der Veröffentlichungsstufe-Infrastruktur weitergeleitet. AEM als Cloud Service erreicht dies durch eine schnelle Synchronisierung der `/home`-Ordnerhierarchie (Benutzerinformationen, Gruppenmitgliedschaft usw.) über alle Knoten der Veröffentlichungsstufe.

Im Gegensatz zu anderen AEM verwenden Benutzer- und Gruppenmitgliedssynchronisierungen in AEM als Cloud Service keinen Point-to-Point-Messaging-Ansatz, sondern implementieren einen Veröffentlichungsabonnement-Ansatz, der keine Kundenkonfiguration erfordert.

>[!NOTE]
>
>Standardmäßig sind die Synchronisierung der Benutzerzugehörigkeit und der Gruppenmitgliedschaft nicht aktiviert. Die Daten werden daher nicht mit der Veröffentlichungsstufe synchronisiert oder bleiben auch nicht dauerhaft erhalten. Um die Funktion zu aktivieren, senden Sie eine Anfrage an den Kundendienst, in der das entsprechende Programm und die entsprechenden Umgebung angegeben sind.

## Cache-Überlegungen {#cache-considerations}

Authentifizierte HTTP-Anforderungen können sowohl auf dem CDN als auch auf dem Dispatcher schwer zwischengespeichert werden, da sie die Möglichkeit bieten, dass benutzerspezifischer Status als Teil der Antwort der Anforderung übertragen wird. Die versehentliche Zwischenspeicherung authentifizierter Anforderungen und deren Bereitstellung für andere anfordernde Browser kann zu fehlerhaften Erlebnissen oder sogar zum Versiegeln von geschützten oder Benutzerdaten führen.

Zu den Ansätzen für die Aufrechterhaltung einer hohen Cache-Fähigkeit von Anforderungen bei gleichzeitiger Unterstützung benutzerspezifischer Antworten gehören:

* AEM Dispatcher-Zugriffsberechtigungen für vertrauliche Zwischenspeicherung
* Sling Dynamic Include
* AEM ContextHub