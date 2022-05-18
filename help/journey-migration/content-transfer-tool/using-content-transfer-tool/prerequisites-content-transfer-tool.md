---
title: Voraussetzungen für die Verwendung des Content Transfer Tools
description: Voraussetzungen für die Verwendung des Content Transfer Tools
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
source-git-commit: 4ccebe19d38f1ece58ea7170344ef2fd86a513d2
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 89%

---

# Voraussetzungen für die Verwendung des Content Transfer Tools {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
>abstract="Lesen Sie die wichtigen Überlegungen zur Verwendung des Content Transfer Tools, einschließlich Java- und AEM-Versionen, unterstützten Datenspeichertypen, Überlegungen zu Benutzergruppen und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#pre-reqs" text="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#best-practices" text="Best Practices und Richtlinien"

In der folgenden Tabelle sind die Voraussetzungen für die Verwendung des Content Transfer Tool zusammengefasst.

Machen Sie sich mit den im Folgenden aufgeführten Aspekten vertraut:

| Zu beachten | Derzeit unterstützte Funktionen |
|--- |--- |
| AEM-Version | Das Content Transfer Tool kann nur unter AEM 6.3 oder höheren Versionen ausgeführt werden. |
| Größe des Segmentspeichers | Derzeit werden vorhandene Repositorys mit weniger als 55 Millionen JCR-Knoten und bis zu 83 GB (Online-komprimierte Größe) auf der *Autoreninstanz* und 50 GB auf der *Veröffentlichungsinstanz* unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Segmentspeichergröße oberhalb dieser Beschränkungen zu erörtern. |
| Gesamtgröße des Content-Repositorys <br>*(Segmentspeicher + Datenspeicher)* | Das Content Transfer Tool wurde entwickelt, um Inhalte für Dateidatenspeicher mit einer Kapazität von bis zu 20 TB zu übertragen. Mehr als 20 TB werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für Inhalte zu erörtern, deren Größe mehr als 20 TB beträgt. <br>Um die Inhaltsübertragung für große Repositorys erheblich zu beschleunigen, kann ein optionaler Schritt für eine [Vorabkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#setting-up-pre-copy-step) verwendet werden. Dies gilt für die Datenspeichertypen Dateidatenspeicher, Amazon S3 und Azure Data Store. Für Amazon S3 und Azure Data Store werden Repository-Größen von mehr als 20 TB unterstützt. |
| Gesamtgröße des Lucene-Index | Gesamtgröße des Lucene-Index von 25 GB, außer `/oak:index/lucene` und `/oak:index/damAssetLucene` wird derzeit unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Indexgröße oberhalb dieser Beschränkungen zu erörtern. |
| Knotennamenlänge | Die Länge eines Knotennamens muss 150 Byte oder weniger betragen, wenn der übergeordnete Pfad des Knotens >= (gleich oder größer) 350 Byte beträgt. Diese Knotennamen müssen auf &lt;= 150 Byte gekürzt werden, damit sie vom Knotenspeicher &quot;Dokument&quot;in AEM as a Cloud Service unterstützt werden. Die Aufnahme schlägt fehl, wenn diese langen Knotennamen nicht gekürzt werden. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool kann nicht verwendet werden, um Inhalte unter unveränderlichen Pfaden zu migrieren. Um Inhalte von `/etc` zu übertragen, dürfen nur bestimmte `/etc`-Pfade ausgewählt werden, jedoch nur, um [die Migration von AEM Forms zu AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=de#paths-of-various-aem-forms-specific-assets) zu unterstützen. Für alle anderen Anwendungsfälle finden Sie weitere Informationen unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=de#restructuring). |
| Knoteneigenschaftswert in MongoDB | Die in MongoDB gespeicherten Knoteneigenschaftswerte dürfen 16 MB nicht überschreiten. Dies wird von MongoDB durchgesetzt. Aufnahmen schlagen fehl, wenn die Datenmenge der Eigenschaftswerte größer als diese Grenze ist. Bevor Sie eine Extraktion durchführen, führen Sie dieses [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar)-Skript aus. Überprüfen Sie alle großen Eigenschaftswerte und überprüfen Sie, ob sie benötigt werden. Diejenigen, die 16 MB überschreiten, müssen in Binärwerte konvertiert werden. |

## Wie geht es weiter {#whats-next}

Nachdem Sie die Voraussetzungen gelesen und festgestellt haben, ob Sie das Content Transfer Tool in Ihrem Migrationsprojekt verwenden können, Informieren Sie sich über [Richtlinien und Best Practices bei der Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de).
