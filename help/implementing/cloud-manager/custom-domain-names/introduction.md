---
title: Einführung in benutzerdefinierte Domain-Namen
description: Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4e887b753eaf09e104c68484792f00dcb08ee304
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 67%

---


# Einführung in benutzerdefinierte Domänennamen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Verwalten von benutzerdefinierten Domain-Namen"
>abstract="Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Hinzufügen eines benutzerdefinierten Domain-Namens"
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Anzeigen und Aktualisieren eines benutzerdefinierten Domain-Namens"

Adobe Experience Manager as a Cloud Service wird mit einem standardmäßigen Domain-Namen bereitgestellt, der auf `*.adobeaemcloud.com` endet. Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen. Der standardmäßige Domain-Name `*.adobeaemcloud.com` bleibt selbst dann bestehen, wenn Sie Ihrer Website benutzerdefinierte Domain-Namen zuordnen.

## Was sind benutzerdefinierte Domänennamen? {#what-are-custom-domain-names}

Jeder Website ist eine eindeutige, von Computern lesbare, numerische Adresse zugeordnet, z. B. `184.33.123.64`. Das Domain Name System (DNS) ermöglicht es Ihnen, benutzerdefinierte Marken-Domains an Websites anzuhängen, indem numerische Adressen in einprägsame Adressen wie `wknd.com` übersetzt werden.

Es empfiehlt sich, einen Domain-Namen für Ihre Website zu verwenden, der für Ihre Kundschaft einprägsam ist und Ihre Marke widerspiegelt.

Sie können einen Domain-Namen von einer Registrierungsstelle für Domain-Namen kaufen, einer Firma oder Organisation, die Domain-Namen verwaltet und verkauft. Registrierungsstellen für Domain-Namen verwalten Domain-Namen auf DNS-Servern.

>[!IMPORTANT]
>
>Cloud Manager ist keine Registrierungsstelle für Domain-Namen und bietet keine DNS-Services an.

## Benutzerdefinierte Domänennamen und eigene CDNs {#byo-cdn}

AEM as a Cloud Service bietet einen integrierten Content Delivery Network (CDN)-Dienst, ermöglicht Ihnen aber auch das BYO (Bring Your Own) CDN zur Verwendung mit AEM. Benutzerdefinierte Domänen können entweder im AEM verwalteten CDN oder einem von Ihnen verwalteten CDN installiert werden.

* Cloud Manager verwaltet benutzerdefinierte Domänennamen und Zertifikate, die im AEM verwalteten CDN installiert sind.
* Benutzerdefinierte Domänennamen und Zertifikate, die in einem BYO-CDN installiert sind, werden direkt in diesem CDN verwaltet.

**Domänen, die in Ihrem eigenen CDN verwaltet werden, erfordern keine Installation über Cloud Manager** - Sie werden AEM über den X-Forwarded-Host zur Verfügung gestellt und entsprechen den in der Dispatcher definierten Hosts. Weitere Informationen finden Sie in der [CDN-Dokumentation](/help/implementing/dispatcher/cdn.md).

In einer Umgebung können Sie beide Domänen im AEM verwalteten CDN installieren und in einem BYO-CDN installieren.

## Workflow {#workflow}

Das Hinzufügen eines benutzerdefinierten Domain-Namens erfordert die Interaktion zwischen dem DNS-Service und Cloud Manager. Aufgrund dieses Workflows sind verschiedene Schritte erforderlich, um benutzerdefinierte Domänennamen zu installieren, zu konfigurieren und zu überprüfen. In der folgenden Tabelle finden Sie einen Überblick über die erforderlichen Schritte, einschließlich Links zur Dokumentation mit Informationen zur Durchführung dieser Schritte.

| Schritt | Beschreibung | Dokumentation |
|---|---|---|
| 1 | Hinzufügen eines SSL-Zertifikats zu Cloud Manager | [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | Hinzufügen einer Domain zu Cloud Manager | [Fügen Sie einen benutzerdefinierten Domänennamen hinzu](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 3 | Hinzufügen eines TXT-Eintrags zur Verifizierung der Domain | [TXT-Eintrag hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 4 | Überprüfen des Domain-Verifizierungsstatus | [Überprüfen des Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 5 | Konfigurieren der DNS-Einstellungen durch Hinzufügen von DNS-CNAME- oder APEX-Einträgen, die auf AEM as a Cloud Service verweisen | [DNS-Einstellungen konfigurieren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 6 | Überprüfen des Status von DNS-Einträgen | [Überprüfen des DNS-Datensatzstatus](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>In der Regel ist das Einrichten benutzerdefinierter Domänennamen mit AEM as a Cloud Service ein einfacher Prozess. Gelegentlich können jedoch Probleme bei der Domain-Zuweisung auftreten, die bis zur Behebung von 1-2 Werktagen erforderlich sein können. Daher wird dringend empfohlen, die Domains rechtzeitig vor dem Tag ihrer Live-Schaltung zu installieren. Weitere Informationen finden Sie im Dokument [Überprüfen des Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) .

## Einschränkungen {#limitations}

Die Verwendung benutzerdefinierter Domain-Namen mit AEMaaCS unterliegt einer Reihe von Einschränkungen.

* Benutzerdefinierte Domain-Namen werden in Cloud Manager nur für Veröffentlichungs- und Vorschau-Services für Sites-Programme unterstützt.
   * Benutzerdefinierte Domänen für Autoren-Services werden nicht unterstützt.
* Jede Cloud Manager-Umgebung kann bis zu 500 benutzerdefinierte Domänen pro Umgebung hosten.
* Domain-Namen können nicht zu Umgebungen hinzugefügt werden, solange eine laufende Pipeline an diese Umgebungen angeschlossen ist.
* Derselbe Domänenname kann nicht in mehr als einer Umgebung verwendet werden.
* Es kann jeweils nur ein Domain-Name hinzugefügt werden.
* AEM as a Cloud Service unterstützt keine Platzhalterdomänen `*.example.com`.
* Vor dem Hinzufügen eines benutzerdefinierten Domain-Namens muss ein gültiges SSL-Zertifikat, das den benutzerdefinierten Domain-Namen enthält, für Ihr Programm installiert werden (Platzhalterzertifikate sind gültig). 

## Erste Schritte {#get-started}

* Beginnen Sie mit der Konfiguration eines neuen benutzerdefinierten Domänennamens für Ihr Projekt, indem Sie [ein SSL-Zertifikat hinzufügen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
* Verwalten Sie die vorhandenen Domänennamen, indem Sie das Dokument [Benutzerdefinierte Domänennamen verwalten](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) durchlesen.
