---
title: Stapelsatzvorgaben
description: Erfahren Sie, wie Sie die Erstellung von Bildsets und Rotationssets mithilfe von Stapelsatzvorgaben in Dynamic Media automatisieren.
contentOwner: Rick Brough
feature: Image Presets,Viewer Presets
role: User
exl-id: 022ee347-54ec-4cec-b808-9eb3a9e51424
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '3434'
ht-degree: 98%

---

# Über Stapelsatzvorgaben {#about-bsp}

Verwenden Sie **[!UICONTROL Stapelsatzvorgaben]**, um die Erstellung und Organisation mehrerer Assets in einem Bildset oder Rotationsset zu erleichtern, wenn Sie Asset-Dateien einzeln oder mit der Massenaufnahme in einen Ordner hochladen. Sie können die Vorgaben zusammen mit den von Ihnen in [!DNL Dynamic Media] eingeplanten Asset-Importaufträgen ausführen lassen. Jede Vorgabe ist ein eindeutig benannter, in sich abgeschlossener Satz von Anweisungen, die definieren, wie das Bildset oder Rotationsset mithilfe von Bildern erstellt wird, die den definierten Benennungskonventionen im Vorgabenrezept entsprechen.

>[!IMPORTANT]
>
>Verwenden Sie Stapelsatzvorgaben in [!DNL Dynamic Media Classic] und migrieren Sie von [!DNL Dynamic Media Classic] zu Adobe Experience Manager as a Cloud Service? In diesem Fall müssen Sie die Definitionen der Stapelsatzvorgaben in [!DNL Adobe Experience Manager as a Cloud Service] manuell neu erstellen.

**Best Practice**: Beim Arbeiten mit Stapelsatzvorgaben empfiehlt Adobe den folgenden Workflow:

