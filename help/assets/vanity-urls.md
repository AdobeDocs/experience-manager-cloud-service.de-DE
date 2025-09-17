---
title: Erstellen von Vanity-URLs mit Dynamic Media mit OpenAPI-Funktionen
description: Verwenden Sie die OpenAPI-Funktionen von Dynamic Media, um Ihre URLs für die lange Asset-Bereitstellung in kurze, markenspezifische Vanity-URLs umzuwandeln. Eine Vanity-URL ist eine kurze, saubere, leicht zu merkende und lesbare Version Ihrer komplexen Versand-URL. Sie können Ihren Markennamen, Produktnamen und relevante Keywords in die Vanity-URL aufnehmen, um die Sichtbarkeit Ihrer Marke und die Benutzerinteraktion zu verbessern
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 6c730591374b8ee4373a1a584f54386118e518da
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 0%

---


# Was sind Vanity-URLs?{#vanity-urls}

Verwenden Sie [!DNL Dynamic Media OpenAPI capabilities] , um Ihre URLs für die lange Asset-Bereitstellung in kurze, markenspezifische Vanity-URLs umzuwandeln. Standard-URLs für die Asset-Bereitstellung enthalten systemgenerierte Asset-UUIDs, die die Versand-URL komplex, schwer zu merken und freizugeben machen. Ersetzen Sie diese Asset-UUIDs durch einfache Kennungen (Vanity-IDs), um eine Vanity-URL zu generieren. Eine Vanity-URL ist eine kurze, saubere und lesbare Version Ihrer komplexen Versand-URL.

