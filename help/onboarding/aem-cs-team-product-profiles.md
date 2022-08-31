---
title: AEM as a Cloud Service – Team- und Produktprofile
description: Erfahren Sie, wie AEM as a Cloud Service Team und Produktprofile den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und beschränken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: d54c25791cbb06232ff6e24bb7b8005b366a2144
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 28%

---

# AEM as a Cloud Service – Team- und Produktprofile {#product-profiles}

Erfahren Sie, wie AEM as a Cloud Service Team und Produktprofile den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und beschränken.

## Produktprofile {#profiles}

Wenn Sie einem Benutzer Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihm nicht unbedingt uneingeschränkten Zugriff gewähren. Produktprofile ermöglichen es jeder Lösung, über eigene Benutzerberechtigungen zu verfügen. Diese sind über den Link [Admin Console.](/help/journey-onboarding/admin-console.md)

## AEM as a Cloud Service-Produktprofile {#aem-product-profiles}

AEM as a Cloud Service ist ein vollständig Cloud-natives Angebot, das AEM als Dienst bereitstellt. Es bietet AEM auf Cloud-native Weise mit neuen Attributen wie „always on“ (immer aktiv), „always current“ (immer aktuell), „always secure“ (immer sicher) und „always at scale“ (immer skaliert). Gleichzeitig wird das wichtigste Wertversprechen aufrecht erhalten, das AEM als anpassbare Plattform für Kunden bereitstellt und es Teams in Unternehmen ermöglicht, sich in ihre Entwicklungs- und Bereitstellungsverfahren zu integrieren. Weitere Informationen zu AEM as a Cloud Service finden Sie unter [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md).

Ihre AEM as a Cloud Service Teammitglieder werden über die Admin Console beim Onboarding zu einem oder mehreren der folgenden Produktprofile hinzugefügt und zugewiesen.

* **AEM Administratoren**: Ein AEM Administrator wird in der Regel Entwicklern zugewiesen, insbesondere Entwicklern, die Zugriff auf beispielsweise die Entwicklungsumgebungen benötigen. Das Produktprofil des AEM-Administrators wird verwendet, um Administratorberechtigungen in der zugehörigen AEM zu gewähren.

* **AEM**: AEM Benutzer sind die Benutzer in Ihrer Organisation, die AEM as a Cloud Service verwenden, um Inhalte zu erstellen. Diese Benutzer müssen auf AEM zugreifen, um ihre Aufgaben zu erledigen. Das Produktprofil AEM Benutzer wird in der Regel einem AEM Inhaltsautor zugewiesen, der den Inhalt erstellt und überprüft. Dieser Inhalt kann viele Arten von Inhalten umfassen, z. B. Seiten, Assets, Veröffentlichungen usw. Diese Mitglieder erhalten das AEM Produktprofil der Benutzer, das unten angezeigt wird.

![Produktprofile](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Jeder Benutzer, der einem AEM as a Cloud Service-Produktprofil zugewiesen ist, hat (schreibgeschützten) Zugriff auf Cloud Manager.

>[!TIP]
>
>Weiterführende Informationen zum Onboarding finden Sie im Abschnitt [Onboarding-Journey.](/help/journey-onboarding/overview.md)

## Cloud Manager-Produktprofile {#cloud-manager-product-profiles}

Cloud Manager verfügt über vorkonfigurierte Produktprofile, die als rollenbasierte Berechtigungen betrachtet werden können. Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, indem er sie diesen Produktprofilen zuweist.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument . [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) für weitere Details.

Jedem Produktprofil sind spezifische Berechtigungen zugeordnet.

* **Business Owner** - In dieser Rolle können Sie ein neues Programm hinzufügen oder ein Programm bearbeiten, eine Umgebung hinzufügen oder aktualisieren, Code in AEM Umgebung bereitstellen oder Code-Qualitätsprüfungen durchführen.
* **Bereitstellungsmanager** - In dieser Rolle sind Sie berechtigt, eine Umgebung hinzuzufügen oder zu aktualisieren, eine beliebige Pipeline auszuführen, Code für AEM Umgebung bereitzustellen oder Code-Qualitätsprüfungen durchzuführen.
* **Entwickler** - In dieser Rolle haben Sie die Berechtigung, persönliche Zugriffstoken für den Zugriff auf Git zu generieren.
* **Programm-Manager** - In dieser Rolle sind Sie berechtigt, Pipelines zu planen, die dreistufigen Quality Gates zu überschreiben und eine Produktionsgenehmigung zu erteilen.

Ein Benutzer kann mehreren Produktprofilen zugewiesen werden. Beispielsweise können Sie beide **Business Owner** und **Implementierung verwalten** r -Rollen einem Benutzer die Summe dieser Berechtigungen geben.

Ihr Cloud Manager-Team umfasst mindestens:

* One **Business Owner**, in der Regel auch der Systemadministrator ist und die erste Person sein muss, die sich anmeldet und auf Cloud Manager zugreift
* One **Bereitstellungsmanager**
* One **Entwickler**

>[!NOTE]
>
>Um Zugriff auf AEM as a Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen angehören: `AEM Users` oder `AEM Administrators`. Berechtigungen zum Verwalten von Cloud Manager reichen nicht aus.
