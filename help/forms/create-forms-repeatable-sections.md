---
title: So erstellen Sie wiederholbare Bedienfelder in den Kernkomponenten des adaptiven Formulars
description: Erfahren Sie, wie Sie wiederholbare Abschnitte oder Felder in einem adaptiven Formular erstellen.
role: Architect, Developer, Admin, User
feature: Adaptive Forms, Core Components
exl-id: 02521bf3-83c1-40a0-8fe6-23af240727e9
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 99%

---

# Erstellen von Formularen mit wiederholbaren Abschnitten (Kernkomponenten) {#repeat-panel}


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-forms-repeatable-sections.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Ein wiederholbarer Abschnitt bezieht sich auf einen Teil eines Formulars, der mehrfach dupliziert oder wiederholt werden kann, um Informationen für mehrere Instanzen der gleichen Daten zu erfassen.

Dies könnte beispielsweise ein Formular sein, mit dem Informationen über die Arbeitserfahrung einer Person erfasst werden. Sie könnten einen wiederholbaren Abschnitt zum Erfassen der Details jeder vorherigen Beschäftigung haben. Der wiederholbare Abschnitt enthält normalerweise Felder wie Unternehmensname, Stellenbezeichnung, Beschäftigungsdauer und Arbeitsverantwortlichkeiten. Die Benutzerin bzw. der Benutzer kann mehrere Instanzen des wiederholbaren Abschnitts hinzufügen, um Informationen zu den einzelnen Beschäftigungen einzugeben, die sie bzw. er in der Vergangenheit hatte.

![Wiederholbarkeit](/help/forms/assets/repeatable-adaptive-form-example.gif)

Am Ende dieses Artikels werden Sie Folgendes gelernt haben:

* Erstellen eines wiederholbaren Abschnitts in einem adaptiven Formular
* Festlegen der Mindest- oder Höchstanzahl von Wiederholungen für adaptive Formularkomponenten
* Verwenden des Regeleditors, um Hinzufügungs- oder Löschaktionen für wiederholbare Abschnitte zu konfigurieren

Sie können die Komponenten [Bedienfeld](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html?lang=de), [Horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html?lang=de), [Vertikale Registerkarten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) oder [Assistent](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) verwenden, um Abschnitte eines adaptiven Formulars wiederholbar zu machen. Sie können untergeordnete Komponenten zu diesen Komponenten hinzufügen, um wiederholbare Abschnitte in einem Formular zu erstellen.


Die Beispiele in diesem Dokument basieren auf der [Panel](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel)-Komponente. Sie können die gleichen Schritte ausführen, um die Komponenten [Bedienfeld](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html?lang=de), [horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html?lang=de), [Vertikale Registerkarten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) oder [Assistent](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) wiederholbar zu machen.

## Hinzufügen oder Löschen von wiederholbaren Abschnitten in einem Formular {#add-or-delete-repeatable-section-in-panel-container}

Um ein Panel im Formular zu wiederholen oder wiederholbare Panels zu entfernen, verwendet eine Formularautorin bzw. ein -autor eine Schaltflächenkomponente, um eine Instanz des Panels hinzuzufügen oder zu entfernen. So fügen Sie wiederholbare Abschnitte (Panels) in einem Formular hinzu oder löschen sie:

