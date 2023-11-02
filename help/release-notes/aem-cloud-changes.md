---
title: Wesentliche Änderungen an Adobe Experience Manager (AEM) as a Cloud Service
description: Wesentliche Änderungen an Adobe Experience Manager (AEM) as a Cloud Service.
exl-id: fe11d779-66cd-45aa-aa6b-c819b88d2405
source-git-commit: 30edc83364dd9666b94f54048abc8b7f92ad6ce3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 50%

---

# Wesentliche Änderungen an Experience Manager as a Cloud Service {#notable-changes-aem-cloud}

Adobe Experience Manager (AEM) Cloud Service bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM. Es gibt jedoch einige Unterschiede zwischen AEM Sites On-Premise oder Adobe Managed Service im Vergleich zu AEM Cloud Service. In diesem Dokument wird auf die wichtigsten Unterschiede eingegangen.

>[!CONTEXTUALHELP]
>id="aem_cloud_notable_changes"
>title="Wesentliche Änderungen an AEM as a Cloud Service"
>abstract="Auf dieser Registerkarte können Sie Inhalte anzeigen, die Ihnen dabei helfen, die Unterschiede zwischen AEM On-Premise oder Adobe Managed Services im Vergleich zu AEM as a Cloud Service zu verstehen."
>additional-url="https://video.tv.adobe.com/v/330543?captions=ger" text="Weiterentwicklung von AEM as a Cloud Service"


