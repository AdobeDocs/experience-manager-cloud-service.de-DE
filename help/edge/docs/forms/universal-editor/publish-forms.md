---
title: Veröffentlichen von AEM-Formularen für Edge Delivery Services.
description: Veröffentlichen Sie Ihre Edge Delivery Services-Formulare schnell und nahtlos.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: e4a71d1a513bebed67b9571a483871dc16c36daa
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 100%

---

# Veröffentlichen Ihres adaptiven Formulars mit Edge Delivery Services

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Namen des Repositorys von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Name der Organisation „adobe“ und der Name des Repositorys „abc“.</span>


Wenn Ihr Formular fertig gestellt und einsatzbereit ist, können Sie es veröffentlichen, um es Ihrer Kundschaft zur Datenerfassung und -übermittlung zugänglich zu machen. Durch die Veröffentlichung wird sichergestellt, dass das Formular in Edge Delivery verfügbar ist, sodass die Benutzenden nahtlos damit interagieren können. Auf diese Weise kann Ihre Kundschaft das Formular in Echtzeit ausfüllen und übermitteln. Dadurch wird eine effiziente Datenerfassung und eine optimierte Verarbeitung gewährleistet.

## Voraussetzungen

* Ein Formular, das mit der **Vorlage „Edge Delivery Services“** erstellt wurde. [Weitere Informationen](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) zum Erstellen eines EDS-basierten Formulars.

## Veröffentlichen des Formulars

Sie können **EDS-basierte adaptive Formulare** in Edge Delivery veröffentlichen, indem Sie die folgenden Schritte ausführen:

<!--1. Select the **Adaptive Form** that you want to publish and click the **Edit** ![edit icon](/help/forms/assets/edit.svg) icon.
   ![Select EDS-Based Form](/help/forms/assets/select-eds-based-form.png)-->

1. Öffnen Sie Ihr adaptives Formular im Editor und klicken Sie in der oberen Leiste auf das Symbol **Veröffentlichen**.
   ![Klicken Sie auf „Veröffentlichen“](/help/forms/assets/publish-icon-eds-form.png)

1. Wenn Sie auf **Veröffentlichen** klicken, wird ein Bildschirm oder ein Popup angezeigt, in dem die veröffentlichten Assets angezeigt werden, einschließlich des Formulartitels. In diesem Beispiel wird die Vorlage **Wknd_Form** verwendet.
   ![Beim Klicken auf „Veröffentlichen“](/help/forms/assets/on-click-publish.png)

1. Klicken Sie erneut auf **Veröffentlichen**. Daraufhin wird ein Bestätigungs-Popup angezeigt, das angibt, dass Ihr Formular jetzt veröffentlicht wurde.
   ![Erfolgreiche Veröffentlichung](/help/forms/assets/publish-success.png)

1. Um den Veröffentlichungsstatus des Formulars zu überprüfen, klicken Sie erneut auf **Veröffentlichen**.
   ![Veröffentlichungsstatus](/help/forms/assets/publish-status.png)

1. Um **die Veröffentlichung eines Formulars aufzuheben**, öffnen Sie das Formular im Editor, klicken Sie auf das Menü mit den drei Punkten oben rechts und klicken Sie dann auf **Veröffentlichung aufheben**.
   ![Veröffentlichung aufheben](/help/forms/assets/unpublish--form.png)

## Aktivieren der Formularübermittlung in Edge Delivery durch Konfigurieren eines Referrer-Filters für AEM Publisher

Um die sichere Formularübermittlung zu gewährleisten, müssen Sie einen **Referrer-Filter** in AEM Publisher konfigurieren. Dieser Filter stellt sicher, dass nur autorisierte Anforderungen von Edge Delivery Schreibvorgänge (POST, PUT, DELETE, COPY, MOVE) ausführen können, sodass nicht autorisierte Änderungen verhindert werden. Im Folgenden werden die Schritte zum Konfigurieren eines Referrer-Filters für AEM Publisher beschrieben:

### Aktualisieren der URL der AEM-Instanz in Edge Delivery

Ändern Sie die `submitBaseUrl` in der Datei **constant.js** im Formularblock, um die URL der AEM-Instanz anzugeben:

**Für die Cloud-Einrichtung:**

```js
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';
```
**Für die lokale Entwicklung:**

```js
export const submitBaseUrl = 'http://localhost:4503';
```

### Ändern der CORS-Konfiguration

Passen Sie die **CORS-Einstellungen** so an, dass Anforderungen zur Formularübermittlung von Edge Delivery-Domains zugelassen werden. Weitere Informationen finden Sie im [CORS-Konfigurationshandbuch](https://experienceleague.adobe.com/de/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).

**CORS-Beispielkonfiguration:**

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Franklin Stage
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  

# Franklin Live
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```
Informationen zur lokalen Entwicklung finden Sie in der [Dokumentation](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter), um CORS über die **Host-URL Ihrer Entwicklungsbenutzeroberfläche** zu aktivieren.

### Konfigurieren des Referrer-Filters

Richten Sie den **Referrer-Filter** in AEM Cloud Service über Cloud Manager ein. [Erfahren Sie mehr](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) über das Konfigurieren des Referrer-Filters auf einer AEM Cloud Service-Instanz mithilfe von Cloud Manager.

**JSON-Konfiguration für den Referrer-Filter:**

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
    "https://.*\\.hlx\\.page:443",
    "https://.*\\.hlx\\.live:443"
  ],
  "filter.methods": [
    "POST",
    "PUT",
    "DELETE",
    "COPY",
    "MOVE"
  ],
  "exclude.agents.regexp": [
    ""
  ]
}
```

Diese Konfiguration gibt an, welche HTTP-Methoden gefiltert werden, welche Referrer zulässig sind und welche Benutzeragenten vom Filter ausgeschlossen werden. Durch die Implementierung dieser Konfigurationen werden **Formularübermittlungen über Edge Delivery** gesichert und auf autorisierte Quellen beschränkt.

### Zugreifen auf das veröffentlichte adaptive Formular

Auf Ihr adaptives Formular kann jetzt über **Edge Delivery** zugegriffen werden. Dabei wird das folgende URL-Format verwendet:

```
https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
```

Die URL von **Wknd-Form** lautet beispielsweise:

```
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form
```


## Siehe auch

{{universal-editor-see-also}}

