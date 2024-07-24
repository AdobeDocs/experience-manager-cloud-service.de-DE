---
title: Einführung in benutzerdefinierte Domain-Namen
description: Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1c9924b4477d53d86bb72eda8597a02304450195
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 67%

---


# Einführung in benutzerdefinierte Domain-Namen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Verwalten von benutzerdefinierten Domain-Namen"
>abstract="Über die Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domain hinzufügen, um Ihre Website selbst mit einem eindeutigen, markenspezifischen Namen zu kennzeichnen."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Hinzufügen eines benutzerdefinierten Domain-Namens"
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Anzeigen und Aktualisieren eines benutzerdefinierten Domain-Namens"

Adobe Experience Manager as a Cloud Service wird mit einem Standard-Domain-Namen bereitgestellt, der auf `*.adobeaemcloud.com` endet. Mithilfe der Cloud Manager-Benutzeroberfläche können Sie eine benutzerdefinierte Domäne hinzufügen, um Ihre Site mit einem eindeutigen Markennamen auf Self-Service-Art zu identifizieren. Der standardmäßige Domänenname `*.adobeaemcloud.com` bleibt erhalten, selbst wenn Sie benutzerdefinierte Domänennamen mit Ihrer Website verknüpft haben.

## Was sind benutzerdefinierte Domain-Namen? {#what-are-custom-domain-names}

Jeder Website ist eine eindeutige, von Computern lesbare, numerische Adresse zugeordnet, z. B. `184.33.123.64`. Das Domain Name System (DNS) ermöglicht es Ihnen, benutzerdefinierte Marken-Domains an Websites anzuhängen, indem numerische Adressen in einprägsame Adressen wie `wknd.com` übersetzt werden.

Es empfiehlt sich, einen Domänennamen für Ihre Site zu haben, der für Ihre Kunden unvergesslich ist und Ihre Marke widerspiegelt.

Sie können einen Domain-Namen von einer Registrierungsstelle für Domain-Namen kaufen, einer Firma oder Organisation, die Domain-Namen verwaltet und verkauft. Registrierungsstellen für Domain-Namen verwalten Domain-Namen auf DNS-Servern.

>[!IMPORTANT]
>
>Cloud Manager ist keine Registrierungsstelle für Domain-Namen und bietet keine DNS-Services an.

## Benutzerdefinierte Domänennamen und BYO-CDNs {#byo-cdn}

AEM as a Cloud Service bietet einen integrierten CDN-Dienst (Content Delivery Network), ermöglicht Ihnen aber auch, Ihr eigenes CDN (BYO) für die Verwendung mit AEM bereitzustellen. Benutzerdefinierte Domänen können entweder im AEM verwalteten CDN oder einem von Ihnen verwalteten CDN installiert werden.

* Benutzerdefinierte Domänennamen (und Zertifikate), die im AEM verwalteten CDN installiert sind, werden über Cloud Manager verwaltet.
* Benutzerdefinierte Domänennamen (und Zertifikate), die in Ihrem eigenen CDN installiert sind, werden in diesem spezifischen CDN verwaltet.

**Domänen, die in Ihrem eigenen CDN verwaltet werden, müssen nicht über Cloud Manager installiert werden.** Sie werden AEM über den X-Forwarded-Host zur Verfügung gestellt und entsprechen den in der Dispatcher definierten Hosts. Weitere Informationen finden Sie in der [CDN-Dokumentation.](/help/implementing/dispatcher/cdn.md)

In einer Umgebung können Sie beide Domänen im von AEM verwalteten CDN und in Ihrem eigenen CDN installiert haben.

## Workflow {#workflow}

Das Hinzufügen eines benutzerdefinierten Domain-Namens erfordert die Interaktion zwischen dem DNS-Service und Cloud Manager. Daher sind verschiedene Schritte zum Installieren, Konfigurieren und Überprüfen benutzerdefinierter Domänennamen erforderlich. Die folgende Tabelle bietet einen Überblick über die erforderlichen Schritte, einschließlich Links zu Dokumentationsressourcen, um diese Schritte durchzuführen.

| Schritt | Beschreibung | Dokumentation |
|---|---|---|
| 1 | Hinzufügen eines SSL-Zertifikats zu Cloud Manager | [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | Benutzerdefinierte Domäne zu Cloud Manager hinzufügen | [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 3 | TXT-Datensatz zur Verifizierung der Domain hinzufügen | [Hinzufügen eines TXT-Datensatzes](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 4 | Überprüfen des Domänenverifizierungsstatus | [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 5 | DNS-Einstellungen konfigurieren, indem DNS-CNAME- oder APEX-Datensätze hinzugefügt werden, die auf AEM as a Cloud Service verweisen | [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 6 | Status von DNS-Datensätzen überprüfen | [Überprüfen des Status von DNS-Einträgen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>In der Regel ist das Einrichten benutzerdefinierter Domänennamen mit AEM as a Cloud Service ein einfacher Prozess. Gelegentlich können jedoch Probleme bei der Domain-Zuweisung auftreten, die 1-2 Werktage dauern können, bis sie gelöst sind. Daher wird dringend empfohlen, die Domains rechtzeitig vor dem Tag ihrer Live-Schaltung zu installieren. Weitere Informationen finden Sie im Dokument [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

## Einschränkungen {#limitations}

Die Verwendung benutzerdefinierter Domain-Namen mit AEMaaCS unterliegt einer Reihe von Einschränkungen.

* Benutzerdefinierte Domänennamen werden in Cloud Manager nur für Veröffentlichungs- und Vorschaudienste für Sites-Programme unterstützt.
   * Benutzerdefinierte Domänen für Autoren-Services werden nicht unterstützt.
* Jede Cloud Manager-Umgebung kann bis zu 500 benutzerdefinierte Domänen pro Umgebung hosten.
* Domänennamen können nicht zur Umgebung hinzugefügt werden, solange eine laufende Pipeline an diese Umgebung angeschlossen ist.
* Derselbe Domänenname kann nicht in mehreren Umgebungen verwendet werden.
* Es kann jeweils nur ein Domain-Name hinzugefügt werden.
* AEM as a Cloud Service unterstützt keine Platzhalterdomänen `*.example.com`.
* Bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, muss für Ihr Programm ein gültiges SSL-Zertifikat installiert werden, das den benutzerdefinierten Domänennamen enthält (Wildcard-Zertifikate sind gültig).

## Erste Schritte! {#get-started}

* Beginnen Sie mit der Konfiguration eines neuen benutzerdefinierten Domänennamens für Ihr Projekt, indem Sie [ein SSL-Zertifikat hinzufügen.](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* Verwalten Sie Ihre vorhandenen Domänennamen, indem Sie das Dokument [Verwalten benutzerdefinierter Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) lesen.
