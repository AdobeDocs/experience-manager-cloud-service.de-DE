---
title: Erstellen wiederholbarer Bereiche in den Kernkomponenten des adaptiven Formulars
description: Erfahren Sie, wie Sie wiederholbare Abschnitte oder Felder in einem adaptiven Formular erstellen.
role: Architect, Developer, Admin, User
exl-id: 02521bf3-83c1-40a0-8fe6-23af240727e9
source-git-commit: defeee2fee42c6274c71438d6f9fde6e49a05081
workflow-type: tm+mt
source-wordcount: '1390'
ht-degree: 26%

---

# Erstellen von Formularen mit wiederholbaren Abschnitten (Kernkomponenten) {#repeat-panel}


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-forms-repeatable-sections.html?lang=en) |
| AEM as a Cloud Service | Dieser Artikel |

Ein wiederholbarer Abschnitt bezieht sich auf einen Teil eines Formulars, der mehrmals dupliziert oder wiederholt werden kann, um Informationen für mehrere Instanzen derselben Daten zu erfassen.

Betrachten Sie beispielsweise ein Formular, mit dem Informationen über die Arbeitserfahrung einer Person erfasst werden. Möglicherweise verfügen Sie über einen wiederholbaren Abschnitt zum Erfassen der Details jedes vorherigen Auftrags. Der wiederholbare Abschnitt enthält normalerweise Felder wie Unternehmensname, Berufsbezeichnung, Datum der Beschäftigung und Verantwortlichkeiten für den Auftrag. Der Benutzer kann mehrere Instanzen des wiederholbaren Abschnitts hinzufügen, um Informationen zu den einzelnen Aufträgen einzugeben, die er gespeichert hat.

![Wiederholbarkeit](/help/forms/assets/repeatable-adaptive-form-example.gif)

Am Ende dieses Artikels lernen Sie Folgendes:

* Erstellen eines wiederholbaren Abschnitts in einem adaptiven Formular
* Mindest- oder Höchstanzahl von Wiederholungen für adaptive Formularkomponenten festlegen
* Verwenden Sie den Regeleditor, um Hinzufügen- oder Löschaktionen für wiederholbare Abschnitte zu konfigurieren

Sie können die [Bedienfeld](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html)oder [Assistent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) Komponenten, um Abschnitte eines adaptiven Formulars wiederholbar zu machen. Sie können untergeordnete Komponenten zum Bedienfeld, Akkordeon, horizontalen Registerkarten oder Assistentenkomponenten hinzufügen, um wiederholbare Abschnitte in einem Formular zu erstellen.


Die Beispiele in diesem Dokument basieren auf dem [Bedienfeld](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html) -Komponente. Sie können die gleichen Schritte ausführen, um die [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html), und [Assistent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) wiederholbare Komponenten.

## Hinzufügen oder Löschen wiederholbarer Abschnitte in einem Formular {#add-or-delete-repeatable-section-in-panel-container}

Um ein Bedienfeld im Formular zu wiederholen oder wiederholbare Bedienfelder zu entfernen, verwendet ein Formularautor eine Schaltflächenkomponente, um eine Instanz des Bedienfelds hinzuzufügen oder zu entfernen. So fügen Sie wiederholbare Abschnitte (Bereiche) in einem Formular hinzu oder löschen sie:

