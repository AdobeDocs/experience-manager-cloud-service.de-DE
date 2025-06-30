---
title: Bereitstellen eines benutzerdefinierten Designs
description: Erfahren Sie, wie Sie das Design der Site mithilfe der Pipeline bereitstellen.
exl-id: fe065972-39db-4074-a802-85895c701efd
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 34c2604c7dcc2a1b27f617fe2d88eeb7496b3456
workflow-type: ht
source-wordcount: '1002'
ht-degree: 100%

---

# Bereitstellen eines benutzerdefinierten Designs {#deploy-your-customized-theme}

{{traditional-aem}}

Erfahren Sie, wie Sie das Design der Site mithilfe der Pipeline bereitstellen.

## Ihre bisherige Tour {#story-so-far}

Im vorherigen Dokument der Tour zur schnellen AEM-Site-Erstellung, [Anpassen des Site-Designs](customize-theme.md), haben Sie gelernt, wie das Design erstellt wird, wie es angepasst wird und wie es mithilfe von AEM-Live-Inhalten getestet wird. Jetzt sollten Sie:

* Die grundlegende Struktur des Site-Designs und dessen Bearbeitung verstehen.
* Verstehen, wie Sie Ihre Design-Anpassungen mit echten AEM-Inhalten über einen lokalen Proxy testen können.
* Wissen, wie Sie Ihre Änderungen in das AEM Git-Repository übertragen.

Sie können jetzt den letzten Schritt ausführen und die Pipeline verwenden, um diese bereitzustellen.

## Ziel {#objective}

In diesem Dokument wird erläutert, wie Sie das Design mithilfe der Pipeline bereitstellen. Nach dem Lesen sollten Sie:

* Wissen, wie Sie eine Pipeline-Bereitstellung auslösen können.
* Verstehen, wie Sie den Bereitstellungsstatus überprüfen.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt für Frontend-Entwickler.

## Starten der Pipeline {#start-pipeline}

Nachdem Sie die Design-Anpassung am AEM-Git-Repository vorgenommen haben, können Sie [die von Admins erstellte Pipeline](pipeline-setup.md) ausführen, um die Änderungen zu implementieren.

1. Melden Sie sich bei Cloud Manager [wie beim Abrufen Ihrer Git-Zugriffsinformationen](retrieve-access.md) an und greifen Sie auf Ihr Programm zu. Auf der Registerkarte **Übersicht** sehen Sie eine Karte für **Pipelines**.

   ![Übersicht über Cloud Manager](assets/cloud-manager-overview.png)

1. Wählen Sie die Auslassungspunkte neben der Pipeline aus, die Sie starten müssen. Wählen Sie im Dropdown-Menü **Ausführen**.

   ![Pipeline ausführen](assets/run-pipeline.png)

1. Wählen Sie im Bestätigungsdialogfeld **Pipeline ausführen** die Option **Ja** aus. 

   ![Pipeline-Ausführung bestätigen](assets/pipeline-confirm.png)

1. In der Liste der Pipelines zeigt die Spalte „Status“ an, dass die Pipeline jetzt ausgeführt wird.

   ![Pipeline-Ausführungsstatus](assets/pipeline-running.png)

## Überprüfen des Pipeline-Status {#pipeline-status}

Sie können den Status der Pipeline überprüfen, um sich über die Details des Fortschritts zu informieren.

1. Wählen Sie die Auslassungspunkte neben der Pipeline aus.

   ![Pipeline-Details anzeigen](assets/view-pipeline-details.png)

1. Das Pipeline-Detailfenster zeigt die Aufschlüsselung des Pipeline-Fortschritts an.

   ![Pipeline-Details](assets/pipeline-details.png)

>[!TIP]
>
>Im Fenster „Pipeline-Details“ können Sie **Download-Protokoll** auswählen, um jeden Schritt der Pipeline für die Fehlerbehebung anzuzeigen, falls einer der Schritte fehlschlagen sollte. Das Debuggen der Pipeline würde den Rahmen dieser Tour sprengen. Die technischen Dokumente für Cloud Manager finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) dieser Seite.

## Überprüfen der bereitgestellten Anpassungen {#view-customizations}

Sobald die Pipeline abgeschlossen ist, können Sie den Administrator bitten, die Änderungen zu validieren. Der Administrator wird dann:

1. Die AEM-Authoring-Umgebung öffnen.
1. Navigieren Sie zu [der von der bzw. dem Admin zuvor erstellten Site](create-site.md).
1. Bearbeiten Sie eine der Inhaltsseiten.
1. Sehen Sie sich die angewendeten Änderungen an.

![Angewendete Änderungen](assets/changes-applied.png)

## Tour beendet? {#end-of-journey}

Herzlichen Glückwunsch! Sie haben die AEM-Journey zur schnellen Site-Erstellung abgeschlossen! Sie sollten jetzt:

