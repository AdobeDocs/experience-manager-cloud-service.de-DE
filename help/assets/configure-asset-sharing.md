---
title: Freigeben von Assets, Ordnern und Sammlungen als Link
description: In diesem Artikel wird beschrieben, wie Sie Assets, Ordner und Sammlungen in Experience Manager Assets als Hyperlink freigeben.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Asset-Linkfreigabe konfigurieren {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Sie generieren die URL für Assets, die Sie für Benutzer freigeben möchten, im Dialogfeld „Linkfreigabe“. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei AEM Assets anmelden müssen.

>[!NOTE]
>
>Wenn Sie Links von Ihrer AEM Authoring-Instanz an externe Entitäten freigeben möchten, stellen Sie sicher, dass Sie nur die folgenden URLs für `GET` Anforderungen bereitstellen. Sperren Sie andere URLs, um sicherzustellen, dass Ihre AEM Author-Instanz sicher ist.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


## Konfigurieren von Day CQ Mail Service {#configmailservice}

Bevor Sie Assets als Links freigeben können, konfigurieren Sie den E-Mail-Dienst.

1. Tippen/Klicken Sie auf das AEM-Logo und navigieren Sie dann zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web Console]**.
1. Wählen Sie in der Liste der Dienste **[!UICONTROL Day CQ Mail Service]** aus.
1. Klicken Sie auf das Symbol **[!UICONTROL Bearbeiten]** neben dem Dienst und konfigurieren Sie die folgenden Parameter für den **Day CQ Mail Service]** mit den angegebenen Details zu ihren Namen:

   * SMTP-Server-Hostname: email server host name
   * SMTP-Server-Anschluss: email server port
   * SMTP-Benutzer: email server user name
   * SMTP-Kennwort: email server password

1. Klicken oder tippen Sie auf **Speichern**.

## Konfigurieren der maximal zulässigen Datengröße {#maxdatasize}

Wenn Sie Assets herunterladen, die mithilfe der Linkfreigabe-Funktion freigegeben wurden, komprimiert AEM die Asset-Hierarchie aus dem Repository und gibt anschließend das Asset in einer ZIP-Datei zurück. Da jedoch die Datenmenge, die in einer ZIP-Datei komprimiert werden kann, nicht begrenzt wird, führt das bei großen komprimierten Datenmengen zu Speicherfehlern in JVM. To secure the system from a potential denial of service attack due to this situation, configure the maximum size using the **Max Content Size (uncompressed)** parameter for Day CQ DAM Adhoc Asset Share Proxy Servlet in Configuration Manager. Wenn die unkomprimierte Größe des Assets den konfigurierten Wert überschreitet, werden Asset-Download-Anforderungen abgelehnt. Der Standardwert lautet 100 MB.

1. Tippen/Klicken Sie auf das AEM-Logo und gehen Sie dann zu **Werkzeuge** > **Vorgänge** > **Web Console**.
1. From the web console, locate the **Day CQ DAM Adhoc Asset Share Proxy Servlet** configuration.
1. Öffnen Sie die **Day CQ DAM Adhoc Asset Share Proxy Servlet**-Konfiguration im Bearbeitungsmodus und ändern Sie den Wert des Parameters **Max. Inhaltsgröße (nicht komprimiert)**.
1. Speichern Sie die Änderungen.

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->
