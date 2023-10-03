---
title: Vorschau eines adaptiven Formulars anzeigen
description: Benutzer können Formulare vor der Veröffentlichung oder Aktivierung in der Vorschau anzeigen, um sicherzustellen, dass sie die Erwartungen erfüllen. Die Vorschauoptionen können je nach unterstützten Formulartypen variieren.
uuid: 9ec359ea-f518-441c-9c3d-e3c1ea07a532
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
source-git-commit: 92f89243b79c6c2377db3ca2b8ea244957416626
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 33%

---


# Formularvorschau {#previewing-a-form}

## Übersicht {#overview}

In [!DNL AEM Forms] können Sie die Formulare und Dokumente im Repository in der Vorschau anzeigen. Die Vorschau zeigt genau, wie die Formulare aussehen und sich verhalten, wenn sie für die Endbenutzer freigegeben werden.

Bei der Vorschau von Formularen werden diese in der interaktiven Benutzeroberfläche wiedergegeben und der Benutzer kann die Formulare mit Daten ausfüllen. Bei der Vorschau von Dokumenten werden diese im nicht interaktiven Modus gerendert und der Benutzer kann nur das Dokument anzeigen. Für Formulare ist eine zusätzliche Option der benutzerdefinierten Vorschau verfügbar. Mit dieser Option können Sie eine Vorschau des Formulars mit Daten aus einer XML-Datei anzeigen. Die Daten füllen einige oder alle Felder des Formulars aus, das in der Vorschau angezeigt wird.

In der folgenden Tabelle sind die Vorschauoptionen aufgeführt, die für verschiedene Typen unterstützter Formulare verfügbar sind:

<table>
 <tbody>
  <tr>
   <td><strong>Asset-Typ</strong><br /> </td>
   <td><strong>Verfügbare Vorschauoptionen</strong><br /> </td>
  </tr>
  <tr>
   <td>Dokument</td>
   <td>PDF-Vorschau</td>
  </tr>
  <tr>
   <td>PDF-Formular</td>
   <td>PDF-Vorschau und Vorschau mit Daten<br /> </td>
  </tr>
  <tr>
   <td>Adaptives Formular</td>
   <td>HTML-Vorschau und HTML-Vorschau mit Daten</td>
  </tr>
  <tr>
   <td>Formularvorlage</td>
   <td>PDF-Vorschau, PDF-Vorschau mit Daten HTML-Vorschau, HTML-Vorschau mit Daten<br /> </td>
  </tr>
 </tbody>
</table>

## Formularvorschau {#previewing-a-form-1}

1. Wählen Sie ein Asset aus, das Sie in der Vorschau anzeigen möchten, und klicken Sie in der Symbolleiste „Aktionen“ auf „Vorschau“ ![aem6forms_preview](assets/aem6forms_preview.png).

   >[!NOTE]
   >
   >Um ein Asset auszuwählen, wechseln Sie aus der standardmäßigen Kartenansicht in die Listenansicht. Klicken Sie auf ![aem6forms_viewlist](assets/aem6forms_viewlist.png) oder ![aem6forms_viewcard](assets/aem6forms_viewcard.png), um die Ansichten zu wechseln.

1. Durch Klicken auf Vorschau werden die möglichen Vorschauoptionen aufgelistet, die für den ausgewählten Asset-Typ gelten. Klicken Sie auf die gewünschte Option, um das ausgewählte Asset in einer neuen Registerkarte anzuzeigen.

   Ihre Optionen sind:

   * Vorschau als HTML
   * Vorschau mit Daten
   * Vorschau als PDF (verfügbar für Formularvorlagen)

## Vorschau mit Daten {#preview-with-data}

Wenn Sie **Vorschau mit Daten** können Sie sehen, wie das Formular mit echten eingegebenen Daten aussieht. Mit der Option Vorschau mit Daten können Sie eine XML-Datei hochladen, die Beispielbenutzerdaten enthält. Die Beispielbenutzerdaten werden zum Ausfüllen des Vorschauformulars in dem von Ihnen ausgewählten Format verwendet.

1. Wählen Sie ein Asset aus, klicken Sie auf „Vorschau“ ![aem6forms_preview](assets/aem6forms_preview.png) und wählen Sie **Vorschau mit Daten** aus.
1. Geben Sie im Dialogfeld &quot;Formularvorschau&quot;FormData als XML-Datei an. Klicken Sie auf Vorschau , um das Formular mit den zusammengeführten Daten aus XML wiederzugeben.

