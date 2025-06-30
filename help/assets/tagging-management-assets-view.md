---
title: Verwalten von Tags in der Assets-Ansicht
description: Erfahren Sie, wie Sie Tags in der Assets-Ansicht verwalten. Mit Tags können Sie Assets kategorisieren, damit sie sich leichter durchsuchen und suchen lassen.
exl-id: 7c5e1212-054f-46ca-9982-30e40b0482e1
feature: Smart Tags
role: User, Admin, Developer
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 100%

---

# Verwalten von Tags in der Asset-Ansicht {#view-assets-and-details}

>[!CONTEXTUALHELP]
>id="assets_taxonomy_management"
>title="Tags verwalten"
>abstract="Mit Tags können Sie Assets kategorisieren, damit sie sich leichter durchsuchen und suchen lassen. Admins können die hierarchische Tagging-Struktur verwenden, die die Anwendung relevanter Metadaten, die Kategorisierung von Assets, die Unterstützung der Suche, die Wiederverwendung von Tags, die Verbesserung der Auffindbarkeit usw. erleichtert."

Mit Tags können Sie Assets kategorisieren, damit sie sich leichter durchsuchen und suchen lassen. Tagging hilft bei der Verbreitung der entsprechenden Taxonomie an andere Benutzende und Workflows.

Flache Listen mit kontrolliertem Vokabular können im Laufe der Zeit unüberschaubar werden. Admins können die hierarchische Tagging-Struktur verwenden, die die Anwendung relevanter Metadaten, die Kategorisierung von Assets, die Unterstützung der Suche, die Wiederverwendung von Tags, die Verbesserung der Auffindbarkeit usw. erleichtert.

Sie können einen Namespace auf Stammebene sowie eine hierarchische Struktur untergeordneter Tags innerhalb des Namespace erstellen. Beispielsweise können Sie den Namespace `Activities` auf Stammebene mit den Tags `Cycling`, `Hiking` und `Running` innerhalb des Namespace erstellen. Weitere untergeordnete Tags wie `Clothing` und `Shoes` sind unter `Running` möglich.

![Tagging-Verwaltung](assets/tags-hierarchy.png)

Das Tagging bietet viele Vorteile, z. B.:

* Mit Tagging können Autorinnen und Autoren verschiedene Assets einfach über eine gemeinsame Taxonomie organisieren. Autorinnen und Autoren können Assets anhand gemeinsamer Tags schnell suchen und organisieren.

* Hierarchische Tags sind äußerst flexibel und eignen sich hervorragend, um Begriffe logisch zu organisieren. Mithilfe von Namespaces, Tags und untergeordneten Tags lassen sich ganze Taxonomiesysteme darstellen.

* Tags können sich im Laufe der Zeit weiterentwickeln, wenn sich das organisatorische Vokabular ändert.

* In der Admin-Ansicht verwaltete Tags bleiben mit den in der Assets-Ansicht verwalteten Tags synchronisiert. Dadurch werden Metadaten-Governance und -Integrität sichergestellt.

Um Tags auf Assets anwenden zu können, müssen Sie zunächst einen Namespace erstellen und anschließend Tags erstellen, die Sie zum Namespace hinzufügen. Sie können auch Tags erstellen und diese zu einem vorhandenen Namespace hinzufügen. Alle auf der Stammebene erstellten Tags werden automatisch zum Standard-Tags-Namespace hinzugefügt. Anschließend können Sie das Feld „Tags“ zum Metadatenformular hinzufügen, damit es auf der Seite mit den Asset-Details angezeigt wird. Nachdem Sie diese Einstellungen konfiguriert haben, können Sie damit beginnen, Tags auf Assets anzuwenden.

>[!NOTE]
>
>Sie müssen das Feld „Tags“ nur dann zum Metadatenformular hinzufügen, wenn Sie nicht das standardmäßige Metadatenformular verwenden.

![Tagging-Verwaltung](assets/tagging-taxonomy-management.png)

In der Admin-Ansicht stehen zusätzliche Funktionen zur Verfügung, die über die in diesem Artikel genannten hinausgehen. Dazu gehören das Zusammenführen, Umbenennen, Lokalisieren und Veröffentlichen von Tags.

## Erstellen eines Namespace {#create-a-namespace}

Ein Namespace ist ein Container für Tags, die nur auf Stammebene vorhanden sein können. Um mit der Einrichtung der hierarchischen Tag-Struktur zu beginnen, definieren Sie zunächst einen logischen Namen für den Namespace. Wenn Sie ein Tag zu keinem der vorhandenen Namespaces hinzufügen, wird das Tag automatisch in die Standard-Tags verschoben.

