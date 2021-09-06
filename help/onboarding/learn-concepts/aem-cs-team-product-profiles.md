---
title: AEM als Cloud Service-Team und Produktprofile
description: Auf dieser Seite erfahren Sie mehr über AEM als Cloud Service-Team und Produktprofile.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 56ca8e80081e62ceb3f5fc2bf9c32aa3bcee12c6
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 8%

---

# AEM als Cloud Service-Team und Produktprofile {#product-profiles}

## Produktprofile {#profiles}

Wenn Sie einem Benutzer Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihm nicht unbedingt uneingeschränkten Zugriff gewähren. Produktprofile ermöglichen es jeder Lösung, über eigene Benutzerberechtigungen zu verfügen. Diese sind über [Adobe Admin Console](/help/onboarding/learn-concepts/admin-console.md) verfügbar und zugänglich.

Lesen Sie mehr über [AEM als Cloud Service-Produktprofile](#aem-product-profiles) und [Cloud Manager-Produktprofile](#cloud-manager-product-profiles) , um zu verstehen, wie diese bei der Teameinrichtung konzertiert funktionieren.

## AEM als Cloud Service - Produktprofile {#aem-product-profiles}

AEM as a Cloud Service ist das vollständig Cloud-native Angebot, das AEM als Dienst bereitstellt. Es bietet AEM auf Cloud-native Weise mit neuen Attributen wie immer on, immer aktuell, immer sicher und immer im Maßstab. Gleichzeitig wird der Hauptwert des Vorschlags beibehalten, der AEM als anpassbare Plattform für Kunden bereitstellt und es Teams der Unternehmensklasse ermöglicht, sich in ihre Entwicklungs- und Bereitstellungsverfahren zu integrieren. Weitere Informationen zu AEM als Cloud Service finden Sie unter [Einführung in Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=de) .

Ihre AEM als Cloud Service-Team-Mitglieder werden über die Admin Console beim Onboarding zu einem oder mehreren der folgenden Produktprofile hinzugefügt und zugewiesen.

* **AEM Administratoren**: Ein AEM Administrator wird in der Regel Entwicklern zugewiesen, insbesondere Entwicklern, die Zugriff auf beispielsweise die Entwicklungsumgebungen benötigen. Das Produktprofil AEM Administratoren wird verwendet, um Administratorberechtigungen in der zugehörigen AEM zu gewähren.

* **AEM-Benutzer**: AEM Benutzer sind die Benutzer in Ihrem Unternehmen, die AEM als Cloud Service im Rahmen der Vereinbarung mit Adobe verwenden. Diese Mitglieder müssen Zugriff auf AEM haben, um ihre Aufgaben wahrnehmen zu können. Das Produktprofil AEM Benutzer wird in der Regel einem AEM Inhaltsautor zugewiesen, der den Inhalt erstellt und überprüft (dabei kann es sich um verschiedene Typen handeln). z. B. Seiten, Assets, Veröffentlichungen usw.), bevor sie auf Ihrer Website veröffentlicht werden. Diesen Mitgliedern wird das AEM Benutzerproduktprofil zugewiesen, das unten angezeigt wird.

   ![](/help/onboarding/learn-concepts/assets/admin-console-profiles.png)

   >[!NOTE]
   >Jeder Benutzer, der einem AEM als Cloud Service-Produktprofil zugewiesen ist, hat (schreibgeschützt) Zugriff auf Cloud Manager.

## Cloud Manager-Produktprofile {#cloud-manager-product-profiles}

Cloud Manager verfügt über vorkonfigurierte Produktprofile, oder ganz einfach über rollenbasierte Berechtigungen. Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, indem er diesen Produktprofilen die zuweist. Er muss sich mit diesen Produktprofilen und dem Team-Mitglied, dem diese Profile zugewiesen werden sollen, vertraut machen.
>[!NOTE]
>Weitere Informationen finden Sie unter [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/learn-concepts/cloud-manager-introduction.md##role-based-permissions) .

Jedem Produktprofil sind spezifische Berechtigungen zugeordnet. Beispiele für Rollen:

* **Business Owner**: Sie sind berechtigt, ein neues Programm hinzuzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren, die Pipeline hinzuzufügen, zu bearbeiten/löschen und jede Pipeline auszuführen sowie Code für AEM Umgebung oder Codequalität bereitzustellen.

* **Implementierungs-Manager**: Sie verfügen über die Berechtigung zum Hinzufügen oder Aktualisieren einer Umgebung, zum Ausführen einer beliebigen Pipeline und zum Bereitstellen von Code zur AEM-Umgebung oder Code-Qualitätsprüfung.

* **Entwickler**: Sie haben die Berechtigung, ein persönliches Zugriffstoken für den Zugriff auf Git zu generieren.

* **Programm-Manager**, Sie sind berechtigt, Pipelines zu planen, dreistufige Quality Gates zu überschreiben und eine Produktionsgenehmigung zu erteilen.

Ein Benutzer kann mehreren Produktprofilen zugewiesen werden. Wenn einem Benutzer beispielsweise die Rollen Business Owner und Deployment Manager zugewiesen werden, erhalten diese die Kombination oder Summe dieser Berechtigungen.

Ihr Cloud Manager-Team umfasst mindestens:

* Ein Business Owner, normalerweise auch Systemadministrator, und muss die erste Person sein, die sich anmeldet und auf Cloud Manager zugreift
* One Deployment Manager
* Ein Entwickler

   >[!NOTE]
   >Um Zugriff auf AEM als Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen angehören: `AEM Users` oder `AEM Administrators`. Sie müssen über Berechtigungen für die Instanz verfügen. Berechtigungen zum Verwalten des zugehörigen Cloud Manager reichen nicht aus.
