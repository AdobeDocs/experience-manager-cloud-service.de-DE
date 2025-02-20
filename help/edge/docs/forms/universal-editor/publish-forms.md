---
title: Veröffentlichen Sie AEM Forms für Edge Delivery Services.
description: Veröffentlichen Sie Ihre Edge Delivery Services-Formulare schnell und nahtlos.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: ba42a99e6138616ab6a7564c4bf58400844bdcc4
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---

# Veröffentlichen des adaptiven Formulars in Edge Delivery Services

Wenn Ihr Formular fertig gestellt und einsatzbereit ist, können Sie es veröffentlichen, um es Ihren Kunden zur Datenerfassung und -übermittlung zugänglich zu machen. Durch die Veröffentlichung wird sichergestellt, dass das Formular in Edge Delivery verfügbar ist, sodass Benutzende nahtlos damit interagieren können. Auf diese Weise können Kunden das Formular in Echtzeit ausfüllen und senden, was eine effiziente Datenerfassung und eine optimierte Verarbeitung gewährleistet.

## Voraussetzungen

* Ein Formular, das mit der Vorlage **Edge Delivery Services (EDS) erstellt**. [Weitere Informationen](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) zum Erstellen eines EDS-basierten Formulars.

## Formular veröffentlichen

Sie können jedes **EDS-basierte adaptive Formular** in Edge Delivery veröffentlichen, indem Sie die folgenden Schritte ausführen:

<!--1. Select the **Adaptive Form** that you want to publish and click the **Edit** ![edit icon](/help/forms/assets/edit.svg) icon.
   ![Select EDS-Based Form](/help/forms/assets/select-eds-based-form.png)-->

1. Öffnen Sie Ihr adaptives Formular im Editor und klicken Sie auf das Symbol **Veröffentlichen** in der oberen Leiste.
   ![Klicken Sie auf Veröffentlichen](/help/forms/assets/publish-icon-eds-form.png)

1. Wenn Sie auf **Veröffentlichen** klicken, wird ein Bildschirm oder Popup angezeigt, in dem die veröffentlichten Assets angezeigt werden, einschließlich des Formulartitels. In diesem Beispiel wird die Vorlage **WKND_**) verwendet.
   ![Klicken Sie auf Veröffentlichen](/help/forms/assets/on-click-publish.png)

1. Klicken Sie **erneut auf**Veröffentlichen“. Daraufhin wird ein Bestätigungs-Popup angezeigt, das angibt, dass Ihr Formular jetzt veröffentlicht ist.
   ![Erfolg der Veröffentlichung](/help/forms/assets/publish-success.png)

1. Um den Veröffentlichungsstatus des Formulars zu überprüfen, klicken Sie erneut **Veröffentlichen**.
   ![Veröffentlichungsstatus](/help/forms/assets/publish-status.png)

1. Um **Veröffentlichung** Formulars aufzuheben, öffnen Sie das Formular im Editor, klicken Sie auf das Dreipunkt-Menü in der oberen rechten Ecke und klicken Sie auf **Veröffentlichung aufheben**.
   ![Veröffentlichung aufheben](/help/forms/assets/unpublish--form.png)

## Aktivieren der Formularübermittlung in Edge Delivery durch Konfigurieren eines Referrer-Filters für AEM Publisher

Um die sichere Übermittlung von Formularen zu gewährleisten, müssen Sie einen **Referrer-Filter** im AEM Publisher konfigurieren. Dieser Filter stellt sicher, dass nur autorisierte Anfragen von Edge Delivery Schreibvorgänge ausführen können (POST, PUT, DELETE, COPY, MOVE), um nicht autorisierte Änderungen zu verhindern. Im Folgenden werden die Schritte zum Konfigurieren eines Referrer-Filters für AEM Publisher beschrieben:

### Aktualisieren der AEM-Instanz-URL in Edge Delivery

Ändern Sie die `submitBaseUrl` in der Datei **constant.js** im Formularblock, um die AEM-Instanz-URL anzugeben:

**Für die Cloud-Einrichtung:**

```js
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';
```
**Für die lokale Entwicklung:**

```js
export const submitBaseUrl = 'http://localhost:4503';
```

### Ändern der CORS-Konfiguration

Passen Sie die **CORS-Einstellungen** an, um Formularübermittlungsanfragen von Edge Delivery-Domains zuzulassen. Weitere Informationen finden Sie [CORS](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)Konfigurationshandbuch.

**CORS-Beispielkonfiguration:**

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Franklin Stage
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  

# Franklin Live
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```
Informationen zur lokalen Entwicklung finden Sie in der [Dokumentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter), um CORS über Ihre **Host-URL der Entwicklungs-Benutzeroberfläche)** aktivieren.

### Konfigurieren des Referrer-Filters

Richten Sie den **Referrer-Filter** in AEM Cloud Service über Cloud Manager ein. [Erfahren Sie mehr](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) über das Konfigurieren des Referrer-Filters auf einer AEM Cloud Service-Instanz mithilfe eines Cloud Managers.

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

Diese Konfiguration gibt an, welche HTTP-Methoden gefiltert werden, welche Referrer zulässig sind und welche Benutzeragenten vom Filter ausgeschlossen werden. Durch die Implementierung dieser Konfigurationen **Formularübermittlungen über Edge Delivery** gesichert und auf autorisierte Quellen beschränkt.

### Zugreifen auf das veröffentlichte adaptive Formular

Auf Ihr adaptives Formular kann jetzt über **Edge Delivery zugegriffen werden** wobei das folgende URL-Format verwendet wird:

```
https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
```

Beispielsweise lautet die URL für **Wknd-Form**:

```
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form
```


## Siehe auch

{{universal-editor-see-also}}

