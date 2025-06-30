---
title: Seiteneigenschaften
description: Erfahren Sie mehr über die verschiedenen Eigenschaften, die eine Seite haben kann, wie sie das Verhalten der Seite steuern und wie sie verwaltet wird.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
solution: Experience Manager Sites
feature: Authoring
role: User
mini-toc-levels: 2
source-git-commit: b9328a22ff544f2c663868d33d7b06e02819f1d7
workflow-type: ht
source-wordcount: '2138'
ht-degree: 100%

---


# Seiteneigenschaften {#page-properties}

Erfahren Sie mehr über die verschiedenen Eigenschaften, die eine Seite haben kann, wie sie das Verhalten der Seite steuern und wie sie verwaltet wird.

>[!TIP]
>
>Weitere Informationen zum Bearbeiten und Ändern der Eigenschaften einer Seite finden Sie im Dokument [Bearbeiten der Seiteneigenschaften.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md)

## Überblick und Verfügbarkeit von Eigenschaften {#overview}

Seiteneigenschaften können zahlreiche Aspekte einer Seite steuern, vom Titel und Branding der Seite bis zu ihren Berechtigungen. Die Eigenschaften sind auf mehrere Registerkarten verteilt, von denen einige je nach Seitentyp ausgeblendet sein können. Wie die meisten Eigenschaften in AEM [können Seiteneigenschaften vererbt werden.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md#inheritance)

>[!NOTE]
>
>In diesem Dokument werden alle möglichen Seiteneigenschaften beschrieben. Je nach Seitentyp sind nicht alle Eigenschaften verfügbar.

## Registerkarte „Allgemein“ {#basic}

### Titel und Tags {#title-tags}

* **Titel**: Definiert den Meta-Titel der Seite für SEO-Zwecke sowie den im Seiteninhalt angezeigten Titel (sofern nicht überschrieben)
   * Der Titel der Seite wird an verschiedenen Stellen in der Benutzeroberfläche von AEM angezeigt, zum Beispiel in den Karten-/Listenansichten **Sites** in der [Sites-Konsole](/help/sites-cloud/authoring/sites-console/introduction.md).
   * Dies ist ein Pflichtfeld.
* **Tags**: Definiert die Meta-Tags der Seite für SEO-Zwecke.
   * Sie können Tags zur Seite hinzufügen oder von ihr entfernen, indem Sie die Liste im Auswahlfeld aktualisieren.
   * Verwenden Sie die Dropdown-Funktion, um aus vorhandenen Tags auszuwählen.
   * Nachdem Sie ein Tag ausgewählt haben, wird es unterhalb des Auswahlfelds aufgelistet. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
   * Sie können ein völlig neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.
      * Der neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
      * Das neue Tag wird dann mit einem kleinen Stern auf der rechten Seite angezeigt, der es als neues Tag kennzeichnet.
   * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein „x“ angezeigt, mit dem Sie das Tag für diese Seite löschen können.
   * Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags.](/help/sites-cloud/authoring/sites-console/tags.md)
* **In der Navigation ausblenden**: Gibt an, ob die Seite in der Seitennavigation der resultierenden Site ein- oder ausgeblendet werden soll.

### Branding {#branding}

Wenden Sie eine konsistente Markenidentität auf allen Seiten an, indem Sie einen Marken-Slug an jeden Seitentitel anhängen. Diese Funktion erfordert die Verwendung der Seitenkomponente ab Version 2.14.0 der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)

* **Marken-Slug**
   * **Überschreiben**: Aktivieren Sie diese Option, um den Marken-Slug auf dieser Seite zu definieren.
      * Der Wert wird von allen untergeordneten Seiten geerbt, es sei denn, deren Werte zum **Überschreiben** sind ebenfalls festgelegt.
   * **Überschreibungswert** – Der Text des Marken-Slugs, der an den Seitentitel angehängt werden soll.
      * Der Wert wird nach einem Pipe-Zeichen an den Seitentitel angehängt, z. B. `Cycling Tuscany | Always ready for the WKND`.

### HTML-ID {#html-id}

* **ID** – HTML-ID, die auf die Komponente angewandt wird.

### Weitere Titel und Beschreibungen {#more-titles}

* **Seitentitel**: Ein Titel zur Verwendung auf der Seite. 
   * Dieser wird normalerweise von Titelkomponenten verwendet.
   * Wenn dies leer gelassen wird, wird der **Titel** verwendet.