* Wissen, wie Cloud Manager und die Frontend-Pipeline bei der Verwaltung und Bereitstellung von Frontend-Anpassungen funktionieren.
* Wissen, wie Sie eine AEM-Site basierend auf einer Vorlage erstellen und wie Sie das Sitedesign herunterladen.
* Gelernt haben, wie Sie einen Frontend-Entwickler hinzufügen, damit er auf das AEM-Git-Repository zugreifen kann.
* Das Design mit AEM-Proxy-Inhalt anpassen und testen und diese Änderungen an AEM-Git übertragen können.
* Die Frontend-Anpassung mithilfe der Pipeline bereitstellen können.

Sie können jetzt die Designs Ihrer eigenen AEM-Site anpassen. Bevor Sie jedoch mit der Erstellung verschiedener Workflows mit mehreren Frontend-Pipelines beginnen, lesen Sie das Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md). Damit können Sie die Frontend-Entwicklung wie folgt optimal nutzen:

* Pflegen einer einzigen Quelle für Daten.
* Aufrechterhalten einer Trennung von Interessen.

AEM ist ein leistungsfähiges Tool, und es stehen viele zusätzliche Optionen zur Verfügung. Schauen Sie sich einige der zusätzlichen Ressourcen an, die im Abschnitt [Zusätzliche Ressourcen](#additional-resources) verfügbar sind, um mehr über die Funktionen zu erfahren, die Sie während dieser Tour gesehen haben.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie einige zusätzliche Ressourcen, die näher auf einige der in diesem Dokument erwähnten Konzepte eingehen.

* [Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs](/help/sites-cloud/administering/site-creation/site-rail.md): Erfahren Sie mehr über die leistungsstarken Funktionen der Site-Leiste, mit denen Sie Ihr Site-Design einfach anpassen und verwalten können, einschließlich des Herunterladens von Design-Quellen und der Verwaltung von Design-Versionen.
* [AEM as a Cloud Service – Technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) – Wenn Sie bereits über ein solides Verständnis von AEM verfügen, können Sie direkt unsere ausführlichen technischen Dokumente hinzuziehen.
* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=de) – Wenn Sie an weiteren Details zu den Funktionen von Cloud Manager interessiert sind, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
* [Rollenbasierte Berechtigungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html?lang=de): Cloud Manager verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Weitere Informationen zu diesen Rollen und deren Verwaltung finden Sie in diesem Dokument.
* [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md) – Weitere Informationen zum Einrichten und Verwalten von Git-Repositorys für Ihr AEMaaCS-Projekt finden Sie in diesem Dokument.
* [Konfigurieren der CI/CD-Pipeline – Cloud Services](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) – Weitere Informationen zum Einrichten von Pipelines, sowohl für den vollständigen Stapel als auch für das Frontend, finden Sie in diesem Dokument.
* [AEM-Standard-Site-Vorlage](https://github.com/adobe/aem-site-template-standard) – Dies ist das GitHub-Repository der AEM-Standard-Site-Vorlage.
* [AEM-Sitedesign](https://github.com/adobe/aem-site-template-standard-theme-e2e) – Dies ist das GitHub-Repository des AEM-Sitedesigns.
* [npm](https://www.npmjs.com) - AEM-Designs, die zum schnellen Erstellen von Sites verwendet werden, die auf nmp basieren.
* [webpack](https://webpack.js.org): AEM-Designs, die zum schnellen Erstellen von Sites verwendet werden, verwenden webpack.
* [Organisieren von Seiten](/help/sites-cloud/authoring/sites-console/organizing-pages.md) – In dieser Anleitung wird beschrieben, wie Sie Seiten Ihrer AEM-Site organisieren.
* [Erstellen von Seiten](/help/sites-cloud/authoring/sites-console/creating-pages.md) – In dieser Anleitung wird beschrieben, wie Sie neue Seiten zu Ihrer Site hinzufügen.
* [Verwalten von Seiten](/help/sites-cloud/authoring/sites-console/managing-pages.md) – In dieser Anleitung wird beschrieben, wie Sie die Seiten Ihrer Site verwalten, einschließlich Verschieben, Kopieren und Löschen.
* [Arbeiten mit Paketen](/help/implementing/developing/tools/package-manager.md) – Pakete ermöglichen den Import und Export von Repository-Inhalten. In diesem Dokument wird erläutert, wie Sie mit Paketen in AEM 6.5 arbeiten. Dies gilt auch für AEMaaCS.
* [Onboarding-Journey](/help/journey-onboarding/overview.md) – Dieses Handbuch dient als Ausgangspunkt, um sicherzustellen, dass Ihre Teams eingerichtet sind und Zugriff auf AEM as a Cloud Service haben.
* [Dokumentation zu Adobe Experience Manager Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de) – Vollständige Details zu den Funktionen finden Sie in der Dokumentation zu Cloud Manager.
* [Dokumentation zur Site-Administration](/help/sites-cloud/administering/site-creation/create-site.md) – Weitere Informationen zu den Funktionen des Tools für die schnelle Site-Erstellung finden Sie in den technischen Dokumenten zur Site-Erstellung.
* [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) – In diesem Dokument werden einige Überlegungen beschrieben, die Sie beachten sollten, um das gesamte Potenzial des Frontend-Entwicklungsprozesses mithilfe der Frontend-Pipeline optimal zu nutzen.
