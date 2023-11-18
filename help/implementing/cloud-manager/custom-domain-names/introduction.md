---
title: Einführung in benutzerdefinierte Domain-Namen
description: Mit der Benutzeroberfläche von Cloud Manager können Sie per Self-Service eine benutzerdefinierte Domain hinzufügen, um Ihre Site mit einem eindeutigen, markenspezifischen Namen zu identifizieren.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 86%

---


# Einführung in benutzerdefinierte Domain-Namen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Verwalten von benutzerdefinierten Domain-Namen"
>abstract="Mit der Benutzeroberfläche von Cloud Manager können Sie per Self-Service eine benutzerdefinierte Domain hinzufügen, um Ihre Site mit einem eindeutigen, markenspezifischen Namen zu identifizieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html?lang=de" text="Hinzufügen eines benutzerdefinierten Domain-Namens"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.html?lang=de" text="Benutzerdefinierte Domain-Namen anzeigen und aktualisieren"

Mit der Benutzeroberfläche von Cloud Manager können Sie per Self-Service eine benutzerdefinierte Domain hinzufügen, um Ihre Site mit einem eindeutigen, markenspezifischen Namen zu identifizieren. Adobe Experience Manager as a Cloud Service wird mit einem Standard-Domain-Namen bereitgestellt, der auf `*.adobeaemcloud.com` endet. Dieser Name bleibt selbst dann bestehen, wenn Sie Ihrer Website benutzerdefinierte Domain-Namen zuordnen.

## Was sind benutzerdefinierte Domain-Namen? {#what-are-custom-domain-names}

Jeder Website ist eine eindeutige, von Computern lesbare, numerische Adresse zugeordnet, z. B. `184.33.123.64`. Das Domain Name System (DNS) ermöglicht es Ihnen, benutzerdefinierte Markendomänen an Websites anzuhängen, indem numerische Adressen in speicherbare Adressen wie `wknd.com`.

Es empfiehlt sich, einen Domain-Namen für Ihre Site zu verwenden, der für Ihre Kunden einprägsam ist und Ihre Marke widerspiegelt.

Sie können einen Domain-Namen von einer Registrierungsstelle für Domain-Namen kaufen, einer Firma oder Organisation, die Domain-Namen verwaltet und verkauft. Registrierungsstellen für Domain-Namen verwalten Domain-Namen auf DNS-Servern.

>[!IMPORTANT]
>
>Cloud Manager ist keine Registrierungsstelle für Domain-Namen und bietet keine DNS-Services an.

## Benutzerdefinierte Domänennamen und BYO-CDNs {#byo-cdn}

AEM as a Cloud Service bietet einen integrierten Content Delivery Network (CDN)-Dienst, ermöglicht aber auch das Einbringen eines eigenen CDN (BYO) zur Verwendung mit AEM. Benutzerdefinierte Domänen können entweder im AEM verwalteten CDN oder einem von Ihnen verwalteten CDN installiert werden.

* Benutzerdefinierte Domänennamen (und Zertifikate), die im AEM verwalteten CDN installiert sind, werden über Cloud Manager verwaltet.
* Benutzerdefinierte Domänennamen (und Zertifikate), die in Ihrem eigenen CDN installiert sind, werden in diesem spezifischen CDN verwaltet.

Domains, die in Ihrem eigenen CDN verwaltet werden, müssen nicht über Cloud Manager installiert werden. Sie werden AEM über „X-Forwarded-Host“ zur Verfügung gestellt und stimmen mit den im Dispatcher definierten virtuellen Hosts überein. Weitere Informationen finden Sie in der [CDN-Dokumentation](/help/implementing/dispatcher/cdn.md).

In einer Umgebung können Sie beide Domänen im von AEM verwalteten CDN und in Ihrem eigenen CDN installiert haben.

## Workflow {#workflow}

Das Hinzufügen eines benutzerdefinierten Domain-Namens erfordert die Interaktion zwischen dem DNS-Service und Cloud Manager. Aus diesem Grund sind mehrere Schritte erforderlich, um benutzerdefinierte Domänennamen zu installieren, zu konfigurieren und zu überprüfen. In der folgenden Tabelle finden Sie einen Überblick über die erforderlichen Schritte, einschließlich der Schritte, die bei häufigen Fehlern durchgeführt werden müssen.

| Schritt | Beschreibung | Verantwortung | Weitere Informationen |
|--- |--- |--- |---|
| 1 | Hinzufügen eines SSL-Zertifikats zu Cloud Manager | Kunde | [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | TXT-Datensatz zur Verifizierung der Domain hinzufügen | Kunde | [Hinzufügen eines TXT-Datensatzes](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 3 | Verifizierungsstatus der Domain | Kunde | [Überprüfen des Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3a | Wenn die Domain-Verifizierung mit dem Status `Domain Verification Failure` fehlschlägt | Kunde | [Überprüfen des Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3b | Wenn die Domain-Verifizierung mit dem Status `Verified, Deployment Failed` fehlschlägt, kontaktieren Sie Adobe | Adobe-Kundenunterstützung | [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 4 | DNS-Einstellungen konfigurieren, indem DNS-CNAME- oder APEX-Datensätze hinzugefügt werden, die auf AEM as a Cloud Service verweisen | Kunde | [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 5 | Status von DNS-Datensätzen überprüfen | Kunde | [Überprüfen des Status von DNS-Einträgen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5a | Wenn der DNS-Datensatzstatus mit `DNS status not detected` fehlschlägt | Kunde | [Überprüfen des Status von DNS-Einträgen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5b | Wenn der DNS-Datensatzstatus mit `DNS resolves incorrectly` fehlschlägt | Kunde | [Überprüfen des Status von DNS-Einträgen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>In der Regel ist das Einrichten benutzerdefinierter Domänennamen mit AEM as a Cloud Service ein einfacher Prozess. Gelegentlich kann es jedoch zu Problemen mit der Domain-Domain-Delegierung kommen, deren Behebung bis zu 1-2 Werktage dauern kann. Daher wird dringend empfohlen, die Domains rechtzeitig vor dem Tag ihrer Live-Schaltung zu installieren. Weitere Informationen finden Sie im Dokument [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

## Einschränkungen {#limitations}

Die Verwendung benutzerdefinierter Domänennamen mit AEMaaCS unterliegt verschiedenen Einschränkungen.

* Benutzerdefinierte Domänennamen werden in Cloud Manager für Veröffentlichungs- und Vorschau-Services für Sites-Programme unterstützt. Benutzerdefinierte Domänen für Autoren-Services werden nicht unterstützt.
* Jede Cloud Manager-Umgebung kann bis zu 500 benutzerdefinierte Domänen pro Umgebung hosten.
* Domänennamen können nicht zu Umgebungen hinzugefügt werden, solange eine aktuelle, laufende Pipeline mit diesen Umgebungen verbunden ist.
* Derselbe Domänenname kann nicht in mehr als einer Umgebung verwendet werden.
* Es kann jeweils nur ein Domain-Name hinzugefügt werden.
* AEM as a Cloud Service unterstützt keine Platzhalterdomänen `*.example.com`.
* Vor dem Hinzufügen eines benutzerdefinierten Domänennamens muss ein gültiges SSL-Zertifikat, das den benutzerdefinierten Domänennamen enthält, für Ihr Programm installiert werden (Platzhalterzertifikate sind gültig). Weitere Informationen finden Sie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
