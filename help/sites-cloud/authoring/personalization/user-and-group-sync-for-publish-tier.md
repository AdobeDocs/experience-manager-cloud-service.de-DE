---
title: Registrierung, Anmeldung und Anwenderprofil
description: In diesem Abschnitt erfahren Sie mehr über Registrierung, Anmeldung, Anwenderdaten und Gruppensynchronisierung für AEM as a Cloud Service.
exl-id: a991e710-a974-419f-8709-ad86c333dbf8
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: ht
source-wordcount: '1132'
ht-degree: 100%

---

# Registrierung, Anmeldung und Anwenderprofil {#registration-login-and-userprofile}

## Einführung {#introduction}

Web-Programme bieten häufig Funktionen zur Kontoverwaltung, mit denen sich Endanwender auf einer Website registrieren können. Dadurch werden ihre Anwenderdaten beibehalten, sodass sie sich auch künftig anmelden und von einem einheitlichen Anwendererlebnis profitieren können. In diesem Artikel werden die folgenden Konzepte für AEM as a Cloud Service beschrieben:

* Registrierung
* Anmeldung
* Speichern von Anwenderprofildaten im Profil
* Gruppenmitgliedschaft
* Datensynchronisierung

>[!IMPORTANT]
>
>Damit die in diesem Artikel beschriebene Funktion ordnungsgemäß genutzt werden kann, muss die Funktion zur Synchronisierung von Anwenderdaten aktiviert sein. Dazu ist derzeit Anfrage beim Kunden-Support erforderlich, in der das betreffende Programm und die entsprechenden Umgebung angegeben werden. Wenn diese Option nicht aktiviert ist, werden Anwenderinformationen nur für einen kurzen Zeitraum (1–24 Stunden) beibehalten.

## Registrierung {#registration}

Wenn sich ein Endanwender für ein Konto in einem AEM-Programm registriert, wird im Veröffentlichungs-Service von AEM ein Benutzerkonto erstellt, wie in einer Anwenderressource unter `/home/users` im JCR-Repository dargestellt.

Zur Implementierung der Registrierung gibt es zwei Ansätze, wie nachfolgend beschrieben.

### Von AEM verwaltet {#aem-managed-registration}

Es kann benutzerdefinierter Registrierungs-Code geschrieben werden, der mindestens den Benutzernamen und das Kennwort der Benutzenden benötigt und einen Benutzereintrag in AEM erstellt, der dann bei der Anmeldung zur Authentifizierung verwendet werden kann. Normalerweise werden die folgenden Schritte zum Aufbau dieses Registrierungsmechanismus verwendet:

1. Anzeigen einer benutzerdefinierten AEM-Komponente, die Registrierungsinformationen erfasst
1. Verwenden eines ordnungsgemäß bereitgestellten Service-Anwenders bei der Übermittlung, um Folgendes zu erreichen:
   1. Mithilfe einer der `findAuthorizables()`-Methoden der UserManager-API überprüfen, ob noch kein Anwender vorhanden ist
   1. Erstellen eines Anwenderdatensatzes mithilfe einer der `createUser()`-Methoden der UserManager-API
   1. Beibehalten aller mit den `setProperty()`-Methoden der Authorizable-Schnittstelle erfassten Profildaten
1. Optionale Abläufe, etwa die Anforderung, dass Anwender ihre E-Mail-Adresse validieren müssen

### Extern {#external-managed-registration}

In einigen Fällen erfolgte die Registrierung oder Anwendererstellung zuvor in einer Infrastruktur außerhalb von AEM. In diesem Szenario wird der Anwenderdatensatz bei der Anmeldung in AEM erstellt.

## Anmeldung {#login}

Sobald ein Endanwender beim Veröffentlichungs-Service von AEM registriert ist, kann sich dieser Anwender für den authentifizierten Zugriff anmelden (mithilfe von AEM-Autorisierungsmechanismen). Außerdem können dann anwenderspezifische Daten wie seine Profildaten beibehalten werden.

## Implementierung {#implementation}

Die Anmeldung lässt sich mithilfe der beiden folgenden Methoden implementieren:

