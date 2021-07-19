---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Erfahren Sie mehr über Asset-Metadaten in [!DNL Experience Manager Assets] und lernen Sie die verschiedenen Bearbeitungsmöglichkeiten kennen.
contentOwner: AG
feature: Metadaten
role: User,Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 90%

---

# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten {#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Asset, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder vorhandenen Feldern neue Metadateneigenschaften hinzufügen (etwa wenn ein Metadatenfeld leer ist).

Da Unternehmen gesteuertes und zuverlässiges Metadatenvokabular benötigen, lässt [!DNL Experience Manager Assets] das Adhoc-Hinzufügen von neuen Metadateneigenschaften nicht zu. Autoren können keine neuen Metadatenfelder für Assets hinzufügen, Entwickler hingegen schon. Informationen finden Sie unter [Erstellen neuer Metadateneigenschaften für Assets](meta-edit.md#editing-metadata-schema).

## Bearbeiten von Metadaten für ein Asset  {#editing-metadata-for-an-asset}

So bearbeiten Sie Metadaten:

1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Benutzeroberfläche von AEM Assets das Asset aus und klicken oder tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften anzeigen]**.
   * Wählen Sie die Schnellaktion **[!UICONTROL Eigenschaften anzeigen]** aus der Miniaturansicht des Assets aus.
   * Klicken oder tippen Sie auf der Asset-Seite auf das Symbol **[!UICONTROL Eigenschaften anzeigen]**.

   Auf der Asset-Seite werden alle Metadaten des Assets angezeigt. Diese Metadaten wurden automatisch beim Hochladen (Aufnahme) in Experience Manager Assets extrahiert.

1. Nehmen Sie auf den verschiedenen Registerkarten bei Bedarf Änderungen an den Metadaten vor. Klicken oder tippen Sie anschließend in der Symbolleiste auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Klicken oder tippen Sie auf **[!UICONTROL Schließen]**, um zur Benutzeroberfläche von AEM Assets zurückzukehren.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen.

Alle Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Dies erfolgt über den Experience Manager-Metadaten-Writeback-Workflow. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) werden überschrieben und neu erstellte Eigenschaften (einschließlich benutzerdefinierten Eigenschaften wie `cq:tags`) werden zusammen mit dem Schema hinzugefügt.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Bearbeiten von Metadatenschemata {#editing-metadata-schema}

Weitere Informationen zur Bearbeitung von Metadatenschemata finden Sie unter [Bearbeiten von Metadaten-Schemaformularen](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines benutzerdefinierten Namespace in Experience Manager {#registering-a-custom-namespace-within-aem}

Sie können innerhalb von Experience Manager eigene Namespaces hinzufügen. Es gibt vordefinierte Namespaces wie cq, jcr und sling. Sie können aber auch einen Namespace für Ihre Repository-Metadaten und die XML-Verarbeitung hinzufügen.

1. Wechseln Sie zur Seite für die Verwaltung des Knotentyps *https://&lt;Host>:&lt;Port>/crx/explorer/nodetypes/index.jsp*.
1. Klicken oder tippen Sie am oberen Rand der Seite auf **[!UICONTROL Namespaces]**. Die Seite zur Namespace-Verwaltung wird in einem Fenster angezeigt.

1. Um einen Namespace hinzuzufügen, klicken oder tippen Sie am unteren Rand auf **[!UICONTROL Neu]**.
1. Geben Sie einen benutzerdefinierten Namespace gemäß der XML-Namespace-Konvention ein (ID in Form einer URI und verknüpftes Präfix für die ID). Klicken oder tippen Sie auf **[!UICONTROL Speichern]**.
