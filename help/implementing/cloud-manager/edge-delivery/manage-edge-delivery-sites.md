---
title: Verwalten von Edge Delivery-Sites in Cloud Manager
description: Erfahren Sie, wie Sie einer Edge Delivery-Site eine CDN-Konfiguration hinzufügen oder eine Edge Delivery-Site löschen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: 603602dc70f9d7cdf78b91b39e3b7ff5090a6bc0
workflow-type: ht
source-wordcount: '712'
ht-degree: 100%

---

# Verwalten von Edge Delivery-Sites in Cloud Manager {#manage-edge-delivery-sites}

Erfahren Sie, wie Sie Edge Delivery-Sites in Cloud Manager verwalten, indem Sie einer vorhandenen Site eine CDN-Konfiguration hinzufügen. oder eine Edge Delivery-Site löschen.

## Hinzufügen einer Domain-Zuordnung zu einer vorhandenen Edge Delivery-Site {#add-cdn-to-edge-delivery-site}

Siehe [Hinzufügen einer Domain-Zuordnung](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md).

## Umbenennen einer Edge Delivery-Site (#rename-edge-delivery-site)

Es gibt verschiedene Gründe, um in Adobe Cloud Manager eine Edge Delivery-Site umzubenennen:

* **Klarheit und Organisation**: Durch eine Umbenennung lässt sich der Zweck der Site oder ihrer zugehörigen Umgebung (z. B. Produktion, Staging) besser beschreiben.
* **Vermeiden von Verwirrung**: Wenn mehrere Sites vorhanden sind, kann durch eine Umbenennung leichter zwischen ihnen unterscheiden werden. Dadurch wird die Wahrscheinlichkeit verringert, dass Konfigurationen oder Aktualisierungen auf die falsche Site angewendet werden.
* **Standardisierung**: Durch eine Umbenennung kann einer einheitlichen Namenskonvention gefolgt werden, die den Richtlinien Ihrer Organisation entspricht und so das Management und Auditing vereinfacht.

**So benennen Sie eine Edge Delivery-Site um:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem eine Edge Delivery-Site hinzugefügt werden soll.
1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie in der Edge Delivery-Site-Tabelle auf die Auslassungspunkte am Ende einer Zeile, deren Site umbenannt werden soll.
Klicken Sie auf **Umbenennen**.
   * Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen. Klicken Sie unter der Überschrift **Services** auf ![Web-Seiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.
Klicken Sie in der Edge Delivery-Site-Tabelle auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site umbenannt werden soll. Klicken Sie auf **Umbenennen**.

1. Geben Sie im Dialogfeld **Edge Delivery-Site bearbeiten** den neuen Namen der Site in das Feld **Site-Name** ein.

1. Klicken Sie auf **Bearbeiten**.

## Löschen einer Edge Delivery-Site {#delete-edge-delivery-site}

Wenn Sie eine Edge Delivery Services-Site löschen, werden auch alle zugehörigen CDN-Konfigurationen entfernt. Diese Aktion trennt die Verbindung zwischen benutzerdefinierten Domains und der Site. Weitere Informationen finden Sie unter „CDN-Konfigurationen“. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**So löschen Sie eine Edge Delivery-Site:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem eine Edge Delivery-Site hinzugefügt werden soll.
1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie in der Edge Delivery-Site-Tabelle auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site entfernt werden soll.
Klicken Sie auf ![Symbol zum Löschen der Edge Delivery-Site](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Löschen** und dann erneut auf **Löschen**, um das Entfernen der Site zu bestätigen.

     ![Hinzufügen einer Edge Delivery-Site auf der Registerkarte „Edge Delivery“](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen. Klicken Sie unter der Überschrift **Services** auf ![Symbol der Web-Seite für Edge Delivery-Sites](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.
Klicken Sie in der Tabelle der Edge Delivery-Sites auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site entfernt werden soll. Klicken Sie auf ![Symbol zum Löschen der Edge Delivery-Site](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Löschen** und dann erneut auf **Löschen**, um das Entfernen der Site zu bestätigen.

     ![Hinzufügen einer Edge Delivery-Site über die Schaltfläche „Edge Delivery-Sites“](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Verwalten einer Edge Delivery-Site zwischen Helix 4 und Helix 5

Verwenden Sie den API-Endpunkt `/program/{programId}/site/{siteId}`, um eine Edge Delivery-Site zwischen Helix 4 und Helix 5 zu migrieren.

>[!IMPORTANT]
>
>CDN-Konfigurationen für Helix 4-Websites können nicht automatisch zu Helix 5 migriert werden. Diese Einschränkung besteht, da die Produktions-Sites der Kundinnen und Kunden möglicherweise weiterhin auf Helix 4 ausgeführt werden, während sich deren Helix 5-Versionen noch in der Entwicklung befinden.

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
