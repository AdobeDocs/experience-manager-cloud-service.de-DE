---
title: Migration zu Cloud Service von Adobe Experience Manager 6.x
description: Migration zu Cloud Service von Adobe Experience Manager 6.x
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Wechseln zu Adobe Experience Manager Assets as a Cloud Service {#move-to-assets-cloud-service}

<!-- About the need to move from previous AEM deployment to a cloud service deployment. And how does Adobe help do it OOTB?
-->

## Über das Migrations-Tool {#migration-tool}

<!-- 
Link back to information about the tool in the Experience Manager as a Cloud Service docs if the tool works the same for Sites and Assets. Document the Assets-specific information here.

* What is the migration tool called? Is there a branding term for it?
* How much do we want to elaborate about the Pattern Detector rules? Is there a branding term for it?
* Before migrating using the tool, is any prepping required?
* See CQ-4271901

-->

Mit dem Migrations-Tool können Sie Folgendes erreichen:

* Konvertieren vorhandener Workflow-Modelle in Verarbeitungsprofile, die mit dem Assets Compute Service verwendet werden können
* Entfernen nicht unterstützter Schritte aus den Workflow-Modellen
* Deaktivieren von Workflow-Launchern
* Zusammenführen von Konfigurationen – nach der Benutzerbestätigung/-validierung – im vorhandenen Quell-Code

Das Migrations-Tool erstellt Verarbeitungsprofile in einem Maven-Modul, die Benutzer auf zwei Arten verwenden können:

* Zusammenführen in einem bestehenden Projekt
* Hinzufügen des Moduls als neues Untermodul

Das Migrations-Tool stellt einen Bericht über die vorgenommenen Änderungen sowie Informationen zu den Änderungen bereit.

<!--  

What is the output of the tool, besides migrated content.

Give details about reports and logs of the tool. 

* How to access the report, including required permissions.
* How to read/interpret the report.
* Location of logs. How to read the logs.
* What common errors to look for. Troubleshooting for these errors.

-->

## Migrieren von Inhalten in eine neue Bereitstellung {#content-migration-across-deployments}
