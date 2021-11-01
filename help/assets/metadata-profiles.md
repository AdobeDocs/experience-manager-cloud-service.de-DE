---
title: Metadatenprofile
description: Informieren Sie sich über Metadatenprofile für Assets. Erfahren Sie, wie Sie Metadatenprofile erstellen und auf Ordner-Assets anwenden können.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: eef90c6a-b354-4342-8b97-21d067ae2979
source-git-commit: cec07dad7a62439e26d9657459964b01ce6e3dba
workflow-type: tm+mt
source-wordcount: '1356'
ht-degree: 93%

---

# Metadatenprofile {#metadata-profiles}

Mit einem Metadatenprofil können Sie standardmäßige Metadaten auf Assets in einem Ordner anwenden. Erstellen Sie ein Metadatenprofil und wenden Sie es auf einen Ordner an. Jedes Asset, das Sie nachfolgend in den Ordner hochladen, übernimmt die standardmäßigen Metadaten, die Sie in „Metadatenprofil“ konfiguriert haben.

Ein wichtiges Konzept für die Verwendung von Profilen in Experience Manager Assets besteht darin, dass sie Ordnern zugewiesen werden. In einem Profil sind Einstellungen in Form von Metadatenprofilen zusammen mit Videoprofilen oder Bildprofilen enthalten. Mit diesen Einstellungen wird der Inhalt eines Ordners und seiner zugehörigen Unterordner verarbeitet. Wie Sie Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern verarbeiten, hat daher erhebliche Auswirkungen darauf, wie diese Assets von einem Profil verarbeitet werden.
Durch die Verwendung konsistenter und angemessener Strategien zur Datei- und Ordnernamen sowie einer guten Metadatenpraxis können Sie die digitale Asset-Sammlung optimal nutzen und sicherstellen, dass die richtigen Dateien vom richtigen Profil verarbeitet werden.

## Hinzufügen eines Metadatenprofils {#adding-a-metadata-profile}

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]** und klicken Sie dann auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel für das Metadatenprofil ein, etwa „Beispielmetadaten“, und tippen Sie auf **[!UICONTROL Senden]**. Es wird „Formular bearbeiten“ für das Metadatenprofil angezeigt.
1. Klicken Sie auf eine Komponente und konfigurieren Sie deren Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Klicken Sie beispielsweise auf die Komponente **[!UICONTROL Beschreibung]** und bearbeiten Sie die zugehörigen Eigenschaften.
Bearbeiten Sie die folgenden Eigenschaften für die Komponente **[!UICONTROL Beschreibung]**:

   * **[!UICONTROL Feldbezeichnung]**: Der Anzeigename der Metadateneigenschaft. Dieser dient lediglich als Referenz für den Benutzer.
   * **[!UICONTROL Zu Eigenschaft zuordnen]**: Der Wert dieser Eigenschaft liefert den relativen Pfad/Namen zum Asset-Knoten, unter dem er im Repository gespeichert ist. Der Wert sollte immer mit `./` beginnen, um anzugeben, dass der Pfad sich unter dem Knoten des Assets befindet.

      Der Wert, den Sie für **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, wird als Eigenschaft unter dem Metadatenknoten des Assets gespeichert. Beispiel: Wenn Sie `/jcr:content/metadata/dc:desc` als Namen von **[!UICONTROL Zu Eigenschaft zuordnen]** [!DNL Adobe Experience Manager Assets] angeben, wird der Wert `dc:desc` von im Metadatenknoten des Assets gespeichert.

   * **[!UICONTROL Standardwert]**: Mit dieser Eigenschaft können Sie einen Standardwert für die Metadatenkomponente hinzufügen. Wenn Sie beispielsweise „Meine Beschreibung“ angeben, wird dieser Wert der Eigenschaft `dc:desc` im Metadatenknoten des Assets zugewiesen.

      >[!NOTE]
      >
      >Wenn Sie einer neuen Metadateneigenschaft (die noch nicht im Knoten `/jcr:content/metadata` vorhanden ist) einen Standardwert hinzufügen, werden die Eigenschaft und deren Wert nicht standardmäßig auf der Eigenschaftsseite des Assets angezeigt. Um die neue [!UICONTROL Eigenschaft] auf der Eigenschaftsseite des Assets anzuzeigen, müssen Sie das entsprechende Schemaformular ändern.

1. (Optional) Fügen Sie dem Bearbeitungsformular auf der Registerkarte **[!UICONTROL Formular erstellen]** weitere Komponenten hinzu und konfigurieren Sie die zugehörigen Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Die folgenden Eigenschaften sind auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbar:

| Komponente | Eigenschaften |
|------------------|----------------------------------------------------|
| Bereichs-Kopfzeile | Feldbezeichnung, Beschreibung |
| Einzeilentext | Feldbezeichnung, Zu Eigenschaft zuordnen, Standardwert |
| Mehrwerttext | Feldbezeichnung, Zu Eigenschaft zuordnen, Standardwert |
| Zahl | Feldbezeichnung, Zu Eigenschaft zuordnen, Standardwert |
| Datum | Feldbezeichnung, Zu Eigenschaft zuordnen, Standardwert |
| Standard-Tags | Feldbezeichnung, Zu Eigenschaft zuordnen, Standardwert, Beschreibung |

