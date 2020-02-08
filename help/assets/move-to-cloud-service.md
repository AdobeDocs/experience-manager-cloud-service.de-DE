---
title: Migration zum Cloud-Dienst von Adobe Experience Manager 6.x
description: Migration zum Cloud-Dienst von Adobe Experience Manager 6.x
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Zu Adobe Experience Manager Assets als Cloud-Dienst wechseln {#move-to-assets-cloud-service}

<!-- About the need to move from previous AEM deployment to a cloud service deployment. And how does Adobe help do it OOTB?
-->

## Info zum Migrationswerkzeug {#migration-tool}

<!-- 
Link back to information about the tool in the Experience Manager as a Cloud Service docs if the tool works the same for Sites and Assets. Document the Assets-specific information here.

* What is the migration tool called? Is there a branding term for it?
* How much do we want to elaborate about the Pattern Detector rules? Is there a branding term for it?
* Before migrating using the tool, is any prepping required?
* See CQ-4271901

-->

Mit dem Migrationswerkzeug können Sie Folgendes erreichen:

* Konvertieren Sie die vorhandenen Workflow-Modelle in Verarbeitungsprofile, die mit dem Assets Compute Service funktionieren.
* Entfernen Sie nicht unterstützte Schritte aus den Workflow-Modellen.
* Deaktivieren Sie Workflow-Starter.
* Zusammenführen Sie die Konfigurationen nach der Benutzerbestätigung/-überprüfung im vorhandenen Quellcode.

Das Migrationswerkzeug erstellt Verarbeitungsprofile in einem Maven-Modul, die Benutzer auf zwei Arten verwenden können:

* Zusammenführen zu einem ihrer bestehenden Projekte.
* Fügen Sie das Modul als neues Untermodul hinzu.

Das Migrationswerkzeug enthält einen Bericht über die vorgenommenen Änderungen und Informationen zu den Änderungen.

<!--  

What is the output of the tool, besides migrated content.

Give details about reports and logs of the tool. 

* How to access the report, including required permissions.
* How to read/interpret the report.
* Location of logs. How to read the logs.
* What common errors to look for. Troubleshooting for these errors.

-->

## Migrieren von Inhalten in eine neue Bereitstellung {#content-migration-across-deployments}
