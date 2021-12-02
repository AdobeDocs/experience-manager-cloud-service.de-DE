---
title: Voraussetzungen für die Verwendung des Content Transfer Tools
description: Voraussetzungen für die Verwendung des Content Transfer Tools
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: 3b1ef6eef7249a33908102b287ee4b373d7e843b
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 64%

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
| Größe des Segmentspeichers | Derzeit werden vorhandene Repositorys mit weniger als 55 Millionen JCR-Knoten und bis zu 83 GB (Online-komprimierte Größe) auf der *Autoreninstanz* und 31 GB auf der *Veröffentlichungsinstanz* unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Segmentspeichergröße oberhalb dieser Beschränkungen zu erörtern. |
| Gesamtgröße des Content-Repositorys <br>*(Segmentspeicher + Datenspeicher)* | Das Content Transfer Tool wurde entwickelt, um Inhalte für Dateidatenspeicher mit einer Kapazität von bis zu 20 TB zu übertragen. Mehr als 20 TB werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, um Optionen für Inhalte zu besprechen, die größer als 20 TB sind. <br>Um den Inhaltstransfer für große Repositorys erheblich zu beschleunigen, ist ein optionales [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#setting-up-pre-copy-step) -Schritt verwendet werden. Dies gilt für die Datenspeichertypen File Data Store, Amazon S3 und Azure Data Store. Für Amazon S3 und Azure Data Store werden Repository-Größen von mehr als 20 TB unterstützt. |
| Lucene-Indexgröße insgesamt | Die Gesamtgröße des Lucene-Index von maximal 25 GB wird derzeit unterstützt. Erstellen Sie ein Support-Ticket bei der Kundenunterstützung von Adobe, um Optionen für die Indexgröße oberhalb dieser Beschränkungen zu erörtern. |
| Knotennamenlänge | Die Länge eines Knotennamens darf maximal 150 Byte betragen. Knotennamen, die länger als 150 Byte sind, müssen auf 150 Byte oder weniger gekürzt werden, damit sie vom Document-Knotenspeicher in Adobe Experience Manager as a Cloud Service unterstützt werden. Die Aufnahme schlägt fehl, wenn diese langen Knotennamen nicht gekürzt werden. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool kann nicht verwendet werden, um Inhalte unter unveränderlichen Pfaden zu migrieren. Um Inhalte von `/etc` zu übertragen, dürfen nur bestimmte `/etc`-Pfade ausgewählt werden, jedoch nur, um [die Migration von AEM Forms zu AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=de#paths-of-various-aem-forms-specific-assets) zu unterstützen. Für alle anderen Anwendungsfälle finden Sie weitere Informationen unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=de#restructuring). |
| Knoteneigenschaftswert in MongoDB | Die in MongoDB gespeicherten Knoteneigenschaftswerte dürfen 16 MB nicht überschreiten. Dies wird von MongoDB durchgesetzt. Die Erfassung schlägt fehl, wenn die Eigenschaftswerte größer als diese Grenze sind. Führen Sie vor dem Ausführen einer Extraktion Folgendes aus: [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) Skript. Überprüfen Sie alle großen Eigenschaftswerte und überprüfen Sie, ob sie benötigt werden. Diejenigen, die 16 MB überschreiten, müssen in Binärwerte konvertiert werden. |

## Wie geht es weiter {#whats-next}

Nachdem Sie die Voraussetzungen geprüft und festgestellt haben, ob Sie das Content Transfer Tool in Ihrem Migrationsprojekt verwenden können, lesen Sie [Richtlinien und Best Practices für die Verwendung des Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en).
