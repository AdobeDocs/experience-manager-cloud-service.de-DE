---
title: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool
description: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 100%

---

# Anzeigen von Protokollen für einen Migrationssatz {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Anzeigen von Protokollen"
>abstract="Überprüfen Sie nach Abschluss der Extraktion der Aufnahme die Protokolle auf Fehler/Warnungen. Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder den Adobe-Support kontaktieren"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#troubleshooting" text="Fehlerbehebung"
>additional-url="https://helpx.adobe.com/de/enterprise/admin-guide.html/de/enterprise/using/support-for-experience-cloud.ug.html" text="Kontaktaufnahme mit dem Adobe-Support"

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
