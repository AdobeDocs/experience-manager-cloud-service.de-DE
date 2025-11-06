---
title: Von Tabellen bis hin zu Formularen – Validierungen für adaptive Formularbausteine
description: Erstellen Sie leistungsstarke Formulare schneller mit Tabellen und Blockfelder für ein adaptives Formular. Diese Anleitung hilft Ihnen beim Erstellen benutzerdefinierter Validierungen für EDS-Formularblock-Felder.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 16e1d42a-42d0-4335-ba81-feedea7ed7d7
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 100%

---

# Hinzufügen von Validierungen zu Formularfeldern

Der adaptive Formularbaustein verfügt über integrierte Validierungsfunktionen. Diese Validierungen werden in modernen Browsern basierend auf dem ausgewählten Feldtyp und den von Ihnen bereitgestellten zusätzlichen Eigenschaften automatisch angewendet.

## Grundlegendes zu Feldtypen und Feldvalidierungen

Der adaptive Formularbaustein unterstützt eine Vielzahl von [HTML5-Eingabetypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), darunter für Text, E-Mail, Zahl und Datum. Ebenfalls berücksichtigt werden Elemente für [Textbereich](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), Auswahl und Feldsatz sowie umfassende Eingabevalidierungsfunktionen, die zu HTML5 gehören.

Die HTML-Feldtypen dienen dazu, die Art der Daten zu definieren, die Benutzende eingeben können. Verschiedene Feldtypen verfügen über unterschiedliche integrierte Validierungsregeln:

E-Mail: Dieser Feldtyp gleicht die Benutzereingabe automatisch mit einem allgemeinen Format für E-Mail-Adressen ab. Benutzenden, die eine ungültige E-Mail-Adresse eingeben, wird eine Fehlermeldung angezeigt.
Zahl: Dieser Feldtyp lässt nur numerische Eingaben zu. Benutzenden, die nicht numerische Zeichen eingeben, wird ein Fehler angezeigt.
Datum: Dieser Feldtyp gleicht die Benutzereingabe mit einem standardmäßigen Datumsformat ab. Daten, die außerhalb eines angemessenen Bereichs liegen, werden ggf. auch als ungültig gekennzeichnet.
URL: Dieser Feldtyp gleicht die Benutzereingabe mit einem gültigen URL-Format ab. Benutzenden, die eine ungültige URL eingeben, wird eine Fehlermeldung angezeigt.
Tel: Dieser Feldtyp ist speziell für Telefonnummern vorgesehen und kann eine Validierung auf Grundlage bestimmter Länderformate (nicht allgemein unterstützt) auslösen.