* [Wiederholbarmachen eines Panel-Containers](#make-panel-container-repeatable)
* [Hinzufügen eines wiederholbaren Abschnitts](#add-repeatable-section-using-instance-manager-via-scripts)
* [Löschen von wiederholbaren Abschnitten](#delete-repeatable-section-using-instance-manager-via-scripts)

### Wiederholbarmachen des Panel-Containers {#make-panel-container-repeatable}

![Registerkarte „Barrierefreiheit“](/help/forms/assets/repeat-panel.png)

Um ein Panel wiederholbar zu machen, führen Sie die folgenden Schritte aus:

1. Wählen Sie einen Panel-Container aus und wählen Sie dann ![cmppr](/help/forms/assets/cmppr.png).
1. Klicken Sie auf **Panel wiederholen** und schalten Sie den Umschalter auf **Panel wiederholbar machen** um.
1. Legen Sie die **minimalen Wiederholungen** wie für die Mindestanzahl an wiederholbaren Abschnitten erforderlich fest. Sie können **Mindestwiederholungen** für nicht zu wiederholende Panels auf null setzen oder die wiederholten Panels entfernen. Standardmäßig ist der minimale Wert der Wiederholungen null.
1. Legen Sie die **maximalen Wiederholungen** auf die erforderliche Anzahl von Wiederholungen fest. Der Wert ist standardmäßig unbegrenzt.

   >[!NOTE]
   >
   > 
   > * Der Mindestwiederholungswert kann nicht -ve sein.
   > * Um einen nicht wiederholbaren Bereich zu erstellen, setzen Sie die Werte der Felder „Maximum“ (Höchstanzahl) und „Minimum“ (Mindestanzahl) auf jeweils 1.

### Wiederholbaren Abschnitt mithilfe des Instanz-Managers hinzufügen (über Skripte) {#add-repeatable-section-using-instance-manager-via-scripts}

Das übergeordnete Element des Panels, das wiederholt werden soll, muss Schaltflächen zum Hinzufügen enthalten, um eine wiederholbare Instanz des Panels zu verwalten. Führen Sie die folgenden Schritte aus, um Schaltflächen in das übergeordnete Element einzufügen und Skripte auf den Schaltflächen zu aktivieren:

1. Fügen Sie eine **Schaltflächenkomponente** zum übergeordneten Element des Panels hinzu. Im Beispielvideo unten wird eine Schaltflächenkomponente mit dem Bezeichnungsnamen **Hinzufügen** und Feldnamen **AddPanel** verwendet. Wählen Sie die Komponente aus und wählen Sie dann ![edit-rules](/help/forms/assets/edit-rules.png). Die Regeln der Schaltflächenkomponente werden im Regeleditor geöffnet.
1. Klicken Sie im Fenster des Regeleditors auf **Erstellen**.

   Wählen Sie in der Zeile „Formularobjekte“ und „Funktionen“ **Visual Editor.**

   1. Wählen Sie im Regelbereich unter „WENN“ den Status **Angeklickt**.
   1. Unter „DANN“, wählen Sie **Instanz hinzufügen** aus und ziehen Sie den Bereich per Drag-and-Drop mit ![toggle-side-panel](/help/forms/assets/toggle-side-panel.png) oder wählen Sie ihn mithilfe von **Objekt ablegen oder hier auswählen** aus.

   Wählen Sie in der Zeile „Formularobjekte und Funktionen“ **Code-Editor** aus. Klicken Sie auf **Regeln bearbeiten** und in den Code-Bereich:

   * Um eine Schaltfläche zum Hinzufügen eines Bereichs zu erstellen, geben Sie `this.panel.instanceManager.addInstance()` an.

   Klicken Sie auf **Fertig**.

>[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)


### Löschen wiederholbarer Abschnitte mithilfe des Instanz-Managers (über Skripte) {#delete-repeatable-section-using-instance-manager-via-scripts}

Das übergeordnete Element des Panels sollte Schaltflächen zum Hinzufügen und Löschen enthalten, um Instanzen der wiederholbaren Panels zu löschen. Führen Sie die folgenden Schritte aus, um Schaltflächen in das übergeordnete Element einzufügen und Skripte auf den Schaltflächen zum Löschen der wiederholbaren Panels zu aktivieren:

1. Fügen Sie eine **Schaltflächenkomponente** zum übergeordneten Element des Panels hinzu. Im Video unten wird eine Schaltflächenkomponente mit dem Bezeichnungsnamen **delete** und dem Feldnamen **DeletePanel** verwendet. Wählen Sie die Komponente aus und wählen Sie dann ![edit-rules](/help/forms/assets/edit-rules.png). Die Regeln der Schaltflächenkomponente werden im Regeleditor geöffnet.
1. Klicken Sie im Fenster des Regeleditors auf **Erstellen**.

   Wählen Sie in der Zeile „Formularobjekte“ und „Funktionen“ **Visual Editor.**

   1. Wählen Sie im Regelbereich unter „WENN“ **DeletePanel**, den Status **Angeklickt** aus.
   1. Wählen Sie unter „DANN“ **Instanz entfernen** aus und ziehen Sie den Bereich per Drag-and-Drop mit ![toggle-side-panel](/help/forms/assets/toggle-side-panel.png) oder wählen Sie ihn mithilfe von **Objekt ablegen oder hier auswählen** aus.

   Wählen Sie in der Zeile „Formularobjekte und Funktionen“ **Code-Editor** aus. Klicken Sie auf **Regeln bearbeiten** und in den Code-Bereich:

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
>Angenommen, Sie erstellen ein adaptives Formular mit einem wiederholbaren Bereich, der ein Textfeld enthält. Wenn Sie das Formular mit drei wiederholbaren Textfeldern vorausfüllen, benötigen Sie die nachfolgende xml:
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

>[!NOTE]
>
> Wenn alle Instanzen eines Bereichs aus einem adaptiven Formular entfernt wurden, können Sie eine Instanz des entfernten Bereichs mithilfe der Syntax _panelName erfassen, um den Instanz-Manager des Bereichs zu erfassen, und die gelöschte Instanz mit der addInstance-API des Instanz-Managers hinzufügen. Beispiel: &#39;_panelName.addInstance()&#39;. Dies fügt eine Instanz der entfernten Bereichs hinzu.

## Verwenden von wiederholten Teilformularen aus der Formularvorlage (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Wiederholbare Teilformulare ähneln den wiederholbaren Bedienfeldern in adaptiven Formularen. Führen Sie in AEM Forms Designer die folgenden Schritte aus, um ein sich wiederholendes Teilformular zu erstellen:

1. Wählen Sie das übergeordnete Teilformular des zu wiederholenden Teilformulars in der Palette „Hierarchie“ aus.
1. Klicken Sie in der Palette „Objekt“ auf die Registerkarte „Teilformular“ und wählen Sie in der Liste „Inhalt“ die Option „Textfluss“ aus.
1. Wählen Sie das zu wiederholende Teilformular aus.
1. Klicken Sie in der Palette „Objekt“ auf die Registerkarte „Teilformular“ und wählen Sie in der Liste „Inhalt“ die Option „Position“ oder „Textfluss“ aus.
1. Klicken Sie auf die Registerkarte „Bindung“ und wählen Sie die Option „Teilformular für jedes Datenelement wiederholen“ aus.
1. Um die Mindestanzahl von Wiederholungen festzulegen, wählen Sie die Option für die Mindestanzahl aus und geben Sie im entsprechenden Feld eine Zahl ein. Wenn diese Option auf den Wert „0“ gesetzt ist und zum Zeitpunkt der Datenzusammenführung keine Daten für die Objekte im Teilformular zur Verfügung stehen, wird das Teilformular beim Rendern des Formulars nicht platziert.
1. Um die maximale Anzahl von Teilformularwiederholungen festzulegen, wählen Sie „Max.“ aus und geben Sie im entsprechenden Feld eine Zahl ein. Wenn Sie im Feld „Max.“ keinen Wert eingeben, ist die Anzahl von Teilformularwiederholungen unbeschränkt.
1. Wenn Sie unabhängig von der Datenmenge eine bestimmte Anzahl an Teilformularwiederholungen festlegen möchten, wählen Sie „Anfangszahl“ aus und geben Sie im entsprechenden Feld eine Zahl ein. Wenn Sie diese Option aktivieren und keine oder weniger Daten zur Verfügung stehen als unter „Anfangszahl“ angegeben, werden leere Instanzen des Teilformulars in das Formular eingefügt.
1. Fügen Sie im übergeordneten Teilformular zwei Schaltflächen hinzu: eine zum Hinzufügen der Instanz und eine andere zum Löschen der Instanz des wiederholbaren Teilformulars. Ausführliche Anweisungen finden Sie unter [Erstellen einer Aktion](https://help.adobe.com/de_DE/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. Verknüpfen Sie nun die Formularvorlage mit dem adaptiven Formular. Ausführliche Anweisungen finden Sie unter [Erstellen eines adaptiven Formulars basierend auf einer Vorlage](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=de#create-an-adaptive-form-based-on-an-xfa-form-template).
1. Verwenden Sie die in Schritt 9 erstellten Schaltflächen, um Teilformulare hinzuzufügen und zu entfernen.

Die angehängte ZIP-Datei enthält ein Beispiel für ein wiederholbares Teilformular.

[Datei abrufen](/help/forms/assets/samplerepeatablesubform.zip)

## Verwenden der Wiederholungseinstellungen eines XML-Schemas (XSD) {#using-repeat-settings-of-an-xml-schema-xsd-br}

Sie können wiederholbare Bereiche aus einem XML-Schema mit den Eigenschaften „minOccurs“ und „maxOccurs“ eines beliebigen Elements eines komplexen Typs erstellen. Ausführliche Informationen zum XML-Schema finden Sie unter [Erstellen adaptiver Formulare mithilfe eines XML-Schemas als Formularmodell](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-xml-schema-form-model.html?lang=de).

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


## Siehe auch {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Create an Adaptive Form](creating-adaptive-form-core-components.md)
>* [Create style or themes for your forms](using-themes-in-core-components.md)
>* [Add dynamic behavior to forms using the rule editor](rule-editor.md)
>* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/features/console-layout.md)

-->