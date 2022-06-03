---
title: Übersicht über das Content Transfer Tool
description: Übersicht über das Content Transfer Tool
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: 3bf12642e94076a67010e4701715a54138a490ee
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 72%

---

# Übersicht {#overview-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Übersicht"
>abstract="Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können. Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en" text="Richtlinien und Best Practices"

<!-- Alexandru: Old version of contextual help, keep for failover/debugging
>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Overview"
>abstract="Content Transfer Tool is a tool developed by Adobe that can be used to move existing content over from a source AEM instance (on-premise or AMS) to the target AEM Cloud Service instance. This tool also transfers principals (users or groups) automatically."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#extraction-process" text="Extraction Process"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#ingestion-process" text="Ingestion Process" -->

Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können.

Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch.

Es ist eine neue Version des Content Transfer Tool verfügbar, das den Inhaltstransferprozess mit Cloud Acceleration Manager integriert. Es wird dringend empfohlen, zu dieser neuen Version zu wechseln, um alle Vorteile nutzen zu können, die sie bietet:

* Self-Service-Methode zur einmaligen Extraktion eines Migrationssatzes und zur gleichzeitigen Aufnahme in mehrere Umgebungen
* Verbessertes Benutzererlebnis durch bessere Ladezustände, Limits und Fehlerbehandlung
* Aufnahmeprotokolle werden beibehalten und stehen immer zur Fehlerbehebung zur Verfügung

So verwenden Sie die neue Version (v2.0.10) <!-- update when version is available --> Sie müssen ältere Versionen des Content Transfer Tool deinstallieren, da es eine wesentliche Änderung in der Architektur des Tools gab.

>[!NOTE]
>
> In Situationen, in denen bereits eine Migration durchgeführt wird, können Sie die vorherige CTT-Version weiter verwenden, bis die Migration abgeschlossen ist. Die Dokumentation zur vorherigen CTT-Version finden Sie im Abschnitt [Legacy-Dokumentation](/help/journey-migration/content-transfer-tool/ctt-legacy/overview-content-transfer-tool-legacy.md).

## Phasen im Content Transfer Tool {#phases-content-transfer-tool}

Beim Inhaltstransfer gibt es zwei Phasen:

1. **Extraktion**: Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als *Migrationssatz* bezeichnet wird. Ein *Migrationssatz* ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern.

   Weitere Informationen finden Sie unter [Extraktionsvorgang beim Inhaltstransfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=de).

   >[!NOTE]
   > Es wird empfohlen, das User Mapping Tool als Teil der Extraktion auszuführen. Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=de).

1. **Aufnahme**: Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem *Migrationssatz* in die Cloud Service-Zielinstanz.

   Weitere Informationen finden Sie unter [Aufnahmevorgang beim Inhaltstransfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=de).

## Attribute eines Migrationssatzes {#attributes-migration-set}

Ein Migrationssatz hat die folgenden Attribute:

* Mit der neuen Version können Sie maximal fünf Migrationssätze in einem Projekt erstellen, das in Cloud Acceleration Manager erstellt wurde.
* Jeder Migrationssatz sollte einen eindeutigen Namen haben.

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

In der Extraktionsphase muss die Option ***Überschreiben*** deaktiviert werden, um einen vorhandenen Migrationssatz *aufzufüllen*. Weitere Informationen finden Sie unter [Auffüllextraktion](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=de#top-up-extraction-process).

In der Aufnahmephase muss die *Löschoption* deaktiviert werden, damit der Delta-Inhalt zusätzlich zum aktuellen Inhalt angewendet wird. Weitere Informationen finden Sie unter [Auffüllaufnahme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=de#top-up-ingestion-process).

## Wie geht es weiter {#whats-next}

Nun, da Sie sich mit dem Content Transfer Tool und seiner Übersicht, die dieses Tool beschreibt, vertraut gemacht haben, können Sie vorhandene Inhalte von einer Quell-AEM-Instanz (On-Premise oder AMS) in die AEM Cloud Service-Zielinstanz verschieben. Lesen Sie dazu [Voraussetzungen für das Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=de).
