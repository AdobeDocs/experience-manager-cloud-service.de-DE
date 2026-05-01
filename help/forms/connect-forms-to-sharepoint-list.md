---
title: Senden von Daten an einen SharePoint-Listenspeicher bei Übermittlung eines adaptiven Formulars
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list when you submit the form.
keywords: Verbinden der SharePoint-Liste für ein adaptives Formular, Senden an SharePoint, Erstellen einer SharePoint-Listenkonfiguration, Verwenden der Übermittlungsaktion „An SharePoint senden“ in einem adaptiven Formular, Verbinden eines adaptiven Formulars mit der Microsoft&reg;-SharePoint-Liste.
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 9ac3e7be-c6fa-4dbc-9aba-b81741ba6c55
source-git-commit: 0e5045b87719781301d91874c7355eda9426beef
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 54%

---

# Verbinden eines adaptiven Formulars mit einer Microsoft® SharePoint-Liste {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

<span> Dieses Video gilt nur für Kernkomponenten. Informationen zu UE/Foundation-Komponenten finden Sie im Artikel.</span>

So verwenden Sie die Sendeaktion [!UICONTROL An SharePoint senden] in einem adaptiven Formular:

1. [Erstellen einer SharePoint-Listenkonfiguration](#1-create-a-sharepoint-list-configuration): Dadurch wird AEM Forms mit Ihrem Microsoft® Sharepoint-Listenspeicher verbunden.
1. [Verwenden von „Senden mit Formulardatenmodell (FDM)“ in einem adaptiven Formular](#2-use-the-submit-using-form-data-model-fdm-in-an-adaptive-form-use-submit-using-fdm): Dadurch wird Ihr adaptives Formular mit dem konfigurierten Microsoft® SharePoint verbunden.

## &#x200B;1. Erstellen einer Microsoft SharePoint-Listenkonfiguration

So verbinden Sie AEM Forms mit Ihrer Microsoft® SharePoint-Liste:

1. Wechseln Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie in der Dropdown-Liste auf **[!UICONTROL Erstellen]** > **[!UICONTROL SharePoint-Liste]**. Der SharePoint-Konfigurationsassistent wird angezeigt.
1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL OAuth-URL]** an. Informationen zum Abrufen der Client-ID, des Client-Geheimnisses und der Mandanten-ID für die OAuth-URL finden Sie in der [Dokumentation von Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
   * Sie können die `Client ID` und das `Client Secret` Ihrer App über das Microsoft® Azure-Portal abrufen.
   * Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` durch die URL Ihrer Autoreninstanz.
   * Fügen Sie die API-Berechtigungen `offline_access` und `Sites.Manage.All` auf der Registerkarte **Microsoft® Graph** hinzu, um Lese- und Schreibberechtigungen bereitzustellen. Fügen Sie die Berechtigung `AllSites.Manage` auf der Registerkarte **Sharepoint**  hinzu, um remote mit SharePoint-Daten zu interagieren.
   * Verwenden der OAuth-URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

     >[!NOTE]
     >
     > Ob das Feld **Client-Geheimnis** obligatorisch oder optional ist, hängt von der Konfiguration Ihrer Azure Active Directory-Anwendung ab. Wenn Ihre Anwendung so konfiguriert ist, dass sie ein Client-Geheimnis verwendet, ist die Angabe des Client-Geheimnisses obligatorisch.

1. Klicken Sie auf **[!UICONTROL Verbinden]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.
1. Wählen Sie **[!UICONTROL SharePoint-Site]** und **[!UICONTROL SharePoint-Liste]** aus der Dropdown-Liste.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für die Microsoft® SharePoint-Liste zu erstellen.

### Zertifikatbasierte Authentifizierung {#certificate-based-authentication}

<span class="preview"> Zertifikatbasierte Authentifizierung für die SharePoint-Listenkonfiguration wird vom Early-Adopter-Programm unterstützt. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

Im Konfigurationsassistenten SharePoint-Liste :

1. Legen Sie **[!UICONTROL Authentifizierungstyp]** auf **Zertifikatbasierte Authentifizierung** fest.
1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Zertifikatalias]**, **[!UICONTROL Mandanten-ID]** und **[!UICONTROL Mandantenname]**.
1. Geben Sie die **[!UICONTROL SharePoint-Site]** URL ein, überprüfen Sie bei Bedarf die Site-Verbindung und wählen Sie die **[!UICONTROL SharePoint-Liste]**.
1. Klicken Sie auf **[!UICONTROL Verbinden]**, um die Verbindung zu überprüfen, und klicken Sie dann auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern.

Im folgenden Screenshot wird die Konfiguration der SharePoint-Liste mit **zertifikatbasierter Authentifizierung** angezeigt:

![Konfiguration der SharePoint-Liste mit zertifikatbasierter Authentifizierung](/help/forms/assets/sharepoint-list-certificate-auth-configuration.png){width=50%, height=50%, align=center}

Um das Zertifikat für AEM und Microsoft Azure vorzubereiten, führen Sie die folgenden Schritte in AEM aus und registrieren Sie dann das öffentliche Zertifikat in Microsoft Azure.

**In AEM**

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
1. Suchen Sie nach **[!UICONTROL fd-cloudservice]**, wählen Sie den Benutzer aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Öffnen Sie die **[!UICONTROL Keystore]** . Wenn noch kein KeyStore erstellt wurde, klicken Sie auf **[!UICONTROL KeyStore erstellen]** und füllen Sie die Eingabeaufforderungen aus, um das KeyStore-Kennwort festzulegen.
1. Fügen Sie den privaten Schlüssel zum Keystore hinzu: Erweitern Sie **[!UICONTROL Privaten Schlüssel aus Keystore-Datei hinzufügen]** und laden Sie Ihre **.jks-** hoch.
1. Geben Sie einen **[!UICONTROL Alias]** ein, der dem **[!UICONTROL Zertifikatalias]** in der SharePoint-Listenkonfiguration entspricht, senden Sie das Schlüsselmaterial und klicken Sie dann auf **[!UICONTROL Speichern und schließen]**.

Der Screenshot zeigt den KeyStore, nachdem das Zertifikat hinzugefügt wurde. Der **[!UICONTROL Alias]** muss mit dem **[!UICONTROL Zertifikatalias]** in der Cloud-Konfiguration der SharePoint-Liste übereinstimmen:

![fd-cloudservice-user-Keystore mit Zertifikatalias](/help/forms/assets/fd-cloudservice-keystore-certificate.png){width=50%, height=50%, align=center}

**In Microsoft Azure**

1. Öffnen Sie Ihre Anwendungsregistrierung und navigieren Sie zu **Zertifikate und Geheimnisse** > **Zertifikate**.
1. Wählen Sie **Zertifikat hochladen** und laden Sie die Zertifikatdatei (öffentlichen Schlüssel) hoch, der Azure für das Programm vertrauen muss.

Der Screenshot zeigt die Registerkarte **Zertifikate** im Azure-Portal, wo Sie das Zertifikat für die App-Registrierung hochladen:

![Zertifikate und Geheimnisse für die Registrierung der Azure-App](/help/forms/assets/azure-app-registration-sharepoint-certificates.png){width=50%, height=50%, align=center}

## &#x200B;2. Verwenden von Senden mit Formulardatenmodell (FDM) in einem adaptiven Formular {#use-submit-using-fdm}

Sie können die erstellte SharePoint-Listenkonfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument in einer SharePoint-Liste zu speichern. Führen Sie die folgenden Schritte aus, um eine SharePoint-Liste in einem adaptiven Formular zu verwenden:

1. [Erstellen eines Formulardatenmodells (FDM) mithilfe einer Microsoft® SharePoint-Listenkonfiguration](/help/forms/create-form-data-models.md)
1. [Konfigurieren des Formulardatenmodells (FDM) zum Abrufen und Senden von Daten](/help/forms/work-with-form-data-model.md#configure-services)
1. [Erstellen eines adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
1. [Konfigurieren einer Sendeaktion mit einem Formulardatenmodell (FDM)](/help/forms/using-form-data-model.md)

Wenn Sie das Formular absenden, werden die Daten im angegebenen Microsoft® Sharepoint-Listenspeicher gespeichert.

>[!NOTE]
>
> Die folgenden Spaltentypen werden in der Microsoft® SharePoint-Liste nicht unterstützt:
>
> * Bildspalte
> * Metadatenspalte
> * Personenspalte
> * Externe Datenspalte

## Verwandte Artikel

{{af-submit-action}}