### Von AEM verwaltet {#aem-managed-implementation}

Kunden können eigene benutzerdefinierte Komponenten schreiben. Dazu empfehlen wir Ihnen, sich hier eingehender informieren:

* in der Dokumentation zum [Sling-Authentifizierungs-Framework](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* bei den [AEM Community Experts](https://bit.ly/ATACEFeb15), die Sie in den Sessions zur Anmeldung befragen können.

### Zusammenarbeit mit einem Identitätsanbieter {#integration-with-an-idp}

Kunden können sich mit Identitätsanbieter zusammenarbeiten, der die Anwender authentifiziert. Zu den Integrationstechnologien zählen SAML und OAuth/SSO, wie nachfolgend beschrieben.

**SAML-basiert**

Kunden können über ihren bevorzugten SAML-Identitätsanbieter die SAML-basierte Authentifizierung nutzen. Bei Inanspruchnahme eines IDP in Verbindung mit AEM ist der IDP dafür verantwortlich, die Anmeldeinformationen der Benutzenden zu authentifizieren und die Authentifizierung der Benutzenden mit AEM zu vermitteln, die Benutzerdatensätze nach Bedarf in AEM zu erstellen und die Gruppenmitgliedschaft der Benutzenden in AEM zu verwalten, wie durch die SAML-Assertion beschrieben.

>[!NOTE]
>
>Nur die anfängliche Authentifizierung der Anmeldeinformationen der Anwender wird vom Identitätsanbieter authentifiziert. Die nachfolgenden Anfragen an AEM werden mit einem AEM-Login-Token-Cookie ausgeführt, solange das Cookie verfügbar ist.

Weitere Informationen zum [SAML 2.0-Authentifizierungs-Handler](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html?lang=de) finden Sie in der Dokumentation.

**OAuth/SSO**

Informationen zur Verwendung AEM SSO-Authentifizierungs-Handler-Service finden Sie in der Dokumentation zu [Single Sign-On (SSO)](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html?lang=de).

Die `com.adobe.granite.auth.oauth.provider`-Schnittstelle kann mit dem OAuth-Anbieter Ihrer Wahl implementiert werden.

### Sticky Sessions und Encapsulated Tokens {#sticky-sessions-and-encapsulated-tokens}

AEM as a Cloud Service verfügt über Cookie-basierte Sticky Sessions, die sicherstellen, dass Endbenutzende bei jeder Anfrage an denselben Veröffentlichungsknoten weitergeleitet werden. Um die Leistung zu steigern, ist die Funktion für „Encapsulated Tokens“ standardmäßig aktiviert, sodass Anwenderdatensätze im Repository nicht bei jeder Anfrage referenziert werden müssen. Wenn der Veröffentlichungsknoten, zu dem Endbenutzende gehören, ersetzt wird, ist der Datensatz mit der Anwender-ID auf dem neuen Veröffentlichungsknoten verfügbar, wie im nachfolgenden Abschnitt zur Datensynchronisierung beschrieben.

## Benutzerprofil {#user-profile}

Es gibt verschiedene Ansätze zur Beibehaltung von Daten, abhängig von der Art der Daten.

### AEM-Repository {#aem-repository}

Informationen zum Anwenderprofil können auf zwei Arten geschrieben und gelesen werden:

* Server-seitige Verwendung mit der `com.adobe.granite.security.user`-Schnittstelle „UserPropertiesManager“, die Daten unter dem Knoten des Anwenders in `/home/users` platziert. Stellen Sie sicher, dass Seiten, die pro Benutzer eindeutig sind, nicht zwischengespeichert werden.
* Client-seitige Verwendung von ContextHub, wie in [der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=de#personalization) beschrieben.

### Datenspeicher von Drittanbietern {#third-party-data-stores}

Endbenutzerdaten können an Drittanbieter wie etwa CRMs gesendet und bei der Anmeldung von Benutzenden über APIs abgerufen werden. Sie werden auf dem Profil-Knoten der AEM-Benutzenden beibehalten und nach Bedarf von AEM verwendet.

Der Echtzeitzugriff auf Dienste von Drittanbietern zum Abruf von Profilattributen ist möglich. Es ist jedoch wichtig sicherzustellen, dass dies die Anfrageverarbeitung in AEM nicht wesentlich beeinflusst.

## Berechtigungen (geschlossene Benutzergruppen) {#permissions-closed-user-groups}

Zugriffsrichtlinien auf Veröffentlichungsebene, auch geschlossene Benutzergruppen genannt, werden in der AEM-Authoring-Umgebung wie [hier beschrieben](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=de#applying-your-closed-user-group-to-content-pages) definiert. Um den Zugriff auf bestimmte Abschnitte oder Seiten einer Website für einige Benutzende zu beschränken, wenden Sie die geschlossenen Benutzergruppen nach Bedarf mithilfe der AEM-Authoring-Umgebung wie hier beschrieben an, und replizieren Sie sie auf der Veröffentlichungsebene.

* Wenn sich Anwender mithilfe von SAML bei einem Identitätsanbieter anmelden, identifiziert der Authentifizierungs-Handler die Gruppenmitgliedschaften des Anwenders (die mit den geschlossenen Anwendergruppen auf der Veröffentlichungsebene übereinstimmen sollten) und behält die Verknüpfung zwischen dem Anwender und der Gruppe über einen Repository-Datensatz bei.
* Wenn die Anmeldung ohne Einbindung eines Identitätsanbieters erfolgt, kann der benutzerdefinierte Code dieselben Repository-Strukturbeziehungen anwenden.

Unabhängig von der Anmeldung kann benutzerdefinierter Code auch die Gruppenmitgliedschaften eines Anwenders beibehalten und verwalten, wie es die spezifischen Anforderungen eines Unternehmens erfordern.

## Datensynchronisierung {#data-synchronization}

Endbenutzende von Websites erwarten bei jeder Website-Anfrage ein konsistentes Erlebnis. Das gilt auch dann, wenn sie sich mit einem anderen Browser anmelden: Selbst wenn sie ihm nicht bekannt sind, werden sie an verschiedene Server-Knoten der Infrastruktur auf Veröffentlichungsebene weitergeleitet. AEM as a Cloud Service erreicht dies durch eine schnelle Synchronisierung der `/home`-Ordnerhierarchie (Benutzerprofilinformationen, Gruppenmitgliedschaft usw.) für alle Knoten der Veröffentlichungsebene.

Anders als bei anderen AEM-Lösungen verfolgt die Anwender- und Gruppenmitgliedssynchronisierung in AEM as a Cloud Service keinen Point-to-Point-Messaging-Ansatz, sondern einen Ansatz, der auf Veröffentlichen/Abonnieren ausgelegt ist und keine Konfiguration durch den Kunden erfordert.

>[!NOTE]
>
>Standardmäßig ist die Synchronisierung von Anwenderprofilen und Gruppenmitgliedschaften nicht aktiviert, sodass die Daten nicht mit der Veröffentlichungsebene synchronisiert oder gar dauerhaft auf ihr beibehalten werden. Um die Funktion zu aktivieren, senden Sie eine Anfrage an den Kunden-Support, in der das entsprechende Programm und die entsprechenden Umgebung angegeben sind.

## Überlegungen zum Cache {#cache-considerations}

Das Zwischenspeichern authentifizierter HTTP-Anfragen sowohl im CDN als auch auf dem Dispatcher kann sich schwierig gestalten, da möglicherweise anwenderspezifische Status als Teil der Antwort auf die Anfrage übertragen werden. Das unbeabsichtigte Zwischenspeichern authentifizierter Anfragen und deren Bereitstellung für andere anfordernde Browser kann zu fehlerhaften Erlebnissen oder sogar zum Verlust von geschützten oder Anwenderdaten führen.

Ansätze für die Aufrechterhaltung einer hohen Cache-Fähigkeit von Anfragen bei gleichzeitiger Unterstützung anwenderspezifischer Antworten:

* Zwischenspeicherung, bei der AEM Dispatcher-Zugriffsberechtigungen berücksichtigt wird
* Sling Dynamic Include
* AEM-ContextHub
