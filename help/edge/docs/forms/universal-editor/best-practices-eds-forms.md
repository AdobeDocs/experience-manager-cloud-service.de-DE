---
title: Best Practices für die Entwicklung von Forms mit hoher Leistung
description: Erfahren Sie mehr über die wichtigsten Best Practices für die Erstellung benutzerfreundlicher, barrierefreier und leistungsstarker Formulare mit AEM Forms. Verbessern Sie die Datenqualität, das Benutzererlebnis und die Erfolgsraten bei der Übermittlung.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: 67b6873b-bb93-4d38-963c-2ca65a1a644b
source-git-commit: 37b20a97942f381b46ce36a6a3f72ac019bba5b7
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 1%

---

# Best Practices für die Erstellung von Forms

## Überblick

Die Erstellung effektiver Formulare geht über die technische Implementierung hinaus. Sie erfordert ein Verständnis der Benutzerpsychologie, der Standards für die Barrierefreiheit und der Leistungsoptimierung. Dieses umfassende Handbuch enthält bewährte Best Practices für die Entwicklung von Formularen, die Benutzende tatsächlich ausfüllen möchten.

### Lerninhalte

Am Ende dieses Dokuments erfahren Sie, wie Sie:

* Entwerfen Sie benutzerfreundliche und barrierefreie Formulare, die für alle funktionieren
* Optimieren der Formularleistung und der Ladezeiten
* Verantwortungsvoller und transparenter Umgang mit Benutzerdaten
* Implementieren einer ordnungsgemäßen Fehlerbehandlung und -validierung
* Erstellen von Formularen mit hohen Abschlussraten

### Zielgruppe

Dieses Handbuch wurde für folgende Zwecke entwickelt:

* **Formularentwickler** die bessere Benutzererlebnisse schaffen möchten
* **Entwickler** Implementieren der Formularfunktion
* **UX-Experten** Optimieren von Formular-Workflows
* **Stakeholder** die versuchen, die Konversionsraten von Formularen zu verbessern

### Grundprinzipien

Die besten Formulare folgen diesen Grundprinzipien:

1. **Benutzerzentriertes Design** - Konzentrieren Sie sich darauf, was Benutzer erreichen müssen
2. **Barrierefreiheit zuerst** - Stellen Sie sicher, dass jeder Ihre Formulare verwenden kann
3. **Leistungsoptimierung** - Schnelle Formulare werden häufiger ausgefüllt
4. **Datenverantwortung** - Respektieren Sie die Privatsphäre der Benutzer und minimieren Sie die Datenerfassung
5. **Klare Kommunikation** - Führen Sie Benutzer reibungslos durch den Prozess

Der Bau großartiger Formen geht über die Technologie hinaus. So stellen Sie sicher, dass Ihre Formulare benutzerfreundlich sind und ihre Ziele erreichen:

## Entwerfen einer benutzerfreundlichen und zugänglichen Forms

* **Klare, sichtbare Kennzeichnungen verwenden** Jedes Formularfeld benötigt eine `<label>`. Verlassen Sie sich nicht nur auf Platzhaltertext (Text innerhalb des Eingabefelds), da dieser verschwindet, wenn Benutzende eingeben, und die Barrierefreiheit beeinträchtigt.
   * *Gut:* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
   * *Schlecht:* `<input type="email" placeholder="Email Address">`
* **Einfach halten:** Verwenden Sie nach Möglichkeit standardmäßige HTML-Eingabetypen (`<input type="date">`, `<input type="tel">`). Häufig verfügen sie über eine bessere Unterstützung für Mobilgeräte und bessere Barrierefreiheit als komplexe benutzerdefinierte Widgets.
* **Logische Reihenfolge und Gruppierung** Ordnen Sie die Felder in einer für den Benutzer sinnvollen Weise an. Gruppieren Sie verwandte Felder mithilfe von `<fieldset>` und `<legend>`.
* **Übersichtliche Anweisungen bereitstellen** Bieten Sie für alle Felder, die verwirrend sein könnten, knappen Hilfetext oder QuickInfos an.
* **Tastaturnavigation:** Sie sicher, dass Benutzende nur mit der Tastatur (Tabulatortaste, Umschalt+Tabulatortaste, Eingabetaste, Leertaste) durch das gesamte Formular navigieren können.
* **Fehlerbehandlung:** Fehler offensichtlich und leicht zu korrigieren. Zeigen Sie Fehlermeldungen neben dem entsprechenden Feld an und erklären Sie, was behoben werden muss.

