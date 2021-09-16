---
title: Nur für Platzierung generieren für Adobe InDesign
description: Generieren Sie mithilfe des Experience Manager Assets-Workflows und von ImageMagick FPO-Ausgabedarstellungen neuer und vorhandener Assets.
contentOwner: Vishabh Gupta
role: Admin
feature: Renditions
source-git-commit: 7e82c3c5490c2f6d43167e6784cdbbb60f811a6f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 8%

---


# Nur für Platzierung generieren für Adobe InDesign {#fpo-renditions}

Beim Platzieren großer Assets aus Experience Manager in Adobe InDesign-Dokumenten muss ein Kreativprofi eine beträchtliche Zeit warten, nachdem er [ein Asset](https://helpx.adobe.com/de/indesign/using/placing-graphics.html) platziert hat. In der Zwischenzeit kann der Benutzer InDesign nicht verwenden. Dies unterbricht den kreativen Fluss und wirkt sich negativ auf das Kundenerlebnis aus. Adobe ermöglicht die zeitweilige Platzierung kleinformatiger Ausgabedarstellungen in InDesign-Dokumenten. Wenn die endgültige Ausgabe erforderlich ist, z. B. für Druck- und Veröffentlichungs-Workflows, ersetzen die Original-Assets mit voller Auflösung die temporäre Ausgabedarstellung im Hintergrund. Diese asynchrone Aktualisierung im Hintergrund beschleunigt den Designprozess, um die Produktivität zu steigern, und behindert nicht den kreativen Prozess.

Assets bietet Ausgabeformate, die nur für die Platzierung (FPO) verwendet werden. Diese FPO-Ausgabedarstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf. Wenn für ein Asset keine FPO-Ausgabedarstellung verfügbar ist, verwendet Adobe InDesign stattdessen das ursprüngliche Asset. Dieser Ausweichmechanismus stellt sicher, dass der kreative Workflow ohne Unterbrechung fortgesetzt wird.

Experience Manager as a Cloud Service bietet Cloud-native Asset-Verarbeitungsfunktionen zum Generieren der FPO-Ausgabedarstellungen. Verwenden Sie Asset-Microservices für die Generierung von Ausgabedarstellungen. Sie können die Ausgabegenerierung neu hochgeladener Assets und der in Experience Manager vorhandenen Assets konfigurieren.

Im Folgenden werden die Schritte zum Generieren von FPO-Ausgabedarstellungen beschrieben:

1. [Erstellen Sie ein Verarbeitungsprofil](#create-processing-profile).

1. Konfigurieren Sie Experience Manager für die Verwendung dieses Profils, um [neue Assets zu verarbeiten](#generate-renditions-of-new-assets).
1. Verwenden Sie die Profile, um [vorhandene Assets zu verarbeiten](#generate-renditions-of-existing-assets).

## Erstellen eines Verarbeitungsprofils {#create-processing-profile}

Um FPO-Ausgabedarstellungen zu generieren, erstellen Sie ein **[!UICONTROL Verarbeitungsprofil]**. Die Profile verwenden Cloud-native Asset-Microservices für die Verarbeitung. Anweisungen finden Sie unter [Erstellen von Verarbeitungsprofilen für Asset-Microservices](asset-microservices-configure-and-use.md).

Wählen Sie **[!UICONTROL FPO-Ausgabe erstellen]** aus, um die FPO-Ausgabe zu generieren. Klicken Sie optional auf **[!UICONTROL Neu hinzufügen]** , um demselben Profil weitere Ausgabeformateinstellungen hinzuzufügen.

![create-processing-profile-fpo-renditions](assets/create-processing-profile-fpo-renditions.png)

## Generieren von Ausgabeformaten neuer Assets {#generate-renditions-of-new-assets}

Um FPO-Ausgabedarstellungen neuer Assets zu generieren, wenden Sie das **[!UICONTROL Verarbeitungsprofil]** auf den Ordner in den Ordnereigenschaften an. Klicken Sie auf der Eigenschaftsseite eines Ordners auf die Registerkarte **[!UICONTROL Asset-Verarbeitung]**, wählen Sie das **[!UICONTROL FPO-Profil]** als **[!UICONTROL Verarbeitungsprofil]** aus und speichern Sie die Änderungen. Alle neuen Assets, die in den Ordner hochgeladen wurden, werden mit diesem Profil verarbeitet.

![add-fpo-rendition](assets/add-fpo-rendition.png)


## Generieren von Ausgabeformaten vorhandener Assets {#generate-renditions-of-existing-assets}

Um Ausgabedarstellungen zu generieren, wählen Sie die Assets aus und führen Sie die folgenden Schritte aus.

![fpo-existing-asset-reprocess](assets/fpo-existing-asset-reprocess.gif)


## Anzeigen von FPO-Ausgabeformaten {#view-fpo-renditions}

Sie können die generierten FPO-Ausgabedarstellungen überprüfen, nachdem der Workflow abgeschlossen ist. Klicken Sie in der Experience Manager Assets-Benutzeroberfläche auf das Asset, um eine große Vorschau zu öffnen. Öffnen Sie die linke Leiste und wählen Sie **[!UICONTROL Ausgabeformate]** aus. Alternativ können Sie den Tastaturbefehl `Alt + 3` verwenden, wenn die Vorschau geöffnet ist.

Klicken Sie auf **[!UICONTROL FPO rendition]** , um die Vorschau zu laden. Optional können Sie mit der rechten Maustaste auf die Ausgabedarstellung klicken und sie in Ihrem Dateisystem speichern. Suchen Sie in der linken Leiste nach verfügbaren Ausgabedarstellungen.

![rendition_list](assets/list-renditions.png)
