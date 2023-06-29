---
title: Voraussetzungen für die Verwendung des Content Transfer Tools
description: Voraussetzungen für die Verwendung des Content Transfer Tools
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 41%

---

# Voraussetzungen für die Verwendung des Content Transfer Tools {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
>abstract="Beachten Sie wichtige Überlegungen zur Verwendung des Content Transfer-Tools, einschließlich Java™- und AEM-Versionen, unterstützter Datenspeichertypen, Überlegungen zu Benutzergruppen und mehr."
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=de" text="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#best-practices" text="Best Practices und Richtlinien"

In der folgenden Tabelle sind die Voraussetzungen für die Verwendung des Content Transfer Tool zusammengefasst.

Überprüfen Sie alle unten aufgeführten Überlegungen:

| Zu beachten | Derzeit unterstützte Funktionen |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AEM-Version | Das Content Transfer Tool kann nur unter AEM 6.3 oder höheren Versionen ausgeführt werden. |
| Größe des Segmentspeichers | Ein bestehendes Repository mit weniger als 55 Millionen JCR-Knoten und bis zu 250 GB (online komprimierte Größe) in *Author* und 50 GB in *Publish* wird derzeit unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, damit Sie Optionen für die Segmentspeichergröße über diesen Beschränkungen diskutieren können. |
| Gesamtgröße des Content-Repositorys <br>*(Segmentspeicher + Datenspeicher)* | Das Content Transfer Tool wurde entwickelt, um bis zu 20 Terabyte für den Datenspeichertyp &quot;Dateidatenspeicher&quot;zu übertragen. Mehr als 20 Terabyte werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, damit Sie Optionen für Inhalte mit mehr als 20 Terabyte besprechen können. <br>Um die Inhaltsübertragung für große Repositorys erheblich zu beschleunigen, kann ein optionaler Schritt für eine [Vorabkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html#setting-up-pre-copy-step) verwendet werden. Dieser Vorgang gilt für den Dateidatenspeicher, Amazon S3 und Azure Data Store-Typen von Datenspeichern. Für Amazon S3 und Azure Data Store werden Repository-Größen von mehr als 20 Terabyte unterstützt. |
| Gesamtgröße des Lucene-Index | Gesamtgröße des Lucene-Index von 25 GB, ausgenommen `/oak:index/lucene` und `/oak:index/damAssetLucene` wird unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, damit Sie Optionen für die Indexgröße über diesem Limit besprechen können. |
| Knotennamenlänge | Die Länge eines Knotennamens muss 150 Byte oder weniger betragen, wenn der übergeordnete Pfad des Knotens >= (gleich oder größer) 350 Byte ist. Diese Knotennamen müssen auf &lt;= 150 Byte gekürzt werden, damit sie vom Knotenspeicher &quot;Dokument&quot;in AEM as a Cloud Service unterstützt werden. Übernahmen schlagen fehl, wenn diese langen Knotennamen nicht behoben sind. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool kann nicht verwendet werden, um Inhalte unter unveränderlichen Pfaden zu migrieren. So übertragen Sie Inhalte von `/etc`können Sie bestimmte `/etc` Pfade, aber nur zur Unterstützung [AEM Forms in AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html#paths-of-various-aem-forms-specific-assets). Alle anderen Anwendungsfälle finden Sie unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html) , um mehr über die Repository-Umstrukturierung zu erfahren. |
| Knoteneigenschaftswert in MongoDB | Die in MongoDB gespeicherten Knoteneigenschaftswerte dürfen 16 MB nicht überschreiten. Diese Regel wird von MongoDB durchgesetzt. Die Erfassung schlägt fehl, wenn die Eigenschaftswerte größer als diese Grenze sind. Bevor Sie eine Extraktion durchführen, führen Sie dieses [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar)-Skript aus. Überprüfen Sie alle großen Eigenschaftswerte und überprüfen Sie, ob sie benötigt werden. Die Werte, die 16 MB überschreiten, müssen in Binärwerte umgewandelt werden. |

## Wie geht es weiter {#whats-next}

Nachdem Sie die Voraussetzungen geprüft und festgestellt haben, ob Sie das Content Transfer Tool in Ihrem Migrationsprojekt verwenden können, lesen Sie [Richtlinien und Best Practices für die Verwendung des Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de).
