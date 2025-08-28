---
title: Einführung in benutzerdefinierte Domain-Namen
description: Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: fdd86b966f0480c00b7cd975d63a48b82fb1d027
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 100%

---


# Einführung in benutzerdefinierte Domain-Namen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Verwalten von benutzerdefinierten Domain-Namen"
>abstract="Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Hinzufügen eines benutzerdefinierten Domain-Namens"
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Anzeigen und Aktualisieren eines benutzerdefinierten Domain-Namens"

Adobe Experience Manager as a Cloud Service wird mit einem standardmäßigen Domain-Namen bereitgestellt, der auf `*.adobeaemcloud.com` endet. Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen. Der standardmäßige Domain-Name `*.adobeaemcloud.com` bleibt selbst dann bestehen, wenn Sie Ihrer Website benutzerdefinierte Domain-Namen zuordnen.

## Was sind benutzerdefinierte Domain-Namen? {#what-are-custom-domain-names}

Jeder Website ist eine eindeutige, von Computern lesbare, numerische Adresse zugeordnet, z. B. `184.33.123.64`. Das Domain Name System (DNS) ermöglicht es Ihnen, benutzerdefinierte Marken-Domains an Websites anzuhängen, indem numerische Adressen in einprägsame Adressen wie `wknd.com` übersetzt werden.

Es empfiehlt sich, einen Domain-Namen für Ihre Website zu verwenden, der für Ihre Kundschaft einprägsam ist und Ihre Marke widerspiegelt.

Sie können einen Domain-Namen von einer Registrierungsstelle für Domain-Namen kaufen, einer Firma oder Organisation, die Domain-Namen verwaltet und verkauft. Registrierungsstellen für Domain-Namen verwalten Domain-Namen auf DNS-Servern.

>[!IMPORTANT]
>
>Cloud Manager ist keine Registrierungsstelle für Domain-Namen und bietet keine DNS-Services an.

## Benutzerdefinierte Domain-Namen und eigene CDNs {#byo-cdn}

AEM as a Cloud Service bietet einen integrierten CDN(Content Delivery Network)-Service, ermöglicht Ihnen aber auch, Ihr eigenes CDN (BYO, Bring Your Own) für AEM bereitzustellen. Benutzerdefinierte Domains können entweder im AEM verwalteten CDN oder einem von Ihnen verwalteten CDN installiert werden.

* Cloud Manager verwaltet benutzerdefinierte Domain-Namen und Zertifikate, die im von AEM verwalteten CDN installiert sind.
* Benutzerdefinierte Domain-Namen und Zertifikate, die in einem eigenen CDN installiert sind, werden direkt in diesem CDN verwaltet.

**Domains, die in Ihrem eigenen CDN verwaltet werden, erfordern keine Installation über Cloud Manager.** Sie werden AEM über „X-Forwarded-Host“ zur Verfügung gestellt und stimmen mit den im Dispatcher definierten virtuellen Hosts überein. Weitere Informationen finden Sie in der [CDN-Dokumentation](/help/implementing/dispatcher/cdn.md).

In einer Umgebung können Sie beide Domains im von AEM verwalteten CDN und in Ihrem eigenen CDN installiert haben.

## Workflow {#workflow}

Das Hinzufügen eines benutzerdefinierten Domain-Namens erfordert die Interaktion zwischen dem DNS-Service und Cloud Manager. Für diesen Workflow ist eine Reihe von Schritten zum Installieren, Konfigurieren und Überprüfen benutzerdefinierter Domain-Namen erforderlich. In der folgenden Tabelle finden Sie die erforderlichen Schritte, einschließlich Links zur Dokumentation mit Informationen zur Durchführung dieser Schritte.

>[!WARNING]
>
>Führen Sie Schritt 4 (DNS konfigurieren) *erst dann aus*, wenn Schritt 3 (Domain-Zuordnung hinzufügen) erfolgreich abgeschlossen wurde. Durch Einhalten dieser Reihenfolge wird die Domain beim CDN von Adobe registriert und das richtige Routing eingerichtet, um Ihre Site vor Domain-Übernahmen zu schützen.

| Schritt | Beschreibung |
| --- | --- |
| 1 | [SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | [Benutzerdefinierte Domain hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 3 | [Domain-Zuordnung hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 4 | [DNS konfigurieren](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#config-dns) |
| 5 | [DNS-Status überprüfen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>In der Regel ist das Einrichten benutzerdefinierter Domain-Namen mit AEM as a Cloud Service ein einfacher Prozess. Gelegentlich kann es jedoch zu Problemen mit der Domain-Delegierung kommen, deren Behebung 1 bis 2 Werktage dauern kann. Daher wird empfohlen, die Domains rechtzeitig vor dem Tag ihrer Live-Schaltung zu installieren. Weitere Informationen finden Sie im Dokument [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

## Nutzungshinweise {#usage-notes}

* Benutzerdefinierte Domain-Namen werden in Cloud Manager nur für Veröffentlichungs- und Vorschau-Services für Sites-Programme unterstützt.
   * Benutzerdefinierte Domänen für Autoren-Services werden nicht unterstützt.
* Jede Cloud Manager-Umgebung kann bis zu 500 benutzerdefinierte Domänen pro Umgebung hosten.
* Domain-Namen können nicht zu Umgebungen hinzugefügt werden, solange eine laufende Pipeline an diese Umgebungen angeschlossen ist.
* Derselbe Domain-Name kann nicht in mehreren Umgebungen verwendet werden.
* Es kann jeweils nur ein Domain-Name hinzugefügt werden.
* AEM as a Cloud Service unterstützt keine Platzhalterdomänen `*.example.com`.
* Vor dem Hinzufügen eines benutzerdefinierten Domain-Namens muss ein gültiges SSL-Zertifikat, das den benutzerdefinierten Domain-Namen enthält, für Ihr Programm installiert werden (Platzhalterzertifikate sind gültig). 
* Für die Verwendung eines benutzerdefinierten Domain-Namens mit der [Funktion „Frontend-Pipeline“](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md#custom-domains) sind zusätzliche Konfigurationsschritte erforderlich.

## Erste Schritte {#get-started}

* Beginnen Sie mit der Konfiguration eines neuen benutzerdefinierten Domain-Namens für Ihr Projekt, indem Sie ein [SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
* Verwalten Sie Ihre vorhandenen Domain-Namen, indem Sie die Informationen im Dokument [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) beachten.
