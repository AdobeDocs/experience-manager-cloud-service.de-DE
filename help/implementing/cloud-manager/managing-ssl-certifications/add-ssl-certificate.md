---
title: Hinzufügen eines SSL-Zertifikats
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL- oder DV(Domain Validation)-Zertifikat hinzufügen.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8e2fc0d4ee82e79d1a822a528b1a46acce3c192a
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 92%

---


# Hinzufügen eines SSL-Zertifikats {#add-ssl-cert}

Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager ein kundenseitig verwaltetes SSL-Zertifikat oder ein von Adobe generiertes und verwaltetes DV(Domain Validation)-Zertifikat hinzufügen.

Siehe auch [Fehlerbehebung bei SSL-Zertifikatfehlern](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).

## Hinzufügen eines SSL-Zertifikats {#adding-an-ssl-certificate}

Die Bereitstellung eines Zertifikats kann einige Tage dauern. Adobe empfiehlt daher, dass das Zertifikat frühzeitig vor Ablauf einer Frist oder dem Tag der Veröffentlichung bereitgestellt wird.

Überprüfen Sie die **Zertifikatanforderungen** in der [Einführung in die Verwaltung von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements), um sicherzustellen, dass AEM as a Cloud Service das Zertifikat unterstützt, das hinzugefügt werden soll.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

>[!NOTE]
>
>Kundinnen und Kunden dürfen keine DV(Domain Validation)-Zertifikate hochladen.

**Hinzufügen eines SSL-Zertifikats**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich unter **Dienste** auf **SSL-Zertifikate**. Wenn das linke Navigationsbedienfeld nicht wie im folgenden Bild angezeigt wird, müssen Sie ggf. auf das Hamburger-Symbol oben links klicken.

   ![Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Klicken Sie oben rechts auf der Seite auf **SSL-Zertifikat hinzufügen**.

1. Führen Sie im Dialogfeld **SSL-Zertifikat hinzufügen** basierend auf dem [vorliegenden Anwendungsfall](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) einen der folgenden Schritte aus:

   | | Anwendungsfall | Schritte |
   | --- | --- | --- |
   | 1 | **Hinzufügen eines von Adobe verwalteten Zertifikats (DV)** | **So fügen Sie ein von Adobe verwaltetes Zertifikat (DV) hinzu:**<br> a. Legen Sie für den Zertifikatstyp die Option **Von Adobe verwaltet (DV)** fest.<br>![Fügen Sie ein DV-Zertifikat hinzu](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. Geben Sie im Feld **Zertifikatname** einen Namen ein, der dem Zertifikat zugeordnet werden soll.<br>c. Wählen Sie in der Dropdownliste **Domänen auswählen** eine oder mehrere Domänen aus, die dem DV-Zertifikat zugeordnet werden sollen.<br>Keine Domains auswählbar? Ist dies der Fall, müssen Sie eine benutzerdefinierte Domain hinzufügen. Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Nachdem Sie einen benutzerdefinierten Domain-Namen hinzugefügt haben, kehren Sie zu diesem Thema zurück und beginnen Sie erneut mit Schritt 1.<br>d. Fahren Sie mit Schritt 7 fort. |
   | 2 | **Hinzufügen eines kundenseitig verwalteten Zertifikats (OV/EV)** | **So fügen Sie ein kundenseitig verwaltetes Zertifikats (OV/EV) hinzu:**<br> a. Legen Sie für den Zertifikatstyp die Option **Kundenseitig verwaltet (OV/EV)** fest.<br>b. Geben Sie in das Feld **Zertifikatname** einen Namen für Ihr Zertifikat ein. Dieses Feld dient nur zu Informationszwecken, und der Name kann so gewählt werden, dass Sie Ihr Zertifikat leicht finden können.<br>c. Fügen Sie in die Felder **Zertifikat**, **Privater Schlüssel** und **Zertifikatskette** die erforderlichen Werte ein.<br>![Dialogfeld „SSL-Zertifikat hinzufügen“](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Alle erkannten Fehler in den Werten werden angezeigt. Bevor Sie Ihr Zertifikat speichern können, müssen Sie alle Fehler beheben. Weitere Informationen zum Beheben häufiger Fehler finden Sie unter [Zertifikatfehler](#certificate-errors).<br>d. Fahren Sie mit Schritt 7 fort. |

<!--
    **Add an SSL certificate:**
    1. Select the certificate type **Customer managed (OV/EV)**.
    1. In **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your certificate easily.
    1. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.

        ![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)
  
    Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate errors](#certificate-errors) to learn more about troubleshooting common errors.

    **Add a DV certificate:**
    1. Select the certificate type **Adobe managed (DV)**.

        ![Adding a DC certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

    1. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV certificate.

        No domains to select? If so, it means that you must add a custom domain. See [Add a custom domain](#add-custom-domain). When you are finished, resume the steps from the beginning again. -->

1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

   Nachdem das Zertifikat erfolgreich ausgestellt wurde, wird in der Tabelle **SSL-Zertifikate** ein grünes Häkchen angezeigt.

Sie haben jetzt ein funktionierendes SSL-Zertifikat für Ihr Projekt hinzugefügt. Dieser Schritt ist oft der erste, um einen benutzerdefinierten Domain-Namen einzurichten.

* Informationen zum Einrichten eines benutzerdefinierten Domain-Namens finden Sie unter [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
* Informationen zum Aktualisieren und Verwalten Ihrer SSL-Zertifikate in Cloud Manager finden Sie unter [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

<!--
### Add a custom domain {#add-custom-domain}

Before you can add an Adobe generated and managed Domain Validated (DV) certificate, you must first add a custom domain. The process for doing so is nearly the same as detailed in [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) and [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). However, that functionality is now slightly expanded, as described below.

1. When adding a custom domain name, in the **Verify domain** dialog box, select an **Adobe managed certificate**.

    ![Choose Adobe-managed](assets/verify-domain-dialog.png)

1. In the **Verify domain** dialog box, add a CNAME verification record to your DNS.

    ![Add CNAME entry](assets/verify-domain-dialog-adobe-managed.png)

1. After the domain is created, click the ellipsis button in the list of domains and select **Verify** to verify the domain.

    ![Verify domain](assets/verify-domain.png) 

1. Resume the task [Add a DV certificate](#adding-an-ssl-certificate). -->


