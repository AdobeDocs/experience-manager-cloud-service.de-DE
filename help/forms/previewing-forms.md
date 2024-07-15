---
title: Vorschau eines adaptiven Formulars
description: Benutzende können eine Vorschau des Formulars anzeigen, bevor es veröffentlicht oder aktiviert wird, um sicherzustellen, dass es den Erwartungen entspricht. Die Vorschauoptionen können je nach unterstützten Formulartypen variieren.
topic-tags: author
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 72235277-6c34-4341-9a10-02afa753e7f5
source-git-commit: 05548d56d791584781606b02839c5602b4469f7b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 100%

---

# Formularvorschau {#previewing-a-form}

## Übersicht {#overview}

In [!DNL AEM Forms] können Sie die Formulare und Dokumente im Repository in der Vorschau anzeigen. Die Vorschau zeigt genau, wie die Formulare aussehen und sich verhalten, wenn sie für die Endbenutzenden freigegeben werden.

Bei der Vorschau von Formularen werden diese in der interaktiven Benutzeroberfläche gerendert und die Benutzenden können die Formulare mit Daten ausfüllen. Bei der Vorschau von Dokumenten werden diese im nicht interaktiven Modus gerendert und die Benutzenden können nur das Dokument anzeigen. Für Formulare ist eine zusätzliche Option der benutzerdefinierten Vorschau verfügbar. Mit dieser Option können Sie eine Vorschau des Formulars mit Daten aus einer XML-Datei anzeigen. Die Daten füllen einige oder alle Felder des Formulars aus, das in der Vorschau angezeigt wird.

In der folgenden Tabelle sind die Vorschauoptionen aufgeführt, die für verschiedene Typen unterstützter Formulare verfügbar sind:

<table>
 <tbody>
  <tr>
   <td><strong>Asset-Typ</strong><br /> </td>
   <td><strong>Verfügbare Vorschauoptionen</strong><br /> </td>
  </tr>
  <!--<tr>
   <td>Document</td>
   <td>PDF preview</td>
  </tr>-->
  <tr>
   <td>PDF-Formular</td>
   <td>PDF-Vorschau und Vorschau mit Daten<br /> </td>
  </tr>
  <tr>
   <td>Adaptives Formular</td>
   <td>HTML-Vorschau und HTML-Vorschau mit Daten</td>
  </tr>
  <!--<tr>
   <td>Form Template</td>
   <td>PDF preview, PDF preview with Data, HTML preview, HTML preview with Data<br /> </td>
  </tr>-->
 </tbody>
</table>

## Formularvorschau {#previewing-a-form-1}

1. Wählen Sie ein Asset aus, das Sie in der Vorschau anzeigen möchten, und klicken Sie in der Symbolleiste „Aktionen“ auf „Vorschau“ ![aem6forms_preview](assets/aem6forms_preview.png).

   >[!NOTE]
   >
   >Um ein Asset auszuwählen, wechseln Sie aus der standardmäßigen Kartenansicht in die Listenansicht. Klicken Sie auf ![aem6forms_viewlist](assets/aem6forms_viewlist.png) oder ![aem6forms_viewcard](assets/aem6forms_viewcard.png), um die Ansichten zu wechseln.

1. Durch das Klicken auf „Vorschau“ werden die möglichen Vorschauoptionen aufgelistet, die für den ausgewählten Asset-Typ anwendbar sind. Klicken Sie auf die gewünschte Option, um das ausgewählte Asset in einer neuen Registerkarte zu rendern.

   Ihre Optionen sind:

   * Anzeigen als HTML-Vorschau
   * Vorschau mit Daten
     <!--* Preview as PDF (available for form templates)-->

## Vorschau mit Daten {#preview-with-data}

Wenn Sie **Vorschau mit Daten** auswählen, können Sie sehen, wie das Formular mit echten eingegebenen Daten aussieht.  Mit der Option „Vorschau mit Daten“ können Sie eine XML-Datei hochladen, die Beispielbenutzerdaten enthält. Die Beispielbenutzerdaten werden zum Ausfüllen des Vorschauformulars in dem von Ihnen ausgewählten Format verwendet.

1. Wählen Sie ein Asset aus, klicken Sie auf „Vorschau“ ![aem6forms_preview](assets/aem6forms_preview.png) und wählen Sie **Vorschau mit Daten** aus.
1. Geben Sie im Dialogfeld „Formularvorschau“ FormData als XML-Datei an. Klicken Sie auf „Vorschau“, um das Formular mit den zusammengeführten Daten aus der XML-Datei zu rendern.
