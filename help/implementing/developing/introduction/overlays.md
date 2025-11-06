---
title: Überlagerungen für Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service nutzt das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen zu erweitern und anzupassen.
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 93%

---

# Überlagerungen in AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service verwendet das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen (z. B. das Erstellen von Seiten) zu erweitern und anzupassen.

Der Begriff „Überlagerung“ kann in unterschiedlichen Zusammenhängen verwendet werden. In diesem Zusammenhang, der Erweiterung von AEM as a Cloud Service, bedeutet eine Überlagerung, dass Sie die vordefinierte Funktionalität nehmen und Ihre eigenen Definitionen darüber legen, um die Standardfunktionalität anzupassen.

In einer Standardinstanz wird die vordefinierte Funktionalität unter `/libs` gehalten und es wird empfohlen, Ihre Überlagerung (Anpassungen) unter der Verzweigung `/apps` zu definieren (mithilfe eines [Suchpfades](#search-paths), um die Ressourcen aufzulösen).

* Die Touch-fähige Benutzeroberfläche verwendet [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-bezogene Überlagerungen:

   * Methode

      * Rekonstruieren Sie die entsprechende `/libs`-Struktur unter `/apps`.

        Diese Neustrukturierung erfordert keine 1::1-Kopie, da der [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) verwendet wird, um die erforderlichen Originaldefinitionen zu vergleichen. Der Sling Resource Merger stellt Services für den Zugriff auf und die Zusammenführung von Ressourcen mittels Diff(Differenzierungs)-Mechanismen bereit.

      * Nehmen Sie unter `/apps` Änderungen vor.

   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Definieren Sie nur neu, was erforderlich ist.

>[!CAUTION]
>
>Der [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) verwendet werden. Diese Regel bedeutet, dass die Erstellung einer Überlagerung mit einer Skelettstruktur nur für die standardmäßige, Touch-fähige Benutzeroberfläche geeignet ist.

Überlagerungen sind die empfohlene Methode für viele Änderungen. Sie können beispielsweise Ihre Konsolen konfigurieren oder eine Auswahlkategorie für den Asset-Browser im Seitenbereich erstellen (wird bei der Seitenbearbeitung verwendet). Sie sind aus folgenden Gründen erforderlich:

* **Nehmen Sie *keine* Änderungen in der Verzweigung `/libs` vor**
Alle Änderungen, die Sie vornehmen, können verloren gehen, da diese Verzweigung für Änderungen anfällig ist, wenn Upgrades auf Ihre Instanz angewendet werden.

* Sie bündeln Ihre Änderungen an einem Speicherort und erleichtern Ihnen so das Nachverfolgen, Migrieren, Sichern oder Debuggen Ihrer Änderungen, falls erforderlich.

## Suchpfade {#search-paths}

AEM verwendet einen Suchpfad, um eine Ressource zu finden, wobei – standardmäßig – zuerst die Verzweigung `/apps` und dann die Verzweigung `/libs` durchsucht wird. Durch diesen Mechanismus hat Ihre Überlagerung in `/apps` (und die dort definierten Anpassungen) Priorität.

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, je nach den in der OSGi-Konfiguration definierten Suchpfaden.
