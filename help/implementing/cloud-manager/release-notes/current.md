---
title: Versionshinweise für Cloud Manager 2023.4.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.4.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: be39b09b609cccff916db462af9a84149d23a698
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 50%

---


# Versionshinweise für Cloud Manager 2023.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.4.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2023.4.0 in AEM as a Cloud Service wurde am 13. April 2023 veröffentlicht. Die nächste Version soll am 11. Mai 2023 veröffentlicht werden.

## Neue Funktionen {#what-is-new}

* [Der AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) wurde auf Version 41 aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Wenn eine [certificate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) abläuft, [Domänennamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md) und [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) mit dem Zertifikat verknüpft ist, wird nicht mehr aus dem CDN entfernt.  In solchen Fällen ist die Site weiterhin erreichbar.
* Die Benutzeroberfläche von Cloud Manager bietet sichtbarere Warnhinweise, dass die [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) läuft bald ab.
* In seltenen Fällen konnten Kunden keine neue Umgebung erstellen oder eine Umgebung löschen.
