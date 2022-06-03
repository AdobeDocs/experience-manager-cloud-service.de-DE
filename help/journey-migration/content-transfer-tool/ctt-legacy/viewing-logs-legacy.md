---
title: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool (alt)
description: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 90%

---

# Anzeigen von Protokollen für einen Migrationssatz (veraltet) {#view-logs-content-transfer-tool}

Überprüfen Sie nach Abschluss der einzelnen Schritte (Extraktion und Aufnahme) die Protokolle und suchen Sie nach Fehlern.  Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder den Adobe-Support kontaktieren

## Schritte zum Anzeigen von Protokollen {#viewing-logs}

Auf der Seite *Übersicht* können Sie die Protokolle für einen vorhandenen Migrationssatz anzeigen.
Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht*, wählen Sie den zu löschenden Migrationssatz aus und klicken Sie in der Aktionsleiste auf **Protokoll anzeigen**.

   ![image](/help/journey-migration/content-transfer-tool/assets/view-log1.png)

1. Das Dialogfeld **Protokolle** wird angezeigt. Klicken Sie auf **Extraktionsprotokolle**, um die Protokolle in einer neuen Registerkarte anzuzeigen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets/view-log2.png)
Oder:

   Sie können die Protokolle für Ihren Migrationssatz auch über den Bildschirm *Übersicht* anzeigen. Wählen Sie den Migrationssatz aus und klicken Sie unter **EXTRAKTION** auf den Status. Klicken Sie in diesem Fall auf **FERTIG**, um die Protokolle in einer neuen Registerkarte anzuzeigen.

   ![image](/help/journey-migration/content-transfer-tool/assets/view-log3.png)

1. Um die Protokolle ohne Verwendung der Benutzeroberfläche zu verfolgen, können Sie SSH in Ihre AEM-Quellumgebung einbinden und die Datei `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file` verfolgen.