* [Bereichscontainer wiederholbar machen](#make-panel-container-repeatable)
* [Wiederholbaren Abschnitt hinzufügen](#add-repeatable-section-using-instance-manager-via-scripts)
* [Wiederholbare Abschnitte löschen](#delete-repeatable-section-using-instance-manager-via-scripts)

### Bereichscontainer wiederholbar machen {#make-panel-container-repeatable}

![Registerkarte „Barrierefreiheit“](/help/forms/assets/repeat-panel.png)

Um ein Bedienfeld wiederholbar zu machen, führen Sie die folgenden Schritte aus:
1. Wählen Sie einen Bereichscontainer aus und tippen Sie auf ![cmppr](/help/forms/assets/cmppr.png).
1. Klicken Sie auf **Wiederholungsbereich** und schalten Sie den Umschalter auf **Bedienfeld wiederholbar machen**.
1. Satz **minimale Wiederholungen** wie für wiederholbare Mindestabschnitte erforderlich, können Sie **minimale Wiederholungen** auf null setzen, um Bereiche nicht abzurufen oder die wiederholten Bereiche zu entfernen. Standardmäßig ist der Wert der minimalen Wiederholung null.
1. Satz **maximale Wiederholungen** um die erforderliche Bedienfeldanzahl zu wiederholen, ist der Wert standardmäßig unbegrenzt.

   >[!NOTE]
   >
   > 
   > * Die Mindestwiederholung kann nicht -ve sein.
   > * Um einen nicht wiederholbaren Bereich zu erstellen, setzen Sie den Wert des Felds &quot;maximum&quot;und &quot;minimum&quot;auf &quot;one&quot;.

### Wiederholbarer Abschnitt mithilfe des Instanzmanagers hinzufügen (über Skripte) {#add-repeatable-section-using-instance-manager-via-scripts}

Das übergeordnete Element des Bereichs, der wiederholt werden soll, sollte eine Schaltfläche zum Hinzufügen enthalten, um die Wiederholungsinstanz des Bedienfelds zu verwalten. Führen Sie die folgenden Schritte aus, um Schaltflächen in das übergeordnete Element einzufügen und Skripte auf den Schaltflächen zu aktivieren:

1. Hinzufügen einer **Schaltflächenkomponente** zum übergeordneten Element des Bedienfelds. Im folgenden Beispiel-Video wird eine Schaltflächenkomponente mit dem Beschriftungsnamen **Hinzufügen** und Feldname **AddPanel** verwendet wird. Wählen Sie die Komponente aus und tippen Sie auf ![edit-rules](/help/forms/assets/edit-rules.png). Die Regeln der Schaltflächenkomponente werden im Regeleditor geöffnet.
1. Klicken Sie im Fenster des Regeleditors auf **Erstellen**.

   Wählen Sie in der Zeile „Formularobjekte“ und „Funktionen“ **Visual Editor.**

   1. Wählen Sie im Regelbereich unter „WENN“ den Status **Angeklickt**.
   1. Wählen Sie unter THEN die Option **Instanz hinzufügen** und ziehen Sie das Bedienfeld per Drag &amp; Drop ![Umschalten des Seitenbereichs](/help/forms/assets/toggle-side-panel.png) oder wählen Sie sie mithilfe der **Legen Sie ein Objekt ab oder wählen Sie hier aus.**

   Auswählen **Code-Editor** in der Zeile &quot;Formularobjekte und Funktionen&quot;. Klicken Sie auf **Regeln bearbeiten** und in den Code-Bereich:

   * Um eine Schaltfläche zum Hinzufügen eines Bereichs zu erstellen, geben Sie `this.panel.instanceManager.addInstance()` an.

   Klicken Sie auf **Fertig**.

>[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)


### Löschen wiederholbarer Abschnitte mithilfe des Instanzmanagers (über Skripte) {#delete-repeatable-section-using-instance-manager-via-scripts}

Das übergeordnete Element des Bedienfelds sollte eine Schaltfläche zum Löschen enthalten, um die Instanz der wiederholbaren Bedienfelder zu löschen. Führen Sie die folgenden Schritte aus, um Schaltflächen zum übergeordneten Element einzufügen und Skripten auf den Schaltflächen zu aktivieren, um wiederholbare Bereiche zu löschen:

1. Hinzufügen einer **Schaltflächenkomponente** zum übergeordneten Element des Bedienfelds, im Video unten eine Schaltflächenkomponente mit dem Beschriftungsnamen **delete** und Feldname **DeletePanel** verwendet. Wählen Sie die Komponente aus und tippen Sie auf ![edit-rules](/help/forms/assets/edit-rules.png). Die Regeln der Schaltflächenkomponente werden im Regeleditor geöffnet.
1. Klicken Sie im Fenster des Regeleditors auf **Erstellen**.

   Wählen Sie in der Zeile „Formularobjekte“ und „Funktionen“ **Visual Editor.**

   1. Im Regelbereich unter WENN **DeletePanel**, Status auswählen **angeklickt wird**.
   1. Wählen Sie unter THEN die Option **Instanz löschen** und ziehen Sie das Bedienfeld per Drag &amp; Drop ![Umschalten des Seitenbereichs](/help/forms/assets/toggle-side-panel.png) oder wählen Sie sie mithilfe der **Legen Sie ein Objekt ab oder wählen Sie hier aus.**

   Auswählen **Code-Editor** in der Zeile &quot;Formularobjekte und Funktionen&quot;. Klicken Sie auf **Regeln bearbeiten** und in den Code-Bereich:

   * Um eine Schaltfläche zum Löschen eines Bereichs zu erstellen, geben Sie `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)` an.

   Klicken Sie auf **Fertig**.
>[!VIDEO](https://video.tv.adobe.com/v/3421620/adaptive-forms-repeatable-sections)

>[!NOTE]
>
>Wenn ein Feld zu einem wiederholbaren Bereich gehört, können Sie mithilfe des Namens in Ihren Skripten nicht direkt darauf zugreifen. Um auf das Feld zuzugreifen, müssen Sie die wiederholbare Instanz, zu der das Feld gehört, unter Verwendung der `instances`-API in `InstanceManager` angeben. Die Syntax für die Verwendung der `instances`-API in `InstanceManager` lautet:
>
>
>`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
>
>
>Beispiel: Sie erstellen ein adaptives Formular mit einem wiederholbaren Bedienfeld mit einem Textfeld. Wenn Sie das Formular mit drei wiederholbaren Textfeldern vorausfüllen, benötigen Sie die nachfolgende xml:
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
>

<!-- 
>For more information, see: Class: InstanceManager#instances in [AEM Forms Java API reference](https://adobe.com/go/learn_aemforms_documentation_63).      
-->

>[!NOTE]
>
> Wenn alle Instanzen eines Bereichs aus einem adaptiven Formular entfernt werden, erfassen Sie zum Hinzufügen einer Instanz des entfernten Bereichs die _panelName-Syntax, um den Instanzmanager des Bereichs zu erfassen, und verwenden Sie die addInstance-API des Instanzmanagers, um die gelöschte Instanz hinzuzufügen. Beispiel: _panelName.addInstance(). Dies fügt eine Instanz der entfernten Bereichs hinzu.

<!--
![panel-repeatability-video](/help/adaptive-forms/assets/panel-repeatability-video.mp4)
-->

<!--

## Using the accordion layout for the parent panel &nbsp; {#using-the-accordion-layout-for-the-parent-panel-nbsp}

A panel has various layouts options. The Layout for accordian design option has out of the box support for repeatable panels. Perform the following steps to repeatable panel with Layout for accordian design option:

1. On the parent of panel to be repeated, tap ![cmppr](assets/cmppr.png). You can see the properties in the sidebar. In the **Layout** drop-down, select **Accordion**.
1. On a panel, which is to be repeated, tap ![cmppr](assets/cmppr.png). You can see the panel properties in the sidebar. Enable the **Make Panel Repeatable** tab, and specify value for the **Maximum** and **Minimum** fields.

   Now, you can use the plus (+) and delete ( ![delete-panel](assets/delete-panel.png)) buttons to add and remove the panels.

-->

## Verwenden von wiederholten Teilformularen aus der Formularvorlage (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Wiederholbare Teilformulare ähneln den wiederholbaren Bedienfeldern in adaptiven Formularen. Führen Sie in AEM Forms Designer die folgenden Schritte aus, um ein sich wiederholendes Teilformular zu erstellen:

1. Wählen Sie in der Palette &quot;Hierarchie&quot;das übergeordnete Teilformular des zu wiederholenden Teilformulars aus.
1. Klicken Sie in der Palette &quot;Objekt&quot;auf die Registerkarte &quot;Teilformular&quot;und wählen Sie in der Liste &quot;Inhalt&quot;die Option &quot;Textfluss&quot;aus.
1. Wählen Sie das zu wiederholende Teilformular aus.
1. Klicken Sie in der Palette &quot;Objekt&quot;auf die Registerkarte &quot;Teilformular&quot;und wählen Sie in der Liste &quot;Inhalt&quot;die Option &quot;Position&quot;oder &quot;Textfluss&quot;aus.
1. Klicken Sie auf die Registerkarte &quot;Bindung&quot;und wählen Sie &quot;Teilformular wiederholen für jedes Datenelement&quot;.
1. Um die Mindestanzahl von Wiederholungen festzulegen, wählen Sie &quot;Min-Zähler&quot;aus und geben Sie im entsprechenden Feld eine Zahl ein. Wenn diese Option auf 0 gesetzt ist und zum Zeitpunkt der Datenzusammenführung keine Daten für die Objekte im Teilformular bereitgestellt werden, wird das Teilformular bei der Wiedergabe des Formulars nicht platziert.
1. Um die maximale Anzahl von Teilformularwiederholungen festzulegen, wählen Sie &quot;Maximal&quot;aus und geben Sie im entsprechenden Feld eine Zahl ein. Wenn Sie im Feld &quot;Maximal&quot;keinen Wert angeben, ist die Anzahl der Teilformularwiederholungen unbegrenzt.
1. Wenn Sie unabhängig von der Datenmenge eine bestimmte Anzahl an Teilformularwiederholungen festlegen möchten, wählen Sie &quot;Anfangszahl&quot;und geben Sie im entsprechenden Feld eine Zahl ein. Wenn Sie diese Option auswählen und entweder keine Daten verfügbar sind oder weniger Dateneinträge als der angegebene Wert für &quot;Anfangszahl&quot;vorhanden sind, werden leere Instanzen des Teilformulars weiterhin im Formular platziert.
1. Fügen Sie im übergeordneten Teilformular zwei Schaltflächen hinzu: eine zum Hinzufügen der Instanz und eine andere zum Löschen der Instanz des wiederholbaren Teilformulars. Ausführliche Anweisungen finden Sie unter [Erstellen einer Aktion](https://help.adobe.com/de_DE/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. Verknüpfen Sie nun die Formularvorlage mit dem adaptiven Formular. Ausführliche Anweisungen finden Sie unter [Erstellen eines adaptiven Formulars basierend auf einer Vorlage](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=en#create-an-adaptive-form-based-on-an-xfa-form-template).
1. Verwenden Sie die in Schritt 9 erstellten Schaltflächen, um Teilformulare hinzuzufügen und zu entfernen.

Die angehängte ZIP-Datei enthält ein Beispiel für ein wiederholbares Teilformular.

[Datei laden](/help/forms/assets/samplerepeatablesubform.zip)

## Verwenden der Wiederholungseinstellungen eines XML-Schemas (XSD) {#using-repeat-settings-of-an-xml-schema-xsd-br}

Sie können wiederholbare Bereiche aus einem XML-Schema mit den Eigenschaften „minOccurs“ und „maxOccurs“ eines beliebigen Elements eines komplexen Typs erstellen. Ausführliche Informationen zum XML-Schema finden Sie unter [Erstellen adaptiver Formulare mit dem XML-Schema als Formularmodell](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-xml-schema-form-model.html).

Im folgenden Code verwendet der `SampleType`Bereich die Eigenschaften „minOccurs“ und „maxOccurs“.

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


## Verwandte Artikel

* [Erstellen eines adaptiven Formulars](creating-adaptive-form-core-components.md)
* [Erstellen von Stilen oder Designs für Ihre Formulare](using-themes-in-core-components.md)
* [Dynamisches Verhalten zu Formularen mithilfe des Regeleditors hinzufügen](rule-editor.md)
* [Festlegen des Layouts von Formularen für verschiedene Bildschirmgrößen und Gerätetypen](/help/sites-cloud/authoring/features/responsive-layout.md)
