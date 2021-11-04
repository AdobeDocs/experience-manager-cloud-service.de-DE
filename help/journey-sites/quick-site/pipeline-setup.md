---
title: Einrichten der Pipeline
description: Erstellen Sie eine Front-End-Pipeline, um die Anpassung des Designs Ihrer Site zu verwalten.
source-git-commit: f8695dd8fdc9ffb203bab943c335ab2957df6251
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 1%

---


# Einrichten Ihrer Pipeline {#set-up-your-pipeline}

Erstellen Sie eine Front-End-Pipeline, um die Anpassung des Designs Ihrer Site zu verwalten.

>[!CAUTION]
>
>Das Tool für die schnelle Site-Erstellung ist derzeit eine technische Vorschau. Sie wird zu Test- und Evaluierungszwecken bereitgestellt und ist nicht zur Verwendung in der Produktion bestimmt, es sei denn, sie wurde mit der Adobe Support vereinbart.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Schnellsite-Journey [Erstellen einer Site aus Vorlage,](create-site.md) Sie haben gelernt, wie Sie mit einer Site-Vorlage schnell eine AEM Site erstellen können, die mithilfe von Frontend-Tools weiter angepasst werden kann. Jetzt sollten Sie:

* Erfahren Sie, wie Sie AEM Site-Vorlagen abrufen.
* Erfahren Sie, wie Sie mit einer Vorlage eine neue Site erstellen.
* Erfahren Sie, wie Sie die Vorlage von Ihrer neuen Website herunterladen können, um sie für den Frontend-Entwickler bereitzustellen.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie eine Front-End-Pipeline einrichten können, die der Frontend-Entwickler später im Journey zur Bereitstellung von Frontend-Anpassungen verwendet.

## Ziel {#objective}

In diesem Dokument erfahren Sie mehr über Front-End-Pipelines und die Erstellung einer Pipeline zur Verwaltung der Bereitstellung des angepassten Designs Ihrer Site. Nach dem Lesen sollten Sie:

* Erfahren Sie, was eine Front-End-Pipeline ist.
* Erfahren Sie, wie Sie eine Front-End-Pipeline in Cloud Manager einrichten.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt für den Cloud Manager-Administrator.

## Voraussetzungen {#requirements}