Siehe die folgenden URL-Formate, um die Unterschiede zu verstehen:
* [Standard-Versand-URL](#standard-urls)
* [Vanity-URLs](#vanity-url)

Standard-Versand-URLs verwenden `aaid` gefolgt von einer UUID, während Vanity-URLs `avid` gefolgt von einer benutzerdefinierten Kennung (Vanity-Kennung) verwenden.

Verwenden Sie kurze und einfache Vanity-IDs, um Ihre Versand-URL kurz, sauber, lesbar, leicht zu merken und freizugeben. Verwenden Sie Ihren Markennamen, Produktnamen und relevante Keywords als Vanity-IDs, um die Sichtbarkeit Ihrer Marke und die Benutzerinteraktion zu verbessern.

Wenn Ihr Benutzer auf Ihre Vanity-URL klickt, wird [!DNL Dynamic Media with OpenAPI] zur Aufnahmezeit automatisch dem ursprünglichen Asset-Speicherort zugeordnet und zum Zeitpunkt des Versands ordnungsgemäß aufgelöst, um dem Benutzer das Asset bereitzustellen.

Erfahren Sie, wie [Vanity-URLs erstellen](#create-vanity-urls).

## Standard-Versand-URLs{#standard-urls}

Die standardmäßige URL für die [!DNL Dynamic Media with OpenAPI]-Asset-Bereitstellung enthält eine eindeutige systemgenerierte Kennung und weist das folgende Format auf.

***format:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:aaid:aem:<asset-uuid>/as/<seoname>.<format>`

Die Standard-Versand-URL enthält `aaid` (*tatsächliche Asset-*) nach dem `urn:` und eine UUID zwischen `urn:aaid:aem:` und `/as/<seoname>.<format>`.

***Beispiel:*** `https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:43341ab1-4086-44d2-b7ce-ee546c35613b/as/check.jpeg`

Im obigen Beispiel ist `43341ab1-4086-44d2-b7ce-ee546c35613b` die UUID.

## Vanity-URLs{#vanity-url}

Die Vanity-URLs enthalten eine Vanity-Kennung anstelle der Asset-UUID und haben das folgende Format.

***format:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/<seoname>.<format>`

Die Vanity-URL enthält `avid` (*tatsächliche Vanity-Kennung*) nach dem `urn:` und Ihre Vanity-ID zwischen `urn:avid:aem:` und `/<seoname>.<format>`.

***Beispiel:*** `https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:avid:aem:VanityCheck/as/check.jpeg`

Im obigen Beispiel ist `VanityCheck` die Vanity-ID, die die UUID ersetzt hat.

## Wichtige Funktionen und Vorteile{#capabilities-and-benefits-of-vanity-urls}

Die Verwendung aussagekräftiger Vanity-IDs zur Anpassung der Standard-URLs für die Asset-Bereitstellung bietet mehrere Vorteile und messbare Auswirkungen. Zu den wichtigsten Funktionen und Vorteilen von Vanity-URLs gehören die folgenden.

### Schlüsselfunktionen{#key-capabilities}

* **URL-Anpassung** Ersetzen Sie lange Kennungen (Asset-UUIDs) in der Versand-URL durch kürzere, markenorientierte Alternativen, um eine sauberere Versand-URL zu generieren.
* **Echtzeit-Umleitung:** Vanity-URLs werden zur Laufzeit zu ursprünglichen Asset-UUIDs umgeleitet, ohne dass die Workflows unterbrochen werden. Benutzer sehen saubere URLs in der Adressleiste, während das System das technische Routing übernimmt.
* **Einfaches Link-Management:** Sie Ihre Vanity-URLs jederzeit anpassen, ohne die Leistung der Asset-Bereitstellung zu beeinträchtigen.

### Die wichtigsten Vorteile{#key-benefits}

* **Verbessert das Benutzererlebnis:** Saubere und kürzere Vanity-URLs sind lesbar, benutzerfreundlich, einfach zu merken und freizugeben.

* **Verbessert die Benutzerinteraktion:** URLs mit Markenbezeichnungen schaffen Vertrauen und Zuversicht bei den Benutzern. Benutzer klicken mit höherer Wahrscheinlichkeit auf professionelle, markenspezifische Links, was zu höheren Clickthrough-Raten führt.

* **SEO-Optimierung:** URLs, die relevante Keywords enthalten, verbessern das Suchmaschinen-Ranking und die Auffindbarkeit.

* **Verbesserte Markensichtbarkeit:** Markenspezifische URLs stärken die Markenpräsenz auf allen Marketing-Kanälen, einschließlich E-Mail, Social Media und Werbekampagnen.
Darüber hinaus wird die Markenidentität und -erkennung durch die konsistente Verwendung von Marken-URLs in allen Kommunikationen gestärkt.

* **Tracking und Analyse von Kampagnen:** Verwenden Sie eindeutige Vanity-URLs für verschiedene Kampagnen und Kanäle, um detaillierte Einblicke in Traffic-Quellen und die Konversionsleistung zu erhalten.

## Voraussetzungen{#prerequisites-for-creating-vanity-id}

Um die Vanity-URL zu erstellen, stellen Sie sicher, dass Sie bereits [die Assets für die öffentliche Bereitstellung genehmigt haben](/help/assets/manage-organize-assets-view.md#manage-asset-status).

## Erstellen von Vanity-URLs{#create-vanity-urls}

Führen Sie die folgenden Schritte aus, um Vanity-URLs zu erstellen:
1. [Einrichten von Asset-Metadaten](#set-up-asset-metadata)
1. [Erstellen und Zuordnen einer Cloud Manager-Umgebungsvariablen](#map-cloud-manager-environment-variable)
1. [Validieren der Assets, für die eine Vanity-URL für die Bereitstellung erforderlich ist](/help/assets/manage-organize-assets-view.md#manage-asset-status)
1. [Vanity-URLs generieren](#generate-vanity-urls)

### Einrichten von Asset-Metadaten{#set-up-asset-metadata}

Führen Sie die folgenden Schritte aus, um die Vanity-ID im Metadatenformular Ihres Assets einzurichten:
1. Navigieren Sie zur Detailseite des Ordners, in dem sich die Assets für [!DNL Dynamic Media with OpenAPI] Versand befinden.
1. [Bearbeiten Sie dieses Metadatenformular](/help/assets/metadata-assets-view.md#edit-metadata-forms) indem Sie einen der folgenden Schritte ausführen:
   * Fügen Sie ein neues Metadatenfeld hinzu und geben Sie die erforderliche Vanity-ID als Wert dieses Felds an.
   * Aktualisieren Sie das vorhandene Feld, indem Sie den Wert einer vorhandenen Metadateneigenschaft durch die erforderliche Vanity-ID ersetzen. Lernen Sie die [Best Practices](#best-practices) zum Erstellen der Vanity-ID kennen.
     ![Vanity-ID](/help/assets/assets/vanity-id-metadata.png)
Weitere Informationen zu [Metadatenschemata](/help/assets/metadata-schemas.md).

     >[!NOTE]
     >
     > Ein einzelnes Asset kann über mehrere Vanity-IDs verfügen. [Kontaktieren Sie den Adobe](https://helpx.adobe.com/de/contact.html)Support und stellen Sie eine Anfrage zum Generieren der erforderlichen Vanity-IDs.

Nachdem Sie Ihre Vanity-ID im Asset-Metadatenformular eingerichtet haben[ (ordnen Sie dieses Metadatenfeld dem Bereitstellungsmechanismus des Systems zu](#map-cloud-manager-environment-variable).

### Erstellen und Zuordnen einer Cloud Manager-Umgebungsvariablen{#map-cloud-manager-environment-variable}

Führen Sie die folgenden Schritte aus, um eine Umgebungsvariable zu erstellen und sie dem Metadatenfeld zuzuordnen, das die Vanity-ID enthält:

1. [Navigieren Sie zur Seite „Konfigurationen“ Ihrer Cloud Manager](/help/implementing/cloud-manager/environment-variables.md)Umgebung und gehen Sie folgendermaßen vor:
   1. `ASSET_DELIVERY_VANITY_ID` Variable hinzufügen. Das ist der Schlüssel.
   1. Ordnen Sie im Wertfeld die Metadateneigenschaft zu, die die Vanity-ID enthält. Die Zuordnung folgt `dc:<your-metadata-property>` Format, wobei das Präfix der Metadatenzuordnung (z. B. *dc:*) je nach Metadatenkonfigurationseigenschaft variiert.
      ![ASSET_DELIVERY_VANITY_ID-Variable](/help/assets/assets/environment-config.png)
1. Speichern Sie Ihre Änderungen, um die Pods in Ihrer Umgebung neu zu starten.

### Validieren der Assets für die Bereitstellung{#approve-assets-for-delivery}

Nachdem Sie die `ASSET_DELIVERY_VANITY_ID` Variable in Ihrer Cloud Manager-Umgebung der Asset-Metadateneigenschaft zugeordnet haben, die die Vanity-ID enthält, [ Sie Ihre Assets, für die eine Vanity-URL für die Bereitstellung erforderlich ist](/help/assets/manage-organize-assets-view.md#manage-asset-status).

### Vanity-URLs generieren{#generate-vanity-urls}

Nehmen Sie die folgenden Ersetzungen in Ihrer Standard-Versand-URL vor, um sie in eine Vanity-URL umzuwandeln:

* Ersetzen **UUID** durch Ihre **Vanity ID**.
* `aaid` durch `avid` ersetzen.

Siehe die [URL-Umwandlung von Standard- in Vanity-URL](#standard-urls) oben.
Erfahren Sie, wie [ Dynamic Media mit OpenAPI-Bereitstellungs](/help/assets/approve-assets.md#copy-delivery-url-for-approved-assets)URLs für Ihre Assets kopieren.

Wenn Ihr Benutzer auf die Vanity-URL klickt, ordnet [!DNL Dynamic Media with OpenAPI] die Vanity-ID zur Aufnahmezeit automatisch der ursprünglichen Asset-UUID zu und löst sie zur Bereitstellungszeit ordnungsgemäß auf, um das Asset ohne Verzögerung an den Benutzer bereitzustellen. Sie können die Vanity-URL in Echtzeit anpassen, ohne die Leistung der Asset-Bereitstellung zu beeinträchtigen.

[Verbessern Sie die Wirkung Ihrer Vanity-URLs mithilfe der erweiterten Anpassungsfunktionen von AEM Cloud Service.](#scale-using-vanity-url)

## Skalieren mithilfe von Vanity-URLs{#scale-using-vanity-url}

Mit AEM as a Cloud Service können Sie [ DNS- und CDN-Namen ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/introduction) Ihren Webadressen anpassen. Verwenden Sie diese AEMCS-Funktionen mit Ihren Vanity-URLs, um sie in eindeutige Web-Adressen umzuwandeln, die sauber, beschreibend, mit Marken versehen und intuitiv sind und die [oben genannten Vorteile](#key-benefits) bieten.

Siehe die folgende Vanity-URL und ihre anpassbaren Komponenten:

**Vanity-URL-Format:**

`https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/<seoname>.<format>`

<table style="border-collapse:collapse; table-layout:auto; width:auto;">
  <tr valign="top">
    <td style="padding:0 4px; white-space:nowrap;">
      <div align="left"><code>https://delivery&#8209;&lt;tenant&gt;.adobeaemcloud.com</code></div>
      <div align="center">↓</div>
      <div align="center"><a href="#customize-dns">Dieses DNS anpassen</a></div>
    </td>
    <td style="padding:0 6px; white-space:nowrap;">/</td>
    <td style="padding:0 4px; white-space:nowrap;">
      <div align="left"><code>adobe/assets/urn:avid:aem:</code></div>
      <div align="center">↓</div>
      <div align="center"><a href="#rewrite-cdn-rules">URL mit Neuschreibungsregeln anpassen</a></div>
    </td>
    <td style="padding:0 4px; white-space:nowrap;">
      <div align="left"><code>&lt;vanity-id&gt;</code></div>
      <div align="center">↓</div>
      <div align="center"><a href="#create-vanity-urls">Vanity-ID erstellen</a></div>
    </td>
    <td style="padding:0 4px; white-space:nowrap; width:1%;">
      <div align="left"><code>/&lt;seoname&gt;.&lt;format&gt;</code></div>
    </td>
  </tr>
</table>

**Vanity-URL-Format mit benutzerdefinierten DNS- und CDN-Namen:**

`https://<custom-dns>` `/` `dam/assets/` `<vanity-id>` `/<seoname>.<format>`

**Anpassbare URL-Komponenten**

* ***[DNS-Name (Hostname):](#customize-DNS)*** `https://delivery-<tenant>.adobeaemcloud.com` ist die Server-Domain, die Ihre Assets hostet. [DNS anpassen, um den Host-Namen zu ändern](#customize-DNS).
* ***[CDN-Neuschreibungsregeln:](#rewrite-cdn-rules)*** `adobe/assets/urn:avid:aem:` ist die Pfadstruktur, die Asset-Typen und Bereitstellungsmethoden identifiziert. [CDN-Regeln neu schreiben](#rewrite-cdn-rules) um den Domain-Pfad zu ändern.

### DNS anpassen{#customize-dns}

[Ersuchen Sie den Adobe-Support](https://helpx.adobe.com/de/contact.html) um das erforderliche benutzerdefinierte DNS für Ihre Bereitstellungsebene zu generieren. Befolgen Sie die [Best Practices](#best-practices) zum Erstellen benutzerdefinierter DNS-Namen.

### CDN-Regeln neu schreiben{#rewrite-cdn-rules}

Führen Sie die folgenden Schritte aus, um die CDN-Regeln für den Versand neu zu schreiben:

1. Navigieren Sie zu Ihrem AEM-Repository, um eine YAML-Konfigurationsdatei zu erstellen.
2. Führen Sie die Schritte im Abschnitt [Setup](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-error-pages#setup) aus, um CDN-Regeln zu konfigurieren und die Konfiguration über Ihre Cloud Manager-Konfigurations-Pipeline bereitzustellen.
Befolgen Sie die [Best Practices](#best-practices) zum Erstellen Ihres Domain-Pfads.
   [Erfahren Sie mehr über CDN-Neuschreibungsregeln](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#request-transformations).

Im Folgenden finden Sie Beispiele für Neuschreibungsregeln für das Anhängen von Dateinamen mit Erweiterungen in Vanity-URLs. Passen Sie diese Neuschreibungsregeln entsprechend Ihren spezifischen Anforderungen an. [Wenden Sie sich an den Adobe](https://helpx.adobe.com/de/contact.html)Support, um weitere Hilfe zu erhalten:

```- name: cdn-rewrite-rule
  when:
    allOf:
      - reqProperty: tier
        equals: delivery
```

#### Für SVG, GIF und PDF {#svg-gif-pdf}

```
    type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:svg|gif|pdf|docx|xlsx))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/original/as/\1\2
```

#### Für Videos{#video}

Für Videos einschließlich MP4, MOV, AVI und MKV

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:mp4|mov|avi|mkv))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/play\2
```

#### Für Bild{#image}

Für alle Bildtypen außer SVG.

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.[^/]+)(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/as/\1\2
```

## Befolgen Sie die Best Practices zum Erstellen sauberer Vanity-URLs{#best-practices}

Befolgen Sie die folgenden Best Practices für die Erstellung von Vanity-IDs, benutzerdefinierten DNS- und Domain-Namen:

1. Verwenden Sie keine Sonderzeichen in Vanity-IDs wie Leerzeichen, Schrägstrichen, Bindestrichen und mehr. Das System ersetzt Sonderzeichen in Vanity-IDs durch eine vordefinierte Zuordnung.
1. Verwenden Sie Ihren Markennamen, Produktnamen und relevante Keywords in Ihren Vanity-IDs, benutzerdefinierten DNS- und Domain-Namen, um die Sichtbarkeit Ihrer Marke und die Benutzerinteraktion zu verbessern.
1. Verwenden Sie kurze, beschreibende Wörter oder Zeichenfolgen, die Bedeutung vermitteln.
1. Verwenden Sie Texte, die Benutzer zu Klicks einladen.
