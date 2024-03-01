---
title: Dankeseite für EDS Forms konfigurieren
description: Erfahren Sie, wie Sie Dankeseiten und Weiterleitungen für EDS Forms konfigurieren, um das Benutzererlebnis zu optimieren und die Journey der Benutzer zu optimieren.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e2970c7a141025222c6b119787142e7c39d453af
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Konfigurieren von Dankeseiten und Weiterleitungen in adaptiven Forms-Blöcken

Dankeseiten und Umleitungen sind wichtige Aspekte der Verbesserung des Benutzererlebnisses, die Benutzern eine Bestätigung, klare Kommunikation und reibungslose Navigation nach der Formularübermittlung bieten.

## Konfigurieren von Dankeseiten

Dankeseiten dienen als beruhigende Bestätigung für Benutzer und ermöglichen es Unternehmen, wichtige Informationen zu kommunizieren und gleichzeitig die Markenidentität zu stärken. Führen Sie die folgenden Schritte aus, um eine Dankeseite für EDS Forms zu konfigurieren:

1. Rufen Sie den Ordner AEM Edge-Bereitstellungsprojekt in Microsoft SharePoint oder Google Workspace auf.
1. Erstellen Sie in Ihrem Projektverzeichnis eine Microsoft Word- oder Google Docs-Datei mit dem Namen &quot;Danke&quot;.
1. Fügen Sie Ihre Dankesnachricht zur Datei &quot;Danke&quot; hinzu.
   ![Beispiel-Dankeseite](/help/edge/assets/sample-thankyou-page.png)
1. Verwenden Sie AEM Sidekick, um die Datei &quot;Danke&quot; in der Vorschau anzuzeigen und zu veröffentlichen.

## Weiterleiten von Benutzern nach Übermittlung

Die Umleitung erleichtert nahtlose Journey, indem sie Benutzer zu relevanten Zielen führt, die Interaktion optimiert und die Konversionsraten erhöht.

Standardmäßig leitet der Block Adaptive Forms die Benutzer zur &quot;Dankeseite&quot;weiter. Um Benutzer auf eine andere Seite als die standardmäßige &quot;Danksagungsseite&quot;umzuleiten, haben Sie zwei Optionen:

* entweder die vorhandene Dankeseite durch eine andere Seite ersetzen oder
* leitet die &quot;Danksagungsseite&quot; zu einer anderen Seite Ihrer Wahl weiter.

### Ersetzen Sie die vorhandene &quot;Danksagungsseite&quot;

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


