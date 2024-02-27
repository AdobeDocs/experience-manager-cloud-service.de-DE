---
title: AEM Forms Edge Delivery Service - häufig verwendete Regex-Ausdrücke zur Validierung von Formularfeldern
description: AEM Forms Edge Delivery Service - häufig verwendete Regex-Ausdrücke zur Validierung von Formularfeldern
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 78d40574e6fea8dde22414e43fd77215b9e7d2a1
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 4%

---


# Häufig verwendete Regex-Ausdrücke für Überprüfungen

Im Folgenden finden Sie einige reguläre Ausdrücke, mit denen Sie die Formularüberprüfung über das hinaus erweitern können, was moderne Browser bieten:

## Starkes Kennwort

```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Stellt mindestens 8 Zeichen sicher mit:

* Kleinbuchstabe (a-z)
* Großbuchstabe (A-Z)
* Ziffer (0-9)
* Sonderzeichen (@$!%*?&amp;)


## E-Mail-Adresse


```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Ermöglicht Buchstaben, Zahlen und Sonderzeichen im Benutzernamen und Domänennamen.


## Telefonnummer (Format &quot;USA&quot;)

```regex
^\(?([0-9]{3})\)?[-. ]([0-9]{3})[-. ]([0-9]{4})$
```

Validiert Telefonnummern im Format (XXX) XXX-XXXX.



## URL

```regex
^(http|https)://.*$
```

Stellt eine gültige URL sicher, die mit http oder https beginnt.



## Datum (JJJJ-MM-TT)

```regex
^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12][0-9]|3[01])$
```

Validiert Daten im Format JJJJ-MM-TT.


## Zeit (HH:MM)

```regex
^([01][0-9]|2[0-3]):[0-5][0-9]$
```

Validiert die Uhrzeiten im Format HH:MM (24-Stunden-Format).


## Postleitzahl (US-Format)

```regex
^\d{5}(?:[-\ ]\d{4})?$
```

Validiert 5-stellige US-Postleitzahlen mit optionalem Bindestrich und 4-stelliger Erweiterung.


## Benutzername (alphanumerisch und Unterstrich)

```regex
^[a-zA-Z0-9_]+$
```

Ermöglicht Buchstaben, Zahlen und Unterstriche.


## Farbhexadezimalcode

```regex
^#[0-9a-fA-F]{6}$
```

Validiert 6-stellige Hexadezimalfarbcodes. Beispiel: #FFFFFF.


## IP-Adresse

```regex
^(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})$
```

Validiert IPv4-Adressen.



## Sozialversicherungsnummer (US-Format)

```regex
^\d{3}-\d{2}-\d{4}$
```



## Kreditkartennummer

```regex
^(?:4[0-9]{12}(?:[0-9]{3})?|[25][1-7][0-9]{14}$
```

Validiert Telefonnummern im Format (XXX) XXX-XXXX.



## Telefonnummer (US-Format):

```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Validiert Telefonnummern im Format (XXX) XXX-XXXX.
