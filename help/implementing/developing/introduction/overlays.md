---
title: Überlagerungen für Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service nutzt das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen zu erweitern und anzupassen.
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 32%

---

# Überlagerungen in AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service verwendet das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen (z. B. das Erstellen von Seiten) zu erweitern und anzupassen.

Der Begriff „Überlagerung“ kann in unterschiedlichen Zusammenhängen verwendet werden. In diesem Zusammenhang bedeutet eine Erweiterung AEM as a Cloud Service, dass eine Überlagerung die vordefinierten Funktionen nutzt und eigene Definitionen über sie durchsetzt, um die Standardfunktionalität anzupassen.

In einer Standardinstanz wird die vordefinierte Funktion unter `/libs` Es wird empfohlen, Ihre Überlagerung (Anpassungen) unter der `/apps` Verzweigung (mithilfe von [Suchpfad](#search-paths) um die Ressourcen aufzulösen).

* Die Touch-optimierte Benutzeroberfläche verwendet [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-zugehörige Überlagerungen:

   * Methode

      * Rekonstruieren Sie die entsprechende `/libs`-Struktur unter `/apps`.

        Diese Umstrukturierung erfordert keine 1:1-Kopie, da die [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) wird verwendet, um auf die erforderlichen Originaldefinitionen zu verweisen. Der Sling Resource Merger bietet Dienste für den Zugriff auf und die Zusammenführung von Ressourcen mit Vergleichsmechanismen (Differenzierungsmechanismen).

      * under `/apps`, nehmen Sie Änderungen vor.

   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Definieren Sie nur das Erforderliche neu.

>[!CAUTION]
>
>Der [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) verwendet werden. Diese Regel bedeutet, dass das Erstellen einer Überlagerung mit einer Skelettstruktur nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist.

Überlagerungen sind die empfohlene Methode für viele Änderungen. Sie können beispielsweise Ihre Konsolen konfigurieren oder eine Auswahlkategorie für den Asset-Browser im Seitenbereich erstellen (wird bei der Seitenbearbeitung verwendet). Sie sind aus folgenden Gründen erforderlich:

* **Im `/libs` Verzweigung, *nicht* Änderungen vornehmen**
Alle Änderungen, die Sie vornehmen, können verloren gehen, da diese Verzweigung bei jeder Anwendung von Upgrades auf Ihre Instanz geändert werden kann.

* Sie konzentrieren Ihre Änderungen an einem Ort, wodurch Sie Ihre Änderungen bei Bedarf leichter verfolgen, migrieren, sichern oder debuggen können.

## Suchpfade {#search-paths}

AEM verwendet den Suchpfad, um eine Ressource zu finden, wobei zuerst - standardmäßig - die `/apps` und dann `/libs` -Verzweigung. Dieser Mechanismus bedeutet, dass Ihre Überlagerung in `/apps` (und die dort definierten Anpassungen) hat Priorität.

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, abhängig von den in der OSGi-Konfiguration definierten Suchpfaden.
