---
title: Wie wird Forms Designer heruntergeladen und installiert, um Vorlagen für Datensatzdokumente zu erstellen?
description: Verwenden Sie Forms Designer, um XDP- und PDF-Formularvorlagen zu erstellen, die als Vorlage für ein Datensatzdokument dienen.
keywords: Installieren von Designer, Installieren von Forms Designer, Anforderungen für die Installation von Forms Designer
exl-id: d6f1cb21-c48b-406d-8d47-482d7a1b4cc3
source-git-commit: defeee2fee42c6274c71438d6f9fde6e49a05081
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 61%

---

# Herunterladen und Installieren von Forms Designer {#installing-and-configuring-designer}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dieser Artikel |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/installing-configuring-designer.html) |

Designer ist ein benutzerfreundliches grafisches Programm für die Formulargestaltung, das die Erstellung von XDP- und PDF-Formularvorlagen vereinfacht. Sie können eine Formularvorlage entwerfen, deren Logik definieren und strikte gesetzliche Anforderungen einhalten. XDP- und PDF-Formulare dienen als Vorlage für Datensatzdokumente in einem adaptiven Formular. Diese Formularvorlagen unterscheiden sich von [Vorlagen für adaptive Formulare](template-editor.md).

## Voraussetzungen {#pre-requisites}

Um die neueste Version von AEM Forms Designer 64-Bit oder 32-Bit zu installieren, benötigen Sie die folgende Software und die erforderliche Mindesthardware für die Installation und Konfiguration von Designer:

+++ 64-Bit-Designer (empfohlen)

* [!DNL Microsoft® Windows® 2016 Server] oder [!DNL Microsoft® Windows® 2019 Server], und [!DNL Microsoft® Windows® 10]
* Mindestens 2 GB RAM
* 20 GB Festplattenspeicher
* Grafikspeicher - 128 MB GPU (256 MB wird empfohlen)
* 2,35 GB verfügbarer Festplattenspeicher
* Bildschirmauflösung 1024 x 768 Pixel oder höher
* Beschleuniger für Video-Hardware (optional)
* Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC.
* Administratorrechte für die Installation von Designer.
* [!DNL Microsoft® Visual C++ 2019] (VC 14.28 oder höher) 64-Bit-Laufzeit

+++

+++ 32-Bit-Designer

* [!DNL Microsoft® Windows® 2016 Server], [!DNL Microsoft® Windows® 2019 Server], oder [!DNL Microsoft® Windows® 10]
* 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
* 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
* Grafikspeicher – 128 MB GPU (256 MB empfohlen)
* 2,35 GB verfügbarer Festplattenspeicher
* Bildschirmauflösung 1024 x 768 Pixel oder höher
* Beschleuniger für Video-Hardware (optional)
* Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC.
* Administratorrechte für die Installation von Designer.
* Microsoft® Visual C++ 2019 (VC 14.28 oder höher) 32-Bit-Laufzeit

+++

## Installieren von Designer {#install-designer}

>[!NOTE]
>
> Deinstallieren Sie vor der Installation der 64-Bit-Version von Forms Designer die 32-Bit-Version von Designer.

So installieren Sie Designer:

1. Laden Sie Designer vom [Software-Verteilungsportal](https://experience.adobe.com/downloads) herunter.
1. Klicken Sie auf setup.exe, um das Installationsprogramm auszuführen.
1. Anschließend geben Sie Ihre Daten auf dem Bildschirm „Personalisierung“ ein.
1. Wenn Sie die Lizenzvereinbarung akzeptieren, klicken Sie auf **[!UICONTROL Weiter]**, um fortzufahren.
1. (Optional) Ändern Sie den Standardinstallationspfad, wenn Sie Designer an einem anderen Speicherort installieren möchten. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie auf **[!UICONTROL Zurück]**, um gegebenenfalls die Voreinstellungen zu ändern. Um Designer zu installieren, klicken Sie auf **[!UICONTROL Installieren]**.
1. Klicken Sie auf **[!UICONTROL Fertig stellen]**, wenn die Installation abgeschlossen ist.

## Siehe auch {#see-also}

* [Verwenden benutzerdefinierter Schriftarten](/help/forms/use-custom-fonts.md)
* [Erstellen eines eigenständigen, auf Kernkomponenten basierenden adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
