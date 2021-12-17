---
title: Verwalten Ihrer Demosites
description: Erfahren Sie mehr über die Tools, die Ihnen bei der Verwaltung Ihrer Demosites helfen, und wie Sie diese entfernen können.
source-git-commit: cb04570664188635d6dc0237eb4ab0a9d347aaf2
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 1%

---


# Verwalten Ihrer Demosites {#manage-demo-sites}

Erfahren Sie mehr über die Tools, die Ihnen bei der Verwaltung Ihrer Demosites helfen, und wie Sie diese entfernen können.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Schnellsite-Journey [Site erstellen,](create-site.md) Sie haben eine neue Demosite erstellt, die auf den Vorlagen des Referenz-Demo-Add-ons basiert. Sie sollten jetzt:

* Erfahren Sie, wie Sie auf die AEM Authoring-Umgebung zugreifen.
* Erfahren Sie, wie Sie eine Site basierend auf einer Vorlage erstellen.
* Machen Sie sich mit den Grundlagen zum Navigieren in der Site-Struktur und Bearbeiten einer Seite vertraut.

Nachdem Sie nun Ihre eigene Demosite zur Verfügung haben, werden in diesem Artikel die verfügbaren Tools beschrieben, mit denen Sie Ihre Demosites verwalten und sie entfernen können.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie die von Ihnen erstellten Demosites verwalten können. Nach dem Lesen sollten Sie:

* Erfahren Sie, wie Sie auf die Self-Service-Demodienstprogramme zugreifen können.
* Erfahren Sie, welche Hilfsprogramme Ihnen zur Verfügung stehen.
* Löschen einer vorhandenen Demosite oder Vorlage.

## Zugriff auf die Self-Service-Demodienstprogramme {#accessing-utilities}

Da Sie nun über eigene Demosites verfügen, möchten Sie wahrscheinlich wissen, wie Sie diese verwalten können. Die Pipeline hat nicht nur die Site-Vorlagen bereitgestellt, um Ihre Demo-Sites-Inhalte bereitzustellen, sondern auch eine Reihe von Dienstprogrammen zur Verwaltung dieser Sites bereitgestellt.

1. Wählen Sie in der AEM globalen Navigationsleiste die Option **Instrumente** -> **Referenz-Demos** -> **Referenz Demo Utilities**.

   ![Self-Service-Demodienstprogramme](assets/demo-utilities.png)

1. Referenz Demo Utilities ist eine Sammlung nützlicher Funktionen, mit denen Sie Ihre Adobe Experience Manager-Umgebung einrichten und überwachen können. Die Ansicht beim Öffnen ist die **Dashboard**, die als Statusprüfung der Umgebung und ihrer Demofunktionalität dient.

   ![Dashboard](assets/dashboard.png)

Self-Service-Demo-Dienstprogramme bieten eine Reihe von Tools.

* **Sites löschen** - Wählen Sie die Site aus, die Sie in dieser Adobe Experience Manager-Instanz löschen möchten. Beachten Sie, dass es sich um eine destruktive Aktion handelt, die nicht rückgängig gemacht werden kann, sobald sie eingeleitet wurde.
* **Löschen von Site-Vorlagen** - Wählen Sie die Site-Vorlage aus, die Sie in dieser Adobe Experience Manager-Instanz löschen möchten. Bevor Sie eine Site-Vorlage löschen, stellen Sie sicher, dass auch alle Sites, die auf die Vorlage verweisen, gelöscht werden. Beachten Sie, dass es sich um eine destruktive Aktion handelt, die nicht rückgängig gemacht werden kann, sobald sie eingeleitet wurde.
* **Prime Author Cache** - Dadurch werden mehrere Ressourcen innerhalb der Adobe Experience Manager-Instanz abgerufen, wodurch die Abrufzeiten verkürzt werden. Es kann mehrere Sekunden dauern.
* **Android-App** - Tools zum Installieren und Starten der Android-Demo-App. Erstellen Sie eine Site basierend auf der **WKND Single Page App** , um diese Seite zu füllen. Verwendung von einem Android-Gerät, Emulator oder Bluestacks.
* **Benutzereinstellungen** - Popup-Dialogfelder für Tutorial deaktivieren.
* **GraphQL einrichten** - Richten Sie den globalen GraphQL-Endpunkt schnell ein.