>[!NOTE]
>In diesem Dokument werden die wesentlichen Änderungen an AEM als Ganzes hervorgehoben. Weitere Informationen und lösungsspezifische Änderungen finden Sie unter:
>
>* [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* [Neue Funktionen und Unterschiede](/help/overview/what-is-new-and-different.md) von Adobe Experience Manager as a Cloud Service im Vergleich zu vorherigen Versionen.
>* [Architektur](/help/overview/architecture.md) von Adobe Experience Manager as a Cloud Service
>* [Wesentliche Änderungen an AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Wesentliche Änderungen an AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)

Die wichtigsten Unterschiede sind in folgenden Bereichen festzustellen:

* [/apps und /libs sind zur Laufzeit unveränderlich](#apps-libs-immutable)

* [OSGi-Pakete und -Konfigurationen müssen als Code behandelt werden](#osgi)

* [Änderungen am Publishing-Repository sind nicht zulässig.](#changes-to-publish-repo)

* [Benutzerdefinierte Ausführungsmodi sind nicht zulässig](#custom-runmodes)

* [Entfernung von Replikations-Agenten   und damit zusammenhängenden Änderungen](#replication-agents)

* [Entfernung der klassischen Benutzeroberfläche](#classic-ui)

* [Bereitstellung auf Veröffentlichungsseite](#publish-side-delivery)

* [Asset-Handhabung und -Bereitstellung](#asset-handling)

## /apps und /libs sind zur Laufzeit unveränderlich {#apps-libs-immutable}

Alle Inhalte und Unterordner in `/apps` und `/libs` ist schreibgeschützt. Funktionen oder benutzerdefinierter Code, die dort Änderungen vornehmen sollen, können dies nicht tun. Es wird ein Fehler zurückgegeben, der besagt, dass diese Inhalte schreibgeschützt sind und der Schreibvorgang nicht abgeschlossen werden konnte. Dies wirkt sich auf verschiedene AEM aus:

* Änderungen in `/libs` sind überhaupt nicht zulässig.
   * Dies ist keine neue Regel, wurde jedoch in früheren On-Premise-Versionen von AEM nicht durchgesetzt.
* Überlagerungen für Bereiche in `/libs` , die überlagert werden können, sind weiterhin in `/apps`.
   * Solche Überlagerungen müssen über die CI/CD-Pipeline von Git stammen.
* Designinformationen für statische Vorlagen, die in gespeichert sind `/apps` kann nicht über die Benutzeroberfläche bearbeitet werden.
   * Es wird empfohlen, stattdessen bearbeitbare Vorlagen zu verwenden.
   * Wenn weiterhin statische Vorlagen erforderlich sind, müssen die Konfigurationsinformationen über die CI/CD-Pipeline von Git stammen.
* MSM-Blueprint und benutzerdefinierte MSM-Rollout-Konfigurationen müssen von Git über die CI/CD-Pipeline installiert werden.
* Änderungen an der I18n-Übersetzung müssen von Git über die CI/CD-Pipeline vorgenommen werden.

## OSGi-Pakete und -Konfigurationen müssen als Code behandelt werden {#osgi}

Änderungen an OSGi-Bundles und -Konfigurationen müssen über die CI/CD-Pipeline eingeführt werden.

* Neue oder aktualisierte OSGi-Bundles müssen über Git über die CI/CD-Pipeline eingeführt werden.
* Änderungen an OSGi-Konfigurationen können nur über die CI/CD-Pipeline von Git stammen.

Die Web-Konsole, die in früheren Versionen von AEM zum Ändern der OSGi- Konfiguration verwendet wird, ist in AEM Cloud Service nicht verfügbar.

## Änderungen am Veröffentlichungs-Repository sind nicht zulässig {#changes-to-publish-repo}

Abgesehen von Änderungen unter dem Ordner `/home` auf der Veröffentlichungsebene sind direkte Änderungen am Veröffentlichungs-Repository in AEM Cloud Service nicht zulässig. In früheren Versionen von On-Premise-AEM oder AEM auf AMS konnten Code-Änderungen direkt am Veröffentlichungs-Repository vorgenommen werden. Einige Einschränkungen können auf die folgenden Arten gemildert werden:

* Für inhalts- und inhaltsbasierte Konfiguration: Nehmen Sie Ihre Änderungen in der Autoreninstanz vor und veröffentlichen Sie sie.
* Für Code und Konfiguration: Nehmen Sie Ihre Änderungen im GIT-Repository vor und führen Sie die CI/CD-Pipeline aus, um sie einzuführen.

## Benutzerdefinierte Ausführungsmodi sind nicht zulässig {#custom-runmodes}

Zusätzliche oder benutzerdefinierte Ausführungsmodi sind in AEM Cloud Service nicht möglich. Eine Liste der standardmäßig für AEM Cloud Service bereitgestellten Ausführungsmodi finden Sie im Dokument . [Bereitstellung auf AEM as a Cloud Service.](/help/implementing/deploying/overview.md#runmodes)

## Entfernung von Replikations-Agenten   und damit zusammenhängenden Änderungen {#replication-agents}

In AEM Cloud Service werden Inhalte über [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) veröffentlicht. Die in früheren Versionen von AEM verwendeten Replikationsagenten werden nicht mehr verwendet oder bereitgestellt, was sich auf die folgenden Bereiche bestehender AEM-Projekte auswirken kann:

* Benutzerdefinierte Workflows, die Inhalte beispielsweise an Replikations-Agenten von Vorschau-Servern senden.
* Anpassung an Replikations-Agenten zur Umwandlung von Inhalten.
* Verwenden der Rückwärtsreplikation, um Inhalte aus der Veröffentlichung zurück in die Autoreninstanz zu bringen.

Darüber hinaus werden die Schaltflächen zum Anhalten und Deaktivieren aus der Verwaltungskonsole des Replikationsagenten entfernt.

## Entfernung der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist in AEM Cloud Service nicht mehr verfügbar.

## Bereitstellung auf Veröffentlichungsseite {#publish-side-delivery}

HTTP-Beschleunigung einschließlich CDN und Traffic-Management für Autoren- und Veröffentlichungsdienste werden in AEM Cloud Service standardmäßig bereitgestellt.

Bei Projekten, die von AMS oder einer lokalen Installation umgestellt werden, empfiehlt Adobe dringend die Verwendung des integrierten CDN, da die Funktionen in AEM Cloud Service für das bereitgestellte CDN optimiert sind.

## Asset-Handhabung und -Bereitstellung {#asset-handling}

Das Hochladen, Verarbeiten und Herunterladen von Assets wurde in [!DNL Experience Manager Assets] as a [!DNL Cloud Service] optimiert. AEM [!DNL Assets] ist jetzt effizienter, ermöglicht eine größere Skalierung und ermöglicht Ihnen, schneller hochzuladen und herunterzuladen. Außerdem wirkt sich dies auf den vorhandenen benutzerdefinierten Code und einige Vorgänge aus. Eine Liste der Änderungen und die Parität mit den Funktionen von [!DNL Experience Manager] 6.5 finden Sie unter [Änderungen an [!DNL Assets]](/help/assets/assets-cloud-changes.md).
