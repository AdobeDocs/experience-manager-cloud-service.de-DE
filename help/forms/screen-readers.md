---
title: Bildschirmlesehilfen für HTML5-Formulare
description: Listet die von HTML5-Formularen unterstützten Bildschirmlesehilfen auf.
content-type: reference
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: HTML5 Forms,Mobile Forms
exl-id: 07d20c2f-7d13-48ac-8d58-b367eb194558
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 100%

---

# Bildschirmlesehilfen für HTML5-Formulare {#screen-readers-for-html-forms}

<span class="preview"> Die HTML5-Formularfunktion wird als Teil des Early-Access-Programms angeboten. Um Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (Arbeits-)E-Mail-ID an aem-forms-ea@adobe.com.
</span>

HTML5-Formularkomponenten rendern XFA-Formularvorlagen im HTML5-Format. Diese Formulare können von allen Standard-Browsern wiedergegeben werden, die HTML5 unterstützen. Um ein ähnliches Datenerfassungserlebnis in allen PDF- und HTML5-Formularen zu unterstützen, wird das Layout der PDF-Formulare in HTML5-Formularen beibehalten.

HTML5-Formulare verwenden standardmäßige HTML-Konstrukte, sodass für diese Formulare barrierefreie HTML-Anwendungen verwendet werden können. Wenn ein Formular gemäß den Best Practices für barrierefreie Formulare entworfen wurde, funktioniert es mit jeder unterstützten Bildschirmlesehilfe. Außerdem ist für solche Formulare die Tastaturnavigation aktiviert.

## Barrierefreiheitsstandards {#accessibility-standards}

HTML5-Formulare erfüllen Abschnitt 508 für Barrierefreiheit mit bekannten Ausnahmen. Siehe [VPAT für HTML5-Formulare](https://www.adobe.com/content/dam/cc1/en/accessibility/compliance/pdfs/adobe-livecycle-es4-section-508-vpat-portfolio.pdf) für Details.

## Zertifizierte Bildschirmlesehilfen für HTML5-Formulare {#certified-screen-readers-for-html-forms}

* JAWS 14.0 auf Microsoft® Windows
* VoiceOver auf macOS X und iPad

### JAWS {#jaws}

In HTML5-Formularen funktionieren alle standardmäßigen Tasteneingaben und Tastaturbefehle. Weitere Informationen zur Verwendung von JAWS finden Sie unter [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/jaws-hq.asp).

### VoiceOver {#voiceover}

HTML5-Formulare unterstützen alle Standard-Tasteneingaben und Gesten für VoiceOver. Weitere Informationen zum Einrichten und Verwenden von VoiceOver finden Sie unter [https://www.apple.com/de/accessibility/vision/](https://www.apple.com/de/accessibility/vision/).

## Bekannte Probleme {#known-issues}

* **(Ausschließlich Internet Explorer 9)** In HTML5-Formularen werden die Seiten bei Bedarf geladen (dynamisch). Das Laden von Seiten bei Bedarf verursacht Probleme mit Bildschirmlesehilfen. Wenn sich der Fokus der Bildschirmlesehilfe im letzten Feld der Seite befindet und die Tabulatortaste gedrückt wird, kehrt die Bildschirmlesehilfe zum ersten Feld der ersten Seite des Formulars zurück.
* **(Ausschließlich Internet Explorer 9)** Das Datumsauswahl-Steuerelement in HTML5-Formularen lässt sich nicht vollständig über die Tastatur steuern. Wenn Sie im Datumsauswahl -Steuerelement die Bild-Auf/Bild-Ab-Tasten mehrmals hintereinander drücken, wird das Datumsauswahl-Steuerelement geschlossen und der Fokus wird auf das nächste/letzte Feld gerichtet.

* VoiceOver kann Pfeiltasten auf dem Datumswidget auf iPad Safari nicht erkennen.
