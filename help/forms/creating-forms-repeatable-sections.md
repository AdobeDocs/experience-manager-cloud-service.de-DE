---
title: Erstellen von Formularen mit wiederholbaren Abschnitten
seo-title: Creating forms with repeatable sections
description: Wiederholbare Abschnitte sind Bereiche, die dynamisch zu einem Formular hinzugefügt oder daraus entfernt werden können.
seo-description: Repeatable sections are panels that can be dynamically added or removed to a form.
uuid: c3fa2aa4-a6b4-458e-8534-138e075290b1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 01724ca0-6901-45e7-b045-f44814ed574e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 100%

---


# Erstellen von Formularen mit wiederholbaren Abschnitten {#creating-forms-with-repeatable-sections}

Wiederholbare Abschnitte sind Bereiche, die dynamisch zu einem Formular hinzugefügt oder daraus entfernt werden können.

Beispiel: Bei der Bewerbung auf eine Stelle gibt der Arbeitssuchende Details zur vorherigen Beschäftigung an, wie Firmenname, Rolle, Projekt und andere Informationen. Die Informationen aller Arbeitgeber erfordern unterschiedliche, aber ähnlich aussehende Abschnitte. In einem solchen Fall bietet das Beschäftigungsformular einen Arbeitgeberabschnitt sowie eine Option, um weitere dieser Abschnitte dynamisch hinzuzufügen. Diese Abschnitte, die dynamisch hinzugefügt werden, werden als wiederholbare Abschnitte bezeichnet.

Sie können wiederholbare Bereiche mit einer der folgenden Methoden erstellen:

## Verwenden des Instanzmanagers über Skripte  {#using-instance-manager-via-scripts-nbsp}

1. Wählen Sie im Bearbeitungsmodus einen Bereich und tippen Sie dann auf ![cmppr](assets/cmppr.png). Aktivieren Sie in der Randleiste unter „Eigenschaften“ **[!UICONTROL Bereich wiederholbar machen]**. Geben Sie Werte für die Felder **[!UICONTROL Maximum]** und **[!UICONTROL Minimum]** an.

   Das Feld „Maximum“ (Höchstanzahl) legt fest, wie oft ein Bereich maximal auf der Seite angezeigt werden kann. Sie können -1 im Feld „Maximum Count“ (Höchstanzahl) angeben, damit der Bereich beliebig oft angezeigt werden kann.

   Das Feld „Minimum“ (Mindestanzahl) gibt an, wie oft ein Bereich mindestens auf dem Formular angezeigt wird. Wenn Sie die Mindestanzahl auf null setzen, können Sie später alle Instanzen über Skripte entfernen, nachdem die Darstellung abgeschlossen ist.

   >[!NOTE]
   >
   >Um einen nicht wiederholbaren Bereich zu erstellen, setzen Sie die Werte der Felder „Maximum“ (Höchstanzahl) und „Minimum“ (Mindestanzahl) auf jeweils 1. Beim Akkordeon-Layout wird der Wert „-1“ im Feld „Maximum Count“ (Höchstanzahl) nicht unterstützt. Sie können eine hohe Zahl angeben, um einen fast unbegrenzten Wert zu erreichen.

