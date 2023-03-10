---
title: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool
description: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
source-git-commit: fac037b59753ba1de960df47311c1febc2059d27
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Anzeigen von Protokollen für einen Migrationssatz {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Anzeigen von Protokollen"
>abstract="Überprüfen Sie nach Abschluss der Extraktion der Aufnahme die Protokolle auf Fehler/Warnungen. Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder den Adobe-Support kontaktieren"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#troubleshooting" text="Fehlerbehebung"
>additional-url="https://helpx.adobe.com/de/enterprise/admin-guide.html/de/enterprise/using/support-for-experience-cloud.ug.html" text="Kontaktaufnahme mit dem Adobe-Support"

Überprüfen Sie nach Abschluss der einzelnen Schritte (Extraktion und Aufnahme) die Protokolle und suchen Sie nach Fehlern.  Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder den Adobe-Support kontaktieren

## Schritte zum Anzeigen von Protokollen {#viewing-logs}

### Extraktionsprotokolle

Um die Extraktionsprotokolle anzuzeigen, navigieren Sie zu Ihrer Adobe Experience Manager-Quellinstanz und wählen Sie dann den gewünschten Migrationssatz aus.

Gehen Sie dann wie folgt vor:

1. Wählen Sie einen Migrationssatz aus und klicken Sie in der Aktionsleiste auf **Protokoll anzeigen**. Dadurch wird das Dialogfeld „Protokolle“ angezeigt. Klicken Sie auf **Extraktionsprotokoll**, um die Protokolle auf einer neuen Registerkarte anzuzeigen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam25.png) \
   Oder klicken Sie auf den Status **BEENDET**, um die Protokolle auf einer neuen Registerkarte anzuzeigen.

1. Um die Protokolle ohne Verwendung der Benutzeroberfläche zu verfolgen, können Sie SSH in Ihre AEM-Quellumgebung einbinden und die Datei `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file` verfolgen.

### Aufnahmeprotokolle

Rufen Sie die Aufnahmeprotokolle auf, indem Sie in Cloud Acceleration Manager die Liste der Aufnahmevorgänge aufrufen. Suchen Sie dann den gewünschten Migrationsauftrag und klicken Sie auf die drei Punkte (**...**) des Auftrags. Sie können dann auf **Protokoll herunterladen** klicken, um Protokolle herunterzuladen.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam28.png)
