---
title: Interaktive Kommunikation importieren und exportieren
description: Der Import und Export von interaktiver Kommunikation ermöglicht es Benutzern, die Kommunikation über Umgebungen hinweg nahtlos zu migrieren, wiederzuverwenden und zu verwalten.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 15%

---


# Interaktive Kommunikation importieren und exportieren

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

Die Import- und Exportfunktion in Interactive Communication (IC) ermöglicht es Benutzern, die Kommunikation über Umgebungen hinweg nahtlos zu migrieren, wiederzuverwenden und zu verwalten. Dadurch können Sie eine interaktive Kommunikation (IC) zusammen mit den zugehörigen Fragmenten und Datenmodellen aus einer Umgebung exportieren und in eine andere importieren, was Konsistenz gewährleistet und den doppelten Aufwand bei der Bereitstellung reduziert.

## Wichtigste Vorteile

- Vereinfacht die Migration von ICs über Umgebungen hinweg.
- Behält Fragmente, Datenmodelle und Abhängigkeiten bei.
- Reduziert den Aufwand für die Neuerstellung von ICs über Projekte hinweg.

## Interaktive Kommunikation importieren und exportieren

Erstellen Sie eine interaktive Kommunikation (IC) in einer Umgebung und verwenden Sie sie in einer anderen, indem Sie sie exportieren und importieren, indem Sie die folgenden Schritte ausführen:

+++&#x200B;1. Exportieren der interaktiven Kommunikation

1.1. Wählen Sie eine [erstellte interaktive Kommunikation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/interactive-communication/create-interactive-communication) (IC) aus.
1.2. Klicken Sie auf die Option **Herunterladen**, um sie als ZIP-Datei zu exportieren.
1.3. Die heruntergeladene ZIP-Datei enthält die IC zusammen mit ihrer ausgewählten **Vorlage**, **Fragmenten** und **Datenmodell**.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/downloadic.png)
+++

+++&#x200B;2. Importieren von interaktiver Kommunikation

2.1. Zur Zielumgebung wechseln.
2.2. Navigieren Sie zu **Forms > Forms und Dokumente > Erstellen > Datei-Upload**.
2.3. Laden Sie die ZIP-Datei hoch, um **IC** importieren.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/uploadfile.png)

2.4. Nach dem Hochladen wird die IC zusammen mit den zugehörigen Fragmenten und dem Datenmodell angezeigt.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/importfragment.png)
+++

+++&#x200B;3. Fragment importieren und exportieren

3.1. Wählen Sie zum Exportieren das gewünschte Fragment aus **Forms > Forms und Dokumente** und klicken Sie dann auf **Herunterladen**, um es als ZIP-Datei zu exportieren.

3.2. Um zu importieren, gehen Sie zur Zielumgebung, navigieren Sie zu Forms > Forms und Dokumente > Erstellen **Datei hochladen** und laden Sie die exportierte ZIP-Datei hoch.

Dadurch wird die einfache Wiederverwendung von Fragmenten in verschiedenen Umgebungen ermöglicht, was die Konsistenz des Designs gewährleistet und Doppelarbeit reduziert.
+++
