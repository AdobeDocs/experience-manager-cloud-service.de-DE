---
title: Dankeseite für EDS Forms konfigurieren
description: Erfahren Sie, wie Sie Dankeseiten und Weiterleitungen für EDS Forms konfigurieren, um das Benutzererlebnis zu optimieren und die Journey der Benutzer zu optimieren.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: cadeccd916884ca2437e2b2684771c181cc8281e
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 1%

---


# Dankeseite oder Umleitungsformular nach der Übermittlung anzeigen

Nachdem ein Benutzer ein Formular gesendet hat, ist es entscheidend, ein nahtloses Erlebnis entweder über eine Dankeseite oder eine Umleitung bereitzustellen. Diese Elemente bestätigen nicht nur die erfolgreiche Übermittlung, sondern verbessern auch die Benutzerzufriedenheit und führen sie bei ihrer Journey weiter.

* **Danksagungsseite**: Eine Dankeseite ist ein Eckpfeiler der Benutzererfahrung, der Sicherheit bietet und wichtige Informationen vermittelt und gleichzeitig die Markenidentität stärkt. Es dient als direkte Anerkennung der Aktion des Benutzers und fördert ein Gefühl der Fertigstellung und Zufriedenheit.

* **Umleiten**: Eine Umleitung spielt eine zentrale Rolle bei der Lenkung der Benutzer zu relevanten Zielen, der Optimierung der Interaktion und letztendlich der Steigerung der Konversionsraten. Durch eine Umleitung, die Benutzer nahtlos zum nächsten Schritt im Journey führt, wird eine reibungslose Navigation gewährleistet. Beispielsweise die Umleitung des Benutzers zur Zahlungsseite nach der Erfassung anfänglicher Details.

Im Block Adaptive Forms wird standardmäßig eine Dankeseite angezeigt. Sie haben jedoch die Flexibilität, dieses Erlebnis an Ihre spezifischen Anforderungen anzupassen. Zu den Optionen gehören:

* [Konfigurieren der Dankeseite und -nachricht zur Anpassung an Ihre Marken- und Kommunikationsziele](#configuring-the-thank-you-page-and-message)
* [Weiterleiten von Benutzern zu einer anderen Seite nach der Übermittlung](#redirect-users-to-another-page-post-submission)die Journey weiter zu verbessern

## Konfigurieren der Dankeseite und -meldung

Das Standardverhalten des Bausteins Adaptive Forms besteht darin, bei der Übermittlung die Dankeseite anzuzeigen. Führen Sie die folgenden Schritte aus, um die Dankeseite für Ihren adaptiven Forms-Block zu konfigurieren:

1. Rufen Sie den Ordner AEM Edge-Bereitstellungsprojekt in Microsoft SharePoint oder Google Workspace auf.
1. Erstellen Sie in Ihrem Projektverzeichnis eine Microsoft Word- oder Google Docs-Datei mit dem Namen &quot;Danke&quot;.
1. Fügen Sie Ihre Dankesnachricht zur Datei &quot;Danke&quot; hinzu. </br>

   ![Beispiel-Dankeseite](/help/edge/assets/sample-thankyou-page.png)

1. Verwenden Sie AEM Sidekick, um die Datei &quot;Danke&quot; in der Vorschau anzuzeigen und zu veröffentlichen.

Ihr adaptiver Forms-Block zeigt die Dankeseite bei der Formularübermittlung an.

## Umleiten von Benutzern zu einer anderen Seite nach der Übermittlung

Standardmäßig leitet der Block Adaptive Forms die Benutzer zur &quot;Dankeseite&quot;weiter. Um Benutzer auf eine andere Seite als die standardmäßige &quot;Danksagungsseite&quot;umzuleiten, haben Sie zwei Optionen:

* entweder die vorhandene &quot;Danksagungsseite&quot;durch eine andere Seite ersetzen oder
* leitet die &quot;Danksagungsseite&quot; zu einer anderen Seite Ihrer Wahl weiter.

### Vorhandene &quot;Dankeseite&quot;ersetzen

1. Öffnen Sie &quot;[EDS-Projekt]/blocks/form/form.js&quot;zur Bearbeitung.
1. Ändern Sie die `thankyou` in der folgenden Zeile auf die gewünschte Seite klicken:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Beispiel:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'payment';
   ```

   >[!NOTE]
   >
   > Stellen Sie sicher, dass im Projektordner des Edge Delivery Service-Projekts in Microsoft SharePoint oder Google Workspace eine Seite mit demselben Namen vorhanden ist. Wenn die Seite nicht vorhanden ist, erstellen und veröffentlichen Sie sie.

1. Fahren Sie fort, um den aktualisierten Ordner &quot;form.js&quot;und die zugrunde liegenden Dateien in Ihr Edge Delivery Service-Projekt auf GitHub einzuchecken. Durch diese Aktualisierung wird sichergestellt, dass das Formular jetzt wie angegeben zur aktualisierten Seite weiterleitet.

1. Stellen Sie sicher, dass die Seite in Ihrem EDS-Projektordner vorhanden ist, und veröffentlichen Sie sie.


### Website-Umleitungen verwenden

Konfigurieren Sie eine Website-Umleitung, um die &quot;Danke&quot;-Seite auf eine andere Seite umzuleiten. Siehe Abschnitt [Umleitungs-Dokumentation](https://www.aem.live/docs/redirects) für detaillierte Anweisungen.

## Mehr anzeigen

* [Formularkomponenten](/help/edge/docs/forms/form-components.md)
* [Formularfeldeigenschaften](/help/edge/docs/forms/eds-form-field-properties)
* [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
* [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-eds-forms.md)
* [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
* [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)