Führen Sie die folgenden Schritte aus, um einen Namespace zu erstellen:

1. Navigieren Sie unter `Settings` zu `Taxonomy Management`, um die Liste der vorhandenen Namespaces anzuzeigen. Sie können auch das Datum der letzten Änderung, die Person, die den Namespace oder die Tags darunter geändert hat, und die Häufigkeit der Verwendung des Tags in einem Asset anzeigen.
1. Klicken Sie auf `Create Namespace`.
1. Fügen Sie `Title`, `Name` und `Description` für den Namespace hinzu. Ihre Eingabe im Feld `Title` wird oben in der Hierarchie angezeigt. In der folgenden Abbildung bezieht sich **Aktivitäten** etwa auf den Namespace-Titel.

   ![Tagging-Verwaltung](assets/tags-hierarchy.png)

1. Klicken Sie auf `Save`.

## Hinzufügen von Tags zu einem Namespace {#add-tags-to-namespace}

Führen Sie die folgenden Schritte aus, um Tags zu einem Namespace hinzuzufügen:

1. Gehen Sie zum **[!UICONTROL Taxonomie-Management]**.
1. Wählen Sie den Namespace aus und klicken Sie auf `Create`, um das Tag auf der obersten Ebene unter dem Namespace zu erstellen. Wenn Sie ein untergeordnetes Tag unter einem Tag erstellen müssen, das in einem Namespace vorhanden ist, wählen Sie das Tag aus und klicken Sie dann auf `Create`.
   ![Hierarchie der Tags](assets/hierarchy-of-tags.png)

   In diesem Beispiel stellt das Bild auf der linken Seite das Tag dar, das im Feld `Path` direkt unter dem Namespace `automobile-four-wheeler` angezeigt wird. Das Bild rechts ist ein Beispiel für untergeordnete Tags, die innerhalb eines Tags hinzugefügt werden, da neben dem Namespace mehr Tag-Namen (nämlich `jeep` und `jeep-meridian`) im Feld `Path` angezeigt werden.
1. Geben Sie den Titel, den Namen und die Beschreibung für das Tag an und klicken Sie auf `Save`.


   >[!NOTE]
   >
   >* Die Felder `Title` und `Name` sind obligatorisch, das Feld `Description` hingegen optional.
   >* Standardmäßig kopiert das Tool den im Titelfeld eingegebenen Text, entfernt dabei Leerzeichen und Sonderzeichen (. &amp; / \ : * ? [ ] | &quot; %) und speichert ihn als Namen.
   >* Sie können das Feld `Title` später aktualisieren. Das Feld `Name` ist allerdings schreibgeschützt.

## Hinzufügen von Tags zu Standard-Tags {#add-tags-to-standard-tags}

Unstrukturierte Tags oder Tags, die keine Hierarchie aufweisen, werden unter dem Namespace `Standard Tags` gespeichert. Wenn Sie zusätzliche beschreibende Begriffe hinzufügen möchten, ohne dass sich dies auf die verwaltete Taxonomie auswirkt, können Sie diesen Wert außerdem unter `Standard Tags` speichern. Sie können diese Werte im Laufe der Zeit unter strukturierte Namespaces verschieben. Darüber hinaus können Sie den Namespace `Standard Tags` als freien Eintrag für Keywords verwenden.

Um ein Standard-Tag zu erstellen, klicken Sie auf der Stammebene auf `Create Tag`. Geben Sie Titel, Name und Beschreibung an und klicken Sie dann auf `Save`.

![Hinzufügen von Tags zu Standard-Tags](assets/adding-tags-to-standard-tags.png)

>[!NOTE]
>
>Wenn Sie den Namespace `Standard Tags` mithilfe des Assets as a Cloud Services löschen, werden die auf Stammebene erstellten Tags nicht in der Liste der verfügbaren Tags angezeigt.

## Verschieben von Tags {#move-tags}

Wenn Sie Ihre Tags unter der falschen Hierarchie gespeichert haben oder sich Ihre Taxonomie im Laufe der Zeit ändert, können Sie die ausgewählten Tags verschieben, um die Datenintegrität zu wahren. Beim Verschieben von Tags müssen die folgenden Bedingungen berücksichtigt werden:

* Tags können nur unterhalb vorhandener Namespaces oder innerhalb einer vorhandenen Tag-Hierarchie verschoben werden.
* Tags können nicht in den Stamm verschoben werden, um ein Namespace zu werden.
* Beim Verschieben eines übergeordneten Tags werden auch alle untergeordneten Tags verschoben, die in der Hierarchie gespeichert sind.

