---
title: AEM as a Cloud Service – Team- und Produktprofile
description: Auf dieser Seite erfahren Sie mehr über Team- und Produktprofile in AEM as a Cloud Service.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 56ca8e80081e62ceb3f5fc2bf9c32aa3bcee12c6
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 100%

---

# AEM as a Cloud Service – Team- und Produktprofile {#product-profiles}

## Produktprofile {#profiles}

Wenn Sie einem Benutzer Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihm nicht unbedingt uneingeschränkten Zugriff gewähren. Mit Produktprofilen kann jede Lösung über eigene Benutzerberechtigungen verfügen. Diese sind über die [Adobe Admin Console](/help/onboarding/learn-concepts/admin-console.md) verfügbar und zugänglich.

Lesen Sie mehr über [AEM as a Cloud Service-Produktprofile](#aem-product-profiles) und [Cloud Manager-Produktprofile](#cloud-manager-product-profiles), um zu verstehen, wie diese zusammenarbeiten, wenn Ihr Team eingerichtet wird.

## AEM as a Cloud Service-Produktprofile {#aem-product-profiles}

AEM as a Cloud Service ist das vollständig Cloud-native Angebot, das AEM als Service bereitstellt. Es bietet AEM auf Cloud-native Weise mit neuen Attributen wie „always on“ (immer aktiv), „always current“ (immer aktuell), „always secure“ (immer sicher) und „always at scale“ (immer skaliert). Gleichzeitig wird das wichtigste Wertversprechen aufrecht erhalten, das AEM als anpassbare Plattform für Kunden bereitstellt und es Teams in Unternehmen ermöglicht, sich in ihre Entwicklungs- und Bereitstellungsverfahren zu integrieren. Weitere Informationen zu AEM as a Cloud Service finden Sie unter [Einführung in Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=de).

Ihre AEM as a Cloud Service-Team-Mitglieder werden während des Onboardings über die Admin Console einem oder mehreren der folgenden Produktprofile hinzugefügt und zugewiesen.

* **AEM-Administratoren**: Ein AEM-Administrator wird in der Regel Entwicklern zugewiesen, insbesondere Entwicklern, die Zugriff auf beispielsweise die Entwicklungsumgebungen benötigen. Das Produktprofil „AEM-Administratoren“ wird verwendet, um Administratorberechtigungen in der zugehörigen AEM-Instanz zu gewähren.

* **AEM-Benutzer**: AEM-Benutzer sind die Benutzer in Ihrem Unternehmen, die AEM as a Cloud Service im Rahmen der Vereinbarung mit Adobe verwenden. Diese Mitglieder müssen Zugriff auf AEM haben, um ihre Aufgaben wahrnehmen zu können. Das Produktprofil „AEM-Benutzer“ wird in der Regel einem AEM-Inhaltsautor zugewiesen, der Inhalte erstellt und überprüft (dabei kann es sich um verschiedene Typen handeln). z. B. Seiten, Assets, Veröffentlichungen usw.), bevor sie auf Ihrer Website veröffentlicht werden. Diesen Mitgliedern wird das AEM-Benutzerproduktprofil zugewiesen, das unten angezeigt wird.

   ![](/help/onboarding/learn-concepts/assets/admin-console-profiles.png)

   >[!NOTE]
   >Jeder Benutzer, der einem AEM as a Cloud Service-Produktprofil zugewiesen ist, hat (schreibgeschützten) Zugriff auf Cloud Manager.

## Cloud Manager-Produktprofile {#cloud-manager-product-profiles}

Cloud Manager verfügt über vorkonfigurierte Produktprofile oder einfacher gesagt über rollenbasierte Berechtigungen. Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, indem er Benutzer diesen Produktprofilen zuweist. Er muss sich mit diesen Produktprofilen und den Team-Mitgliedern, denen diese Profile zugewiesen werden sollen, vertraut machen.
>[!NOTE]
>Weitere Informationen finden Sie unter [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/learn-concepts/cloud-manager-introduction.md##role-based-permissions).

Jedem der Produktprofile sind spezifische Berechtigungen zugeordnet. Beispiele für Rollen:

* **Geschäftsinhaber**: Sie sind berechtigt, ein neues Programm hinzuzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren, die Pipeline hinzuzufügen, zu bearbeiten oder zu löschen und jede Pipeline auszuführen sowie Code zur AEM-Umgebung oder Code-Qualitätsprüfung bereitzustellen.

* **Implementierungs-Manager**: Sie verfügen über die Berechtigung zum Hinzufügen oder Aktualisieren einer Umgebung, zum Ausführen einer beliebigen Pipeline und zum Bereitstellen von Code zur AEM-Umgebung oder Code-Qualitätsprüfung.

* **Entwickler**: Sie sind berechtigt, ein persönliches Zugriffs-Token für den Zugriff auf Git zu generieren.

* **Programm-Manager**: Sie sind berechtigt, Pipelines zu planen, dreistufige Quality Gates zu überschreiben und eine Produktionsgenehmigung zu erteilen.

Ein Benutzer kann mehreren Produktprofilen zugewiesen werden. Wenn Sie beispielsweise einem Anwender die Rollen „Geschäftsinhaber“ und „Implementierungs-Manager“ zuweisen, erhalten diese die Kombination oder Summe dieser Berechtigungen.

Ihr Cloud Manager-Team umfasst mindestens:

* Einen Geschäftsinhaber, der normalerweise auch Systemadministrator ist, und die erste Person sein muss, die sich anmeldet und auf Cloud Manager zugreift
* Einen Implementierungs-Manager
* Einen Entwickler

   >[!NOTE]
   >Um Zugriff auf AEM as a Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen angehören: `AEM Users` oder `AEM Administrators`. Sie müssen über Berechtigungen für die Instanz verfügen. Berechtigungen zum Verwalten des zugehörigen Cloud Manager reichen nicht aus.
