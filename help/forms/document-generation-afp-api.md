---
title: Wie wird die AFP Output Sync API verwendet?
description: Erfahren Sie, wie Sie mit der AFP Output Sync API Ausgabedarstellungen abrufen und synchronisieren können.
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, User
exl-id: 5602fc63-ef74-44eb-b3be-61b8f8a2795a
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 14%

---

# Generieren von AFP-Output mithilfe des AEM Forms-API

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugegriffen werden kann. </span>

Advanced Function Presentation (AFP) ist ein leistungsstarkes Dokumentformat, das hauptsächlich für Druckzwecke entwickelt wurde.\
In diesem Handbuch werden alle erforderlichen Schritte und Konfigurationen zum Generieren der AFP-Ausgabe mithilfe von AEM Forms beschrieben.

<!--
## Prerequisites

To support AFP output generation, the following OSGi bundles must be present and in an **active** state:

* **AFP Core Bundle** – Available in the AFP repository
* **Forms Output Core** – Found in the Forms Output comments package
* **Bedrock Connector** – Provided by the Forms Output API
* **Cloud Ready Implementation** – Available through the Forms installer

>[!NOTE]
>
> * If any bundle is inactive, resolve dependency issues or reinstall manually.
> * To enable AFP generation, the `FT_FORMS-17887` toggle configurations must be set in AEM configuration manager.-->

## AFP-Generierungs-API

Generiert eine AFP-Datei (Advanced Function Presentation) mit einer XDP-Vorlage und Eingabedaten.

### Autorisierung

Sie können entweder **BasicAuth** (Admin-Anmeldeinformationen) für lokale Umgebungen oder **BearerAuth** Autorisierung für AEM Cloud-Instanzen verwenden.

### Anfrage

**Endpunkt:**
`POST http://<server>:<port>/adobe/forms/document/generate/afp`

### Kopfzeilen

| Schlüssel | Wert |
| --------------- | ------------------------------------------------------ |
| `Content-Type` | `application/pdf` |
| `Authorization` | `(Bearer Access token)` |

### Anfragetext

**Content-Type: multipart/form-data**

| Schlüssel | Typ | Erforderlich | Beschreibung |
| ---------- | ---- | -------- | ------------------------------------------------------------------------- |
| `template` | Datei/Text | Ja | XDP-Datei, die als Vorlage für die AFP-Generierung verwendet wird (z. B. `demo.xdp`) |
| `data` | Datei/Text | Nein | Datendatei (XML oder JSON), die mit der Vorlage zusammengeführt werden soll (z. B. `data.xml`) |
| `options` | Text | Nein | JSON-String mit Optionen zur Steuerung der AFP-Ausgabe (z. B. Auflösung, Gebietsschema) |

**Beispiel `options` JSON (Textfeld):**

```json
{
  "pdfVersion": "1.7",
  "resolution": 300,
  "locale": "en-US",
  "embedFonts": true,
  "contentRoot": "/usr/tmp"
}
```

### Antworten

| Code | Beschreibung |
| ----- | ------------------------------------------------------------------------- |
| `200` | Vorgang erfolgreich. Gibt den AFP-Dokumentstrom zurück. |
| `400` | Fehlerhafte Anfrage. Die Anfrage-Payload ist fehlerhaft oder es fehlen erforderliche Felder. |
| `500` | Interner Server-Fehler. Versuchen Sie es später erneut. |

### cURL-Befehl

```
curl --location 'http://<server>:<port>/adobe/forms/document/generate/afp' \
--header 'Authorization: Bearertoken <base64-encoded-credentials>' \
--form 'template=@"<path-to-template>.xdp"' \
--form 'data=@"<path-to-data-file>.xml"' \
--form 'options=<JSON-options-string>'
```

### Testen der API

Sie können die .yaml-Datei herunterladen und in Postman hochladen, um die Funktionalität der APIs zu überprüfen.

![AFP Postman Bild](/help/forms/assets/afp-postman.png)

Sie können die Antwort speichern und die gespeicherte Datei im AFP-Reader öffnen, um sie anzuzeigen.

![PDF Reader](/help/forms/assets/afp-pdf.png)
