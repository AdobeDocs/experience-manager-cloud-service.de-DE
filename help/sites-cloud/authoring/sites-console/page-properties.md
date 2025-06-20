---
title: Seiteneigenschaften
description: Erfahren Sie mehr über die verschiedenen Eigenschaften einer Seite und darüber, wie sie das Verhalten der Seite steuern und wie sie verwaltet wird.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
solution: Experience Manager Sites
feature: Authoring
role: User
mini-toc-levels: 2
source-git-commit: b9328a22ff544f2c663868d33d7b06e02819f1d7
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 37%

---


# Seiteneigenschaften {#page-properties}

Erfahren Sie mehr über die verschiedenen Eigenschaften einer Seite und darüber, wie sie das Verhalten der Seite steuern und wie sie verwaltet wird.

>[!TIP]
>
>Weitere Informationen zum Bearbeiten und Ändern der Eigenschaften einer Seite finden Sie im Dokument [Bearbeiten der Seiteneigenschaften.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md)

## Übersicht und Verfügbarkeit von Eigenschaften {#overview}

Seiteneigenschaften können viele Aspekte einer Seite steuern, vom Titel und Branding der Seite bis zu ihren Berechtigungen. Die Eigenschaften sind auf mehrere Registerkarten verteilt, von denen einige je nach Seitentyp ausgeblendet sein können. Wie die meisten Eigenschaften in AEM [ Seiteneigenschaften vererbt werden.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md#inheritance)

>[!NOTE]
>
>In diesem Dokument werden alle möglichen Seiteneigenschaften beschrieben. Je nach Seitentyp sind nicht alle Eigenschaften verfügbar.

## Registerkarte „Allgemein“ {#basic}

### Titel und Tags {#title-tags}

* **Titel** - Definiert den Meta-Titel der Seite für SEO-Zwecke sowie den im Seiteninhalt angezeigten Titel (sofern nicht überschrieben)
   * Der Seitentitel wird an verschiedenen Stellen in der Benutzeroberfläche von AEM angezeigt, einschließlich der Karten **/** in der [Sites-Konsole.](/help/sites-cloud/authoring/sites-console/introduction.md)
   * Dies ist ein Pflichtfeld.
* **Tags** - Definiert die Seiten-Meta-Tags für SEO-Zwecke
   * Sie können der Seite Tags hinzufügen oder Tags aus der Seite entfernen, indem Sie die Liste im Auswahlfeld aktualisieren.
   * Verwenden Sie die Dropdown-Liste, um aus vorhandenen Tags auszuwählen.
   * Nachdem Sie ein Tag ausgewählt haben, wird es unterhalb des Auswahlfelds aufgelistet. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
   * Sie können ein völlig neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.
      * Der neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
      * Das neue Tag wird dann mit einem kleinen Stern auf der rechten Seite angezeigt, der es als neues Tag kennzeichnet.
   * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein „x“ angezeigt, mit dem Sie das Tag löschen können.
   * Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags.](/help/sites-cloud/authoring/sites-console/tags.md)
* **In der Navigation ausblenden** - Gibt an, ob die Seite in der Seitennavigation der resultierenden Site ein- oder ausgeblendet werden soll

### Branding {#branding}

Wenden Sie eine konsistente Markenidentität auf allen Seiten an, indem Sie einen Marken-Slug an jeden Seitentitel anhängen. Diese Funktion erfordert die Verwendung der Seitenkomponente ab Version 2.14.0 der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)

* **Marken-Slug**
   * **Überschreiben**: Aktivieren Sie diese Option, um den Marken-Slug auf dieser Seite zu definieren.
      * Der Wert wird von allen untergeordneten Seiten geerbt, es sei denn, deren Werte zum **Überschreiben** sind ebenfalls festgelegt.
   * **Überschreibungswert** – Der Text des Marken-Slugs, der an den Seitentitel angehängt werden soll.
      * Der Wert wird nach einem Pipe-Zeichen wie `Cycling Tuscany | Always ready for the WKND` an den Seitentitel angehängt

### HTML-ID {#html-id}

* **ID** – HTML-ID, die auf die Komponente angewandt wird.

### Weitere Titel und Beschreibungen {#more-titles}

* **Seitentitel** - Ein Titel zur Verwendung auf der Seite
   * Dies wird normalerweise von Titelkomponenten verwendet.
   * Wenn dies leer gelassen wird, wird der **Titel** verwendet.
* **Navigationstitel** - Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie eine kürzere Alternative wählen möchten).
   * Wenn leer, wird **Seitentitel** verwendet.
* **Untertitel** - Ein Untertitel zur Verwendung auf der Seite
* **Beschreibung** - Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten

### Einschaltzeit/Ausschaltzeit {#on-off-time}

Die Ein-/Ausschaltzeit für eine Seite ist eine praktische Methode, um bereits veröffentlichte Inhalte vorübergehend auszublenden. Der Inhalt bleibt auf der Veröffentlichungsinstanz, wenn er deaktiviert ist. Durch Deaktivieren einer Seite wird die Veröffentlichung des Inhalts nicht rückgängig gemacht.

* **Einschaltzeit**: Zeitpunkt (Datum und Uhrzeit), zu dem die veröffentlichte Seite in der Publishing-Umgebung sichtbar (gerendert) wird. Die Seite muss entweder manuell oder durch vorkonfigurierte automatische Replikation veröffentlicht werden.

   * Wenn sie bereits [veröffentlicht](/help/sites-cloud/authoring/sites-console/publishing-pages.md) ist diese Seite in der Veröffentlichungsinstanz verfügbar, ruht jedoch (ausgeblendet), bis sie zum angegebenen Zeitpunkt gerendert wird.
   * Wenn die Seite nicht veröffentlicht und [für die automatische Replikation konfiguriert) ](/help/operations/replication.md#on-and-off-times-trigger-configuratio), wird sie automatisch veröffentlicht und zum angegebenen Zeitpunkt gerendert.
   * Wenn die Seite nicht veröffentlicht und nicht für die automatische Replikation konfiguriert ist, wird sie nicht automatisch veröffentlicht, sodass eine 404 angezeigt wird, wenn versucht wird, auf die Seite zuzugreifen.

* **Ausschaltzeit**: Ähnlich wie und häufig in Kombination mit der **Einschaltzeit** wird hier der Zeitpunkt festgelegt, zu dem die Publishing-Umgebung auf der Veröffentlichungsseite ausgeblendet wird.

Lassen Sie diese Felder (**Einschaltzeit** und **Ausschaltzeit**) für Seiten, die Sie veröffentlichen möchten, leer und stehen sofort zur Verfügung und stehen in der Veröffentlichungsumgebung zur Verfügung, bis sie deaktiviert werden (das normale Szenario).

>[!NOTE]
>Wenn entweder die **Einschaltzeit** oder die **Ausschaltzeit** in der Vergangenheit liegt und die automatische Replikation konfiguriert ist, wird die entsprechende Aktion sofort ausgelöst.

>[!TIP]
>
>Ein-/Ausschaltzeiten behandeln ausschließlich bereits veröffentlichte Inhalte (entweder manuell oder über automatische Replikation). Aus diesem Grund werden Veröffentlichungs-Workflows, wie die zur Genehmigung von Inhalten, nicht durch Ein-/Ausschaltzeiten ausgelöst, und Ein-/Ausschaltzeiten wirken sich nicht auf den Veröffentlichungsstatus der Seite aus. Aus diesem Grund sind Ein-/Ausschaltzeiten am besten geeignet, um vorübergehend Inhalte anzuzeigen/auszublenden, die bereits genehmigt und veröffentlicht sind.
>
>Wenn Sie neue Inhalte mit allen zugehörigen Workflows veröffentlichen oder Inhalte vollständig von Ihrer Site entfernen (Veröffentlichung aufheben) möchten, sollten Sie [Veröffentlichung verwalten“](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication)

### Vanity-URL {#vanity-url}

Mit dieser Eigenschaft können Sie eine Vanity-URL für diese Seite eingeben, sodass Sie eine kürzere und/oder ausdrucksstärkere URL verwenden können. Beispiel: Wenn die Vanity-URL `welcome` für die Seite mit dem Pfad `/v1.0/startpage` auf der Website `http://example.com` verwendet wird, wäre `http://example.com/welcome` die Vanity-URL von `http://example.com/content/v1.0/startpage`

>[!CAUTION]
>
>Vanity-URLs:
>
>* Muss eindeutig sein.
>* unterstützen keine Regex-Muster.
>* sollten nicht auf eine vorhandene Seite eingestellt sein.

* **Hinzufügen** – Wählen Sie dies aus, um ein Feld anzuzeigen, in dem eine Vanity-URL für die Seite definiert wird.
   * Wählen Sie es erneut aus, um mehrere hinzuzufügen.
   * Wählen Sie das Symbol **Entfernen** aus, um die Vanity-URL zu löschen.
* **Vanity-URL umleiten** - Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll oder ob eine Umleitung zur tatsächlichen URL der Seite erfolgen soll.

## Erweitert {#advanced}

### Einstellungen {#settings}

* **Sprache** – Die Seitensprache
* **Sprachstamm** – Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.
* **Umleiten** - Gibt die Seite an, zu der diese Seite automatisch mit einem HTML-`302 Found` umgeleitet werden soll
   * **Ständige Umleitung** – Wenn diese Option aktiviert ist, wird die Seite zum Zielpfad weitergeleitet, der zusammen mit dem HTML-Status `301 Moved Permanently` bereitgestellt wird.
* **Design**
* **Alias** – Gibt einen Alias an, der für diese Seite verwendet werden soll.
   * Beispiel: Wenn Sie einen Alias `private` für die Seite `/content/wknd/us/en/magazine/members-only` definieren, kann auf diese Seite über `/content/wknd/us/en/magazine/private` zugegriffen werden.
   * Durch die Erstellung eines Alias wird die Eigenschaft `sling:alias`, die sich nur auf die Ressource und nicht auf den Repository-Pfad auswirkt, auf dem Seitenknoten festgelegt.
   * Seiten, auf die im Editor über Aliasnamen zugegriffen wird, können nicht veröffentlicht werden. [Veröffentlichungsoptionen](/help/sites-cloud/authoring/sites-console/publishing-pages.md) im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.
   * Weitere [ finden Sie unter „Lokalisierte Seitennamen“ unter „Best Practices für SEO](/help/overview/seo-and-url-management.md#localized-page-names) und URL-Verwaltung“.

### Konfiguration {#configuration}

* **Von &lt;path> geerbt** - Aktivierung/Deaktivierung der Vererbung der **Cloud-Konfiguration** für die Seite
   * Schaltet die Verfügbarkeit der **Cloud-Konfiguration** zur Bearbeitung um

* **Cloud-Konfiguration** – Der Pfad zur gewählten Konfiguration

### Vorlageneinstellungen {#template-settings}

* **Erlaubte Vorlagen**: [Definiert die Liste der Vorlagen, die innerhalb dieses Unterzweigs verfügbar sind](/help/sites-cloud/authoring/page-editor/templates.md#enabling-and-allowing-a-template-template-author)
   * Jeder Wert muss ein absoluter Pfad zu einer Vorlage sein.
   * Verwenden Sie `/.*`, um alle Vorlagen unter diesem Pfad zuzulassen.
* **Seite als Vorlage verwenden**: [Erstellt eine neue Vorlage basierend auf der aktuellen Seite.](/help/sites-cloud/authoring/universal-editor/templates.md)
   * Gilt nur für Seiten, die für den universellen Editor unter Verwendung von Edge Delivery Services erstellt wurden.

### Authentifizierungspflicht {#authentication}

* **Aktivieren** - Aktiviert die Verwendung der Authentifizierung für den Zugriff auf die Seite

>[!NOTE]
>
>Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](#permissions)** definiert.

* **Anmeldeseite** - Die für die Anmeldung zu verwendende Seite

### Export {#export}

* **Exportkonfiguration** – Gibt eine Exportkonfiguration an

## SEO {#seo}

* **Kanonische URL** - Wird zum Überschreiben der kanonischen URL der Seite verwendet
   * Wenn Sie das Feld leer lassen, ist die URL der Seite ihre kanonische URL.

* **Robots-Tags** - Wählen Sie im Dropdown-Menü die Robots-Tags aus, um das Verhalten der Suchmaschinen-Crawler zu steuern
   * Einige Optionen stehen im Konflikt miteinander, wobei in diesem Fall die Option mit größerer Berechtigung Vorrang hat.

* **Sitemap generieren** - Wenn ausgewählt, wird ein `sitemap.xml` für diese Seite und ihre untergeordneten Elemente generiert.

## Bilder {#images}

### Vorgestelltes Bild {#featured-image}

In diesem Abschnitt wird das anzuzeigende Bild ausgewählt und konfiguriert. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

* **Bild** - Sie können **Asset** „Auswählen“ oder nach einer hochzuladenden Datei suchen und dann **Bearbeiten** oder **Löschen** das ausgewählte Bild auswählen.
* **Alternativtext** - Ein Text, der die Bedeutung und/oder Funktion des Bildes wiedergibt und häufig von Sprachausgaben verwendet wird
* **Vererben - Aus dem DAM-Asset stammender Wert** - Wenn diese Option aktiviert ist, wird der Alternativtext mit dem Wert der „Metadaten`dc:description` in DAM gefüllt.

### Miniaturansicht {#thumbnail}

In diesem Abschnitt können Sie die Miniaturansicht für die Seite auswählen und konfigurieren. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

* **Vorschau generieren** – Erstellen Sie eine Vorschau der Seite, die als Miniatur verwendet werden soll.
* **Bild hochladen** – Laden Sie ein Bild hoch, das als Miniatur verwendet werden soll.
* **Bild auswählen** - Wählen Sie ein vorhandenes Asset aus, das als Miniatur verwendet werden soll.
* **Wiederherstellen** – Diese Option wird verfügbar, nachdem Sie eine Änderung an der Miniatur vorgenommen haben. Wenn Sie Ihre Änderungen nicht behalten möchten, können Sie sie vor dem Speichern rückgängig machen.

## Cloud Services {#cloud-services}

* **Cloud Service-Konfigurationen** - Legt fest, welche Konfiguration für Cloud-Services für die Seite verwendet werden soll
* **Vererbt von** - Für Live Copies und Sprachkopien werden Cloud-Konfigurationen standardmäßig von der Blueprint vererbt.
   * Deaktivieren Sie diese Option, um die Vererbung zu überschreiben

## Personalisierung {#personalization}

### ContextHub-Konfigurationen {#contexthub-config}

* **ContextHub-Pfad** – Definieren der [ContextHub-Konfiguration](/help/sites-cloud/authoring/personalization/contexthub.md)
* **Segmentpfad** – Definieren des [Segmentpfads](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

### Konfiguration für Targeting {#targeting-config}

* **Marke** - Definiert eine [Marke, um einen Bereich für das Targeting anzugeben](/help/sites-cloud/authoring/personalization/targeted-content.md)
   * Für diese Option muss das Benutzerkonto der `Target Administrators` Gruppe angehören.

## Berechtigungen {#permissions}

Verwenden Sie die **Berechtigungen**, um festzulegen, welche Benutzenden, Gruppen oder [geschlossenen Benutzergruppen (CUGs)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html?lang=de) auf die Seite zugreifen und/oder sie ändern können.

* **Hinzufügen von Berechtigungen**
* **Geschlossene Benutzergruppe bearbeiten**
* **Effektive Berechtigungen** anzeigen 

## Blueprint {#blueprint}

Diese Registerkarte ist nur für Seiten sichtbar, die als Blueprints dienen. Blueprints dienen als Grundlage für Live Copys und sind Teil des [Multi-Site-Managements](/help/sites-cloud/administering/msm/overview.md).

* **Rollout** - Initiieren eines Rollouts von Blueprint-Inhalten an die Live Copies
* **Live Copy-Übersicht** - öffnet ein Fenster zum Durchsuchen der Live Copy-Seitenstruktur
* **Aktuelle Live Copies** - Eine Liste der Seiten, die auf der ausgewählten Blueprint-Seite basieren (also Live Copies davon sind)

## Live Copy {#live-copy}

Diese Registerkarte ist nur für Seiten sichtbar, die als Live Copys konfiguriert sind. Wie [ Blueprints sind ](#blueprint) Live Copies Teil von [Multi-Site-Management.](/help/sites-cloud/administering/msm/overview.md)

* **Synchronisieren** - Live Copy wird mit Blueprint synchronisiert; lokale Änderungen werden beibehalten.
* **Zurücksetzen** - Live Copy auf Status der Blueprint zurücksetzen; lokale Änderungen werden entfernt.
* **Aussetzen** – Live Copy von weiteren Änderungen beim Rollout aussetzen
* **Trennen** - Live Copy vom Blueprint trennen

### Quelle {#source}

* Zeigt den Pfad des Blueprints für diese Live Copy an

### Status {#status}

* Listet den aktuellen Live Copy-Status der Seite auf

### Konfiguration {#live-copy-config}

* **Live Copy-Vererbung** - Bei Auswahl dieser Option gilt die Live Copy-Konfiguration für alle untergeordneten Elemente.
* **Rollout-Konfigurationen von übergeordneter Seite übernehmen** - Wenn diese Option aktiviert ist, wird die Rollout-Konfiguration von der übergeordneten Seite übernommen.
* **Rollout-Konfiguration auswählen**: Legt fest, unter welchen Umständen Änderungen aus dem Blueprint übernommen werden, und ist nur verfügbar, wenn **Rollout-Konfigurationen von übergeordneter Seite erben** nicht aktiviert ist.
* **Liste der ausgeschlossenen Pfade**

## Vorschau {#preview}

Wenn [Vorschauumgebung](/help/sites-cloud/authoring/sites-console/previewing-content.md) aktiviert ist, sind die folgenden Details verfügbar:

* **Vorschau-URL** - Die URL, die für den Zugriff auf die Inhalte in der Vorschauumgebung verwendet wird

## Progressive Web App {#progressive-web-app}

Durch eine einfache Konfiguration kann ein Inhaltsautor Funktionen progressiver Web-Apps (PWA) für in AEM Sites erstellte Erlebnisse aktivieren. Ihre Site kann sich dann wie eine native App verhalten, indem sie auf dem Startbildschirm des Geräts der Besucher installiert und offline verfügbar wird.

{{pwa-deprecation}}

### Installierbares Erlebnis konfigurieren {#config-pwa}

* **PWA aktivieren** - Nach der Aktivierung können Besuchende der Seite die Site als PWA installieren.
* **Start-URL** - URL, die geladen werden soll, wenn der Benutzer die Web-Anwendung startet
   * Wenn die URL relativ ist, wird die Manifest-URL als Basis-URL zum Auflösen verwendet
   * Wenn leer, wird die URL der Seite verwendet, von der die App installiert wurde.
   * Es wird empfohlen, einen Wert festzulegen.
* **Anzeigemodus** - Legt fest, wie der Browser ausgeblendet oder den Benutzenden anderweitig auf dem lokalen Gerät präsentiert werden soll
* **Bildschirmausrichtung** - Wie die PWA Geräteausrichtungen handhabt
* **Themenfarbe** - Die Farbe der App, die sich darauf auswirkt, wie das Betriebssystem der lokalen Benutzenden die native Symbolleiste der Benutzeroberfläche und die Navigationssteuerelemente anzeigt
* **Hintergrundfarbe:** Hintergrundfarbe der App, die beim Laden der App angezeigt wird
* **Symbol** - Das Symbol, das die App auf dem Gerät der Benutzenden darstellt, wenn die PWA installiert ist

### Cache-Verwaltung (Erweitert) {#cache-management}

* **Caching-Strategie und Häufigkeit der Inhaltsaktualisierung** - Definiert das Caching-Modell für Ihre PWA.
* **Dateien zum Zwischenspeichern für die Offline-Nutzung**
   * **Vorab-Caching von Dateien (technische Vorschau)** - In AEM gehostete Dateien werden beim Installieren des Service-Sekundärs und vor dessen Verwendung im lokalen Browsercache gespeichert.
   * **Client-seitige Bibliotheken** - Client-seitige Bibliotheken zum Zwischenspeichern für Offline-Erlebnisse
   * **Pfadeinschlüsse** - Netzwerkanfragen für die definierten Pfade werden abgefangen, und zwischengespeicherte Inhalte werden entsprechend der konfigurierten Caching-Strategie und der Häufigkeit der Inhaltsaktualisierung zurückgegeben
   * **Pfadausschlüsse** - Diese Dateien werden unabhängig von den Einstellungen zum Vorab-Caching von Dateien und zu Pfadeinschlüssen niemals zwischengespeichert.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Aktivieren der Progressive Web App-Funktionen](/help/sites-cloud/authoring/sites-console/enable-pwa.md).

