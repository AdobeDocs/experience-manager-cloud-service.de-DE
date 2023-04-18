---
title: Einführung in benutzerdefinierte Domain-Namen
description: Mit der Benutzeroberfläche von Cloud Manager können Sie per Self-Service eine benutzerdefinierte Domain hinzufügen, um Ihre Site mit einem eindeutigen, markenspezifischen Namen zu identifizieren.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: cc6910bad0d0a62232bd66e0080b6802b9a1110b
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 82%

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

* Benutzerdefinierte Domänennamen werden in Cloud Manager sowohl für Veröffentlichungs- als auch für Vorschaudienste für Sites-Programme unterstützt. Benutzerdefinierte Domänen für Autorendienste werden nicht unterstützt.
* Jede Cloud Manager-Umgebung kann bis zu 500 benutzerdefinierte Domänen pro Umgebung hosten.
* Domänennamen können nicht zu Umgebungen hinzugefügt werden, solange eine aktuelle laufende Pipeline an diese Umgebungen angehängt ist.
* Derselbe Domänenname kann nicht in mehr als einer Umgebung verwendet werden.
* Es kann jeweils nur ein Domain-Name hinzugefügt werden.
* AEM as a Cloud Service unterstützt keine Platzhalterdomänen wie `*.example.com`.
* Bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, muss für Ihr Programm ein gültiges SSL-Zertifikat installiert werden, das den benutzerdefinierten Domänennamen enthält (Wildcard-Zertifikate sind gültig). Siehe [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) , um mehr zu erfahren.

>[!NOTE]
>
>Benutzerdefinierte Domänen werden in Cloud Manager **nur dann** unterstützt, wenn Sie das in AEM verwaltete CDN verwenden. Wenn Sie Ihr eigenes CDN einsetzen und [auf das in AEM verwaltete CDN verweisen](/help/implementing/dispatcher/cdn.md), müssen Sie dieses spezielle CDN statt Cloud Manager verwenden, um Domains zu verwalten.

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
>In der Regel ist das Einrichten benutzerdefinierter Domänennamen mit AEM as a Cloud Service ein einfacher Prozess. Gelegentlich kann es jedoch zu Problemen mit der Domain-Domain-Delegierung kommen, deren Behebung bis zu 1-2 Werktage dauern kann. Daher wird dringend empfohlen, die Domains rechtzeitig vor dem Tag ihrer Live-Schaltung zu installieren. Weitere Informationen finden Sie im Dokument [Überprüfen des Domain-Namensstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).
