---
title: Grundlegendes zum universellen Editor - Entwickler-Tutorial
description: Dieses Tutorial hilft Ihnen beim Einrichten und Ausführen der Benutzeroberfläche des universellen Editors. Es führt Sie durch das Verständnis der Benutzeroberfläche, um Ihre eigenen Edge Delivery Services-Formulare im universellen Editor zu erstellen.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: 0c6f024594e1b1fd98174914d2c0714dffecb241
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 1%

---

# Erkunden der Benutzeroberfläche des universellen Editors (WYSIWYG)

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) bietet eine einfache, visuelle und intuitive Benutzeroberfläche für What You See Is What You Get (WYSIWYG) für Adobe Edge Delivery Services (EDS) Forms. Es bietet eine moderne Benutzeroberfläche mit Drag-and-Drop-Funktionen für eine effiziente Formularerstellung.

![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Grundlegendes zur Benutzeroberfläche des universellen Editors

Wenn der Formularautor das Formular mit dem universellen Editor bearbeitet, öffnet die Konsole eine interaktive WYSIWYG-Schnittstelle, über die der Benutzer mit der Bearbeitung des Formulars beginnen kann.

>[!NOTE]
>
> Informationen zum Erstellen von Formularen mit dem universellen Editor finden Sie im Artikel [Erste Schritte mit Edge Delivery Services für AEM Forms mit dem universellen Editor (WYSIWYG)](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

Die Benutzeroberfläche des universellen Editors ist in vier Teile unterteilt:

* **[A: Experience Cloud-Kopfzeile](#experience-cloud-header)**
* **[B: Symbolleiste des universellen Editors](#universal-editor-toolbar)**
* **[C: Bedienfeld „Eigenschaften“](#properties-panel)**
* **[D: Editor](#editor)**

### Experience Cloud-Kopfzeile

Die Experience Cloud-Kopfzeile befindet sich oben in der Konsole. Er enthält Informationen zum aktuellen Speicherort in Experience Cloud. Darüber hinaus können Sie zu anderen Experience Cloud-Programmen navigieren.

![Experience Cloud-Kopfzeile des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)


Sehen wir uns die einzelnen Komponenten an.

* **Adobe Experience Cloud**

  Sie können auf den Link **Adobe Experience Cloud** links im Bildschirm klicken, um zum Stammverzeichnis der Experience Manager-Lösung zu navigieren und auf Tools wie Experience Manager Sites, Experience Manager Assets und Experience Manager Guides zuzugreifen.

  ![Adobe Experience Manager](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png){width=50%,height=50%}

* **Organisationsname**

  Der **Organisationsname** zeigt den Namen der IMS-Organisation an, bei der Sie derzeit angemeldet sind. Sie können zu einer anderen IMS-Organisation wechseln, wenn diese Zugriff auf andere Organisationen hat, indem Sie aus der Dropdown-Liste auswählen. Beispielsweise lautet der derzeit ausgewählte Name der IMS-Organisation `AEM Forms Internal01`.

  ![Organisation](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png){width=50%,height=50%}


* **Hilfe**

  Das Hilfesymbol bietet schnellen Zugriff auf Lern- und Support-Ressourcen. Der Formularautor bzw. die Formularautorin kann das Feedback auch dem Abschnitt **Hilfe** hinzufügen.
  ![Hilfe](/help/edge/docs/forms/universal-editor/assets/ue-help.png){width=50%,height=50%}


* **Benachrichtigungen**

  Im Abschnitt **Benachrichtigung** wird die Anzahl der aktuell zugewiesenen unvollständigen Benachrichtigungen, der Anfragen und der aktuellen Aufgaben in der IMS-Organisation angezeigt.

  ![Benachrichtigung](/help/edge/docs/forms/universal-editor/assets/ue-notification.png){width=50%,height=50%}


* **Lösungen**

  Sie können über den Link **Lösungen** zu anderen Experience Cloud-Lösungen wechseln.
  ![Lösungen](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png){width=50%,height=50%}


* **author**
Das Symbol stellt die Details des Formularautors zusammen mit dem Namen der IMS-Organisation dar, in der der Autor derzeit angemeldet ist.
  ![Autor](/help/edge/docs/forms/universal-editor/assets/ue-author.png){width=50%,height=50%}

### Symbolleiste des universellen Editors

Die Symbolleiste ermöglicht es Ihnen, zu anderen Formularen zu navigieren und sie zu bearbeiten. Außerdem können sie das Formular veröffentlichen oder die Veröffentlichung rückgängig machen, die Eigenschaften des Formulars bearbeiten und auf den Regeleditor zugreifen.
![Symbolleiste des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

Sehen wir uns die einzelnen Komponenten an.

* **Taste HOME**
Mit der Schaltfläche „Startseite“ können Sie zur Startseite des universellen Editors navigieren. Sie können auch direkt die URL des Formulars eingeben, das sie bearbeiten möchten, indem Sie den universellen Editor verwenden.
  ![Universal Editor Home](/help/edge/docs/forms/universal-editor/assets/ue-home.png)



* **Speicherortleiste**
Die **Speicherortleiste** zeigt die Adresse des Formulars an, das der Autor bearbeitet. Sie können auch eine andere Formular-URL eingeben, indem Sie auf die Adressleiste klicken. Die Tastenkombination zum Öffnen der Speicherortleiste lautet Key `l`.
  ![Speicherortleiste](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png){width=50%,height=50%}



* **Regeleditor**

  Der **Regeleditor** bietet eine intuitive visuelle Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sie können das dynamische Formularverhalten mit dem Regeleditor hinzufügen.

  ![Regeleditor](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > * Im universellen Editor ist die Erweiterung des Regeleditors nicht standardmäßig aktiviert. Um die Erweiterung des Regeleditors zu aktivieren, schreiben Sie uns unter [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) von Ihrer offiziellen E-Mail-ID.
  > * Informationen zum Erstellen von Regeln finden Sie im Artikel [Einführung in den Regeleditor beim WYSIWYG-Authoring](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

* **Formulareigenschaften bearbeiten**
Sie können die Formulareigenschaften, z. B. das Formulardatenmodell und das Veröffentlichungsdatum, bearbeiten, indem Sie auf die Option **Formulareigenschaften bearbeiten** klicken.
  ![Formulareigenschaften bearbeiten](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)



* **Authentifizierungs-Header-Einstellungen**
Mit **Einstellungen für den Authentifizierungs**Header kann der Autor einen benutzerdefinierten Authentifizierungs-Header für lokale Entwicklungszwecke festlegen.
  ![Authentifizierungs-Header](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png){width=50%,height=50%}



* **Responsiver Modus**
  **Responsiver Modus** können Sie festlegen, wie der universelle Editor das Formular rendert. Standardmäßig wird der Editor in einem Desktop-Layout geöffnet, bei dem Höhe und Breite automatisch vom Browser bestimmt werden. Alternativ können Sie ein Mobilgerät emulieren und überprüfen, wie das Formular auf Mobilgeräten angezeigt wird.

  ![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png){width=50%,height=50%}


* **Vorschaumodus**
Im Vorschaumodus wird das Formular im Editor genau so angezeigt, wie es veröffentlicht wurde. Dadurch kann der Autor durch Klicken auf Links und Schaltflächen im Formular navigieren. Sobald die Bearbeitung abgeschlossen ist, kann der Autor das Formular für Live-Benutzer veröffentlichen. Der Tastaturbefehl zum Umschalten zwischen Bearbeitungs- und Vorschaumodus ist `p`.
  ![Vorschau](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

* **Seite öffnen**
Die **Seite öffnen** Option öffnet das Formular auf einer neuen Registerkarte für die Vorschau. Der Tastaturbefehl zum Öffnen des Formulars im Vorschaumodus auf einer neuen Registerkarte ist `o`.
  ![Seite öffnen](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

* **Veröffentlichen**

  Sie können das Formular mithilfe der Schaltfläche **Veröffentlichen“ für Live-Benutzer**.
  ![Veröffentlichen](/help/edge/docs/forms/universal-editor/assets/ue-publish.png){width=50%,height=50%}

* **Auslassungspunkte**
Wenn der Autor auf die Option mit den Auslassungspunkten (…) klickt, wird die Option **Veröffentlichung**. Sie können die Veröffentlichung eines Formulars mit der Option „Veröffentlichung **&quot;**.
  ![Ellipse](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png){width=50%,height=50%}

### Bedienfeld „Eigenschaften“

Das **Eigenschaftenbedienfeld** befindet sich auf der rechten Seite des Editors. Es werden die Details der Komponente angezeigt, die in der Hierarchie des Formulars ausgewählt wurde. Dies ist die Standardstruktur, wenn keine Komponente ausgewählt ist.
![Bedienfeld „UE-Eigenschaften](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png){width=50%,height=50%}


Sehen wir uns die einzelnen Komponenten an.


* **Eigenschaftenmodus**
In **Eigenschaften** zeigt die Option die Eigenschaften der ausgewählten Komponente im Editor an. Das Bild zeigt beispielsweise die Eigenschaften der ausgewählten Zahleneingabekomponente an. Sie können die Eigenschaften der Komponente mit dieser Option ändern. Der Tastaturbefehl zum Öffnen der Eigenschaften der Komponente ist `d`.

  ![ue-properties](/help/edge/docs/forms/universal-editor/assets/ue-properties.png){width=50%,height=50%}


* **Inhaltsstruktur**
Mit **Option &quot;**&quot; wird die Hierarchie des Formulars angezeigt. Wenn der Autor auf ein Element in der Inhaltsstruktur klickt, wählt der Editor es aus und scrollt zu dieser Komponente. Die Tastenkombination zum Umschalten zwischen den Ansichten der Inhaltsstruktur lautet Key `f`.

  ![Inhaltsstruktur](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png){width=50%,height=50%}


* **Generieren von Varianten**
  **Varianten generieren** verwendet künstliche Intelligenz, um basierend auf bestimmten Eingabeaufforderungen verschiedene Versionen von Formularen zu erstellen. Diese Eingabeaufforderungen können entweder von Adobe bereitgestellt oder vom Formularautor erstellt und verwaltet werden.

  ![variation](/help/edge/docs/forms/universal-editor/assets/ue-variations.png){width=50%,height=50%}


  >[!NOTE]
  >
  > Anweisungen zur Verwendung von „Varianten für Formulare generieren“ finden Sie im Artikel [Varianten generieren](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/generative-ai/generate-variations) .

* **Experimentieren**:

  **Experimentieren** beziehen sich auf Techniken, mit denen verschiedene Varianten von Formularen und Layouts getestet werden, um das Benutzererlebnis und die Leistung zu optimieren.
  ![Experimentieren](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png){width=50%,height=50%}


* **Personalization**
Mit der Option **Personalization** werden die Einstellungen so konfiguriert, dass eine Verbindung zwischen den Formularen und Adobe Experience Platform (AEP) hergestellt wird, die Teil des Adobe-Ökosystems oder externer Anwendungen sind.
  ![Personalization](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png){width=50%,height=50%}


* **A/B-Tests**:
  **A/B-Tests** beziehen sich auf Techniken, mit denen verschiedene Varianten von Formularen und Layouts getestet werden, um das Benutzererlebnis und die Leistung zu optimieren.
  ![A/B-Tests](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png){width=50%,height=50%}



* **Aufgabenverwaltung**:
Die Funktion **Aufgabenverwaltung** ermöglicht es Ihnen, Workflows zu optimieren und die Zusammenarbeit zu verbessern, indem sie es Teams ermöglicht, Aufgaben im Zusammenhang mit der Anpassung und Optimierung von Formularen zu verwalten, zu verfolgen und auszuführen
  ![Aufgabenverwaltung](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png){width=50%,height=50%}

.
* **Inhaltsentwürfe**

  Mit **Option „Inhaltsentwürfe** können Sie Entwürfe für Rich-Text-Elemente erstellen. Entwürfe können mit vorhandenem Formulartext oder von Grund auf neu erstellt werden. Entwürfe können nach Bedarf bearbeitet oder gelöscht werden. Standardmäßig sind nur drei Entwürfe sichtbar. Wenn Sie jedoch auf **Alle anzeigen** klicken, wird der Rest angezeigt.

  ![Aufgabenverwaltung](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png){width=50%,height=50%}


* **Daten-Source**

  Mit **Option „Data Source** können Sie Datenquellen konfigurieren und beim Erstellen eines Formulardatenmodells (FDM) auswählen. Dadurch werden alle Datenmodellobjekte, Eigenschaften und Services aus den ausgewählten Datenquellen für die Verwendung im Formulardatenmodell verfügbar gemacht.
  ![Data Source](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png){width=50%,height=50%}

* **Hinzufügen**

  Die **Hinzufügen**-Option öffnet eine Dropdown-Liste von Komponenten, die zum ausgewählten Container hinzugefügt werden können. In einem Abschnitt für adaptive Formulare zeigt die Liste beispielsweise die verfügbaren Komponenten an, die einem Formular hinzugefügt werden können. Der Tastaturbefehl zum Öffnen der Liste der Komponenten ist `a`.
  ![Symbol hinzufügen](/help/edge/docs/forms/universal-editor/assets/ue-add.png){width=50%,height=50%}

* **Duplizieren**

  Mit **Option**Duplizieren“ wird eine Kopie der Komponente erstellt, die entweder in der Inhaltsstruktur oder im Editor ausgewählt wird.
  ![Symbol „Duplizieren](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png){width=50%,height=50%}


* **Löschen**
Die **Löschen**-Option löscht eine Komponente, die entweder in der Inhaltsstruktur oder im Editor ausgewählt ist.

  ![Löschen](/help/edge/docs/forms/universal-editor/assets/ue-delete.png){width=50%,height=50%}

### Editor

Mit dem Editor können Sie das Formular bearbeiten, und das in der Positionsleiste angegebene Formular wird im Bearbeitungsbereich gerendert. Wenn sich der Editor im Vorschaumodus befindet, können Sie mithilfe der verfügbaren Schaltflächen und Links durch das Formular navigieren.
![Editor](/help/edge/docs/forms/universal-editor/assets/ue-editor.png){width=50%,height=50%}

## Siehe auch

{{universal-editor-see-also}}
