---
title: Voraussetzungen für die Verwendung des Content Transfer Tools
description: Machen Sie sich mit den Voraussetzungen für die Verwendung des Content Transfer Tools vertraut.
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
feature: Migration
role: Admin
source-git-commit: 3e3d018dfd4babce9abef858e487bf1c116ed3a6
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 100%

---


# Voraussetzungen für die Verwendung des Content Transfer Tools {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
>abstract="Lesen Sie die wichtigen Überlegungen zur Verwendung des Content Transfer Tools, einschließlich Java™- und AEM-Versionen, unterstützten Datenspeichertypen, Überlegungen zu Benutzergruppen und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=de" text="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de#best-practices" text="Best Practices und Richtlinien"

In der folgenden Tabelle sind die Voraussetzungen für die Verwendung des Content Transfer Tool zusammengefasst.

Machen Sie sich mit den im Folgenden aufgeführten Aspekten vertraut:

| Zu beachten | Derzeit unterstützte Funktionen |
|--------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AEM-Version | Das Content Transfer Tool kann nur unter AEM 6.3 oder höheren Versionen ausgeführt werden. |
| Größe des Segmentspeichers | Ein bestehendes Repository mit weniger als 750 Millionen JCR-Knoten und bis zu 500 GB (online komprimierte Größe) in *Author* und 50 GB in *Publish* wird derzeit unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Segmentspeichergröße oberhalb dieser Beschränkungen zu erörtern. |
| Gesamtgröße des Content-Repositorys <br>*(Segmentspeicher + Datenspeicher)* | Das Content Transfer Tool wurde entwickelt, um Inhalte für Dateidatenspeicher mit einer Kapazität von bis zu 20 Terabyte zu übertragen. Mehr als 20 Terabyte werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für Inhalte mit mehr als 20 Terabyte zu erörtern. <br>Um die Inhaltsübertragung für große Repositorys erheblich zu beschleunigen, kann ein optionaler Schritt für eine [Vorabkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#setting-up-pre-copy-step) verwendet werden. Dies gilt für die Speichertypen Dateidatenspeicher, Amazon S3 und Azure Data Store. Für Amazon S3 und Azure Data Store werden Repository-Größen von mehr als 20 Terabyte unterstützt. |
| Gesamtgröße des Lucene-Index | Es wird eine Gesamtgröße des Lucene-Index von maximal 25 GB unterstützt (ohne `/oak:index/lucene` und `/oak:index/damAssetLucene`). Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Indexgröße oberhalb dieser Beschränkungen zu erörtern. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool kann nicht verwendet werden, um Inhalte unter unveränderlichen Pfaden zu migrieren. Um Inhalte von `/etc` zu übertragen, können Sie bestimmte `/etc`-Pfade auswählen, aber nur zur Unterstützung von [AEM Forms zu AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html?lang=de#paths-of-various-aem-forms-specific-assets). Für alle anderen Anwendungsfälle finden Sie weitere Informationen zur Repository-Neustrukturierung unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html?lang=de). |
| Knoteneigenschaftswert in MongoDB | Die in MongoDB gespeicherten Knoteneigenschaftswerte dürfen 16 MB nicht überschreiten. Diese Regel wird von MongoDB durchgesetzt. Aufnahmen schlagen fehl, wenn die Datenmenge der Eigenschaftswerte über dieser Grenze liegt. Bevor Sie eine Extraktion durchführen, führen Sie dieses [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar)-Skript aus. Überprüfen Sie alle großen Eigenschaftswerte und überprüfen Sie, ob sie benötigt werden. Diejenigen, die 16 MB überschreiten, müssen in Binärwerte konvertiert werden. |

## Wie geht es weiter {#whats-next}

Nachdem Sie die Voraussetzungen geprüft und festgestellt haben, ob Sie das Content Transfer Tool für Ihr Migrationsprojekt verwenden können, sehen Sie sich die [Richtlinien und Best Practices bei der Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de) an.