* **Sicherstellen, dass Ihre Forms schnell geladen und sichtbar sind**

   * **Forms hervorheben:** Wenn ein Formular wichtig ist, stellen Sie sicher, dass Benutzende es leicht sehen können, ohne zu viel zu scrollen (möglichst „über der Falte„). Adobes Forschung zeigt, dass viele Formen wenig interagieren, weil sie versteckt sind.
   * **Assets optimieren** Halten Sie benutzerdefinierte JavaScript- oder CSS-Dateien für Ihre Formulare so klein wie möglich, um schnelle Ladezeiten zu gewährleisten. Edge Delivery Services hilft beim Laden der Basisseiten, aber umfangreiche Formularskripte können die Geschwindigkeit noch weiter verringern.

* **Verantwortungsvoller Umgang mit Benutzerdaten**
   * **Fragen Sie nur, was Sie benötigen** Je weniger personenbezogene Daten (PII) Sie anfordern, desto besser. Jedes Feld ist ein potenzieller Grund für einen Benutzer, das Formular zu verlassen.
   * **Seien Sie transparent:** Erklären Sie *warum* Sie bestimmte Informationen und *wie sie verwendet werden*. Link zu Ihrer Datenschutzrichtlinie. Dies schafft Vertrauen.

* **Verbessern des Benutzererlebnisses: CAPTCHA-Alternativen**

   * **Sichtbare Captchas überdenken:** Die Tests „Geben Sie den welligen Text ein“ oder „Klicken Sie auf alle Ampeln“ können für Benutzer, insbesondere Menschen mit Behinderungen, sehr frustrierend sein und häufig zu hohen Abbruchraten führen.

* **Alternativen in Betracht ziehen:**
   * **Honeypot-Felder**: Fügen Sie ein ausgeblendetes Feld hinzu, das nur Bots ausfüllen würden. Wenn sie Daten enthält, ist die Übermittlung wahrscheinlich Spam.
   * **Zeitbasierte Prüfungen:** Messen, wie schnell ein Formular übermittelt wird. Zu schnelle Einreichungen sind oft Bots.
   * **Unsichtbares reCAPTCHA (v3):** Dieser Google-Service analysiert das Benutzerverhalten im Hintergrund und stellt nur dann eine Herausforderung dar, wenn der Benutzer verdächtig erscheint. Dies ist oft ein viel besseres Benutzererlebnis.

## Aufgaben und Aufgaben des Formularentwurfs

| ✅ tun - für eine bessere Forms | ❌ nicht - Vermeiden Sie diese |
|----------------------------------------------------------------------|------------------------------------------------------------------|
| Sichtbare `<label>`-Tags für alle Felder verwenden | Verwenden Sie nur Platzhaltertext anstelle von ordnungsgemäßen Beschriftungen |
| Standardmäßige HTML-Eingabetypen (z. B. `<input type="email">`) bevorzugen | Übermäßig komplexe benutzerdefinierte Widgets verwenden |
| Sicherstellen der vollständigen Tastaturnavigation | Geben Sie vage oder fehlende Fehlermeldungen an. |
| Klare, umsetzbare Fehlermeldungen anzeigen | Übermäßige personenbezogene Daten ohne Begründung anfordern |
| Nur nach notwendigen Informationen fragen | Verwenden schwer zu lösender sichtbarer CAPTCHAs |
| Erläuterung der Verwendung von Daten (Datenschutzinformationen oder Links) | Formular tief in der Seite ausblenden |
| Verwenden von unsichtbaren oder verhaltensbezogenen CAPTCHA-Techniken |                                                                  |
| Formular auf der Seite leicht auffindbar machen (hervorgehobene Platzierung) |                                                                  |


## Nächste Schritte

Dieses Handbuch bietet einen Überblick über die Verwendung von Formularen mit AEM Edge Delivery Services. Detailliertere schrittweise Anleitungen zu bestimmten Konfigurationen finden Sie in der offiziellen Adobe Experience Manager-Dokumentation:

* [Dokumentenbasiertes Authoring mit Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Universeller Editor mit Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Dokumenterstellung (Document Authoring, DA) und Einbetten von Inhalten](https://www.aem.live/developer/da-tutorial)
* [AEM Forms-Sendedienst](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
