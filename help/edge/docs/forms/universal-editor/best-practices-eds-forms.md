---
title: Best Practices für die Gestaltung von leistungsstarken Formularen
description: Erfahren Sie mehr über die wichtigsten Best Practices für die Erstellung nutzungsfreundlicher, barrierefreier und leistungsstarker Formulare mit AEM Forms. Verbessern Sie die Datenqualität, das Kundenerlebnis und die Erfolgsraten bei der Übermittlung.
feature: Edge Delivery Services
role: Admin, Developer
hide: true
hidefromtoc: true
exl-id: 67b6873b-bb93-4d38-963c-2ca65a1a644b
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 100%

---

# Best Practices zum Erstellen von Formularen

## Überblick

Die Erstellung effektiver Formulare geht über die technische Implementierung hinaus. Sie erfordert ein Verständnis der Benutzerpsychologie, der Standards für die Barrierefreiheit und der Leistungsoptimierung. Dieses umfassende Handbuch enthält bewährte Best Practices für die Entwicklung von Formularen, die Benutzende gerne ausfüllen möchten.

### Lerninhalte

Am Ende dieses Dokuments werden Sie Folgendes beherrschen:

- Erstellen benutzerfreundlicher und barrierefreier Formulare für alle
- Optimieren der Formularleistung und der Ladezeiten
- Verantwortungsvoller und transparenter Umgang mit Benutzerdaten
- Implementieren einer ordnungsgemäßen Fehlerbehandlung und -validierung
- Erstellen von Formularen mit hohen Abschlussraten

### Zielgruppe

Dieses Handbuch wurde für folgende Rollen entwickelt:

- **Formular-Designerinnen und -Designer**, die bessere Benutzererlebnisse erstellen möchten
- **Entwicklungs-Fachleute**, die Formularfunktionen implementieren
- **UX-Fachleute**, die Formular-Workflows optimieren
- **Stakeholder**, die die Konversionsraten von Formularen verbessern möchten

### Grundlegende Prinzipien

Die besten Formulare folgen diesen Grundprinzipien:

1. **Benutzerzentriertes Design** – Konzentrieren Sie sich darauf, was Benutzende erreichen möchten
2. **Barrierefreiheit zuerst** – Stellen Sie sicher, dass jede Person Ihre Formulare verwenden kann
3. **Leistungsoptimierung** – Schnelle Formulare werden häufiger ausgefüllt
4. **Datenverantwortung** – Respektieren Sie die Privatsphäre der Benutzenden und minimieren Sie den Umfang erfasster Daten
5. **Klare Kommunikation** – Führen Sie Benutzende reibungslos durch den Prozess

Die Gestaltung großartiger Formulare geht über technische Aspekte hinaus. Stellen Sie sicher, dass Ihre Formulare einfach zu bedienen sind und die gewünschten Ergebnisse liefern:

## Entwerfen eines einfach zu bedienenden und barrierefreien Formulars

- **Verwenden klarer, sichtbarer Beschriftungen:** Jedes Formularfeld benötigt ein `<label>`. Verwenden Sie nicht ausschließlich Platzhaltertext (Text innerhalb des Eingabefelds), da dieser beim Ausfüllen ausgeblendet wird und nicht barrierefrei ist.

   - *Empfohlen:* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
   - *Nicht empfohlen:* `<input type="email" placeholder="Email Address">`

