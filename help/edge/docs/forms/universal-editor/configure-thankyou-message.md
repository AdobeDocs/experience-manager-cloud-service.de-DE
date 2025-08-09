---
title: Konfigurieren einer Umleitungsseite oder Dankesnachricht
description: Erfahren Sie, wie Benutzenden eine Dankesnachricht angezeigt oder sie auf eine Webseite weitergeleitet werden können, die Formularautorinnen bzw. -autoren bei der Erstellung des Formulars konfigurieren können.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '1682'
ht-degree: 40%

---


# Konfigurieren von Dankesnachrichten und Umleitungs-URLs

Formularfragmente sind wiederverwendbare Komponenten, mit denen sich wiederholende Entwicklungsarbeiten erübrigen und die Konsistenz der Formulare in Ihrem Unternehmen sicherstellen lassen. Anstatt für jedes Formular gemeinsame Abschnitte wie Kontaktinformationen, Adressdetails oder Einverständniserklärungen neu zu erstellen, können Sie diese Elemente einmal als Fragmente erstellen und sie in mehreren Formularen wiederverwenden.

**Was Sie in diesem Artikel erreichen werden:**

- Machen Sie sich mit dem geschäftlichen Nutzen und den technischen Funktionen von Formularfragmenten vertraut
- Erstellen wiederverwendbarer Formularfragmente mit dem universellen Editor
- Integrieren von Fragmenten in vorhandene Formulare mit ordnungsgemäßer Konfiguration
- Verwalten des Lebenszyklus von Fragmenten und Beibehalten der Konsistenz über Formulare hinweg

**Vorteile für Unternehmen:**

- **Verkürzte Entwicklungszeit**: Einmalige Erstellung von allgemeinen Formularabschnitten und Wiederverwendung überall
- **Verbesserte Konsistenz**: Standardisierte Layouts und Inhalte für alle Formulare
- **Vereinfachte Wartung**: Aktualisieren Sie ein Fragment einmal, um Änderungen in allen Formularen widerzuspiegeln, die es verwenden
- **Verbesserte Compliance**: Sicherstellen, dass die regulatorischen Abschnitte konsistent und aktuell bleiben

Formularfragmente in Edge Delivery Services unterstützen erweiterte Funktionen wie verschachtelte Fragmente, mehrere Instanzen innerhalb eines Formulars und die nahtlose Integration in Datenquellen.

## Grundlagen zu Formularfragmenten

Formularfragmente in Edge Delivery Services bieten leistungsstarke Funktionen für die Entwicklung modularer Formulare:

**Kernfunktionen:**

- **Konsistenzmanagement**: Fragmente verwalten identische Layouts und Inhalte in mehreren Formularen. Mit dem Ansatz „Einmal ändern, überall widerspiegeln“ werden Aktualisierungen an einem Fragment automatisch auf alle Formulare im Vorschaumodus angewendet.
- **Mehrfache Verwendung**: Fügen Sie dasselbe Fragment mehrmals in einem einzelnen Formular hinzu, wobei jedes Fragment eine unabhängige Datenbindung an verschiedene Datenquellen oder Schemaelemente aufweist.
- **Verschachtelte Strukturen**: Erstellen Sie komplexe Hierarchien, indem Sie Fragmente in andere Fragmente einbetten, um komplexe Formulararchitekturen zu erstellen.

**Technische Anforderungen:**

- **Konsistenz der GitHub-URL**: Sowohl das Fragment als auch jedes Formular, das es verwendet, müssen dieselbe GitHub-Repository-URL angeben
- **Eigenständige Bearbeitung**: Fragmente können nur in ihrer eigenständigen Form geändert werden. Änderungen können nicht innerhalb des Hostformulars vorgenommen werden.

**Veröffentlichungsverhalten:**