1. Klicken Sie auf **[!UICONTROL Fertig]**. Das Metadatenprofil wird der Liste der Profile auf der Seite **[!UICONTROL Metadatenprofile]** hinzugefügt.

## Kopieren eines Metadatenprofils {#copying-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofil]** ein Metadatenprofil aus, um eine Kopie davon zu erstellen.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Metadatenprofil kopieren]** einen Titel für die neue Kopie des Metadatenprofils ein.
1. Klicken Sie auf **[!UICONTROL Kopieren]**. Die Kopie des Metadatenprofils wird in der Liste mit Profilen auf der Seite **[!UICONTROL Metadatenprofile]** angezeigt.

## Löschen eines Metadatenprofils {#deleting-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das zu löschende Profil aus.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Metadatenprofile löschen]**.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Löschen]**, um den Löschvorgang zu bestätigen. Das Metadatenprofil wird aus der Liste gelöscht.

## Anwenden eines Metadatenprofils auf Ordner {#applying-a-metadata-profile-to-folders}

Wenn Sie ein Metadatenprofil zu einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Die Vererbung wird beendet, wenn ein anderes Profil auf einen Unterordner angewendet wird. Sie können einem Ordner nur ein Videoprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Metadatenprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner nach der Änderung hinzugefügt werden. Sie können Metadatenprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie nachträglich geändert haben. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### Anwenden von Metadatenprofilen auf bestimmte Ordner {#applying-metadata-profiles-to-specific-folders}

Sie können ein Metadatenprofil über das Menü **[!UICONTROL Tools]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### Anwenden von Metadatenprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Navigieren Sie zu **[!UICONTROL Tools > Assets > Metadatenprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.
1. Klicken Sie auf **[!UICONTROL Metadatenprofil auf Ordner anwenden]** und wählen Sie mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Klicken Sie anschließend auf **[!UICONTROL Fertig]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Metadatenprofilen auf Ordner aus „Eigenschaften“ {#applying-metadata-profiles-to-folders-from-properties}

1. Klicken Sie auf der linken Leiste auf **[!UICONTROL Assets]** und navigieren Sie dann zu dem Ordner, auf den Sie ein Metadatenprofil anwenden möchten.
1. Tippen oder klicken Sie im Ordner auf das Häkchen, um den Ordner auszuwählen, und tippen oder klicken Sie auf **Eigenschaften**.
1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** aus. Wählen Sie anschließend das Profil aus dem Dropdown-Menü aus und klicken Sie auf **[!UICONTROL Speichern]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

### Globales Anwenden eines Metadatenprofils {#applying-a-metadata-profile-globally}

Profile können nicht nur auf einzelne Ordner, sondern auch global angewendet werden. Dann wird allen Inhalten, die Sie in [!DNL Experience Manager Assets] in beliebigen Ordnern hochladen, das ausgewählte Profil zugeordnet.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie nachträglich geändert haben. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**Um ein Metadatenprofil global anzuwenden, führen Sie einen der folgenden Schritte aus:**

* Navigieren Sie zu `https://[aem_server]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und wenden Sie das entsprechende Profil an und klicken Sie auf **[!UICONTROL Speichern]**.

* Navigieren Sie in CRXDE Lite zum folgenden Knoten: `/content/dam/jcr:content`. Fügen Sie die Eigenschaft `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` hinzu und klicken Sie auf **Alle speichern**.

## Entfernen eines Metadatenprofils aus Ordnern {#removing-a-metadata-profile-from-folders}

Wenn Sie ein Metadatenprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

Sie können ein Metadatenprofil aus einem Ordner im Menü **Tools** entfernen. Wenn Sie sich im Ordner befinden, ist dies über die **Eigenschaften** möglich. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten aus Ordnern entfernen.

### Entfernen von Metadatenprofilen aus Ordnern über die Benutzeroberfläche „Profile“ {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools > Assets > Metadatenprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Klicken Sie auf **[!UICONTROL Metadatenprofil aus Ordner(n) entfernen]** und wählen Sie einen oder mehrere Ordner aus, aus dem bzw. denen ein Profil entfernt werden soll, und klicken Sie dann auf **[!UICONTROL Fertig]**.

   Sie können bestätigen, dass das Metadatenprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Metadatenprofilen aus Ordnern über „Eigenschaften“ {#removing-metadata-profiles-from-folders-via-properties}

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, aus dem Sie ein Metadatenprofil entfernen möchten.
1. Klicken Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und klicken Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** aus. Wählen Sie anschließend **[!UICONTROL Keine]** aus dem Dropdown-Menü aus und klicken Sie auf **[!UICONTROL Speichern]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.
