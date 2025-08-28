---
title: Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung
description: Erfahren Sie, wie Sie Dankesseiten und Umleitungen für den Formularbaustein konfigurieren, um das Anwendererlebnis zu optimieren und die Journey der Benutzenden zu optimieren.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: ht
source-wordcount: '557'
ht-degree: 100%

---

# Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung

Nachdem Benutzende ein Formular abgesendet haben, ist es entscheidend, ihnen durch eine Dankesnachricht ein nahtloses Erlebnis zu bieten. Dies bestätigt nicht nur die erfolgreiche Übermittlung, sondern verbessert zudem die Zufriedenheit der Benutzenden und führt sie weiter auf ihrer Journey.

- **Dankesnachricht**: Eine Dankesnachricht ist ein Eckpfeiler des Anwendererlebnisses, indem sie eine Rückversicherung bietet, wichtige Informationen vermittelt und gleichzeitig die Markenidentität stärkt. Sie dient als direkte Bestätigung der Aktion der Benutzenden und gibt ihnen das Gefühl, etwas geschafft zu haben, ein Gefühl von Zufriedenheit.

- **Umleitung**: Eine Umleitung spielt eine zentrale Rolle dabei, Benutzende zu relevanten Zielen zu steuern, die Interaktion zu optimieren und letztendlich Konversionsraten zu steigern. Durch eine Umleitung, die Benutzende nahtlos zum nächsten Schritt in der Journey führt, wird ein reibungsloses Navigationserlebnis sichergestellt. Ein Beispiel dafür ist die Weiterleitung einer Person zur Zahlungsseite, nachdem die ersten Details erfasst wurden.

Standardmäßig verhält sich der adaptive Formularbaustein so, dass bei der Übermittlung die folgende Dankesnachricht angezeigt wird. Die Nachricht wird nach erfolgreicher Übermittlung des Formulars oben im Formular angezeigt.

![Standardmäßige Dankesnachricht](/help/edge/assets/thank-you-message.png)

Sie haben jedoch die Flexibilität, dieses Erlebnis an Ihre individuellen Anforderungen anzupassen. Sie haben unter anderem folgende Möglichkeiten:

- Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung
- Umleiten von Benutzenden zu einer anderen Seite nach der Übermittlung zur Durchführung weiterer Aktionen

>[!NOTE]
>
> In der folgenden [Abfragetabelle](/help/edge/docs/forms/assets/enquiry.xlsx) finden Sie Informationen zum Anpassen der Dankesnachricht an Ihre Anforderungen.

## Konfigurieren einer benutzerdefinierten Dankesnachricht

Wenn Sie nach erfolgreicher Übermittlung des Formulars eine personalisierte Dankesnachricht anzeigen möchten, können Sie Ihre Tabelle so konfigurieren, dass diese angezeigt wird.

Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte Dankesnachricht für Ihren adaptiven Formularbaustein zu konfigurieren:

1. Wechseln Sie in Microsoft SharePoint oder Google Workspace zum Projektordner „Edge Delivery“ und öffnen Sie die Tabelle.
1. Fügen Sie in der Spalte `value` eine benutzerdefinierte Dankesnachricht für den Feldtyp `submit` in der Tabelle hinzu.

   ![Benutzerdefinierte Dankesnachricht](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   Fügen Sie beispielsweise für den Feldtyp `submit` die Meldung `Submission Successful!` in die Spalte `value` ein.

1. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Benutzerdefinierte Dankesnachricht](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## Umleiten von Benutzenden zu einer anderen Seite nach der Übermittlung

Wenn Benutzende nach der Formularübermittlung zu einer anderen Seite umgeleitet werden, kann dies das Anwendererlebnis verbessern, indem relevante Informationen bereitgestellt, Aktionen bestätigt und Benutzende zu gewünschten Ergebnissen angeleitet werden. Beispiel:

- Nachdem eine Person ein Kaufformular ausgefüllt hat, wird sie auf eine Zahlungsseite umgeleitet, um die Transaktion sicher abzuschließen.
- Beim Senden eines Registrierungsformulars für eine Veranstaltung oder ein Webinar werden Benutzende auf eine Bestätigungsseite umgeleitet, auf der Details zu dem Ereignis, z. B. Datum, Uhrzeit und Ort, angezeigt werden.

Gehen Sie wie folgt vor, um Benutzende auf eine andere Seite weiterzuleiten:

1. Wechseln Sie in Microsoft SharePoint oder Google Workspace zum Projektordner „Edge Delivery“ und öffnen Sie die Tabelle.
1. Fügen Sie die URL in die Spalte `value` für den Feldtyp `submit` in der Tabelle ein, um Benutzende bei erfolgreicher Übermittlung des Formulars weiterzuleiten.
Um die Seite auf eine andere Seite umzuleiten, verwenden Sie die URL der Seite [Edge Delivery-Dokumentation](https://www.aem.live/docs/) 

   ![Umleitungs-URL für Dankesnachricht](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Umleitungs-Dankesnachricht](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

Sie können auch eine neue Dokumentdatei erstellen und ihre Vorschau-URL in die Spalte `value` für den Feldtyp `submit` einfügen.

Nachdem Benutzende ein Formular abgesendet haben, ist es wichtig, ihnen eine klare Dankesnachricht zu bieten. Sie bestätigt, dass die Übermittlung erfolgreich war, und steigert die Benutzerzufriedenheit.

