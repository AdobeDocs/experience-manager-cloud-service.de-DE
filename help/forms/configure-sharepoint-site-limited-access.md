---
title: Wie wird eine SharePoint-Site mit eingeschränktem Zugriff unter Verwendung des Autorisierungsumfangs konfiguriert?
description: Erfahren Sie, wie Sie SharePoint Site mit eingeschränktem Zugriff mithilfe des Autorisierungsumfangs konfigurieren.
keywords: Konfigurieren einer SharePoint-Site mit eingeschränktem Zugriff?, Konfigurieren von SharePoint mit eingeschränktem Zugriff, Verwenden des Autorisierungsumfangs zum Beschränken des Zugriffs für die SharePoint-Site.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 3230bab2-c1aa-409d-9f01-c42cf88b1135
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 24%

---

# Konfigurieren von SharePoint-Sites mit eingeschränktem Zugriff mithilfe des Autorisierungsumfangs

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

Durch den eingeschränkten oder eingeschränkten Zugriff soll die Sicherheitsverwaltung verbessert werden, indem Admins die Möglichkeit erhalten, den Benutzerzugriff auf eine bestimmte SharePoint-Site oder eine Gruppe von SharePoint-Sites zu steuern. Die Berechtigungsstufe ist nützlich, wenn Sie einem Benutzer oder einer Gruppe Zugriff auf eine bestimmte Site gewähren müssen, ohne ihm das Anzeigen anderer nicht zulässiger SharePoint-Sites zu ermöglichen.

## Vorteile der Konfiguration von SharePoint Site mit eingeschränktem Zugriff

Vorteile für eingeschränkten Zugriff auf die SharePoint-Site:

* **Verbesserte Sicherheit**: Durch die Einschränkung des Zugriffs können Sie sicherstellen, dass nur autorisierte Mitarbeiter sensible Informationen anzeigen oder bearbeiten können, wodurch das Risiko des unbefugten Zugriffs reduziert wird.

* **Prinzip der geringsten**: Es bietet Benutzenden die minimalen Zugriffsebenen (oder -berechtigungen), die für die Ausführung ihrer Aufgabenfunktionen erforderlich sind. Dadurch wird die Anfälligkeit der einzelnen Benutzer gegenüber sensiblen Teilen des Netzwerks minimiert, was sie vor potenziellen internen Bedrohungen schützen kann.

* **Datenschutz**: Der eingeschränkte Zugriff hilft beim Schutz kritischer Daten vor einer Gefährdung. Dadurch wird sichergestellt, dass nur Benutzer, die die Daten einsehen müssen, darauf zugreifen können. Dies ist für die Einhaltung von Datenschutzbestimmungen unerlässlich.

* **Schutz vor versehentlichem Datenverlust**: Wenn weniger Personen Inhalte ändern können, wird die Wahrscheinlichkeit versehentlicher Löschungen oder Änderungen wichtiger Daten erheblich reduziert.

* **Kontrollierter Datenfluss**: Hilft bei der Kontrolle des Informationsflusses innerhalb und außerhalb des Unternehmens, um sicherzustellen, dass die Daten nicht in falsche Hände geraten.

## Konfigurieren von SharePoint mit eingeschränktem Zugriff über den Autorisierungsumfang

Gehen Sie wie folgt vor, um SharePoint Sites mit eingeschränktem Zugriff mithilfe von Autorisierungsumfängen zu konfigurieren:

1. [Erstellen eines Programms mit dem &#x200B;](#create-an-application-with-the-limited-permission-in-the-azure-portal)
1. [Festlegen des Autorisierungsumfangs bei der AEM-Instanz](#set-the-authorization-scope-at-aem-instance)

### Erstellen einer Anwendung mit eingeschränkter Berechtigung im Azure-Portal

Erstellen Sie eine Anwendung im [Microsoft Azure](https://portal.azure.com/#home)Portal mit dem `Sites.Selected` Berechtigungsbereich in der Graph-API von Microsoft.

![SharePoint ausgewählte Site](/help/forms/assets/sharepoint-selected-site.png)

Informationen zum Abrufen von `Client ID`, `Client Secret` und `Tenant ID` für `OAuth URL` finden Sie in der [Dokumentation zu Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
* Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` durch die URL Ihrer Autoreninstanz.
* Fügen Sie den `offline_access` und `Sites.Selected` Berechtigungsbereich in der Graph-API von Microsoft hinzu, um eingeschränkten Zugriff auf Sites zu ermöglichen.
* Für OAuth-URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

Für die Verwendung der `Sites.Selected` API-Berechtigung ist eine im Azure-Portal registrierte Anwendung mit den entsprechenden Berechtigungen für SharePoint Online Sites erforderlich. Durch diese Einrichtung wird sichergestellt, dass die Anwendung über die erforderliche Autorisierung verfügt, um im definierten Umfang mit der SharePoint-Site zu interagieren, wodurch der erforderliche eingeschränkte Zugriff bereitgestellt wird.

Anweisungen zum Entwickeln von Anwendungen, die [&#x200B; Berechtigungen für SharePoint Online Sites verwenden, finden Sie &#x200B;](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/develop-applications-that-use-sites-selected-permissions-for-spo/ba-p/3790476) Blog-Artikel `Sites.Selected` Entwickeln von Anwendungen, die Sites verwenden.Ausgewählte Berechtigungen für SPO Sites .

### Festlegen des Autorisierungsumfangs bei der AEM-Instanz

Um den eingeschränkten Zugriff auf eine Microsoft SharePoint-Site zu ermöglichen, muss der Autorisierungsumfang korrekt festgelegt werden. So legen Sie den Autorisierungsumfang fest und verbinden AEM Forms mit Ihrem Microsoft® SharePoint-Speicher:

1. Gehen Sie zu Ihrer **AEM Forms-Autoreninstanz** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sobald Sie **[!UICONTROL Microsoft® SharePoint]** auswählen, werden Sie zum **[!UICONTROL SharePoint-Browser]** weitergeleitet.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL SharePoint-Dokumentenbibliothek]** in der Dropdown-Liste. Der SharePoint-Konfigurationsassistent wird angezeigt.

   ![SharePoint-Site: Eingeschränkter Site-Zugriff](/help/forms/assets/sharepoint-doc-library-limited-scopes.png)

1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]** und **[!UICONTROL Client-Geheimnis]** an. Informationen zum Abrufen der Client-ID und des Client-Geheimnisses finden Sie in der [Dokumentation zu Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).

1. Verwenden Sie als `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize` die OAuth-URL. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

   >[!NOTE]
   >
   > Ob das Feld **Client-Geheimnis** obligatorisch oder optional ist, hängt von der Konfiguration Ihrer Azure Active Directory-Anwendung ab. Wenn Ihre Anwendung so konfiguriert ist, dass sie ein Client-Geheimnis verwendet, ist die Angabe des Client-Geheimnisses obligatorisch.

1. Fügen Sie die `offline_access Sites.Selected` in das Feld `Authorization Scope` ein. Wenn Sie den `offline_access Sites.Selected` Bereich im `Authorization Scope` Textfeld hinzufügen, wird das `SharePoint Site ID` Textfeld auf dem Bildschirm angezeigt.

1. Geben Sie die SharePoint Site-ID an. Informationen zum Abrufen der SharePoint-Site-ID finden Sie im Abschnitt [Zusätzliche Bytes](#extra-bytes).

1. Klicken Sie **[!UICONTROL Site-Verbindung überprüfen]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.

1. Wählen Sie jetzt **SharePoint-Site** > **Dokumentbibliothek** > **SharePoint-Ordner**, um die Daten zu speichern.

   >[!NOTE]
   >
   >* Standardmäßig ist `forms-ootb-storage-adaptive-forms-submission` auf der ausgewählten SharePoint-Site vorhanden.
   >* Erstellen Sie einen Ordner als `forms-ootb-storage-adaptive-forms-submission`, wenn er nicht bereits in der `Documents`-Bibliothek der ausgewählten SharePoint-Site vorhanden ist, indem Sie auf **Ordner erstellen** klicken.

Jetzt können Sie diese [SharePoint Sites-Konfiguration für die Sendeaktion in einem adaptiven Formular &#x200B;](/help/forms/configure-submit-action-sharepoint.md#use-sharepoint-document-library-configuration-in-an-adaptive-form-use-sharepoint-configuartion-in-af).

## Zusätzliche Bytes

So rufen Sie den Wert der `SharePoint Site ID` ab:
1. Navigieren Sie zu den [Microsoft Graph Explorer-APIs](https://developer.microsoft.com/en-us/graph/graph-explorer).
1. Klicken Sie im linken Bereich unter den `SharePoint Sites`-APIs auf `Search for a SharePoint site by keyword`.
1. Ersetzen Sie den `contoso` durch den tatsächlichen Namen Ihrer SharePoint-Site, um die entsprechende Site-ID abzurufen.

   ![SharePoint-Dokumentbibliotheks-ID](/help/forms/assets/sharepoint-site-id.png)

Beim Klicken auf die Schaltfläche `Run Query` wird die Site-ID auf dem Bildschirm angezeigt.
