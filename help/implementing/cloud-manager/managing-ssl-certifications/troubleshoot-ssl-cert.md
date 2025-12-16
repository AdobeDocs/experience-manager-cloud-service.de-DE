---
title: Fehlerbehebung bei SSL-Zertifikatsproblemen
description: Erfahren Sie, wie Sie Probleme mit SSL-Zertifikaten beheben können, indem Sie häufige Ursachen identifizieren, damit Sie sichere Verbindungen aufrechterhalten können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 8fb8f708-51a5-46d0-8317-6ce118a70fab
source-git-commit: 7d86ec9cd7cc283082da44111ad897a5aa548f58
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 77%

---

# Fehlerbehebung bei SSL-Zertifikatsproblemen {#certificate-problems}

Erfahren Sie, wie Sie Probleme mit SSL-Zertifikaten beheben können, indem Sie häufige Ursachen identifizieren, damit Sie sichere Verbindungen aufrechterhalten können.

+++**Ungültiges Zertifikat**

## Ungültiges Zertifikat {#invalid-certificate}

Dieser Fehler tritt auf, weil die Kundin bzw. der Kunde einen verschlüsselten privaten Schlüssel verwendet und den Schlüssel im DER-Format bereitgestellt hat.

+++

+++**Der private Schlüssel muss im PKCS 8-Format sein**

## Der private Schlüssel muss im PKCS 8-Format sein. {#pkcs-8}

Dieser Fehler tritt auf, weil die Kundin bzw. der Kunde einen verschlüsselten privaten Schlüssel verwendet und den Schlüssel im DER-Format bereitgestellt hat.

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

+++Zertifikatgültigkeit

## Zertifikatgültigkeit {#validity}

Cloud Manager erwartet, dass das SSL-Zertifikat ab dem aktuellen Datum mindestens 90 Tage gültig ist. Überprüfen Sie die Gültigkeit der Zertifikatskette.

+++

+++Auf meine Domain wird ein falsches SAN-Zertifikat angewendet

## Auf meine Domain wird ein falsches SAN-Zertifikat angewendet {#wrong-san-cert}

Nehmen wir an, Sie möchten `dev.yoursite.com` und `stage.yoursite.com` mit Ihrer produktionsfremden Umgebung und `prod.yoursite.com` mit Ihrer Produktionsumgebung verknüpfen.

Um das CDN für diese Domains zu konfigurieren, muss für jede Domain ein Zertifikat installiert sein. Daher müssen Sie ein Zertifikat installieren, das die `*.yoursite.com` für Ihre Nicht-Produktions-Domains abdeckt, und ein weiteres, das auch die `*.yoursite.com` für Ihre Produktions-Domains abdeckt.

Diese Konfiguration ist gültig. Wenn Sie jedoch eines der Zertifikate aktualisieren, decken beide Zertifikate immer noch denselben SAN-Eintrag ab. Daher installiert das CDN das neueste Zertifikat auf allen anwendbaren Domains, was unerwartet erscheinen kann.

Obwohl dieses Szenario unerwartet sein kann, ist es kein Fehler und das Standardverhalten des zugrunde liegenden CDN. Wenn Sie zwei oder mehr SAN-Zertifikate haben, die denselben SAN-Domäneneintrag abdecken, installiert das CDN das zuletzt aktualisierte Zertifikat für diese Domäne. Diese Situation tritt auch dann auf, wenn ein anderes Zertifikat bereits denselben Domain-Eintrag abdeckt.

+++
