---
title: Anwenden elektronischer Signaturen auf ein Formular mithilfe der Freihandsignatur
seo-title: Apply electronic signatures to a form using scribble signatures
description: Signieren von Formularen mit Freihandsignaturen
seo-description: Signing forms using scribble
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 76d178d1-8e40-41b3-80d4-66b2f8d04211
docset: aem65
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
source-git-commit: 76f13cb4236b8c7eb515d647a1cede6fa2cf4799
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 73%

---

# Anwenden elektronischer Signaturen auf ein Formular mithilfe der Freihandsignatur {#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

Sie können die Komponente **Freihandsignatur** und **Signaturschritt** verwenden, um eine Signatur (per Freihanfunktion) in ein adaptives Formular zu schreiben. Die Komponente „Signaturschritt“ zeigt eine PDF-Version des adaptiven Formulars an. Sie benötigen ein Formular, bei dem die Option „Datensatzdokument“ aktiviert ist, oder auf Vorlagen basierende adaptive Formulare, um die Komponente „Signaturschritt“ zu verwenden.

![Dialogfeld für Freihandsignatur](assets/scribble-signature.png)

## Verschiedene Optionen im Signaturfenster verfügbar

* **A:** Klicken Sie auf **Pinsel** -Symbol, um Ihre Signatur auf der Arbeitsfläche zu zeichnen.
* **B:** Klicken Sie auf **Löschen** -Symbol, um die Signatur auf der Arbeitsfläche zu löschen.
* **C:** Klicken Sie auf **Geolocation** -Symbol, um die Geolocation zusammen mit der Signatur hinzuzufügen.
* **D:** Klicken Sie auf **Tastatur** -Symbol, um Ihren Namen auf der Arbeitsfläche einzugeben.

Sobald Sie auf Fertig tippen ![aem_forms_save](assets/aem_forms_save.png) im Scribble-Signaturfenster angezeigt, können Sie die Signatur nicht bearbeiten. Wenn Sie die Signatur bearbeiten möchten, müssen Sie die aktuelle Signatur ignorieren und mit der obigen Option &quot;Paint Brush/Keyboard&quot;erneut signieren.

Sie können auf die **Konfigurieren** ![](assets/configure.png) -Symbol, um das Seitenverhältnis der Arbeitsfläche für Scribble-Signaturen festzulegen.
* Wenn das Seitenverhältnis der Arbeitsfläche für Scribble-Signaturen kleiner als 1 ist, werden die Geolocation-Informationen am unteren Rand der Arbeitsfläche für Scribble-Signatur hinzugefügt.


* Wenn das Seitenverhältnis der Arbeitsfläche für Scribble-Signaturen größer als 1 ist, werden die Geolocation-Informationen auf der rechten Seite der Arbeitsfläche für Scribble-Signaturen hinzugefügt.


![Scribble signature-bottom](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>Signaturen werden immer im PNG-Format gespeichert.

## Konfigurieren eines adaptiven Formulars zur Verwendung der Freihandsignatur {#configure-an-adaptive-form-to-use-scribble-signature}

1. Erstellen Sie ein adaptives Formular, bei dem die Option „Datensatzdokument“ aktiviert ist oder das auf einer Formularvorlage basiert. Eine schrittweise Anleitung finden Sie unter [Erstellen eines adaptiven Formulars](creating-adaptive-form.md).
1. Ziehen Sie die Komponente **Freihandsignatur** aus dem Komponentenbrowser in das adaptive Formular.
1. Tippen Sie auf das Symbol **Konfigurieren** (![configure](assets/configure.png)). Dadurch wird der Eigenschaftenbrowser geöffnet und Eigenschaften der Komponente „Freihandsignatur“ angezeigt. Konfigurieren Sie die Eigenschaften der Komponente „Freihandsignatur“.
1. Ziehen Sie die Komponente „Signaturschritt“ aus dem Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.

   >[!NOTE]
   >
   >Die Komponente „Signaturschritt“ nimmt die gesamte für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Komponente „Signaturschritt“ enthält.

1. Tippen Sie im Inhaltsbrowser auf **Formularcontainer** und dann auf das Symbol **Konfigurieren** (![](assets/configure.png)). Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Containers für adaptive Formulare anzeigt. Navigieren Sie zu **Container für adaptive Formulare** > **Elektronische Signatur** und heben Sie die Auswahl der Option **Adobe Sign aktivieren** auf. Tippen Sie auf das Symbol Fertig ![aem_forms_save](assets/aem_forms_save.png), um die Änderungen zu speichern.

   >[!NOTE]
   >
   >Wenn Sie einem adaptiven Formular die Komponente „Signaturschritt“ hinzufügen, wird die Option „Adobe Sign aktivieren“ automatisch ausgewählt.

1. Tippen Sie auf das Symbol **Konfigurieren** (![configure](assets/configure.png)). Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Signaturschritts anzeigt. Konfigurieren Sie die folgenden Eigenschaften:

   * **Elementname**: Geben Sie den Namen der Komponente an.

   * **Titel:** Geben Sie den eindeutigen Titel der Komponente an.
   * **Vorlagennachricht**: Geben Sie die Nachricht an, die angezeigt werden soll, während das PDF-Signaturdokument geladen wird. Adobe Sign-Dienste benötigen einige Zeit, um das PDF-Signaturdokument vorzubereiten und zu laden.
   * **Signaturdienst**: Wählen Sie die Option **Freihandsignatur** aus.

   * **CSS-Klasse**: Geben Sie ggf. die CSS-Klasse der Client-Bibliothek an. Es wird empfohlen, anstelle der CSS-Klasse [Designs](themes.md) und [Inline-Stile](inline-style-adaptive-forms.md) zu verwenden.

   Tippen Sie auf das Symbol Fertig ![aem_forms_save](assets/aem_forms_save.png), um die Änderungen zu speichern. Die Signatur wurde erfolgreich konfiguriert.

   Wenn Sie jetzt ein Formular ausfüllen, wird eine PDF-Version des adaptiven Formulars angezeigt und es sind Optionen zum Signieren des PDF-Dokuments verfügbar. Weitere Informationen finden Sie unter [Signieren eines adaptiven Formulars mit Freihandsignatur](signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Signieren eines adaptiven Formulars mit Freihandsignatur {#sign-an-adaptive-form-using-scribble-signature}

1. Wenn Sie ein adaptives Formular ausgefüllt und die Signaturschrittseite erreicht haben, wird der Signaturbildschirm angezeigt.

   ![Signaturbildschirm für EchoSign-Seite](assets/esignscribblesign.jpg)

1. Klicken Sie auf **[!UICONTROL Signieren]**. Das Dialogfeld „Freihandsignatur“ wird angezeigt. Signieren Sie das Formular und klicken Sie auf das Symbol „Fertig“ ![aem_forms_save](assets/aem_forms_save.png), um die Signatur zu speichern.

   ![Dialogfeld für Freihandsignatur](assets/scribblewidget.png)

1. Klicken Sie auf „Abschließen“, um den Signiervorgang abzuschließen.

   ![Signiervorgang abschließen](assets/scribblecomplete.jpg)

Die Signaturen werden dem Formular hinzugefügt und die Formularsteuerung wechselt zum nächsten Bereich.
