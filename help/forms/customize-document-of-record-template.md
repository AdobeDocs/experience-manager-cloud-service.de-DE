---
title: Wie lässt sich die automatisch generierte Datensatzdokument-Vorlage für adaptive Forms anpassen?
description: Erfahren Sie, wie Sie die automatisch generierte Datensatzdokument-Vorlage (Document of Record, DoR) für adaptive Forms mit Adobe Forms Designer herunterladen, anpassen und erneut hochladen.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer
source-git-commit: 51ec9ef76a8f3f9b7bf2cdc25b03f72e286f586f
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 4%

---


# Anpassen der automatisch generierten Datensatzdokument-Vorlage

<span class="preview"> Dieser Artikel gilt sowohl für **Kernkomponenten** als auch für **Foundation-Komponenten** basierte adaptive Forms.</span>

Wenn Sie automatisch ein Datensatzdokument (DoR) für ein adaptives Formular generieren, erstellt AEM Forms eine Standardvorlage, die auf der Formularstruktur basiert. Sie können diese automatisch generierte Vorlage an die Branding- und Layout-Anforderungen Ihres Unternehmens anpassen.

Der Anpassungs-Workflow umfasst drei Schritte:

1. Laden Sie die automatisch generierte DoR-Vorlage von Forms Manager herunter.
1. Ändern Sie die Vorlage mit Adobe Forms Designer.
1. Laden Sie die angepasste Vorlage erneut in AEM Forms hoch und konfigurieren Sie sie als benutzerdefinierte Vorlage.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* Zugriff auf AEM Forms Manager mit Berechtigungen zum Herunterladen und Hochladen von Vorlagen.
* Adobe Forms Designer auf Ihrem lokalen Computer installiert.
* Ein adaptives Formular mit **[!UICONTROL Generieren des Datensatzdokuments]**.

## Schritt 1: Herunterladen der automatisch generierten DoR-Vorlage {#download-auto-generated-dor-template}

So laden Sie die automatisch generierte DoR-Vorlage (XDP-Datei) für Ihr adaptives Formular herunter:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.
1. Navigieren Sie zu **[!UICONTROL Forms]** > **[!UICONTROL Forms und]**.
1. Wählen Sie das adaptive Formular aus, für das Sie die DoR-Vorlage herunterladen möchten.
1. Öffnen Sie die Eigenschaften des ausgewählten adaptiven Formulars.
1. Wählen Sie im Bedienfeld Eigenschaften die Option **[!UICONTROL Datensatzdokument herunterladen]**, um die automatisch generierte DoR-Vorlage (XDP-Datei) herunterzuladen.
1. Speichern Sie die heruntergeladene XDP-Datei auf Ihrem lokalen Computer.


## Schritt 2: Anpassen der Vorlage mit Adobe Forms Designer {#customize-template-using-designer}

Öffnen Sie die heruntergeladene XDP-Vorlage in Adobe Forms Designer und ändern Sie sie entsprechend den Anforderungen Ihres Unternehmens.

1. Öffnen Sie die heruntergeladene XDP-Datei in **Adobe Forms Designer**.
1. Passen Sie die Vorlage nach Bedarf an. Beispiele für Anpassungen:

   * **Mehrere Musterseiten**: Fügen Sie zusätzliche Musterseiten hinzu, um verschiedene Layouts für bestimmte Seiten des Datensatzdokuments zu definieren. Verwenden Sie beispielsweise eine eigene erste Seite mit einem Firmenbriefkopf und nachfolgende Seiten mit einem einfacheren Layout.
   * **Schriftfarben und Schriftfamilien**: Ändern Sie die Schriftfarbe, -größe und -familie, um sie an die Richtlinien Ihrer Unternehmensmarke anzupassen.
   * **Benutzerdefinierte Elemente**: Fügen Sie Elemente wie Firmenlogos, Kopfzeilen, Fußzeilen und Haftungsausschlusstext hinzu, um eine konsistente Markenidentität zu gewährleisten.
   * **Seitenlayout und -stile**: Passen Sie Ränder, Abstände und die gesamte Seitenstruktur an, um die Lesbarkeit zu verbessern.
   * **Feldstile und -positionierung**: Passen Sie das Erscheinungsbild und die Position von Formularfeldern an Ihr bevorzugtes Layout an.

1. Speichern Sie die benutzerdefinierte XDP-Vorlage.

>[!NOTE]
>
> Entfernen oder ändern Sie keine Skripte, die in der Vorlage vorhanden sind. Das Ändern von Skripten kann sich auf die Datenbindung und die Generierung des Datensatzdokuments auswirken.

## Schritt 3: Benutzerdefinierte Vorlage erneut in AEM hochladen {#reupload-customized-template}

Nachdem Sie die Vorlage angepasst haben, laden Sie sie in AEM Forms hoch und konfigurieren Sie das adaptive Formular für die Verwendung.

1. Laden Sie die benutzerdefinierte XDP-Vorlage in Ihre AEM Forms-Instanz hoch:
   * Navigieren Sie zu **[!UICONTROL Forms]** > **[!UICONTROL Forms und]**.
   * Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]** und laden Sie die benutzerdefinierte XDP-Datei hoch.

