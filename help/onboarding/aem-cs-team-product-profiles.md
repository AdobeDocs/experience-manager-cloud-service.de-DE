---
title: AEM as a Cloud Service – Team- und Produktprofile
description: Erfahren Sie, wie Sie über AEM as a Cloud Service Team- und Produktprofile erstellen und den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren oder einschränken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 928a3f0d8ee98e211aa03ad3d0fd83b780e98bbc
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 89%

---


# AEM as a Cloud Service – Team- und Produktprofile {#product-profiles}

Erfahren Sie, wie Sie über AEM as a Cloud Service Team- und Produktprofile erstellen und den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren oder einschränken.

## Produktprofile {#profiles}

Wenn Sie einem Benutzer Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihm nicht unbedingt uneingeschränkten Zugriff gewähren. Mit Produktprofilen kann jeder Lösung ein eigener Satz von Benutzerberechtigungen zugewiesen werden. Diese sind über die [Admin Console](/help/journey-onboarding/admin-console.md) verfügbar und zugänglich.

## AEM as a Cloud Service-Produktprofile {#aem-product-profiles}

AEM as a Cloud Service ist ein vollständig Cloud-natives Angebot, das AEM als Service bereitstellt. Es bietet AEM auf Cloud-native Weise mit neuen Attributen wie „always on“ (immer aktiv), „always current“ (immer aktuell), „always secure“ (immer sicher) und „always at scale“ (immer skaliert). Gleichzeitig wird das wichtigste Wertversprechen aufrecht erhalten, das AEM als anpassbare Plattform für Kunden bereitstellt und es Teams in Unternehmen ermöglicht, sich in ihre Entwicklungs- und Bereitstellungsverfahren zu integrieren. Weitere Informationen zu AEM as a Cloud Service finden Sie in der [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md).

Ihre AEM as a Cloud Service-Team-Mitglieder werden während des Onboardings über die Admin Console einem oder mehreren der folgenden Produktprofile hinzugefügt und zugewiesen.

* **AEM-Administratoren**: Die Rolle des AEM-Administrators wird in der Regel Entwicklerinnen bzw. Entwicklern zugewiesen, insbesondere jenen, die Zugriff beispielsweise auf die Entwicklungsumgebungen benötigen. Das Produktprofil „AEM-Administratoren“ wird verwendet, um Administratorberechtigungen in der zugehörigen AEM-Instanz zu gewähren.

* **AEM-Benutzende**: AEM-Benutzende sind die Personen in Ihrer Organisation, die AEM as a Cloud Service im Allgemeinen zum Erstellen von Inhalten verwenden. Diese Benutzenden benötigen Zugriff auf AEM, um ihre Aufgaben wahrnehmen zu können. Das Produktprofil eines AEM-Benutzers bzw. einer AEM-Benutzerin wird üblicherweise einem AEM-Inhaltsautor bzw. einer AEM-Inhaltsautorin zugewiesen, der/die die Inhalte erstellt und überprüft. Bei diesen Inhalten kann es sich um z. B. Seiten, Assets oder Veröffentlichungen handeln. Diesen Team-Mitgliedern wird das unten gezeigte Produktprofil „AEM-Benutzer“ zugewiesen.

