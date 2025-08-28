---
title: Edge Delivery Services für AEM Forms – Häufig verwendete Regex-Ausdrücke zur Validierung von Formularfeldern
description: Edge Delivery Services für AEM Forms – Häufig verwendete Regex-Ausdrücke zur Validierung von Formularfeldern
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 5cfe23bb-155f-4639-b7b7-5edc172ba92a
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: ht
source-wordcount: '193'
ht-degree: 100%

---

# Häufig verwendete Regex-Ausdrücke für Validierungen

Im Folgenden finden Sie einige reguläre Ausdrücke, mit denen Sie die Validierung von Formularen über das hinaus erweitern können, was moderne Browser bieten:

## Starkes Kennwort

```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Gewährleistet mindestens 8 Zeichen mit:

- Kleinbuchstabe (a-z)
- Großbuchstabe (A-Z)
- Ziffer (0-9)
- Sonderzeichen (@$!%*?&amp;)


## E-Mail-Adresse


```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Erlaubt Buchstaben, Zahlen und Sonderzeichen im Benutzernamen und Domain-Namen.


## Telefonnummer (US-Format)

```regex
^\(?([0-9]{3})\)?[-. ]([0-9]{3})[-. ]([0-9]{4})$
```

Validiert Telefonnummern im Format (XXX) XXX-XXXX.



## URL

```regex
^(http|https)://.*$
```

Gewährleistet eine gültige URL, die mit http oder https beginnt.



## Datum (JJJJ-MM-TT)

```regex
^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12][0-9]|3[01])$
```

Validiert Daten im Format JJJJ-MM-TT.


## Uhrzeit (HH:MM)

```regex
^([01][0-9]|2[0-3]):[0-5][0-9]$
```

Validiert die Uhrzeiten im Format HH::MM (24-Stunden-Format).


## Postleitzahl (US-Format)

```regex
^\d{5}(?:[-\ ]\d{4})?$
```

Validiert 5-stellige US-Postleitzahlen mit optionalem Bindestrich und 4-stelliger Erweiterung.


## Benutzername (alphanumerisch und Unterstrich)

```regex
^[a-zA-Z0-9_]+$
```

Erlaubt Buchstaben, Zahlen und Unterstriche.


## Farb-Hexadezimal-Code

```regex
^#[0-9a-fA-F]{6}$
```

Validiert 6-stellige Hexadezimal-Farb-Codes. Beispiel: #FFFFFF.


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