Führen Sie die folgenden Schritte aus, um Tags zu verschieben:

1. Wählen Sie das Tag oder die gesamte Tag-Hierarchie unter dem entsprechenden Namespace aus und klicken Sie auf `Move`.
1. Wählen Sie im Dialogfeld „Verschieben“ das neue Ziel-Tag oder den neuen Namespace mithilfe des Abschnitts `Select Tag` aus.
1. Klicken Sie auf `Save`. Das Tag wird an seiner neuen Position angezeigt.

## Bearbeiten von Tags {#edit-tags}

Um den Titel eines Tags zu bearbeiten, wählen Sie das Tag aus und klicken Sie auf `Edit`. Geben Sie den neuen Titel an und klicken Sie auf `Save`.

>[!NOTE]
>
>* Der `Name` eines Tags kann nicht aktualisiert werden. Der Stammpfad für ein Tag basiert ebenfalls auf dem Namen des Tags. Der Pfad bleibt auch dann unverändert, wenn Sie das Feld `Title` aktualisieren.
>* Im Assets as a Cloud Service sind zusätzliche Funktionen wie Zusammenführen, Lokalisieren und Veröffentlichen verfügbar.

## Löschen von Tags {#delete-tags}

Sie können mehrere Namespaces oder Tags gleichzeitig löschen. Der Löschvorgang kann nicht rückgängig gemacht werden.

Führen Sie die folgenden Schritte aus, um Tags zu löschen:

1. Wählen Sie den Namespace oder das Tag aus und klicken Sie auf `Delete`.
1. Klicken Sie auf `Confirm`.

