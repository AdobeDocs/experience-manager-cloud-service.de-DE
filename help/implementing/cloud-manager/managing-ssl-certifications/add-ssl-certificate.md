---
title: SSL-Zertifikat hinzufügen - Verwalten von SSL-Zertifikaten
description: SSL-Zertifikat hinzufügen - Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: 4255035b68467e4ad783edd88e8f4e96855cfe50
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# Hinzufügen eines SSL-Zertifikats {#adding-an-ssl-certificate}

>[!NOTE]
>AEM als Cloud Service akzeptiert nur OV-(Organisationsüberprüfung) oder EV-(erweiterte Validierung) Zertifikate. DV(Domain Validation)-Zertifikate werden nicht akzeptiert. Darüber hinaus muss jedes Zertifikat ein X.509 TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle (CA) mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel sein.

Die Bereitstellung eines Zertifikats dauert einige Tage, und es wird empfohlen, das Zertifikat auch Monate im Voraus bereitzustellen. Weitere Informationen finden Sie unter [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) abrufen.

## Zertifikatformat {#certificate-format}

SSL-Dateien müssen im PEM-Format vorliegen, damit sie in Cloud Manager installiert werden können. Zu den gängigen Dateierweiterungen im PEM-Format gehören `.pem,` .`crt`, `.cer`, und `.cert`.

Gehen Sie wie folgt vor, um das Format Ihrer SSL-Dateien in PEM zu konvertieren:

* PFX in PEM konvertieren

   `openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

* P7B in PEM konvertieren

   `openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

* DER in PEM konvertieren

   `openssl x509 -inform der -in certificate.cer -out certificate.pem`

## Wichtige Überlegungen {#important-considerations}

* Ein Benutzer muss sich in der Rolle &quot;Geschäftsinhaber&quot;oder &quot;Deployment Manager&quot;befinden, um ein SSL-Zertifikat in Cloud Manager installieren zu können.

* Cloud Manager lässt jederzeit maximal 10 SSL-Zertifikate zu, die mit einer oder mehreren Umgebung im gesamten Programm verknüpft werden können, selbst wenn ein Zertifikat abgelaufen ist. In der Benutzeroberfläche von Cloud Manager können jedoch bis zu 50 SSL-Zertifikate mit dieser Einschränkung im Programm installiert werden.

## Hinzufügen eines Zertifikats {#adding-a-cert}

Gehen Sie wie folgt vor, um ein Zertifikat hinzuzufügen:

1. Melden Sie sich bei Cloud Manager an.
1. Navigieren Sie zum Bildschirm **Umgebung** von **Übersicht**.
1. Klicken Sie im linken Navigationsmenü auf **SSL Certificates**. In diesem Bildschirm wird eine Tabelle mit Details zu vorhandenen SSL-Zertifikaten angezeigt.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Klicken Sie auf **Hinzufügen SSL-Zertifikat**, um das Dialogfeld **Hinzufügen SSL-Zertifikat** zu öffnen.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   1. Geben Sie unter **Zertifikatname** einen Namen für Ihr Zertifikat ein. Dabei kann es sich um einen beliebigen Namen handeln, mit dem Sie Ihr Zertifikat leicht referenzieren können.
   1. Fügen Sie die Felder **Zertifikat**, **Privater Schlüssel** und **Zertifikatskette** in die entsprechenden Felder ein. Verwenden Sie das Symbol zum Einfügen rechts neben dem Eingabefeld.
Alle drei Felder sind nicht optional und müssen einbezogen werden.

      >[!NOTE]
      >Alle erkannten Fehler werden angezeigt. Sie müssen alle Fehler beheben, bevor Ihr Zertifikat gespeichert werden kann. Weitere Informationen zum Beheben häufiger Fehler finden Sie unter [Zertifikatfehler](#certificate-errors).

1. Klicken Sie auf **Speichern**, um das Zertifikat zu senden. Es wird als neue Zeile in der Tabelle angezeigt.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

## Zertifikatfehler {#certificate-errors}

### Richtige Zertifikatreihenfolge {#correct-certificate-order}

Der häufigste Grund für das Fehlschlagen einer Zertifikatbereitstellung ist, dass die Zwischen- oder Kettenzertifikate nicht in der richtigen Reihenfolge sind. Insbesondere müssen zwischengeschaltete Zertifikatdateien mit dem Stammzertifikat oder -zertifikat enden, das am nächsten zum Stammordner liegt, und sich in absteigender Reihenfolge vom `main/server`-Zertifikat zum Stammordner befinden.

Sie können die Reihenfolge der Zwischendateien mithilfe des folgenden Befehls festlegen:

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

Sie können mithilfe der folgenden Befehle überprüfen, ob der private Schlüssel und das `main/server`-Zertifikat übereinstimmen:

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>Die Ausgabe dieser beiden Befehle muss genau gleich sein. Wenn Sie keinen passenden privaten Schlüssel zu Ihrem `main/server`-Zertifikat finden können, müssen Sie das Zertifikat erneut signieren, indem Sie eine neue CSR generieren und/oder ein aktualisiertes Zertifikat von Ihrem SSL-Anbieter anfordern.

### Gültigkeitsdaten des Zertifikats {#certificate-validity-dates}

Cloud Manager erwartet, dass das SSL-Zertifikat in Zukunft mindestens 90 Tage gültig ist. Sie sollten die Gültigkeit der Zertifikatskette überprüfen.
