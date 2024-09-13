---
title: Hinzufügen eines SSL-Zertifikats
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL-Zertifikat oder DV-Zertifikat (Domänenvalidierung) hinzufügen.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d2f05915c0bf0af073db7f070b83f13aeae55252
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 20%

---


# Hinzufügen eines SSL-Zertifikats {#add-ssl-cert}

Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager ein kundenverwaltetes SSL-Zertifikat oder ein von der Adobe generiertes und verwaltetes DV-Zertifikat (Domain Validation) hinzufügen.

Siehe auch [Fehlerbehebung bei SSL-Zertifikatfehlern](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).

## Hinzufügen eines SSL-Zertifikats {#adding-an-ssl-certificate}

Die Bereitstellung eines Zertifikats kann einige Tage dauern. Daher empfiehlt Adobe, das Zertifikat rechtzeitig vor Ablauf einer Frist oder einem Live-Datum bereitzustellen.

Überprüfen Sie die **Zertifikatanforderungen** in der [Einführung in das Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements), um sicherzustellen, dass AEM as a Cloud Service das Zertifikat unterstützt, das Sie hinzufügen möchten.

Ein Benutzer muss Mitglied der Rolle **Business Owner** oder **Deployment Manager** sein, um diese Aufgabe abzuschließen.

>[!NOTE]
>
>Kunden dürfen keine DV-Zertifikate (Domain Validation) hochladen.

**Hinzufügen eines SSL-Zertifikats:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich unter **Dienste** auf **SSL-Zertifikate**. Wenn das linke Navigationsfenster nicht wie im folgenden Bild dargestellt angezeigt wird, müssen Sie möglicherweise auf das Hamburger-Symbol in der oberen linken Ecke klicken.

   ![Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Klicken Sie in der rechten oberen Ecke der Seite auf **SSL-Zertifikat hinzufügen**.

1. Führen Sie im Dialogfeld **SSL-Zertifikat hinzufügen** basierend auf [Ihrem speziellen Anwendungsfall](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) einen der folgenden Schritte aus:

   | | Anwendungsfall | Schritte |
   | --- | --- | --- |
   | 1 | **Hinzufügen eines von Adobe verwalteten Zertifikats (DV)** | **Hinzufügen eines von Adobe verwalteten Zertifikats (DV):**<br> a. Wählen Sie den Zertifikatstyp **Adobe managed (DV)** aus.<br>![Fügen Sie ein DV-Zertifikat hinzu](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. Wählen Sie in der Dropdownliste **Domänen auswählen** eine oder mehrere Domänen aus, die dem DV-Zertifikat zugeordnet werden sollen.<br>Keine Domänen zur Auswahl? Ist dies der Fall, müssen Sie eine benutzerdefinierte Domäne hinzufügen. Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Wenn Sie mit dem Hinzufügen eines benutzerdefinierten Domänennamens fertig sind, kehren Sie zu diesem Thema zurück und beginnen Sie erneut mit Schritt 1.<br>d. Fahren Sie mit Schritt 7 fort. |
   | 2 | **Hinzufügen eines kundenverwalteten Zertifikats (OV/EV)** | **Hinzufügen eines kundenverwalteten Zertifikats (OV/EV):**<br> a. Wählen Sie den Zertifikatstyp &quot;**Vom Kunden verwaltet (OV/EV)**&quot;.<br>b. Geben Sie im Feld **Zertifikatname** einen Namen für Ihr Zertifikat ein. Dieses Feld dient nur zu Informationszwecken und der Name kann so gewählt werden, dass Sie Ihr Zertifikat leicht finden können.<br>c. Fügen Sie in die Felder **Zertifikat**, **Privater Schlüssel** und **Zertifikatskette** die erforderlichen Werte in die entsprechenden Felder ein.<br>![Dialogfeld &quot;SSL-Zertifikat hinzufügen&quot;](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Alle erkannten Fehler in Werten werden angezeigt. Bevor Sie Ihr Zertifikat speichern können, müssen Sie alle Fehler beheben. Weitere Informationen zur Fehlerbehebung bei häufigen Fehlern finden Sie unter [Zertifikatfehler](#certificate-errors) .<br>d. Fahren Sie mit Schritt 7 fort. |

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

* Informationen zum Einrichten eines benutzerdefinierten Domänennamens finden Sie unter [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
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


