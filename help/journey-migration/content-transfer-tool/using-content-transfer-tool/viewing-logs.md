---
title: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool
description: Anzeigen von Protokollen für einen Migrationssatz im Content Transfer Tool
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
source-git-commit: 9a098eefbb730ae2930169cf7402ab4799043291
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 59%

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

Um die Extraktionsprotokolle anzuzeigen, navigieren Sie zu Ihrer Adobe Experience Manager-Quellinstanz und wählen Sie dann den gewünschten Migrationssatz aus.

Gehen Sie dann wie folgt vor:

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Protokoll anzeigen** in der Aktionsleiste aus. Dadurch wird das Dialogfeld Protokolle angezeigt. Klicken **Extraktionsprotokoll** um die Protokolle in einer neuen Registerkarte anzuzeigen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam25.png) \
   Oder klicken Sie auf die **FERTIG** Status , um die Protokolle in einer neuen Registerkarte anzuzeigen.

1. Um die Protokolle ohne Verwendung der Benutzeroberfläche zu verfolgen, können Sie SSH in Ihre AEM-Quellumgebung einbinden und die Datei `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file` verfolgen.

1. Um Aufnahmeprotokolle anzuzeigen, gehen Sie zur Liste der Aufnahmevorgänge in Cloud Acceleration Manager und klicken Sie auf die drei Punkte (**...**). Sie können dann auf **Protokoll herunterladen** um Protokolle herunterzuladen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam28.png)