* **Navigationstitel**: Sie können einen eigenen Titel für die Navigation angeben (z. B. wenn Sie einen kürzeren Titel wünschen). 
   * Wenn dies leer gelassen wird, wird der **Seitentitel** verwendet.
* **Untertitel**: Ein Untertitel zur Verwendung auf der Seite.
* **Beschreibung**: Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

### Ein-/Ausschaltzeit {#on-off-time}

Die Ein-/Ausschaltzeit für eine Seite ist eine praktische Möglichkeit zum vorübergehenden Ausblenden bereits veröffentlichter Inhalte. Der Inhalt bleibt auf der Veröffentlichungsinstanz, wenn er ausgeschaltet ist. Durch das Ausschalten einer Seite wird die Veröffentlichung des Inhalts nicht rückgängig gemacht.

* **Einschaltzeit**: Zeitpunkt (Datum und Uhrzeit), zu dem die veröffentlichte Seite in der Publishing-Umgebung sichtbar (gerendert) wird. Die Seite muss entweder manuell oder durch vorkonfigurierte automatische Replikation veröffentlicht werden.

   * Wenn diese Seite bereits [veröffentlicht wurde](/help/sites-cloud/authoring/sites-console/publishing-pages.md), ist sie auf der Veröffentlichungsinstanz verfügbar, wird aber bis zum Rendern am angegebenen Zeitpunkt ruhend (ausgeblendet) gehalten.
   * Wenn die Seite nicht veröffentlicht, aber [für die automatische Replikation](/help/operations/replication.md#on-and-off-times-trigger-configuratio) konfiguriert ist, wird sie automatisch veröffentlicht und dann zum festgelegten Zeitpunkt gerendert.
   * Wenn die Seite nicht veröffentlicht und nicht für die automatische Replikation konfiguriert ist, wird sie nicht automatisch veröffentlicht. Daher wird ein 404-Fehler angezeigt, wenn jemand versucht, auf die Seite zuzugreifen.

* **Ausschaltzeit**: Ähnlich wie die **Einschaltzeit** (und häufig in Kombination damit) wird hier der Zeitpunkt festgelegt, zu dem die Veröffentlichungsseite in der Veröffentlichungsumgebung ausgeblendet wird.

Lassen Sie diese Felder (**Einschaltzeit** und **Ausschaltzeit**) für Seiten, die Sie sofort veröffentlichen und verfügbar haben möchten und die in der Veröffentlichungsumgebung verfügbar sein sollen, solange leer, bis sie deaktiviert werden (der Normalfall).

>[!NOTE]
>Wenn entweder die **Einschaltzeit** oder die **Ausschaltzeit** in der Vergangenheit liegt und die automatische Replikation konfiguriert ist, wird die entsprechende Aktion sofort ausgelöst.

>[!TIP]
>
>Ein-/Ausschaltzeiten gelten ausschließlich für bereits veröffentlichte Inhalte (entweder manuell oder über die automatische Replikation). Aus diesem Grund werden Veröffentlichungs-Workflows, wie die zur Genehmigung von Inhalten, nicht durch Ein-/Ausschaltzeiten ausgelöst, und Ein-/Ausschaltzeiten wirken sich nicht auf den Veröffentlichungsstatus der Seite aus. Aus diesem Grund sind Ein-/Ausschaltzeiten am besten geeignet, um bereits genehmigte und veröffentlichte Inhalte vorübergehend anzuzeigen bzw. auszublenden.
>
>Wenn Sie neue Inhalte mit allen zugehörigen Workflows veröffentlichen oder Inhalte vollständig von Ihrer Site entfernen (d. h. die Veröffentlichung von Inhalten aufheben) möchten, sollten Sie [Ihre Veröffentlichung verwalten](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication).

### Vanity-URL {#vanity-url}

Mit dieser Eigenschaft können Sie eine Vanity-URL für diese Seite eingeben, was es Ihnen ermöglicht, eine kürzere und/oder aussagekräftigere URL zu verwenden. Beispiel: Wenn die Vanity-URL `welcome` für die Seite mit dem Pfad `/v1.0/startpage` auf der Website `http://example.com` verwendet wird, wäre `http://example.com/welcome` die Vanity-URL von `http://example.com/content/v1.0/startpage`

>[!CAUTION]
>
>Vanity-URLs:
>
>* Sie müssen eindeutig sein
>* unterstützen keine Regex-Muster.
>* sollten nicht auf eine vorhandene Seite eingestellt sein.

* **Hinzufügen** – Wählen Sie dies aus, um ein Feld anzuzeigen, in dem eine Vanity-URL für die Seite definiert wird.
   * Wählen Sie es erneut aus, um mehrere hinzuzufügen.
   * Wählen Sie das Symbol **Entfernen** aus, um die Vanity-URL zu löschen.
* **Vanity-URL umleiten**: Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll oder ob eine Umleitung auf die tatsächliche URL der Seite erfolgen soll.

## Erweitert {#advanced}

### Einstellungen {#settings}

* **Sprache** – Die Seitensprache
* **Sprachstamm** – Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.
* **Umleiten**: Gibt die Seite an, zu der diese Seite automatisch mit einem HTML `302 Found`-Status weitergeleitet werden soll.
   * **Dauerhafte Weiterleitung** – Wenn diese Option aktiviert ist, wird die Seite zum Zielpfad weitergeleitet, der zusammen mit dem HTML-Status `301 Moved Permanently` bereitgestellt wird.
* **Design**
* **Alias** – Gibt einen Alias an, der für diese Seite verwendet werden soll.
   * Beispiel: Wenn Sie einen Alias `private` für die Seite `/content/wknd/us/en/magazine/members-only` definieren, kann auf diese Seite über `/content/wknd/us/en/magazine/private` zugegriffen werden.
   * Durch die Erstellung eines Alias wird die Eigenschaft `sling:alias`, die sich nur auf die Ressource und nicht auf den Repository-Pfad auswirkt, auf dem Seitenknoten festgelegt.
   * Seiten, auf die im Editor über Aliasnamen zugegriffen wird, können nicht veröffentlicht werden. [Veröffentlichungsoptionen](/help/sites-cloud/authoring/sites-console/publishing-pages.md) im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.
   * Weitere Informationen finden Sie im Abschnitt [„Lokalisierte Seitennamen“ auf der Seite „Best Practices für SEO- und URL-Verwaltung“](/help/overview/seo-and-url-management.md#localized-page-names).

### Konfiguration {#configuration}

* **Von &lt;path> geerbt**: Aktivieren/Deaktivieren der Vererbung der **Cloud-Konfiguration** für die Seite
   * Aktiviert/deaktiviert die Verfügbarkeit der **Cloud-Konfiguration** für die Bearbeitung

* **Cloud-Konfiguration**: Der Pfad zur gewählten Konfiguration

### Vorlageneinstellungen {#template-settings}

* **Erlaubte Vorlagen**: [Definiert die Liste der Vorlagen, die innerhalb dieses Unterzweigs verfügbar sind](/help/sites-cloud/authoring/page-editor/templates.md#enabling-and-allowing-a-template-template-author)
   * Jeder Wert muss ein absoluter Pfad zu einer Vorlage sein.
   * Verwenden Sie `/.*`, um alle Vorlagen unter diesem Pfad zuzulassen.
* **Seite als Vorlage verwenden**: [Erstellt eine neue Vorlage basierend auf der aktuellen Seite.](/help/sites-cloud/authoring/universal-editor/templates.md)
   * Gilt nur für Seiten, die für den universellen Editor unter Verwendung von Edge Delivery Services erstellt wurden.

### Authentifizierungspflicht {#authentication}

* **Aktivieren**: Aktiviert die Verwendung der Authentifizierung für den Zugriff auf die Seite.

>[!NOTE]
>
>Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](#permissions)** definiert.

* **Anmeldeseite** - Die für die Anmeldung zu verwendende Seite

### Export {#export}

* **Exportkonfiguration**: Gibt eine Exportkonfiguration an

## SEO {#seo}

* **Kanonische URL**: Wird zum Überschreiben der kanonischen URL der Seite verwendet.
   * Wenn Sie dieses Feld leer lassen, dient die URL der Seite als ihre kanonische URL

* **Robots-Tags**: Verwenden Sie die Dropdown-Liste zum Auswählen der Robots-Tags, um das Verhalten der Suchmaschinen-Crawler zu steuern.
   * Einige Optionen stehen im Konflikt miteinander, wobei in einem solchen Fall die Option mit größerer Berechtigung Vorrang hat.

* **Sitemap generieren**: Wenn ausgewählt, wird eine `sitemap.xml` für diese Seite und ihre Unterseiten generiert.

## Bilder {#images}

### Vorgestelltes Bild {#featured-image}

In diesem Abschnitt wird das anzuzeigende Bild ausgewählt und konfiguriert. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

* **Bild**: Sie können ein Asset **auswählen** oder nach einer hochzuladenden Datei suchen und dann das ausgewählte Bild **bearbeiten** oder **löschen**.
* **Alternativtext**: Ein Text, der die Bedeutung und/oder Funktion des Bildes wiedergibt und häufig von Bildschirmlesehilfen verwendet wird.
* **Übernehmen – Wert aus dem DAM-Asset übernommen**: Wenn diese Option aktiviert ist, wird der Alternativtext mit dem Wert der `dc:description`-Metadaten in DAM befüllt.

### Miniaturansicht {#thumbnail}

In diesem Abschnitt wird die Miniaturansicht des Bilds für die Seite ausgewählt und konfiguriert. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

* **Vorschau generieren** – Erstellen Sie eine Vorschau der Seite, die als Miniatur verwendet werden soll.
* **Bild hochladen** – Laden Sie ein Bild hoch, das als Miniatur verwendet werden soll.
* **Bild auswählen**: Wählen Sie ein vorhandenes Asset aus, das als Miniaturansicht verwendet werden soll.
* **Wiederherstellen** – Diese Option wird verfügbar, nachdem Sie eine Änderung an der Miniatur vorgenommen haben. Wenn Sie Ihre Änderungen nicht behalten möchten, können Sie sie vor dem Speichern rückgängig machen.

## Cloud Services {#cloud-services}

* **Cloud-Service-Konfigurationen**: Definiert, welche Konfiguration für Cloud-Services für die Seite verwendet wird
* **Vererbt von**: Für Live Copies und Sprachkopien werden Cloud-Konfigurationen standardmäßig von der Blueprint vererbt.
   * Deaktivieren Sie dies zum Überschreiben der Vererbung

## Personalisierung {#personalization}

### ContextHub-Konfigurationen {#contexthub-config}

* **ContextHub-Pfad** – Definieren der [ContextHub-Konfiguration](/help/sites-cloud/authoring/personalization/contexthub.md)
* **Segmentpfad** – Definieren des [Segmentpfads](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

### Konfiguration für Targeting {#targeting-config}

* **Marke**: Legt eine [Marke fest, um einen Bereich für das Targeting anzugeben](/help/sites-cloud/authoring/personalization/targeted-content.md).
   * Für diese Option muss das Benutzerkonto der Gruppe `Target Administrators` angehören.

## Berechtigungen {#permissions}

Verwenden Sie die Registerkarte **Berechtigungen**, um festzulegen, welche Benutzenden, Gruppen oder [geschlossenen Benutzergruppen (Closed User Groups, CUGs)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html?lang=de) auf die Seite zugreifen und/oder sie ändern können.

* **Hinzufügen von Berechtigungen**
* **Geschlossene Benutzergruppe bearbeiten**
* **Effektive Berechtigungen** anzeigen 

## Blueprint {#blueprint}

Diese Registerkarte ist nur für Seiten sichtbar, die als Blueprints dienen. Blueprints dienen als Grundlage für Live Copys und sind Teil des [Multi-Site-Managements](/help/sites-cloud/administering/msm/overview.md).

* **Rollout**: Initiieren eines Rollouts von Blueprint-Inhalten an die Live Copies
* **Live Copy-Übersicht**: Öffnet ein Fenster zum Durchsuchen der Live Copy-Seitenstruktur
* **Aktuelle Live Copies**: Eine Liste von Seiten, die auf der ausgewählten Blueprint-Seite basieren (das heißt, Live Copies dieser Seite sind).

## Live Copy {#live-copy}

Diese Registerkarte ist nur für Seiten sichtbar, die als Live Copys konfiguriert sind. Wie [Blueprints](#blueprint) sind Live Copies Teil des [Multi-Site-Managements](/help/sites-cloud/administering/msm/overview.md).

* **Synchronisieren** – Live Copy wird mit Blueprint synchronisiert; lokale Änderungen werden beibehalten.
* **Zurücksetzen**: Die Live Copy wird auf den Status des Blueprints zurückgesetzt, wobei lokale Änderungen entfernt werden
* **Aussetzen** – Für die Live Copy werden weitere Änderungen beim Rollout ausgesetzt
* **Trennen**: Die Live Copy wird vom Blueprint getrennt

### Quelle {#source}

* Zeigt den Pfad des Blueprints für diese Live Copy an

### Status {#status}

* Listet den aktuellen Live Copy-Status der Seite auf

### Konfiguration {#live-copy-config}

* **Live Copy-Vererbung**: Bei Auswahl dieser Option gilt die Live Copy-Konfiguration für alle untergeordneten Elemente.
* **Rollout-Konfigurationen aus übergeordnetem Element übernehmen**: Wenn diese Option aktiviert ist, wird die Rollout-Konfiguration von der übergeordneten Seite übernommen.
* **Rollout-Konfiguration auswählen**: Legt fest, unter welchen Umständen Änderungen aus dem Blueprint übernommen werden, und ist nur verfügbar, wenn **Rollout-Konfigurationen aus übergeordnetem Element übernehmen** nicht aktiviert ist.
* **Liste der ausgeschlossenen Pfade**

## Vorschau {#preview}

Wenn eine [Vorschauumgebung](/help/sites-cloud/authoring/sites-console/previewing-content.md) aktiviert ist, sind die folgenden Details verfügbar:

* **Vorschau-URL**: Die URL, die für den Zugriff auf die Inhalte in der Vorschau-Umgebung verwendet wird

## Progressive Web App {#progressive-web-app}

Durch eine einfache Konfiguration können Inhaltsautorinnen und -autoren PWA-Funktionen (Progressive Web App) für in AEM Sites erstellte Erlebnisse aktivieren. Ihre Site kann sich dann wie eine native App verhalten, indem sie auf dem Startbildschirm des Geräts der Besucherinnen und Besucher installierbar und offline verfügbar gemacht wird.

{{pwa-deprecation}}

### Konfigurieren der Installierbarkeit {#config-pwa}

* **PWA aktivieren**: Wenn diese Option aktiviert ist, können Benutzende die Site als PWA installieren.
* **Startup-URL**: URL, die geladen werden sollte, wenn Benutzende die Web-Anwendung starten.
   * Wenn die URL relativ ist, wird die Manifest-URL als Basis-URL zum Auflösen verwendet.
   * Wenn das Feld leer ist, wird die URL der Seite verwendet, von der aus die App installiert wurde.
   * Es wird empfohlen, einen Wert festzulegen.
* **Anzeigemodus**: Legt fest, wie der Browser ausgeblendet oder den Benutzenden anderweitig auf dem lokalen Gerät präsentiert werden soll
* **Bildschirmausrichtung**: Wie die PWA die Geräteausrichtung handhabt
* **Themenfarbe**: Die Farbe der App, was sich darauf auswirkt, wie das Betriebssystem der lokalen Benutzenden die native Symbolleiste der Benutzeroberfläche und die Navigationssteuerelemente anzeigt
* **Hintergrundfarbe** : Die Hintergrundfarbe der App, die beim Laden der App angezeigt wird
* **Symbol**: Das Symbol, das die App auf dem Gerät der Benutzenden repräsentiert, wenn die PWA installiert ist

### Cache-Verwaltung (Erweitert) {#cache-management}

* **Caching-Strategie und Häufigkeit der Inhaltsaktualisierung**: Legt das Caching-Modell für Ihre PWA fest.
* **Dateien zum Zwischenspeichern für die Offline-Nutzung**
   * **Vorab-Caching von Dateien (technische Vorschau)**: In AEM gehostete Dateien werden beim Installieren des Service-Workers und vor dessen Verwendung im lokalen Browser-Cache gespeichert.
   * **Client-seitige Bibliotheken**: Client-seitige Bibliotheken zum Zwischenspeichern für die Offline-Nutzung
   * **Pfadeinschlüsse**: Netzwerkanfragen für die definierten Pfade werden abgefangen, und zwischengespeicherte Inhalte werden entsprechend der konfigurierten Caching-Strategie und der Häufigkeit der Inhaltsaktualisierung zurückgegeben
   * **Pfadausschlüsse**: Diese Dateien werden, unabhängig von den Einstellungen zum Vorab-Caching von Dateien und zu Pfadeinschlüssen, niemals zwischengespeichert.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Aktivieren der Progressive Web App-Funktionen](/help/sites-cloud/authoring/sites-console/enable-pwa.md).