1. Erstellen Sie eine Stapelsatzvorgabe. Weitere Informationen finden Sie unter [Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset](#creating-bsp).
1. Erstellen Sie einen Asset-Ordner oder verwenden Sie einen vorhandenen Asset-Ordner und stellen Sie sicher, dass dieser mit [!DNL Dynamic Media] synchronisiert wird. Siehe [Erstellen von Ordnern](/help/assets/manage-digital-assets.md#creating-folders).
1. Wenden Sie die Stapelsatzvorgabe auf den Asset-Ordner an. Weitere Informationen finden Sie unter [Informationen zum Anwenden von Stapelsatzvorgaben auf Ordner](#apply-bsp).
1. Laden Sie Bilder in den Asset-Ordner hoch. Weitere Informationen finden Sie unter [Hochladen von Assets für Bildsets](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [Hochladen von Assets für Rotationssets](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets) oder [Hinzufügen digitalen Assets zu Adobe Experience Manager](/help/assets/add-assets.md#add-assets-to-experience-manager).
1. Das Bildset oder Rotationsset wird automatisch im gewünschten Ordner generiert.
1. Veröffentlichen Sie Ihr Bildset oder Rotationsset. Weitere Informationen finden Sie unter [Veröffentlichen von Dynamic Media-Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset {#creating-bsp}

Um Stapelsatzvorgaben zu erstellen, sollten Sie sich mit regulären Ausdrücken vertraut machen und diese verstehen.

Idealerweise hat Ihre Firma bereits eine Benennungskonvention für die Gruppierung von Assets in einem Satz festgelegt.
Um Ihnen die Bedeutung der Verwendung einer Namenskonvention zu verdeutlichen, nehmen wir an, dass die definierte Namenskonvention Ihres Unternehmens `<style>-<color>-<view>` lautet. Der Grundname für das Set muss immer `<style>-<color>` lauten und die Namenserweiterung des Sets muss `-SET` sein. Wenn Sie ein Bild mit dem Namen `0123-RED-01` hochladen, wird ein Set mit dem Namen `0123-RED-SET` erstellt. Wenn Sie später die Bilder `0123-RED-03` und `0123-BLUE-01` hochladen, wird das Bild `RED-03` dem Set an der zweiten Position hinzugefügt, da es niedriger als `01` sortiert ist. Das Bild `BLUE-01` wäre jedoch Teil eines neuen Sets mit dem Namen `0123-BLUE-SET`. Beim nächsten Hochladen von Assets fügen Sie die Dateien `0123-RED-02` und `0123-BLUE-02` hinzu. Jedes Asset wird seinem jeweiligen Set hinzugefügt. Das Bild `RED-02` wird aufgrund der Sortierreihenfolge automatisch zwischen den vorhandenen Bildern `01` und `03` sortiert.

Auf der Seite **[!UICONTROL Stapelsatzvorgabe]** in [!DNL Dynamic Media] können Sie Stapelsatzvorgaben erstellen, bearbeiten oder löschen und Stapelsatzvorgaben auf Asset-Ordner anwenden oder daraus entfernen. Sie können entweder die Dropdown-Listen für Formularfelder verwenden, um eine Stapelsatzvorgabe zu definieren, oder das Feld **[!UICONTROL Raw-Code]** verwenden, mit dem Sie die Syntax für reguläre Ausdrücke eingeben können.

Sie können so viele Stapelsatzvorgaben wie nötig erstellen, um alle erforderlichen Asset-Aufnahmeaufträge abzudecken.

### Über Asset-Benennungskonventionen

Der Bereich **[!UICONTROL Asset-Benennungskonvention]** auf der Seite **[!UICONTROL Stapelsatzvorgabe]** enthält zwei Elemente, mit denen Sie Ihre Stapelsatzvorgabe definieren können: **[!UICONTROL Übereinstimmung]** und **[!UICONTROL Grundname]**. Mit diesen Elementen können Sie eine Namenskonvention definieren und den Teil der Konvention identifizieren, der zum Benennen des Sets verwendet wird, das diese Elemente enthält. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

Die individuelle Namenskonvention eines Unternehmens verwendet häufig eine oder mehrere Zeilen der Definition aus jedem dieser beiden Elemente. Sie können für Ihre eindeutige Definition so viele Zeilen wie erforderlich verwenden und sie zu eindeutigen Elementen gruppieren, beispielsweise Elementen für Hauptbild, Farbe, alternative Ansicht und Muster.

Beispielsweise könnte die Syntax für einen regulären Ausdruck mit einer wörtlichen Übereinstimmung wie folgt aussehen:

`(\w+)-\w+-\w+`

### Über die Sequenzreihenfolge

Sie können optional die Reihenfolge festlegen, in der die Bilder angezeigt werden, nachdem das Bildset oder Rotationsset in [!DNL Dynamic Media] gruppiert wurde. Die Assets werden standardmäßig in alphanumerischer Reihenfolge angeordnet. Sie können jedoch eine kommagetrennte Liste mit regulären Ausdrücken verwenden, um die Reihenfolge zu definieren.

In Bezug auf die Automatisierung der Sequenzreihenfolge geben Sie Regeln an, um bei Bedarf eine bestimmte Sortierung von Assets zu erzwingen. Nehmen Sie zum Beispiel an, dass Ihr erstes Asset immer `_main` heißt und Sie möchten, dass darauf `_alt1`, `_alt2`, `_alt3` usw. folgen. In solchen Fällen können Sie eine Regel für die Sequenzreihenfolge mit der folgenden Syntax erstellen:

`.*_main,.*_alt[0-9]`

Obwohl eine Zwangssortierung möglich ist, ist es am besten, sich so weit wie möglich auf eine alphanumerische Nummerierung für die Sequenzreihenfolge zu verlassen. Darüber hinaus können Sie die Editor-Tools für Bildsets und Rotationssets in [!DNL Dynamic Media] verwenden, um die Sequenzreihenfolge der Assets einfach zu ändern, oder neue Assets im Set per Drag-and-Drop hinzufügen und löschen.

Nach dem Erstellen einer Stapelsatzvorgabe wenden Sie diese auf einen oder mehrere von Ihnen erstellte Ordner an. Weitere Informationen finden Sie unter [Informationen zum Anwenden von Stapelsatzvorgaben auf Ordner](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**So erstellen Sie eine Stapelsatzvorgabe für ein Bildset oder Rotationsset:**

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. Klicken Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** rechts oben auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe erstellen]** im Textfeld **[!UICONTROL Vorgabenname]** einen beschreibenden Namen ein. Der Vorgabenname kann nicht bearbeitet werden, wenn Sie ihn später ändern möchten.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Vorgabetyp]** die Option **[!UICONTROL Bildset]** oder **[!UICONTROL Rotationsset]** aus. Stellen Sie sicher, dass Sie den richtigen Vorgabetyp auswählen. Es kann später nicht bearbeitet werden.
1. Wählen Sie **[!UICONTROL Erstellen]**.
1. Legen Sie rechts auf der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** unter den Überschriften **[!UICONTROL Vorgabendetails]** und **[!UICONTROL Benennungskonvention festlegen]** die gewünschten bearbeitbaren Optionen fest.
Weitere Informationen zu den bearbeitbaren Optionen, die Ihnen zur Verfügung stehen, finden Sie unter [Optionen „Vorgabendetails“, „Benennungskonvention festlegen“ und „Regelresultate – RegX“](#features-options-bsp).

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. Erstellen Sie eine oder mehrere Gruppen mit regulären Ausdrücken.

   * Klicken Sie links auf der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** unter **[!UICONTROL Übereinstimmung]**, **[!UICONTROL Grundname]** oder **[!UICONTROL Sequenzreihenfolge]** auf **[!UICONTROL Gruppe hinzufügen]**.
   * Das Feld **[!UICONTROL Übereinstimmung]** ist erforderlich. **[!UICONTROL Grundname]** ist nur dann erforderlich, wenn im Feld **[!UICONTROL Übereinstimmung]** noch kein Grundname mithilfe einer Klammergruppierung angegeben ist. **[!UICONTROL Sequenzreihenfolge]** ist optional.
   * Geben Sie mithilfe der Dropdown-Listen und Textfelder im Gruppenformular eine Ausdrucksgruppe an, die Sie zur Definition der Benennungskriterien für die Assets des Bildsets oder des Rotationsets verwenden möchten.
      * Wenn Sie Ausdrücke für eine Gruppe auswählen und angeben, beachten Sie, dass die tatsächliche Syntax regulärer Ausdrücke unten rechts auf der Seite unter der Überschrift **[!UICONTROL Regelergebnisse – RegX]** angezeigt wird. Um die Zeichenfolge des regulären Ausdrucks unten rechts aktualisiert zu sehen, klicken Sie auf eine beliebige Stelle außerhalb des Formularbereichs. Diese Zeichenfolgen für reguläre Ausdrücke stellen das Muster dar, mit dem Sie bei der Suche nach [!DNL Dynamic Media]-Assets übereinstimmen möchten, um Ihr Bildset oder Rotationsset zu erstellen.
      * Wenn Sie eine Gruppe hinzugefügt haben und diese entfernen möchten, klicken Sie auf **[!UICONTROL X]**.
   * Wenn Sie zwei oder mehr Gruppen hinzufügen, wählen Sie in der Dropdown-Liste **[!UICONTROL Und]** die Option **[!UICONTROL Und]** aus, um eine neu hinzugefügte Gruppe mit einer zuvor hinzugefügten Ausdrucksgruppe zu verbinden. Oder wählen Sie **[!UICONTROL Oder]** aus, um die vorherige Ausdrucksgruppe und die neu erstellte Gruppe abwechselnd hinzuzufügen. Der Operand **[!UICONTROL Oder]** wird durch die Verwendung eines vertikalen Linienzeichens `|` in der Syntax des regulären Ausdrucks selbst definiert.

1. Führen Sie einen der folgenden Schritte aus:

   * Um eine weitere neue Gruppe hinzuzufügen, klicken Sie unter **[!UICONTROL Übereinstimmung]**, **[!UICONTROL Grundname]** oder **[!UICONTROL Sequenzreihenfolge]** auf **[!UICONTROL Gruppe hinzufügen]**. Erstellen Sie eine weitere Gruppe mit regulären Ausdrücken wie im vorherigen Schritt.
   * Überprüfen Sie die Syntax für reguläre Ausdrücke im Bereich **[!UICONTROL Regelresultate – RegX]**. Wenn Sie die Syntax ändern müssen, nehmen Sie Ihre Änderungen in der entsprechenden Gruppe links auf der Seite vor.
   * Wenn Sie mit dem Erstellen von Ausdrucksgruppen fertig sind, fahren Sie mit dem nächsten Schritt fort.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.

Jetzt können Sie die Stapelsatzvorgabe auf einen Asset-Ordner anwenden. Anschließend laden Sie Assets in diesen Ordner hoch. Dieser Workflow erzeugt automatisch ein Bildset oder Rotationsset. Siehe [Informationen zum Anwenden von Stapelsatzvorgaben auf Asset-Ordner](#apply-bsp).

### Optionen „Vorgabendetails“, „Benennungskonvention festlegen“ und „Regelresultate – RegX“ {#features-options-bsp}

Diese Optionen stehen auf der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** zur Verfügung, wenn Sie eine Stapelsatzvorgabe erstellen oder bearbeiten.

Weitere Informationen finden Sie unter [Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset](#creating-bsp) oder unter [Bearbeiten einer Stapelsatzvorgabe](#edit-bsp).

| **[!UICONTROL Vorgabendetails]** | Beschreibung |
| --- | --- |
| Vorgabenname | Schreibgeschützt. Der Name, den Sie beim ersten Erstellen des Stapelsatzes angegeben haben. Wenn Sie die Vorgabe erneut benennen müssen, können Sie die vorhandene Stapelsatzvorgabe kopieren und einen neuen Namen angeben. Weitere Informationen finden Sie unter [Kopieren einer vorhandenen Stapelsatzvorgabe](#copy-bsp). |
| Typ | Schreibgeschützt. Der Typ wurde beim ersten Erstellen des Stapelsatzes angegeben. Durch Kopieren einer bestehenden Stapelsatzvorgabe können Sie deren [!UICONTROL Typ] nicht ändern. Sie müssen stattdessen eine Vorgabe erstellen. |
| Abgeleitete Assets einschließen | Optional. Wenn das IPS von [!DNL Dynamic Media] generierte oder „abgeleitete“ Bilder mit dem Rotationsset oder Bildset enthalten soll, wählen Sie **[!UICONTROL Ja]** (Standard) aus. Ein abgeleitetes Asset ist ein Bild, das nicht direkt von einem Benutzer hochgeladen wurde. Stattdessen wurde das Asset vom IPS erzeugt, wenn ein primäres Asset hochgeladen wurde. Zum Beispiel wird ein Bild-Asset, das IPS aus einer Seite in einer PDF-Datei generiert hat, als die PDF-Datei in [!DNL Dynamic Media] hochgeladen wurde, als abgeleitetes Asset betrachtet. |
| Zielordner | Optional. Falls Sie eine große Anzahl von Bildsets oder Rotationssets definieren, empfiehlt Adobe, diese Sets von den Ordnern, die die Assets selbst enthalten, getrennt zu halten. Daher sollten Sie die Erstellung eines Ordners für Bildsets oder Rotationssets erwägen und das Programm so umstellen, dass es im Stapelsatz generierte Sets hier ablegt.<br>Geben Sie in diesem Fall an, für welchen Ordner in der Experience Manager Assets-Ordnerstruktur (`/content/dam`) die Stapelsatzvorgabe aktiv sein soll. Stellen Sie sicher, dass der Ordner für die [!DNL Dynamic Media]-Synchronisierung aktiviert ist, damit er als Zielordner zulässig ist. Weitere Informationen finden Sie unter [Konfigurieren von selektiver Veröffentlichung auf der Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder).<br>Eine bestimmte Stapelsatzvorgabe kann mehr als einem Ordner zugewiesen werden, wenn Sie die Vorgabe für die (Eigenschaften **[!UICONTROL des Ordners]**. Weitere Informationen finden Sie unter [Anwenden von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Asset-Ordners](#apply-bsp-to-folders-via-properties).<br>Wenn Sie keinen Ordner angeben, wird das von der Stapelsatzvorgabe erstellte Bildset oder Rotationsset im selben Ordner erstellt wie der Asset-Ordner, in den Sie hochgeladen haben. |
| **[!UICONTROL Benennungskonvention festlegen]** |  |
| Präfix<br>oder<br>Suffix | Optional. Geben Sie entweder ein Präfix, ein Suffix oder beide in die entsprechenden Felder ein.<br>Mit den Präfix- und Suffix-Feldern können Sie beliebig viele Stapelsatzvorgaben mit einer alternativen, benutzerdefinierten Dateinamenkonvention für einen bestimmten Satz von Inhalten erstellen. Diese Methode ist besonders in Fällen nützlich, in denen es eine Ausnahme vom definierten Standardbenennungsschema eines Unternehmens gibt.<br>Das Präfix oder Suffix wird dem **[!UICONTROL Grundnamen]** hinzugefügt, den Sie im Bereich **[!UICONTROL Asset-Benennungskonvention]** festlegen. Durch das Hinzufügen eines Präfixes oder Suffixes stellen Sie sicher, dass Ihr Bildset oder Rotationsset exklusiv und unabhängig von anderen Assets erstellt wird. Dies kann auch dazu dienen, anderen bei der Identifizierung von Dateitypen zu helfen. Um beispielsweise einen verwendeten Farbmodus zu bestimmen, können Sie `rgb` oder `cmyk` als Präfix oder Suffix hinzufügen.<br>Obwohl die Angabe einer Benennungskonvention nicht erforderlich ist, um die Funktionalität der Stapelsatzvorgaben zu verwenden, wird als Best Practice empfohlen, die festgelegte Benennungskonvention zu verwenden. Auf diese Weise können Sie beliebig viele Elemente Ihrer Benennungskonvention festlegen, die in einem Satz gruppiert werden sollen, um die Erstellung von Stapelsätzen zu optimieren. |
| **[!UICONTROL Regelresultate – RegX]** |  |
| Asset-Benennungskonvention – Übereinstimmung | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den von Ihnen gewählten Formularoptionen „Übereinstimmung“ oder dem eingegebenen Raw-Code an. |
| Asset-Benennungskonvention – Grundname | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den von Ihnen gewählten Formularoptionen „Grundname“ oder dem eingegebenen Raw-Code an. |
| Sequenzreihenfolge – Übereinstimmung | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den von Ihnen gewählten Optionen des Formulars oder dem eingegebenen Raw-Code an. |

## Informationen zum Anwenden von Stapelsatzvorgaben auf Asset-Ordner {#apply-bsp}

Wenn Sie einem oder mehreren Asset-Ordnern Stapelsatzvorgaben zuweisen, übernehmen alle Unterordner automatisch die Vorgaben aus ihrem übergeordneten Ordner.

Sie können mehrere Stapelsatzvorgaben auf einen Asset-Ordner anwenden.

Ordner, denen eine Stapelsatzvorgabe zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen der Vorgabe angezeigt, die im Ordner in der **[!UICONTROL Kartenansicht]** angezeigt wird.

Um Stapelsatzvorgaben auf Asset-Ordner anzuwenden, verwenden Sie eine der beiden folgenden Methoden:

* [Anwenden der Stapelsatzvorgaben auf Asset-Ordner auf der Seite „Stapelsatzvorgabe“](#apply-bsp-to-folders-via-bsp-page) – Diese Methode bietet Ihnen die größte Flexibilität. Sie können eine oder mehrere Vorgaben auf einen oder mehrere Ordner anwenden.
* [Anwenden von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Asset-Ordners](#apply-bsp-to-folders-via-properties) – Mit dieser Methode können Sie eine oder mehrere Stapelsatzvorgaben auf einen Ordner anwenden.

Stellen Sie am besten sicher, dass die Asset-Ordner mit [!DNL Dynamic Media] synchronisiert sind, und wenden Sie dann die gewünschten Vorgaben an.

Verarbeiten Sie Assets in einem Ordner neu, wenn eines der folgenden beiden Szenarien eintritt:

* Sie möchten eine Stapelsatzvorgabe für einen vorhandenen Asset-Ordner ausführen, in den bereits Assets hochgeladen wurden.
* Sie bearbeiten später eine vorhandene Stapelsatzvorgabe, die zuvor auf einen Asset-Ordner angewendet wurde.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Anwenden von Stapelsatzvorgaben auf Asset-Ordner auf der Seite „Stapelsatzvorgabe“ {#apply-bsp-to-folders-via-bsp-page}

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen jeder Stapelsatzvorgabe, die Sie auf Ordner anwenden möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Stapelvorgabe auf Ordner anwenden]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Ordner auswählen]** das Kontrollkästchen jedes Ordners, auf den die Stapelsatzvorgaben angewendet werden sollen.
1. Klicken Sie oben rechts auf der Seite **[!UICONTROL Ordner auswählen]** auf **[!UICONTROL Anwenden]**.

### Anwenden von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Asset-Ordners {#apply-bsp-to-folders-via-properties}

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Gehen Sie zu einem Ordner, auf den Sie eine oder mehrere Stapelsatzvorgaben anwenden möchten.
1. Aktivieren Sie auf der Seite links neben der Spalte **[!UICONTROL Name]** das Kontrollkästchen eines Ordners.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Klicken Sie auf der Seite „Eigenschaften“ des Ordners auf die Registerkarte **[!UICONTROL Dynamic Media-Verarbeitung]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Wählen Sie unter **[!UICONTROL Vorgaben für Stapelsätze]** aus der Dropdown-Liste **[!UICONTROL Vorgabenname]** den Namen einer Stapelsatzvorgabe aus, die Sie anwenden möchten. Der Screenshot oben zeigt zwei ausgewählte Stapelsatzvorgaben, die auf den Asset-Ordner angewendet wurden.

   Wenn im Dropdown-Listenfeld **[!UICONTROL Vorgabename]** keine Stapelsatzvorgaben vorhanden sind, bedeutet dies, dass Sie noch keine Stapelsatzvorgaben erstellt haben. Weitere Informationen finden Sie unter [Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset](#creating-bsp).

   Um eine angewendete Stapelsatzvorgabe zu entfernen, klicken Sie auf **[!UICONTROL X]** rechts neben dem Vorgabetyp.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern und schließen]**.

## Bearbeiten einer Stapelsatzvorgabe {#edit-bsp}

Sie können eine von Ihnen bereits erstellte Stapelsatzvorgabe bearbeiten. Sie können jede der Ausdrucksgruppen ändern, die Sie für die Asset-Benennungskonvention oder die Asset-Reihenfolge erstellt haben. Bei Bedarf können Sie auch den Zielordner aktualisieren und Benennungskonventionen festlegen.

Der Name und der Vorgabetyp der Vorgabe (Bildset oder Rotationsset) können jedoch nicht geändert werden. Wenn der Name einer Vorgabe geändert werden muss, können Sie die vorhandene Vorgabe kopieren und einen neuen Namen angeben. Weitere Informationen finden Sie unter [Kopieren einer Stapelsatzvorgabe](#copy-bsp).

Wenn Sie eine Stapelsatzvorgabe bearbeiten, die zuvor auf einen Ordner angewendet wurde, wird die neu bearbeitete Vorgabe nur auf neue Assets angewendet, die in den Ordner hochgeladen werden.

Wenn die neu bearbeitete Vorgabe erneut auf die vorhandenen Assets im Ordner angewendet werden soll, müssen Sie den Ordner erneut verarbeiten. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->Auf diese Weise können die vorhandenen Assets nun als Teil eines Bildsets oder Rotationssets betrachtet und hinzugefügt werden. Darüber hinaus werden die vorhandenen Assets, die bereits im Bildset oder Rotationsset enthalten waren – basierend auf der zuvor verwendeten Stapelsatzvorgabe – nicht entfernt und unverändert angezeigt. In diesem Szenario wird davon ausgegangen, dass sie sich nicht mehr auf der Grundlage der neu bearbeiteten Vorgabe qualifizieren.

**So bearbeiten Sie eine Stapelsatzvorgabe:**

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** die Stapelsatzvorgabe, die Sie ändern möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Stapelsatzvorgabe bearbeiten]**.
1. Bearbeiten Sie die Vorgabe nach Bedarf.
1. Klicken Sie oben rechts auf der Seite **[!UICONTROL Stapelsatzvorgabe]** auf **[!UICONTROL Speichern]**.

## Kopieren einer vorhandenen Stapelsatzvorgabe {#copy-bsp}

Sie können eine vorhandene Stapelsatzvorgabe kopieren, um zu vermeiden, dass eine komplexe Vorgabe manuell neu erstellt werden muss, oder um eine Vorgabe einfach umzubenennen. Der verwendete Vorgabetyp (Bildset oder Rotationsset) kann jedoch nicht geändert werden.

Wenn Sie eine vorhandene Vorgabe kopieren, die von Asset-Ordnern referenziert wird, sind diese Ordner nicht betroffen.

**So kopieren Sie eine vorhandene Stapelsatzvorgabe:**

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen der Stapelsatzvorgabe, die Sie kopieren möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe kopieren]** im Textfeld **[!UICONTROL Titel]** einen neuen Namen für die Vorgabe ein.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. Klicken Sie auf **[!UICONTROL Kopieren]**.

## Informationen zum Entfernen von Stapelsatzvorgaben aus Ordnern {#remove-bsp-from-folder}

Wenn Sie Stapelsatzvorgaben aus Ordnern entfernen, wird für neue Assets, die Sie in diese Ordner hochladen, die Stapelsatzvorgabe nicht angewendet. Vorhandene Assets im Ordner, die bereits zum Bildset oder Rotationsset hinzugefügt wurden, basierend auf der auf den Ordner angewendeten Stapelsatzvorgabe, werden weiterhin unverändert angezeigt.

Wenn Sie stattdessen die Vorgaben aus den Ordnern *löschen* möchten, finden Sie weitere Informationen unter [Löschen von Stapelsatzvorgaben](#delete-bsp).

Es gibt zwei Methoden, mit denen Sie Stapelsatzvorgaben aus Ordnern entfernen können.

* [Entfernen von Stapelsatzvorgaben aus Ordnern auf der Seite „Stapelsatzvorgabe“](#remove-bsp-from-folders-via-bsp-page) – Diese Methode bietet Ihnen die größte Flexibilität. Sie können eine oder mehrere Vorgaben aus einem oder mehreren Ordnern entfernen.
* [Entfernen von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Ordners](#remove-bsp-from-folders-via-properties) – Mit dieser Methode können Sie eine oder mehrere Stapelsatzvorgaben entfernen, allerdings nur aus einem einzelnen Ordner.

### Entfernen von Stapelsatzvorgaben aus Ordnern über die Seite „Stapelsatzvorgaben“ {#remove-bsp-from-folders-via-bsp-page}

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen für eine oder mehrere Stapelsatzvorgaben, die Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Stapelvorgabe aus Ordnern entfernen]**.

1. Wählen Sie auf der Seite **[!UICONTROL Ordner auswählen]** einen oder mehrere Ordner aus, aus denen die Stapelsatzvorgaben entfernt werden sollen.
1. Klicken Sie oben rechts auf der Seite **[!UICONTROL Ordner auswählen]** auf **[!UICONTROL Entfernen]**.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. Klicken Sie im Dialogfeld **[!UICONTROL Profil entfernen]** auf **[!UICONTROL Entfernen]**.

### Entfernen von Stapelsatzvorgaben von der Seite „Eigenschaften“ eines Ordners {#remove-bsp-from-folders-via-properties}

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Navigieren Sie zu einem Ordner, aus dem Sie eine oder mehrere Stapelsatzvorgaben entfernen möchten.
1. Aktivieren Sie auf der Seite links neben der Spalte **[!UICONTROL Name]** das Kontrollkästchen eines Ordners.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Klicken Sie auf der Seite „Eigenschaften“ des Ordners auf **[!UICONTROL Dynamic Media-Verarbeitung]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Klicken Sie unter **[!UICONTROL Stapelsatzvorgaben]** auf **[!UICONTROL X]** rechts neben dem Vorgabetyp.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern und schließen]**.

## Stapelsatzvorgaben löschen {#delete-bsp}

Sie können Stapelsatzvorgaben löschen, um sie dauerhaft aus [!DNL Dynamic Media] zu entfernen. Das heißt, sie werden nicht mehr auf der Seite [!UICONTROL Stapelsatzvorgabe] angezeigt und auch nicht in der Dropdown-Liste **[!UICONTROL Vorgaben für Stapelsätze]** der Registerkarte **[!UICONTROL Dynamic Media-Verarbeitung]** auf der Seite **[!UICONTROL Eigenschaften]** des Ordners. Daher wird die Vorgabe bei einer erneuten Verarbeitung des Ordners oder beim Hochladen neuer Assets in den Ordner nicht auf vorhandene Assets angewendet.

Wenn Sie eine Vorgabe löschen, die zuvor auf einen oder mehrere Ordner angewendet wurde, werden alle Bildsets oder Rotationssets, die aus Assets in diesen Ordnern erstellt wurden, weiterhin unverändert angezeigt.

Wenn Sie stattdessen nur Vorgaben aus Ordnern *entfernen* möchten, finden Sie weitere Informationen unter [Entfernen von Stapelsatzvorgaben aus Ordnern](#remove-bsp-from-folder).

**So löschen Sie Stapelsatzvorgaben:**

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen für eine oder mehrere Stapelsatzvorgaben, die Sie löschen möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Stapelsatzvorgaben löschen]**.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. Klicken Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe(n) löschen]** auf **[!UICONTROL Löschen]**.

   Wenn die zu löschende Vorgabe von einem Asset-Ordner referenziert wurde, klicken Sie stattdessen auf **[!UICONTROL Löschen erzwingen]**.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Bildsets](/help/assets/dynamic-media/image-sets.md)
>* [Rotationssets](/help/assets/dynamic-media/spin-sets.md)
>* [Konfigurieren von selektiver Veröffentlichung auf der Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder) – Weitere Informationen zum Synchronisieren eines einzelnen Ordners mit [!DNL Dynamic Media] finden Sie unter „Sync-Modus“ in diesem Thema.
>* [Erstellen einer Dynamic Media-Konfiguration in Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) – Weitere Informationen zum Synchronisieren aller Ordner mit [!DNL Dynamic Media] finden Sie unter „Dynamic Media-Sync-Modus“ in diesem Thema.