1. Das übergeordnete Element des Bereichs, der wiederholt werden soll, muss Schalter zum Hinzufügen und Löschen enthalten, um Instanzen der wiederholbaren Bereiche zu verwalten. Führen Sie die folgenden Schritte aus, um Schaltflächen in das übergeordnete Element einzufügen und Skripte auf den Schaltflächen zu aktivieren:

   1. Ziehen Sie eine Schaltflächenkomponente per Drag-and-Drop aus der Randleiste in das übergeordnete Element des Bereichs. Wählen Sie die Komponente aus und tippen Sie auf ![edit-rules](assets/edit-rules.png). Die Regeln der Schaltfläche werden im Regeleditor geöffnet.
   1. Im Fenster des Regeleditors klicken Sie auf **Erstellen**.

      Wählen Sie in der Zeile „Formularobjekte“ und „Funktionen“ **Visual Editor.**

      1. Wählen Sie im Regelbereich unter „WENN“ den Status **Angeklickt**.
      1. Unter „DANN“:

         * Um eine Schaltfläche zum Hinzufügen eines Bereichs zu erstellen, wählen Sie **Instanz hinzufügen** und ziehen Sie den Bereich per Drag-and-Drop mit ![toggle-side-panel](assets/toggle-side-panel.png) oder wählen Sie ihn mithilfe von **Objekt ablegen oder hier auswählen** aus.
         * Um eine Schaltfläche zum Löschen eines Bereichs zu erstellen, wählen Sie **Instanz entfernen** und ziehen Sie den Bereich per Drag-and-Drop mit ![toggle-side-panel](assets/toggle-side-panel.png) oder wählen Sie ihn mithilfe von **Objekt ablegen oder hier auswählen** aus.

      Wählen Sie in der Zeile „Formularobjekte und Funktionen“ **Code-Editor** aus. Klicken Sie auf **Regeln bearbeiten** und in den Code-Bereich:

      * Um eine Schaltfläche zum Hinzufügen eines Bereichs zu erstellen, geben Sie `this.panel.instanceManager.addInstance()` an.
      * Um eine Schaltfläche zum Löschen eines Bereichs zu erstellen, geben Sie `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)` an.

      Klicken Sie auf **Fertig**.

      >[!NOTE]
      >
      >Wenn ein Feld zu einem wiederholbaren Bereich gehört, können Sie mithilfe des Namens in Ihren Skripten nicht direkt darauf zugreifen. Um auf das Feld zuzugreifen, müssen Sie die wiederholbare Instanz, zu der das Feld gehört, unter Verwendung der `instances`-API in `InstanceManager` angeben. Die Syntax für die Verwendung der `instances`-API in `InstanceManager` lautet:
      >
      >
      >`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
      >
      >
      >Sie erstellen beispielsweise ein adaptives Formular mit einen wiederholbaren Bereich mit einem Textfeld. Wenn Sie das Formular mit drei wiederholbaren Textfeldern vorausfüllen, benötigen Sie die nachfolgende xml:
      >
      >
      >`<panel1><textbox1>AA1</panel1></textbox1>`
      >
      >
      >`<panel1><textbox1>AA2</panel1></textbox1>`
      >
      >
      >`<panel1><textbox1>AA3</panel1></textbox1>`
      >
      >
      >Zum Lesen von AA1-Daten müssen Sie Folgendes angeben:
      >
      >
      >`Panel1.instanceManager.instances[0].textbox.value`
      >
      >
      >Zum Lesen von AA2-Daten müssen Sie Folgendes angeben:
      >
      >
      >`Panel1.instanceManager.instances[1].textbox.value`
      >
      >
      >Weitere Informationen finden Sie unter: Klasse: InstanceManager#instances in der [AEM Forms Java API-Referenz](https://adobe.com/go/learn_aemforms_documentation_63_de).

      >[!NOTE]
      >
      >Wenn alle Instanzen eines Bereichs aus einem adaptiven Formular entfernt werden, nutzen Sie zum Hinzufügen einer Instanz des entfernten Bereichs die _panelName-Syntax, um den Instanzmanager des Bereichs zu erfassen, und verwenden Sie die addInstance-API des Instanzmanagers, um die gelöschte Instanz hinzuzufügen. Beispiel: _panelName.addInstance(). Dies fügt eine Instanz der entfernten Bereichs hinzu.



## Verwenden des Akkordeon-Layouts für den übergeordneten Bereich  {#using-the-accordion-layout-for-the-parent-panel-nbsp}

Ein Bereich weist verschiedene Layout-Optionen auf. Die Option zum Layout für das Akkordeon-Design bietet standardmäßig Unterstützung für wiederholbare Bereiche. Führen Sie die folgenden Schritte aus, um einen wiederholbaren Bereich mit der Option zum Layout für das Akkordeon-Design zu erstellen:

1. Klicken Sie im übergeordneten Element des zu wiederholenden Bereichs auf ![cmppr](assets/cmppr.png). Sie können die Eigenschaften in der Randleiste anzeigen. Wählen Sie in der Dropdown-Liste **Layout** die Option **Akkordeon**.
1. Tippen Sie in einem Bereich, der wiederholt werden soll, auf ![cmppr](assets/cmppr.png). Sie können die Eigenschaften des Bereichs in der Randleiste anzeigen. Aktivieren Sie die Registerkarte **Bereich wiederholbar machen** und geben Sie den Wert für die Felder **Maximum** und **Minimum** ein.

   Jetzt können Sie die Schaltflächen Plus (+) und Löschen (![delete-panel](assets/delete-panel.png)) verwenden, um Bereiche hinzuzufügen und zu entfernen.

## Verwenden von wiederholten Teilformularen aus der Formularvorlage (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Wiederholbare Teilformulare ähneln den wiederholbaren Bereichen in adaptiven Formularen. Führen Sie in [!DNL AEM Forms] Designer die folgenden Schritte aus, um ein sich wiederholendes Teilformular zu erstellen:

1. Wählen Sie das übergeordnete Teilformular des zu wiederholenden Teilformulars in der Palette „Hierarchie“ aus.
1. Klicken Sie in der Palette „Objekt“ auf die Registerkarte „Teilformular“ und wählen Sie in der Liste „Inhalt“ die Option „Textfluss“ aus.
1. Wählen Sie das zu wiederholende Teilformular aus.
1. Klicken Sie in der Palette „Objekt“ auf die Registerkarte „Teilformular“ und wählen Sie in der Liste „Inhalt“ die Option „Position“ oder „Textfluss“ aus.
1. Klicken Sie auf die Registerkarte „Bindung“ und wählen Sie die Option „Teilformular wiederh. f. jedes Datenelement“ aus.
1. Um die Mindestanzahl von Wiederholungen festzulegen, wählen Sie die Option „Min-Zähler“ aus und geben Sie im entsprechenden Feld eine Zahl ein. Wenn diese Option auf 0 gesetzt ist und zum Zeitpunkt der Datenzusammenführung keine Daten für die Objekte im Teilformular zur Verfügung stehen, wird das Teilformular bei der Wiedergabe des Formulars nicht platziert.
1. Um die maximale Anzahl von Wiederholungen festzulegen, wählen Sie die Option „Maximal“ aus und geben Sie im entsprechenden Feld eine Zahl ein. Wenn Sie im Feld „Maximal“ keinen Wert eingeben, ist die Anzahl von Teilformularwiederholungen unbeschränkt.
1. Wenn Sie unabhängig von der Datenmenge eine bestimmte Anzahl von Teilformularwiederholungen festlegen möchten, aktivieren Sie die Option „Anfangszahl“ und geben im zugehörigen Feld eine Zahl ein. Wenn Sie diese Option aktivieren und es stehen keine oder weniger als unter „Anfangszahl“ angegebene Daten zur Verfügung, werden leere Instanzen des Teilformulars in das Formular eingefügt.
1. Fügen Sie zwei Schaltflächen im übergeordneten Teilformular hinzu: eine für das Hinzufügen von Instanzen und eine andere für das Löschen von Instanzen des wiederholbaren Teilformulars. Ausführliche Anweisungen finden Sie unter [Erstellen einer Aktion](https://help.adobe.com/de_DE/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. Jetzt verknüpfen Sie die Formularvorlage mit dem adaptiven Formular. Ausführliche Anweisungen finden Sie unter [Erstellen eines adaptiven Formulars basierend auf einer Vorlage](creating-adaptive-form.md#create-an-adaptive-form-based-on-a-template).
1. Verwenden Sie die in Schritt 9 erstellten Schaltflächen, um Teilformulare hinzuzufügen und zu entfernen.

Die angehängte ZIP-Datei enthält ein Beispiel für ein wiederholbares Teilformular.

[Datei laden](assets/samplerepeatablesubform.zip)

## Verwenden der Wiederholungseinstellungen eines XML-Schemas (XSD) {#using-repeat-settings-of-an-xml-schema-xsd-br}

Sie können wiederholbare Bereiche aus einem XML-Schema mit den Eigenschaften „minOccurs“ und „maxOccurs“ eines beliebigen Elements eines komplexen Typs erstellen. Ausführliche Informationen zum XML-Schema finden Sie unter [Erstellen adaptiver Formulare mit XML-Schema als Formularmodell](adaptive-form-xml-schema-form-model.md).

Im folgenden Code verwendet der Bereich `SampleType` die Eigenschaften „minOccurs“ und „maxOccurs“.

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>

        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartDate" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails"
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```

>[!NOTE]
>
>Bei einem anderen als dem Akkordeon-Layout verwenden Sie Schaltflächenkomponenten für adaptive Formulare, um Instanzen hinzuzufügen und zu entfernen.
