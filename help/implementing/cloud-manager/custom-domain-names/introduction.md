---
title: Einführung in benutzerdefinierte Domänennamen
description: In der Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domäne hinzufügen, um Ihre Site mit einem eindeutigen Markennamen auf Self-Service-Art zu identifizieren.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: cc1b0d653706150c616ceafd002dc7594b6c7072
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 37%

---


# Einführung in benutzerdefinierte Domänennamen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Verwalten von benutzerdefinierten Domain-Namen"
>abstract="In der Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domäne hinzufügen, um Ihre Site mit einem eindeutigen Markennamen auf Self-Service-Art zu identifizieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html?lang=de" text="Hinzufügen eines benutzerdefinierten Domain-Namens"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.html?lang=de" text="Benutzerdefinierte Domain-Namen anzeigen und aktualisieren"

In der Benutzeroberfläche von Cloud Manager können Sie eine benutzerdefinierte Domäne hinzufügen, um Ihre Site mit einem eindeutigen Markennamen auf Self-Service-Art zu identifizieren. Adobe Experience Manager as a Cloud Service erhält einen standardmäßigen Domänennamen, der auf `*.adobeaemcloud.com`. Dieser standardmäßige Domänenname bleibt erhalten, selbst wenn Sie Ihrer Website benutzerdefinierte Domänennamen zuweisen.

## Was sind benutzerdefinierte Domänennamen? {#what-are-custom-domain-names}

Jeder Website ist eine eindeutige, maschinenlesbare, numerische Adresse zugeordnet, z. B. `184.33.123.64`. Das Domain Name System (DNS) ermöglicht es Ihnen, benutzerdefinierte Markendomänen an Websites anzuhängen, indem numerische Adressen in speicherbare Adressen wie `wknd.com`.

Es empfiehlt sich, einen Domänennamen für Ihre Site zu verwenden, der für Ihre Kunden unvergesslich ist und Ihre Marke widerspiegelt.

Sie können einen Domain-Namen von einer Domain-Namenregistrierungsstelle kaufen, einer Firma oder Organisation, die Domain-Namen verwaltet und verkauft. Domänennamenregistrierungen verwalten Domänennamen auf DNS-Servern.

>[!IMPORTANT]
>
>Cloud Manager ist keine Domain-Namenregistrierungsstelle und bietet keine DNS-Services an.

## Beschränkungen {#limitations}

Die Verwendung benutzerdefinierter Domänennamen mit AEMaaCS unterliegt einer Reihe von Einschränkungen.

* Benutzerdefinierte Domänennamen werden in Cloud Manager sowohl für Veröffentlichungs- als auch für Vorschau-Services für Sites-Programme unterstützt. Benutzerdefinierte Domains werden auf der Autorenseite nicht unterstützt.
* Jede Cloud Manager-Umgebung kann bis zu 500 benutzerdefinierte Domains pro Umgebung hosten.
* AEM as a Cloud Service unterstützt keine Platzhalter-Domains.
* Bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, muss für Ihr Programm ein gültiges SSL-Zertifikat installiert werden, das den benutzerdefinierten Domänennamen enthält. Weitere Informationen finden Sie unter Hinzufügen eines SSL-Zertifikats.
* Domain-Namen können nicht zur Umgebung hinzugefügt werden, solange eine laufende Pipeline an diese Umgebung angeschlossen ist.
* Es kann jeweils nur ein Domain-Name hinzugefügt werden.
* Derselbe Domain-Name kann nicht in mehr als einer Umgebung verwendet werden.

## Workflow {#workflow}

Das Hinzufügen eines benutzerdefinierten Domänennamens erfordert die Interaktion zwischen dem DNS-Dienst und Cloud Manager. Aus diesem Grund sind eine Reihe von Schritten zum Installieren, Konfigurieren und Überprüfen benutzerdefinierter Domänennamen erforderlich. In der folgenden Tabelle finden Sie einen Überblick über die erforderlichen Schritte, einschließlich der Schritte, die bei häufigen Fehlern durchgeführt werden müssen.

| Schritt | Beschreibung | Verantwortung | Weitere Informationen |
|--- |--- |--- |---|
| 1 | SLL-Zertifikat zu Cloud Manager hinzufügen | Kunde | [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | TXT-Eintrag zur Verifizierung der Domäne hinzufügen | Kunde | [Hinzufügen eines TXT-Datensatzes](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 3 | Verifizierungsstatus der Domain | Kunde | [Überprüfen des Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3a | Wenn die Domänenüberprüfung mit dem Status fehlschlägt `Domain Verification Failure` | Kunde | [Überprüfen des Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3b | Wenn die Domänenüberprüfung mit dem Status fehlschlägt `Verified, Deployment Failed`, Adobe kontaktieren | Adobe-Kundenunterstützung | [Überprüfen des Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 4 | DNS-Einstellungen konfigurieren, indem DNS-CNAME- oder APEX-Einträge hinzugefügt werden, die auf AEM as a Cloud Service verweisen | Kunde | [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 5 | DNS-Eintragsstatus überprüfen | Kunde | [Überprüfen des Status von DNS-Einträgen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5a | Wenn der DNS-Datensatzstatus mit `DNS status not detected` | Kunde | [Überprüfen des Status von DNS-Einträgen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5b | Wenn der DNS-Datensatzstatus mit `DNS resolves incorrectly` | Kunde | [Überprüfen des Status von DNS-Einträgen](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