Konfigurieren Sie dann das Formular so, dass die benutzerdefinierte Vorlage verwendet wird. Die Schritte unterscheiden sich je nachdem, ob das Formular auf Kernkomponenten oder Foundation-Komponenten basiert.

>[!BEGINTABS]

>[!TAB Kernkomponenten]

Für adaptive Forms basierend auf Kernkomponenten:

1. Öffnen Sie das adaptive Formular in dem Editor, auf den Sie die benutzerdefinierte Vorlage anwenden möchten.
1. Wählen Sie in der Inhaltsstruktur den **[!UICONTROL Guide-Container]** (Stammbereich) aus.
1. Öffnen Sie **[!UICONTROL Eigenschaften]** und klicken Sie auf das Symbol **[!UICONTROL Datensatzdokument]** (DoR), um die Eigenschaften des Datensatzdokuments zu öffnen.
1. Öffnen Sie auf **[!UICONTROL Registerkarte]** das Dropdown-Menü **[!UICONTROL Vorlage]** und wählen Sie **[!UICONTROL Benutzerdefiniert]**.
1. Durchsuchen Sie die hochgeladene benutzerdefinierte XDP-Vorlage und wählen Sie sie aus.
1. Wählen Sie das Häkchen aus, das gespeichert werden soll.

   ![Eigenschaften des Datensatzdokuments - Vorlage auf „Benutzerdefiniert“ (Kernkomponenten)](/help/forms/assets/submission-pdf-dor-custom-template.png)

>[!TAB Foundation-Komponenten]

Für adaptive Forms auf Basis von Foundation-Komponenten:

1. Öffnen Sie das adaptive Formular in dem Editor, auf den Sie die benutzerdefinierte Vorlage anwenden möchten.
1. Wählen Sie den Stammbereich (Formular-Container) aus.
1. Öffnen Sie **[!UICONTROL Eigenschaften des Datensatzdokuments]** (über den Bereich „Eigenschaften“ oder die Registerkarte „Datensatzdokument„).
1. Öffnen Sie auf **[!UICONTROL Registerkarte]** das Dropdown-Menü **[!UICONTROL Vorlage]** und wählen Sie **[!UICONTROL Benutzerdefiniert]**.
1. Durchsuchen Sie die hochgeladene benutzerdefinierte XDP-Vorlage und wählen Sie sie aus.
1. Wählen Sie **[!UICONTROL Fertig]** aus, um zu speichern.

   ![Datensatzdokument-Eigenschaften - Vorlage auf „Benutzerdefiniert“ (Foundation-Komponenten)](/help/forms/assets/dor-custom-template-foundation-components.png)

>[!ENDTABS]

Das adaptive Formular verwendet jetzt die benutzerdefinierte Vorlage beim Generieren des Datensatzdokuments.

## Überprüfen der benutzerdefinierten Vorlage {#verify-customized-template}

So bestätigen Sie, dass die angepasste Vorlage korrekt angewendet wird:

1. Senden Sie einen Testeintrag für das adaptive Formular.
1. Generieren Sie das Datensatzdokument.
1. Überprüfen Sie, ob die generierte PDF Ihre Anpassungen widerspiegelt, einschließlich Logos, Schriftarten, Layout-Änderungen und anderer Branding-Elemente.

## Fehlerbehebung {#troubleshooting}

| Problem | Auflösung |
|---|---|
| Die benutzerdefinierte Vorlage wird nicht hochgeladen. | Stellen Sie sicher, dass die XDP-Datei gültig und nicht beschädigt ist. Stellen Sie sicher, dass Sie über die erforderlichen Berechtigungen zum Hochladen von Dateien in AEM Forms verfügen. |
| Anpassungen werden nicht im generierten Datensatzdokument angezeigt. | Bestätigen Sie, dass Sie die richtige benutzerdefinierte Vorlage im Abschnitt **[!UICONTROL Konfiguration der Datensatzdokument]** der Formulareigenschaften ausgewählt haben. |
| Layout- oder Formatierungsprobleme in der generierten PDF. | Stellen Sie sicher, dass die Anpassungen in Adobe Forms Designer den [Konventionen für Basisvorlagen](/help/forms/generate-document-of-record-core-components.md#base-template-conventions) entsprechen. Stellen Sie sicher, dass alle Elemente innerhalb der Vorlagenstruktur ordnungsgemäß positioniert sind. |

## Siehe auch {#see-also}

* [Generieren eines Datensatzdokuments für adaptive Formulare (Kernkomponenten)](/help/forms/generate-document-of-record-core-components.md)
* [Generieren eines Datensatzdokuments für adaptive Forms (Foundation-Komponenten)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Basisvorlage eines Datensatzdokuments](/help/forms/generate-document-of-record-core-components.md#base-template-of-a-document-of-record)
* [Anpassen der Branding-Informationen im Datensatzdokument](/help/forms/generate-document-of-record-core-components.md#customize-the-branding-information-in-document-of-record)

