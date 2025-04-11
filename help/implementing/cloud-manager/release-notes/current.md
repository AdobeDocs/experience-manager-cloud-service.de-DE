---
title: Versionshinweise für Cloud Manager 2025.4.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.4.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 6d6e3e452b7910148e22d95a222c1a3b674ea83b
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 60%

---

# Versionshinweise für Cloud Manager 2025.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Erfahren Sie mehr über die Cloud Manager-Version 2025.4.0 in AEM (Adobe Experience Manager) as a Cloud Service.


Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.4.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 10. April 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 8. Mai 2025 geplant.

## Neue Funktionen {#what-is-new}

* **(UI) Verbesserte Sichtbarkeit der Bereitstellung**

  Die Seite mit den Details zur Pipeline-Ausführung in Cloud Manager zeigt jetzt eine Statusmeldung (“*Warten - Andere Aktualisierung läuft*) an, wenn eine Bereitstellung darauf wartet, dass eine andere Bereitstellung abgeschlossen wird. Dieser Workflow erleichtert das Verständnis der Sequenzierung während der Umgebungsbereitstellung.  <!-- CMGR-66890 -->

  ![Dialogfeld „Entwicklungsbereitstellung“ mit Details und Aufschlüsselung](/help/implementing/cloud-manager/release-notes/assets/dev-deployment.png)

* Verbesserung der **(UI)-Domain-Validierung**

  Beim Hinzufügen einer Domain zeigt Cloud Manager jetzt einen Fehler an, wenn die Domain bereits in einem Fastly-Konto installiert ist: &quot;*Die Domain ist bereits in einem Fastly-Konto installiert. Bitte entfernen Sie sie zuerst von dort, bevor Sie sie zu Cloud Service hinzufügen.*&quot;

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adoption-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor deren allgemeiner Veröffentlichung zu erhalten.

Derzeit stehen die folgenden Möglichkeiten für eine frühzeitige Einführung zur Verfügung:

### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion zum **Einbringen des eigenen Git** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Pipelines, die externe Repositorys (ausgenommen GitHub-gehostete Repositorys) und die Option **Bereitstellungsauslöser** **Bei Git-Änderungen** verwenden, starten jetzt automatisch.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

### AEM Home {#aem-home}

AEM Home bietet einen zentralen Ausgangspunkt für das Verwalten von Inhalten, Assets und Sites in Adobe Experience Manager. AEM Home wurde für ein personalisiertes Erlebnis konzipiert und ermöglicht Ihnen die nahtlose Navigation im AEM-Ökosystem entsprechend Ihren Rollen und Zielen. Es dient als Leitfaden und bietet wichtige Einblicke und empfohlene Maßnahmen, mit denen Sie Ihre Ziele effizient erreichen können. Mit einem klaren, rollenbasierten Layout gewährleistet AEM Home schnellen Zugriff auf wichtige Tools und ermöglicht so ein optimiertes und effektives Erlebnis für alle AEM-Funktionen.

AEM Home steht Early-Adoptern zur Verfügung und bietet ein optimiertes Erlebnis, das auf die Verbesserung von Workflows, die Priorisierung von Zielen und die Bereitstellung von Ergebnissen ausgerichtet ist. Wenn Sie sich dafür entscheiden, können Sie die Entwicklung von AEM Home beeinflussen, indem Sie Feedback geben, um seine Zukunft mitzubestimmen und seinen Wert für die gesamte AEM-Community zu erhöhen.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com). Stellen Sie sicher, dass Sie die folgenden Informationen angeben:

* Die Rolle, die Ihrem Profil am besten entspricht: Inhaltsautor, Entwickler, Geschäftsinhaber, Admin oder Sonstige (geben Sie eine Beschreibung an).
* Ihre primäre Oberfläche für den Zugriff auf AEM: AEM Sites, AEM Assets, AEM Forms, Cloud Manager oder Sonstige (Beschreibung angeben).

## Fehlerbehebungen

* **Bei Zertifikaten fehlt das Feld „Allgemeiner Name (CN)**

  Cloud Manager löst beim Verarbeiten von EV/OV-Zertifikaten, die keinen Gebrauchsnamen (Common Name, CN) im Feld „Betreff“ enthalten, keine NullPointerException (NPE) und keine HTTP-Antwort vom Typ 500 mehr aus. Moderne Zertifikate lassen häufig die CN weg und verwenden stattdessen Subject Alternative Name (SAN). Diese Fehlerbehebung stellt sicher, dass die Abwesenheit von CN nicht mehr zu einem Fehler während des Konfigurationserstellungsprozesses führt, wenn SAN vorhanden ist. <!-- CMGR-67548 -->

* **Domain-Verifizierungsproblem mit falscher Zertifikatübereinstimmung**

  Cloud Manager überprüft Domains nicht mehr fälschlicherweise mit falschen Zertifikaten. Zuvor verwendete die Validierungslogik musterbasierte Übereinstimmungen anstelle exakter Übereinstimmungen, was dazu führte, dass Domains wie `should-not-be-verified.example.com` aufgrund von Überschneidungen mit gültigen Zertifikaten für `example.com` als überprüft angezeigt wurden. Durch diese Fehlerbehebung wird sichergestellt, dass bei der Domain-Validierung jetzt auf exakte Übereinstimmungen geprüft wird, sodass fehlerhafte Zertifikatverknüpfungen vermieden werden. <!-- CMGR-67225 -->

* **Erzwungene Eindeutigkeit für Vorwärtsnamen von erweiterten Netzwerk-Ports**

  Cloud Manager erzwingt jetzt eine eindeutige Benennung für die Weiterleitung erweiterter Netzwerk-Ports. Zuvor waren doppelte Namen zulässig, was zu Konflikten führen konnte. Diese Fehlerbehebung stellt sicher, dass jeder Port-Forward-Eintrag einen eigenen Namen hat, der mit den Best Practices für die Netzwerkkonfigurationsintegrität übereinstimmt. <!-- CMGR-67082 -->


<!-- ## Known issues {#known-issues} -->

