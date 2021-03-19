---
title: Organisieren von digitalen Assets
description: Organisieren Sie Ihre digitalen Assets mithilfe der unterschiedlichen Methoden, die Adobe Experience Manager Assets bietet.
contentOwner: AG
feature: Asset-Verwaltung
topic: '"Administrator, Business Practitioner"'
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 98%

---


# Organisieren von digitalen Assets {#organize-digital-assets}

Alle digitalen Assets, Metadaten und Inhalte von Microsoft Office- und PDF-Dokumenten werden extrahiert und für die Suche aufbereitet. Die Suche ermöglicht weitreichende Filtermöglichkeiten für Assets und hält dabei vollständig die korrekten Berechtigungen ein. Metadaten werden in „Metadaten in Digital Asset Management“ ausführlich behandelt.

AEM Assets unterstützt verschiedene Methoden zum Organisieren von Inhalten. Sie können sie hierarchisch anhand von Ordnern organisieren oder in ungeordneter Ad-hoc-Manier ablegen, wobei zum Beispiel Tags verwendet werden können. Benutzer können Tags im DAM Asset Editor bearbeiten, in dem Teil-Assets, Ausgabeformate und Metadaten angezeigt werden.

## Erstellen von Ordnern {#create-folders}

Wenn Sie eine Sammlung von Assets organisieren, etwa alle *Naturaufnahmen*, können Sie Ordner erstellen, um diese zu gruppieren. Mit Ordnern können Sie Assets kategorisieren und organisieren. Bei AEM Assets müssen Sie Assets nicht in Ordner organisieren, um besser zu arbeiten.

>[!NOTE]
>
>Die Freigabe eines Assets-Ordners (in Marketing Cloud) vom Typ `sling:OrderedFolder` wird nicht unterstützt. Wenn Sie einen Ordner freigeben möchten, wählen Sie beim Erstellen eines Ordners nicht „Geordnet“ aus.

1. Navigieren Sie zu dem Ort in Ihrem Ordner „Digitale Assets“, an dem Sie einen neuen Ordner erstellen möchten.
1. Klicken Sie im Menü auf **[!UICONTROL Erstellen]**. Wählen Sie **[!UICONTROL Neuer Ordner]** aus.
1. Geben Sie in das Feld **[!UICONTROL Titel]** einen Ordnernamen an. DAM verwendet standardmäßig den Titel, den Sie als Ordnernamen angegeben haben. Wenn der Ordner erstellt wurde, können Sie die Standardeinstellung außer Kraft setzen und einen anderen Ordnernamen angeben.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ihr Ordner wird im Ordner „Digitale Assets“ angezeigt.

## Hinzufügen von CUG-Eigenschaften zu Ordnern {#add-cug-properties-to-folders}

Sie können einschränken, wer in Assets auf bestimmte Ordner zugreifen kann, indem Sie den Ordner einer CUG (Closed User Group, geschlossene Benutzergruppe) zuweisen. So weisen Sie einen Ordner einer CUG zu:

1. Klicken Sie in Assets mit der rechten Maustaste auf den Ordner, dem Sie CUG-Eigenschaften zuweisen möchten, und wählen Sie **Eigenschaften** aus.
1. Klicken Sie auf die Registerkarte **CUG**.
1. Aktivieren Sie das Kontrollkästchen **Aktiviert**, um den Ordner und die darin enthaltenen Assets nur einer geschlossenen Benutzergruppe zugänglich zu machen.
1. Rufen Sie die Anmeldeseite auf, sofern vorhanden, und fügen Sie diese Informationen hinzu. Fügen Sie zulässige Gruppen hinzu, indem Sie auf **Element hinzufügen** klicken. Fügen Sie, sofern nötig, den Bereich hinzu. Klicken Sie auf **OK**, um die Änderungen zu speichern.

## Verwenden von Tags zum Organisieren von Assets {#use-tags-to-organize-assets}

Sie können zum Organisieren von Assets Ordner und/oder Tags verwenden. Wenn Sie Assets Tags hinzufügen, können Sie diese bei einer Suche leichter finden. Gehen Sie wie folgt vor, um einem Asset Tags hinzuzufügen:

1. Öffnen Sie das Asset, indem Sie in Digital Asset Manager doppelt darauf klicken.
1. Öffnen Sie das Menü im Bereich **Tags**, um die verfügbaren Tags anzuzeigen. Wählen Sie die entsprechenden Tags aus. Löschen Sie ein Tag, indem Sie den Mauszeiger über dem Tag platzieren und auf `X` klicken.
1. Klicken Sie auf **Speichern**, um hinzugefügte Tags zu speichern.
