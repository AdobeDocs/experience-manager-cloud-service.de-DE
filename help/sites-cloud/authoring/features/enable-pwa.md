---
title: Aktivieren der progressiven Web-App-Funktionen
description: AEM Sites ermöglicht es dem Autor von Inhalten, progressive Web-App-Funktionen über eine einfache Konfiguration zu aktivieren, anstatt zu kodieren.
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 54c4755207d84f6f11effea72e94e20027446ba9
workflow-type: tm+mt
source-wordcount: '2046'
ht-degree: 1%

---


# Aktivieren der progressiven Web-App-Funktionen {#enabling-pwa}

Durch eine einfache Konfiguration kann ein Inhaltsautor jetzt progressive Funktionen für Web-Apps (PWA) für in AEM Sites erstellte Erlebnisse aktivieren.

>[!CAUTION]
>
>Dies ist eine erweiterte Funktion, die Folgendes erfordert:
>
>* Kenntnisse der PWA
>* Kenntnis der Site- und Inhaltsstruktur
>* Erläuterungen zu Cachestrategien
>* Unterstützung durch Ihr Entwicklungsteam

>
>
Bevor Sie diese Funktion verwenden, sollten Sie dies mit Ihrem Entwicklungsteam besprechen, um die beste Möglichkeit zu finden, sie für Ihr Projekt zu nutzen.

>[!NOTE]
>
>Die in diesem Dokument beschriebenen Funktionen sollen mit der AEM Version [März 2021 als Cloud Service verfügbar gemacht werden.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)

## Einführung {#introduction}

[Progressive Web-Apps (PWA) ](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) ermöglichen ansprechende App-ähnliche Erlebnisse für AEM Sites, indem sie es ermöglichen, lokal auf dem Benutzercomputer gespeichert und offline verfügbar zu sein. Ein Benutzer kann eine Site unterwegs durchsuchen, selbst wenn er eine Internetverbindung verliert. PWA ermöglichen nahtlose Erlebnisse, selbst wenn das Netzwerk verloren geht oder instabil ist.

Anstatt eine erneute Kodierung der Site erforderlich zu machen, kann ein Inhaltsersteller die Eigenschaften der PWA als zusätzliche Registerkarte in den [Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md) einer Site konfigurieren.

