---
title: Einführung in benutzerdefinierte Domain-Namen
description: Mit der Benutzeroberfläche von Cloud Manager können Sie per Self-Service eine benutzerdefinierte Domain hinzufügen, um Ihre Site mit einem eindeutigen, markenspezifischen Namen zu identifizieren.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: 01ff58fee9d309de75afcb556726e1cf32b9f70a
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 83%

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

Jeder Website ist eine eindeutige, von Computern lesbare, numerische Adresse zugeordnet, z. B. `184.33.123.64`. Das Domain Name System (DNS) ermöglicht es Ihnen, benutzerdefinierte Marken-Domains an Websites anzuhängen, indem numerische Adressen in einprägsame Adressen wie `wknd.com` übersetzt werden.

Es empfiehlt sich, einen Domain-Namen für Ihre Site zu verwenden, der für Ihre Kunden einprägsam ist und Ihre Marke widerspiegelt.

Sie können einen Domain-Namen von einer Registrierungsstelle für Domain-Namen kaufen, einer Firma oder Organisation, die Domain-Namen verwaltet und verkauft. Registrierungsstellen für Domain-Namen verwalten Domain-Namen auf DNS-Servern.

>[!IMPORTANT]
>
>Cloud Manager ist keine Registrierungsstelle für Domain-Namen und bietet keine DNS-Services an.

## Beschränkungen {#limitations}

Die Verwendung benutzerdefinierter Domain-Namen mit AEMaaCS unterliegt einer Reihe von Beschränkungen.

* Benutzerdefinierte Domain-Namen werden in Cloud Manager für Veröffentlichungs- und Vorschau-Services für Sites-Programme unterstützt. Benutzerdefinierte Domains werden auf der Autorenseite nicht unterstützt.
* Jede Cloud Manager-Umgebung kann bis zu 500 benutzerdefinierte Domains pro Umgebung hosten.
* AEM as a Cloud Service unterstützt keine Platzhalter-Domains.
* Vor dem Hinzufügen eines benutzerdefinierten Domain-Namens muss ein gültiges SSL-Zertifikat, das den benutzerdefinierten Domain-Namen enthält, für Ihr Programm installiert werden. Weitere Informationen finden Sie unter „Hinzufügen eines SSL-Zertifikats“.
* Domain-Namen können nicht zu Umgebungen hinzugefügt werden, solange eine laufende Pipeline an diese Umgebungen angeschlossen ist.
* Es kann jeweils nur ein Domain-Name hinzugefügt werden.
* Derselbe Domain-Name kann nicht in mehren Umgebungen verwendet werden.

>[!NOTE]
>
>Benutzerdefinierte Domänen werden in Cloud Manager unterstützt **only** wenn Sie das AEM verwaltete CDN verwenden. Wenn Sie Ihr eigenes CDN und [verweisen auf das AEM verwaltete CDN](/help/implementing/dispatcher/cdn.md) Sie müssen dieses spezifische CDN verwenden, um Domänen zu verwalten, die nicht von Cloud Manager sind.

## Workflow {#workflow}

Das Hinzufügen eines benutzerdefinierten Domain-Namens erfordert die Interaktion zwischen dem DNS-Service und Cloud Manager. Aus diesem Grund ist eine Reihe von Schritten zum Installieren, Konfigurieren und Überprüfen benutzerdefinierter Domain-Namen erforderlich. In der folgenden Tabelle finden Sie einen Überblick über die erforderlichen Schritte, einschließlich der Schritte, die bei häufigen Fehlern durchgeführt werden müssen.

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
>Das Einrichten benutzerdefinierter Domänennamen mit AEM as a Cloud Service ist normalerweise ein einfacher Prozess. Gelegentlich kann es jedoch zu Problemen mit der Domain-Zuweisung kommen, die bis zur Behebung von Problemen 1-2 Werktage dauern können. Daher wird dringend empfohlen, die Domänen lange vor ihrem Live-Datum zu installieren. Siehe Dokument . [Überprüfen des Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) für weitere Informationen.
