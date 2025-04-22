---
title: Hinzufügen eines SSL-Zertifikats
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Tools von Cloud Manager Ihr eigenes SSL- oder ein von Adobe verwaltetes DV(Domain-Validierungs)-Zertifikat hinzufügen.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: bf903736e256bb9275bad6c0271b31b8dbdec625
workflow-type: ht
source-wordcount: '1021'
ht-degree: 100%

---


# Hinzufügen eines SSL-Zertifikats {#add-ssl-cert}

Erfahren Sie, wie Sie mit Cloud Ihr eigenes SSL- oder ein von Adobe verwaltetes DV(Domain-Validierungs)-Zertifikat hinzufügen.

>[!NOTE]
>
>Wenn Sie ein kundenseitig verwaltetes (OV/EV) SSL-Zertifikat und einen kundenseitig verwalteten CDN-Anbieter verwenden, brauchen Sie kein SSL-Zertifikat hinzuzufügen und können direkt zu [CDN-Konfiguration hinzufügen](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) gehen, sobald Sie bereit sind.

Die Bereitstellung eines Zertifikats kann mehrere Tage dauern. Adobe empfiehlt daher, dass Sie Ihr eigenes Zertifikat frühzeitig vor Ablauf einer Frist oder dem Tag der Veröffentlichung bereitstellen, um Verzögerungen zu vermeiden.

