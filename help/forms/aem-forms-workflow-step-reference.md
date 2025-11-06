---
title: Welche Workflow-Schritte sind für den AEM Forms-Cloud-Service verfügbar, um einen Workflow zu erstellen, oder für die Automatisierung von Geschäftsprozessen (Business Process Automation, BPM)?
description: Mit Forms-zentrierten Workflows können Sie schnell auf adaptiven Formularen basierende Workflows erstellen. Mit Adobe Sign können Sie Dokumente elektronisch signieren, formularbasierte Geschäftsprozesse erstellen, Daten abrufen und an mehrere Datenquellen senden sowie E-Mail-Benachrichtigungen senden.
exl-id: e1403ba6-8158-4961-98a4-2954b2e32e0d
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
keywords: Verwendung von AEM-Workflows, Verwendung von Schritten zur Aufgabenzuweisung, Schritt zur Konvertierung in PDF/A, Schritt zur Generierung eines Datensatzdokuments, Verwendung von Workflows, Schritt zur Unterzeichnung eines Dokuments, Schritt zur Generierung einer gedruckten Ausgabe, Schritt zur Generierung einer nicht interaktiven PDF-Ausgabe
feature: Adaptive Forms, Workflow
role: Admin, User
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '7409'
ht-degree: 99%

---


# Verwenden von formularzentrierten AEM-Workflows – Schrittreferenz zur Automatisierung von Geschäftsprozessen {#forms-centric-workflow-on-osgi-step-reference}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Sie verwenden Workflow-Modelle. Anhand eines Modells können Sie eine Reihe von Schritten definieren und ausführen. Sie können auch Modelleigenschaften definieren, um beispielsweise festzulegen, ob es sich um einen Übergangs-Workflow oder einen Workflow mit mehreren Ressourcen handelt. Sie können [verschiedene AEM-Workflow-Schritte in ein Modell aufnehmen, um die Business-Logik zu erzielen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de#extending-aem).

## Forms-zentrierte Schritte {#forms-workflow-steps}

Durch Forms-zentrierte Workflow-Schritte werden AEM Forms-spezifische Vorgänge in einem AEM-Workflow ausgeführt. Mit diesen Schritten können Sie schnell einen auf adaptiven Formularen basierenden, formularzentrierten Workflow auf OSGi erstellen. Diese Workflows können für die Entwicklung grundlegender Überprüfungs- und Genehmigungs-Workflows, interner und „Across-the-Firewall“-Geschäftsprozesse verwendet werden. Mit Forms-Workflow-Schritten können Sie auch:

* Geschäftsprozesse, Workflows nach der Übermittlung und Backend-Workflows zur Verwaltung von Registrierungsprozessen erstellen.

* Aufgaben erstellen und einem Benutzer oder einer Gruppe zuweisen.

* [!DNL Adobe Sign] verwenden, um in einem AEM-Workflow ein Dokument zum Unterzeichnen zu senden.

* Bei Bedarf oder bei Formularübermittlung ein Datensatzdokument generieren.

* Ein Workflow-Modell mit verschiedenen Datenquellen verbinden, um Daten einfach zu speichern und abzurufen.

* Den E-Mail-Schritt verwenden, um Benachrichtigungs-E-Mails und andere Anhänge bei Abschluss einer Aktion und bei Start oder Abschluss eines Workflows zu versenden.

>[!NOTE]
>
>Wenn das Workflow-Modell für einen externen Speicher markiert ist, können Sie für alle Schritte des Forms-Workflows nur die Variablenoption zum Speichern oder Abrufen von Datendateien und Anlagen auswählen.

## Schritt „Aufgabe zuweisen“ {#assign-task-step}

Beim Schritt „Aufgabe zuweisen“ wird eine Aufgabe erstellt und einem Benutzer oder einer Gruppe zugewiesen. Zusammen mit der Zuweisung der Aufgabe gibt die Komponente außerdem das adaptive Formular oder die nicht interaktive PDF-Datei für die Aufgabe an. Das adaptive Formular ist erforderlich, damit die Benutzer Eingaben vornehmen können, und die nicht interaktive PDF-Datei oder ein schreibgeschütztes adaptives Formular wird in Workflows verwendet, die nur zur Überprüfung dienen.

Sie können mit dieser Komponente auch das Verhalten der Aufgabe steuern. Beispielsweise das Erstellen eines automatischen Datensatzdokuments, das Zuweisen der Aufgabe an einen bestimmten Benutzer oder eine Gruppe, das Angeben des Pfads der übermittelten Daten, das Angeben des Pfads der Daten, die vorab ausgefüllt werden sollen, und das Angeben der Standardaktionen. Der Schritt „Aufgabe zuweisen“ hat folgende Eigenschaften:

* **[!UICONTROL Titel:]** Bezeichnung der Aufgabe. Der Titel wird im AEM-Posteingang angezeigt.
* **[!UICONTROL Beschreibung]**: Erläuterung der Vorgänge, die in der Aufgabe ausgeführt werden. Diese Informationen sind für andere Prozessentwickler nützlich, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **[!UICONTROL Miniaturbildpfad:]** Pfad des Aufgabenminiaturbilds. Wenn kein Pfad angegeben ist, wird für ein adaptives Formular das Standardminiaturbild angezeigt, und für das Datensatzdokument wird ein Standardsymbol angezeigt.
* **[!UICONTROL Workflow-Schritt]**: Ein Workflow kann mehrere Schritte umfassen. Diese werden im AEM-Posteingang angezeigt. Sie können diese Schritte in den Eigenschaften des Modells definieren (Sidekick > Seite > Seiteneigenschaften > Schritte).
* **[!UICONTROL Priorität]**: Die ausgewählte Priorität wird im AEM-Posteingang angezeigt. Die verfügbaren Optionen sind „Hoch“, „Mittel“ und „Niedrig“. Der Standardwert ist „Mittel“.
* **[!UICONTROL Fälligkeitsdatum]**: Geben Sie die Anzahl der Tage oder Stunden an, nach denen die Aufgabe als „überfällig“ markiert wird. Wenn Sie **[!UICONTROL Aus]** wählen, wird die Aufgabe niemals als überfällig markiert. Sie können auch einen Zeitüberschreitungs-Handler angeben, um bestimmte Aufgaben nach Überschreitung der Frist auszuführen.

* **[!UICONTROL Tage]**: Die Anzahl der Tage, innerhalb derer die Aufgabe abgeschlossen werden soll. Die Tage werden ab dem Zeitpunkt gezählt, zu dem die Aufgabe einer Person zugewiesen wird. Wenn eine Aufgabe nicht abgeschlossen wurde und die Anzahl der Tage im Feld „Tage“ überschreitet, wird bei Auswahl dieser Option nach den fälligen Tagen ein Zeitüberschreitungs-Handler ausgelöst.
* **[!UICONTROL Stunden]**: Die Anzahl der Stunden, innerhalb derer die Aufgabe abgeschlossen werden soll. Die Stunden werden ab dem Zeitpunkt gezählt, zu dem die Aufgabe einer Person zugewiesen wird. Wenn eine Aufgabe nicht abgeschlossen wurde und die Anzahl der Stunden im Feld „Stunden“ überschreitet, wird bei Auswahl dieser Option nach den fälligen Stunden ein Zeitüberschreitungs-Handler ausgelöst.
* **[!UICONTROL Zeitüberschreitung nach Fälligkeitsdatum]**: Wählen Sie diese Option aus, um das Auswahlfeld „Zeitüberschreitungshandler“ zu aktivieren.
* **[!UICONTROL Zeitüberschreitungshandler]**: Wählen Sie das Skript aus, das ausgeführt werden soll, wenn der Schritt „Aufgabe zuweisen“ das Fälligkeitsdatum überschreitet. Skripte, die im CRX-Repository unter [apps]/fd/dashboard/scripts/timeoutHandler abgelegt werden, stehen zur Auswahl. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Admin erstellt den Pfad, bevor dieser verwendet wird.
* **[!UICONTROL Markieren Sie die Aktion und den Kommentar aus der letzten Aufgabe in „Aufgabendetails“]**: Wählen Sie diese Option aus, um die letzte ausgeführte Aktion und den Kommentar im Abschnitt „Aufgabendetail“ einer Aufgabe anzuzeigen.
* **[!UICONTROL Typ]**: Wählen Sie den Typ des Dokuments aus, das ausgefüllt werden soll, wenn der Workflow gestartet wird. Sie können ein adaptives Formular, ein schreibgeschütztes adaptives Formular oder ein nicht interaktives PDF-Dokument auswählen.

<!-- , Interactive Communication Agent UI, or Interactive Communication Web Channel Document. -->


* **[!UICONTROL Adaptives Formular verwenden]**: Geben Sie die Methode zum Suchen des adaptiven Eingabeformulars an. Diese Option ist verfügbar, wenn Sie in der Dropdown-Liste „Typ“ die Option „Adaptives Formular“ oder „Schreibgeschütztes adaptives Formular“ auswählen. Sie können das adaptive Formular verwenden, das an den Workflow übermittelt wurde, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Typs „Zeichenfolge“ verwenden, um den Pfad anzugeben.\
  Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie ein adaptives Formular zur Laufzeit mit den verfügbaren Eingabemethoden angeben.

<!-- 

* **[!UICONTROL Use Interactive Communication]**: Specify the method to locate the input interactive communication. You can use the interactive communication submitted to the workflow, available at an absolute path, or available at a path in a variable. You can use a variable of type String to specify the path. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 

> [!NOTE]
>
>You must have cm-agent-users and workflow-users group assignments to access Interactive Communications Agent UI in AEM inbox.  

-->

