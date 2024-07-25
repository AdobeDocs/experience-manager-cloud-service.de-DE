---
Title: How to configure a SharePoint Site with limited access using authorization scope?
Description: Learn how to configure SharePoint Site with limited access using the authorization scope.
keywords: Wie konfiguriere ich SharePoint Site mit eingeschränktem Zugriff?, Konfigurieren von SharePoint mit eingeschränktem Zugriff, Verwenden des Autorisierungsbereichs zum Beschränken des Zugriffs für SharePoint Site.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 4962c058e2cc2135dd3626655ba7b21dbdcbd455
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 24%

---


<span class="preview"> Die Funktion ist im Programm für frühe Anwender verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

# Konfigurieren von SharePoint-Sites mit eingeschränktem Zugriff über den Autorisierungsbereich

Der eingeschränkte oder eingeschränkte Zugriff soll die Sicherheitsverwaltung verbessern, indem Administratoren den Benutzerzugriff auf eine bestimmte SharePoint-Site oder eine Gruppe von SharePoint-Sites steuern können. Die Berechtigungsebene ist nützlich, wenn Sie einem Benutzer oder einer Gruppe Zugriff auf eine bestimmte Site gewähren müssen, ohne ihm zu ermöglichen, andere nicht zulässige SharePoint Sites anzuzeigen.

## Vorteile bei der Konfiguration von SharePoint Site mit eingeschränktem Zugriff

Vorteile für eingeschränkten Zugriff auf die SharePoint-Site:

* **Verbesserte Sicherheit**: Durch die Beschränkung des Zugriffs können Sie sicherstellen, dass nur autorisierte Mitarbeiter in der Lage sind, sensible Informationen anzuzeigen oder zu bearbeiten, wodurch das Risiko eines unbefugten Zugriffs verringert wird.

* **Grundsatz der geringsten Berechtigung**: Es bietet Benutzern die für die Ausführung ihrer Auftragsfunktionen erforderlichen Mindestzugriffsebenen - oder Berechtigungen. Dadurch wird die Exposition der einzelnen Benutzer gegenüber sensiblen Teilen des Netzwerks minimiert, die vor potenziellen internen Bedrohungen geschützt werden können.

* **Datenschutz**: Der eingeschränkte Zugriff hilft beim Schutz kritischer Daten vor der Exposition. Dadurch wird sichergestellt, dass nur Benutzer, die die Daten sehen müssen, darauf zugreifen können, was für die Einhaltung der Datenschutzbestimmungen von wesentlicher Bedeutung ist.

* **Vermeidung versehentlicher Datenverluste**: Da weniger Personen Inhalte ändern können, ist die Wahrscheinlichkeit einer versehentlichen Löschung oder Änderung wichtiger Daten erheblich verringert.

* **Kontrollierter Datenfluss**: Dieser ermöglicht die Steuerung des Informationsflusses innerhalb und außerhalb der Organisation und stellt sicher, dass die Daten nicht in den falschen Händen landen.

## Konfigurieren von SharePoint mit eingeschränktem Zugriff über den Autorisierungsbereich

Gehen Sie wie folgt vor, um SharePoint Sites mit eingeschränktem Zugriff mithilfe von Autorisierungsbereichen zu konfigurieren:

