---
title: Verwalten von Edge Delivery-Sites in Cloud Manager
description: Erfahren Sie, wie Sie einer Edge Delivery-Site eine CDN-Konfiguration hinzufügen oder eine Edge Delivery-Site löschen.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: 069e94e230b856fba15c3f465c966a5bf6b0ac46
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 43%

---

# Verwalten von Edge Delivery-Sites in Cloud Manager {#manage-edge-delivery-sites}

Erfahren Sie, wie Sie Edge Delivery-Sites in Cloud Manager verwalten, indem Sie einer vorhandenen Site eine CDN-Konfiguration hinzufügen. oder eine Edge Delivery-Site löschen.

## Hinzufügen einer Domain-Zuordnung zu einer vorhandenen Edge Delivery-Site {#add-cdn-to-edge-delivery-site}

Siehe [Hinzufügen einer Domain-Zuordnung](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md).

## Umbenennen einer Edge Delivery-Site (#rename-edge-delivery-site)

In Adobe Cloud Manager können Sie eine Edge Delivery-Site aus verschiedenen Gründen umbenennen:

* **Klarheit und Organisation**: Durch eine Umbenennung lässt sich der Zweck der Site oder ihrer zugehörigen Umgebung (z. B. Produktion, Staging) besser beschreiben.
* **Verwirrung vermeiden**: Wenn mehrere Websites verwendet werden, kann das Umbenennen dabei helfen, zwischen ihnen zu unterscheiden, wodurch das Risiko der Anwendung von Konfigurationen oder Aktualisierungen auf eine falsche Site reduziert wird.
* **Standardisierung**: Durch eine Umbenennung kann einer einheitlichen Namenskonvention gefolgt werden, die den Richtlinien Ihrer Organisation entspricht und so das Management und Auditing vereinfacht.

**So benennen Sie eine Edge Delivery-Site um:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem eine Edge Delivery-Site hinzugefügt werden soll.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf der **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie in der Edge Delivery-Site-Tabelle auf die Auslassungspunkte am Ende einer Zeile, deren Site Sie umbenennen möchten.
Klicken Sie auf **Umbenennen**.
   * Klicken Sie oben links auf der Seite auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Menü anzuzeigen. Klicken Sie unter der Überschrift **Services** auf ![Web-Seiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Klicken Sie in der Edge Delivery-Site![Tabelle auf ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)Mehr-Symbol) am Ende einer Zeile, deren Site Sie umbenennen möchten. Klicken Sie auf **Umbenennen**.

1. Geben Sie im Dialogfeld **Edge Delivery-Site bearbeiten** den neuen Namen der Site in das Feld **Site-Name** ein.
1. Klicken Sie auf **Bearbeiten**.


## Aktivieren der Veröffentlichungsebene für eine Edge Delivery-Site (Beta) {#activate-publish-tier-for-eds}

>[!NOTE]
>
>Die hier beschriebene Veröffentlichungsfunktion befindet sich in Beta. Um sich der Beta anzuschließen, senden Sie eine E-Mail an [](mailto:grp-beta_xwalk-publish_config@adobe.com)grp-beta_xwalk-publish_config@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

Diese Funktion gilt nur für Edge Delivery-Sites, die mit der Option **AEM Authoring** in Programmen erstellt wurden, bei denen die Funktion für die flexible Veröffentlichungsebene aktiviert ist.

Wenn Ihre Edge Delivery-Site das Authoring mit AEM verwendet, stellt Adobe die Veröffentlichungsebene nicht standardmäßig bereit, da Edge Delivery die Inhaltsbereitstellung übernimmt. Sie können die Veröffentlichungsebene jedoch jederzeit aktivieren, wenn dies für Ihre Site erforderlich ist. Dies ist beispielsweise der Fall, wenn Sie die herkömmliche Veröffentlichung von AEM zusammen mit Edge Delivery unterstützen möchten.

Nachdem Ihre Edge Delivery-Site erstellt wurde und ihr Status in Cloud Manager **Verifiziert** angezeigt wird, können Sie Inhalte mit dem universellen Editor von AEM erstellen und veröffentlichen.

**So greifen Sie über Cloud Manager auf den universellen Editor zu:**

1. Suchen Sie auf der Registerkarte Edge Delivery in der Liste Edge Delivery Sites Ihre Site.

   ![Veröffentlichen von Inhalten von der AEM-Autoreninstanz in Edge Delivery.](/help/implementing/cloud-manager/edge-delivery/assets/eds-content-source-link.png)

1. Klicken Sie auf **Link** Content Source&quot; in der Zeile der Site. Der Link öffnet die Seite des universellen Editors von AEM, in der Sie Inhalte für Ihre Site erstellen und bearbeiten können.—>

**So aktivieren Sie die Veröffentlichungsebene für eine Edge Delivery-Site:**

1. Klicken Sie auf der **Programmübersicht** auf der Registerkarte **Versand veröffentlichen** auf der Karte **Umgebung** auf das Informationssymbol.

1. Wählen Sie im Informations-Popup unter **Veröffentlichungs-URL** die Option **Zum Aktivieren klicken** aus, um die Bereitstellung der Veröffentlichungsebene in der Cloud Manager-Benutzeroberfläche zu aktivieren.

   ![Klicken Sie, um die Bereitstellung der Veröffentlichungsebene zu aktivieren](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/click-to-activate-publish-tier-capabilities.png)