* Beim Speichern oder Veröffentlichen wird mit dieser Konfiguration ein Ereignis-Handler Trigger, der die [Manifestdateien](https://developer.mozilla.org/en-US/docs/Web/Manifest) und [Dienstarbeiter](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) ausschreibt, die PWA-Funktionen auf der Site aktivieren.
* Sling-Zuordnungen werden ebenfalls beibehalten, um sicherzustellen, dass der Dienst vom Stamm der Anwendung aus bereitgestellt wird, um das Kopieren von Inhalten zu aktivieren, wodurch Offline-Funktionen in der App ermöglicht werden.

Mit PWA verfügt der Benutzer über eine lokale Kopie der Site, wodurch ein App-ähnliches Erlebnis auch ohne Internetverbindung entsteht.

>[!NOTE]
>
>Progressive Web-Apps sind eine sich entwickelnde Technologie und Unterstützung für die Installation lokaler Apps und andere Funktionen [hängen davon ab, welchen Browser Sie verwenden.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)

## Voraussetzungen {#prerequisites}

Um PWA-Funktionen für Ihre Site verwenden zu können, müssen Sie zwei Voraussetzungen für die Umgebung Ihres Projekts erfüllen:

1. [Verwenden Sie Core ](#adjust-components) Components, um diese Funktion zu nutzen
1. [Passen Sie die ](#adjust-dispatcher) Dispatcher-Regeln an, um die erforderlichen Dateien bereitzustellen.

Dies sind technische Schritte, die der Autor mit dem Entwicklungsteam koordinieren muss. Diese Schritte sind nur einmal pro Site erforderlich.

### Verwenden Sie die Kernkomponenten {#adjust-components}

Hauptkomponenten ab Version 2.15.0 unterstützen die PWA-Funktionen von AEM Sites vollständig. Da AEMaaCS immer die neueste Version der Hauptkomponenten enthält, können Sie die PWA-Funktionen sofort nutzen. Ihr AEMaaCS-Projekt erfüllt diese Anforderung automatisch.

>[!NOTE]
>
>Es wird nicht empfohlen, die PWA-Funktionen für benutzerdefinierte Komponenten oder Komponenten zu verwenden, die nicht [vom Erzkomponenten erweitert sind.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=de)
<!--
Your components need to include the [manifest files](https://developer.mozilla.org/en-US/docs/Web/Manifest) and [service worker,](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) which supports the PWA features.

 To do this, the developer will need to add the following link to the `customheaderlibs.html` file of your page component.

```xml
<link rel="manifest" href="/content/<projectName>/manifest.webmanifest" crossorigin="use-credentials"/>
```

The developer will also need to add the following link to the `customfooterlibs.html` file of your page component.

```xml
<script>
        // Check that service workers are supported
        if ('serviceWorker' in navigator) {
            // Use the window load event to make sure the page load performs well
            window.addEventListener('load', () => {
                let serviceWorker = '/<projectName>sw.js';
                navigator.serviceWorker.register(serviceWorker);
            });
        }
</script>
```
-->

### Anpassen des Dispatchers {#adjust-dispatcher}

Die PWA-Funktion generiert und verwendet `/content/<sitename>/manifest.webmanifest`-Dateien. Standardmäßig legt [der Dispatcher](/help/implementing/dispatcher/overview.md) diese Dateien nicht offen. Um diese Dateien bereitzustellen, muss der Entwickler die folgende Konfiguration zum Site-Projekt hinzufügen.

```text
File location: [project directory]/dispatcher/src/conf.dispatcher.d/filters/filters.any >

# Allow webmanifest files
/0102 { /type "allow" /extension "webmanifest" /path "/content/*/manifest" }
```

Je nach Projekt sollten Sie verschiedene Arten von Erweiterungen in die Umformulierungsregeln einbeziehen. Die Erweiterung `webmanifest` kann nützlich sein, wenn Sie eine Regel zum Ausblenden und Weiterleiten von Anforderungen an `/content/<projectName>` in die Umschreibungsbedingungen einführen.

```text
RewriteCond %{REQUEST_URI} (.html|.jpe?g|.png|.svg|.webmanifest)$
```

## Aktivieren von PWA für Ihre Site {#enabling-pwa-for-your-site}

Wenn [die Voraussetzungen](#prerequisites) erfüllt sind, ist es für einen Inhaltsersteller sehr einfach, PWA-Funktionen für eine Site zu aktivieren. Im Folgenden finden Sie eine Grundübersicht, wie dies zu bewerkstelligen ist. Die einzelnen Optionen sind im Abschnitt [Detaillierte Optionen aufgeführt.](#detailed-options)

1. Melden Sie sich bei AEM an.
1. Tippen oder klicken Sie im Hauptmenü auf **Navigation** -> **Sites**.
1. Wählen Sie Ihr Siteprojekt aus und tippen Sie auf oder klicken Sie auf [**Eigenschaften**](/help/sites-cloud/authoring/fundamentals/page-properties.md) oder verwenden Sie den Hotkey `p`.
1. Wählen Sie die Registerkarte **Progressive Web App** und konfigurieren Sie die entsprechenden Eigenschaften. Sie möchten mindestens Folgendes:
   1. Wählen Sie die Option **PWA aktivieren**.
   1. Definieren Sie die **Startup-URL**.

      ![PWA aktivieren](../assets/pwa-enable.png)

   1. Laden Sie ein PNG-Symbol im Format 512 x 512 in den DAM hoch und verweisen Sie darauf als Symbol für die App.

      ![Symbol PWA definieren](../assets/pwa-icon.png)

   1. Konfigurieren Sie die Pfade, die der Dienst offline verwenden soll. Typische Pfade sind:
      * `/content/<sitename>`
      * `/content/experiencefragements/<sitename>`
      * `/content/dam/<sitename>`
      * Beliebige Schriftartverweise von Drittanbietern
      * `/etc/clientlibs/<sitename>`

      ![Definieren von PWA-Offline-Pfaden](../assets/pwa-offline.png)


1. Tippen oder klicken Sie auf **Speichern und schließen**.

Ihre Site ist jetzt konfiguriert und Sie können sie als lokale App installieren.[](#using-pwa-enabled-site)

## Verwenden Ihrer PWA-aktivierten Site {#using-pwa-enabled-site}

Nachdem Sie [Ihre Site so konfiguriert haben, dass sie PWA unterstützt, können Sie sie nun selbst erleben.](#enabling-pwa-for-your-site)

1. Rufen Sie die Site in einem [unterstützten Browser auf.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)
1. In der Adressleiste des Browsers wird ein neues Symbol angezeigt, das darauf hinweist, dass die Site als lokale App installiert werden kann.
   * Je nach Browser kann das Symbol variieren, und der Browser zeigt ggf. auch eine Benachrichtigung an (z. B. ein Banner oder ein Dialogfeld), die darauf hinweist, dass eine Installation als lokale App möglich ist.
1. Installieren Sie das Programm.
1. Die App wird auf dem Startbildschirm Ihres Geräts installiert.
1. Öffnen Sie die App, navigieren Sie ein wenig und sehen Sie, dass die Seiten offline verfügbar sind.

## Detaillierte Optionen {#detailed-options}

Im folgenden Abschnitt finden Sie weitere Details zu den Optionen, die verfügbar sind, wenn [Sie Ihre Site für PWA konfigurieren.](#enabling-pwa-for-your-site)

### Konfigurieren des installierbaren Erlebnisses {#configure-installable-experience}

Mit diesen Einstellungen kann sich Ihre Site wie eine native App verhalten, da sie auf dem Startbildschirm des Besuchers installiert und offline verfügbar ist.

* **PWA**  aktivieren - Dies ist der Hauptschalter, um die PWA für die Site zu aktivieren.
* **Startup-URL** : Dies ist die  [bevorzugte Beginn-](https://developer.mozilla.org/en-US/docs/Web/Manifest/start_url) URL, die die App öffnet, wenn der Benutzer die lokal installierte App lädt.
   * Dies kann ein beliebiger Pfad in Ihrer Inhaltsstruktur sein.
   * Dies muss nicht der Stamm sein und ist oft eine spezielle Begrüßungsseite für die App.
   * Wenn diese URL relativ ist, wird die Manifest-URL als Basis-URL verwendet, um sie zu beheben.
   * Wenn das Feld leer gelassen wird, verwendet das Feature die Adresse der Webseite, von der aus die Web-App installiert wurde.
   * Es wird empfohlen, einen Wert festzulegen.
* **Anzeigemodus** : Eine App mit aktiviertem PWA ist weiterhin eine AEM, die über einen Browser bereitgestellt wird. [Diese ](https://developer.mozilla.org/en-US/docs/Web/Manifest/display) Anzeigeoptionen definieren, wie der Browser auf dem lokalen Gerät ausgeblendet oder dem Benutzer auf andere Weise angezeigt werden soll.
   * **Eigenständig** : Der Browser ist dem Benutzer vollständig ausgeblendet und erscheint wie eine native App. Dies ist der Standardwert.
      * Mit dieser Option muss die App-Navigation vollständig über Ihre Inhalte mithilfe von Links und Komponenten auf den Seiten der Site möglich sein, ohne die Navigationssteuerelemente des Browsers zu verwenden.
   * **Browser**  - Der Browser wird wie gewohnt beim Besuch der Site angezeigt.
   * **Minimale Benutzeroberfläche** : Der Browser ist wie eine native App meistens ausgeblendet, es werden jedoch grundlegende Navigationssteuerelemente angezeigt.
   * **Vollbild** : Der Browser ist wie eine native App vollständig ausgeblendet, wird aber im Vollbildmodus gerendert.
      * Mit dieser Option muss die App-Navigation vollständig über Ihre Inhalte mithilfe von Links und Komponenten auf den Seiten der Site möglich sein, ohne die Navigationssteuerelemente des Browsers zu verwenden.
* **Bildschirmausrichtung**  - Als lokale App muss die PWA wissen, wie  [Geräteausrichtungen zu handhaben sind.](https://developer.mozilla.org/en-US/docs/Web/Manifest/orientation)
   * **Beliebig** : Die App passt sich der Ausrichtung des Geräts des Benutzers an. Dies ist der Standardwert.
   * **Hochformat** : Dies zwingt die App, unabhängig von der Ausrichtung des Geräts im Hochformat-Layout zu öffnen.
   * **Querformat** : Hiermit wird die App unabhängig von der Ausrichtung des Geräts im Querformat-Layout geöffnet.
* **Designfarbe** : Hiermit wird die  [Farbe der ](https://developer.mozilla.org/en-US/docs/Web/Manifest/theme_color) Anwendung definiert, die sich darauf auswirkt, wie das Betriebssystem des lokalen Benutzers die native Symbolleiste der Benutzeroberfläche und Navigationssteuerelemente anzeigt. Abhängig vom Browser kann sich dies auf andere Elemente der App-Präsentation auswirken.
   * Verwenden Sie das Popup &quot;Farbraum&quot;, um eine Farbe auszuwählen.
   * Die Farbe kann auch durch den Hexadezimalwert oder den RGB-Wert definiert werden.
* **Hintergrundfarbe** : Hiermit wird die  [Hintergrundfarbe der App definiert, ](https://developer.mozilla.org/en-US/docs/Web/Manifest/background_color) die beim Laden der App angezeigt wird.
   * Verwenden Sie das Popup &quot;Farbraum&quot;, um eine Farbe auszuwählen.
   * Die Farbe kann auch durch den Hexadezimalwert oder den RGB-Wert definiert werden.
   * Bestimmte Browser [erstellen automatisch einen Begrüßungsbildschirm](https://developer.mozilla.org/en-US/docs/Web/Manifest#Splash_screens) aus dem App-Namen, der Hintergrundfarbe und dem Symbol.
* **Symbol** : Hiermit wird  [das ](https://developer.mozilla.org/en-US/docs/Web/Manifest/icons) Symbol definiert, das die App auf dem Gerät des Benutzers darstellt.
   * Das Symbol muss eine PNG-Datei im Format 512 x 512 Pixel sein.
   * Das Symbol muss [in DAM gespeichert sein.](/help/assets/overview.md)

### Cache-Verwaltung (erweitert) {#offline-configuration}

Diese Einstellungen machen Teile dieser Site offline verfügbar und lokal auf dem Gerät des Besuchers verfügbar. Dadurch kann der Cache der Web-App gesteuert werden, um Netzwerkanforderungen zu optimieren und Offline-Erlebnisse zu unterstützen.

* **Cachestrategie und Häufigkeit der Inhaltsaktualisierung**  - Diese Einstellung definiert das Cachemodell für Ihre PWA.
   * **Moderat**  -  [Diese ](https://web.dev/stale-while-revalidate/) Einstellung ist für die meisten Sites der Fall und ist der Standardwert.
      * Mit dieser Einstellung werden die Inhalte, die der Benutzer zuerst anzeigte, aus dem Cache geladen. Während der Benutzer diesen Inhalt verwendet, wird der Rest des Inhalts im Cache erneut überprüft.
   * **Häufig**  - Dies ist der Fall für Seiten, die Updates benötigen, um sehr schnell zu sein, wie Auktionshäuser.
      * Bei dieser Einstellung sucht die App zuerst nach dem neuesten Inhalt über das Netzwerk, und wenn dieser nicht verfügbar ist, wird der lokale Cache erneut geöffnet.
   * **Selten**  - Dies gilt für nahezu statische Websites wie z. B. Referenzseiten.
      * Bei dieser Einstellung sucht die App zuerst nach dem Inhalt im Cache, und wenn nicht verfügbar, kehrt sie zum Abrufen zurück.
* **Datei vor dem Zwischenspeichern** : Diese auf AEM gehosteten Dateien werden im lokalen Browser-Cache gespeichert, wenn der Service-Mitarbeiter installiert und bevor sie verwendet wird. Dadurch wird sichergestellt, dass die Web-App im Offlinemodus voll funktionsfähig ist.
* **Pfadeinschlüsse** : Netzwerkanforderungen für die definierten Pfade werden abgefangen und zwischengespeicherte Inhalte werden gemäß der konfigurierten  **Cachestrategie und der Häufigkeit der Inhaltsaktualisierung** zurückgegeben.
* **Cache-Ausschlüsse** : Diese Dateien werden unabhängig von den Einstellungen unter &quot; **Datei vor** Zwischenspeicherung&quot;und &quot; **Pfad&quot;nie zwischengespeichert**.

>[!TIP]
>
>Ihr Entwicklerteam verfügt vermutlich über wertvolle Informationen zur Einrichtung Ihrer Offlinekonfiguration.

## Einschränkungen und Recommendations {#limitations-recommendations}

Nicht alle PWA-Funktionen sind für AEM Sites verfügbar. Dies sind einige bemerkenswerte Einschränkungen.

* Ein Benutzer muss die Seite mindestens einmal durchsuchen, bevor sie offline zwischengespeichert wird.
* Seiten werden nicht automatisch synchronisiert oder aktualisiert, wenn der Benutzer die App nicht verwendet.

Bei der Implementierung von PWA gibt Adobe außerdem die folgenden Empfehlungen ab.

### Minimieren Sie die Anzahl der Ressourcen, die vor dem Zwischenspeichern bereitgestellt werden sollen. {#minimize-precache}

Adobe empfiehlt Ihnen, die Anzahl der Seiten auf den Pre-Cache zu begrenzen.

* Betten Sie Bibliotheken ein, um die Anzahl der Einträge zu reduzieren, die bei der Vorzwischenspeicherung verwaltet werden sollen.
* Schränken Sie die Anzahl der Bildvarianten auf den Pre-Cache ein.

### Aktivieren Sie PWA, nachdem die Projektskripte und Stylesheets stabilisiert wurden. {#pwa-stabilized}

Client-Bibliotheken werden mit dem Zusatz eines Cache-Selektors bereitgestellt, der das folgende Muster `lc-<checksumHash>-lc` berücksichtigt. Jedes Mal, wenn eine der Dateien (und Abhängigkeiten), aus denen eine Bibliothek besteht, geändert wird, ändert sich dieser Selektor. Wenn Sie eine Client-Bibliothek aufgelistet haben, die vom Service-Worker vorab zwischengespeichert werden soll, und auf eine neue Version verweisen möchten, rufen Sie den Eintrag manuell ab und aktualisieren Sie ihn. Daher empfehlen wir Ihnen, Ihre Site nach der Stabilisierung der Projektskripte und Stylesheets als PWA zu konfigurieren.

### Minimieren Sie die Anzahl der Bildvarianten. {#minimize-variations}

Die Image-Komponente der AEM Core-Komponenten bestimmt eine der Frontend-Darstellungen, die Sie am besten abrufen können. Dieser Mechanismus enthält auch einen Zeitstempel, der der letzten geänderten Zeit dieser Ressource entspricht. Dieser Mechanismus kompliziert die Konfiguration des PWA-Pre-Cache.

Beim Konfigurieren des Pre-Cache muss der Benutzer alle Pfadvarianten, die abgerufen werden können, Liste haben. Diese Varianten bestehen aus Parametern wie Qualität und Breite. Es wird dringend empfohlen, die Anzahl dieser Varianten auf maximal drei zu reduzieren - klein, mittel, groß. Dies können Sie über das Dialogfeld für die Inhaltsrichtlinie der [Bildkomponente.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=de)

Wenn der Speicher- und Netzwerkverbrauch nicht sorgfältig konfiguriert wird, kann dies die Leistung Ihres PWA erheblich beeinträchtigen. Wenn Sie z. B. 50 Bilder bearbeiten möchten und 3 Breiten pro Bild haben möchten, muss der Benutzer, der die Site pflegt, eine Liste von bis zu 150 Einträgen im Bereich &quot;PWA vor Cache&quot;der Seiteneigenschaften verwalten.

Adobe empfiehlt Ihnen auch, Ihre Site so zu konfigurieren, dass sie eine PWA ist, nachdem sich die Verwendung der Bilder im Projekt stabilisiert hat.
