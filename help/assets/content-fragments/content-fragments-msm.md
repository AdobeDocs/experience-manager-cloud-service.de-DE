---
title: Wiederverwenden von Inhaltsfragmenten mit MSM und Live Copies
description: Erfahren Sie, wie Sie mit der Live Copy-Funktion von MSM denselben oder ähnliche Inhaltsfragmentinhalte an mehreren Stellen verwenden können, während Sie mit dem Quellinhalt synchronisieren.
source-git-commit: 3ce1a982055c2f9c900edbd88e079deb6d3a036a
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 20%

---

# Wiederverwenden von Inhaltsfragmenten mit MSM {#reuse-content-fragments-using-msm}

Multi Site Manager (MSM) und die Live Copy-Funktion ermöglichen Ihnen die Verwendung desselben Inhalts an mehreren Stellen bei der Synchronisierung mit dem Quellinhalt.

* Mit MSM Live Copies können Sie:
   * Inhalte einmalig erstellen und diese
   * Verwenden Sie diesen Inhalt in anderen Bereichen derselben oder anderer Sites oder Anwendungen erneut.
* MSM behält dann die Live-Beziehungen zwischen Ihren Quellinhalten und deren Live Copies bei, sodass:
   * die Quelle und die Live Copies synchronisiert werden, wenn den Quellinhalt ändern.
   * Sie Anpassungen am Inhalt der Live Copies vornehmen können, indem Sie die Live-Beziehung zu einzelnen Unterseiten und/oder Komponenten trennen.

Eine ausführliche Übersicht über MSM-Konzepte finden Sie unter [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](/help/sites-cloud/administering/msm/overview.md).

>[!NOTE]
>
>[Multi-Site-Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) -Funktion in Adobe Experience Manager ermöglicht Benutzern die Wiederverwendung von einmalig erstellten Inhalten, die dann über mehrere Webspeicherorte hinweg wiederverwendet werden können.

Mit MSM für Inhaltsfragmente können Sie:

* Erstellen Sie Inhaltsfragmente einmal und erstellen Sie dann (verknüpfte) Kopien dieser Fragmente, um sie in anderen Bereichen der Site oder Anwendung wiederzuverwenden.
* Halten Sie mehrere Kopien synchronisiert, indem Sie die Quellkopie einmalig aktualisieren und dann die Änderungen an die (Live-)Kopien übertragen.
* Lokale Änderungen vornehmen, indem Sie die Verknüpfung zwischen übergeordneten und untergeordneten Fragmenten vorübergehend oder dauerhaft aussetzen, entweder vollständig oder für ihre Varianten oder Felder.

Mit MSM für Inhaltsfragmente in Verbindung mit Funktionen im Inhaltsfragment-Editor können Sie die Vererbung auf Feldebene unterbrechen und reaktivieren.

>[!CAUTION]
>
>MSM für Inhaltsfragmente ist nur verfügbar, wenn Inhaltsfragmente über die **Assets**-Konsole verwendet werden.
>
>Die MSM-Funktionalität ist *nicht* verfügbar, wenn die **Inhaltsfragmentkonsole** verwendet wird.

## Verfahren {#how-to}

Weitere Informationen zur Verwendung von MSM für Inhaltsfragmente (auch für Assets) finden Sie in der folgenden Dokumentation:

* Verwendung [MSM für Inhaltsfragmente (und Assets)](/help/assets/reuse-assets-using-msm.md)

* [Erstellen einer Live Copy](/help/assets/reuse-assets-using-msm.md)

  >[!CAUTION]
  >
  >Wenn Sie MSM verwenden möchten, um Kopien von Inhaltsfragmenten zu erstellen), können Sie **Eindeutig** -Einschränkungen sollten aus allen Datentypen entfernt werden, die in der entsprechenden [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md).

* [Eigenschaften und Status der Quelle und Live Copy anzeigen](/help/assets/reuse-assets-using-msm.md#properties)
* [Übertragen von Änderungen von der Quelle an die Live Copy](/help/assets/reuse-assets-using-msm.md#rollout-sync)
* Vererbung abbrechen und reaktivieren für:
   * Felder und Varianten der [Inhaltsfragmente-Editor](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
   * [Metadaten verwandter Assets](/help/assets/content-fragments/content-fragments-variations.md#canceling-reenabling-inheritance-individual-items)
* [Aussetzen und Fortsetzen der Beziehung](/help/assets/reuse-assets-using-msm.md#suspend-resume)
* [Entfernen der Live-Beziehung](/help/assets/reuse-assets-using-msm.md#detach)
* [MSM für Inhaltsfragmente (und Assets) mit MSM für Sites vergleichen](/help/assets/reuse-assets-using-msm.md#comparison)

## Einschränkungen {#limitations}

* Trigger, die sich auf Änderungen beziehen, und die zugehörige Rollout-Konfiguration sind für Inhaltsfragmente nicht vorhanden.