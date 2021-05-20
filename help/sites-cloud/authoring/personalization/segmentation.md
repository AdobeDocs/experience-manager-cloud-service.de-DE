---
title: Grundlegendes zur Segmentierung
description: Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung
exl-id: 36a9623a-bb19-498a-a0e9-ef80582b1fcf
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 96%

---

# Grundlegendes zur Segmentierung {#understanding-segmentation}

Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. In den meisten Fällen müssen vor dem Start einer Kampagne bereits Segmente definiert sein.

Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Das Verstehen dieser Ziele und das Erfüllen der Erwartungen sind wichtige Erfolgsfaktoren beim Onlinemarketing.

Dies können Sie mithilfe der Segmentierung erreichen, indem Sie die folgenden Faktoren eines Besuchers analysieren und charakterisieren:

* Aktivität auf der Website
* Profil
* Aktivität auf anderen Websites

Inhalte können dann entsprechend den zutreffenden Segmenten speziell auf die Anforderungen und Interessen des Besuchers abgestimmt werden.

## Verwenden von Segmentierung {#using-segmentation}

Segmente werden unter „Konfigurieren von Segmentierung“ definiert. Sie werden dazu verwendet, den tatsächlich für Zielgruppen sichtbaren Inhalt zu steuern.<!--Segments are defined in [Configuring Segmentation](/help/sites-administering/campaign-segmentation.md). They are used to steer the actual content seen by a specific target audience.-->

## Segmentierungsterminologie {#segmentation-terminology}

Im Rahmen der Segmentierung wird die folgende Terminologie verwendet:

* **Besucher**: Ein Besucher ist eine Person, die eine Website besucht. Der Besuch dieser Person beginnt in der Regel auf einer verweisenden Seite und geht dann über auf eine oder mehrere Seitenansichten auf Ihrer eigenen Website. Aus den Details des Besuchs dieser Person kann ein Verhaltensprofil erstellt werden.
* **Benutzer**: Ein Benutzer ist ein Besucher, der sich bei der Website registriert, um ein Kontoprofil zu erhalten. Um ein Profil zu erstellen, geben Benutzer weitere Informationen zu ihrer Person an, z. B. eine E-Mail-Adresse oder ihr Geschlecht. Es können auch weitere Informationen erfasst werden, beispielsweise Aktivität in der Community und Kaufmuster. Basierend auf den in dem Profil angegebenen Informationen kann ein demografisches Profil erstellt werden.
* **Eigenschaft**: Eine Eigenschaft ist ein Merkmal oder eine Charakteristik eines Besuchers, das bzw. die verwendet werden kann, um die Zugehörigkeit zu einem bestimmten Segment zu bestimmen.
* **Segment**: Ein Segment ist eine Sammlung von Besuchern, die bestimmte Eigenschaften teilen. Segmente sollten klar voneinander getrennt sein und so wenig Überlappung wie möglich mit anderen Segmenten aufweisen.
* **Verhaltenseigenschaften**: Bei Verhaltenseigenschaften handelt es sich um diejenigen Eigenschaften, die sich auf das Verhalten eines Besuchers auf einer Website beziehen. Dazu gehören:
   * Interessensgebiete auf Ihrer Website, einschließlich besuchter Seiten und gekaufter Produkte
   * Interessensgebiete auf der verweisenden Website, einschließlich verwendeter Suchbegriffe oder Anzeigen, auf die geklickt wurde
   * Interessensgebiete auf anderen Sites, die durch Tools wie Spyjax ermittelt werden
   * Loyalität der Besucher, Dauer des Besuchs, Häufigkeit der Besuche
* **Demografische Eigenschaften**: Dabei handelt es sich um ausgewählte Merkmale der Population, darunter:
   * Alter
   * Einkommen
   * Größe der Familie
   * Familienstand
   * Geschlecht
   * Standort
* **Abgeleitete Eigenschaften**  - Einige demografische Eigenschaften lassen sich ohne Registrierung nur schwer ermitteln, können aber durch Kombination von verhaltensbezogenen und demografischen Eigenschaften abgeleitet werden.
   * Beispielsweise können Besitzer von Sites durch Kombination der verweisenden URL (als Verhaltenseigenschaft) mit demografischen Informationen (ermittelt mithilfe von Tools wie [Google Ad Planner](https://www.google.com/adplanner/)) demografische Eigenschaften ihrer Besucher ableiten.
* **Untersegment**: Ein Segment kann in mehrere Untersegmente unterteilt werden. Dies geschieht über das Definieren weiterer Eigenschaften.
* **Teaser-Seite**: Eine Teaser-Seite richtet sich an eine bestimmte Zielgruppe. Sie enthält wiederverwendbare Inhalte, die in dem Teaser-Absatz verwendet werden können.
* **Kampagne**: Bei einer Kampagne handelt es sich um eine Sammlung von Teaser-Seiten und E-Mail-Marketing-Seiten, z. B. Newsletter oder Einladungen. Eine Kampagne läuft in der Regel für eine begrenzte Zeitdauer und wird dann von einer anderen Kampagne abgelöst.
* **Teaser-Absatz**: Dies ist ein Absatz, der Inhalte in Abhängigkeit von einer Auswahlstrategie von einer anderen Seite abruft. Bei dieser Auswahlstrategie können Segmente und Kampagnen berücksichtigt werden.
* **Liste**: Eine Liste wird aus einem Segment registrierter Benutzer extrahiert. Beispielsweise der Ort, der verwendet wird, um die Inhalte des Teaser-Absatzes zu steuern.
