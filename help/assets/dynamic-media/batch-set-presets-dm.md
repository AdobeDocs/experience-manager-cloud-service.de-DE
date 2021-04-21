---
title: Stapelsatzvorgaben
description: Erfahren Sie, wie Sie die Erstellung von Bildsets und Rotationssets mithilfe von Stapelsatzvorgaben in Dynamic Media automatisieren.
contentOwner: Rick Brough
feature: Bildvorgaben,Viewer-Vorgaben
role: Business Practitioner
exl-id: 022ee347-54ec-4cec-b808-9eb3a9e51424
translation-type: tm+mt
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '3444'
ht-degree: 58%

---

# Über Stapelsatzvorgaben {#about-bsp}

Verwenden Sie **[!UICONTROL Stapelsatzvorgaben]**, um mehrere Assets in einem Bildsatz oder Rotationsset zu erstellen und zu organisieren, wenn Sie Asset-Dateien entweder einzeln oder mit Massenaufnahmen in einen Ordner hochladen. Sie können die Vorgaben zusammen mit den von Ihnen in [!DNL Dynamic Media] eingeplanten Asset-Importaufträgen ausführen lassen. Jede Vorgabe ist ein eindeutig benannter, in sich abgeschlossener Satz von Anweisungen, die definieren, wie das Bildset oder Rotationsset mithilfe von Bildern erstellt wird, die den definierten Namenskonventionen im Vorgabenrezept entsprechen.

>[!IMPORTANT]
>
>Wenn Sie Stapelsatzvorgaben in [!DNL Dynamic Media Classic] verwendet haben und als Cloud Service von [!DNL Dynamic Media Classic] zu Adobe Experience Manager migrieren, erstellen Sie Ihre Stapelsatzvorgaben-Definitionen manuell in [!DNL Adobe Experience Manager as a Cloud Service].

**Best Practice** : Beim Arbeiten mit Stapelsatzvorgaben empfiehlt die Adobe den folgenden Arbeitsablauf:

1. Erstellen Sie eine Stapelsatzvorgabe. Weitere Informationen finden Sie unter [Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset](#creating-bsp).
1. Erstellen Sie einen Asset-Ordner oder verwenden Sie einen vorhandenen Asset-Ordner und stellen Sie sicher, dass dieser mit [!DNL Dynamic Media] synchronisiert wird. Weitere Informationen finden Sie unter [Erstellen von Ordnern](/help/assets/manage-digital-assets.md#creating-folders).
1. Wenden Sie die Stapelsatzvorgabe auf den Asset-Ordner an. Weitere Informationen finden Sie unter [Informationen zum Anwenden von Stapelsatzvorgaben auf Ordner](#apply-bsp).
1. Laden Sie Bilder in den Asset-Ordner hoch. Weitere Informationen finden Sie unter [Hochladen von Assets für Bildsets](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [Hochladen von Assets für Rotationssets](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets) oder [Hinzufügen digitalen Assets zu Adobe Experience Manager](/help/assets/add-assets.md#add-assets-to-experience-manager).
1. Bildsatz oder Rotationsset wird automatisch im gewünschten Ordner generiert.
1. Veröffentlichen Sie Ihr Bildset oder Rotationsset. Weitere Informationen finden Sie unter [Veröffentlichen von Dynamic Media-Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset {#creating-bsp}

Um Stapelsatzvorgaben zu erstellen, sollten Sie sich mit regulären Ausdrücken vertraut machen und diese verstehen.

Idealerweise hat Ihre Firma bereits eine Benennungsregel für die Gruppierung von Assets in einem Satz festgelegt.
Um Ihnen die Bedeutung der Verwendung einer Namenskonvention zu verdeutlichen, nehmen wir an, dass die definierte Namenskonvention Ihres Unternehmens `<style>-<color>-<view>` lautet. Der Grundname für das Set muss immer `<style>-<color>` lauten und die Namenserweiterung des Sets muss `-SET` sein. Wenn Sie ein Bild mit dem Namen `0123-RED-01` hochladen, wird ein Set mit dem Namen `0123-RED-SET` erstellt. Wenn Sie später die Bilder `0123-RED-03` und `0123-BLUE-01` hochladen, wird das Bild `RED-03` dem Set an der zweiten Position hinzugefügt, da es niedriger als `01` sortiert ist. Das Bild `BLUE-01` wäre jedoch Teil eines neuen Sets mit dem Namen `0123-BLUE-SET`. Beim nächsten Hochladen von Assets fügen Sie die Dateien `0123-RED-02` und `0123-BLUE-02` hinzu. Jedes Asset wird seinem jeweiligen Set hinzugefügt. Das Bild `RED-02` wird aufgrund der Sortierreihenfolge automatisch zwischen den vorhandenen Bildern `01` und `03` sortiert.

Auf der Seite **[!UICONTROL Stapelsatzvorgabe]** in [!DNL Dynamic Media] können Sie Stapelsatzvorgaben erstellen, bearbeiten oder löschen und Stapelsatzvorgaben auf Asset-Ordner anwenden oder daraus entfernen. Sie können entweder die Dropdown-Listen für Formularfelder verwenden, um eine Stapelsatzvorgabe zu definieren, oder das Feld **[!UICONTROL Raw-Code]** verwenden, mit dem Sie die Syntax für reguläre Ausdrücke eingeben können.

Sie können so viele Stapelsatzvorgaben wie nötig erstellen, um alle erforderlichen Asset-Aufnahmeaufträge abzudecken.

**Über Asset-Benennungskonventionen**

Der Bereich **[!UICONTROL Asset-Benennungsregel]** auf der Seite **[!UICONTROL Stapelsatzvorgabe]** enthält zwei Elemente, die Sie zum Definieren Ihrer Stapelsatzvorgabe verwenden können: **[!UICONTROL Übereinstimmung]** und **[!UICONTROL Basisname]**. Mit diesen Elementen können Sie eine Namenskonvention definieren und den Teil der Konvention identifizieren, der zum Benennen des Sets verwendet wird, der diese Elemente enthält. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

Die Benennungsregel einer Firma verwendet häufig eine oder mehrere Definitionszeilen aus diesen beiden Elementen. Sie können für Ihre eindeutige Definition so viele Zeilen wie erforderlich verwenden und sie zu eindeutigen Elementen gruppieren, beispielsweise Elementen für Hauptbild, Farbe, alternative Ansicht und Muster.

Beispielsweise könnte die Syntax für einen regulären Ausdruck mit einer wörtlichen Übereinstimmung wie folgt aussehen:

`(\w+)-\w+-\w+`

**Über die Sequenzreihenfolge**

Sie können optional die Reihenfolge definieren, in der Bilder angezeigt werden, nachdem der Bildsatz oder das Rotationsset in [!DNL Dynamic Media] gruppiert wurde. Die Assets werden standardmäßig in alphanumerischer Reihenfolge angeordnet. Sie können jedoch auch eine durch Kommas getrennte Liste mit regulären Ausdrücken verwenden, um die Reihenfolge anzupassen.

In Bezug auf die Automatisierung der Sequenzreihenfolge geben Sie Regeln an, um bei Bedarf eine bestimmte Sortierung von Assets zu erzwingen. Nehmen Sie zum Beispiel an, dass Ihr erstes Asset immer `_main` heißt und Sie möchten, dass darauf `_alt1`, `_alt2`, `_alt3` usw. folgen. In solchen Fällen können Sie eine Regel für die Sequenzreihenfolge mit der folgenden Syntax erstellen:

`.*_main,.*_alt[0-9]`

Obwohl eine Sortierungssequenz möglich ist, sollten Sie sich bei der Sequenzreihenfolge möglichst auf die alphanumerische Nummerierung verlassen. Darüber hinaus können Sie die Bildsatz- oder Rotationsset-Editor-Werkzeuge in [!DNL Dynamic Media] verwenden, um die Reihenfolge der Assets neu anzuordnen oder neue Assets im Satz mithilfe eines Drag &amp; Drop-Vorgangs hinzuzufügen und zu löschen.

Nach dem Erstellen einer Stapelsatzvorgabe wenden Sie diese auf einen oder mehrere von Ihnen erstellte Ordner an. Weitere Informationen finden Sie unter [Informationen zum Anwenden von Stapelsatzvorgaben auf Ordner](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**So erstellen Sie eine Stapelsatzvorgabe für ein Bildset oder Rotationsset:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. Tippen Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** rechts oben auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe erstellen]** im Textfeld **[!UICONTROL Vorgabenname]** einen beschreibenden Namen ein. Der Vorgabenname kann nicht bearbeitet werden, wenn Sie ihn später ändern möchten.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Vorgabetyp]** die Option **[!UICONTROL Bildset]** oder **[!UICONTROL Rotationsset]** aus. Stellen Sie sicher, dass Sie den richtigen Vorgabetyp auswählen. Es kann später nicht bearbeitet werden.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Legen Sie rechts auf der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** die bearbeitbaren Optionen fest, die Sie unter den Überschriften **[!UICONTROL Vorgabendetails]** und **[!UICONTROL Benennungskonvention festlegen]** verwenden möchten.
Weitere Informationen zu den bearbeitbaren Optionen, die Ihnen zur Verfügung stehen, finden Sie unter [Vorgabedetails, Namenskonvention festlegen und Regelergebnisse - RegX-Optionen](#features-options-bsp).

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. Erstellen Sie eine oder mehrere Gruppen mit regulären Ausdrücken.

   * Tippen Sie links auf der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** unter **[!UICONTROL Übereinstimmung]**, **[!UICONTROL Basisname]** oder **[!UICONTROL Sequenzreihenfolge]** auf **[!UICONTROL Hinzufügen Gruppe]**.
   * Das Feld **[!UICONTROL Übereinstimmung]** ist erforderlich. **[!UICONTROL Basisnamen]** sind nur dann obligatorisch, wenn im  **** Feld &quot;Übereinstimmung&quot;nicht bereits ein Basisname mithilfe einer Klammergruppierung angegeben wurde. **[!UICONTROL Sequenzreihenfolge]** ist optional.
   * Geben Sie mithilfe der Dropdown-Listen und Textfelder im Gruppenformular eine Ausdrucksgruppe an, die Sie zur Definition der Benennungskriterien für die Assets des Bildsets oder des Rotationsets verwenden möchten.
      * Wenn Sie Ausdruck für eine Gruppe auswählen und angeben, beachten Sie, dass die tatsächliche Syntax des regulären Ausdrucks unten rechts auf der Seite unter der Überschrift **[!UICONTROL Regelergebnisse - RegX]** angezeigt wird. Um die Zeichenfolge des regulären Ausdrucks unten rechts zu aktualisieren, tippen Sie auf eine beliebige Stelle außerhalb des Formularbereichs. Diese Zeichenfolgen für reguläre Ausdrücke stellen das Muster dar, mit dem Sie bei der Suche nach [!DNL Dynamic Media]-Assets übereinstimmen möchten, um Ihr Bildset oder Rotationsset zu erstellen.
      * Um eine hinzugefügte Gruppe zu entfernen, tippen Sie auf **[!UICONTROL X]**.
   * Wenn Sie zwei oder mehr Gruppen hinzufügen, wählen Sie in der Dropdown-Liste **[!UICONTROL Und]** die Option **[!UICONTROL Und]** aus, um eine neu hinzugefügte Gruppe mit einer zuvor hinzugefügten Ausdrucksgruppe zu verbinden. Oder wählen Sie **[!UICONTROL Oder]** aus, um die vorherige Ausdrucksgruppe und die neu erstellte Gruppe abwechselnd hinzuzufügen. Der Operand **[!UICONTROL Oder]** wird durch die Verwendung eines vertikalen Linienzeichens `|` in der Syntax des regulären Ausdrucks selbst definiert.

1. Führen Sie einen der folgenden Schritte aus:

   * Um eine weitere neue Gruppe hinzuzufügen, klicken Sie unter **[!UICONTROL Übereinstimmung]**, **[!UICONTROL Grundname]** oder **[!UICONTROL Sequenzreihenfolge]** auf **[!UICONTROL Gruppe hinzufügen]**. Erstellen Sie eine weitere Gruppe mit regulären Ausdrücken wie im vorherigen Schritt.
   * Überprüfen Sie die Syntax für reguläre Ausdrücke im Bereich **[!UICONTROL Regelresultate – RegX]**. Wenn Sie die Syntax ändern müssen, bearbeiten Sie die entsprechende Gruppe links auf der Seite.
   * Wenn Sie mit der Erstellung der Ausdruck-Gruppen fertig sind, fahren Sie mit dem nächsten Schritt fort.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.

Sie können die Stapelsatzvorgabe jetzt auf einen Asset-Ordner anwenden. Anschließend laden Sie Assets in diesen Ordner hoch. Dieser Arbeitsablauf führt zur automatischen Erstellung Ihres Bildsatzes oder Rotationssets. Siehe [Informationen zum Anwenden von Stapelsatzvorgaben auf Asset-Ordner](#apply-bsp).

### Optionen „Vorgabendetails“, „Benennungskonvention festlegen“ und „Regelresultate – RegX“ {#features-options-bsp}

Diese Optionen stehen auf der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** zur Verfügung, wenn Sie eine Stapelsatzvorgabe erstellen oder bearbeiten.

Weitere Informationen finden Sie unter [Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset](#creating-bsp) oder unter [Bearbeiten einer Stapelsatzvorgabe](#edit-bsp).

| **[!UICONTROL Vorgabendetails]** | Beschreibung |
| --- | --- |
| Vorgabenname | Schreibgeschützt. Der Name, den Sie beim ersten Erstellen des Stapelsatzes angegeben haben. Wenn Sie die Vorgabe umbenennen müssen, können Sie die vorhandene Stapelsatzvorgabe kopieren und einen neuen Namen angeben. Weitere Informationen finden Sie unter [Kopieren einer vorhandenen Stapelsatzvorgabe](#copy-bsp). |
| Typ | Schreibgeschützt. Der Typ wurde beim ersten Erstellen des Stapelsatzes angegeben. Durch Kopieren einer vorhandenen Stapelsatzvorgabe können Sie deren [!UICONTROL Typ] nicht ändern. Sie müssen stattdessen eine Vorgabe erstellen. |
| Abgeleitete Assets einschließen | Optional. Wenn die IPS von [!DNL Dynamic Media] generierte oder abgeleitete Bilder mit dem Rotationsset oder Bildsatz enthalten sollen, wählen Sie **[!UICONTROL Ja]** (Standard). Ein abgeleitetes Asset ist ein Bild, das nicht direkt von einem Benutzer hochgeladen wurde. Stattdessen wurde das Asset vom IPS erzeugt, wenn ein primäres Asset hochgeladen wurde. Zum Beispiel wird ein Bild-Asset, das IPS aus einer Seite in einer PDF-Datei generiert hat, als die PDF-Datei in [!DNL Dynamic Media] hochgeladen wurde, als abgeleitetes Asset betrachtet. |
| Zielordner | Optional. Wenn Sie eine große Anzahl von Bildsätzen oder Rotationssets definieren, empfiehlt Adobe, diese Bildsätze von den Ordnern, die die Assets selbst enthalten, getrennt zu halten. Erstellen Sie daher einen Ordner &quot;Bildsätze&quot;oder &quot;Rotationssets&quot;und leiten Sie die Anwendung an die Stelle, an der die Stapelsätze erstellt wurden.<br>Geben Sie in diesem Fall an, für welchen Ordner in der Ordnerstruktur &quot;Experience Manager Assets&quot;(`/content/dam`) die Stapelsatzvorgabe aktiv ist. Stellen Sie sicher, dass der Ordner für die [!DNL Dynamic Media]-Synchronisierung aktiviert ist, um ihn als Zielordner zuzulassen. Weitere Informationen finden Sie unter [Konfigurieren von selektiver Veröffentlichung auf der Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder).<br>Es kann mehreren Ordnern eine bestimmte Stapelsatzvorgabe zugewiesen werden, wenn Sie die Vorgabe mithilfe der  **[!UICONTROL Eigenschaften]** des Ordners anwenden. Weitere Informationen finden Sie unter [Anwenden von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Asset-Ordners](#apply-bsp-to-folders-via-properties).<br>Wenn Sie keinen Ordner angeben, wird der mit der Stapelsatzvorgabe erstellte Bildsatz oder Rotationsset im selben Ordner erstellt, in den Sie den Asset-Ordner hochgeladen haben. |
| **[!UICONTROL Benennungskonvention festlegen]** |  |
| Präfix<br>oder<br>Suffix | Optional. Geben Sie entweder ein Präfix, ein Suffix oder beide in die entsprechenden Felder ein.<br>Mit den Feldern &quot;Präfix&quot;und &quot;Suffix&quot;können Sie so viele Stapelsatzvorgaben mit einer alternativen, benutzerdefinierten Dateibenennungsregel für einen bestimmten Inhaltssatz erstellen. Diese Methode ist besonders in Fällen nützlich, in denen es eine Ausnahme vom definierten Standardbenennungsschema eines Unternehmens gibt.<br>Das Präfix oder Suffix wird dem **[!UICONTROL Grundnamen]** hinzugefügt, den Sie im Bereich **[!UICONTROL Asset-Benennungskonvention]** festlegen. Durch Hinzufügen eines Präfix oder Suffixs stellen Sie sicher, dass der Bildsatz oder das Rotationsset ausschließlich und unabhängig von anderen Assets erstellt wird. Dies kann auch dazu dienen, anderen bei der Identifizierung von Dateitypen zu helfen. Um beispielsweise einen verwendeten Farbmodus zu bestimmen, können Sie `rgb` oder `cmyk` als Präfix oder Suffix hinzufügen.<br>Es ist nicht erforderlich, eine Benennungsregel für Stapelsatzvorgaben festzulegen. Es empfiehlt sich jedoch, die Benennungsregel für Stapelsätze zu verwenden. Auf diese Weise können Sie so viele Elemente Ihrer Benennungsregel definieren, die Sie in einem Satz gruppieren möchten, um die Erstellung von Stapelsätzen zu optimieren. |
| **[!UICONTROL Regelresultate – RegX]** |  |
| Asset-Benennungskonvention – Übereinstimmung | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den von Ihnen gewählten Formularoptionen „Übereinstimmung“ oder dem eingegebenen Raw-Code an. |
| Asset-Benennungskonvention – Grundname | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den von Ihnen gewählten Formularoptionen „Grundname“ oder dem eingegebenen Raw-Code an. |
| Sequenzreihenfolge – Übereinstimmung | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den von Ihnen gewählten Optionen des Formulars oder dem eingegebenen Raw-Code an. |

## Stapelsatzvorgaben auf Asset-Ordner {#apply-bsp} anwenden

Wenn Sie Stapelsatzvorgaben einem oder mehreren Asset-Ordnern zuweisen, übernehmen alle Unterordner automatisch die Vorgaben aus dem übergeordneten Ordner.

Sie können mehrere Stapelsatzvorgaben auf einen Asset-Ordner anwenden.

Ordner, denen eine Stapelvorgabe zugewiesen ist, werden in der Benutzeroberfläche mit dem Namen der Vorgabe angezeigt, die im Ordner in der Ansicht **[!UICONTROL Card]** aufgeführt ist.

Um Stapelsatzvorgaben auf Asset-Ordner anzuwenden, verwenden Sie eine der beiden folgenden Methoden:

* [Anwenden der Stapelsatzvorgaben auf Asset-Ordner auf der Seite „Stapelsatzvorgabe“](#apply-bsp-to-folders-via-bsp-page) – Diese Methode bietet Ihnen die größte Flexibilität. Sie können eine oder mehrere Vorgaben auf einen oder mehrere Ordner anwenden.
* [Anwenden von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Asset-Ordners](#apply-bsp-to-folders-via-properties) – Mit dieser Methode können Sie eine oder mehrere Stapelsatzvorgaben auf einen Ordner anwenden.

Vergewissern Sie sich, dass die Asset-Ordner mit [!DNL Dynamic Media] synchronisiert werden, und wenden Sie dann die gewünschten Vorgaben an.

Verarbeiten Sie Assets in einem Ordner neu, wenn eines der folgenden beiden Szenarien eintritt:

* Sie möchten eine Stapelsatzvorgabe für einen vorhandenen Asset-Ordner ausführen, in den bereits Assets hochgeladen wurden.
* Sie bearbeiten später eine vorhandene Stapelsatzvorgabe, die zuvor auf einen Asset-Ordner angewendet wurde.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Anwenden von Stapelsatzvorgaben auf Asset-Ordner auf der Seite „Stapelsatzvorgabe“ {#apply-bsp-to-folders-via-bsp-page}

1. Tippen Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen jeder Stapelsatzvorgabe, die Sie auf Ordner anwenden möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelvorgabe auf Ordner]** anwenden.
1. Aktivieren Sie auf der Seite **[!UICONTROL Ordner auswählen]** das Kontrollkästchen jedes Ordners, auf den die Stapelsatzvorgaben angewendet werden sollen.
1. Tippen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Ordner auswählen]** auf **[!UICONTROL Anwenden]**.

### Anwenden von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Asset-Ordners {#apply-bsp-to-folders-via-properties}

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Navigieren Sie zu einem Ordner, auf den Sie eine oder mehrere Stapelsatzvorgaben anwenden möchten.
1. Aktivieren Sie auf der Seite links neben der Spalte **[!UICONTROL Name]** das Kontrollkästchen eines Ordners.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Tippen Sie auf der Seite „Eigenschaften“ des Ordners auf die Registerkarte **[!UICONTROL Dynamic Media-Verarbeitung]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Wählen Sie unter **[!UICONTROL Stapelsatzvorgaben]** aus dem Dropdown-Feld **[!UICONTROL Vorgabenname]** den Liste einer Stapelsatzvorgabe aus, die Sie anwenden möchten. Der Screenshot oben zeigt zwei ausgewählte Stapelsatzvorgaben, die auf den Asset-Ordner angewendet werden.

   Wenn im Dropdown-Listenfeld **[!UICONTROL Vorgabename]** keine Stapelsatzvorgaben vorhanden sind, bedeutet dies, dass Sie noch keine Stapelsatzvorgaben erstellt haben. Weitere Informationen finden Sie unter [Erstellen einer Stapelsatzvorgabe für ein Bildset oder Rotationsset](#creating-bsp).

   Um eine angewendete Stapelsatzvorgabe zu entfernen, tippen Sie auf **[!UICONTROL X]** rechts neben dem Vorgabetyp.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern und schließen]**.

## Bearbeiten einer Stapelsatzvorgabe {#edit-bsp}

Sie können eine von Ihnen bereits erstellte Stapelsatzvorgabe bearbeiten. Sie können jede der Ausdrucksgruppen ändern, die Sie für die Asset-Benennungskonvention oder die Asset-Reihenfolge erstellt haben. Bei Bedarf können Sie auch den Zielordner aktualisieren und Namenskonventionen festlegen.

Der Name und der Vorgabetyp der Vorgabe (Bildset oder Rotationsset) können jedoch nicht geändert werden. Wenn der Name einer Vorgabe geändert werden muss, kopieren Sie die vorhandene Vorgabe und geben Sie einen neuen Namen an. Weitere Informationen finden Sie unter [Kopieren einer Stapelsatzvorgabe](#copy-bsp).

Wenn Sie eine Stapelsatzvorgabe bearbeiten, die zuvor auf einen Ordner angewendet wurde, wird die neu bearbeitete Stapelsatzvorgabe nur auf neue Assets angewendet, die in diesen Ordner hochgeladen wurden.

Wenn die neu bearbeitete Vorgabe erneut auf die vorhandenen Assets im Ordner angewendet werden soll, müssen Sie den Ordner erneut verarbeiten. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->Auf diese Weise können die vorhandenen Assets nun als Teil eines Bildsets oder Rotationssets betrachtet und hinzugefügt werden. Darüber hinaus werden die vorhandenen Assets, die bereits im Bildsatz oder Rotationsset enthalten waren - basierend auf der zuvor verwendeten Stapelsatzvorgabe - nicht entfernt und unverändert angezeigt. Bei diesem Szenario wird davon ausgegangen, dass sie sich nicht mehr auf der Grundlage der neu bearbeiteten Vorgabe qualifizieren.

**So bearbeiten Sie eine Stapelsatzvorgabe:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** die Stapelsatzvorgabe, die Sie ändern möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelsatzvorgabe bearbeiten]**.
1. Bearbeiten Sie die Vorgabe nach Bedarf.
1. Tippen Sie oben rechts auf der Seite **[!UICONTROL Stapelsatzvorgabe]** auf **[!UICONTROL Speichern]**.

## Kopieren einer vorhandenen Stapelsatzvorgabe {#copy-bsp}

Sie können eine vorhandene Stapelsatzvorgabe kopieren, um zu vermeiden, dass eine komplexe Vorgabe manuell neu erstellt werden muss oder Sie eine Vorgabe einfach umbenennen möchten. Der verwendete Vorgabetyp (Bildset oder Rotationsset) kann jedoch nicht geändert werden.

Wenn Sie eine vorhandene Vorgabe kopieren, die von Asset-Ordnern referenziert wird, sind diese Ordner nicht betroffen.

**So kopieren Sie eine vorhandene Stapelsatzvorgabe:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen der Stapelsatzvorgabe, die Sie kopieren möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe kopieren]** im Textfeld **[!UICONTROL Titel]** einen neuen Namen für die Vorgabe ein.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. Tippen Sie auf **[!UICONTROL Kopieren]**.

## Informationen zum Entfernen von Stapelsatzvorgaben aus Ordnern {#remove-bsp-from-folder}

Wenn Sie Stapelsatzvorgaben aus Ordnern entfernen, wird für neue Assets, die Sie in diese Ordner hochladen, nicht die Stapelsatzvorgabe angewendet. Vorhandene Assets im Ordner, die dem Bildsatz oder dem Rotationsset bereits hinzugefügt wurden, basierend auf der Stapelsatzvorgabe, die auf den Ordner angewendet wurde. Weiter, um den Status anzuzeigen.

Wenn Sie stattdessen die Vorgaben aus den Ordnern *löschen* möchten, finden Sie weitere Informationen unter [Löschen von Stapelsatzvorgaben](#delete-bsp).

Es gibt zwei Methoden, mit denen Sie Stapelsatzvorgaben aus Ordnern entfernen können.

* [Entfernen von Stapelsatzvorgaben aus Ordnern auf der Seite „Stapelsatzvorgabe“](#remove-bsp-from-folders-via-bsp-page) – Diese Methode bietet Ihnen die größte Flexibilität. Sie können eine oder mehrere Vorgaben aus einem oder mehreren Ordnern entfernen.
* [Entfernen von Stapelsatzvorgaben auf der Seite „Eigenschaften“ eines Ordners](#remove-bsp-from-folders-via-properties) – Mit dieser Methode können Sie eine oder mehrere Stapelsatzvorgaben aus einem Ordner entfernen.

### Entfernen von Stapelsatzvorgaben aus Ordnern über die Seite „Stapelsatzvorgaben“ {#remove-bsp-from-folders-via-bsp-page}

1. Tippen Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen für eine oder mehrere Stapelsatzvorgaben, die Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelvorgabe aus Ordner]** entfernen.

1. Wählen Sie auf der Seite **[!UICONTROL Ordner]** auswählen einen oder mehrere Ordner aus, in denen die Stapelsatzvorgaben entfernt werden sollen.
1. Tippen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Ordner auswählen]** auf **[!UICONTROL Entfernen]**.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. Tippen Sie im Dialogfeld **[!UICONTROL Profil löschen]** auf **[!UICONTROL Entfernen]**.

### Entfernen von Stapelsatzvorgaben von der Seite „Eigenschaften“ eines Ordners {#remove-bsp-from-folders-via-properties}

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Navigieren Sie zu einem Ordner, aus dem Sie eine oder mehrere Stapelsatzvorgaben entfernen möchten.
1. Aktivieren Sie auf der Seite links neben der Spalte **[!UICONTROL Name]** das Kontrollkästchen eines Ordners.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Tippen Sie auf der Seite „Eigenschaften“ des Ordners auf **[!UICONTROL Dynamic Media-Verarbeitung]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Tippen Sie unter **[!UICONTROL Stapelsatzvorgaben]** auf **[!UICONTROL X]** rechts neben dem Vorgabentyp.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern und schließen]**.

## Löschen von Stapelsatzvorgaben {#delete-bsp}

Sie können Stapelsatzvorgaben löschen, um sie dauerhaft aus [!DNL Dynamic Media] zu entfernen. Das heißt, sie werden nicht mehr auf der Seite [!UICONTROL Stapelsatzvorgaben] angezeigt und auch nicht auf der Dropdown-Liste **[!UICONTROL Stapelsatzvorgaben]** der Registerkarte **[!UICONTROL Dynamic Media-Verarbeitung]** auf der Seite **[!UICONTROL Eigenschaften]** des Ordners. Daher wird die Vorgabe nicht auf vorhandene Assets angewendet, die bei einer erneuten Ordnerverarbeitung oder beim Hochladen neuer Assets in den Ordner vorhanden sind.

Wenn Sie eine Vorgabe löschen, die zuvor auf einen oder mehrere Ordner angewendet wurde, werden Bildsätze oder Rotationssets, die aus Assets in diesen Ordnern erstellt wurden, weiterhin unverändert angezeigt.

Wenn Sie stattdessen *Vorgaben aus Ordnern entfernen möchten, finden Sie weitere Informationen unter [Entfernen von Stapelsatzvorgaben aus Ordnern](#remove-bsp-from-folder).*

**So löschen Sie Stapelsatzvorgaben:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen für eine oder mehrere Stapelsatzvorgaben, die Sie löschen möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelsatzvorgaben löschen]**.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. Tippen Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe(n) löschen]** auf **[!UICONTROL Löschen]**.

   Wenn die zu löschende Vorgabe von einem Asset-Ordner referenziert wurde, tippen Sie stattdessen auf **[!UICONTROL Löschen erzwingen]**.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Bildsets](/help/assets/dynamic-media/image-sets.md)
>* [Rotationssets](/help/assets/dynamic-media/spin-sets.md)
>* [Konfigurieren der selektiven Veröffentlichung auf Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder)  - Weitere Informationen zum Synchronisieren eines einzelnen Ordners finden Sie unter &quot;Synchronisierungsmodus&quot; [!DNL Dynamic Media].
>* [Erstellen einer Dynamic Media-Konfiguration in Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)  - Weitere Informationen zum Synchronisieren aller Ordner mit finden Sie unter &quot;Dynamic Media-Synchronisierungsmodus&quot; [!DNL Dynamic Media].