>[!NOTE]
>
>* Mit dem übergeordneten Tag oder Namespace werden auch die in der Hierarchie gespeicherten untergeordneten Tags gelöscht. Wenn Sie den übergeordneten Namespace löschen oder aktualisieren müssen, wird empfohlen, [die Tags an das neue Ziel zu verschieben](#moving-tags), bevor die übergeordnete Hierarchie gelöscht wird.
>* Beim Löschen eines Tags werden auch alle Verweise aus Assets gelöscht.
>* Sie können die auf Stammebene vorhandenen Standard-Tags nicht löschen.

## Hinzufügen der Tag-Komponente zum Metadatenformular {#add-tags-to-metadata-form}

Die Tag-Komponente wird zum Metadatenformular `default` automatisch hinzugefügt. Sie können ein [Metadatenformular](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/metadata.html?lang=de#metadata-forms) entweder durch Verwendung einer Vorlage oder von Grund auf neu entwerfen. Wenn Sie keine vorhandene Metadatenformular-Vorlage verwenden, können Sie Ihr Metadatenformular ändern und die Tags-Komponente hinzufügen. Die Metadaten-Eigenschaftszuordnung wird automatisch ausgefüllt und kann zurzeit nicht geändert werden. [!DNL Assets as a Cloud Service]Benutzende können die Zuordnung so aktualisieren, dass Tag-Werte mithilfe benutzerdefinierter Namespaces gespeichert und nur Untergruppen von Hierarchien über Stammpfade angezeigt werden.

Sehen Sie sich dieses kurze Video an, um zu erfahren, wie Sie die Tags-Komponente zu Ihrem Metadatenformular hinzufügen:

>[!VIDEO](https://video.tv.adobe.com/v/3420452)


### Hinzufügen von Tags zu Assets {#add-tags-to-assets}

1. Gehen Sie zur Seite mit den Asset-Details und navigieren Sie zum Abschnitt `Tags` des Metadatenformulars.
1. Wählen Sie das Tag-Auswahlsymbol neben dem Feld „Tags“ aus oder geben Sie einen Tag-Namen ein, um sich die vorgeschlagenen Ergebnisse anzeigen zu lassen.

   ![Tagging von Assets](assets/adding-tags-to-assets.png)

1. Wählen Sie mindestens ein Tag aus. Das untergeordnete Tag wird automatisch zusammen mit dem übergeordneten Tag oder Namespace ausgewählt.
In den Assets Essentials geänderte Tags werden auch in Assets as a Cloud Service angewendet.

## Hinzufügen von Tags zur Blockierungsliste {#blocklist-essentials}

Mit [!DNL Assets view] können Sie jetzt eine Blockierungsliste mit Wörtern festlegen, die beim Hochladen in das Repository nicht als Smart-Tags zu Assets hinzugefügt werden sollen. Diese Funktion hilft Ihnen, die Markenkonformität zu wahren, und reduziert den Aufwand für die Moderation von Smart-Tags.
<!--
### Block smart tags for single asset {#block-smart-tags-for-single-asset}
![block smart tags](assets/block-smart-tags.png)
-->

### Blockieren von Smart-Tags für alle Assets {#block-smart-tags-for-all-assets}

[!DNL Assets view] ermöglicht es Admins, Smart-Tags für die vorhandenen und die neu hinzugefügten Assets zu blockieren. Führen Sie die folgenden Schritte aus, um Tags zu blockieren:

1. Navigieren Sie zu **[!UICONTROL Blockierte Tags]** unter **[!UICONTROL Einstellungen]**.
1. Klicken Sie auf **[!UICONTROL Blockiertes Tag hinzufügen]**.
1. Geben Sie die Tags in das Textfeld ein, die Sie blockieren möchten, und drücken Sie die **[!UICONTROL Eingabetaste]**.
1. Nachdem Sie die Tags hinzugefügt haben, klicken Sie auf **[!UICONTROL Hinzufügen]**. Die eingegebenen Tags werden in der Liste der blockierten Tags aufgeführt.

   >[!NOTE]
   >
   >Sie können der Liste maximal 25 Tags gleichzeitig hinzufügen. Wiederholen Sie die Schritte, um der Blockierungsliste weitere Tags hinzuzufügen.

Sie können Smart-Tags auch für ein einzelnes Asset blockieren. Navigieren Sie zu den Details eines Assets. Entfernen Sie unter der Registerkarte **[!UICONTROL Tags]** die unerwünschten Smart-Tags und klicken Sie auf **[!UICONTROL Speichern]**. Die Tags werden in der Blockierungsliste für das ausgewählte Asset aufgeführt.

### Auf der Blockierungsliste ausgeführte Aktionen {#blocklist-actions}

* **Entfernen von Tags:** Sie können die Tags auch aus der Blockierungsliste entfernen. Wählen Sie dazu ein oder mehrere Tags aus, die Sie entfernen möchten. Klicken Sie auf **[!UICONTROL Entfernen]**. Sie können maximal 25 Tags gleichzeitig aus der Liste entfernen.
* **Alle auswählen:** Aktivieren Sie das Kontrollkästchen neben dem **Tag-Namen**, um alle Tags in der Blockierungsliste auszuwählen.
* **Sortieren:** Sie können die Blockierungsliste in auf- oder absteigender Reihenfolge sortieren. Klicken Sie dazu auf den Pfeil neben dem **Tag-Namen**.

  ![Tags blockieren](assets/blocklist.gif)

  >[!NOTE]
  >
  >Verwenden Sie beim Hinzufügen eines Tags in der Blockierungsliste keine Sonderzeichen. Es können Zeichen wie a–z, A–Z, 0–9 und - verwendet werden.

### Exportieren der Blockierungsliste{#export-blocklist}

Mit der Assets-Ansicht können Sie die aufgelisteten blockierten Tags in das CSV-Format exportieren. Führen Sie die folgenden Schritte aus, um die Blockierungsliste zu exportieren:

1. Klicken Sie auf **[!UICONTROL Als CSV exportieren]**.
1. Wählen Sie den entsprechenden Speicherort für die CSV-Datei aus. Sie können die Datei auch gemäß den Anforderungen umbenennen.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Die exportierte Liste im CSV-Format wird am ausgewählten Speicherort heruntergeladen.

### Importieren der Blockierungsliste{#import-blocklist}

Die Assets-Ansicht bietet die Möglichkeit, blockierte Tags aus einer Datenquelle (CSV) zu importieren. Führen Sie die folgenden Schritte aus, um die Blockierungsliste zu importieren:

1. Klicken Sie auf **[!UICONTROL Als CSV importieren]**.
1. Wählen Sie die CSV-Datei von Ihrem Gerät aus. Klicken Sie auf **[!UICONTROL Datei auswählen]**, um über Ihr Gerät zur Datei zu navigieren. Alternativ können Sie die CSV-Datei per Drag-and-Drop von Ihrem Gerät ziehen.
1. Klicken Sie auf **[!UICONTROL Hochladen]**. Die Tags aus der CSV-Datei werden in der Liste der blockierten Tags aufgeführt.

   ![Importieren der Liste der blockierten Tags](assets/import-blocked-tags.png)

Falls Sie eine Vorlage für blockierte Tags herunterladen möchten, gehen Sie wie folgt vor:

1. Klicken Sie auf **[!UICONTROL Vorlage herunterladen]**.
1. Wählen Sie den entsprechenden Speicherort für die CSV-Datei aus. Sie können die Datei auch gemäß den Anforderungen umbenennen.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Vorlagen für blockierte Tags im CSV-Format werden am ausgewählten Speicherort heruntergeladen.