![Produktprofile](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Jeder Benutzer, der einem AEM as a Cloud Service-Produktprofil zugewiesen ist, hat über die Rolle **Cloud Manager-Benutzer** schreibgeschützten Zugriff auf Cloud Manager.
>
>Benutzer nur mit der Rolle **Cloud Manager-Benutzer** können sich bei Cloud Manager anmelden und zu den AEM-Autorenumgebungen navigieren (falls vorhanden), indem sie die Menüoptionen unter **Programme** verwenden. Die Rolle **Cloud Manager-Benutzer** reicht nicht aus, um auf Programmdetails zuzugreifen. Wenn ein solcher Zugriff erforderlich ist, müssen Benutzende von ihrem Systemadministrator zusätzliche Rollen erhalten.

>[!WARNING]
>
>Der **AEM-Admin**-Produktprofilname darf nicht geändert werden. Das Ändern des **AEM-Admin**-Produktprofilnamens entfernt Adminrechte von allen Benutzenden, die diesem Profil zugewiesen sind.

>[!TIP]
>
>* Weitere Informationen zu AEM-Produktprofilen finden Sie unter [Zuweisen von AEM-Produktprofilen](/help/journey-onboarding/assign-profiles-aem.md).
>* Weitere Informationen zum Onboarding-Prozess finden Sie in der [Onboarding-Tour](/help/journey-onboarding/overview.md).

## Cloud Manager-Produktprofile {#cloud-manager-product-profiles}

Cloud Manager verfügt über vorkonfigurierte Produktprofile, die man sich als rollenbasierte Berechtigungen vorstellen kann. Ihr(e) System-Admin ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, indem er/sie die Team-Mitglieder diesen Produktprofilen zuweist.

>[!TIP]
>
>Weitere Informationen finden Sie unter [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

Jedem Produktprofil sind spezifische Berechtigungen zugeordnet.

* **Geschäftsinhaber**
   * In dieser Rolle können Sie ein neues Programm hinzufügen oder ein Programm bearbeiten, eine Umgebung hinzufügen oder aktualisieren, Code in AEM Umgebung bereitstellen oder Code-Qualitätsprüfungen durchführen.
   * Dieser Anwender ist verantwortlich für die Definition von KPIs, die Genehmigung von Produktionbereitstellungen und das Überschreiben von gravierenden 3-Tier-Fehlern, falls erforderlich.
* **Bereitstellungs-Manager**
   * In dieser Rolle sind Sie berechtigt, eine Umgebung hinzuzufügen oder zu aktualisieren, eine beliebige Pipeline auszuführen, Code für AEM Umgebung bereitzustellen oder Code-Qualitätsprüfungen durchzuführen.
   * Dieser Anwender verwaltet die Bereitstellungsvorgänge mit Cloud Manager, um Staging- und Produktionsbereitstellungen durchzuführen, CI/CD-Pipeline zu bearbeiten, kann bei Bedarf gravierende 3-Tier-Fehler genehmigen und hat Zugriff auf das Git-Repository.
* **Entwickler**
   * In dieser Rolle haben Sie die Berechtigung, persönliche Zugriffstoken für den Zugriff auf Git zu generieren.
   * Dieser Anwender entwickelt und testet benutzerdefinierten Anwendungscode, verwendet Cloud Manager hauptsächlich zur Anzeige des Bereitstellungsstatus und für Code-Commits auf das Git-Repository zugreifen.
* **Programm-Manager**
   * In dieser Rolle haben Sie die Berechtigung, Pipelines zu planen, die dreistufigen Quality Gates zu überschreiben und eine Produktionsgenehmigung zu erteilen.
   * Dieser Anwender nutzt Cloud Manager, um die Einrichtung von Teams vorzunehmen, den Status zu überprüfen, KPIs einzusehen und ggf. gravierende 3-Tier-Fehler zu genehmigen.

Benutzende können mehreren Produktprofilen zugewiesen werden. Wenn Sie beispielsweise einem Benutzer bzw. einer Benutzerin die beiden Rollen **Geschäftsinhaber** und **Bereitstellungs-Manager** zuweisen, erhält er/sie die Summe aller dieser Berechtigungen.

Ihr Cloud Manager-Team umfasst mindestens:

* Einen **Geschäftsinhaber**, der in der Regel auch der/die System-Admin ist und die erste Person sein muss, die sich bei Cloud Manager anmeldet und darauf zugreift
* Einen **Bereitstellungs-Manager**
* **Einen Entwickler bzw. eine Entwicklerin**

>[!NOTE]
>
>Um Zugriff auf AEM as a Cloud Service zu erhalten, müssen Benutzende einem von zwei Produktprofilen angehören: `AEM Users` oder `AEM Administrators`. Die Berechtigungen zum Verwalten von Cloud Manager reichen nicht aus.

>[!TIP]
>
>* Weitere Informationen zu Cloud Manager-Produktprofilen finden Sie unter [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Weitere Informationen zum Onboarding-Prozess finden Sie in der [Onboarding-Tour](/help/journey-onboarding/overview.md).
