---
title: AEM as a Cloud Service – Team- und Produktprofile
description: Erfahren Sie, wie AEM as a Cloud Service Team und Produktprofile den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und beschränken können.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 69ac8e444a0f22649b48ec25b549ad60858f8b1b
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 74%

---

# AEM as a Cloud Service – Team- und Produktprofile {#product-profiles}

Erfahren Sie, wie AEM as a Cloud Service Team und Produktprofile den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und beschränken können.

## Produktprofile {#profiles}

Wenn Sie einem Benutzer Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihm nicht unbedingt uneingeschränkten Zugriff gewähren. Mit Produktprofilen kann jeder Lösung ein eigener Satz von Benutzerberechtigungen zugewiesen werden. Diese sind über die [Admin Console](/help/journey-onboarding/admin-console.md) verfügbar und abrufbar.

## AEM as a Cloud Service-Produktprofile {#aem-product-profiles}

AEM as a Cloud Service ist ein vollständig Cloud-natives Angebot, das AEM als Service bereitstellt. Es bietet AEM auf Cloud-native Weise mit neuen Attributen wie „always on“ (immer aktiv), „always current“ (immer aktuell), „always secure“ (immer sicher) und „always at scale“ (immer skaliert). Gleichzeitig wird das wichtigste Wertversprechen aufrecht erhalten, das AEM als anpassbare Plattform für Kunden bereitstellt und es Teams in Unternehmen ermöglicht, sich in ihre Entwicklungs- und Bereitstellungsverfahren zu integrieren. Weitere Informationen zu AEM as a Cloud Service finden Sie unter [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md).

Ihre AEM as a Cloud Service-Team-Mitglieder werden während des Onboardings über die Admin Console einem oder mehreren der folgenden Produktprofile hinzugefügt und zugewiesen.

* **AEM-Administratoren**: Die Rolle des AEM-Administrators wird in der Regel Entwicklern bzw. Entwicklerinnen zugewiesen, insbesondere jenen, die Zugriff auf beispielsweise die Entwicklungsumgebungen benötigen. Das Produktprofil „AEM-Administratoren“ wird verwendet, um Administratorberechtigungen in der zugehörigen AEM-Instanz zu gewähren.

* **AEM-Benutzende**: AEM-Benutzende sind die Personen in Ihrer Organisation, die AEM as a Cloud Service im Allgemeinen zum Erstellen von Inhalten verwenden. Diese Benutzenden benötigen Zugriff auf AEM, um ihre Aufgaben wahrnehmen zu können. Das Produktprofil eines AEM-Benutzers bzw. einer AEM-Benutzerin wird üblicherweise einem AEM-Inhaltsautor bzw. einer AEM-Inhaltsautorin zugewiesen, der/die die Inhalte erstellt und überprüft. Bei diesen Inhalten kann es sich um z. B. Seiten, Assets oder Veröffentlichungen handeln. Diesen Team-Mitgliedern wird das unten gezeigte Produktprofil „AEM-Benutzer“ zugewiesen.

![Produktprofile](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Jeder Benutzer, der einem AEM as a Cloud Service Produktprofil zugewiesen ist, hat schreibgeschützten Zugriff auf Cloud Manager über die **Cloud Manager-Benutzer** Rolle.
>
>Benutzer mit nur der **Cloud Manager-Benutzer** Die Rolle kann sich bei Cloud Manager anmelden und zu den (falls vorhanden) AEM Autorenumgebungen navigieren, indem Sie die **Programme** Menüoptionen. Die **Cloud Manager-Benutzer** Rolle reicht nicht aus, um auf Programmdetails zuzugreifen. Wenn ein solcher Zugriff erforderlich ist, müssen Benutzer von ihrem Systemadministrator zusätzliche Rollen erhalten.

>[!TIP]
>
>* Weitere Informationen zu AEM Produktprofilen finden Sie im Dokument . [Zuweisen AEM Produktprofilen.](/help/journey-onboarding/assign-profiles-aem.md)
>* Weitere Informationen zum Onboarding-Prozess finden Sie unter [Onboarding-Tour](/help/journey-onboarding/overview.md).


## Cloud Manager-Produktprofile {#cloud-manager-product-profiles}

Cloud Manager verfügt über vorkonfigurierte Produktprofile, die man sich als rollenbasierte Berechtigungen vorstellen kann. Ihr(e) System-Admin ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, indem er/sie die Team-Mitglieder diesen Produktprofilen zuweist.

>[!TIP]
>
>Weitere Einzelheiten finden Sie im Dokument [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

Jedem Produktprofil sind spezifische Berechtigungen zugeordnet.

* **Business Owner** - In dieser Rolle können Sie ein neues Programm hinzufügen oder ein Programm bearbeiten, eine Umgebung hinzufügen oder aktualisieren, Code in AEM Umgebung bereitstellen oder Code-Qualitätsprüfungen durchführen.
* **Implementierungs-Manager**: In dieser Rolle sind Sie berechtigt, eine Umgebung hinzuzufügen oder zu aktualisieren, eine beliebige Pipeline auszuführen und Code in der AEM-Umgebung bereitzustellen oder Code-Qualitätsprüfungen durchzuführen.
* **Entwickler**: In dieser Rolle sind Sie berechtigt, persönliche Zugriffs-Token für den Zugriff auf Git zu generieren.
* **Programm-Manager**: In dieser Rolle sind Sie berechtigt, Pipelines zu planen, die dreistufigen Quality Gates außer Kraft zu setzen und Produktionsgenehmigungen zu erteilen.

Benutzende können mehreren Produktprofilen zugewiesen werden. Wenn Sie beispielsweise einem Benutzer bzw. einer Benutzerin die beiden Rollen **Geschäftsinhaber** und **Implementierungs-Manager** zuweisen, erhält er/sie die Summe aller dieser Berechtigungen.

Ihr Cloud Manager-Team umfasst mindestens:

* Einen **Geschäftsinhaber**, der in der Regel auch der/die System-Admin ist und die erste Person sein muss, die sich bei Cloud Manager anmeldet und darauf zugreift
* Einen **Implementierungs-Manager**
* **Einen Entwickler bzw. eine Entwicklerin**

>[!NOTE]
>
>Um Zugriff auf AEM as a Cloud Service zu erhalten, müssen Benutzende einem von zwei Produktprofilen angehören: `AEM Users` oder `AEM Administrators`. Die Berechtigungen zum Verwalten von Cloud Manager reichen nicht aus.

>[!TIP]
>
>* Weitere Informationen zu Cloud Manager-Produktprofilen finden Sie im Dokument . [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen.](/help/journey-onboarding/assign-profiles-cloud-manager.md)
>* Weitere Informationen zum Onboarding-Prozess finden Sie unter [Onboarding-Tour](/help/journey-onboarding/overview.md).