* **[!UICONTROL Pfad des adaptiven Formulars]**: Geben Sie den Pfad des adaptiven Formulars an. Sie können das adaptive Formular verwenden, das an den Workflow übermittelt wird und an einem absoluten Pfad verfügbar ist, oder das adaptive Formular aus einem Pfad abrufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist.
* **[!UICONTROL PDF-Eingabedatei auswählen mit]**: Geben Sie den Pfad eines nicht interaktiven PDF-Dokuments an. Das Feld ist verfügbar, wenn Sie im Feld „Typ“ ein nicht interaktives PDF-Dokument auswählen. Sie können die PDF-Eingabedatei unter Verwendung des Pfads auswählen, der relativ zur Payload ist, unter einem absoluten Pfad gespeichert wird oder eine Variable des Datentyps „Dokument“ verwendet. Beispiel: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Der Pfad existiert nicht im CRX-Repository. Ein Admin erstellt den Pfad, bevor dieser verwendet wird. Für die Verwendung der Option „PDF-Pfad“ muss die Option „Datensatzdokument“ aktiviert sein oder Sie benötigen auf Formularvorlagen basierende Adaptive Forms.
* **[!UICONTROL Für abgeschlossene Aufgaben das adaptive Formular rendern als]**: Wenn eine Aufgabe als „abgeschlossen“ markiert ist, können Sie das adaptive Formular als schreibgeschütztes adaptives Formular oder PDF-Dokument rendern. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare zum Rendern des adaptiven Formulars als Datensatzdokument.
* **[!UICONTROL Vorbefüllt]**: Folgende unten aufgeführte Felder dienen als Eingaben für die Aufgabe:

   * **[!UICONTROL Eingabedatendatei auswählen mit]**: Pfad der Eingabedatendatei (.json, .xml, .doc oder Formulardatenmodell [FDM]). Sie können die Eingabedatendatei mit einem Pfad abrufen, der relativ zur Payload ist, oder die Datei abrufen, die in einer Variablen des Datentyps Dokument, XML oder JSON gespeichert ist. Beispielsweise enthält die Datei die Daten, die über eine AEM-Posteingangsanwendung für das Formular übermittelt werden. Ein Beispielpfad ist [Payload_Directory]/workflow/data.
   * **[!UICONTROL Eingabeanhänge auswählen mit]**: Anhänge, die am Speicherort verfügbar sind, werden an das Formular angehängt, das mit der Aufgabe verknüpft ist. Der Pfad kann relativ zur Payload sein oder den Anhang abrufen, der in einer Variablen eines Dokuments gespeichert ist. Ein Beispielpfad ist [Payload_Directory]/attachments/. Sie können Anlagen angeben, die relativ zur Payload platziert werden, oder eine Dokumenttyp-Variable („Array-Liste“ > „Dokument“) verwenden, um einen Eingabeanhang für das adaptive Formular anzugeben.

  <!-- 
    
    * **[!UICONTROL Choose input JSON]**: Select an input JSON file using a path that is relative to payload or stored in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list.

    * **[!UICONTROL Choose a custom prefill service]**: Select the prefill service to retrieve the data and prefill the Interactive Communication Web channel document or the Agent UI.  
    
    * **[!UICONTROL Use the prefill service of the interactive communication selected above]**: Use this option to use the prefill service of the Interactive Communication defined in the Use Interactive Communication drop-down list. 
    
    -->

   * **[!UICONTROL Zuordnung von Anforderungsattributen]**: Verwenden Sie den Abschnitt „Zuordnung von Anforderungsattributen“, um den [Namen und den Wert des Anforderungsattributs](work-with-form-data-model.md#bindargument) zu definieren. Rufen Sie die Details aus der Datenquelle basierend auf dem in der Anforderung angegebenen Attributnamen und -wert ab. Sie können einen Wert für das Anforderungsattribut mit einem Literalwert oder einer Variablen des Datentyps „Zeichenfolge“ definieren.

  <!--  
     
     The prefill service and request attribute mapping options are available only if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 
     
     -->

* **[!UICONTROL Übermittelte Informationen]**: Folgende Felder dienen als Ausgabespeicherorte für die Aufgabe:

   * **[!UICONTROL Ausgabedatendatei speichern mit]**: Speichern der Datendatei (.json, .xml, .doc oder Formulardatenmodell [FDM]). Die Datendatei enthält Informationen, die über das zugeordnete Formular übermittelt werden. Sie können die Ausgabedatendatei unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder sie in einer Variablen des Datentyps „Dokument“, XML oder JSON speichern. Zum Beispiel [Payload_Directory]/Workflow/data, wobei „data“ für eine Datei steht.
   * **[!UICONTROL Anhänge speichern mit]**: Speichern Sie die Formularanhänge in einer Aufgabe. Sie können die Anhänge unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder sie in einer Variablen der Array-Liste vom Datentyp „Dokument“ speichern.
   * **[!UICONTROL Datensatzdokument speichern mit]**: Pfad zum Speichern einer Datensatzdokumentdatei. Beispielsweise [Payload_Directory]/DocumentofRecord/credit-card.pdf. Sie können das Datensatzdokument unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder es in einer Variablen des Datentyps „Dokument“ speichern. Wenn Sie die Option **[!UICONTROL Relativ zur Nutzlast]** auswählen, wird das Datensatzdokument nicht generiert, wenn das Feld „Pfad“ leer bleibt. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste „Typ“ die Option „Adaptives Formular“ auswählen.

  <!-- 
    
    * **[!UICONTROL Save Web Channel data using]**: Save the Web Channel data file using a path that is relative to the payload or store it in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. c
    * **[!UICONTROL Save PDF document using]**: Save the PDF document using a path that is relative to the payload or store it in a variable of Document data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list.
    <!-- * **[!UICONTROL Save layout template using]**: Save the layout template using a path that is relative to the payload or store it in a variable of Document data type. The [layout template](layout-design-details.md) refers to an XDP file that you create using Forms Designer. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. 
    
    -->

* **[!UICONTROL Verantwortlicher]** > **[!UICONTROL Optionen zuweisen]**: Geben Sie die Methode an, mit der die Aufgabe einem Benutzer zugewiesen werden soll. Sie können die Aufgabe dynamisch einem Benutzer oder einer Gruppe zuweisen, indem Sie das Skript „Teilnehmerauswahl“ verwenden oder die Aufgabe einem bestimmten AEM-Benutzer oder einer bestimmten Gruppe zuweisen.
* **[!UICONTROL Teilnehmerauswahl]**: Die Option ist verfügbar, wenn die Option **[!UICONTROL Dynamisch zu einem Benutzer oder einer Gruppe]** im Feld „Optionen zuweisen“ ausgewählt ist. Sie können ein ECMAScript oder einen Service verwenden, um einen Benutzer oder eine Gruppe dynamisch auszuwählen. Weitere Informationen finden Sie unter [Erstellen eines benutzerdefinierten Schritts „Dynamischer Teilnehmer“ in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de&CID=RedirectAEMCommunityKautuk).

* **[!UICONTROL Teilnehmer]**: Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** im Feld **[!UICONTROL Teilnehmerauswahl]** ausgewählt ist. In diesem Feld können Sie Benutzende oder Gruppen für die Option „RandomParticipantChooser“ auswählen.

* **[!UICONTROL Zuweisung]**: Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** im Feld **[!UICONTROL Teilnehmerauswahl]** ausgewählt ist. Mit dem Feld können Sie eine Variable des Datentyps „Zeichenfolge“ auswählen, um den Verantwortlichen zu definieren.

* **[!UICONTROL Argumente]**: Das Feld ist verfügbar, wenn ein anderes Skript als „RandomParticipantChoose“ im Feld „Teilnehmerauswahl“ ausgewählt wurde. In diesem Feld können Sie eine Liste mit durch Kommas getrennten Argumenten für das im Feld „Teilnehmerauswahl“ ausgewählte Skript angeben.

* **[!UICONTROL Benutzer oder Gruppe]**: Die Aufgabe wird einer ausgewählten Person oder einer Gruppe zugewiesen. Die Option ist verfügbar, wenn die Option **[!UICONTROL Zu einem bestimmten Benutzer bzw. einer speziellen Gruppe]** im Feld **[!UICONTROL Optionen zuweisen]** ausgewählt ist. Das Feld listet alle Benutzer und Gruppen der Gruppe [!DNL workflow-users] auf.\
  Das Dropdown-Menü **[!UICONTROL Benutzer oder Gruppe]** führt die Benutzer und Gruppen auf, auf die der angemeldete Benutzer Zugriff hat. Die Anzeige des Benutzernamens hängt davon ab, ob Sie Zugriffsrechte auf den Knoten **[!UICONTROL users]** im CRX-Repository für diese bestimmte Person haben.

* **[!UICONTROL E-Mail-Benachrichtigung senden]**: Wählen Sie diese Option aus, um E-Mail-Benachrichtigungen an den Verantwortlichen zu senden. Diese Benachrichtigungen werden gesendet, wenn eine Aufgabe einem Benutzer oder einer Gruppe zugewiesen wird. Mit der Option **[!UICONTROL Empfänger-E-Mail-Adresse]** können Sie den Mechanismus zum Abrufen der E-Mail-Adresse angeben.

* **[!UICONTROL Empfänger-E-Mail-Adresse]**: Sie können die E-Mail-Adresse in einer Variablen speichern, mit einem Literal eine permanente E-Mail-Adresse angeben oder die Standard-E-Mail-Adresse der beauftragten Person verwenden, die in ihrem Profil angegeben ist. Sie können das Literal oder eine Variable verwenden, um die E-Mail-Adresse einer Gruppe anzugeben. Die Option „Variable“ ist beim dynamischen Abrufen und Verwenden einer E-Mail-Adresse hilfreich. Die Option **[!UICONTROL Standardmäßige E-Mail-Adresse des Verantwortlichen verwenden]** gilt nur für einen einzelnen Verantwortlichen. In diesem Fall wird die E-Mail-Adresse verwendet, die im Benutzerprofil der beauftragten Person gespeichert ist.

* **[!UICONTROL HTML-E-Mail-Vorlage]**: Wählen Sie die E-Mail-Vorlage für die Benachrichtigungs-E-Mail. Um eine Vorlage zu bearbeiten, ändern Sie die Datei unter /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt im CRX-Repository.
* **[!UICONTROL Delegierung zulassen an]**: Der AEM-Posteingang bietet dem angemeldeten Benutzer eine Option, den zugewiesenen Workflow an einen anderen Benutzer zu übertragen. Sie können innerhalb derselben Gruppe oder an die Benutzerin bzw. den Benutzer des Workflows aus einer anderen Gruppe delegieren. Wenn die Aufgabe einem einzelnen Benutzer zugewiesen ist und die Option **[!UICONTROL Delegierung an Mitglieder der Gruppe an Verantwortlichen zulassen]** aktiviert ist, kann die Aufgabe nicht an einen anderen Benutzer oder eine andere Gruppe übertragen werden.
* **[!UICONTROL Freigabeeinstellungen]**: Der AEM-Posteingang bietet Optionen zum Freigeben einer einzelnen oder aller Aufgaben im Posteingang für andere Benutzende:
   * Wenn die Option **[!UICONTROL Zulassen, dass der Beauftragte explizit im Posteingang teilen kann]** aktiviert ist, kann die Person die Aufgabe im AEM-Posteingang auswählen und sie für andere AEM-Benutzende freigeben.
   * Wenn die Option **[!UICONTROL Zulassen, dass der Beauftragte explizit über Posteingang teilen kann]** ausgewählt ist und Benutzende ihre Posteingangselemente freigeben oder anderen Benutzenden den Zugriff auf ihre Posteingangselemente gestatten, werden nur Aufgaben, für die die zuvor genannte Option aktiviert ist, für andere Benutzende freigegeben.
   * Wenn die Option **[!UICONTROL Zulassen, dass Verantwortlicher Abwesenheitseinstellungen delegiert]** ausgewählt ist. Der Verantwortliche kann die Option aktivieren, um die Aufgabe zusammen mit anderen Abwesenheitsoptionen an andere Benutzer zu delegieren. Jegliche neuen Aufgaben, die dem Benutzer der Abwesenheitsfunktion zugewiesen werden, werden automatisch an die in den Abwesenheitseinstellungen aufgeführten Benutzer delegiert (ihnen zugewiesen).

  So können andere Benutzende Aufgaben der verantwortlichen Person auswählen, während diese abwesend ist und nicht an zugewiesenen Aufgaben arbeiten kann.

* **[!UICONTROL Aktionen]** > **[!UICONTROL Standardaktionen]**: Standardmäßig sind die Aktionen „Übermitteln“, „Speichern“ und „Zurücksetzen“ verfügbar. Alle Standardaktionen sind standardmäßig aktiviert.
* **[!UICONTROL Route-Variable]**: Name der Route-Variablen. Die Route-Variable erfasst benutzerdefinierte Aktionen, die Benutzende im AEM-Posteingang auswählen.
* **[!UICONTROL Routen]**: Eine Aufgabe kann eine Verzweigung auf verschiedene Routen aufweisen. Bei Auswahl im AEM-Posteingang gibt die Route einen Wert zurück, und der Workflow verzweigt basierend auf der ausgewählten Route. Sie können Routen entweder in einer Variablen des Arrays des Datentyps „Zeichenfolge“ speichern oder **[!UICONTROL Literal]** auswählen, um Routen manuell hinzuzufügen.

* **[!UICONTROL Routentitel]**: Geben Sie den Titel für die Route an. Er wird im AEM-Posteingang angezeigt.
* **[!UICONTROL Coral-Symbol]**: Geben Sie das HTML-Attribut eines Coral-Symbols an. Die Adobe CoralUI-Bibliothek bietet eine Vielzahl von Touch-First-Symbolen. Sie können ein Symbol für die Route auswählen und verwenden. Es wird zusammen mit dem Titel im AEM-Posteingang angezeigt. Wenn Sie die Routen in einer Variablen speichern, verwenden die Routen ein standardmäßiges „Tags“-Korallensymbol.
* **[!UICONTROL Zulassen, dass Verantwortlicher Kommentare hinzufügt]**: Wählen Sie diese Option, um Kommentare für die Aufgabe zu aktivieren. Eine beauftragte Person kann die Kommentare innerhalb des AEM-Posteingangs zum Zeitpunkt der Aufgabenübermittlung hinzufügen.
* **[!UICONTROL Kommentar in Variable speichern]**: Speichern Sie den Kommentar in einer Variablen des Datentyps „Zeichenfolge“. Diese Option wird nur angezeigt, wenn Sie das Kontrollkästchen **[!UICONTROL Zulassen, dass Verantwortlicher Kommentare hinzufügt]** aktivieren.

* **[!UICONTROL Zulassen, dass Verantwortlicher der Aufgabe Anhänge hinzufügt]**: Wählen Sie diese Option, um Anhänge für die Aufgabe zu aktivieren. Eine beauftragte Person kann die Anhänge im AEM-Posteingang zum Zeitpunkt der Aufgabenübermittlung hinzufügen. Sie können auch die maximale Größe **[!UICONTROL (Maximale Dateigröße)]** eines Anhangs begrenzen. Der Standardwert lautet 2 MB.

* **[!UICONTROL Ausgabe-Aufgabenanlagen mit den folgenden Optionen speichern]**: Geben Sie den Speicherort des Anhangsordners an. Sie können Ausgabeaufgabenanhänge mit einem Pfad relativ zur Nutzlast oder in einer Variablen eines Arrays des Datentyps „Dokument“ speichern. Diese Option wird nur angezeigt, wenn Sie das Kontrollkästchen **[!UICONTROL Zulassen, dass Verantwortlicher der Aufgabe Anhänge hinzufügt]** aktivieren und **[!UICONTROL Adaptives Formular]**, **[!UICONTROL Schreibgeschütztes adaptives Formular]** oder **[!UICONTROL Nicht interaktives PDF-Dokument]** aus der Dropdown-Liste **[!UICONTROL Typ]** in der Registerkarte **[!UICONTROL Formular/Dokument]** auswählen.

* **[!UICONTROL Benutzerdefinierte Metadaten verwenden]**: Wählen Sie diese Option, um das benutzerdefinierte Metadatenfeld zu aktivieren. Benutzerdefinierte Metadaten werden in E-Mail-Vorlagen verwendet.
* **[!UICONTROL Benutzerdefinierte Metadaten]**: Wählen Sie benutzerdefinierte Metadaten für die E-Mail-Vorlagen. Die benutzerdefinierten Metadaten sind im CRX-Repository unter apps/fd/dashboard/scripts/metadataScripts verfügbar. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Admin erstellt den Pfad, bevor dieser verwendet wird. Sie können auch einen Service für die benutzerdefinierten Metadaten verwenden. Sie können auch die Schnittstelle `WorkitemUserMetadataService` erweitern, um benutzerdefinierte Metadaten bereitzustellen.
* **[!UICONTROL Daten aus vorherigen Schritten anzeigen]**: Wählen Sie diese Option (falls verfügbar) aus, damit Verantwortliche frühere Verantwortlicher, bei der Aufgabe bereits vorgenommene Aktionen, Kommentare zu dieser Aufgabe und das Datensatzdokument der abgeschlossenen Aufgabe anzeigen können.
* **[!UICONTROL Daten aus allen nachfolgenden Schritten anzeigen]**: Wählen Sie diese Option aus, damit der aktuelle Verantwortliche durchgeführte Aktionen und Kommentare anzeigen kann, die von nachfolgenden Verantwortlichen zur Aufgabe hinzugefügt werden. Außerdem kann sich der aktuelle Verantwortliche ein Datensatzdokument der abgeschlossenen Aufgabe anzeigen lassen – sofern verfügbar.
* **[!UICONTROL Sichtbarkeit des Datentyps]**: Standardmäßig kann ein Verantwortlicher ein Datensatzdokument, Verantwortliche, durchgeführte Aktionen und Kommentare anzeigen, die frühere und nachfolgende Verantwortliche hinzugefügt haben. Verwenden Sie die Option „Sichtbarkeit des Datentyps“, um den Typ der für die Verantwortlichen sichtbaren Daten zu begrenzen.

>[!NOTE]
>
>Die Optionen zum Speichern des Schritts „Aufgabe zuweisen“ als Entwurf und zum Abrufen des Verlaufs des Schritts „Aufgabe zuweisen“ sind nicht verfügbar, wenn Sie ein AEM-Workflow-Modell für die externe Datenspeicherung konfigurieren. Außerdem ist die Option zum Speichern im Posteingang deaktiviert.

## Schritt „Nach PDF/A konvertieren“ {#convert-pdfa}

PDF/A ist ein Archivierungsformat für die langfristige Beibehaltung des Dokumentinhalts durch Einbetten der Schriftarten und Dekomprimieren der Datei. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Sie können den Schritt ***Nach PDF/A konvertieren*** in einem AEM-Workflow verwenden, um Ihre PDF-Dokumente in das PDF/A-Format zu konvertieren.

Der Schritt „In PDF/A konvertieren“ weist die folgenden Eigenschaften auf:

**[!UICONTROL Eingabedokument]**: Das Eingabedokument kann relativ zur Payload sein, einen absoluten Pfad haben, selbst Payload sein oder in einer Variablen des Datentyps „Dokument“ gespeichert sein.

**[!UICONTROL Konvertierungsoptionen]**: Mithilfe dieser Eigenschaft werden die Einstellungen zum Konvertieren von PDF-Dokumenten in PDF/A-Dokumente angegeben. Auf dieser Registerkarte stehen verschiedene Optionen zur Verfügung:

* **[!UICONTROL Compliance]**: Gibt den PDF/A-Standard an, mit dem die Ausgabe des PDF/A-Dokuments kompatibel sein muss. Es unterstützt verschiedene PDF-Standards wie PDF/A-1b, PDF/A-2b oder PDF/A-3b.
* **[!UICONTROL Ergebnisebene]**: Gibt das Ergebnisniveau als „PassFail“, „Zusammenfassung“ oder „Detailliert“ für die Konversionsausgabe an.
* **[!UICONTROL Farbraum]**: Gibt den vordefinierten Farbraum als S_RGB, COATED_FOGRA27, JAPAN_COLOR_COATED oder SWOP an, der für PDF/A-Ausgabedateien verwendet werden kann.
* **[!UICONTROL Optionaler Inhalt]**: Zulassen, dass bestimmte Grafikobjekte und/oder Anmerkungen nur dann im Ausgabedokument von PDF/A sichtbar sind, wenn ein bestimmter Kriteriensatz erfüllt ist.

**[!UICONTROL Ausgabedokumente]**: Gibt den Speicherort für die Ausgabedatei an. Die Ausgabedatei kann an einem Speicherort gespeichert werden, der relativ zur Nutzlast ist, die Nutzlast überschreibt, wenn es sich bei der Nutzlast um eine Datei handelt, oder in einer Variablen des Dokumentdatentyps.


## Schritt „E-Mail senden“ {#send-email-step}

Verwenden Sie den Schritt „E-Mail senden“, um eine E-Mail zu senden, z. B. mit einem Datensatzdokument, einem Link zu einem adaptiven Formular <!-- , link of an interactive communication--> oder einem angehängten PDF-Dokument. Der Schritt „E-Mail senden“ unterstützt [HTML-E-Mail](https://en.wikipedia.org/wiki/HTML_email). HTML-E-Mails sind responsiv und passen sich an den E-Mail-Client und die Bildschirmgröße der Empfängerinnen und Empfänger an. Sie können eine HTML-E-Mail-Vorlage verwenden, um das Erscheinungsbild, das Farbschema und das Verhalten der E-Mail zu definieren.

Beim E-Mail-Schritt wird der Day CQ Mail Service zum Senden von E-Mails verwenden. Bevor Sie den E-Mail-Schritt verwenden, stellen Sie sicher, dass der E-Mail-Service konfiguriert wurde. E-Mail unterstützt standardmäßig nur HTTP- und HTTPS-Protokolle. [Kontaktieren Sie das Supportteam](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=de#sending-email), um Ports für den Versand von E-Mails und das SMTP-Protokoll für Ihre Umgebung zu aktivieren. Mit dieser Einschränkung kann die Sicherheit der Plattform verbessert werden.

Der E-Mail-Schritt hat folgende Eigenschaften:

**[!UICONTROL Titel]**: Der Titel des Schritts hilft beim Identifizieren des Schritts im Workflow-Editor.

**[!UICONTROL Beschreibung]**: Erläuterungen können für andere Prozessentwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

**[!UICONTROL E-Mail-Betreff]**: Der Betreff kann aus Workflow-Metadaten abgerufen, manuell angegeben oder aus dem in einer Variablen gespeicherten Wert abgerufen werden. Zur Auswahl stehen:

* **[!UICONTROL Literal]** – Geben Sie den Betreff manuell an.
* **[!UICONTROL Aus Workflow-Metadaten abrufen]** – Sie können den Betreff von einer Metadateneigenschaft abrufen.
* **[!UICONTROL Variable]** – Sie können den Betreff aus dem Wert abrufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist.

**[!UICONTROL HTML-E-Mail-Vorlage]**: HTML-Vorlage für die E-Mail. Sie können Variablen in einer E-Mail-Vorlage spezifizieren. Der E-Mail-Schritt extrahiert und zeigt alle Variablen an, die in einer Vorlage für Eingaben enthalten sind.

**[!UICONTROL E-Mail-Vorlagen-Metadaten]**: Der Wert der E-Mail-Vorlagenvariablen kann ein benutzerspezifizierter Wert, der Pfad eines Assets auf dem Autoren- oder Veröffentlichungsserver, ein Bild oder eine Workflow-Metadateneigenschaft sein.

* **[!UICONTROL Literal]**: Verwenden Sie diese Option, wenn Sie den genauen zu spezifizierenden Wert kennen. Beispiel: [beispiel@beispiel.com](mailto:example@example.com).

* **[!UICONTROL Workflow-Metadaten]**: Verwenden Sie diese Option, wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird. Geben Sie nach Auswahl der Option den Namen der Metadateneigenschaft in das leere Textfeld unter der Option „Workflow-Metadaten“ ein. Beispiel: e-mailAdresse.

<!-- 

* **[!UICONTROL Asset URL]**: Use the option to embed a web link of an interactive communication to the email. After selecting the option, browse and choose the interactive communication to embed. The asset can reside on the author or the publish server. 

-->

* **[!UICONTROL Bild]**: Verwenden Sie diese Option, um ein Bild in die E-Mail einzubetten. Nachdem Sie die Option ausgewählt haben, suchen Sie nach dem entsprechenden Bild und wählen Sie es aus. Die Bildoption ist nur für die Bild-Tags (&lt;img src=&quot;&#42;&quot;/>) verfügbar, die auch in der E-Mail-Vorlage vorhanden sind.

**[!UICONTROL E-Mail-Adresse des Absenders/Empfängers]**: Wählen Sie die Option **[!UICONTROL Literal]**, um eine E-Mail-Adresse manuell anzugeben, oder wählen Sie die Option **[!UICONTROL Aus Workflow-Metadaten abrufen]**, um den Betreff aus einer Metadateneigenschaft abzurufen. Sie können auch eine Liste von Metadateneigenschaften-Arrays für die Option **[!UICONTROL Aus Workflow-Metadaten abrufen]** angeben. Wählen Sie die Option **[!UICONTROL Variable]** aus, um die E-Mail-Adresse aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist.

* **[!UICONTROL Dateianhang]**: Das am angegebenen Speicherort verfügbare Asset wird an die E-Mail angehängt. Der Pfad des Assets kann relativ zur Payload oder zum absoluten Pfad sein. Ein Beispielpfad ist [Payload_Directory]/attachments/.

Wählen Sie die Option **[!UICONTROL Variable]**, um den in einer Variablen des Datentyps „Dokument“, XML oder JSON gespeicherte Dateianhang abzurufen.

**[!UICONTROL Dateiname]**: Name der E-Mail-Anhangsdatei. Der E-Mail-Schritt ändert den Originaldateinamen des Anhangs in den angegebenen Dateinamen. Der Name kann manuell angegeben oder aus einer Workflow-Metadateneigenschaft oder einer Variable abgerufen werden. Verwenden Sie die Option **[!UICONTROL Literal]**, wenn Sie den genauen zu spezifizierenden Wert kennen. Verwenden Sie die Option **[!UICONTROL Variable]**, um den Dateinamen aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist. Verwenden Sie die Option **[!UICONTROL Aus Workflow-Metadaten abrufen]**, wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird.

## Schritt „Datensatzdokument generieren“ {#generate-document-of-record-step}

Wenn ein Formular ausgefüllt oder übermittelt wird, können Sie das Formular drucken oder als Dokument speichern. Dies wird als Datensatzdokument (DoR) bezeichnet. Sie können den Schritt „Datensatzdokument generieren“ verwenden, um eine schreibgeschützte oder interaktive PDF-Version eines adaptiven Formulars zu erstellen. Die PDF-Version enthält Informationen, die zusammen mit dem Layout des adaptiven Formulars in das Formular eingegeben werden.

Der Schritt „Datensatzdokument generieren“ hat folgende Eigenschaften:

**[!UICONTROL Adaptives Formular verwenden]**: Geben Sie die Methode zum Suchen des adaptiven Eingabeformulars an. Sie können das adaptive Formular verwenden, das an den Workflow übermittelt wurde, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Datentyps „Zeichenfolge“ verwenden, um den Pfad im Feld **[!UICONTROL Variable zur Auflösung auswählen]** anzugeben.\
Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie ein adaptives Formular zur Laufzeit mit den verfügbaren Eingabemethoden angeben.

**[!UICONTROL Pfad des adaptiven Formulars]**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie die Option **[!UICONTROL Unter einem absoluten Pfad verfügbar]** im Feld **[!UICONTROL Adaptives Formular verwenden]** auswählen.

**[!UICONTROL Eingabedaten auswählen mit]**: Pfad der Eingabedaten für das adaptive Formular. Sie können die Daten an einem Speicherort relativ zur Payload speichern, einen absoluten Pfad der Daten angeben oder Daten abrufen, die in einer Variablen des Datentyps „Dokument“, JSON oder XML gespeichert sind. Die Eingabedaten werden mit dem adaptiven Formular zusammengeführt, um ein Datensatzdokument zu erstellen.

**[!UICONTROL Pfad für Eingabeanhang auswählen mit]**: Pfad der Anhänge. Diese Anhänge sind im Datensatzdokument enthalten. Sie können die Anhänge an einem Speicherort relativ zur Payload speichern, einen absoluten Pfad der Anhänge angeben oder Anhänge abrufen, die in einer Variablen des Datentyps „Dokument“ gespeichert sind.

Wenn Sie den Pfad eines Ordners angeben, z. B. Anhänge, werden alle Dateien, die direkt im Ordner verfügbar sind, an das Datensatzdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die im angegebenen Pfad für den Anhang direkt verfügbar sind, werden die Dateien im Datensatzdokument als Anhänge aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.

**[!UICONTROL Generiertes Datensatzdokument mithilfe nachstehender Optionen speichern]**: Geben Sie den Speicherort für ein Datensatzdokument an. Sie können den Payload-Ordner überschreiben oder das Datensatzdokument an einem Speicherort im Payload-Verzeichnis ablegen oder es in einer Variablen des Datentyps „Dokument“ speichern.

**[!UICONTROL Gebietsschema]**: Geben Sie die Sprache des Datensatzdokuments an. Wählen Sie **[!UICONTROL Literal]** aus, um das Gebietsschema aus einer Dropdown-Liste auszuwählen, oder wählen Sie **[!UICONTROL Variable]**, um das Gebietsschema aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist. Definieren Sie den Gebietsschema-Code und speichern Sie den Wert für das Gebietsschema in einer Variablen. Geben Sie beispielsweise **en_US** für Englisch und **fr_FR** für Französisch an.

## Schritt „DDX aufrufen“ {#invokeddx}

Dokumentbeschreibungs-XML (DDX) ist eine deklarative Auszeichnungssprache, deren Elemente Dokumentbausteine darstellen. Diese Bausteine umfassen PDF-Seiten, XDP-Dokumente sowie andere Elemente wie Kommentare, Lesezeichen und formatierten Text. DDX definiert eine Reihe von Vorgängen, die auf ein oder mehrere Eingabedokumente angewendet werden können, um ein oder mehrere Ausgabedokumente zu generieren. Eine einzelne DDX kann mit einer Reihe von Quelldokumenten verwendet werden. Sie können in einem AEM-Workflow den ***DDX-Schritt aufrufen***, um verschiedene Vorgänge wie Zusammenstellen/Aufteilen von Dokumenten oder Erstellen und Ändern von Acrobat und XFA Forms und andere auszuführen, die in der [DDX-Referenzdokumentation](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) beschrieben werden.

„DDX-Schritt aufrufen“ hat die folgenden Eigenschaften:

**[!UICONTROL Eingabedokumente]**: Wird zum Festlegen von Eigenschaften eines Eingabedokuments verwendet. Auf dieser Registerkarte stehen verschiedene Optionen zur Verfügung:

* **[!UICONTROL Verwendung von DDX festlegen]**: Gibt das Eingabedokument relativ zur Payload an, hat einen absoluten Pfad, kann als Payload bereitgestellt oder in einer Variablen des Dokumentdatentyps gespeichert werden.
* **[!UICONTROL Zuordnung aus Payload erstellen]**: Ist diese Option ausgewählt, werden alle Dokumente im Payload-Ordner zur Zuordnung des Eingabedokuments für das Aufrufen der API im Assembler hinzugefügt. Der Knotenname für jedes Dokument wird als Schlüssel in der Zuordnung verwendet.
* **[!UICONTROL Zuordnung des Eingabedokuments]**: Diese Option wird verwendet, um mit der Schaltfläche **[!UICONTROL HINZUFÜGEN]** mehrere Einträge hinzuzufügen. Jeder Eintrag stellt den Schlüssel des Dokuments in der Zuordnung und die Quelle des Dokuments dar.

**[!UICONTROL Umgebungsoptionen]**: Diese Option wird verwendet, um Verarbeitungseinstellungen für den API-Aufruf festzulegen. Auf dieser Registerkarte stehen verschiedene Optionen zur Verfügung:

* **[!UICONTROL Nur validieren]**: Prüft die Gültigkeit des Eingabe-DDX-Dokuments.
* **[!UICONTROL Fehlschlagen bei Fehler]**: Boolescher Wert, der angibt, ob der Aufruf des API-Dienstes bei einem Fehler fehlschlägt oder nicht. Standardmäßig ist dieser Wert auf „False“ festgelegt.
* **[!UICONTROL Erste Bates-Zahl]**: Gibt die Zahl an, die sich selbstständig erhöht. Diese selbstständig inkrementierende Zahl wird automatisch auf jeder aufeinander folgenden Seite angezeigt.
* **[!UICONTROL Standardstil]**: Legt den Standardstil für die Ausgabedatei fest.

>[!NOTE]
>
>Umgebungsoptionen werden mit HTTP-APIs synchronisiert.

**[!UICONTROL Ausgabedokumente]**: Gibt den Speicherort für die Ausgabedatei an. Auf dieser Registerkarte stehen verschiedene Optionen zur Verfügung:

* **[!UICONTROL Ausgabe in Payload speichern]**: Speichert Ausgabedokumente unter dem Payload-Ordner oder überschreibt die Payload, falls die Payload eine Datei ist.
* **[!UICONTROL Zuordnung des Ausgabedokuments]**: Gibt explizit den Speicherort an, unter dem jede Dokumentdatei gespeichert werden soll, indem ein Eintrag pro Dokument hinzugefügt wird. Jeder Eintrag stellt das Dokument und den Speicherort dar, an dem es gespeichert werden soll. Wenn mehrere Ausgabedokumente vorhanden sind, wird diese Option verwendet.

## Schritt „Formulardatenmodell(FDM)-Dienst aufrufen“ {#invoke-form-data-model-service-step}

Sie können [[!DNL AEM Forms] -Datenintegration](data-integration.md) verwenden, um unterschiedliche Datenquellen zu konfigurieren und Verbindungen zu ihnen herzustellen. Diese Datenquellen können ein Webservice, ein REST-Service, ein OData-Service und eine CRM-Lösung sein. Mit der [!DNL AEM Forms]-Datenintegration können Sie ein Formulardatenmodell (FDM) erstellen, das verschiedene Dienste umfasst, um Vorgänge zum Abrufen, Hinzufügen und Aktualisieren von Daten in der konfigurierten Datenbank durchzuführen. Sie können den **[!UICONTROL Schritt „Formulardatenmodell-Service aufrufen“]** verwenden, um ein Formulardatenmodell (FDM) zu wählen und die Services des FDM verwenden, um Daten aus unterschiedlichen Datenquellen abzurufen, sie zu aktualisieren oder hinzuzufügen.

Um die Eingaben für die Felder des Schritts zu erläutern, werden die folgende Datenbanktabelle und JSON-Datei als Beispiel verwendet:

**[!UICONTROL Beispiel-Tabelle mit CustomerDetails]**

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Wert<br /> </td> 
  </tr> 
  <tr> 
   <td>Vorname<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Nachname</td> 
   <td>Rose</td> 
  </tr> 
  <tr> 
   <td>Kunden-ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>E-Mail-Adresse<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**[!UICONTROL JSON-Beispieldatei]**

```json
  { 
    customer: { 
     firstName: "Sarah", 
     lastName:"Rose", 
     customerId: "1", 
     emailAddress:"srose@we.info" 
   }, 
    insurance: {
     customerId: "1", 
    policyType: "Premium,
    policyNumber: "Premium-521499",
    customerDetails: { 
     firstName: "Sarah",
     lastName: "Rose",
     customerId: "1",
     emailAddress: "srose@we.info" 
    }
   }
  }
```

Der Schritt „Formulardatenmodell(FDM)-Dienst aufrufen“ enthält folgende Felder zum Vereinfachen von Formulardatenmodell(FDM)-Vorgängen:

* **[!UICONTROL Titel:]** Titel des Schrittes. Dies erleichtert die Identifizierung dieses Schritts im Workflow-Editor.
* **[!UICONTROL Beschreibung]**: Erläuterungen können für andere Prozessentwickelnde nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **[!UICONTROL Pfad für Formulardatenmodell]**: Suchen Sie nach einem Formulardatenmodell (FDM) auf dem Server und wählen Sie es aus.

* **[!UICONTROL Fehler und Validierungen]**: Mit dieser Option können Sie Fehlermeldungen erfassen und Validierungsoptionen für abgerufene und an Datenquellen gesendete Daten festlegen. Mit diesen Änderungen können Sie sicherstellen, dass die an den Schritt „Formulardatenmodell(FDM)-Dienst aufrufen“ übergebenen Daten den von der Datenquelle definierten Datenbegrenzungen entsprechen. Weitere Informationen finden Sie unter [Automatisierte Validierung von Eingabedaten](work-with-form-data-model.md#automated-validation-of-input-data)

* **[!UICONTROL Validierungsstufe]**: Es gibt drei Kategorien von Validierungen: Einfach, Vollständig und AUS:

   * Vollständig: Alle Begrenzungen werden validiert.
   * Einfach: Nur erforderliche und löschbare Begrenzungen.
   * AUS: Es findet keine Validierung statt.

* **[!UICONTROL Workflow bei Fehler beenden]**: Wenn eine Begrenzung nicht validiert werden kann, wird der Workflow gestoppt.

* **[!UICONTROL Fehler-Code in Variable speichern]**: Sie können einen Fehlercode in einer [Variable vom Typ „Zeichenfolge“](variable-in-aem-workflows.md) speichern.

* **[!UICONTROL Fehlermeldung in Variable speichern]**: Sie können eine Fehlermeldung in einer [Variablen vom Typ „Zeichenfolge“](variable-in-aem-workflows.md) speichern.

* **[!UICONTROL Fehlerdetails in Variable speichern]**: Sie können Fehlerdetails in einer [Variablen vom Typ ](variable-in-aem-workflows.md)JSON speichern.

* **[!UICONTROL Dienst]**: Liste der Dienste, die durch das ausgewählte Formulardatenmodell (FDM) bereitgestellt werden.
* **[!UICONTROL Eingabe für Services]** > **[!UICONTROL Bereitstellung von Eingabedaten mit Literal, Variable oder Workflow-Metadaten und einer JSON-Datei]**: Ein Service kann mehrere Argumente aufweisen. Wählen Sie die Option zum Abrufen des Werts der Service-Parameter aus einer Workflow-Metadateneigenschaft, einem JSON-Objekt oder einer Variable aus oder geben Sie den Wert direkt in das bereitgestellte Textfeld ein:

   * **[!UICONTROL Literal]**: Verwenden Sie diese Option, wenn Sie den genauen zu spezifizierenden Wert kennen. Beispiel: srose@we.info.
   * **[!UICONTROL Variable]**: Verwenden Sie die Option, um den in einer Variablen gespeicherten Wert abzurufen.
   * **[!UICONTROL Aus Workflow-Metadaten abrufen]**: Verwenden Sie diese Option, wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird. Beispiel: e-mailAdresse.

   * **[!UICONTROL Relativ zur Nutzlast]**: Verwenden Sie die Option zum Abrufen des Dateianhangs, der in einem Pfad relativ zur Payload gespeichert ist. Wählen Sie die Option aus und geben Sie entweder den Ordnernamen an, der den Dateianhang enthält, oder geben Sie den Dateinamen für den Anhang im Textfeld an.

     >[!NOTE]
     >
     > Der Workflow-Schritt **Formulardatenmodell aufrufen** unterstützt Workflow-seitige Metadaten für Base64-kodierte Anlagen-Arrays in [SharePoint-Listenbasierten Formulardatenmodellen](/help/forms/connect-forms-to-sharepoint-list.md) und ermöglicht es Workflows, Metadaten wie Dateinamen, MIME-Typ oder benutzerdefinierte Eigenschaften für die Anlagen zu übergeben, zu speichern und abzurufen.
     > ![SP-Listenanhänge](/help/edge/docs/forms/assets/workflow-sp-list.png)
     >
     > Der Ordner Relativ zur Payload enthält einen Dateianhang am `attachment` Speicherort. Geben Sie `attachment` im Textfeld an, nachdem Sie die Option **[!UICONTROL Relativ zur Payload]** ausgewählt haben.

   * **[!UICONTROL JSON Dot Notation]**: Verwenden Sie die Option, wenn der zu verwendende Wert in einer JSON-Datei enthalten ist. Beispiel: Insurance.customerDetails.emailAddress. Die Option „JSON Dot Notation“ ist nur verfügbar, wenn Zuordnungseingabefelder aus der Eingabe-JSON-Option ausgewählt sind.
   * **[!UICONTROL Zuordnen von Eingabefeldern aus Eingabe-JSON]**: Geben Sie den Pfad einer JSON-Datei an, um den Eingabewert einiger Dienstargumente aus der JSON-Datei abzurufen. Der Pfad der JSON-Datei kann relativ zur Payload bzw. zu einem absoluten Pfad sein oder Sie können ein JSON-Eingabedokument mit einer Variablen vom Typ JSON oder Formulardatenmodell (FDM) auswählen.

* **[!UICONTROL Eingabe für Dienste]** > **[!UICONTROL Eingabedaten mithilfe einer Variablen oder einer JSON-Datei bereitstellen]**: Wählen Sie diese Option, um Werte für alle Argumente aus einer JSON-Datei abzurufen, die unter einem absoluten Pfad, einem Pfad relativ zur Nutzlast oder in einer Variablen gespeichert wurde.
* **[!UICONTROL Auswahl des Eingabe-JSON-Dokuments mit]**: Die JSON-Datei, die Werte für alle Service-Argumente enthält. Der Pfad der JSON-Datei kann **[!UICONTROL relativ zur Nutzlast]** oder ein **[!UICONTROL absoluter Pfad]** sein. Sie können das JSON-Eingabedokument auch mit einer Variablen vom Datentyp „JSON“ oder „Formulardatenmodell (FDM)“ abrufen.

* **[!UICONTROL JSON Dot Notation]**: Lassen Sie das Feld leer, um alle Objekte der angegebenen JSON-Datei als Eingabe für Service-Argumente zu verwenden. Um ein bestimmtes JSON-Objekt aus der angegebenen JSON-Datei als Eingabe für Service-Argumente zu lesen, geben Sie die Dot Notation für das JSON-Objekt an, z. B. wenn Sie eine JSON ähnlich wie am Anfang des Abschnitts aufgeführt haben, geben Sie „insurance.customerDetails“ an, um alle Details eines Kunden als Eingabe für den Service anzugeben.
* **[!UICONTROL Ausgabe des Service]** > **[!UICONTROL Ausgabewerte zu Variablen oder Metadaten zuordnen und schreiben]**: Wählen Sie diese Option, um die Ausgabewerte als Eigenschaften des Metadatenknotens der Workflow-Instanz im CRX-Repository zu speichern. Geben Sie den Namen der Metadateneigenschaft an und wählen Sie das entsprechende Dienstausgabeattribut aus, das der Metadateneigenschaft zugeordnet werden soll, ordnen Sie z. B. die vom Output-Dienst zurückgegebene Telefonnummer mit der Eigenschaft phone_number den Workflow-Metadaten zu. In ähnlicher Weise können Sie die Ausgabe in einer Variablen vom Datentyp „Long“ speichern. Wenn Sie eine Eigenschaft für die Option **[!UICONTROL Zuzuordnendes Service-Ausgangsattribut]** auswählen, werden für die Option **[!UICONTROL Speichern der Ausgabe in]** nur Variablen ausgefüllt, die Daten der ausgewählten Eigenschaft speichern können.

* **[!UICONTROL Ausgabe des Diensts]** > **[!UICONTROL Ausgabe in Variable oder einer JSON-Datei speichern]**: Wählen Sie diese Option aus, um die Ausgabewerte in einer JSON-Datei unter einem absoluten Pfad, einem Pfad relativ zur Nutzlast oder in einer Variablen zu speichern.
* **[!UICONTROL Ausgabe-JSON-Dokument mithilfe folgender Optionen speichern]**: Speichern Sie die JSON-Ausgabedatei. Der Pfad der JSON-Ausgabedatei kann relativ zur Payload oder einem absoluten Pfad sein. Sie können die JSON-Ausgabedatei auch mit einer Variablen vom Datentyp „JSON“ oder „Formulardatenmodell (FDM)“ speichern.



## Schritt „Dokument signieren“ {#sign-document-step}

Mit dem Schritt „Dokument signieren“ können Sie [!DNL Adobe Sign] zum Signieren von Dokumenten verwenden. Wenn Sie zum Signieren eines adaptiven Formulars den Workflow-Schritt [!DNL Adobe Sign] verwenden, kann das Formular je nach Konfiguration des Workflow-Schritts nacheinander an die einzelnen Empfängerinnen und Empfänger weitergeleitet werden oder gleichzeitig an alle gesendet werden. Adaptive Formulare für [!DNL Adobe Sign] werden erst dann an den Experience Manager Forms-Server weitergeleitet, nachdem alle Empfängerinnen und Empfänger den Unterzeichnungsvorgang abgeschlossen haben.

Standardmäßig überprüfen die [!DNL Adobe Sign]-Planungs-Services die Empfängerreaktionen alle 24 Stunden. Sie können [das Standardintervall für Ihre Umgebung ändern](adobe-sign-integration-adaptive-forms.md#for-aem-workflows-only-configure-dnl-adobe-acrobat-sign-scheduler-to-sync-the-signing-status-configure-adobe-sign-scheduler-to-sync-the-signing-status).

Der Schritt „Dokument signieren“ hat folgende Eigenschaften:

* **[!UICONTROL Name der Vereinbarung]**: Geben Sie den Titel der Vereinbarung an. Der Name der Vereinbarung wird Teil des Betreffs und des Textkörpers der E-Mail, die an die Unterzeichner gesendet wird. Sie können den Namen entweder in einer Variablen des Datentyps „Zeichenfolge“ speichern oder **[!UICONTROL Literal]** auswählen, um den Namen manuell hinzuzufügen.

* **[!UICONTROL Gebietsschema]**: Geben Sie die Sprache für die E-Mail- und Verifizierungsoptionen an. Sie können das Gebietsschema entweder in einer Variablen des Datentyps „Zeichenfolge“ speichern oder **[!UICONTROL Literal]** auswählen, um das Gebietsschema aus der Liste der verfügbaren Optionen auszuwählen. Sie müssen den Gebietsschema-Code definieren, während Sie den Wert für das Gebietsschema in einer Variablen speichern. Geben Sie beispielsweise **[!UICONTROL en_US]** für Englisch und **[!UICONTROL fr_FR]** für Französisch an.

* **[!UICONTROL Adobe Sign Cloud-Konfiguration]**: Wählen Sie eine [!DNL Adobe Sign] Cloud-Konfiguration. Wenn Sie [!DNL Adobe Sign] nicht für [!DNL AEM Forms] konfiguriert haben, lesen Sie den Abschnitt [Integrieren von Adobe Sign mit [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

* **[!UICONTROL Zu signierendes Dokument auswählen mit]**: Sie können ein Dokument an einem Speicherort relativ zur Nutzlast auswählen, die Nutzlast als Dokument verwenden, einen absoluten Pfad für das Dokument angeben oder das Dokument abrufen, das in einer Variablen des Datentyps „Dokument“ gespeichert ist.
* **[!UICONTROL Tage bis Abgabetermin]**: Ein Dokument wird als „fällig“ (Abgabetermin erreicht) gekennzeichnet, nachdem für die im Feld **[!UICONTROL Tage bis Abgabetermin]** angegebene Anzahl von Tagen keine Aktivität für die Aufgabe ermittelt wurde. Die Anzahl der Tage wird gezählt, nachdem die Dokumentation einer Benutzerin bzw. einem Benutzer zum Signieren zugewiesen wurde.
* **[!UICONTROL Häufigkeit der E-Mail-Erinnerung]**: Sie können eine Erinnerungs-E-Mail in täglichem oder wöchentlichem Abstand senden. Die Woche wird ab dem Tag gezählt, an dem die Dokumentation einer Benutzerin bzw. einem Benutzer zum Signieren zugewiesen wurde.
* **[!UICONTROL Signaturvorgang]**: Sie können wählen, ob ein Dokument in einer sequenziellen oder parallelen Reihenfolge signiert werden soll. Bei sequenzieller Reihenfolge erhält jeweils nur ein Unterzeichner das Formular zur Unterzeichnung. Nachdem die erste Unterzeichnungsperson das Signieren des Dokuments abgeschlossen hat, wird das Dokument an die zweite gesendet usw. Bei paralleler Reihenfolge können mehrere Unterzeichner ein Formular gleichzeitig signieren.
* **[!UICONTROL Umleitungs-URL]**: Geben Sie eine Umleitungs-URL an. Nachdem das Dokument signiert wurde, können Sie den Verantwortlichen an eine URL umleiten. Normalerweise enthält diese URL eine Dankesnachricht oder weitere Anweisungen.
* **[!UICONTROL Workflow-Schritt]**: Ein Workflow kann mehrere Schritte umfassen. Diese werden im AEM-Posteingang angezeigt. Sie können diese Phasen in den Eigenschaften des Modells definieren (**[!UICONTROL Sidekick]** > **[!UICONTROL Seite]** > **[!UICONTROL Seiteneigenschaften]** > **[!UICONTROL Phasen]**).
* **[!UICONTROL Empfänger auswählen]**: Geben Sie die Methode zum Auswählen von Empfängerinnen und Empfängern für das Dokument an. Sie können den Workflow Benutzenden oder Gruppen dynamisch zuweisen oder manuell Details zu Empfängerinnen oder Empfängern hinzufügen. Wenn Sie in der Dropdown-Liste „Manuell“ auswählen, fügen Sie Empfängerdetails wie E-Mail, Rolle und Authentifizierungsmethode hinzu.

  >[!NOTE]
  >
  >* Im Abschnitt „Rolle“ können Sie die Empfängerrolle als Unterzeichnungsperson, genehmigende Person, akzeptierende Person, zertifizierte Empfangsperson, ausfüllende Person des Formulars und delegierende Person festlegen.
  >* Wenn Sie für die Option „Rolle“ eine delegierende Person auswählen, kann diese Person die Unterzeichnungsaufgabe anderen Empfängerinnen oder Empfängern zuweisen.
  >* Wenn Sie eine Authentifizierungsmethode für [!DNL Adobe Sign] konfiguriert haben, wählen Sie je nach ausgewählter Konfiguration eine Authentifizierungsmethode wie telefonbasierte Authentifizierung, auf sozialer Identität basierende Authentifizierung, wissensbasierte Authentifizierung oder auf behördlicher Identität basierende Authentifizierung aus.

* **[!UICONTROL Skript oder Dienst zur Auswahl von Empfängern]**: Die Option ist nur verfügbar, wenn im Feld „Empfänger auswählen“ die Option „Dynamisch“ ausgewählt ist. Sie können ein ECMAScript oder einen Service angeben, um Unterzeichnungspersonen und Verifizierungsoptionen für ein Dokument auszuwählen.
* **[!UICONTROL Empfängerdetails]**: Die Option ist nur verfügbar, wenn im Feld „Empfänger auswählen“ die Option „Manuell“ ausgewählt ist. Geben Sie eine E-Mail-Adresse an und wählen Sie einen optionalen Verifizierungsmechanismus aus. Bevor Sie einen Zwei-Schritt-Verifizierungsmechanismus auswählen, vergewissern Sie sich, dass die entsprechende Verifizierungsoption für das konfigurierte [!DNL Adobe Sign]-Konto aktiviert ist. Sie können eine Variable des Datentyps „Zeichenfolge“ verwenden, um Werte für die Felder „E-Mail“, „Ländercode“ und „Telefonnummer“ zu definieren. Die Felder „Ländercode“ und „Telefonnummer“ werden nur angezeigt, wenn Sie in der Dropdown-Liste „Bestätigung in zwei Schritten“ die Option „Telefonüberprüfung“ auswählen.
* **[!UICONTROL Signiertes Dokument]**: Sie können den Status des signierten Dokuments in einer Variablen speichern. Um Ihrem signierten Dokument ein Audit-Protokoll für elektronische Signaturen hinzuzufügen und so mehr Sicherheit und Rechtmäßigkeit zu gewährleisten, können Sie den Audit-Bericht einbinden. Sie können das signierte Dokument mit der Variablen oder dem Ordner „Payload“ speichern.

  >[!NOTE]
  >
  > Der Audit-Bericht wird der letzten Seite des signierten Dokuments angefügt.

<!--
## Document Services steps {#document-services-steps}

AEM Document services are a set of services for creating, assembling, and securing PDF Documents. [!DNL AEM Forms] provides a separate AEM Workflow step for each document service.

Similar to other [!DNL AEM Forms] workflow steps, such as Assign Task, Send Email, and Sign Document, you can use variables in all AEM Document services steps. For more information on creating and managing variables, see [Variables in AEM workflows](variable-in-aem-workflows.md).
 
### Apply Document Time Stamp step {#apply-document-time-stamp-step}

Add time stamp to a document. You provide document details such as input document path, input document name, location to store exported data. You may choose to overwrite existing payload file, choose a different file name to store data in a different file under payload folder, provide an absolute path to the data, or store data in a variable of Document data type.

### Convert to image step {#convert-to-image-step}

Converts a PDF document to list of images. Supported image formats are JPEG, JPEG2000, PNG, and TIFF. The following information applies to conversions to TIFF images:

* A multi-page TIFF file is generated.
* Some annotations are not included in TIFF images. Annotations that require Acrobat to generate their appearance are not included.

### Convert to PDF/A step {#convert-to-pdf-a-step}

Converts a PDF document to PDF/A format using the options provided. The PDF/A version of Portable Document Format (PDF) is specialized for archiving and long-term preservation of documents.

### Convert to PS step {#convert-to-ps-step}

Convert PDF documents to PostScript. When converting to PostScript, you can use the conversion operation to specify the source document and whether to convert to PostScript level 2 or 3. The PDF document you convert to a PostScript file must be non-interactive.

### Create PDF from specified type step {#create-pdf-from-specified-type-step}

Generate a PDF document from an input file. The input document can be relative to the payload, have an absolute path, can be payload itself, or stored in a variable of Document data type.

### Create PDF from URL/HTML/ZIP step {#create-pdf-from-url-html-zip-step}

Generates a PDF document from supplied URL, HTML, and ZIP file.

### Export Data step {#export-data-step}

Exports data from a PDF forms or XDP file. It requires you to enter the file path of Input Document and the Export Data Format. The options for Export Data Format are Auto, XDP and XmlData.

### Export PDF to specified type step {#export-pdf-to-specified-type-step}

Converts a PDF document to a selected format.

### Generate Non-Interactive PDF step {#generatenoninteractive}

Generate a Non-Interactive PDF. It provides various customization options.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Import Data step {#import-data-step}

Merges form data into a PDF form. You can import form data into a PDF form.

### Invoke DDX step {#invokeddx}

Executes the DDX file on the specified map of input documents and returns the manipulated PDF documents.

>[!NOTE]
>
>You can use variables to specify the DDX file for input documents. Store the DDX file in a variable of Document or XML data type.

### Optimize PDF step {#optimize-pdf-step}

Optimizes PDF files by reducing their size. The result of this conversion is PDF files that may be smaller than their original versions. This operation also converts PDF documents to the PDF version specified in the optimization parameters.

Optimization settings specify how files are optimized. Here are example settings:

* Target PDF version
* Discarding objects such as JavaScript actions and embedded page thumbnails
* Discarding user data such as comments and file attachments
* Discarding invalid or unused settings
* Compressing uncompressed data or using more efficient compression algorithms
* Removing embedded fonts
* Setting transparency values

### Render PDF Form step {#renderpdf}

Renders a form created in Form Designer (XDP) to a PDF form.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Secure Document step {#secure-document-step}

Encrypt, Sign, and certify a document. [!DNL AEM Forms] supports both password based and certificate base encryption. You can also choose between various algorithms for signing documents. For example, SHA-256 and SH-512. You can also use the workflow step to reader extend PDF documents. The workflow step provides option to enable barcode decoding, digital signatures, import and export of PDF data, and other options.

### Send to Printer step {#send-to-printer-step}

Send a document directly to a printer. It supports the following printing access mechanisms:

* **[!UICONTROL Direct accessible printer]**: A printer that is installed on the same computer is called a direct accessible printer, and the computer is named printer host. This type of printer can be a local printer that is connected to the computer directly.
* **[!UICONTROL Indirect accessible printer]**: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX&reg; printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server's IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.
    -->

## Generieren des Schritts für die gedruckte Ausgabe {#generatePrintedOutput}

Dieser Schritt generiert eine PCL-, PostScript-, ZPL-, IPL-, TPCL- oder DPL-Ausgabe aus einem Formularentwurf und einer Datendatei. Die Datendatei wird mit dem Formularentwurf zusammengeführt und für den Druck formatiert. Die von diesem Schritt generierte Ausgabe kann direkt an einen Drucker gesendet oder als Datei gespeichert werden. Es wird empfohlen, diesen Schritt zu verwenden, wenn Sie Formularentwürfe oder Daten aus einer Anwendung verwenden möchten. Wenn sich Ihre Formularentwürfe im Netzwerk, im lokalen Dateisystem oder einem HTTP-Speicherort befinden, verwenden Sie den Vorgang „generatePrintedOutput“.

Beispielsweise erfordert Ihre Anwendung, dass Sie einen Formularentwurf mit einer Datendatei zusammenführen. Die Daten enthalten Hunderte von Einträgen. Darüber hinaus muss die Ausgabe an einen Drucker gesendet werden, der ZPL unterstützt. Der Formularentwurf und Ihre Eingabedaten befinden sich in einer Anwendung. Verwenden Sie den Vorgang „generatePrintedOutput“, um jeden Eintrag mit einem Formularentwurf zusammenzuführen und die Ausgabe an einen Drucker zu senden, der ZPL unterstützt.

Der Schritt „Gedruckte Ausgabe generieren“ hat die folgenden Eigenschaften:

**[!UICONTROL Eingabeeigenschaften]**

* **[!UICONTROL Vorlagendatei auswählen mit]**: Geben Sie den Pfad der Vorlagendatei an. Sie können die Vorlagendatei auswählen, indem Sie den Pfad relativ zur Nutzlast, einen absoluten Pfad oder eine Variable vom Datentyp „Document“ verwenden. Beispiel: [Payload_Directory]/Workflow/data.xml. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet. Darüber hinaus können Sie auch die Payload als Eingabedatendatei akzeptieren.

* **[!UICONTROL Datendokument auswählen mit]**: Geben Sie den Pfad einer Eingabedatendatei an. Sie können die Eingabedatendatei auswählen, indem Sie den Pfad relativ zum Payload, einen absoluten Pfad oder eine Variable vom Datentyp „Document“ verwenden. Beispiel: [Payload_Directory]/Workflow/data.xml. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet.

* **[!UICONTROL Druckerformat]**: Ein Druckformatwert, der beim Fehlen einer XDC-Datei die zu verwendende Sprache der Seitenbeschreibung angibt, um den Ausgabe-Stream zu generieren. Wenn Sie einen Literalwert angeben, wählen Sie einen der folgenden Werte:

   * **[!UICONTROL Farbe PCL]**: Verwenden Sie diese Option, um eine XDC-Datei für PCL anzugeben.
   * **[!UICONTROL Generisches PostScript]**: Verwenden Sie diese Option, um eine generische XDC-Datei für PostScript zu spezifizieren.
   * **[!UICONTROL ZPL 300 DPI]**: Verwenden Sie ZPL mit 300 DPI. Die Datei zpl300.xdc wird verwendet.
   * **[!UICONTROL ZPL 600 DPI]**: Verwenden Sie ZPL mit 600 DPI. Die Datei zpl600.xdc wird verwendet.
   * **[!UICONTROL IPL 300 DPI]**: Verwenden Sie IPL mit 300 DPI. Die Datei ipl300.xdc wird verwendet.
   * **[!UICONTROL IPL 400 DPI]**: Verwenden Sie IPL mit 400 DPI. Die Datei ipl400.xdc wird verwendet.
   * **[!UICONTROL TPCL 600 DPI]**: Verwenden Sie TPCL mit 600 dpi. Die Datei tpcl600.xdc wird verwendet.
   * **[!UICONTROL Einfaches PostScript]**: Verwenden Sie diese Option, um eine reine Text-XDC-Datei für PostScript zu spezifizieren.
   * **[!UICONTROL DPL300DPI]**: Verwenden Sie DPL mit 300 dpi. Die Datei dpl300.xdc wird verwendet.
   * **[!UICONTROL DPL400DPI]**: Verwenden Sie DPL mit 400 dpi. Die Datei dpl400.xdc wird verwendet.
   * **[!UICONTROL DPL600DPI]**: Verwenden Sie DPL mit 600 DPI. Die Datei dpl600.xdc wird verwendet.
   * **[!UICONTROL HP_PCL_5e]**: Verwenden Sie die Option, um mehrere Canon-Geräte zu unterstützen.


**[!UICONTROL Ausgabeeigenschaften]**

* **[!UICONTROL Ausgabedokument speichern mit]**: Geben Sie den Speicherort für die Ausgabedatei an. Sie können die Ausgabedatei an einem Speicherort speichern, der relativ zum Payload ist, in einer Variablen oder einen absoluten Speicherort angeben, um die Ausgabedatei zu speichern. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet.

**[!UICONTROL Erweiterte Eigenschaften]**

* **[!UICONTROL Speicherort des Inhaltsstamms auswählen mit]**: Der Inhaltsstamm ist ein Zeichenfolgenwert, der den URI, den absoluten Verweis oder den Speicherort im Repository angibt, um relative Elemente abzurufen, die vom Formularentwurf verwendet werden. Wenn der Formularentwurf zum Beispiel auf ein Bild verweist, das relativ ist, wie `../myImage.gif`, muss `myImage.gif` auf `repository://` liegen. Der Standardwert ist `repository://`, was auf die Stammebene des Repositorys verweist.

  Wenn Sie ein Asset aus Ihrer Anwendung auswählen, muss der Pfad des Inhaltsstamm-URI die richtige Struktur aufweisen. Wenn beispielsweise ein Formular aus einer Anwendung namens SampleApp ausgewählt und unter `SampleApp/1.0/forms/Test.xdp` gespeichert wird, muss der Inhaltsstamm-URI als `repository://administrator@password/Applications/SampleApp/1.0/forms/` bzw. `repository:/Applications/SampleApp/1.0/forms/` (wenn die Berechtigung „null“ ist) angegeben werden. Wenn der Inhaltsstamm-URI auf diese Weise angegeben wird, werden die Pfade aller referenzierten Elemente im Formular für diesen URI aufgelöst.

* **[!UICONTROL XCI-Datei auswählen mit]**: XCI-Dateien werden verwendet, um Schriftarten und andere Eigenschaften zu beschreiben, die für Formularentwurfselemente verwendet werden. Sie können eine XCI-Datei relativ zur Payload, in einem absoluten Pfad oder mithilfe einer Variablen des Datentyps „Document“ beibehalten.

* **[!UICONTROL Gebietsschema]**: Legt die Sprache fest, die zum Generieren des PDF-Dokuments verwendet wird. Wenn Sie einen Literalwert angeben, wählen Sie eine Sprache aus der Liste oder einen der folgenden Werte:
   * **[!UICONTROL Server-Standard verwenden]**:
(Standard) Verwenden Sie die auf dem Server [!DNL AEM Forms] konfigurierte Gebietsschema-Einstellung. Die Einstellung „Gebietsschema“ wird mit der Administrationskonsole konfiguriert. (Weitere Informationen finden Sie in der [Designer-Hilfe](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/using-designer.pdf).)

   * **[!UICONTROL So verwenden Sie einen benutzerdefinierten Wert]**: 
Geben Sie den Gebietsschema-Code in das Feld „Literal“ ein oder wählen Sie eine Zeichenfolgenvariable aus, die den Gebietsschema-Code enthält. Eine vollständige Liste der unterstützten Gebietsschemata finden Sie unter https://docs.oracle.com/javase/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Kopien]**: Ein ganzzahliger Wert, der die Anzahl der Kopien angibt, die für die Ausgabe generiert werden. Der Standardwert ist 1.

* **[!UICONTROL Duplexdruck]**: Ein Paginierungswert, der angibt, ob zweiseitiger oder einseitiger Druck verwendet werden soll. Drucker, die PostScript und PCL unterstützen, verwenden diesen Wert. Wenn Sie einen Literalwert angeben, wählen Sie einen der folgenden Werte:
   * **[!UICONTROL Duplex, lange Kante]**: Verwenden Sie den zweiseitiger Druck und die Paginierung erfolgt an langen Kanten.
   * **[!UICONTROL Duplex, kurze Kante]**: Verwenden Sie den zweiseitigen Druck mit Paginierung an kurzen Kanten.
   * **[!UICONTROL Simplex]**: Verwenden Sie den einseitigen Druck.

## Schritt „Nicht interaktive PDF-Ausgabe generieren“ {#generatePDFdocuments}

1. Ziehen Sie den Workflow „Nicht-interaktive PDF-Ausgabe generieren“ unter die Registerkarte „Forms Workflow“ per Drag-and-Drop in den Sidekick.
1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Komponente bearbeiten“ Eingabedokumente, Ausgabedokumente und zusätzliche Parameter und klicken Sie auf **[!UICONTROL OK]**.

### Eingabedokumente {#input-documents-3}

* **Vorlagendatei**: Gibt den Speicherort der XDP-Vorlage an. Dies ist ein Pflichtfeld.

* **Datendokument**: Gibt den Speicherort der Daten-XML an, die mit der Vorlage zusammengeführt werden muss.

### Ausgabedokument {#output-document}

**Ausgabedokument**: Gibt den Namen des generierten PDF-Formulars an.

### Zusätzliche Parameter {#additional-parameters-1}

* **Inhaltsstamm**: Gibt den Pfad zum Ordner im Repository an, in dem in der Eingabe-XDP-Vorlage verwendete Fragmente oder Bilder gespeichert werden.
* **Gebietsschema**: Gibt das Standardgebietsschema für das generierte PDF-Formular an.
* **Acrobat-Version**: Gibt die Acrobat-Zielversion für das generierte PDF-Formular an.
* **Linearisierte PDF**: Gibt an, ob die generierte PDF-Datei für die Ansicht im Web optimiert werden soll.
* **PDF mit Tags**: Gibt an, ob die generierte PDF-Datei barrierefrei gemacht werden soll.
* **XCI-Dokument**: Gibt den Pfad zur XCI-Datei an.

## Siehe auch {#see-also}

* [Variablen in formularzentrierten AEM-Workflows](/help/forms/variable-in-aem-workflows.md)
* [Konfigurieren von Abwesenheitseinstellungen](/help/forms/configure-out-of-office-settings.md)

<!--

>[!MORELIKETHIS]
>
>* [Forms-centric workflow on OSGi](/help/forms/aem-forms-workflow.md)
>* [Use AEM translation workflow to localize Adaptive Forms and Document of Record](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms.md)

-->