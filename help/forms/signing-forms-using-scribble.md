---
title: Wie wende ich elektronische Signaturen auf ein Formular mithilfe von Freihandsignaturen an?
description: Lernen Sie, wie man elektronische Signaturen auf ein Formular mithilfe einer Freihandsignatur anwendet.
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
source-git-commit: eaab351460363b83c7d3667e048235506cc71c41
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 89%

---

# E-Signieren eines Formulars mithilfe von Freihandsignaturen{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/signing-forms-using-scribble.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |


Sie können die Komponente **Freihandsignatur** und **Signaturschritt** verwenden, um eine Signatur (per Freihanfunktion) in ein adaptives Formular zu schreiben. Die Komponente „Signaturschritt“ zeigt eine PDF-Version des adaptiven Formulars an. Sie benötigen ein Formular, bei dem die Option „Datensatzdokument“ aktiviert ist, oder auf Vorlagen basierende adaptive Formulare, um die Komponente „Signaturschritt“ zu verwenden.

![Dialogfeld für Freihandsignatur](assets/scribble-signature.png)

## Verfügbare Optionen im Signaturfenster

* **A:** Klicken Sie auf das **Pinselsymbol**, um Ihre Signatur auf der Arbeitsfläche zu zeichnen.
* **B:** Klicken Sie auf das Symbol **Löschen**, um die Signatur auf der Arbeitsfläche zu löschen.
* **C:** Klicken Sie auf das Symbol **Geolocation**, um die Geolocation zusammen mit der Signatur hinzuzufügen.
* **D:** Klicken Sie auf das **Tastatursymbol**, um Ihren Namen auf der Arbeitsfläche einzugeben.

Nachdem Sie die Option Fertig ausgewählt haben ![aem_forms_save](assets/aem_forms_save.png) im Scribble-Signaturfenster angezeigt, können Sie die Signatur nicht bearbeiten. Wenn Sie die Signatur bearbeiten möchten, müssen Sie die aktuelle Signatur ignorieren und mit der obigen Option „Pinsel“/„Tastatur“ erneut signieren.

Sie können die **Konfigurieren** ![Symbol zum Konfigurieren](assets/configure.png) -Symbol, um das Seitenverhältnis der Arbeitsfläche für Scribble-Signaturen festzulegen.
* Wenn das Seitenverhältnis der Arbeitsfläche für Freihandsignaturen kleiner als 1 ist, werden die Geolocation-Informationen am unteren Rand der Arbeitsfläche für die Freihandsignatur hinzugefügt.


* Wenn das Seitenverhältnis der Arbeitsfläche für Freihandsignaturen größer als 1 ist, werden die Geolocation-Informationen auf der rechten Seite der Arbeitsfläche für Freihandsignaturen hinzugefügt.


![scribble signature-bottom](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>Signaturen werden immer im PNG-Format gespeichert.
>

## Konfigurieren eines adaptiven Formulars zur Verwendung der Freihandsignatur {#configure-an-adaptive-form-to-use-scribble-signature}

1. Erstellen Sie ein adaptives Formular, bei dem die Option „Datensatzdokument“ aktiviert ist oder das auf einer Formularvorlage basiert. Eine schrittweise Anleitung finden Sie unter [Erstellen eines adaptiven Formulars](creating-adaptive-form.md).
1. Ziehen Sie die Komponente **Freihandsignatur** aus dem Komponentenbrowser in das adaptive Formular.
1. Wählen Sie die **Konfigurieren** ![konfigurieren](assets/configure.png) Symbol. Dadurch wird der Eigenschaftenbrowser geöffnet und Eigenschaften der Komponente „Freihandsignatur“ angezeigt. Konfigurieren Sie die Eigenschaften der Komponente „Freihandsignatur“.
1. Ziehen Sie die Komponente „Signaturschritt“ aus dem Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.

   >[!NOTE]
   >
   >Die Komponente „Signaturschritt“ nimmt die gesamte für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Komponente „Signaturschritt“ enthält.

1. Wählen Sie im Inhaltsbrowser die Option **Formular-Container** und wählen Sie die **Konfigurieren** ![Symbol zum Konfigurieren](assets/configure.png) Symbol. Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Containers für adaptive Formulare anzeigt. Navigieren Sie zu **Container für adaptive Formulare** > **Elektronische Signatur** und heben Sie die Auswahl der Option **Adobe Sign aktivieren** auf. Wählen Sie Fertig aus ![aem_forms_save](assets/aem_forms_save.png) -Symbol, um die Änderungen zu speichern.

   >[!NOTE]
   >
   >Wenn Sie einem adaptiven Formular die Komponente „Signaturschritt“ hinzufügen, wird die Option „Adobe Sign aktivieren“ automatisch ausgewählt.

1. Wählen Sie die **Konfigurieren** ![konfigurieren](assets/configure.png) Symbol. Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Signaturschritts anzeigt. Konfigurieren Sie die folgenden Eigenschaften:

   * **Elementname**: Geben Sie den Namen der Komponente an.

   * **Titel**: Geben Sie den eindeutigen Titel der Komponente an.
   * **Vorlagennachricht**: Geben Sie die Nachricht an, die angezeigt werden soll, während das PDF-Signaturdokument geladen wird. Adobe Sign-Dienste benötigen einige Zeit, um das PDF-Signaturdokument vorzubereiten und zu laden.
   * **Signaturdienst**: Wählen Sie die Option **Freihandsignatur** aus.

   * **CSS-Klasse**: Geben Sie ggf. die CSS-Klasse der Client-Bibliothek an. Adobe empfiehlt, [Designs](themes.md) und [Inline-Stile](inline-style-adaptive-forms.md) anstelle der CSS-Klasse zu verwenden.

   Wählen Sie Fertig aus ![aem_forms_save](assets/aem_forms_save.png) -Symbol, um die Änderungen zu speichern. Die Signatur wurde erfolgreich konfiguriert.

   Wenn Sie jetzt ein Formular ausfüllen, wird eine PDF-Version des adaptiven Formulars angezeigt und es sind Optionen zum Signieren des PDF-Dokuments verfügbar. Weitere Informationen finden Sie unter [Signieren eines adaptiven Formulars mit Freihandsignatur](signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Signieren eines adaptiven Formulars mit Freihandsignatur {#sign-an-adaptive-form-using-scribble-signature}

1. Wenn Sie ein adaptives Formular ausgefüllt und die Signaturschrittseite erreicht haben, wird der Signaturbildschirm angezeigt.

   ![Signaturbildschirm für EchoSign-Seite](assets/esignscribblesign.jpg)

1. Klicken Sie auf **[!UICONTROL Signieren]**. Das Dialogfeld „Freihandsignatur“ wird angezeigt. Signieren Sie das Formular und klicken Sie auf das Symbol „Fertig“ ![aem_forms_save](assets/aem_forms_save.png), um die Signatur zu speichern.

   ![Dialogfeld für Freihandsignatur](assets/scribblewidget.png)

1. Klicken Sie auf „Abschließen“, um den Signiervorgang abzuschließen.

   ![Signiervorgang abschließen](assets/scribblecomplete.jpg)

Die Signaturen werden dem Formular hinzugefügt und die Formularsteuerung wechselt zum nächsten Bereich.

## Siehe auch {#see-also}

{{see-also}}