* Sie benötigen Zugriff auf Cloud Manager.
* Sie müssen Mitglied der **Bereitstellungsmanager** Rolle in Cloud Manager.
* In Cloud Manager muss ein Git-Repo für die AEM-Umgebung eingerichtet werden.
   * Dies ist im Allgemeinen bereits bei allen aktiven Projekten der Fall. Ist dies nicht der Fall, lesen Sie bitte die Dokumentation zu Cloud Manager-Repositorys , die im Abschnitt [Zusätzliche Ressourcen](#additional-resources) Abschnitt.

## Was ist eine Front-End-Pipeline? {#front-end-pipeline}

Die Frontend-Entwicklung umfasst die Anpassung von JavaScript, CSS und statischen Ressourcen, die den Stil Ihrer AEM-Site definieren. Der Frontend-Entwickler arbeitet in seinen eigenen lokalen Umgebungen, um diese Anpassungen vorzunehmen. Sobald sie bereit sind, werden die Änderungen an das AEM Git-Repository übertragen. Sie werden jedoch nur in den Quellcode übertragen. Sie sind noch nicht am Leben.

Die Front-End-Pipeline übernimmt diese zugewiesenen Anpassungen und stellt sie in einer AEM Umgebung bereit, im Allgemeinen in Produktions- oder Nicht-Produktionsumgebungen.

Auf diese Weise kann die Front-End-Entwicklung getrennt von und parallel zu jeder vollständigen Stack-Back-End-Entwicklung auf AEM funktionieren, die über eigene Bereitstellungs-Pipelines verfügt.

>[!NOTE]
>
>Die Frontend-Pipelines können nur JavaScript-, CSS- und statische Ressourcen bereitstellen, um Ihre AEM Site zu gestalten. Site-Inhalte wie Seiten oder Assets können nicht in einer Pipeline bereitgestellt werden.

## Zugriff auf Cloud Manager {#login}

1. Melden Sie sich bei Adobe Experience Cloud an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Stellen Sie nach der Anmeldung sicher, dass Sie sich in der richtigen Organisation befinden, indem Sie sie in der oberen rechten Ecke des Bildschirms überprüfen. Wenn Sie nur Mitglied einer Organisation sind, ist dieser Schritt nicht erforderlich. Tippen oder klicken Sie dann auf **Experience Manager**.

   ![Übersicht über Experience Cloud](assets/experience-cloud-overview.png)

1. Tippen oder klicken Sie auf der nächsten Seite auf die **Launch** , um **Cloud Manager** App.

   ![Experience Manager Apps](assets/experience-manager-apps.png)

1. Auf der nächsten Seite werden die verschiedenen verfügbaren Programme aufgelistet. Tippen oder klicken Sie auf den Ordner, den Sie verwalten möchten. Wenn Sie gerade mit AEM as a Cloud Service beginnen, haben Sie wahrscheinlich nur ein Programm zur Verfügung.

   ![Auswählen eines Programms in Cloud Manager](assets/cloud-manager-select-program.png)

Jetzt wird eine Übersicht über Ihren Cloud Manager angezeigt. Ihre Seite sieht anders aus, ähnelt aber diesem Beispiel.

![Übersicht über Cloud Manager](assets/cloud-manager-overview.png)

Notieren Sie den Namen des Programms, auf das Sie zugegriffen haben, oder kopieren Sie die URL. Sie müssen dies später dem Frontend-Entwickler bereitstellen.

## Erstellen einer Front-End-Pipeline {#create-front-end-pipeline}

Nachdem Sie auf Cloud Manager zugegriffen haben, können Sie eine Pipeline für die Frontend-Bereitstellung erstellen.

1. Im **Pipelines** Tippen oder klicken Sie auf der Seite &quot;Cloud Manager&quot;auf die **Hinzufügen** Schaltfläche.

   ![Pipelines](assets/pipelines-add.png)

1. Im Popup-Menü, das unter dem **Hinzufügen** Schaltflächenauswahl **Hinzufügen einer produktionsfremden Pipeline** für die Zwecke dieser Journey.

1. Im **Konfiguration** des **Hinzufügen einer produktionsfremden Pipeline** Dialogfeld, das geöffnet wird:
   * Auswählen **Bereitstellungs-Pipeline**.
   * Geben Sie der Pipeline einen Namen im **Name der produktionsfremden Pipeline** -Feld.

   ![Pipeline-Konfiguration hinzufügen](assets/add-pipeline-configuration.png)

1. Tippen oder klicken Sie auf **Weiter**.

1. Im **Quellcode** tab:
   * Auswählen **Frontend-Code** als den Typ des bereitzustellenden Codes.
   * Stellen Sie sicher, dass die richtige Umgebung unter ausgewählt ist. **Förderfähige Bereitstellungsumgebungen**.
   * Richtig auswählen **Repository**.
   * Definieren Sie, **Git-Verzweigung** Die Pipeline sollte mit verknüpft werden.
   * Definieren Sie die **Code-Speicherort** , wenn sich die Frontend-Entwicklung unter einem bestimmten Pfad im ausgewählten Repository befindet. Der Standardwert ist der Stamm des Repositorys, aber häufig befinden sich die Front-End-Entwicklung und das Backend unter verschiedenen Pfaden.

   ![Quellcode-Informationen zum Hinzufügen der Pipeline](assets/add-pipeline-source-code.png)

1. Tippen oder klicken Sie auf **Speichern**.

Die neue Pipeline wird erstellt und im **Pipelines** im Cloud Manager-Fenster angezeigt. Wenn Sie auf das Auslassungszeichen nach dem Pipeline-Namen klicken, werden Optionen zum weiteren Bearbeiten oder Anzeigen von Details angezeigt.

![Pipeline-Optionen](assets/new-pipeline.png)

>[!TIP]
>
>Wenn Sie bereits mit Pipelines in AEMaaCS vertraut sind und mehr über die Unterschiede zwischen den verschiedenen Pipelines erfahren möchten, einschließlich weiterer Informationen zur Frontend-Pipeline, lesen Sie bitte die Informationen unter Konfigurieren der CI/CD-Pipeline - Cloud Services, die in der [Zusätzliche Ressourcen](#additional-resources) unten.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der Journey zur AEM Schnellseitenerstellung abgeschlossen haben, sollten Sie Folgendes tun:

* Erfahren Sie, was eine Front-End-Pipeline ist.
* Erfahren Sie, wie Sie eine Front-End-Pipeline in Cloud Manager einrichten.

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit der Journey zur AEM SchnellSite-Erstellung fort, indem Sie das Dokument erneut überprüfen. [Gewähren von Zugriff für Frontend-Entwickler,](grant-access.md) wo Sie die Frontend-Entwickler in Cloud Manager integrieren, damit sie Zugriff auf Ihr Git-Repository und Ihre AEM-Pipeline haben.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zur Schnellseitenerstellung zu wechseln, indem Sie das Dokument lesen [Anpassen des Site-Designs,](customize-theme.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Wenn Sie weitere Details zu den Funktionen von Cloud Manager wünschen, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
* [Cloud Manager-Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) - Weitere Informationen zum Einrichten und Verwalten von Git-Repositorys für Ihr AEMaaCS-Projekt finden Sie in diesem Dokument.
* [Konfigurieren der CI/CD-Pipeline - Cloud Services](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) - Weitere Informationen zum Einrichten von Pipelines, sowohl für den vollständigen Stapel als auch für das Frontend, finden Sie in diesem Dokument.