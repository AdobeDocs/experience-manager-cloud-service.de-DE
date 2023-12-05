---
title: 'Optimale Verfahren und wichtige Hinweise zum Arbeiten adaptiven AEM-Formularen:'
description: Einige optimale Verfahren und wichtige Hinweise zum Arbeiten mit Komponenten adaptiver Formulare.
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 82%

---


# Best Practices für das Arbeiten mit Komponenten {#best-practices-for-working-with-components}

Hier finden Sie einige optimale Verfahren und wichtige Hinweise zum Arbeiten mit Komponenten adaptiver Formulare:

* Jede Komponente verfügt über zugehörige Eigenschaften, die ihre Darstellung und Funktion steuern. Um die Eigenschaften einer Komponente zu konfigurieren, wählen Sie die Komponente aus und wählen Sie ![properties](assets/Smock_Wrench_18_N.svg) , um die Komponenteneigenschaften im Eigenschaftenbrowser zu öffnen.
* Eine Komponente wird mit ihrem Elementnamen gekennzeichnet. Wenn Sie ![properties](assets/Smock_Wrench_18_N.svg)können Sie den Namen der Komponente ändern, indem Sie die **[!UICONTROL Elementname]** -Feldwert im Eigenschaftenbrowser. Das Feld „Elementname“ akzeptiert nur Buchstaben, Zahlen, Bindestriche (-) und Unterstriche (_).  Andere Sonderzeichen sind nicht zulässig, und der Elementname sollte mit einem Buchstaben beginnen.

* Sie können die Eigenschaft „Titel“ einer Komponente eines adaptiven Formulars inline im Formulareditor ändern, ohne den Eigenschaftenbrowser zu öffnen, solange der Titel im Formular sichtbar ist. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie diese Option aus, um eine Komponente auszuwählen, die über eine **[!UICONTROL Titel]** -Eigenschaft, deren **[!UICONTROL Titel ausblenden]** -Eigenschaft deaktiviert ist.

   1. Auswählen ![Symbol Bearbeiten](assets/Smock_Edit_18_N.svg) um den Titel bearbeitbar zu machen.

   1. Ändern Sie den Titel und wählen Sie die Eingabetaste aus oder wählen Sie eine beliebige Stelle außerhalb der Komponente aus, um die Änderungen zu speichern. Wählen Sie die Esc-Taste aus, um die Änderungen zu verwerfen.

* Bei einigen Komponenten für adaptive Formulare, z. B. E-Mail und Telefon, stehen standardmäßige Validierungsmuster zur Verfügung. Sie können jedoch eine benutzerdefinierte Validierung angeben, indem Sie das Feld **[!UICONTROL Validierungsmuster]** unter dem Akkordeon „Muster“ in den Komponenteneigenschaften aktualisieren. Weitere Informationen zu Standardvalidierungen finden Sie in den Komponentenbeschreibungen in der Tabelle oben.

* Felder in adaptiven Formularen, z. B. numerische Felder und E-Mail, können so konfiguriert werden, dass spezifische HTML5-Eingabetypen einbezogen werden. Wenn diese Felder auf Mobilgeräten und Tablets im Fokus sind, enthält die Tastatur direkt spezifische Buchstaben, Zahlen und andere Zeichen, die häufig für die Eingabe von Informationen in das betreffende Feld verwendet werden. Damit können Benutzer schnell Informationen eingeben, ohne zwischen Zeichensätzen auf der Tastatur zu wechseln. Um spezielle Eingaben für eine Komponente zu ermöglichen, aktivieren Sie das Kontrollkästchen **[!UICONTROL HTML-Typnummer verwenden]** in den Komponenteneigenschaften.

* Sie können die Eingabe von Rich Text in einer Textfeldkomponente ermöglichen. Um Rich Text für ein Textfeld zu aktivieren, aktivieren Sie das Kontrollkästchen **[!UICONTROL Rich Text zulassen]** in den Komponenteneigenschaften.

* Mithilfe von Textfeld-, E-Mail- und Telefonkomponenten können Sie in Feldern wie Name, Adresse, Kreditkarte, Telefon und E-Mail automatisch Werte aus den Daten übernehmen lassen, die in den Browsereinstellungen für das automatische Ausfüllen gespeichert sind. Um diese Funktion zu aktivieren, wählen Sie **[!UICONTROL Automatisches Ausfüllen aktivieren]** in den Komponenteneigenschaften und ein **[!UICONTROL Attribut für automatisches Ausfüllen]** aus. Wenn ein Benutzer ein adaptives Formular ausfüllt, werden Werte aus dem Profil für automatisches Ausfüllen im Browser oder anhand früher vom Benutzer eingegebener Werte vorgeschlagen. Die automatische Füllung funktioniert, wenn die Einstellungen für die automatische Füllung im Browser des Benutzers aktiviert sind.

* Geben Sie in den Komponenteneigenschaften Werte für Optionsfeld- und Kontrollkästchenelemente im Format `{value}={text}` an.
* Die Dateianhangskomponente ermöglicht es Benutzenden standardmäßig, nur eine Datei anzuhängen. Sie können jedoch die Komponenteneigenschaften so konfigurieren, dass mehrere Anhänge unterstützt werden.  Darüber hinaus können Probleme auftreten, wenn mehrere Dateien mit demselben Dateinamen angehängt werden. Daher wird empfohlen, bei der Übermittlung des Formulars jedem übermittelten Anhang eine eindeutige Kennung zuzuweisen. Gehen Sie dazu wie folgt vor:

   1. Navigieren Sie auf Ihrem [!DNL AEM Forms]-Server zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
   1. Suchen und Auswählen **[!UICONTROL Adaptiver Forms-Konfigurationsdienst]**.
   1. Aktivieren Sie im Dialog „Konfigurations-Service für adaptive Formulare“ **[!UICONTROL Dateinamen individualisieren]**. Diese Option ist standardmäßig deaktiviert.

* Damit Benutzende eine PDF-Datei mit dem Safari-Browser anhängen können, müssen Sie sicherstellen, dass **application/pdf** zur Eigenschaft „Unterstützte Dateitypen“ der Dateianhangskomponente hinzugefügt wird. Adaptive Formulare, die mit der vorherigen [!DNL AEM Forms]-Version erstellt wurden, enthalten in der Eigenschaft „Unterstützte Dateitypen“ möglicherweise **.pdf** statt **application/pdf**.

>[!NOTE]
>
>Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.