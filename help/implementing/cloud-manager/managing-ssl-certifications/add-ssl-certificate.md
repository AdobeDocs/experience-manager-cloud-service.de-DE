---
title: Hinzufügen eines SSL-Zertifikats
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL-Zertifikat hinzufügen.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 06e961febd7cb2ea1d8fca00cb3dee7f7ca893c9
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 88%

---


# Hinzufügen eines SSL-Zertifikats {#adding-an-ssl-certificate}

Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL-Zertifikat hinzufügen.

>[!TIP]
>
>Die Bereitstellung eines Zertifikats kann einige Tage dauern. Adobe empfiehlt daher, dass das Zertifikat rechtzeitig vor Ablauf eines Termins oder eines Live-Datums bereitgestellt wird.

## Zertifikatsanforderungen {#certificate-requirements}

Lesen Sie im Abschnitt **Zertifikatsanforderungen** des Dokuments [Einführung in die Verwaltung von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements), wie Sie sicherstellen, dass das Zertifikat, das Sie hinzufügen möchten, von AEM as a Cloud Service unterstützt wird.

## Hinzufügen eines Zertifikats {#adding-a-cert}

Führen Sie die folgenden Schritte aus, um ein Zertifikat mit Cloud Manager hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **SSL-Zertifikate**. Auf diesem Hauptbildschirm wird eine Tabelle mit Details zu vorhandenen SSL-Zertifikaten angezeigt.

   ![Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Klicken Sie auf **SSL-Zertifikat hinzufügen**, um das Dialogfeld **SSL-Zertifikat hinzufügen** zu öffnen.

   * Geben Sie in **Zertifikatname** einen Namen für Ihr Zertifikat ein.
      * Dies dient nur zu Informationszwecken und der Name kann so gewählt werden, dass Sie Ihr Zertifikat leicht finden können.
   * Fügen Sie das **Zertifikat**, den **privaten Schlüssel** und die **Zertifikatkette** in die entsprechenden Felder ein.
      * Alle drei Felder sind Pflichtfelder.

   ![Dialogfeld zum Hinzufügen des SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * Alle erkannten Fehler werden angezeigt.
      * Sie müssen alle Fehler beheben, bevor Ihr Zertifikat gespeichert werden kann.
      * Weitere Informationen zum Beheben häufiger Fehler finden Sie im Abschnitt [Zertifikatfehler](#certificate-errors).

1. Klicken Sie auf **Speichern**, um Ihr Zertifikat zu speichern.

Nach dem Speichern wird Ihr Zertifikat als neue Zeile in der Tabelle angezeigt.

![Gespeichertes SSL-Zertifikat](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

>[!NOTE]
>
>Eine Benutzerin bzw. ein Benutzer muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um ein SSL-Zertifikat in Cloud Manager zu installieren.

## Zertifikatfehler {#certificate-errors}

Bestimmte Fehler können auftreten, wenn ein Zertifikat nicht ordnungsgemäß installiert ist oder die Anforderungen von Cloud Manager nicht erfüllt.

### Richtige Zertifikatreihenfolge {#correct-certificate-order}

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

### Entfernen von Client-Zertifikaten {#client-certificates}

Wenn Sie beim Hinzufügen eines Zertifikats einen Fehler wie den folgenden erhalten:

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Wahrscheinlich haben Sie das Client-Zertifikat in die Zertifikatskette aufgenommen. Vergewissern Sie sich, dass die Kette nicht das Client-Zertifikat enthält, und versuchen Sie es erneut.

### Zertifikatsrichtlinie {#certificate-policy}

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

Indem Sie nach den OID-Mustern im ausgegebenen Zertifikatstext `grep` suchen, können Sie Ihre Zertifikatsrichtlinie bestätigen.

```shell
# "EV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5

# "OV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5

# "DV Policy - Not Accepted"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
```

### Gültigkeitsdaten des Zertifikats {#certificate-validity-dates}

Cloud Manager erwartet, dass das SSL-Zertifikat ab dem aktuellen Datum mindestens 90 Tage gültig ist. Sie sollten die Gültigkeit der Zertifikatkette überprüfen.

## Nächste Schritte {#next-steps}

Herzlichen Glückwunsch! Sie verfügen jetzt über ein funktionierendes SSL-Zertifikat für Ihr Projekt. Dies ist häufig ein erster Schritt zum Einrichten eines benutzerdefinierten Domänennamens.

* Weitere Informationen zum Einrichten eines benutzerdefinierten Domänennamens finden Sie im Dokument [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) .
* Informationen zum Aktualisieren und Verwalten Ihrer SSL-Zertifikate in Cloud Manager finden Sie im Dokument [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) .
