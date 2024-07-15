---
title: 'Optimale Verfahren und wichtige Hinweise zum Arbeiten adaptiven AEM-Formularen:'
description: Einige optimale Verfahren und wichtige Hinweise zum Arbeiten mit Komponenten adaptiver Formulare.
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 100%

---


# Best Practices für das Arbeiten mit Komponenten {#best-practices-for-working-with-components}

Hier finden Sie einige optimale Verfahren und wichtige Hinweise zum Arbeiten mit Komponenten adaptiver Formulare:

* Jede Komponente verfügt über zugehörige Eigenschaften, die ihre Darstellung und Funktion steuern. Wählen Sie zum Konfigurieren der Eigenschaften einer Komponente die Komponente aus und wählen Sie dann ![Eigenschaften](assets/Smock_Wrench_18_N.svg), um die Komponenteneigenschaften im Eigenschaften-Browser zu öffnen.
* Eine Komponente wird mit ihrem Elementnamen identifiziert. Wenn Sie ![Eigenschaften](assets/Smock_Wrench_18_N.svg) wählen, können Sie den Namen der Komponente ändern, indem Sie den Wert des Felds **[!UICONTROL Elementname]** im Eigenschaften-Browser ändern. Das Feld „Elementname“ akzeptiert nur Buchstaben, Zahlen, Bindestriche (-) und Unterstriche (_). Andere Sonderzeichen sind nicht zulässig, und der Elementname sollte mit einem Buchstaben beginnen.

* Sie können die Eigenschaft „Titel“ einer Komponente eines adaptiven Formulars inline im Formulareditor ändern, ohne den Eigenschaftenbrowser zu öffnen, solange der Titel im Formular sichtbar ist. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie eine Komponente aus, in der die Eigenschaft **[!UICONTROL Titel]** vorhanden und deren Eigenschaft **[!UICONTROL Titel ausblenden]** deaktiviert ist.

   1. Wählen Sie das ![Bearbeitungssymbol](assets/Smock_Edit_18_N.svg), damit der Titel bearbeitet werden kann.

   1. Ändern Sie den Titel und drücken Sie die Eingabetaste oder wählen Sie eine beliebige Stelle außerhalb der Komponente, um die Änderungen zu speichern. Drücken Sie die Esc-Taste, um die Änderungen zu verwerfen.

* Bei einigen Komponenten für adaptive Formulare, z. B. E-Mail und Telefon, stehen standardmäßige Validierungsmuster zur Verfügung. Sie können jedoch eine benutzerdefinierte Validierung angeben, indem Sie das Feld **[!UICONTROL Validierungsmuster]** unter dem Akkordeon „Muster“ in den Komponenteneigenschaften aktualisieren. Weitere Informationen zu Standardvalidierungen finden Sie in den Komponentenbeschreibungen in der Tabelle oben.

* Felder in adaptiven Formularen, z. B. numerische Felder und E-Mail, können so konfiguriert werden, dass spezifische HTML5-Eingabetypen einbezogen werden. Wenn diese Felder auf Mobilgeräten und Tablets im Fokus sind, enthält die Tastatur direkt spezifische Buchstaben, Zahlen und andere Zeichen, die häufig für die Eingabe von Informationen in das betreffende Feld verwendet werden. Damit können Benutzer schnell Informationen eingeben, ohne zwischen Zeichensätzen auf der Tastatur zu wechseln. Um spezielle Eingaben für eine Komponente zu ermöglichen, aktivieren Sie das Kontrollkästchen **[!UICONTROL HTML-Typnummer verwenden]** in den Komponenteneigenschaften.

* Sie können die Eingabe von Rich Text in einer Textfeldkomponente ermöglichen. Um Rich Text für ein Textfeld zu aktivieren, aktivieren Sie das Kontrollkästchen **[!UICONTROL Rich Text zulassen]** in den Komponenteneigenschaften.

* Mithilfe von Textfeld-, E-Mail- und Telefonkomponenten können Sie in Feldern wie Name, Adresse, Kreditkarte, Telefon und E-Mail automatisch Werte aus den Daten übernehmen lassen, die in den Browsereinstellungen für das automatische Ausfüllen gespeichert sind. Um diese Funktion zu aktivieren, wählen Sie **[!UICONTROL Automatisches Ausfüllen aktivieren]** in den Komponenteneigenschaften und ein **[!UICONTROL Attribut für automatisches Ausfüllen]** aus. Wenn ein Benutzer ein adaptives Formular ausfüllt, werden Werte aus dem Profil für automatisches Ausfüllen im Browser oder anhand früher vom Benutzer eingegebener Werte vorgeschlagen. Das automatische Ausfüllen funktioniert, wenn die Einstellungen für das automatische Ausfüllen im Browser der Person aktiviert sind.

* Geben Sie in den Komponenteneigenschaften Werte für Optionsfeld- und Kontrollkästchenelemente im Format `{value}={text}` an.
* Die Dateianlagenkomponente ermöglicht es Benutzenden standardmäßig, nur eine Datei anzuhängen. Sie können die Komponenteneigenschaften jedoch so konfigurieren, dass mehrere Anhänge unterstützt werden. Wenn mehrere Dateien mit demselben Dateinamen angehängt werden, können die Anhänge einige Probleme verursachen. Daher wird empfohlen, bei der Formularübermittlung für jeden gesendeten Anhang eine eindeutige Kennung damit zu verknüpfen. Gehen Sie dazu wie folgt vor:

   1. Navigieren Sie auf Ihrem [!DNL AEM Forms]-Server zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
   1. Suchen Sie **[!UICONTROL Konfigurationsdienst für adaptive Formulare]** und wählen Sie ihn aus.
   1. Aktivieren Sie im Dialog „Konfigurations-Service für adaptive Formulare“ **[!UICONTROL Dateinamen individualisieren]**. Diese Option ist standardmäßig deaktiviert.

* Damit Benutzende eine PDF-Datei mit dem Safari-Browser anhängen können, müssen Sie sicherstellen, dass **application/pdf** zur Eigenschaft „Unterstützte Dateitypen“ der Dateianhangskomponente hinzugefügt wird. Adaptive Formulare, die mit der vorherigen [!DNL AEM Forms]-Version erstellt wurden, enthalten in der Eigenschaft „Unterstützte Dateitypen“ möglicherweise **.pdf** statt **application/pdf**.

>[!NOTE]
>
>Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.