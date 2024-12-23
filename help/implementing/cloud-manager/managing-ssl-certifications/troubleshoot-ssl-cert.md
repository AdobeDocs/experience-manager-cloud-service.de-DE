---
title: Fehlerbehebung bei Problemen mit SSL-Zertifikaten
description: Erfahren Sie, wie Sie Probleme mit SSL-Zertifikaten beheben können, indem Sie häufige Ursachen identifizieren, damit Sie sichere Verbindungen aufrechterhalten können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1017f84564cedcef502b017915d370119cd5a241
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 54%

---


# Fehlerbehebung bei Problemen mit SSL-Zertifikaten {#certificate-problems}

Erfahren Sie, wie Sie Probleme mit SSL-Zertifikaten beheben können, indem Sie häufige Ursachen identifizieren, damit Sie sichere Verbindungen aufrechterhalten können.

+++**Ungültiges Zertifikat**

## Ungültiges Zertifikat {#invalid-certificate}

Dieser Fehler tritt auf, weil der Kunde einen verschlüsselten privaten Schlüssel verwendet und den Schlüssel im DER-Format bereitgestellt hat.

+++

+++**Der private Schlüssel muss im PKCS 8-Format sein**

## Der private Schlüssel muss das PKCS 8-Format aufweisen. {#pkcs-8}

Dieser Fehler tritt auf, weil der Kunde einen verschlüsselten privaten Schlüssel verwendet und den Schlüssel im DER-Format bereitgestellt hat.

+++

+++**Richtige Zertifikatreihenfolge**

## Richtige Zertifikatreihenfolge {#certificate-order}

Der häufigste Grund für das Fehlschlagen einer Zertifikatbereitstellung ist, dass die Zwischen- oder Kettenzertifikate nicht in der richtigen Reihenfolge vorliegen.

Zwischenzertifikatdateien müssen mit dem Stammzertifikat oder dem Zertifikat enden, das am nächsten am Stammzertifikat liegt. Sie müssen in absteigender Reihenfolge vom `main/server`-Zertifikat zum Stammzertifikat vorliegen.

Sie können die Reihenfolge der Zwischenzertifikatdateien mithilfe des folgenden Befehls festlegen.

```shell
openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout
```

Sie können mithilfe der folgenden Befehle überprüfen, ob der private Schlüssel und das `main/server`-Zertifikat übereinstimmen.

```shell
openssl x509 -noout -modulus -in certificate.pem | openssl md5
```

```shell
openssl rsa -noout -modulus -in ssl.key | openssl md5
```

>[!NOTE]
>
>Die Ausgabe dieser beiden Befehle muss genau gleich sein. Wenn Sie keinen passenden privaten Schlüssel zu Ihrem `main/server`-Zertifikat finden können, müssen Sie das Zertifikat neu verschlüsseln, indem Sie eine neue Zertifikatsignaturanforderung (CSR) generieren und/oder ein aktualisiertes Zertifikat von Ihrem SSL-Anbieter anfordern.

+++

+++**Entfernen von Client-Zertifikaten**

## Entfernen von Client-Zertifikaten {#client-certificates}

Wenn Sie beim Hinzufügen eines Zertifikats einen Fehler wie den folgenden erhalten:

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Wahrscheinlich haben Sie das Client-Zertifikat in die Zertifikatskette aufgenommen. Vergewissern Sie sich, dass die Kette nicht das Client-Zertifikat enthält, und versuchen Sie es erneut.

+++

+++**Zertifikatrichtlinie**

## Zertifikatrichtlinie {#policy}

Wenn der folgende Fehler angezeigt wird, überprüfen Sie die Richtlinie Ihres Zertifikats.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

Eingebettete OID-Werte identifizieren normalerweise Zertifikatrichtlinien. Wenn Sie ein Zertifikat als Text ausgeben und nach der OID suchen, wird die Richtlinie des Zertifikats angezeigt.

Sie können Ihre Zertifikatdetails als Text ausgeben, indem Sie das folgende Beispiel als Anleitung verwenden.

```text
openssl x509 -in 9178c0f58cb8fccc.pem -text
certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            91:78:c0:f5:8c:b8:fc:cc
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C = US, ST = Arizona, L = Scottsdale, O = "GoDaddy.com, Inc.", OU = http://certs.godaddy.com/repository/, CN = Go Daddy Secure Certificate Authority - G2
        Validity
            Not Before: Nov 10 22:55:36 2021 GMT
            Not After : Dec  6 15:35:06 2022 GMT
        Subject: C = US, ST = Colorado, L = Denver, O = Alexandra Alwin, CN = adobedigitalimpact.com
        Subject Public Key Info:
...
```

Das OID-Muster im Text definiert den Richtlinientyp des Zertifikats.

| Muster | Richtlinie | In Cloud Manager akzeptabel |
|---|---|---|
| `2.23.140.1.1` | EV | Ja |
| `2.23.140.1.2.2` | OV | Ja |
| `2.23.140.1.2.1` | DV | Nein |

Indem Sie nach den OID-Mustern im ausgegebenen Zertifikatstext `grep` suchen, können Sie Ihre Zertifikatsrichtlinie bestätigen.

```shell
# "EV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5

# "OV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5

# "DV Policy - Not Accepted"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
```
+++

+++**Zertifikatgültigkeit

## Gültigkeit der Bescheinigung {#validity}

Cloud Manager erwartet, dass das SSL-Zertifikat ab dem aktuellen Datum mindestens 90 Tage gültig ist. Überprüfen Sie die Gültigkeit der Zertifikatskette.

+++

++**Falsches SAN-Zertifikat wird auf meine Domäne angewendet

## Falsches SAN-Zertifikat wird auf meine Domäne angewendet {#wrong-san-cert}

Nehmen wir an, Sie möchten `dev.yoursite.com` und `stage.yoursite.com` mit Ihrer Nicht-Produktionsumgebung und `prod.yoursite.com` mit Ihrer Produktionsumgebung verknüpfen.

Um das CDN für diese Domänen zu konfigurieren, müssen Sie für jede Domäne ein Zertifikat installiert haben. Installieren Sie daher ein Zertifikat, das für Ihre Nicht-Produktions-Domänen `*.yoursite.com` abdeckt, und ein anderes Zertifikat, das auch für Ihre Produktionsdomänen gilt.`*.yoursite.com`

Diese Konfiguration ist gültig. Wenn Sie jedoch eines der Zertifikate aktualisieren, da beide Zertifikate denselben SAN-Eintrag abdecken, installiert das CDN das neueste Zertifikat auf allen entsprechenden Domänen, was unerwartet erscheinen könnte.

Auch wenn dies unerwartet sein kann, ist dies kein Fehler und das Standardverhalten des zugrunde liegenden CDN. Wenn Sie über zwei oder mehr SAN-Zertifikate verfügen, die denselben SAN-Domäneneintrag abdecken, wird die Domäne für die Domäne installiert, wenn die Domäne durch ein Zertifikat abgedeckt ist und die andere aktualisiert wird.

+++
