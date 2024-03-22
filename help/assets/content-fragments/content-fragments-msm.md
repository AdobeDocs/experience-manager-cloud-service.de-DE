---
title: Wiederverwenden von Inhaltsfragmenten mit MSM und Live Copies
description: Erfahren Sie, wie Sie mit der Live Copy-Funktion von MSM dieselben oder ähnliche Inhaltsfragmentinhalte an mehreren Stellen verwenden können, während sie mit dem Quellinhalt synchronisiert werden.
source-git-commit: 3ce1a982055c2f9c900edbd88e079deb6d3a036a
workflow-type: ht
source-wordcount: '432'
ht-degree: 100%

---

# Wiederverwenden von Inhaltsfragmenten mit MSM {#reuse-content-fragments-using-msm}

Mit Multi Site Manager (MSM) und dessen Live Copy-Funktionen können Sie dieselben Inhalte an mehreren Orten verwenden und gleichzeitig mit den Quellinhalten synchronisieren.

* Mit MSM Live Copies können Sie:
   * Inhalte einmalig erstellen und anschließend
   * diese Inhalte in anderen Bereichen derselben oder anderer Sites oder Anwendungen wiederverwenden.
* MSM behält dann die Live-Beziehungen zwischen Ihren Quellinhalten und deren Live Copies bei, sodass:
   * die Quelle und die Live Copies synchronisiert werden, wenn den Quellinhalt ändern.
   * Sie die Live-Beziehung zu einzelnen Unterseiten und/oder Komponenten trennen können, wenn Sie Anpassungen ausschließlich am Inhalt der Live Copies vornehmen wollen.

Einen ausführlichen Überblick über MSM-Konzepte finden Sie unter [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](/help/sites-cloud/administering/msm/overview.md).

>[!NOTE]
>
>[Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md): Die Funktion in Adobe Experience Manager ermöglicht es Benutzenden, einmal erstellte Inhalte über mehrere Web-Speicherorte hinweg wiederzuverwenden. 

Mit MSM für Inhaltsfragmente können Sie:

* Einmal Inhaltsfragmente anlegen und dann (verknüpfte) Kopien dieser Fragmente erstellen, um sie in anderen Bereichen der Site oder Anwendung wiederzuverwenden.
* Mehrere Kopien synchron halten, indem Sie die Quellkopie einmal aktualisieren und die Änderungen dann an die Kopien bzw. Live Copies übertragen.
* Lokale Änderungen vornehmen, indem Sie vorübergehend oder dauerhaft die Verknüpfung zwischen übergeordneten und untergeordneten Fragmenten vollständig oder für deren Varianten oder Felder unterbrechen.

Mit MSM für Inhaltsfragmente in Verbindung mit Funktionen im Inhaltsfragmenteditor können Sie die Vererbung auf Feldebene unterbrechen und reaktivieren.

>[!CAUTION]
>
>MSM für Inhaltsfragmente ist nur verfügbar, wenn Inhaltsfragmente über die **Assets**-Konsole verwendet werden.
>
>Die MSM-Funktionalität ist *nicht* verfügbar, wenn die **Inhaltsfragmentkonsole** verwendet wird.

## Anleitung {#how-to}

Weitere Informationen zur Verwendung von MSM für Inhaltsfragmente (auch für Assets) finden Sie in der folgenden Dokumentation:

* Verwenden von [MSM für Inhaltsfragmente (und Assets)](/help/assets/reuse-assets-using-msm.md)

* [Erstellen einer Live Copy](/help/assets/reuse-assets-using-msm.md)

  >[!CAUTION]
  >
  >Wenn Sie MSM verwenden möchten, um Kopien von Inhaltsfragmenten zu erstellen, dann sollten alle **Eindeutig**-Einschränkungen aus allen Datentypen entfernt werden, die in den jeweiligen [Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) verwendet werden.

* [Anzeigen von Eigenschaften und Status von Quelle und Live Copy](/help/assets/reuse-assets-using-msm.md#properties)
* [Übertragen von Änderungen von der Quelle an die Live Copy](/help/assets/reuse-assets-using-msm.md#rollout-sync)
* Abbrechen und Reaktivieren der Vererbung für:
   * Felder und Varianten des [Inhaltsfragmenteditors](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
   * [Metadaten zugehöriger Assets](/help/assets/content-fragments/content-fragments-variations.md#canceling-reenabling-inheritance-individual-items)
* [Aussetzen und Fortsetzen der Beziehung](/help/assets/reuse-assets-using-msm.md#suspend-resume)
* [Entfernen der Live-Beziehung](/help/assets/reuse-assets-using-msm.md#detach)
* [Vergleich von MSM für Inhaltsfragmente (und Assets) mit MSM für Sites](/help/assets/reuse-assets-using-msm.md#comparison)

## Einschränkungen {#limitations}

* Trigger, die sich auf Änderungen beziehen, und die zugehörige Rollout-Konfiguration sind für Inhaltsfragmente nicht vorhanden.