---
title: Voraussetzungen für das Content Transfer Tool
description: Voraussetzungen für das Content Transfer Tool
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: 40f27004e82266d363f034bb9d2858b8f3a4958d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 13%

---

# Voraussetzungen für das Content Transfer Tool {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
>abstract="Lesen Sie die wichtigen Überlegungen zur Verwendung des Content Transfer Tools, einschließlich Java- und AEM-Versionen, unterstützten Datenspeichertypen, Überlegungen zu Benutzergruppen und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#pre-reqs" text="Wichtige Überlegungen zur Verwendung des Content Transfer Tools"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en#best-practices" text="Best Practices und Richtlinien"

Die folgende Tabelle fasst die Voraussetzungen für die Verwendung des Content Transfer Tool zusammen.

Überprüfen Sie alle unten aufgeführten Aspekte:

| Aspekte | Derzeit unterstützte Funktionen |
|--- |--- |
| AEM-Version | Das Content Transfer Tool kann nur mit AEM 6.3 oder höheren Versionen ausgeführt werden. Um das Content Transfer Tool mit AEM 6.2 oder älteren Versionen verwenden zu können, ist eine ersetzende Aktualisierung des Inhalts-Repositorys auf AEM 6.5 erforderlich. Dazu ist es nicht erforderlich, den Code auf AEM 6.5 zu aktualisieren. |
| Größe des Segmentspeichers | Ein vorhandenes Repository mit weniger als 55 Millionen JCR-Knoten und bis zu 83 GB (Online-komprimierte Größe) unter *Autor* und 31 GB unter *Veröffentlichung* wird derzeit unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, um Optionen für die Segmentspeichergröße über diesen Beschränkungen zu besprechen. |
| Gesamtgröße des Inhalts-Repositorys <br>*(Segmentspeicher + Datenspeicher)* | Das Content Transfer Tool wurde entwickelt, um Inhalte für Datenspeicher vom Typ Dateidatenspeicher bis zu 10 TB zu übertragen. Mehr als 10 TB werden derzeit nicht unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, um Optionen für Inhalte zu besprechen, die größer als 10 TB sind. <br>Für Amazon S3- und Azure Data Store-Typen von Datenspeichern kann ein optionaler  [Pre-](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step) CopyStep verwendet werden, um den Inhaltstransfer erheblich zu beschleunigen und eine Datenspeichergröße von mehr als 10 TB zu unterstützen. |
| Indexgröße insgesamt | Die Indexgesamtgröße von maximal 25 GB wird derzeit unterstützt. Erstellen Sie ein Support-Ticket mit der Adobe-Kundenunterstützung, um Optionen für die Indexgröße über diesem Limit zu besprechen. |
| Knotennamenlänge | Die Länge eines Knotennamens muss 150 Byte oder weniger betragen. Knotennamen, die länger als 150 Byte sind, müssen auf &lt;= 150 Byte gekürzt werden, damit sie vom Knotenspeicher &quot;Dokument&quot;in AEM als Cloud Service unterstützt werden. Die Erfassung schlägt fehl, wenn diese langen Knotennamen nicht behoben sind. |
| Inhalt in unveränderlichen Pfaden | Das Content Transfer Tool kann nicht verwendet werden, um Inhalte in unveränderlichen Pfaden zu migrieren. Um Inhalte von `/etc` zu übertragen, dürfen nur bestimmte `/etc` Pfade ausgewählt werden, jedoch nur, um [AEM Forms als Cloud Service von AEM Forms zu unterstützen](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets). Weitere Informationen zur Repository-Umstrukturierung finden Sie unter [Allgemeine Repository-Neustrukturierung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) . |

## Wie geht es weiter {#whats-next}

Nachdem Sie die Voraussetzungen geprüft und festgestellt haben, ob Sie das Content Transfer Tool in Ihrem Migrationsprojekt verwenden können, lesen Sie [Weitere Best Practices und Überlegungen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md) bei der Verwendung des Content Transfer Tool.
