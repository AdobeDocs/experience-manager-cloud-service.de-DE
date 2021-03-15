---
title: Hinzufügen eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
description: Hinzufügen eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 100%

---


# Hinzufügen eines SSL-Zertifikats {#adding-an-ssl-certificate}

>[!NOTE]
>AEM as a Cloud Service akzeptiert nur OV (Organization Validation)- oder EV (Extended Validation)-Zertifikate. DV-Zertifikate (Domain-Validation-Zertifikate) werden nicht akzeptiert. Außerdem muss es sich um ein X.509-TLS-Zertifikat einer vertrauenswürdigen Zertifizierungsstelle mit einem entsprechenden privaten 2048-Bit-RSA-Schlüssel handeln.

Die Bereitstellung eines Zertifikats dauert einige Tage und es wird empfohlen, Monate im Voraus für die Bereitstellung des Zertifikats zu sorgen. Weitere Informationen finden Sie unter [Beziehen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md).

## Zertifikatformat {#certificate-format}

SSL-Dateien müssen im PEM-Format vorliegen, damit sie in Cloud Manager installiert werden können. Zu den gängigen Dateierweiterungen im PEM-Format gehören `.pem,`,.`crt`, `.cer` und `.cert`.

Gehen Sie wie folgt vor, um das Format Ihrer SSL-Dateien in PEM zu konvertieren:

* Konvertieren von PFX in PEM

   `openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

* Konvertieren von P7B in PEM

   `openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

* Konvertieren von DER in PEM

   `openssl x509 -inform der -in certificate.cer -out certificate.pem`

## Wichtige Überlegungen {#important-considerations}

* Ein Anwender muss die Rolle „Geschäftsinhaber“ oder „Bereitstellungs-Manager“ innehaben, um ein SSL-Zertifikat in Cloud Manager installieren zu können.

* Cloud Manager lässt jeweils maximal 10 SSL-Zertifikate zu, die mit einer oder mehreren Umgebungen in Ihrem gesamten Programm verknüpft werden können. Dies gilt auch, wenn ein Zertifikat abgelaufen ist. In der Benutzeroberfläche von Cloud Manager können mit dieser Einschränkung jedoch bis zu 50 SSL-Zertifikate im Programm installiert werden.

## Hinzufügen eines Zertifikats {#adding-a-cert}

Gehen Sie wie folgt vor, um ein Zertifikat hinzuzufügen:

1. Melden Sie sich bei Cloud Manager an.
1. Navigieren Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.
1. Klicken Sie im linken Navigationsmenü auf **SSL-Zertifikate**. Auf diesem Bildschirm wird eine Tabelle mit Details zu vorhandenen SSL-Zertifikaten angezeigt.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Klicken Sie auf **SSL-Zertifikat hinzufügen**, um das Dialogfeld **SSL-Zertifikat hinzufügen** zu öffnen.

   * Geben Sie in **Zertifikatname** einen Namen für Ihr Zertifikat ein. Dabei kann es sich um einen beliebigen Namen handeln, mit dem Sie Ihr Zertifikat einfach referenzieren können.
   * Fügen Sie das **Zertifikat**, den **privaten Schlüssel** und die **Zertifikatkette** in die entsprechenden Felder ein. Verwenden Sie das Symbol zum Einfügen rechts neben dem Eingabefeld.
Alle drei Felder sind nicht optional und müssen ausgefüllt werden.

      ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)


      >[!NOTE]
      >Eventuell erkannte Fehler werden angezeigt. Sie müssen alle Fehler beheben, bevor Ihr Zertifikat gespeichert werden kann. Weitere Informationen zum Beheben häufiger Fehler finden Sie unter [Zertifikatfehler](#certificate-errors).

1. Klicken Sie auf **Speichern**, um das Zertifikat zu übermitteln. Es wird als neue Zeile in der Tabelle angezeigt.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

## Zertifikatfehler {#certificate-errors}

### Richtige Zertifikatreihenfolge {#correct-certificate-order}

Der häufigste Grund für das Fehlschlagen einer Zertifikatbereitstellung ist, dass die Zwischen- oder Kettenzertifikate nicht in der richtigen Reihenfolge vorliegen. Insbesondere müssen Zwischenzertifikatdateien mit dem Stammzertifikat oder dem Zertifikat enden, das sich am nächsten zum Stammordner befindet, und in absteigender Reihenfolge vom `main/server`-Zertifikat zum Stammordner vorliegen.

Sie können die Reihenfolge der Zwischenzertifikatdateien mithilfe des folgenden Befehls festlegen:

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

Sie können mithilfe der folgenden Befehle überprüfen, ob der private Schlüssel und das `main/server`-Zertifikat übereinstimmen:

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>Die Ausgabe dieser beiden Befehle muss genau gleich sein. Wenn Sie keinen passenden privaten Schlüssel zu Ihrem `main/server`-Zertifikat finden können, müssen Sie das Zertifikat erneut erstellen, indem Sie eine neue Zertifikatsignaturanforderung generieren bzw. ein aktualisiertes Zertifikat von Ihrem SSL-Anbieter anfordern.

### Gültigkeitsdaten des Zertifikats {#certificate-validity-dates}

Cloud Manager erwartet, dass das SSL-Zertifikat mindestens 90 Tage gültig ist. Sie sollten die Gültigkeit der Zertifikatkette überprüfen.
