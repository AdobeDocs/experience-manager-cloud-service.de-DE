---
title: Voraussetzungen für die Verwendung des Content Transfer Tools   (Frühere Version)
description: Voraussetzungen für die Verwendung des Content Transfer Tools
hide: true
hidefromtoc: true
exl-id: 6b2878cb-6882-452b-8cab-e590316633f6
source-git-commit: eb633db8fe64a62661c094b88f0ce8d9950ed6d7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Voraussetzungen für die Verwendung des Content Transfer Tools   (Frühere Version) {#prerequisites}

In der folgenden Tabelle sind die Voraussetzungen für die Verwendung des Content Transfer Tool zusammengefasst.

Machen Sie sich mit den im Folgenden aufgeführten Aspekten vertraut:

| Zu beachten | Derzeit unterstützte Funktionen |
|--- |--- |
| AEM-Version | Das Content Transfer Tool kann nur unter AEM 6.3 oder höheren Versionen ausgeführt werden. |
| Größe des Segmentspeichers | Derzeit werden vorhandene Repositorys mit weniger als 55 Millionen JCR-Knoten und bis zu 83 GB (online-komprimierte Größe) auf der *Autoreninstanz* und 31 GB auf der *Veröffentlichungsinstanz* unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Segmentspeichergröße oberhalb dieser Beschränkungen zu erörtern. |
| Gesamtgröße des Content-Repositorys <br>*(Segmentspeicher + Datenspeicher)* | Das Content Transfer Tool wurde entwickelt, um Inhalte für Dateidatenspeicher mit einer Kapazität von bis zu 20 TB zu übertragen. Mehr als 20 TB werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für Inhalte zu erörtern, deren Größe mehr als 20 TB beträgt. <br>Um die Inhaltsübertragung für große Repositorys erheblich zu beschleunigen, kann ein optionaler Schritt für eine [Vorabkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#setting-up-pre-copy-step) verwendet werden. Dies gilt für die Datenspeichertypen Dateidatenspeicher, Amazon S3 und Azure Data Store. Für Amazon S3 und Azure Data Store werden Repository-Größen von mehr als 20 TB unterstützt. |
| Gesamtgröße des Lucene-Index | Derzeit wird eine Gesamtgröße des Lucene-Index von maximal 25 GB unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Indexgröße oberhalb dieser Beschränkungen zu erörtern. |
| Knotennamenlänge | Die Länge eines Knotennamens darf maximal 150 Byte betragen. Knotennamen, die länger als 150 Byte sind, müssen auf 150 Byte oder weniger gekürzt werden, damit sie vom Document-Knotenspeicher in Adobe Experience Manager as a Cloud Service unterstützt werden. Die Aufnahme schlägt fehl, wenn diese langen Knotennamen nicht gekürzt werden. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool kann nicht verwendet werden, um Inhalte unter unveränderlichen Pfaden zu migrieren. Um Inhalte von `/etc` zu übertragen, dürfen nur bestimmte `/etc`-Pfade ausgewählt werden, jedoch nur, um [die Migration von AEM Forms zu AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=de#paths-of-various-aem-forms-specific-assets) zu unterstützen. Für alle anderen Anwendungsfälle finden Sie weitere Informationen unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html). |
| Knoteneigenschaftswert in MongoDB | Die in MongoDB gespeicherten Knoteneigenschaftswerte dürfen 16 MB nicht überschreiten. Dies wird von MongoDB durchgesetzt. Aufnahmen schlagen fehl, wenn die Datenmenge der Eigenschaftswerte größer als diese Grenze ist. Bevor Sie eine Extraktion durchführen, führen Sie dieses [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar)-Skript aus. Überprüfen Sie alle großen Eigenschaftswerte und überprüfen Sie, ob sie benötigt werden. Diejenigen, die 16 MB überschreiten, müssen in Binärwerte konvertiert werden. |

## Wie geht es weiter {#whats-next}

Nachdem Sie die Voraussetzungen gelesen und festgestellt haben, ob Sie das Content Transfer Tool in Ihrem Migrationsprojekt verwenden können, Informieren Sie sich über [Richtlinien und Best Practices bei der Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de).