## Löschen von Demosites und Vorlagen {#deleting}

Nachdem Sie eine Reihe von AEM getestet haben, benötigen Sie Ihre Demosite oder sogar die Vorlage, auf der sie basiert, möglicherweise nicht mehr. Es ist einfach, sowohl Demo-Sites als auch Site-Vorlagen zu löschen.

1. Zugriff auf **Referenz Demo Utilities** und tippen oder klicken Sie auf **Sites löschen**.

   ![Löschen von Sites](assets/delete-sites.png)

1. Die verfügbaren Sites werden in einer Liste dargestellt. Markieren Sie die Website(s), die Sie löschen möchten, und tippen oder klicken Sie auf **Löschen**.

   >[!CAUTION]
   >
   >Das Löschen von Sites und Vorlagen ist eine destruktive Aktion und kann nicht rückgängig gemacht werden, sobald sie initiiert wurden.

1. Bestätigen Sie den Löschvorgang der Site im Dialogfeld.

   ![Löschen der Site bestätigen](assets/confirm-site-delete.png)

1. AEM löscht die ausgewählte(n) Site(s) und zeigt den Fortschritt an, in dem die Variable **Löschen** -Schaltfläche verwendet.

   ![Fortschritt löschen](assets/delete-progress.png)

Die Site wird nun gelöscht.

Sie können Vorlagen auf die gleiche Weise unter der Überschrift löschen **Löschen von Site-Vorlagen** im **Referenz Demo Utilities**.

>[!CAUTION]
>
>Bevor Sie eine Site-Vorlage löschen, stellen Sie sicher, dass auch alle Sites, die auf die Vorlage verweisen, gelöscht werden.

## Ende der Journey? {#end-of-journey}

Herzlichen Glückwunsch! Sie haben die AEM Referenz Demos Add-On Journey abgeschlossen! Sie sollten jetzt:

* Sie verfügen über grundlegende Kenntnisse zu Cloud Manager und verstehen, wie Pipelines Inhalte und Konfigurationen für AEM bereitstellen.
* Erfahren Sie, wie Sie mit Cloud Manager ein neues Programm erstellen können.
* Erfahren Sie, wie Sie das Referenz-Demos-Add-On für das neue Programm aktivieren und eine Pipeline zum Bereitstellen des Add-On-Inhalts ausführen können.
* Erfahren Sie, wie Sie auf die AEM Authoring-Umgebung zugreifen können, um eine Site basierend auf einer Vorlage zu erstellen.
* Erfahren Sie, wie Sie auf die Self-Service-Demodienstprogramme zugreifen können.
* Erfahren Sie, wie Sie eine vorhandene Demosite oder Vorlage löschen.

Sie können jetzt die Funktionen von AEM mit Ihren eigenen Demosites erkunden. AEM ist jedoch ein leistungsstarkes Tool und es gibt viele zusätzliche Optionen. Sehen Sie sich einige der zusätzlichen Ressourcen an, die im Abschnitt [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources) um mehr über die Funktionen zu erfahren, die Sie auf dieser Journey gesehen haben.

## Zusätzliche Ressourcen {#additional-resources}

* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Wenn Sie weitere Details zu den Funktionen von Cloud Manager wünschen, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
* [Site erstellen](/help/sites-cloud/administering/site-creation/create-site.md) - Erfahren Sie, wie Sie AEM verwenden, um eine Site mithilfe von Site-Vorlagen zu erstellen, um den Stil und die Struktur Ihrer Site zu definieren.
* [Seitenbenennungskonventionen AEM.](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices) - Auf dieser Seite finden Sie die Konventionen zum Organisieren AEM Seiten.
* [AEM Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md) - Sehen Sie sich dieses Dokument an, wenn Sie mit grundlegenden Konzepten wie Navigation und Konsolenorganisation noch nicht vertraut AEM sind.
* [AEM as a Cloud Service technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) - Wenn Sie bereits über ein festes Verständnis der AEM verfügen, können Sie die ausführlichen technischen Dokumente direkt konsultieren.
* [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) - Wenn Sie mehr über die Struktur von Site-Vorlagen und deren Verwendung zur Erstellung von Sites erfahren möchten, lesen Sie dieses Dokument.