Informationen zum Aktualisieren und Verwalten Ihrer SSL-Zertifikate in Cloud Manager finden Sie unter [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

Wenn Sie Probleme beim Hinzufügen oder Verwalten Ihrer Zertifikate haben, finden Sie Informationen dazu unter [Fehlerbehebung bei SSL-Zertifikatfehlern](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).


## Voraussetzungen {#prerequisites}

* Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um ein SSL-Zertifikat hinzufügen zu können.
* Wenn Sie Ihr eigenes Zertifikat installieren, überprüfen Sie die **Zertifikatsanforderungen** in [Einführung – Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements).

## Auswählen des hinzuzufügenden SSL-Zertifikats {#which-ssl-to-add}

Nach dem [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) in AEM Cloud Manager hängt der nächste Schritt davon ab, ob Sie sich für die Verwendung eines von Adobe verwalteten (DV) SSL-Zertifikats (empfohlen) oder eines kundenseitig verwalteten (OV/EV) SSL-Zertifikats entschieden haben.

* **Bei einem von Adobe verwalteten (DV) SSL-Zertifikat:**
   * Die Domain-Validierung erfolgt, sobald die benutzerdefinierte Domain in Cloud Manager hinzugefügt und verifiziert wurde.
   * Jetzt müssen Sie [ein von Adobe verwaltetes (DV) SSL-Zertifikat hinzufügen](#add-adobe-managed-ssl-cert).
Nachdem Sie dieses in Cloud Manager hinzugefügt haben, warten Sie, bis Adobe das DV-SSL-Zertifikat in Ihrem Namen ausstellt und installiert.
   * Wenn das Zertifikat aktiv ist, kann Ihre benutzerdefinierte Domain verwendet werden.

* **Bei einem kundenseitig verwalteten (OV/EV) Zertifikat:**

   * Rufen Sie Ihr OV-/EV-SSL-Zertifikat von einer Zertifizierungsstelle ab. Weitere Informationen finden Sie unter [Anforderungen für kundenseitig verwaltete OV-/EV-SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements).
   * Nach dem Erwerb des Zertifikats [fügen Sie die Details Ihres kundenseitig verwalteten (OV/EV) SSL-Zertifikats](#add-customer-managed-ssl-cert) in Cloud Manager hinzu.
   * Nachdem Sie das Zertifikat hinzugefügt haben, wird Ihr benutzerdefinierter Domain-Name als verifiziert markiert und das SSL-Zertifikat wird angewendet.

In beiden Fällen ist die benutzerdefinierte Domain nach der Verifizierung und Installation des Zertifikats für die sichere Verwendung in Ihrer Umgebung verfügbar. Achten Sie darauf, in der Cloud Manager-Benutzeroberfläche regelmäßig [den Status der Domain zu überprüfen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md), um sicherzustellen, dass alles erwartungsgemäß funktioniert.

Siehe auch [Einführung in SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md).

## Hinzufügen eines von Adobe verwalteten Zertifikats (DV) {#add-adobe-managed-ssl-cert}

Benötigen Sie Hilfe, um sich für Ihre Domain zwischen einem von Adobe verwalteten SSL-Zertifikat (empfohlen) oder einem kundenseitig verwalteten SSL-Zertifikat zu entscheiden? Dann sollten Sie unter [Auswählen des hinzuzufügenden SSL-Zertifikats](#which-ssl-to-add) nachlesen.

**Hinzufügen eines von Adobe verwalteten (DV) SSL-Zertifikats :**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü anzuzeigen.

1. Klicken Sie unter der Überschrift **Services** auf ![Sperrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL-Zertifikate**.

   ![Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Klicken Sie oben rechts auf der Seite „SSL-Zertifikate“ auf **SSL-Zertifikat hinzufügen**.

1. Wählen Sie im Dialogfeld **SSL-Zertifikat hinzufügen**, basierend auf Ihrem [vorliegenden Anwendungsfall](#which-ssl-to-add), die Option **Von Adobe verwaltet (DV)** aus.

   ![Hinzufügen eines DV-Zertifikats](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. Geben Sie im Feld **Zertifikatname** einen Namen ein, der dem DV-SSL-Zertifikat zugeordnet werden soll.

1. Wählen Sie in der Dropdown-Liste **Domains auswählen** eine oder mehrere Domains aus, die dem DV-SSL-Zertifikat zugeordnet werden sollen.
   * Keine Domains auswählbar? In diesem Fall müssen Sie zunächst [einen benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) hinzufügen und sicherstellen, dass er verifiziert wird, bevor Sie ein von Adobe verwaltetes SSL-Zertifikat hinzufügen können.
   * Nachdem Sie einen benutzerdefinierten Domain-Namen hinzugefügt haben, kehren Sie zu diesem Thema zurück und beginnen Sie erneut mit Schritt 1.

1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

   Nachdem das SSL-Zertifikat erfolgreich ausgestellt wurde, wird in der Tabelle **SSL-Zertifikate** ein grünes Häkchen („Gültig“) angezeigt.

Sie haben nun ein funktionierendes von Adobe verwaltetes DV-SSL-Zertifikat für Ihr Projekt hinzugefügt. Dieser Schritt ist oft der erste, um einen benutzerdefinierten Domain-Namen einzurichten.

Sie können nun eine [CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) hinzufügen.

## Hinzufügen eines kundenseitig verwalteten SSL-Zertifikats (OV/EV) {#add-customer-managed-ssl-cert}

<!-- IF THIS TOPIC GET UPDATED, REMEMBER TO UPDATE THE STEPS ALSO IN THE "MANAGE SSL CERTIFICATES TOPIC TOO -->

Benötigen Sie Hilfe, um sich für Ihre Domain zwischen einem von Adobe verwalteten SSL-Zertifikat (empfohlen) oder einem kundenseitig verwalteten SSL-Zertifikat zu entscheiden? Dann sollten Sie unter [Auswählen des hinzuzufügenden SSL-Zertifikats](#which-ssl-to-add) nachlesen.

>[!IMPORTANT]
>
>Schließen Sie beim Hinzufügen oder Aktualisieren eines SSL-Zertifikats das neue Zertifikat nicht in die Zertifikatskette ein. Sonst wird das erfolgreiche Abschließen des Uploads verhindert.

**So fügen Sie ein kundenseitig verwaltetes SSL-Zertifikat (OV/EV) hinzu:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü anzuzeigen.

1. Klicken Sie unter der Überschrift **Services** auf ![Sperrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL-Zertifikate**.

   ![Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Klicken Sie oben rechts auf der Seite „SSL-Zertifikate“ auf **SSL-Zertifikat hinzufügen**.

1. Wählen Sie im Dialogfeld **SSL-Zertifikat hinzufügen**, basierend auf Ihrem [vorliegenden Anwendungsfall](#which-ssl-to-add), die Option **Kundenseitig verwaltet (OV/EV)** aus.

1. b. Geben Sie in das Feld **Zertifikatname** einen Namen für Ihr Zertifikat ein. 
Dieses Feld dient nur zu Informationszwecken. Der Name kann so gewählt werden, dass Sie Ihr SSL-Zertifikat leicht finden können.

1. Kopieren Sie in die Felder **Zertifikat**, **Privater Schlüssel** und **Zertifikatskette** die erforderlichen Werte aus Ihrem OV- oder EV-SSL-Zertifikat und fügen Sie sie in die entsprechenden Felder im Dialogfeld ein.

   Alle erkannten Fehler in den Werten werden angezeigt. Bevor Sie Ihr Zertifikat speichern können, müssen Sie alle Fehler beheben. Weitere Informationen zum Beheben häufiger Fehler finden Sie unter [Zertifikatfehler](#certificate-errors).

   ![Dialogfeld „SSL-Zertifikat hinzufügen“](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

   >[!NOTE]
   >
   >* Wenn Sie **Kundenseitig verwaltetes Zertifikat** beim [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) ausgewählt haben, wird die Domäne überprüft, ***nachdem*** das kundenseitig verwaltete SSL-Zertifikat (OV/EV) hinzugefügt und gespeichert wurde. Siehe auch [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to).

   Nachdem das SSL-Zertifikat erfolgreich ausgestellt wurde, wird in der Tabelle **SSL-Zertifikate** ein grünes Häkchen („Überprüft“) angezeigt.

Sie haben jetzt ein funktionierendes SSL-Zertifikat für Ihr Projekt hinzugefügt. Dieser Schritt ist oft der erste, um einen benutzerdefinierten Domain-Namen einzurichten.

Sie können nun eine [CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) hinzufügen.























<!--
## Add an SSL certificate {#add-ssl-cert}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate program.
1. On the **[My Programs](/help/implementing/cloud-manager/navigation.md#my-programs)** console, select the program.
1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to reveal the side menu. 
1. Under the **Services** heading, click ![Lock closed icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificates**. 

   ![Adding an SSL certificate](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Near the upper-right corner of the SSL Certificates page, click **Add SSL Certificate**.

1. In the **Add SSL certificate** dialog box, based on [your particular use case](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), do one of the following:

    | | Use case | Steps |
    | --- | --- | --- |
    | 1 | **Add an Adobe managed (DV) certificate** | **To add an Adobe managed (DV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Adobe managed (DV)**.<br>![Add a DV certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. In the **Certificate name** field, enter a name you want associated with the certificate.<br>c. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV SSL certificate.<br>No domains to select? If so, it means that you must first add a custom domain name and ensure it is verified before you can add an SSL certificate. See [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). When you are finished adding a custom domain name, return to this topic and begin at step 1 again.<br>d. Continue to step 7. |
    | 2 | **Add a customer managed (OV/EV) certificate** | **To add a customer managed (OV/EV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Customer managed (OV/EV)**.<br>b. In the **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your SSL certificate easily.<br>c. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.<br>![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate Errors](#certificate-errors) to learn more about troubleshooting common errors.<br>d. Continue to step 7. | 

1. In the lower-right corner of the dialog box, click **Save**.

    >[!NOTE]
    >
    >* If you selected **Adobe managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified with the added certificate when the custom domain is added. 
    >
    >* If you selected **Customer managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified ***after*** the customer managed (OV/EV) SSL certificate is added and saved. See also [Check the status of a custom domain name](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to).

    After the SSL certificate is successfully issued, it is displayed with a green verified check mark in the **SSL Certificates** table. 

    You now have added a working SSL certificate for your project. This step is often the first to set up a custom domain name. 
    

* To learn about updating and managing your SSL certificates in Cloud Manager, see [Manage SSL certificates](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

* If you are having issues adding or managing your certificates, see [Troubleshoot SSL certificate errors](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md). -->
