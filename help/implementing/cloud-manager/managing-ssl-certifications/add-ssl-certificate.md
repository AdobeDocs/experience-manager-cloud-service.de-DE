---
title: Hinzufügen eines SSL-Zertifikats
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL-Zertifikat hinzufügen.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
source-git-commit: 2c87d5fb33b83ca77b97391e4b0baaf38f8dd026
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 28%

---

# Hinzufügen eines SSL-Zertifikats {#adding-an-ssl-certificate}

Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL-Zertifikat hinzufügen.

>[!TIP]
>
>Die Bereitstellung eines Zertifikats kann einige Tage dauern. Adobe empfiehlt daher, die Bescheinigung rechtzeitig im Voraus bereitzustellen.

## Zertifikatformat {#certificate-format}

SSL-Zertifikatdateien müssen im PEM-Format vorliegen, damit sie mit Cloud Manager installiert werden können. Häufige Dateierweiterungen des PEM-Formats umfassen `.pem,` ..`crt`, `.cer` und `.cert`.

Folgendes `openssl` -Befehle können zum Konvertieren von Nicht-PEM-Zertifikaten verwendet werden.

* Konvertieren von PFX in PEM

   ```shell
   openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes
   ```

* Konvertieren von P7B in PEM

   ```shell
   openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer
   ```

* Konvertieren von DER in PEM

   ```shell
   openssl x509 -inform der -in certificate.cer -out certificate.pem
   ```

## Hinzufügen eines Zertifikats {#adding-a-cert}

Führen Sie die folgenden Schritte aus, um ein Zertifikat mit Cloud Manager hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zu **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Klicken Sie auf **SSL-Zertifikate** aus dem linken Navigationsbereich. Eine Tabelle mit Details zu vorhandenen SSL-Zertifikaten wird auf dem Hauptbildschirm angezeigt.

   ![Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Klicken Sie auf **SSL-Zertifikat hinzufügen**, um das Dialogfeld **SSL-Zertifikat hinzufügen** zu öffnen.

   * Geben Sie in **Zertifikatname** einen Namen für Ihr Zertifikat ein.
      * Dies dient nur zu Informationszwecken und kann ein beliebiger Name sein, der Ihnen dabei hilft, Ihr Zertifikat einfach zu referenzieren.
   * Fügen Sie die **Zertifikat**, **Privater Schlüssel** und **Zertifikatskette** in ihre jeweiligen Felder ein.
      * Sie können das Symbol &quot;Einfügen&quot;rechts neben dem Eingabefeld verwenden.
      * Alle drei Felder sind Pflichtfelder.

   ![Dialogfeld &quot;SSL-Zertifikat hinzufügen&quot;](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * Eventuell erkannte Fehler werden angezeigt.
      * Sie müssen alle Fehler beheben, bevor Ihr Zertifikat gespeichert werden kann.
      * Siehe Abschnitt [Zertifikatfehler](#certificate-errors) Informationen zur Behebung häufiger Fehler.


1. Klicken **Speichern** , um Ihr Zertifikat zu speichern.

Nach dem Speichern wird Ihr Zertifikat als neue Zeile in der Tabelle angezeigt.

![Gespeichertes SSL-Zertifikat](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

>[!NOTE]
>
>Ein Benutzer muss Mitglied der **Business Owner** oder **Bereitstellungsmanager** Rolle, um ein SSL-Zertifikat in Cloud Manager zu installieren.

## Zertifikatfehler {#certificate-errors}

Bestimmte Fehler können auftreten, wenn ein Zertifikat nicht ordnungsgemäß installiert ist oder die Anforderungen von Cloud Manager erfüllt.

### Zertifikatrichtlinie {#certificate-policy}

Wenn der folgende Fehler angezeigt wird, überprüfen Sie die Richtlinie Ihres Zertifikats.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

Normalerweise werden Zertifikatrichtlinien durch eingebettete OID-Werte identifiziert. Wenn Sie ein Zertifikat als Text ausgeben und nach der OID suchen, wird die Richtlinie des Zertifikats angezeigt.

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

von `grep`Ping für die OID-Muster im Text des Ausgabedokuments verwenden, können Sie Ihre Zertifikatrichtlinie bestätigen.

```shell
# "EV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5

# "OV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5

# "DV Policy - Not Accepted"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
```

### Richtige Zertifikatreihenfolge {#correct-certificate-order}

Der häufigste Grund für das Fehlschlagen einer Zertifikatbereitstellung ist, dass die Zwischen- oder Kettenzertifikate nicht in der richtigen Reihenfolge vorliegen.

Zwischenzertifikatdateien müssen mit dem Stammzertifikat oder dem Zertifikat enden, das am nächsten am Stammverzeichnis liegt. Sie müssen in absteigender Reihenfolge von der `main/server` Zertifikat zum Stammverzeichnis hinzufügen.

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
>Die Ausgabe dieser beiden Befehle muss genau gleich sein. Wenn Sie keinen passenden privaten Schlüssel für Ihre `main/server` -Zertifikat verwenden, müssen Sie das Zertifikat erneut verschlüsseln, indem Sie eine neue CSR generieren und/oder ein aktualisiertes Zertifikat von Ihrem SSL-Anbieter anfordern.

### Gültigkeitsdaten des Zertifikats {#certificate-validity-dates}

Cloud Manager geht davon aus, dass das SSL-Zertifikat ab dem aktuellen Datum mindestens 90 Tage gültig ist. Sie sollten die Gültigkeit der Zertifikatkette überprüfen.
