---
title: AEM as a Cloud Service – Team- und Produktprofile
description: Erfahren Sie, wie Sie über AEM as a Cloud Service Team- und Produktprofile erstellen und den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren oder einschränken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 83%

---

# AEM as a Cloud Service – Team- und Produktprofile {#product-profiles}

Erfahren Sie, wie Sie über AEM as a Cloud Service Team- und Produktprofile erstellen und den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren oder einschränken.

## Produktprofile {#profiles}

Wenn Sie einem Benutzer Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihm nicht unbedingt uneingeschränkten Zugriff gewähren. Mit Produktprofilen kann jeder Lösung ein eigener Satz von Benutzerberechtigungen zugewiesen werden. Diese sind über die [ Admin Console](/help/journey-onboarding/admin-console.md) verfügbar und zugänglich.

## AEM as a Cloud Service-Produktprofile {#aem-product-profiles}

AEM as a Cloud Service ist ein vollständig Cloud-natives Angebot, das AEM als Service bereitstellt. Es bietet AEM auf Cloud-native Weise mit neuen Attributen wie „always on“ (immer aktiv), „always current“ (immer aktuell), „always secure“ (immer sicher) und „always at scale“ (immer skaliert). Gleichzeitig wird das wichtigste Wertversprechen aufrecht erhalten, das AEM als anpassbare Plattform für Kunden bereitstellt und es Teams in Unternehmen ermöglicht, sich in ihre Entwicklungs- und Bereitstellungsverfahren zu integrieren. Siehe [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md) um mehr über AEM as a Cloud Service zu erfahren.

Ihre AEM as a Cloud Service Teammitglieder werden über die Admin Console beim Onboarding zu einem oder mehreren der folgenden Produktprofile hinzugefügt und zugewiesen.

* **AEM-Administratoren**: Die Rolle des AEM-Administrators wird in der Regel Entwicklern bzw. Entwicklerinnen zugewiesen, insbesondere jenen, die Zugriff auf beispielsweise die Entwicklungsumgebungen benötigen. Das Produktprofil des AEM-Administrators wird verwendet, um Administratorberechtigungen in der zugehörigen AEM zu gewähren.

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
>* Weitere Informationen zu AEM Produktprofilen finden Sie unter [Zuweisen AEM Produktprofilen](/help/journey-onboarding/assign-profiles-aem.md).
>* Weitere Informationen zum Onboarding-Prozess finden Sie unter [Onboarding-Journey](/help/journey-onboarding/overview.md).

## Cloud Manager-Produktprofile {#cloud-manager-product-profiles}

Cloud Manager verfügt über vorkonfigurierte Produktprofile, die man sich als rollenbasierte Berechtigungen vorstellen kann. Ihr(e) System-Admin ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, indem er/sie die Team-Mitglieder diesen Produktprofilen zuweist.

>[!TIP]
>
>Siehe [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) für weitere Details.

Jedem Produktprofil sind spezifische Berechtigungen zugeordnet.

* **Geschäftsinhaber**: In dieser Rolle haben Sie die Berechtigung, ein neues Programm hinzuzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren, Code in der AEM-Umgebung bereitzustellen oder Code-Qualitätsprüfungen durchzuführen.
* **Bereitstellungs-Manager**: In dieser Rolle sind Sie berechtigt, eine Umgebung hinzuzufügen oder zu aktualisieren, eine beliebige Pipeline auszuführen und Code in der AEM-Umgebung bereitzustellen oder Code-Qualitätsprüfungen durchzuführen.
* **Entwickler**: In dieser Rolle sind Sie berechtigt, persönliche Zugriffs-Token für den Zugriff auf Git zu generieren.
* **Programm-Manager**: In dieser Rolle sind Sie berechtigt, Pipelines zu planen, die dreistufigen Quality Gates außer Kraft zu setzen und Produktionsgenehmigungen zu erteilen.

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
>* Weitere Informationen zum Onboarding-Prozess finden Sie unter [Onboarding-Journey](/help/journey-onboarding/overview.md).
