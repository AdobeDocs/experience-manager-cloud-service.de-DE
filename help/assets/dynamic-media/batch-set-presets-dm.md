---
title: Stapelsatzvorgaben
description: Erfahren Sie, wie Sie die Erstellung von Bildsätzen und Rotationssets mithilfe von Stapelsatzvorgaben in Dynamic Media automatisieren.
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: c7a2fbb4fa6e81caabab829b876741ecf393a2c3
workflow-type: tm+mt
source-wordcount: '3521'
ht-degree: 3%

---


# Stapelsatzvorgaben {#about-bsp}

Verwenden Sie **[!UICONTROL Stapelsatzvorgaben]**, um die Erstellung und Organisation mehrerer Assets in einem Bildsatz oder Rotationsset beim Hochladen von Asset-Dateien in einen Ordner zu erleichtern, entweder einzeln oder mithilfe der Massenaufnahme. Sie können die Vorgabe zusammen mit den Asset-Importaufträgen ausführen lassen, die Sie in [!DNL Dynamic Media] planen. Jede Vorgabe ist ein eindeutig benannter, in sich abgeschlossener Satz von Anweisungen, die definieren, wie der Bildsatz oder das Rotationsset mithilfe von Bildern erstellt wird, die den definierten Benennungsregeln im Vorgabenrezept entsprechen.

>[!IMPORTANT]
>
>Wenn Sie Stapelsatzvorgaben in [!DNL Dynamic Media Classic] verwendet haben und als Cloud Service von [!DNL Dynamic Media Classic] zu Adobe Experience Manager migrieren, müssen Sie Ihre Stapelsatzvorgaben-Definitionen in [!DNL Adobe Experience Manager as a Cloud Service] manuell neu erstellen.

**Best Practice** : Beim Arbeiten mit Stapelsatzvorgaben empfiehlt die Adobe den folgenden Arbeitsablauf:

1. Erstellen Sie eine Stapelsatzvorgabe. Siehe [Erstellen einer Stapelsatzvorgabe für einen Bildsatz oder einen Rotationsset](#creating-bsp).
1. Erstellen Sie einen neuen Asset-Ordner oder verwenden Sie einen vorhandenen Asset-Ordner und stellen Sie sicher, dass dieser mit [!DNL Dynamic Media] synchronisiert wird. Siehe [Erstellen von Ordnern](/help/assets/manage-digital-assets.md#creating-folders).
1. Wenden Sie die Stapelsatzvorgabe auf den Asset-Ordner an. Siehe [Informationen zum Anwenden von Stapelsatzvorgaben auf Ordner](#apply-bsp).
1. Hochladen von Bildern in den Asset-Ordner. Siehe [Hochladen von Assets für Bildsätze](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [Hochladen von Assets für Rotationssets](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets) oder [Hinzufügen digitalen Assets nach Adobe Experience Manager](/help/assets/add-assets.md#add-assets-to-experience-manager).
1. Erstellen Sie den Bildsatz oder das Rotationsset. Siehe [Bildsätze](/help/assets/dynamic-media/image-sets.md) oder [Rotationssets](/help/assets/dynamic-media/spin-sets.md).
1. Veröffentlichen Sie den Bildsatz oder das Rotationsset. Siehe [Veröffentlichen von Dynamic Media-Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Erstellen einer Stapelsatzvorgabe für einen Bildsatz oder ein Rotationsset {#creating-bsp}

Um Stapelsatzvorgaben zu erstellen, sollten Sie sich mit den regulären Ausdrücken vertraut machen und diese verstehen.

Idealerweise sollte Ihre Firma auch eine definierte Benennungsregel für die Gruppierung von Assets in einem Satz haben.
Damit Sie die Wichtigkeit der Verwendung einer Benennungsregel besser verstehen können, nehmen Sie an, dass die definierte Benennungsregel Ihrer Firma `<style>-<color>-<view>` lautet. Der Basisname für den Satz muss immer `<style>-<color>` und die Endung des Satznamens `-SET` sein. Wenn Sie ein Bild mit dem Namen `0123-RED-01` hochladen, wird ein Satz mit dem Namen `0123-RED-SET` erstellt. Wenn Sie später Bilder `0123-RED-03` und `0123-BLUE-01` hochladen, wird das `RED-03`-Bild dem Satz an der zweiten Position hinzugefügt, da es kleiner als `01` sortiert ist. Das Bild `BLUE-01` wäre jedoch Teil eines neuen Satzes mit dem Namen `0123-BLUE-SET`. Beim nächsten Hochladen von Assets fügen Sie die Dateien `0123-RED-02` und `0123-BLUE-02` hinzu. Jeder Asset wird seinem jeweiligen Satz hinzugefügt. Das `RED-02`-Bild wird aufgrund der Sortierreihenfolge automatisch zwischen den vorhandenen `01`- und `03`-Bildern sortiert.

Auf der Seite **[!UICONTROL Stapelsatzvorgabe]** in [!DNL Dynamic Media] können Sie Stapelsatzvorgaben erstellen, bearbeiten oder löschen und Stapelsatzvorgaben auf Asset-Ordner anwenden oder daraus entfernen. Sie können entweder die Dropdown-Listen für Formularfelder verwenden, um eine Stapelsatzvorgabe zu definieren, oder das Feld **[!UICONTROL Rohcode]** verwenden, mit dem Sie die Syntax für regulären Ausdruck eingeben können.

Sie können so viele Stapelsatzvorgaben wie nötig erstellen, um alle erforderlichen Asset-Erfassungsaufträge abzudecken.

**Asset-Benennungskonvention**

Der Bereich **[!UICONTROL Asset-Benennungskonvention]** auf der Seite **[!UICONTROL Stapelsatzvorgabe]** enthält zwei Elemente, mit denen Sie Ihre Stapelsatzvorgabe definieren können: **[!UICONTROL Übereinstimmung]** und **[!UICONTROL Basisname]**. Mit diesen Elementen können Sie eine Benennungsregel definieren und den Teil der Regel identifizieren, der zum Benennen des Satzes verwendet wird, in dem sie enthalten sind. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

Die Benennungsregel einer Firma verwendet häufig eine oder mehrere Definitionszeilen aus diesen beiden Elementen. Sie können für Ihre eindeutige Definition so viele Zeilen wie erforderlich verwenden und sie zu eindeutigen Elementen gruppieren, beispielsweise Elementen für Hauptbild, Farbe, alternative Ansicht und Muster.

Beispielsweise könnte die Syntax für einen regulären Ausdruck mit einer wörtlichen Übereinstimmung wie folgt aussehen:

`(\w+)-\w+-\w+`

**Sequenzreihenfolge**

Sie können optional die Reihenfolge definieren, in der Bilder angezeigt werden, nachdem der Bildsatz oder das Rotationsset in [!DNL Dynamic Media] gruppiert wurde. Die Assets werden standardmäßig in alphanumerischer Reihenfolge angeordnet. Sie können jedoch auch eine durch Kommas getrennte Liste mit regulären Ausdrücken verwenden, um die Reihenfolge anzupassen.

In Bezug auf die Automatisierung der Sequenzreihenfolge geben Sie Regeln an, um bei Bedarf eine bestimmte Sortierung von Assets zu erzwingen. Angenommen, Ihr erstes Asset trägt immer den Namen `_main` und Sie möchten, dass ihm `_alt1`, `_alt2`, `_alt3` usw. folgen. In solchen Fällen können Sie eine Regel zur Sequenzreihenfolge mit der folgenden Syntax erstellen:

`.*_main,.*_alt[0-9]`

Obwohl eine Sortierungssequenz möglich ist, sollten Sie sich bei der Sequenzreihenfolge im Allgemeinen möglichst auf die alphanumerische Nummerierung verlassen. Darüber hinaus können Sie die Bildsatz- oder Rotationsset-Editor-Werkzeuge in [!DNL Dynamic Media] verwenden, um die Sequenzreihenfolge von Assets einfach neu anzuordnen oder mithilfe eines Drag &amp; Drop-Vorgangs neue Assets im Set hinzuzufügen und zu löschen.

Nach dem Erstellen einer Stapelsatzvorgabe wenden Sie diese auf einen oder mehrere von Ihnen erstellte Ordner an. Siehe [Informationen zum Anwenden von Stapelsatzvorgaben auf Ordner](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**So erstellen Sie eine Stapelsatzvorgabe für einen Bildsatz oder ein Rotationsset:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. Tippen Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** rechts oben auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe erstellen]** im Textfeld **[!UICONTROL Vorgabenname]** einen beschreibenden Namen ein. Beachten Sie, dass der Vorgabenname nicht bearbeitet werden kann, wenn Sie ihn später ändern möchten.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Vorgabentyp]** die Option **[!UICONTROL Bildsatz]** oder **[!UICONTROL Rotationsset]**. Stellen Sie sicher, dass Sie den richtigen Vorgabetyp auswählen. es kann später nicht bearbeitet werden.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Legen Sie auf der rechten Seite der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** unter den Überschriften **[!UICONTROL Vorgabendetails]** und **[!UICONTROL Namenskonvention festlegen]** die bearbeitbaren Optionen fest, die Sie bearbeiten möchten.
Weitere Informationen zu den bearbeitbaren Optionen, die Ihnen zur Verfügung stehen, finden Sie unter [Vorgabendetails, Namenskonvention festlegen und Regelergebnisse - RegX-Optionen](#features-options-bsp).

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. Erstellen Sie eine oder mehrere Gruppen mit regulären Ausdrücken.

   * Tippen Sie auf der linken Seite der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** unter **[!UICONTROL Übereinstimmung]**, **[!UICONTROL Basisname]** oder **[!UICONTROL Sequenzreihenfolge]** auf **[!UICONTROL Hinzufügen Gruppe]**.
   * Das Feld **[!UICONTROL Match]** ist erforderlich. **[!UICONTROL Basisnamen]** sind nur dann obligatorisch, wenn im  **** Feld &quot;Übereinstimmung&quot;nicht bereits ein Basisname über eine Klammergruppierung angegeben wurde. **[!UICONTROL Sequenzreihenfolge]** ist optional.
   * Geben Sie mithilfe der Dropdown-Listen und Textfelder im Gruppenformular eine Ausdruck-Gruppe an, die Sie verwenden möchten, um die Benennungskriterien für Bildsatz- oder Rotationsset-Asset-Mitglieder zu definieren.
      * Wenn Sie Ausdruck für eine Ausdruck-Gruppe auswählen und angeben, wird die tatsächliche Syntax des regulären  unten rechts auf der Seite unter der Überschrift **[!UICONTROL Regelergebnisse - RegX]** angezeigt (Sie müssen ggf. auf eine beliebige Stelle außerhalb des Formularbereichs tippen, um die Zeichenfolge des regulären Ausdrucks unten rechts zu aktualisieren). Diese Zeichenfolgen des regulären Ausdrucks stellen das Muster dar, das Sie bei der Suche nach [!DNL Dynamic Media]-Assets verwenden möchten, um einen Bildsatz oder einen Rotationsset zu erstellen.
      * Um eine hinzugefügte Gruppe zu entfernen, tippen Sie auf **[!UICONTROL X]**.
   * Wenn Sie zwei oder mehr Gruppen hinzufügen, wählen Sie in der Dropdown-Liste **[!UICONTROL und]** **[!UICONTROL und]** die Option , um eine neu hinzugefügte Gruppe mit einer beliebigen vorherigen Ausdruck-Gruppe zu verbinden, die Sie hinzugefügt haben. Oder wählen Sie **[!UICONTROL Oder]**, um eine Alternative zwischen der vorherigen Ausdruck und der neu erstellten Gruppe hinzuzufügen. Der Operand **[!UICONTROL Oder]** wird durch die Verwendung eines vertikalen Linienzeichens `|` in der Syntax des regulären Ausdrucks selbst definiert.

1. Führen Sie einen der folgenden Schritte aus:

   * Um eine weitere neue Gruppe hinzuzufügen, klicken Sie unter **[!UICONTROL Übereinstimmung]**, **[!UICONTROL Basisname]** oder **[!UICONTROL Sequenzierreihenfolge]** auf **[!UICONTROL Hinzufügen Gruppe]**. Erstellen Sie eine weitere Gruppe regulärer Ausdruck wie im vorherigen Schritt.
   * Überprüfen Sie die Syntax des regulären Ausdrucks im Bereich **[!UICONTROL Regelergebnisse - RegX]**. Wenn Sie Änderungen an der Syntax vornehmen müssen, bearbeiten Sie die entsprechende Gruppe auf der linken Seite der Seite.
   * Wenn Sie mit der Erstellung der Ausdruck-Gruppen fertig sind, fahren Sie mit dem nächsten Schritt fort.

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.

Sie können die Stapelsatzvorgabe jetzt auf einen oder mehrere Asset-Ordner anwenden, Assets in den Ordner hochladen und dann Ihren Bildsatz oder Ihr Rotationsset erstellen. Siehe [Informationen zum Anwenden von Stapelsatzvorgaben auf Ordner](#apply-bsp).

### Vorgabendetails, Namenskonvention festlegen und Regelergebnisse - RegX-Optionen {#features-options-bsp}

Diese Optionen stehen auf der Seite **[!UICONTROL Stapelsatzvorgabe bearbeiten]** zur Verfügung, wenn Sie eine Stapelsatzvorgabe erstellen oder bearbeiten.

Siehe [Erstellen einer Stapelsatzvorgabe für einen Bildsatz oder einen Rotationsset](#creating-bsp) oder [Bearbeiten einer Stapelsatzvorgabe](#edit-bsp).

| **[!UICONTROL Vorgabendetails]** | Beschreibung |
| --- | --- |
| Vorgabenname | Schreibgeschützt. Der Name, den Sie beim ersten Erstellen des Stapelsatzes angegeben haben. Wenn Sie die Vorgabe erneut benennen müssen, können Sie die vorhandene Stapelsatzvorgabe kopieren und einen neuen Namen angeben. Siehe [Kopieren einer vorhandenen Stapelsatzvorgabe](#copy-bsp). |
| Typ | Schreibgeschützt. Der Typ wurde beim ersten Erstellen des Stapelsatzes angegeben. Durch Kopieren einer vorhandenen Stapelsatzvorgabe können Sie deren [!UICONTROL Typ] nicht ändern. Sie müssen stattdessen eine neue Vorgabe erstellen. |
| Abgeleitete Assets einschließen | Optional. Wählen Sie **[!UICONTROL Ja]** (Standard) aus, damit die IPS von [!DNL Dynamic Media] generierte oder abgeleitete Bilder mit dem Rotationsset oder Bildsatz enthalten. Ein abgeleitetes Asset ist ein Bild, das nicht direkt von einem Benutzer hochgeladen wurde. Stattdessen wurde das Asset vom IPS erzeugt, wenn ein Übergeordnet Asset hochgeladen wurde. Beispiel: Ein Bild-Asset, das IPS von einer Seite in einer PDF zum Zeitpunkt des Hochladevorgangs der PDF in [!DNL Dynamic Media] generiert hat, gilt als abgeleitetes Asset. |
| Zielordner | Optional.  Wenn Sie eine große Anzahl von Bildsätzen oder Rotationssets definieren, sollten Sie es vorziehen, diese Sätze von den Ordnern, die die Assets selbst enthalten, getrennt zu halten. Daher sollten Sie eventuell die Erstellung eines Ordners für Bildsätze oder Rotationssets erwägen und die Anwendung umleiten, um hier die im Stapelsatz generierten Sets zu platzieren.<br>Geben Sie in diesem Fall an, für welchen Ordner in der Adobe Experience Manager Assets-Ordnerstruktur (`/content/dam`) die Stapelsatzvorgabe aktiv sein soll. Stellen Sie sicher, dass der Ordner für die Synchronisierung [!DNL Dynamic Media] aktiviert ist, damit er als Zielordner zulässig ist. Siehe [Konfigurieren der selektiven Veröffentlichung auf Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder).<br>Achten Sie darauf, dass ihr eine bestimmte Stapelsatzvorgabe in mehr als einem Ordner zugewiesen werden kann, wenn Sie die Vorgabe über die  **[!UICONTROL Eigenschaften]** des Ordners anwenden. Siehe [Anwenden von Stapelsatzvorgaben auf der Seite Eigenschaften eines Asset-Ordners](#apply-bsp-to-folders-via-properties).<br>Wenn Sie keinen Ordner angeben, wird die Stapelsatzvorgabe im selben Ordner wie der Ordner zum Hochladen von Assets erstellt. |
| **[!UICONTROL Benennungskonvention festlegen]** |  |
| Präfix<br>oder<br>Suffix | Optional. Geben Sie entweder ein Präfix, ein Suffix oder beide in die entsprechenden Felder ein.<br>Mit den Feldern &quot;Präfix&quot;und &quot;Suffix&quot;können Sie mithilfe einer alternativen, benutzerdefinierten Dateibenennungsregel so viele Stapelsatzvorgaben erstellen, wie sie für einen bestimmten Inhaltssatz erforderlich sind. Diese Methode ist besonders dann nützlich, wenn es eine Ausnahme von dem definierten Standardbenennungsschema einer Firma gibt.<br>Das Präfix oder Suffix wird dem  **[!UICONTROL Basisnamen hinzugefügt, den Sie im Bereich &quot;]** Asset- **** Benennungskonvention&quot;definieren. Durch Hinzufügen eines Präfix- oder Suffixs stellen Sie sicher, dass der Bildsatz oder das Rotationsset ausschließlich und unabhängig von anderen Assets erstellt wird. Es kann auch dazu beitragen, dass andere Dateitypen leichter identifizieren können. Um beispielsweise einen verwendeten Farbmodus zu bestimmen, können Sie `rgb` oder `cmyk` als Präfix oder Suffix hinzufügen.<br>Es ist nicht erforderlich, eine Benennungsregel für Stapelsatzvorgaben festzulegen. Es empfiehlt sich jedoch, mithilfe der Benennungsregel so viele Elemente Ihrer Benennungsregel wie möglich zu definieren, die Sie in einem Satz gruppieren möchten, um die Erstellung von Stapelsätzen zu vereinfachen. |
| **[!UICONTROL Regelresultate – RegX]** |  |
| Asset-Benennungsregel - Übereinstimmung | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den ausgewählten Übereinstimmungsformularoptionen oder dem eingegebenen Rohcode an. |
| Asset-Benennungsregel - Basisname | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den Formularoptionen &quot;Basisname&quot;oder dem eingegebenen Rohcode an. |
| Sequenzreihenfolge - Übereinstimmung | Schreibgeschützt. Zeigt die Syntax des regulären Ausdrucks basierend auf den ausgewählten Formularoptionen oder dem eingegebenen Rohcode an. |

## Stapelsatzvorgaben auf Ordner {#apply-bsp} anwenden

Wenn Sie Stapelsatzvorgaben einem oder mehreren Ordnern zuweisen, übernehmen alle Unterordner automatisch die Vorgaben aus dem übergeordneten Ordner.

Sie können mehrere Stapelsatzvorgaben auf einen Ordner anwenden.

Ordner, denen eine Stapelvorgabe zugewiesen wurde, werden in der Benutzeroberfläche mit dem Namen der Vorgabe angezeigt, die im Ordner in der Ansicht **[!UICONTROL Card]** aufgeführt ist.

Verwenden Sie eine der beiden folgenden Methoden, um Stapelsatzvorgaben auf Ordner anzuwenden:

* [Wenden Sie Stapelsatzvorgaben auf Asset-Ordner auf der Seite](#apply-bsp-to-folders-via-bsp-page)  &quot;Stapelsatzvorgabe&quot;an. Auf diese Weise erhalten Sie die größtmögliche Flexibilität. Sie können eine oder mehrere Vorgaben auf einen oder mehrere Ordner anwenden.
* [Stapelsatzvorgaben auf der Seite](#apply-bsp-to-folders-via-properties)  Eigenschaften eines Asset-Ordners anwenden - Mit dieser Methode können Sie eine oder mehrere Stapelsatzvorgaben auf einen einzelnen Ordner anwenden.

Vergewissern Sie sich, dass die Asset-Ordner mit [!DNL Dynamic Media] synchronisiert sind, und wenden Sie dann die gewünschten Vorgaben an.

Es ist ggf. erforderlich, Assets in einem Ordner neu zu verarbeiten, wenn eines der beiden folgenden Szenarien eintritt:

* Sie möchten eine Stapelsatzvorgabe für einen vorhandenen Asset-Ordner ausführen, in den bereits Assets hochgeladen wurden.
* Sie bearbeiten später eine vorhandene Stapelsatzvorgabe, die zuvor auf einen Asset-Ordner angewendet wurde.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Anwenden von Stapelsatzvorgaben auf Asset-Ordner auf der Seite &quot;Stapelsatzvorgabe&quot;{#apply-bsp-to-folders-via-bsp-page}

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen der Stapelsatzvorgaben, die Sie auf Ordner anwenden möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelvorgabe auf Ordner(s)]** anwenden.
1. Aktivieren Sie auf der Seite **[!UICONTROL Ordner(s)]** auswählen das Kontrollkästchen jedes Ordners, auf den die Stapelsatzvorgaben angewendet werden sollen.
1. Tippen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Ordner auswählen]** auf **[!UICONTROL Anwenden]**.

### Anwenden von Stapelsatzvorgaben auf der Seite Eigenschaften eines Asset-Ordners {#apply-bsp-to-folders-via-properties}

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Navigieren Sie zu einem Ordner, auf den Sie eine oder mehrere Stapelsatzvorgaben anwenden möchten.
1. Aktivieren Sie auf der Seite links neben der Spalte **[!UICONTROL Name]** das Kontrollkästchen der Variablen
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Tippen Sie auf der Seite Eigenschaften des Ordners auf die Registerkarte **[!UICONTROL Dynamic Media Processing]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Wählen Sie unter **[!UICONTROL Stapelsatzvorgabe(en)]** aus der Dropdown-Liste **[!UICONTROL Vorgabenname]** den Namen einer Stapelsatzvorgabe, die Sie anwenden möchten. Der Screenshot oben zeigt, dass zwei Stapelsatzvorgaben auf den Ordner angewendet wurden.

   Wenn im Dropdown-Feld **[!UICONTROL Vorgabenname]** keine Stapelsatzvorgaben vorhanden sind, bedeutet dies, dass Sie noch keine Stapelsatzvorgaben erstellt haben. Siehe [Erstellen einer Stapelsatzvorgabe für einen Bildsatz oder einen Rotationsset](#creating-bsp).

   Um eine angewendete Stapelsatzvorgabe zu entfernen, tippen Sie auf **[!UICONTROL X]** rechts neben dem Vorgabentyp.

1. Tippen Sie in der oberen rechten Ecke der Seite auf **[!UICONTROL Speichern und Schließen]**.

## Bearbeiten einer Stapelsatzvorgabe {#edit-bsp}

Sie können eine bereits erstellte Stapelsatzvorgabe bearbeiten. Sie können die von Ihnen für die Asset-Benennungsregel oder die Sequenzreihenfolge erstellten Ausdruck-Gruppen ändern. Bei Bedarf können Sie auch den Zielordner aktualisieren und Benennungskonventionen festlegen.

Der Name oder der Vorgabentyp der Vorgabe (Bildsatz oder Rotationsset) können jedoch nicht geändert werden. Wenn der Name einer Vorgabe geändert werden muss, können Sie die vorhandene Vorgabe kopieren und einen neuen Namen angeben. Siehe [Kopieren einer Stapelsatzvorgabe](#copy-bsp).

Wenn Sie eine Stapelsatzvorgabe bearbeiten, die zuvor auf einen Ordner angewendet wurde, wird die neu bearbeitete Vorgabe nur auf neue Assets angewendet, die in den Ordner hochgeladen werden.

Wenn die neu bearbeitete Vorgabe erneut auf die vorhandenen Assets im Ordner angewendet werden soll, müssen Sie den Ordner erneut verarbeiten. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). --> Auf diese Weise können die vorhandenen Assets nun als Teil eines Bildsatzes oder Rotationssets betrachtet und hinzugefügt werden. Darüber hinaus werden die vorhandenen Assets, die basierend auf der zuvor verwendeten Stapelsatzvorgabe bereits im Bildsatz oder Rotationsset enthalten waren, nicht entfernt (sofern sie sich nicht mehr auf der Grundlage der neu bearbeiteten Vorgabe qualifizieren) und wie angezeigt.

**So bearbeiten Sie eine Stapelsatzvorgabe:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben.]**
1. Überprüfen Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** die Stapelsatzvorgabe, die Sie ändern möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelsatzvorgabe bearbeiten.]**
1. Bearbeiten Sie die Vorgabe nach Bedarf.
1. Tippen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Stapelsatzvorgabe]** auf **[!UICONTROL Speichern.]**

## Kopieren einer vorhandenen Stapelsatzvorgabe {#copy-bsp}

Sie können eine vorhandene Stapelsatzvorgabe kopieren, um zu vermeiden, dass eine komplexe Vorgabe manuell neu erstellt werden muss, oder um eine Vorgabe einfach umzubenennen. Der verwendete Vorgabentyp (Bildsatz oder Rotationsset) kann jedoch nicht geändert werden.

Wenn Sie eine vorhandene Vorgabe kopieren, die auf Asset-Ordner verweist, sind diese Ordner davon nicht betroffen.

**So kopieren Sie eine vorhandene Stapelsatzvorgabe:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben.]**
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen der zu kopierenden Stapelsatzvorgabe.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgabe kopieren]** im Textfeld **[!UICONTROL Titel]** einen neuen Namen für die Vorgabe ein.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. Tippen Sie auf **[!UICONTROL Kopieren]**.

## Informationen zum Entfernen von Stapelsatzvorgaben aus Ordnern {#remove-bsp-from-folder}

Wenn Sie Stapelsatzvorgaben aus Ordnern entfernen, wird für neue Assets, die Sie in diese Ordner hochladen, nicht die Stapelsatzvorgabe angewendet. Vorhandene Assets im Ordner, die dem Bildsatz oder dem Rotationsset bereits hinzugefügt wurden, werden auf der Grundlage der Stapelsatzvorgabe, die auf den Ordner angewendet wurde, weiterhin unverändert angezeigt.

Wenn Sie stattdessen die Vorgaben *löschen* aus Ordnern löschen möchten, finden Sie weitere Informationen unter [Löschen von Stapelsatzvorgaben](#delete-bsp).

Es gibt zwei Methoden, mit denen Sie Stapelsatzvorgaben aus Ordnern entfernen können.

* [Entfernen von Stapelsatzvorgaben aus Ordnern über die Seite](#remove-bsp-from-folders-via-bsp-page)  &quot;Stapelsatzvorgabe&quot;- Diese Methode bietet Ihnen die größtmögliche Flexibilität. Sie können eine oder mehrere Vorgaben aus einem oder mehreren Ordnern entfernen.
* [Entfernen von Stapelsatzvorgaben aus der Seite](#remove-bsp-from-folders-via-properties)  Eigenschaften eines Ordners - Mit dieser Methode können Sie eine oder mehrere Stapelsatzvorgaben nur aus einem einzelnen Ordner entfernen.

### Entfernen von Stapelsatzvorgaben aus Ordnern über die Seite &quot;Stapelsatzvorgaben {#remove-bsp-from-folders-via-bsp-page}

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen einer oder mehrerer Stapelsatzvorgaben, die Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelvorgabe aus Ordner(n)]** entfernen.

1. Wählen Sie auf der Seite **[!UICONTROL Ordner(s)]** auswählen einen oder mehrere Ordner aus, in denen die Stapelsatzvorgaben entfernt werden sollen. Der Screenshot oben zeigt einen ausgewählten Ordner mit den Namen von zwei Stapelsatzvorgaben, die bereits darauf angewendet wurden und entfernt werden.
1. Tippen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Ordner auswählen]** auf **[!UICONTROL Entfernen]**.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. Tippen Sie im Dialogfeld **[!UICONTROL Profil entfernen]** auf **[!UICONTROL Entfernen]**.

### Entfernen von Stapelsatzvorgaben von der Seite Eigenschaften eines Ordners {#remove-bsp-from-folders-via-properties}

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Navigieren Sie zu einem Ordner, in den Sie eine oder mehrere Stapelsatzvorgaben entfernen möchten.
1. Aktivieren Sie auf der Seite links neben der Spalte **[!UICONTROL Name]** das Kontrollkästchen eines Ordners.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Tippen Sie auf der Seite Eigenschaften des Ordners auf **[!UICONTROL Dynamic Media Processing]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Tippen Sie unter **[!UICONTROL Stapelsatzvorgabe(en)]** auf **[!UICONTROL X]** rechts neben dem Vorgabentyp.

1. Tippen Sie in der oberen rechten Ecke der Seite auf **[!UICONTROL Speichern und Schließen]**.

## Löschen von Stapelsatzvorgaben {#delete-bsp}

Sie können Stapelsatzvorgaben löschen, um sie dauerhaft von [!DNL Dynamic Media] zu entfernen. Das heißt, sie werden nicht mehr auf der Seite [!UICONTROL Stapelsatzvorgabe] angezeigt und auch nicht in der Dropdown-Liste **[!UICONTROL Dynamic Media-Verarbeitung]** auf der Ordnerseite **[!UICONTROL Eigenschaften]**. ]****[!UICONTROL  Daher wird die Vorgabe nicht auf vorhandene Assets angewendet, die bei einer Ordnerneuverarbeitung oder beim Hochladen neuer Assets in den Ordner erneut verarbeitet werden.

Wenn Sie eine Vorgabe löschen, die zuvor auf einen oder mehrere Ordner angewendet wurde, werden Bildsätze oder Rotationssets, die aus Assets in diesen Ordnern erstellt wurden, weiterhin unverändert angezeigt.

Wenn Sie stattdessen nur *Vorgaben aus Ordnern entfernen möchten, lesen Sie [Entfernen von Stapelsatzvorgaben aus Ordnern](#remove-bsp-from-folder).*

**So löschen Sie Stapelsatzvorgaben:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Stapelsatzvorgaben]**.
1. Aktivieren Sie auf der Seite **[!UICONTROL Stapelsatzvorgaben]** links neben der Spalte **[!UICONTROL Vorgabenname]** das Kontrollkästchen der zu löschenden Stapelsatzvorgaben.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Stapelsatzvorgabe(en)]** löschen.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. Tippen Sie im Dialogfeld **[!UICONTROL Stapelsatzvorgaben löschen]** auf **[!UICONTROL Löschen]**.

   Wenn die zu löschende Vorgabe von einem Asset-Ordner referenziert wurde, müssen Sie eventuell stattdessen auf **[!UICONTROL Löschen erzwingen]** tippen.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Bildsets](/help/assets/dynamic-media/image-sets.md)
>* [Rotationssets](/help/assets/dynamic-media/spin-sets.md)
>* [Konfigurieren der selektiven Veröffentlichung auf Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder)  - Weitere Informationen zum Synchronisieren eines einzelnen Ordners mit finden Sie unter &quot;Synchronisierungsmodus&quot; [!DNL Dynamic Media].
>* [Erstellen einer neuen Dynamic Media-Konfiguration in Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)  - Weitere Informationen zum Synchronisieren aller Ordner mit finden Sie unter &quot;Dynamic Media-Synchronisierungsmodus&quot; [!DNL Dynamic Media].