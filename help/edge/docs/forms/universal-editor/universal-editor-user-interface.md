---
title: Grundlegendes zum universellen Editor – Entwickler-Tutorial
description: Dieses Tutorial hilft Ihnen, sich mit der Oberfläche des universellen Editors vertraut zu machen. Es erklärt Ihnen die Benutzeroberfläche, damit Sie Ihre eigenen Edge Delivery Services-Formulare im universellen Editor erstellen können.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: 744f505c8e97b6ca6947b685ddb1eba41b370cfa
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 96%

---

# Erkunden der Benutzeroberfläche des universellen Editors (WYSIWYG)

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) bietet eine einfache, visuelle und intuitive Benutzeroberfläche für What You See Is What You Get (WYSIWYG) für Adobe Edge Delivery Services Forms. Er verfügt über eine moderne Benutzeroberfläche mit Drag-and-Drop-Funktionalität zur effizienten Formularerstellung.

![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Grundlegendes zur Benutzeroberfläche des universellen Editors

Wenn bei der Formularerstellung das Formular mit dem universellen Editor bearbeitet wird, öffnet die Konsole eine interaktive WYSIWYG-Benutzeroberfläche, über die die Benutzenden mit der Bearbeitung des Formulars beginnen können.

>[!NOTE]
>
> Informationen zum Erstellen von Formularen mit dem universellen Editor finden Sie im Artikel [Erste Schritte mit Edge Delivery Services für AEM Forms mithilfe des universellen Editors (WYSIWYG)](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

Die Benutzeroberfläche des universellen Editors ist in vier Teile unterteilt:

* **[A: Kopfzeile von Experience Cloud](#experience-cloud-header)**
* **[B: Symbolleiste des universellen Editors](#universal-editor-toolbar)**
* **[C: Bedienfeld „Eigenschaften“](#properties-panel)**
* **[D: Editor](#editor)**

### Experience Cloud-Kopfzeile

Die Experience Cloud-Kopfzeile befindet sich oben in der Konsole. Sie enthält Informationen zur aktuellen Position in Experience Cloud. Sie ermöglicht darüber hinaus, dass Sie zu anderen Experience Cloud-Programmen navigieren können.

![Experience Cloud-Kopfzeile des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)


Sehen wir uns die einzelnen Komponenten an.

* **Adobe Experience Cloud**

  Sie können links auf dem Bildschirm auf den Link **Adobe Experience Cloud** klicken, um zum Stammverzeichnis der Experience Manager-Lösung zu navigieren und auf Tools wie Experience Manager Sites, Experience Manager Assets und Experience Manager Guides zuzugreifen.

  ![Adobe Experience Manager](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png){width=50%,height=50%}

* **Organisationsname**

  Der **Organisationsname** zeigt den Namen der IMS-Organisation an, bei der Sie derzeit angemeldet sind. Sie können zu einer anderen IMS-Organisation wechseln (falls diese Zugriff auf andere Organisationen bietet), indem Sie aus der Dropdown-Liste auswählen. Beispielsweise lautet der Name der derzeit ausgewählten IMS-Organisation `AEM Forms Internal01`.

  ![Organisation](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png){width=50%,height=50%}


* **Hilfe**

  Das Hilfesymbol bietet Schnellzugriff auf Lern- und Support-Ressourcen. Der Formularverfasser bzw. die Formularverfasserin kann das Feedback auch im Abschnitt **Hilfe** hinzufügen.
  ![Hilfe](/help/edge/docs/forms/universal-editor/assets/ue-help.png){width=50%,height=50%}


* **Benachrichtigungen**

  Im Abschnitt **Benachrichtigung** werden die Anzahl der aktuell zugewiesenen unvollständigen Benachrichtigungen sowie die Anfragen und die aktuellen Aufgaben in der IMS-Organisation angezeigt.

  ![Benachrichtigung](/help/edge/docs/forms/universal-editor/assets/ue-notification.png){width=50%,height=50%}


* **Lösungen**

  Sie können über den Link **Lösungen** zu anderen Experience Cloud-Lösungen wechseln.
  ![Lösungen](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png){width=50%,height=50%}


* **Autor**
Das Symbol stellt die Details des Formularverfassers bzw. der Formularverfasserin zusammen mit dem Namen der IMS-Organisation dar, in der er bzw. sie derzeit angemeldet ist.
  ![Autor](/help/edge/docs/forms/universal-editor/assets/ue-author.png){width=50%,height=50%}

### Symbolleiste des universellen Editors

Über die Symbolleiste können Sie zu anderen Formularen navigieren und sie bearbeiten. Außerdem können sie damit das Formular veröffentlichen oder die Veröffentlichung rückgängig machen, die Eigenschaften des Formulars bearbeiten und auf den Regeleditor zugreifen.
![Symbolleiste des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

Sehen wir uns die einzelnen Komponenten an.

* **Schaltfläche „Startseite“**
Mit der Schaltfläche „Startseite“ können Sie zur Startseite des universellen Editors navigieren. Sie können auch die URL des Formulars direkt eingeben, das sie mit dem universellen Editor bearbeiten möchten.
  ![Startseite des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-home.png)



* **Speicherortleiste**
Die **Speicherortleiste** zeigt die Adresse des Formulars an, das der Verfasser bzw. die Verfasserin gerade bearbeitet. Sie können auch eine andere Formular-URL eingeben, indem Sie auf die Speicherortleiste klicken. Der Tastaturbefehl zum Öffnen der Speicherortleiste lautet `l`.
  ![Speicherortleiste](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png){width=50%,height=50%}



* **Regeleditor**

  Der **Regeleditor** bietet eine intuitive visuelle Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sie können mit dem Regeleditor ein dynamisches Formularverhalten hinzufügen.

  ![Regeleditor](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > * Im universellen Editor ist die Regeleditor-Erweiterung nicht standardmäßig aktiviert. Um die Regeleditor-Erweiterung zu aktivieren, schreiben Sie uns über Ihre offizielle E-Mail-ID an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com).
  > * Informationen zum Erstellen von Regeln finden Sie im Artikel [Einführung in den Regeleditor beim WYSIWYG-Authoring](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

* **Formulareigenschaften bearbeiten**
Sie können die Formulareigenschaften, z. B. das Formulardatenmodell und das Veröffentlichungsdatum, bearbeiten, indem Sie auf die Option **Formulareigenschaften bearbeiten** klicken.
  ![Formulareigenschaften bearbeiten](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)



* **Authentifizierungs-Header-Einstellungen**
Mit den **Authentifizierungs-Header-Einstellungen** kann bei der Erstellung ein benutzerdefinierter Authentifizierungs-Header für lokale Entwicklungszwecke festgelegt werden.
  ![Authentifizierungs-Header](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png){width=50%,height=50%}



* **Responsiver Modus**
  Mit der Option **Responsiver Modus** können Sie festlegen, wie der universelle Editor das Formular rendert. Standardmäßig wird der Editor im Desktop-Layout geöffnet, wobei Höhe und Breite automatisch vom Browser bestimmt werden. Alternativ können Sie ein Mobilgerät emulieren und überprüfen, wie das Formular auf Mobilgeräten aussieht.

  ![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png){width=50%,height=50%}


* **Vorschaumodus**
Im Vorschaumodus wird das Formular im Editor genau so angezeigt, wie es veröffentlicht wird. So kann durch Klicken auf Links und Schaltflächen durch das Formular navigiert werden. Sobald die Bearbeitung abgeschlossen ist, kann das Formular für Live-Benutzende veröffentlicht werden. Der Tastaturbefehl zum Umschalten zwischen Bearbeitungs- und Vorschaumodus ist `p`.
  ![Vorschau](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

* **Seite öffnen**
Die Option **Seite öffnen** öffnet das Formular für die Vorschau auf einer neuen Registerkarte. Der Tastaturbefehl zum Öffnen des Formulars im Vorschaumodus auf einer neuen Registerkarte ist `o`.
  ![Seite öffnen](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

* **Veröffentlichen**

  Sie können das Formular mithilfe der Schaltfläche **Veröffentlichen** für Live-Benutzende verfügbar machen.
  ![Veröffentlichen](/help/edge/docs/forms/universal-editor/assets/ue-publish.png){width=50%,height=50%}

* **Auslassungspunkte**
Wenn der Autor bzw. die Autorin auf die Option mit den Auslassungspunkten (…) klickt, wird die Option **Veröffentlichen** angezeigt. Sie können die Veröffentlichung eines Formulars mit der Option **Veröffentlichung aufheben** wieder aufheben.
  ![Auslassungspunkte](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png){width=50%,height=50%}

### Bedienfeld „Eigenschaften“

Das Bedienfeld **Eigenschaften** befindet sich auf der rechten Seite des Editors. Es zeigt die Details der Komponente an, die in der Hierarchie des Formulars ausgewählt ist. Dies ist die Standardstruktur, wenn keine Komponente ausgewählt ist.
![Bedienfeld „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png){width=50%,height=50%}


Sehen wir uns die einzelnen Komponenten an.


* **Eigenschaftenmodus**
Unter der Option **Eigenschaften** werden die Eigenschaften der ausgewählten Komponente im Editor angezeigt. Das Bild zeigt beispielsweise die Eigenschaften der ausgewählten Komponente für die Zahleneingabe an. Sie können die Eigenschaften der Komponente mit dieser Option ändern. Der Tastaturbefehl zum Öffnen der Eigenschaften der Komponente ist `d`.

  ![Eigenschaften](/help/edge/docs/forms/universal-editor/assets/ue-properties.png){width=50%,height=50%}


* **Inhaltsstruktur**
Mit **Option &quot;**&quot; wird die Hierarchie des Formulars angezeigt. Wenn Sie auf ein Element in der Inhaltsstruktur klicken, wählt der Editor es aus und scrollt zu dieser Komponente. Der Tastaturbefehl zum Umschalten zwischen den Ansichten der Inhaltsstruktur lautet `f`.

  ![Inhaltsstruktur](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png){width=50%,height=50%}


* **Varianten generieren**
  **Varianten generieren** nutzt künstliche Intelligenz, um basierend auf bestimmten Prompts unterschiedliche Versionen von Formularen zu erstellen. Diese Prompts können entweder von Adobe bereitgestellt oder vom Formularverfasser bzw. von der Formularverfasserin erstellt und verwaltet werden.

  ![Variante](/help/edge/docs/forms/universal-editor/assets/ue-variations.png){width=50%,height=50%}


  >[!NOTE]
  >
  > Anweisungen zur Verwendung von „Varianten generieren“ für Formulare finden Sie im Artikel [Generieren von Varianten](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/generative-ai/generate-variations).

* **Experimentieren**

  **Experimentieren** bezieht sich auf Techniken, mit denen verschiedene Varianten von Formularen und Layouts getestet werden, um das Benutzererlebnis und die Leistung zu optimieren.
  ![Experimentieren](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png){width=50%,height=50%}


* **Personalisierung**
Mit der Option **Personalisierung** werden die Einstellungen so konfiguriert, dass eine Verbindung zwischen den Formularen und Adobe Experience Platform (AEP) hergestellt wird, die Teil des Adobe-Ökosystems oder externer Anwendungen sind.
  ![Personalisierung](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png){width=50%,height=50%}


* **A/B-Tests**
  **A/B-Tests** beziehen sich auf Techniken, mit denen verschiedene Varianten von Formularen und Layouts getestet werden, um das Benutzererlebnis und die Leistung zu optimieren.
  ![A/B-Tests](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png){width=50%,height=50%}



* **Aufgabenverwaltung**:
Die Funktion **Aufgabenverwaltung** ermöglicht es Ihnen, Workflows zu optimieren und die Zusammenarbeit zu verbessern, indem sie es Teams möglich macht, Aufgaben im Zusammenhang mit der Anpassung und Optimierung von Formularen zu verwalten, zu verfolgen und auszuführen
  ![Aufgabenverwaltung](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png){width=50%,height=50%}

.
* **Inhaltsentwürfe**

  Mit Option **Inhaltsentwürfe** können Sie Entwürfe für Rich-Text-Elemente erstellen. Entwürfe können mit vorhandenem Formulartext oder von Grund auf neu erstellt werden. Entwürfe können nach Bedarf bearbeitet oder gelöscht werden. Standardmäßig sind nur drei Entwürfe sichtbar. Wenn Sie jedoch auf **Alle anzeigen** klicken, wird auch der Rest angezeigt.

  ![Aufgabenverwaltung](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png){width=50%,height=50%}


* **Datenquelle**

  Mit Option **Datenquelle** können Sie Datenquellen konfigurieren und beim Erstellen eines Formulardatenmodells (FDM) auswählen. So werden alle Datenmodellobjekte, Eigenschaften und Services aus den ausgewählten Datenquellen zur Verwendung im Formulardatenmodell verfügbar gemacht.
  ![Datenquelle](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png){width=50%,height=50%}

* **Hinzufügen**

  Die Option **Hinzufügen** öffnet eine Dropdown-Liste von Komponenten, die zum ausgewählten Container hinzugefügt werden können. In einem Abschnitt für adaptive Formulare zeigt die Liste beispielsweise die verfügbaren Komponenten an, die einem Formular hinzugefügt werden können. Der Tastaturbefehl zum Öffnen der Liste von Komponenten ist `a`.
  ![Symbol hinzufügen](/help/edge/docs/forms/universal-editor/assets/ue-add.png){width=50%,height=50%}

* **Duplizieren**

  Mit der Option **Duplizieren** wird eine Kopie der Komponente erstellt, die entweder in der Inhaltsstruktur oder im Editor ausgewählt ist.
  ![Symbol „Duplizieren“](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png){width=50%,height=50%}


* **Löschen**
Mit der Option **Löschen** wird eine Komponente gelöscht, die entweder in der Inhaltsstruktur oder im Editor ausgewählt ist.

  ![Löschen](/help/edge/docs/forms/universal-editor/assets/ue-delete.png){width=50%,height=50%}

### Editor

Mit dem Editor können Sie das Formular bearbeiten, und das in der Speicherortleiste angegebene Formular wird im Bearbeitungsbereich gerendert. Wenn sich der Editor im Vorschaumodus befindet, können Sie mithilfe der verfügbaren Schaltflächen und Links durch das Formular navigieren.
![Editor](/help/edge/docs/forms/universal-editor/assets/ue-editor.png){width=50%,height=50%}

## Siehe auch

{{universal-editor-see-also}}