- **Auf Einfachheit setzen:** Verwenden Sie nach Möglichkeit standardmäßige HTML-Eingabetypen (`<input type="date">`, `<input type="tel">`). Diese verfügen häufig über eine bessere Unterstützung für Mobilgeräte und bessere Barrierefreiheit als komplexe benutzerdefinierte Widgets.
- **Logische Reihenfolge und Gruppierung:** Ordnen Sie die Felder so an, dass sie für Benutzende nachvollziehbar sind. Gruppieren Sie verwandte Felder mithilfe von `<fieldset>` und `<legend>`.
- **Anweisungen klar und verständlich formulieren:** Stellen Sie für alle möglicherweise unklaren Felder kompakte Hilfetexte oder QuickInfos bereit.
- **Tastaturnavigation:** Stellen Sie sicher, dass Benutzende nur mit der Tastatur (Tabulatortaste, Umschalt+Tabulatortaste, Eingabetaste, Leertaste) durch das gesamte Formular navigieren können.
- **Fehlerbearbeitung:** Machen Sie Fehler deutlich erkennbar und einfach zu beheben. Fehlermeldungen sollten neben dem entsprechenden Feld angezeigt werden und verständlich erklären, wie der Fehler behoben werden kann.
- **Sicherstellen, dass Ihre Formulare schnell geladen werden und sichtbar sind**
- **Formulare deutlich sichtbar positionieren:** Positionieren Sie wichtige Formulare so, dass sie für Benutzende ohne viel Scrollen leicht sichtbar sind (möglichst „im sichtbaren Bereich“). Die Forschung von Adobe, dass viele Formulare zu wenig genutzt werden, weil sie versteckt sind.
- **Assets optimieren:** Reduzieren Sie benutzerdefinierte JavaScript- oder CSS-Dateien für Ihre Formulare, um schnelle Ladezeiten zu gewährleisten. Edge Delivery Services unterstützt das Laden der Basisseiten, aber umfangreiche Formularskripte können die Leistung dennoch beeinträchtigen.
- **Verantwortungsvoller Umgang mit Benutzerdaten**
- **Fragen Sie nur nach wesentlichen Informationen:** Je weniger personenbezogene Daten Sie anfordern, desto besser. Jedes Feld ist ein potenzieller Grund für Benutzende, das Formular zu verlassen.
- **Zeigen Sie Transparenz:** Machen Sie deutlich, *warum* bestimmte Informationen benötigt werden und *wie sie verwendet werden*. Link zu Ihrer Datenschutzrichtlinie. Dies fördert Vertrauen.
- **Verbessern des Kundenerlebnisses: Captcha-Alternativen**
- **Überdenken Sie sichtbare Captchas:** Tests wie „Geben Sie den wellenförmigen Text ein“ oder „Klicken Sie auf alle Ampeln“ können für Benutzende und insbesondere Menschen mit Behinderung sehr frustrierend sein und führen häufig zu hohen Abbruchraten.
- **Ziehen Sie Alternativen in Betracht:**
   - **Honeypot-Felder:**: Fügen Sie ein ausgeblendetes Feld hinzu, das nur von Bots ausgefüllt wird. Wenn es Daten enthält, ist die Übermittlung wahrscheinlich Spam.
   - **Zeitbasierte Prüfungen:** Messen Sie, wie schnell ein Formular übermittelt wird. Bei zu schnellen Übermittlungen handelt es sich oft um Bots.
   - **Unsichtbares reCAPTCHA (v3):** Dieser Google-Service analysiert das Kundenverhalten im Hintergrund und stellt nur etwas infrage, wenn Benutzende verdächtig erscheinen. Dies führt oft zu einem viel besseres Kundenerlebnis.

## Was man beim Formularentwurf tun und nicht tun sollte

| ✅ Tun – für bessere Formulare | ❌ Nicht tun – was man vermeiden sollte |
|----------------------------------------------------------------------|------------------------------------------------------------------|
| Sichtbare `<label>`-Tags für alle Felder verwenden | Ausschließlich Platzhaltertext anstelle von richtigen Beschriftungen verwenden |
| Standardmäßige HTML-Eingabetypen (z. B. `<input type="email">`) bevorzugen | Übermäßig komplexe benutzerdefinierte Widgets verwenden |
| Sicherstellen, dass die vollständige Tastaturnavigation gewährleistet ist | Vage oder nicht vorhandene Fehlermeldungen |
| Klare, umsetzbare Fehlermeldungen anzeigen | Zu viele personenbezogene Daten ohne Begründung anfordern |
| Nur nach notwendigen Informationen fragen | Schwer zu lösende sichtbare CAPTCHAs verwenden |
| Erklären, wie Daten verwendet werden (Datenschutzinformationen oder Links) | Formular auf der Seite nicht auffindbar machen |
| Unsichtbare oder verhaltensbezogene CAPTCHA-Methoden verwenden |                                                                  |
| Formular auf der Seite leicht auffindbar machen (hervorgehobene Platzierung) |                                                                  |


## Nächste Schritte

Dieses Handbuch bietet einen Überblick über die Verwendung von Formularen mit AEM Edge Delivery Services. Detailliertere schrittweise Anweisungen zu bestimmten Konfigurationen finden Sie in der offiziellen Adobe Experience Manager-Dokumentation:

- [Dokumentenbasiertes Authoring mit Edge Delivery Services-Formularen.](/help/edge/docs/forms/tutorial.md)
- [Universeller Editor mit Edge Delivery Services-Formularen.](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [Dokumentenerstellung und Einbetten von Inhalten](https://www.aem.live/developer/da-tutorial)
- [AEM Forms-Übermittlungsdienst](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
