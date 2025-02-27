---
title: Grundlegendes zum universellen Editor - Responsiver Modus
description: In diesem Artikel wird erläutert, wie Sie mit verschiedenen Emulatoren im universellen Editor eine Vorschau von Formularen anzeigen können, um ihr Erscheinungsbild während des Authorings zu visualisieren.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 8f5b4d863ab469c44b4c221eab1fb128706b45c7
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 2%

---

# Responsiver Modus beim WYSIWYG-Authoring

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Organisationsname adobe und der Repository-Name abc.</span>


Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) ermöglicht die Vorschau von Edge Delivery Services Forms mit verschiedenen Emulatoren, um das Erscheinungsbild des Formulars während des Authorings zu sehen.

Der responsive Modus ermöglicht es Entwicklerinnen und Entwicklern, Layouts zu entwerfen, die sich automatisch an verschiedene Bildschirmgrößen anpassen, einschließlich Desktops, Tablets und Mobilgeräten. Der universelle Editor unterstützt Emulatoren für Desktop-, Tablet- und Mobilgeräte. Sie können die Höhe und Breite entsprechend Ihrer Bildschirmgröße festlegen und die folgenden Aktionen ausführen:

* Ausrichtung festlegen
* Breite und Höhe angeben
* Ausrichtung ändern

## Vorschau von Forms im responsiven Modus für verschiedene Geräte

Der universelle Editor bietet ein **Emulator**-Symbol oben rechts im Bildschirm, mit dem Sie Seiten über verschiedene Gerätegrößen hinweg in der Vorschau anzeigen und das Verhalten Ihres responsiven Designs testen können, um ein besseres Benutzererlebnis zu erzielen.

Führen Sie die folgenden Schritte aus, um zu sehen, wie der universelle Editor Formulare in verschiedenen Bildschirmgrößen rendert:

1. Öffnen Sie das Formular im universellen Editor zur Bearbeitung.
1. Wählen Sie das ![Emulator-Symbol](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%} aus, das in der Symbolleiste des universellen Editors verfügbar ist, und klicken Sie auf das Emulator-Symbol, um die Option anzuzeigen.

   ![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

1. Wählen Sie eine Option aus, um ein Formular im universellen Editor auf einem ausgewählten Gerät zu emulieren: Desktop, Tablet, Mobilgerät.

   ![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png){width=40%,height=40%}

   Standardmäßig wird der Editor in einem Desktop-Layout geöffnet, wobei Höhe und Breite automatisch vom Browser bestimmt werden. Alternativ können Sie ein Formular auf einem Mobilgerät oder Tablet-Gerät emulieren. Sie können auch die Bildschirmbreite und -höhe für benutzerdefinierte Geräte anpassen.

Der universelle Editor bietet verschiedene Emulatoren zum Anzeigen einer Vorschau von Formularen auf verschiedenen Geräten. In der folgenden Tabelle sind die verfügbaren Emulatortypen zusammen mit den entsprechenden Gerätedarstellungen aufgeführt:

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">Emulatortyp</th>
        <th style="width: 80%">Gerätebild</th>
    </tr>
    <tr>
        <td style="width: 20%">Desktop</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="Desktop-Emulator" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Tablet</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="Tablet-Emulator" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Mobilgeräte</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="Mobile-Emulator" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Benutzerdefiniertes Gerät</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="Benutzerdefinierter Geräteemulator" style="width: auto; height: auto"></td>
    </tr>
</table>

Mit dem Symbol **Bildschirmdrehung** können Sie bei der Vorschau eines Formulars auf verschiedenen Geräten zwischen Hoch- und Querformat hin- und herschalten. Damit können Entwickler testen, wie sich das responsive Design an Bildschirmrotationen auf verschiedenen Geräten anpasst.

Der universelle Editor unterstützt die verschiedenen Formularlayouts. Weitere Informationen zu den verschiedenen Layouts finden Sie im Abschnitt [Layout](#layout-capabilities)Funktionen.

## Layout-Funktionen

Mit dem universellen Editor können Sie benutzerfreundliche Formulare erstellen, die Endbenutzern dynamische Erlebnisse bieten. Das Formular-Layout steuert, wie Elemente oder Komponenten in einem Formular angezeigt werden.

Der universelle Editor unterstützt die folgenden Arten von Layouts für Formulare:
* [Bereichslayout](#panel-layout)
* [Assistenten-Layout](#wizard-layout)
* [Akkordeon-Layout](#accordion-layout)

### Bedienfeldlayout

Das Bereichslayout ist nützlich, um verwandte Felder so zu organisieren, dass die Navigation und das Auffinden entsprechender Inhalte erleichtert werden. Das Bereichslayout ordnet Formularkomponenten in separaten Bereichen oder Bereichen in Formularen an.

![Bedienfeld-Layout](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

Sie können die [Bedienfeld-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) verwenden, um das Bedienfeld-Layout einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren verschiedener Eigenschaften der Bedienfeldkomponente finden Sie im Artikel [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) .

### Assistenten-Layout


Das Assistenten-Layout vereinfacht ein komplexes Formular, indem es in verschiedene Schritte unterteilt wird. Jeder Schritt stellt einen anderen Teil des Prozesses dar, und Benutzende navigieren nacheinander durch die Schritte, häufig mit den Schaltflächen **Weiter** und **Zurück**. Sie können das Assistenten-Layout verwenden, um ein Formular zu erstellen, das mehrere Abschnitte oder Schritte umfasst.

![Assistentenlayout](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

Sie können die Komponente [Assistent](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) verwenden, um das Assistenten-Layout einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Assistenten-Komponente finden Sie im Artikel [Assistenten-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) .

### Akkordeon-Layout

Das Akkordeon-Layout zeigt Inhalte in ausblendbaren Abschnitten oder Bereichen in einem adaptiven Formular an. Wenn ein Abschnitt erweitert wird, wird der Inhalt darin angezeigt, während andere Abschnitte reduziert bleiben. Dieses Layout ist ideal für die Anzeige großer Informationsmengen in kompakter Form.

![Akkordeon-Layout](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

Sie können die [Akkordeon-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) verwenden, um das Akkordeon-Layout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Akkordeon-Komponente finden Sie im Artikel [Akkordeon-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) .

### Wie wählt man das richtige Layout?

Es ist wichtig, das richtige Layout auszuwählen, um das Benutzererlebnis und die Formularfunktionen zu optimieren. Die Tabelle hilft Ihnen, die verschiedenen verfügbaren Layout-Optionen zu verstehen, und führt Sie bei der Auswahl des am besten geeigneten Layouts basierend auf Ihren spezifischen Anforderungen und Anwendungsfällen:

| Funktion | Bedienfeldlayout | Assistenten-Layout | Akkordeon-Layout |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Zweck** | Gruppiert verwandte Inhalte in separate Abschnitte | Führt Benutzer durch einen mehrstufigen Prozess oder ein mehrstufiges Formular | Organisiert Inhalte in ausblendbaren Abschnitten |
| **Struktur** | Unterschiedliche Abschnitte | Sequenzielle Schritte/Seiten | Reduzierbare Bereiche/Abschnitte |
| **Navigation** | Klicken Sie auf die Panel-Kopfzeilen, um zu navigieren | - Vorwärts: „Weiter“-Taste<br>- Rückwärts: „Zurück“-Schaltfläche<br>- Optionale Schritte überspringen | Auf Kopfzeilen klicken, um Abschnitte zu erweitern/reduzieren |
| **Benutzererlebnis** | Organisiert große Inhaltsmengen auf überschaubare Weise | Schritt-für-Schritt-Anleitung zur Verringerung der Überlastung | Kompakte Ansicht mit erweiterten/reduzierten Abschnitten |
| **Nutzungsszenario** | Komplexe Formulare mit kategorisierten Abschnitten | Einrichtungsprozesse, komplexe Formulare | Häufig gestellte Fragen, Einstellungsmenüs, detaillierte Inhaltsabschnitte |

## Siehe auch

{{universal-editor-see-also}}
