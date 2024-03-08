---
title: Von Tabellen in Forms - Überarbeiten von Feldvalidierungen für adaptive Formulare
description: Erstellen Sie leistungsstarke Formulare schneller mit Tabellen und Bausteinfeldern für adaptive Formulare! Dieses Handbuch hilft Ihnen beim Erstellen benutzerdefinierter Validierungen für EDS Forms Block-Felder.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 16e1d42a-42d0-4335-ba81-feedea7ed7d7
source-git-commit: 53a66eac5ca49183221a1d61b825401d4645859e
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Hinzufügen von Überprüfungen zu Formularfeldern

Der Block für adaptive Formulare verfügt über integrierte Validierungsfunktionen. Diese Validierungen werden in modernen Browsern basierend auf dem ausgewählten Feldtyp und den von Ihnen bereitgestellten zusätzlichen Eigenschaften automatisch angewendet.

## Typen und Validierung von Feldern

Der Block für adaptive Formulare unterstützt eine Vielzahl von [HTML-5-Eingabetypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), einschließlich Text, E-Mail, Zahl, Datum und mehr. Es wird auch berücksichtigt [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), Auswahl und Feldsatz sowie umfassende Eingabedokumentvalidierungsfunktionen, die mit HTML-5 verbunden sind.

verwendet HTML-Feldtypen, um die Art der Daten zu definieren, die ein Benutzer eingeben kann. Verschiedene Feldtypen verfügen über unterschiedliche integrierte Validierungsregeln:

E-Mail: Dieser Feldtyp validiert automatisch die Benutzereingabe anhand eines allgemeinen Formats für E-Mail-Adressen. Benutzern, die eine ungültige E-Mail eingeben, wird eine Fehlermeldung angezeigt.
Zahl: Dieser Feldtyp erlaubt nur numerische Eingaben. Benutzer, die nicht-numerische Zeichen eingeben, erhalten einen Fehler.
Datum: Dieser Feldtyp validiert die Benutzereingabe anhand eines Standarddatumsformats. Daten, die außerhalb eines angemessenen Bereichs liegen, werden möglicherweise auch als ungültig gekennzeichnet.
URL: Dieser Feldtyp validiert die Benutzereingabe anhand eines gültigen URL-Formats. Benutzern, die eine ungültige URL eingeben, wird eine Fehlermeldung angezeigt.
Tel: Dieser Feldtyp wurde speziell für Telefonnummern entwickelt und kann die Überprüfung der Trigger auf der Grundlage bestimmter Länderformate (nicht allgemein unterstützt) ermöglichen.