>[!IMPORTANT]
>
>Im Vorschaumodus werden Fragmentänderungen sofort in allen Formularen übernommen. Im Veröffentlichungsmodus müssen Sie sowohl das Fragment als auch alle Formulare, die es verwenden, erneut veröffentlichen, um Aktualisierungen anzuzeigen.

>[!CAUTION]
>
>Vermeiden Sie rekursive Fragmentverweise (Verschachteln eines Fragments in sich selbst), da dies zu Rendering-Fehlern und unerwartetem Verhalten führt.

## Voraussetzungen

**Technische Setup-Anforderungen:**

- [GitHub-Repository konfiguriert](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) Verbindung zwischen Ihrer AEM-Umgebung und dem GitHub-Repository hergestellt
- [Neuester adaptiver Forms-Block](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) zum GitHub-Repository hinzugefügt (für bestehende Edge Delivery Services-Projekte)
- AEM Forms-Autoreninstanz mit Edge Delivery Services-Vorlage verfügbar
- Zugriff auf die URL Ihrer AEM Forms as a Cloud Service-Autoreninstanz und die GitHub-Repository-URL

**Erforderliche Kenntnisse und Berechtigungen:**

- Grundlegendes zu Konzepten des Formularentwurfs und zur Komponentenhierarchie
- Vertrautheit mit der Benutzeroberfläche des universellen Editors und den Workflows zur Formularerstellung
- Berechtigungen auf Autorenebene in AEM Forms zum Erstellen und Verwalten von Formular-Assets
- Verständnis der Formularstandards Ihres Unternehmens und der wiederverwendbaren Komponentenanforderungen

## Arbeiten mit Edge Delivery Services-Formularfragmenten

Sie können Edge Delivery Services-Formularfragmente im universellen Editor erstellen und die erstellten Fragmente zu Edge Delivery Services-Formularen hinzufügen. Sie können mit Edge Delivery Services-Formularfragmenten die folgenden Aktionen durchführen:

- [Erstellen von adaptiven Formularfragmenten](#creating-form-fragments)
- [Hinzufügen von Formularfragmenten zu einem Formular](#adding-form-fragments-to-a-form)
- [Verwalten von Formularfragmenten](#managing-form-fragments)

+++ Erstellen von adaptiven Formularfragmenten

Gehen Sie zum Erstellen eines Formularfragments im universellen Editor wie folgt vor:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Klicken Sie auf **Erstellen > Adaptives Formularfragment**.

   ![Erstellen eines Fragments](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   Der Assistent zum **Erstellen von adaptiven Formularfragmenten** wird angezeigt.
1. Wählen Sie auf der Registerkarte **Vorlage auswählen** die auf Edge Delivery Services basierende Vorlage aus und klicken Sie auf **[!UICONTROL Weiter]**.
   ![Auswählen einer Edge Delivery Services-Vorlage](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. Geben Sie Titel, Namen, Beschreibung und Tags für das Fragment an. Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.
1. Geben Sie die **GitHub-URL** an. Wenn sich Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter der `wkndforms` befindet, wird die URL `https://github.com/wkndforms/edsforms`.

   ![Allgemeine Eigenschaften](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (Optional) Klicken Sie auf die Registerkarte **Formularmodell**, um sie zu öffnen. Wählen Sie dann aus dem Dropdown-Menü **Auswählen** eines der folgenden Fragmentmodelle:

   ![Zeigt den Modelltyp auf der Registerkarte „Formularmodell“ an](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   - **Formulardatenmodell (FDM)**: Zum Integrieren von Datenmodellobjekten und Diensten aus Datenquellen in Ihr Fragment. Wählen Sie „Formulardatenmodell (FDM)“, wenn Ihr Formular das Lesen und Schreiben von Daten aus mehreren Quellen erfordert.

   - **JSON-Schema**: Zum Integrieren Ihres Formulars in ein Backend-System, indem Sie ein JSON-Schema verknüpfen, das die Datenstruktur definiert. Damit können Sie dynamische Inhalte mithilfe der Schemaelemente hinzufügen.
   - **Keine**: Gibt an, dass das Fragment von Grund auf ohne Formularmodell erstellt werden soll.

   >[!NOTE]
   >
   > Informationen zum Integrieren von Formularen oder Fragmenten mit einem Formulardatenmodell (FDM) im universellen Editor zur Verwendung verschiedener Backend-Datenquellen finden Sie unter [Integrieren von Formularen in das Formulardatenmodell im universellen Editor](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

1. (Optional) Geben Sie auf der Registerkarte **Erweitert** das **Veröffentlichungsdatum** oder das **Datum der Aufhebung der Veröffentlichung** für das Fragment an.

   ![Registerkarte „Erweitert“](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. Klicken Sie **Erstellen**, um das Fragment zu generieren. Es wird ein Erfolgsdialogfeld mit Bearbeitungsoptionen angezeigt.

   ![Bearbeiten eines Fragments](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. Klicken Sie **Bearbeiten**, um das Fragment im universellen Editor mit angewendeter Standardvorlage zu öffnen.

   ![Fragment im universellen Editor für das Authoring](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

1. **Gestalten Ihres Fragmentinhalts**: Fügen Sie Formularkomponenten (Textfelder, Dropdown-Listen, Kontrollkästchen) hinzu, um den wiederverwendbaren Abschnitt zu erstellen. Detaillierte Komponentenanleitungen finden Sie unter [Erste Schritte mit Edge Delivery Services für AEM Forms mit dem universellen Editor](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

1. **Komponenteneigenschaften konfigurieren**: Legen Sie Feldnamen, Validierungsregeln und Standardwerte nach Bedarf für Ihren Anwendungsfall fest.

1. **Speichern und Vorschau**: Speichern Sie das Fragment und verwenden Sie den Vorschaumodus, um das Layout und die Funktionalität zu überprüfen.

   ![Screenshot eines ausgefüllten Formularfragments für Kontaktdetails im universellen Editor mit Feldern für Name, Telefon, E-Mail und Adresse, die in mehreren Formularen wiederverwendet werden können](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

**Validierungs-Checkpoint:**

- Fragment wird im universellen Editor fehlerfrei geladen
- Alle Formularkomponenten werden korrekt gerendert
- Feldeigenschaften und Validierungsregeln funktionieren ordnungsgemäß
- Fragment wird gespeichert und ist in der Forms- und Dokumentenkonsole verfügbar

Sobald Ihr Fragment vollständig ist, können Sie [es in ein beliebiges Edge Delivery Services-Formular integrieren](#adding-form-fragments-to-a-form).

+++


+++ Hinzufügen von Formularfragmenten zu einem Formular

Dieses Beispiel zeigt das Erstellen eines `Employee Details` Formulars, das das `Contact Details` Fragment für die Abschnitte „Mitarbeiter“ und „Vorgesetzte“ verwendet. Dieser Ansatz gewährleistet eine konsistente Datenerfassung und reduziert gleichzeitig den Entwicklungsaufwand.

So integrieren Sie ein Formularfragment in Ihr Formular:

1. Öffnen Sie das Formular im Bearbeitungsmodus.
1. Fügen Sie die Komponente „Formularfragment“ dem Formular hinzu.
1. Öffnen Sie den Inhalts-Browser und navigieren Sie in der **Inhaltsstruktur** zur Komponente **[!UICONTROL Adaptives Formular]**.
1. Navigieren Sie zum Abschnitt, in dem ein Fragment hinzugefügt werden soll. Navigieren Sie beispielsweise zum Panel mit den **Mitarbeiterdetails**.

   ![Navigieren zum Abschnitt](/help/edge/docs/forms/universal-editor/assets/navigate-to-section.png)

1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die Komponente **[!UICONTROL Formularfragment]** aus der Liste der **adaptiven Formularkomponenten** hinzu.
   ![Hinzufügen eines Formularfragments](/help/edge/docs/forms/universal-editor/assets/add-fragment.png)

   Wenn Sie die Komponente **[!UICONTROL Formularfragment]** auswählen, wird das Fragment zu Ihrem Formular hinzugefügt. Sie können die Eigenschaften des hinzugefügten Fragments konfigurieren, indem Sie dessen **Eigenschaften** öffnen. Blenden Sie beispielsweise den Titel des Fragments in seinen **Eigenschaften** aus.

   ![Konfigurieren der Fragmenteigenschaften](/help/edge/docs/forms/universal-editor/assets/fragment-properties.png)

1. Wählen Sie den **Fragmentverweis** auf der Registerkarte **Allgemein** aus. Je nach Formularmodell werden alle für Ihr Formular verfügbaren Fragmente angezeigt.

   Navigieren Sie beispielsweise zu `/content/forms/af` und wählen Sie das Fragment `Contact Details` aus:

   ![Auswählen eines Fragments](/help/edge/docs/forms/universal-editor/assets/select-fragment.png)

1. Klicken Sie auf **[!UICONTROL Auswählen]**.

   Das Formularfragment wird per Verweis auf das Formular hinzugefügt und bleibt mit dem eigenständigen Formularfragment synchronisiert.

   ![Screenshot, der zeigt, wie das Fragment „Kontaktdetails“ erfolgreich in ein Mitarbeiterformular im universellen Editor integriert wurde und wie Fragmente ihre Struktur beibehalten, wenn sie wiederverwendet werden](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   Sie können das Formular in einer Vorschau anzeigen, um zu sehen, wie das Formular im Modus **Vorschau** aussieht.

   ![Vorschau](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   Auf ähnliche Weise können Sie die Schritte 3 bis 7 wiederholen, um das Fragment `Contact Details` für das Panel `Supervisor Details` einzufügen.

   ![Formular „Mitarbeiterdetails“](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

+++



+++ Verwalten von Formularfragmenten

Auf der Benutzeroberfläche von AEM Forms können Sie mehrere Aktionen für Formularfragmente ausführen.

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

1. Wenn Sie ein Formularfragment auswählen, werden in der Symbolleiste die folgenden Vorgänge angezeigt, die Sie mit dem ausgewählten Fragment durchführen können.

   ![Verwalten von Fragmenten](/help/edge/docs/forms/universal-editor/assets/manage-fragment.png)

   <table>
    <tbody>
    <tr>
   <td><p><strong>Vorgang</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
    </tr>
    <tr>
   <td><p>Bearbeiten</p> </td>
   <td><p>Öffnet das Formularfragment im Bearbeitungsmodus.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Eigenschaften</p> </td>
   <td><p>Bietet Optionen zum Ändern der Eigenschaften des Formularfragments.<br /> <br /> </p> </td>
    </tr>
    <td><p>Kopieren</p> </td>
   <td><p> Bietet Optionen zum Kopieren des Formularfragments und zum Einfügen des Fragments an der gewünschten Position. <br /> <br /> </p> </td>
    </tr>
   <tr>
   <td><p>Vorschau</p> </td>
   <td><p>Bietet Optionen zum Anzeigen einer HTML-Vorschau des Fragments oder für eine benutzerdefinierte Vorschau des Fragments durch Zusammenführen von Daten aus einer XML-Datei mit dem Fragment. <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Herunterladen</p> </td>
   <td><p>Lädt das ausgewählte Fragment herunter.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Überprüfung starten/Überprüfung verwalten</p> </td>
   <td><p>Ermöglicht es, eine Überprüfung des ausgewählten Fragments zu initiieren und zu verwalten.<br /> <br /> </p> </td>
    </tr>
    <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
    </tr>-->
    <tr>
   <td><p>Veröffentlichen/Veröffentlichung rückgängig machen</p> </td>
   <td><p>Veröffentlicht das ausgewählte Fragment bzw. macht die Veröffentlichung rückgängig.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Löschen</p> </td>
   <td><p>Löscht das ausgewählte Fragment.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Vergleichen</p> </td>
   <td><p>Vergleicht zwei verschiedene Formularfragmente zu Vorschauzwecken.<br /> <br /> </p> </td>
    </tr>
    </tbody>
    </table>

+++

## Best Practices

**Design und Benennung von Fragmenten:**

- **Verwenden beschreibender, eindeutiger Namen** Wählen Sie Namen aus, die den Zweck des Fragments klar angeben (z. B. „contact-details-with-validation“ anstelle von „fragment1„).
- **Wiederverwendbarkeit planen**: Entwerfen Sie Fragmente kontextunabhängig, sodass sie über verschiedene Formulartypen hinweg funktionieren
- **Fragmente fokussiert halten**: Erstellen Sie Fragmente für einen einzigen Zweck anstelle von komplexen, multifunktionalen Komponenten

**Entwicklungs-Workflow:**

- **Fragmente unabhängig testen**: Überprüfen der Fragmentfunktionalität vor der Integration in Formulare
- **Konsistente GitHub-URLs beibehalten**: Stellen Sie sicher, dass in allen zugehörigen Fragmenten und Formularen dieselbe Repository-URL verwendet wird
- **Zweck von Dokumentfragmenten**: Geben Sie klare Beschreibungen und Tags an, damit Team-Mitglieder verstehen können, wann die einzelnen Fragmente verwendet werden sollen

**Veröffentlichung und Wartung:**

- **Veröffentlichung koordinieren**: Planen Sie beim Aktualisieren von Fragmenten, alle abhängigen Formulare gleichzeitig erneut zu veröffentlichen
- **Versionskontrolle**: Verwenden Sie aussagekräftige Commit-Meldungen beim Aktualisieren von Fragmenten, um Änderungen im Laufe der Zeit zu verfolgen
- **Abhängigkeiten überwachen**: Verfolgen Sie, welche Formulare die einzelnen Fragmente zur Bewertung der Auswirkungen von Aktualisierungen verwenden

>[!TIP]
>
>Fragmentstile, Skripte und Ausdrücke werden bei der Einbettung beibehalten. Daher ist bei der Gestaltung diese Vererbung zu berücksichtigen.

## Zusammenfassung

Sie haben gelernt, wie Sie Formularfragmente in Edge Delivery Services nutzen können, um die Entwicklungseffizienz zu verbessern und die Konsistenz zwischen den Formularen Ihres Unternehmens zu gewährleisten.

**Wichtigste Ergebnisse:**

- **Verständnis**: Ermitteln Sie den geschäftlichen Nutzen und die technischen Möglichkeiten von Formularfragmenten
- **Erstellung**: Erstellen wiederverwendbarer Formularfragmente mit dem universellen Editor mit ordnungsgemäßer Konfiguration
- **Integration**: Es wurden Fragmente zu Formularen mit korrekter Referenzeinrichtung und Eigenschaftskonfiguration hinzugefügt.
- **Management**: Durchsuchte Vorgänge des Fragmentlebenszyklus und Wartungs-Workflows

**Nächste Schritte:**

- Erstellen Sie eine Bibliothek häufig verwendeter Fragmente für Ihre Organisation
- Festlegen von Benennungskonventionen und Governance-Richtlinien für die Fragmentverwendung
- Erkunden Sie die erweiterte Integration mit [Formulardatenmodellen](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) für dynamische datengesteuerte Fragmente
- Implementieren von fragmentbasierten Formularvorlagen für konsistente Benutzererlebnisse

Ihre Formulare profitieren jetzt von einer modularen, verwaltbaren Architektur, die effizient über Projekte skaliert werden kann, während gleichzeitig konsistente Benutzererlebnisse sichergestellt werden.