1. Klicken Sie im Dialogfeld Veröffentlichungsebene aktivieren auf **Aktivieren**.

   ![Dialogfeld „Veröffentlichungsebene aktivieren“](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/activate-publish-tier.png)

   Nach der Aktivierung wird die Veröffentlichungsebene automatisch bereitgestellt. Alternativ kann die Veröffentlichungsebene automatisch bereitgestellt werden, wenn der Autor versucht, Inhalte direkt über die AEM-Benutzeroberfläche zu veröffentlichen.

   Nachdem die Veröffentlichungsebene aktiviert und erfolgreich bereitgestellt wurde, wird der **Zum Aktivieren klicken**-Link deaktiviert/nicht mehr verfügbar.

* **Von AEM-**: Klicken Sie in der Authoring-Oberfläche von AEM auf **Quick Publish**, um Inhalte direkt auf Ihrer Edge Delivery-Site zu veröffentlichen. Die Veröffentlichungsebene ist für diesen Vorgang nicht erforderlich, wenn die Bereitstellung von Edge Delivery verarbeitet wird.

Nach der Veröffentlichung können Sie eine Vorschau Ihres Inhalts unter der `.page` URL Ihrer Site anzeigen oder ihn live unter der `.live` URL anzeigen.—>

>[!NOTE]
>
>Durch das Aktivieren der Veröffentlichungsebene wird eine Veröffentlichungsinfrastruktur zu Ihrer Umgebung hinzugefügt. Diese Funktion wirkt sich auf den Ressourcenverbrauch Ihres Programms aus. Informationen zum Konfigurieren, ob die Veröffentlichungsebene auf Programmebene erforderlich ist, finden Sie unter [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).


## Löschen einer Edge Delivery-Site {#delete-edge-delivery-site}

Wenn Sie eine Edge Delivery Services-Site löschen, werden auch alle zugehörigen CDN-Konfigurationen entfernt. Diese Aktion trennt die Verbindung zwischen benutzerdefinierten Domains und der Site. Weitere Informationen finden Sie unter „CDN-Konfigurationen“. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**So löschen Sie eine Edge Delivery-Site:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem eine Edge Delivery-Site hinzugefügt werden soll.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf der **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie in der Edge Delivery-Site![Tabelle auf ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)Mehr-Symbol) am Ende einer Zeile, deren Site Sie entfernen möchten.
Klicken Sie auf ![Edge Delivery-Site-](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) löschen **Löschen** und klicken Sie dann erneut auf **Löschen**, um das Entfernen der Site zu bestätigen.

     ![Hinzufügen einer Edge Delivery-Site auf der Registerkarte „Edge Delivery“](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Klicken Sie oben links auf der Seite auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Menü anzuzeigen. Klicken Sie unter der Überschrift **Services** auf ![Webseite für Edge Delivery Sites-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Klicken Sie in der Edge Delivery-Site![Tabelle auf ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)Mehr-Symbol) am Ende einer Zeile, deren Site Sie entfernen möchten. Klicken Sie auf ![Edge Delivery-Site-](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) löschen **Löschen** und klicken Sie dann erneut auf **Löschen**, um das Entfernen der Site zu bestätigen.

     ![Hinzufügen einer Edge Delivery-Site über die Schaltfläche „Edge Delivery-Sites“](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Verwalten einer Edge Delivery-Site zwischen Helix 4 und Helix 5

Verwenden Sie den API-Endpunkt `/program/{programId}/site/{siteId}`, um eine Edge Delivery-Site zwischen Helix 4 und Helix 5 zu migrieren.

>[!IMPORTANT]
>
>CDN-Konfigurationen für Helix 4-Websites können nicht automatisch zu Helix 5 migriert werden. Diese Einschränkung besteht, da die Produktionsstandorte der Kunden weiterhin auf Helix 4 ausgeführt werden, während sich deren Helix 5-Versionen noch in der Entwicklung befinden.

**Voraussetzungen**

* Der `sitename` muss bereits vorhanden sein.
* Kenntnis der entsprechenden `branchName`-, Helix-`version`- und `repo`-Werte.
* Durch die Migration werden nur `branchName`, Helix `version` und `repo` geändert. Das Inhaber-Feld kann nicht geändert werden.

**API-Format**

```http
PUT /api/program/{programId}/site/{siteId}
```

**Parameter des Anfragetexts**
Erstellt eine Überschreibung für eine Edge Delivery-Site, um den im Anfragetext angegebenen Ursprung zu erzwingen.

```json
{
  "sitename": "<required site name>",
  "branchName": "<git branch>",
  "version": "v4" | "v5",
  "repo": "<git repository name>"
}
```

### Beispiel 1: Zu Helix 5 migrieren

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix5",
  "branchName": "branch",
  "version": "v5",
  "repo": "my-website"
}
```

**Ursprungs-URL-Ergebnis**
Gibt eine Edge Delivery-Site mit der folgenden Ursprungs-URL zurück:

`"origin": "branch--my-website–Teo48.aem.live"`


### Beispiel 2: Zu Helix 4 migrieren

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix4",
  "branchName": "branch",
  "version": "v4",
  "repo": "my-website"
}
```

**Ursprungs-URL-Ergebnis**
Gibt eine Edge Delivery-Site mit der folgenden Ursprungs-URL zurück:

`"origin": "branch--my-website--Teo48.hlx.live"`

### Beispiel 3: Site ohne Repo nach Helix 5 migrieren

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-reposless-website",
  "branchName": "main",
  "version": "v5",
  "repo": "my-reposless-website"
}
```

**Ursprungs-URL-Ergebnis**
Gibt eine Edge Delivery-Site mit der folgenden Ursprungs-URL zurück:

`"origin": "main--my-repoless-website--Teo48.aem.live"`

## Einreichen eines Support-Tickets {#eds-support-ticket}

{{support-ticket}}
