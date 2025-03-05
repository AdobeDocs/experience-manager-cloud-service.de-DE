---
title: Grundlegendes zum universellen Editor
description: Dieses Tutorial hilft Ihnen, sich mit der Oberfläche des universellen Editors vertraut zu machen. Es erklärt Ihnen die Benutzeroberfläche, damit Sie Ihre eigenen Edge Delivery Services-Formulare im universellen Editor erstellen können.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 10%

---


# Erkunden der Benutzeroberfläche des universellen Editors (WYSIWYG)

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) bietet eine einfache, visuelle und intuitive Benutzeroberfläche für What You See Is What You Get (WYSIWYG) für Adobe Edge Delivery Services Forms. Er verfügt über eine moderne Benutzeroberfläche mit Drag-and-Drop-Funktionalität zur effizienten Formularerstellung.

![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Was Sie lernen werden

Am Ende dieses Tutorials werden Sie:

- Die Hauptkomponenten der Benutzeroberfläche des universellen Editors
- Sicher durch die verschiedenen Schnittstellenbereiche navigieren
- Wissen, wie Sie auf wichtige Tools zur Formularerstellung zugreifen und diese verwenden können
- Vertrautheit mit Tastaturbefehlen, die die Produktivität steigern

## Grundlegendes zur Benutzeroberfläche des universellen Editors

Wenn Sie ein Formular mit dem universellen Editor bearbeiten, öffnet die Konsole eine interaktive WYSIWYG-Oberfläche, über die Sie sofort mit der Bearbeitung beginnen können. Diese Benutzeroberfläche bietet während der Arbeit visuelles Feedback in Echtzeit und zeigt Endbenutzern genau, wie Ihr Formular aussieht.

>[!NOTE]
>
> Informationen zum Erstellen von Formularen mit dem universellen Editor finden Sie im Artikel [Erste Schritte mit Edge Delivery Services für AEM Forms mithilfe des universellen Editors (WYSIWYG)](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

Die Benutzeroberfläche des universellen Editors ist in vier logische Teile unterteilt:

- **[A: Kopfzeile von Experience Cloud](#experience-cloud-header)**
- **[B: Symbolleiste des universellen Editors](#universal-editor-toolbar)**
- **[C: Bedienfeld „Eigenschaften“](#properties-panel)**
- **[D: Editor](#editor)**

Sehen wir uns die einzelnen Abschnitte im Detail an.

### Experience Cloud-Kopfzeile

Der Experience Cloud-Header wird oben in der Konsole angezeigt und bietet Navigationskontext innerhalb des umfassenderen Adobe Experience Cloud-Ökosystems. Es zeigt Ihren aktuellen Speicherort an und ermöglicht den schnellen Zugriff auf andere Experience Cloud-Programme.

![Experience Cloud-Kopfzeile des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)

Untersuchen wir die einzelnen Komponenten:

- **Adobe Experience Cloud**

  Durch Klicken auf den Link **Adobe Experience Cloud** auf der linken Bildschirmseite können Sie zum Stammverzeichnis der Experience Manager-Lösung navigieren. Dort können Sie auf andere Tools wie Experience Manager Sites, Experience Manager Assets und Experience Manager Guides zugreifen.

  ![Adobe Experience Manager](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png)

- **Organisationsname**

  Der **Organisationsname** zeigt den Namen der Identity Management System (IMS)-Organisation an, bei der Sie derzeit angemeldet sind. Wenn Sie Zugriff auf mehrere Organisationen haben, können Sie mithilfe dieses Dropdown-Menüs zwischen ihnen wechseln. Im Screenshot zum Beispiel lautet die aktuell ausgewählte IMS-Organisation &quot;AEM Forms Internal01“.

  ![Organisation](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png)

- **Hilfe**

  Das Hilfesymbol bietet schnellen Zugriff auf Lern- und Support-Ressourcen. Dies ist besonders nützlich, wenn Sie auf Herausforderungen stoßen oder Anleitungen zu bestimmten Funktionen benötigen. Sie können Feedback auch über diesen Abschnitt senden.

  ![Hilfe](/help/edge/docs/forms/universal-editor/assets/ue-help.png)

- **Benachrichtigungen**

  Im Abschnitt **Benachrichtigungen** wird die Anzahl der aktuell zugewiesenen unvollständigen Benachrichtigungen, Anfragen und aktuellen Aufgaben in Ihrer IMS-Organisation angezeigt. Wenn Sie diesen Abschnitt im Auge behalten, behalten Sie den Überblick über Ihren Workflow.

  ![Benachrichtigung](/help/edge/docs/forms/universal-editor/assets/ue-notification.png)

- **Lösungen**

  Das **Lösungen**-Menü ermöglicht den Wechsel zu anderen Adobe Experience Cloud-Lösungen, sodass Sie einfach zwischen verschiedenen Tools in Ihrem Workflow wechseln können.

  ![Lösungen](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png)

- **Benutzerprofil**

  Dieses Symbol zeigt Ihre Profilinformationen zusammen mit dem Namen der IMS-Organisation an, bei der Sie derzeit angemeldet sind. Klicken Sie auf dieses Symbol, um auf Kontoeinstellungen und Abmeldeoptionen zuzugreifen.

  ![Autor](/help/edge/docs/forms/universal-editor/assets/ue-author.png)

### Symbolleiste des universellen Editors

Die Symbolleiste bietet wichtige Navigations- und Bearbeitungswerkzeuge. Damit können Sie zwischen Formularen wechseln, Formulare veröffentlichen oder die Veröffentlichung rückgängig machen, Formulareigenschaften bearbeiten und auf den Regeleditor zugreifen, um dynamische Verhaltensweisen hinzuzufügen.

![Symbolleiste des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

Die einzelnen Komponenten bieten folgende Neuerungen:

- **Taste HOME**

  Die Schaltfläche „Startseite“ kehrt zur Startseite des universellen Editors zurück. Dies ist nützlich, wenn Sie mit der Arbeit an einem anderen Formular beginnen müssen. Sie können auch direkt eine URL in der Adressleiste eingeben, um zu jedem Formular zu navigieren, das Sie bearbeiten möchten.

  ![Startseite des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-home.png)

- **Speicherortleiste**

  Die **Standortleiste** zeigt die Adresse des Formulars an, das Sie gerade bearbeiten. Um zu einem anderen Formular zu wechseln, klicken Sie einfach auf die Adressleiste und geben Sie die URL ein. Der Tastaturbefehl zum Fokussieren der Positionsleiste ist `l`.

  ![Speicherortleiste](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png)

- **Regeleditor**

  Der **Regeleditor** ermöglicht es Ihnen, Ihren Formularen über eine intuitive visuelle Benutzeroberfläche dynamische Verhaltensweisen hinzuzufügen. Damit können Sie Bedingungen, Validierungen und Aktionen erstellen, die auf Benutzereingaben reagieren, sodass Ihre Formulare interaktiv und intelligent werden.

  ![Regeleditor](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > - Die Erweiterung „Regeleditor“ ist im universellen Editor nicht standardmäßig aktiviert. Um diese leistungsstarke Funktion zu aktivieren, kontaktieren Sie uns unter [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) von Ihrer offiziellen E-Mail-Adresse.
  > - Informationen zum Erstellen und Verwalten von Regeln finden Sie im Artikel [Einführung in den Regeleditor beim WYSIWYG-Authoring](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

- **Formulareigenschaften bearbeiten**

  Mit **Option „Formulareigenschaften bearbeiten** können Sie wichtige Formulareinstellungen wie das Formulardatenmodell (FDM) und das Veröffentlichungsdatum konfigurieren. Diese Eigenschaften beeinflussen, wie sich Ihr Formular verhält und mit Backend-Systemen integriert wird.

  ![Formulareigenschaften bearbeiten](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)

- **Authentifizierungs-Header-Einstellungen**

  Mit **Option „Einstellungen für Authentifizierungs** Header“ können Sie benutzerdefinierte Authentifizierungs-Header für lokale Entwicklungszwecke festlegen. Dies ist besonders beim Testen von Formularen nützlich, für die Authentifizierungsdaten erforderlich sind.

  ![Authentifizierungs-Header](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png)

- **Responsiver Modus**

  Mit **Funktion „Responsive**&quot; können Sie testen, wie Ihr Formular auf verschiedenen Geräten angezeigt wird. Standardmäßig wird der Editor im Desktop-Layout geöffnet. Sie können jedoch zur mobilen Ansicht wechseln, um sicherzustellen, dass Ihr Formular auf kleineren Bildschirmen nützlich und attraktiv bleibt.

  ![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png)

- **Vorschaumodus**

  **Vorschaumodus** zeigt das Formular genau so an, wie es bei der Veröffentlichung angezeigt wird. Auf diese Weise können Sie mit dem Formular interagieren, indem Sie auf Links und Schaltflächen klicken, genau wie es Ihre Benutzer tun würden. Dies ist ein wichtiger Schritt vor der Veröffentlichung, um zu überprüfen, ob alles wie erwartet funktioniert. Schalten Sie mithilfe des Tastaturbefehls zwischen Bearbeitungs- und `p` um.

  ![Vorschau](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

- **Seite öffnen**

  Mit der **Seite öffnen**-Schaltfläche wird Ihr Formular in einer neuen Browser-Registerkarte für die Vorschau geöffnet. Dadurch erhalten Sie eine Vollbildansicht Ihres Formulars ohne Editor-Oberfläche. Der Tastaturbefehl für diese Aktion ist `o`.

  ![Seite öffnen](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

- **Veröffentlichen**

  Sobald Ihr Formular für Benutzer bereit ist, **Sie es mit der Schaltfläche** Veröffentlichen“ live und für Ihre Zielgruppe verfügbar machen. Dies ist der letzte Schritt in Ihrem Arbeitsablauf zur Formularerstellung.

  ![Veröffentlichen ](/help/edge/docs/forms/universal-editor/assets/ue-publish.png)

- **Menü mit Auslassungspunkten**

  Durch Klicken auf die Auslassungszeichen (…) werden zusätzliche Optionen angezeigt, einschließlich der Möglichkeit **die Veröffentlichung** Formulars rückgängig zu machen, das derzeit live ist. Dies ist nützlich, wenn Sie ein Formular vorübergehend aus dem öffentlichen Zugriff entfernen oder durch eine aktualisierte Version ersetzen müssen.

  ![Auslassungspunkte](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png)

### Bedienfeld „Eigenschaften“

Das **Eigenschaftenbedienfeld** wird auf der rechten Seite der Benutzeroberfläche angezeigt und zeigt kontextuelle Informationen basierend auf dem an, was Sie im Formular ausgewählt haben. Wenn keine Komponente ausgewählt ist, wird die gesamte Formularstruktur angezeigt.

![Bedienfeld „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

Sehen wir uns die wichtigsten Komponenten an:

- **Eigenschaftenmodus**

  Der **Eigenschaften**-Modus zeigt Einstellungen und Optionen für die aktuell ausgewählte Komponente an. Hier können Sie die einzelnen Elemente Ihres Formulars an Ihre spezifischen Anforderungen anpassen. Der Tastaturbefehl zum Öffnen der Eigenschaften einer ausgewählten Komponente ist `d`.

  ![Eigenschaften](/help/edge/docs/forms/universal-editor/assets/ue-properties.png)

- **Inhaltsstruktur**

  Die **Inhaltsstruktur** zeigt die hierarchische Struktur Ihres Formulars an. Diese visuelle Darstellung hilft Ihnen zu verstehen, wie Komponenten ineinander verschachtelt sind. Wenn Sie auf ein Element in der Struktur klicken, wird es im Editor ausgewählt und zu seiner Position gescrollt. Dies ist besonders bei komplexen Formularen hilfreich. Die Inhaltsstruktur-Ansicht mit dem Tastaturbefehl `f` ein/aus.

  ![Inhaltsstruktur](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png)

- **Varianten generieren**

  Die Funktion **Varianten generieren** nutzt künstliche Intelligenz, um basierend auf bestimmten Eingabeaufforderungen verschiedene Versionen Ihres Formulars zu erstellen. So können Sie mit verschiedenen Ansätzen und Designs experimentieren, ohne jede Variante manuell erstellen zu müssen. Eingabeaufforderungen können von Adobe bereitgestellt oder von Ihnen angepasst werden.

  ![Varianten generieren](/help/edge/docs/forms/universal-editor/assets/ue-variations.png)

  >[!NOTE]
  >
  > Detaillierte Anweisungen zur Verwendung der Funktion „Varianten für Formulare generieren“ finden Sie [ Artikel zum Generieren ](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/generative-ai/generate-variations) Varianten .

- **Experimentieren**

  Mit **Funktion „Experimentieren** können Sie kontrollierte Tests durchführen, um verschiedene Formularentwürfe und Layouts zu vergleichen. Indem Sie analysieren, wie Benutzende mit den einzelnen Varianten interagieren, können Sie datengesteuerte Entscheidungen treffen, um die Konversionsraten und das Benutzererlebnis zu optimieren.

  ![Experimentieren](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png)

- **Personalisierung**

  Die Einstellungen für **Personalization** ermöglichen es Ihnen, Ihre Formulare mit Adobe Experience Platform (AEP) oder externen Anwendungen zu verbinden. Diese Verbindung ermöglicht es Ihnen, auf der Grundlage von Benutzerdaten und Verhaltensweisen maßgeschneiderte Formularerlebnisse zu erstellen, um die Relevanz und Interaktion zu steigern.

  ![Personalisierung](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png)

- **A/B-Tests**

  **A/B** Tests helfen Ihnen beim Vergleich bestimmter Varianten Ihres Formulars, um zu ermitteln, welche besser funktioniert. Im Gegensatz zu umfangreicheren Experimenten konzentrieren sich A/B-Tests normalerweise auf den Vergleich bestimmter Elemente oder Änderungen, um die effektivste Option zu ermitteln.

  ![A/B-Tests](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png)

- **Aufgabenverwaltung**

  Die Funktion **Aufgabenverwaltung** optimiert die Zusammenarbeit, indem sie Ihrem Team hilft, Aufgaben im Zusammenhang mit der Formularerstellung und -optimierung zu organisieren, zu verfolgen und auszuführen. Dies sorgt dafür, dass Projekte effizient und mit klarer Rechenschaftspflicht vorangebracht werden.

  ![Aufgabenverwaltung](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png)

- **Inhaltsentwürfe**

  Mit **Funktion „Inhaltsentwürfe** können Sie vorläufige Versionen von Textelementen in Ihrem Formular erstellen und speichern. Sie können Entwürfe mit vorhandenem Formulartext erstellen oder von Grund auf neu beginnen und sie dann nach Bedarf bearbeiten oder löschen. Standardmäßig werden drei Entwürfe angezeigt. Wenn Sie jedoch auf „Alle **&quot; klicken** werden zusätzliche Entwürfe angezeigt.

  ![Inhaltsentwürfe](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png)

- **Datenquelle**

  Source Mit **Option „Daten-**&quot; können Sie die Datenquellen für Ihr Formulardatenmodell (FDM) konfigurieren und auswählen. Durch diese Integration können alle Datenmodellobjekte, Eigenschaften und Services aus den ausgewählten Quellen im Formular verwendet werden, wodurch ein dynamischer Datenabruf und eine dynamische Übermittlung ermöglicht wird.

  ![Datenquelle](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png)

- **Hinzufügen**

  Die **Hinzufügen**-Schaltfläche zeigt eine Dropdown-Liste von Komponenten an, die zum aktuell ausgewählten Container hinzugefügt werden können. Wenn beispielsweise ein Abschnitt für ein adaptives Formular ausgewählt ist, zeigt diese Liste alle Komponenten an, die diesem Abschnitt hinzugefügt werden können. Der Tastaturbefehl zum Öffnen dieser Komponentenliste ist `a`.

  ![Symbol hinzufügen](/help/edge/docs/forms/universal-editor/assets/ue-add.png)

- **Duplizieren**

  Mit **Option** Duplizieren“ wird eine exakte Kopie der ausgewählten Komponente erstellt. Dies spart Zeit, wenn Sie mehrere ähnliche Elemente benötigen, da Sie sie duplizieren und dann ändern können, anstatt sie von Grund auf neu zu erstellen.

  ![Symbol „Duplizieren](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png)

- **Löschen**

  Mit **Option** Löschen“ wird die ausgewählte Komponente aus dem Formular entfernt. Seien Sie vorsichtig, wenn Sie diese Option verwenden, da sie das Element sofort ohne Bestätigungsaufforderung entfernt.

  ![Löschen](/help/edge/docs/forms/universal-editor/assets/ue-delete.png)

### Editor

Der Editor ist der zentrale Arbeitsbereich, in dem Sie Ihr Formular erstellen und ändern. Es zeigt das in der Speicherortleiste angegebene Formular an und bietet ein WYSIWYG-Erlebnis, das Benutzern genau zeigt, wie das Formular aussehen wird. Im Vorschaumodus können Sie mit dem Formular so interagieren, wie es Ihre Benutzer tun würden, indem Sie die Navigation durch Schaltflächen und Links testen.

![Bearbeiter](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

Im Editor verbringen Sie die meiste Zeit mit dem Hinzufügen von Komponenten, dem Konfigurieren ihrer Eigenschaften und dem Anordnen dieser Komponenten, um ein intuitives, effektives Formularerlebnis zu schaffen.

## Zusammenfassung der Tastaturbefehle

Beachten Sie zur Produktivitätssteigerung die folgenden wichtigen Tastaturbefehle:

- `l` - Fokus auf der Positionsleiste
- `p` - Zwischen Bearbeitungs- und Vorschaumodus wechseln
- `o` - Formular in einer neuen Registerkarte öffnen
- `d` - Eigenschaften der ausgewählten Komponente öffnen
- `f` - Ansicht der Inhaltsstruktur ein/aus
- `a` - öffnet die Liste der hinzuzufügenden Komponenten