1. [Erstellen Sie eine Anwendung mit der ](#create-an-application-with-the-limited-permission-in-the-azure-portal)
1. [Festlegen des Autorisierungsumfangs auf AEM Instanz](#set-the-authorization-scope-at-aem-instance)

### Erstellen einer Anwendung mit eingeschränkter Berechtigung im Azure-Portal

Erstellen Sie eine Anwendung im [Microsoft Azure Portal](https://portal.azure.com/#home) mit dem Berechtigungsbereich `Sites.Selected` in der Diagramm-API von Microsoft.

![Ausgewählte SharePoint-Site](/help/forms/assets/sharepoint-selected-site.png)

Informationen zum Abrufen von `Client ID`, `Client Secret` und `Tenant ID` für `OAuth URL` finden Sie in der [Microsoft®-Dokumentation](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
* Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` durch die URL Ihrer Autoreninstanz.
* Fügen Sie den Berechtigungsbereich `offline_access` und `Sites.Selected` in der Diagramm-API von Microsoft hinzu, um eingeschränkten Zugriff auf Sites bereitzustellen.
* Für OAuth-URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

Für die Verwendung der API-Berechtigung `Sites.Selected` ist eine Anwendung erforderlich, die im Azure-Portal registriert ist und über die entsprechenden Berechtigungen für SharePoint Online Sites verfügt. Durch diese Einrichtung wird sichergestellt, dass die Anwendung über die erforderliche Autorisierung verfügt, um innerhalb des definierten Anwendungsbereichs mit der SharePoint-Site zu interagieren, und so den erforderlichen eingeschränkten Zugriff bietet.

Anweisungen zum Entwickeln von Anwendungen, die `Sites.Selected` -Berechtigungen für SharePoint Online Sites verwenden, finden Sie im [Artikel](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/develop-applications-that-use-sites-selected-permissions-for-spo/ba-p/3790476) .

### Festlegen des Autorisierungsumfangs auf AEM Instanz

Um einen eingeschränkten Zugriff auf eine Microsoft SharePoint-Site zu ermöglichen, ist es wichtig, den Autorisierungsbereich richtig festzulegen. So legen Sie den Autorisierungsbereich fest und verbinden AEM Forms mit Ihrem Microsoft® SharePoint-Speicher:

1. Gehen Sie zu Ihrer **AEM Forms-Autoreninstanz** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sobald Sie **[!UICONTROL Microsoft® SharePoint]** auswählen, werden Sie zum **[!UICONTROL SharePoint-Browser]** weitergeleitet.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL SharePoint-Dokumentenbibliothek]** in der Dropdown-Liste. Der SharePoint-Konfigurationsassistent wird angezeigt.

   ![SharePoint Site Limited Site Access](/help/forms/assets/sharepoint-doc-library-limited-scopes.png)

1. Geben Sie den **[!UICONTROL Titel]**, die **[!UICONTROL Client-ID]** und den **[!UICONTROL Client-Geheimnis]** an. Informationen zum Abrufen der Client-ID und des Client-Geheimnisses finden Sie in der [Microsoft®-Dokumentation](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).

1. Verwenden Sie die OAuth-URL als `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

   >[!NOTE]
   >
   > Ob das Feld **Client-Geheimnis** obligatorisch oder optional ist, hängt von der Konfiguration Ihrer Azure Active Directory-Anwendung ab. Wenn Ihre Anwendung so konfiguriert ist, dass sie ein Client-Geheimnis verwendet, ist die Angabe des Client-Geheimnisses obligatorisch.

1. Fügen Sie die `offline_access Sites.Selected` im Feld `Authorization Scope` hinzu. Wenn Sie den Bereich `offline_access Sites.Selected` in das Textfeld `Authorization Scope` einfügen, wird das Textfeld `SharePoint Site ID` auf dem Bildschirm angezeigt.

1. Geben Sie die SharePoint-Site-ID an. Informationen zum Abrufen der SharePoint Site-ID finden Sie im Abschnitt [Zusätzliche Byte](#extra-bytes) .

1. Klicken Sie auf **[!UICONTROL Überprüfen Sie die Site-Verbindung]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.

1. Wählen Sie jetzt **SharePoint-Site** > **Dokumentbibliothek** > **SharePoint-Ordner**, um die Daten zu speichern.

   >[!NOTE]
   >
   >* Standardmäßig ist `forms-ootb-storage-adaptive-forms-submission` auf der ausgewählten SharePoint-Site vorhanden.
   >* Erstellen Sie einen Ordner als `forms-ootb-storage-adaptive-forms-submission`, wenn er nicht bereits in der `Documents`-Bibliothek der ausgewählten SharePoint-Site vorhanden ist, indem Sie auf **Ordner erstellen** klicken.

Jetzt können Sie diese [SharePoint Sites-Konfiguration für die Sendeaktion in einem adaptiven Formular](/help/forms/configure-submit-action-sharepoint.md#use-sharepoint-document-library-configuration-in-an-adaptive-form-use-sharepoint-configuartion-in-af) verwenden.

## Zusätzliche Byte

So rufen Sie den Wert von `SharePoint Site ID` ab:
1. Navigieren Sie zu den [Microsoft Graph Explorer-APIs](https://developer.microsoft.com/en-us/graph/graph-explorer).
1. Klicken Sie im linken Bereich unter den `SharePoint Sites` -APIs auf `Search for a SharePoint site by keyword`.
1. Ersetzen Sie den Platzhalter `contoso` durch den tatsächlichen Namen Ihrer SharePoint-Site, um die entsprechende Site-ID abzurufen.

   ![SharePoint Document Library ID](/help/forms/assets/sharepoint-site-id.png)

Wenn Sie auf die Schaltfläche `Run Query` klicken, wird die Site-ID auf dem Bildschirm angezeigt.