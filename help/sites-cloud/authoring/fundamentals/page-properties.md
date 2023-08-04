---
title: Bearbeiten der Seiteneigenschaften
description: Erfahren Sie, wie Sie die Eigenschaften definieren, die für die Verwaltung einer Seite in AEM erforderlich sind.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
source-git-commit: 0183e14ad1653e98c06b19ea36c7e97dedccdb84
workflow-type: tm+mt
source-wordcount: '2281'
ht-degree: 80%

---

# Bearbeiten der Seiteneigenschaften {#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden, andere nicht und die Live Copy-Informationen sind entsprechend verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt.

### Allgemein {#basic}

* **Titel und Tags**

   * **Titel** - Der Titel der Seite wird an verschiedenen Stellen angezeigt. Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.
      * Dies ist ein Pflichtfeld.
   * **Tags** – Hier können Sie der Seite Tags hinzufügen oder Tags aus der Seite entfernen, indem Sie die Liste im Auswahlfeld aktualisieren.
      * Nachdem Sie ein Tag ausgewählt haben, wird es unter dem Auswahlfeld aufgeführt. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
      * Sie können ein völlig neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.
         * Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
         * Das neue Tag wird dann mit einem kleinen Stern auf der rechten Seite angezeigt, der es als neues Tag kennzeichnet.
      * In der Dropdown-Liste können Sie aus vorhandenen Tags auswählen.
      * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein „x“ angezeigt, mit dem Sie das Tag löschen können.
      * Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/features/tags.md).
   * **In der Navigation ausblenden** – Gibt an, ob die Seite in der Seitennavigation der resultierenden Site ein- oder ausgeblendet werden soll.

* **Branding**

  Wenden Sie eine konsistente Markenidentität auf allen Seiten an, indem Sie einen Marken-Slug an jeden Seitentitel anhängen. Diese Funktion erfordert die Verwendung der Seitenkomponente ab Version 2.14.0 der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)

   * **Marken-Slug**

      * **Überschreiben** – Aktivieren Sie diese Option, um den Marken-Slug auf dieser Seite zu definieren.
         * Der Wert wird von allen untergeordneten Seiten übernommen, es sei denn, sie verfügen auch über ihre **Überschreibung** festgelegten Werte.
      * **Überschreibungswert** – Der Text des Marken-Slugs, der an den Seitentitel angehängt werden soll.
         * Der Wert wird nach einem Pipe-Zeichen an den Seitentitel angehängt, z. B. „Cycling Tuscany | Always ready for the WKND“.

* **HTML-ID**

   * **ID** – HTML-ID, die auf die Komponente angewandt wird.

* **Weitere Titel und Beschreibungen**

   * **Seitentitel** – Ein Titel zur Verwendung auf der Seite. Wird normalerweise von Titelkomponenten verwendet. Wenn leer, wird die **Titel** verwendet.
   * **Navigationstitel** - Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie etwas präzisere angeben möchten). Wenn leer, wird die **Titel** verwendet.
   * **Untertitel** – Ein Untertitel zur Verwendung auf der Seite.
   * **Beschreibung** – Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit/Ausschaltzeit**

  >[!NOTE]
  >
  > Weitere Informationen zum Konfigurieren der zugehörigen automatischen Replikation finden Sie unter [Ein- und Ausschaltzeiten – Trigger-Konfiguration](/help/operations/replication.md#on-and-off-times-trigger-configuration).

  >[!NOTE]
  >Wenn entweder **Einschaltzeit** oder **Ausschaltzeit** in der Vergangenheit liegt und die automatische Replikation konfiguriert ist, wird die entsprechende Aktion sofort ausgelöst.

   * **Einschaltzeit** - Datum und Uhrzeit, zu der die veröffentlichte Seite in der Veröffentlichungsumgebung sichtbar (gerendert) wird. Die Seite muss entweder manuell oder durch vorkonfigurierte automatische Replikation veröffentlicht werden.

      * Wenn bereits [veröffentlicht (manuell)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) Diese Seite ruht (ausgeblendet) bis zum Rendern zum angegebenen Zeitpunkt.
      * Wenn die Seite nicht veröffentlicht und für die automatische Replikation konfiguriert ist, wird sie automatisch veröffentlicht und dann zum angegebenen Zeitpunkt gerendert.
      * Wenn die Seite nicht veröffentlicht und nicht für die automatische Replikation konfiguriert ist, wird sie nicht automatisch veröffentlicht. Daher wird ein 404-Fehler angezeigt, wenn versucht wird, auf die Seite zuzugreifen.

   * **Ausschaltzeit** - ähnlich wie und häufig in Kombination mit **Einschaltzeit** festgelegt ist, wird dadurch der Zeitpunkt definiert, zu dem die veröffentlichte Seite in der Veröffentlichungsumgebung ausgeblendet wird.

   * Lassen Sie diese Felder (**Einschaltzeit** und **Ausschaltzeit**) für Seiten, die Sie sofort veröffentlichen möchten und die in der Veröffentlichungsumgebung verfügbar sein sollen, leer, bis sie deaktiviert werden (der Normalfall).

* **Vanity-URL**

   * Ermöglicht die Eingabe einer Vanity-URL für diese Seite, was Ihnen ermöglicht, eine kürzere und/oder ausdrucksstärkere URL zu verwenden.
   * Beispiel: Wenn die Vanity-URL `welcome` für die Seite mit dem Pfad `/v1.0/startpage` auf der Website `http://example.com` verwendet wird, wäre `http://example.com/welcome` die Vanity-URL von `http://example.com/content/v1.0/startpage`

  >[!CAUTION]
  >
  >Vanity-URLs:
  >
  >* müssen eindeutig sein, Sie müssen also darauf achten, dass der Wert nicht bereits von einer anderen Seite verwendet wird.
  >* unterstützen keine Regex-Muster.
  >* sollten nicht auf eine vorhandene Seite eingestellt sein.

   * **Hinzufügen** - Tippen oder klicken Sie, um ein Feld anzuzeigen, in dem eine Vanity-URL für die Seite definiert wird.
      * Tippen oder klicken Sie erneut, um mehrere hinzuzufügen.
      * Tippen oder klicken Sie auf das Symbol **Entfernen**, um die Vanity-URL zu löschen.
   * **Vanity-URL umleiten** - Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll.

### Erweitert {#advanced}

* **Einstellungen**

   * **Sprache** – Die Seitensprache
   * **Sprachstamm** – Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.
   * **Umleiten** – Gibt die Seite an, zu der diese Seite automatisch umgeleitet werden soll. mit HTML-Status `302 Found`.
      * **Ständige Umleitung** – Wenn diese Option aktiviert ist, wird die Seite zum Zielpfad weitergeleitet, der zusammen mit dem HTML-Status `301 Moved Permanently` bereitgestellt wird.
   * **Design** – Gibt an, ob die Seite in der Seitennavigation der resultierenden Seite ein- oder ausgeblendet sein soll.
   * **Alias** – Gibt einen Alias an, der für diese Seite verwendet werden soll.
      * Beispiel: Wenn Sie einen Alias `private` für die Seite `/content/wknd/us/en/magazine/members-only` definieren, kann auf diese Seite über `/content/wknd/us/en/magazine/private` zugegriffen werden.
      * Durch die Erstellung eines Alias wird die Eigenschaft `sling:alias`, die sich nur auf die Ressource und nicht auf den Repository-Pfad auswirkt, auf dem Seitenknoten festgelegt.
      * Seiten, auf die im Editor über Aliasnamen zugegriffen wird, können nicht veröffentlicht werden. [Veröffentlichungsoptionen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.
      * Weitere Informationen finden Sie in [„Lokalisierte Seitennamen“ unter „Best Practices für SEO- und URL-Verwaltung“](/help/overview/seo-and-url-management.md#localized-page-names).

* **Konfiguration**

   * **Von &lt;path> geerbt** – Aktivierung/Deaktivierung der Vererbung; stellt die Verfügbarkeit der **Cloud-Konfiguration** zur Auswahl

   * **Cloud-Konfiguration** – Der Pfad zur gewählten Konfiguration

* **Vorlageneinstellungen**

   * **Zulässige Vorlagen** - [Definiert die Liste der verfügbaren Vorlagen](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) innerhalb dieser Unterverzweigung

* **Authentifizierungspflicht**

   * **Aktivieren** - Aktivieren Sie die Verwendung der Authentifizierung für den Zugriff auf die Seite.

     >[!NOTE]
     >
     >Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](#permissions)** definiert.

   * **Anmeldeseite** - Die für die Anmeldung zu verwendende Seite

* **Export**

   * **Exportkonfiguration** – Gibt eine Exportkonfiguration an

* **SEO**

   * **Kanonische URL** - kann verwendet werden, um die kanonische URL der Seite zu überschreiben. Wenn Sie das Feld leer lassen, ist die URL der Seite die kanonische URL

   * **Robots-Tags** – Wählen Sie die Robots-Tags aus, um das Verhalten der Suchmaschinen-Crawler zu steuern.

     >[!NOTE]
     >
     >Einige der Optionen stehen in Konflikt miteinander. Im Falle eines Konflikts hat die Option mit größerer Berechtigung Vorrang.

   * **Sitemap generieren** - Wenn ausgewählt, wird eine sitemap.xml für diese Seite und deren untergeordnete Elemente generiert.

### Bilder {#images}

* **Vorgestelltes Bild**

  Wählen Sie das anzuzeigende Bild aus und konfigurieren Sie es. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

   * **Bild**

     Sie können ein Asset **auswählen** oder nach einer hochzuladenden Datei suchen und diese dann **bearbeiten** oder **löschen**.

   * **Alternativtext** – Ein Text, der die Bedeutung und/oder Funktion des Bildes wiedergibt; z. B. für die Verwendung durch Bildschirmlesehilfen.

   * **Vererben – aus dem DAM-Asset stammender Wert** – Wenn diese Option aktiviert ist, wird der Alternativtext mit dem Wert der `dc:description`-Metadaten in DAM befüllt

* **Miniaturansicht**

  Konfigurieren der Miniatur der Seite

   * **Vorschau generieren** – Erstellen Sie eine Vorschau der Seite, die als Miniatur verwendet werden soll.
   * **Bild hochladen** – Laden Sie ein Bild hoch, das als Miniatur verwendet werden soll.
   * **Bild auswählen** – Wählen Sie ein vorhandenes Asset aus, das als Miniatur verwendet werden soll.
   * **Wiederherstellen** – Diese Option wird verfügbar, nachdem Sie eine Änderung an der Miniatur vorgenommen haben. Wenn Sie Ihre Änderungen nicht behalten möchten, können Sie sie vor dem Speichern rückgängig machen.

### Cloud Services {#cloud-services}

* **Cloud-Service-Konfigurationen** – Eigenschaften für Cloud-Services definieren

### Personalisierung {#personalization}

* **ContextHub-Konfigurationen**

   * **Von &lt;path> geerbt** – Aktivierung/Deaktivierung der Vererbung; schaltet die Verfügbarkeit des **ContextHub-Pfads** und **Segmentpfads** ein oder aus

   * **ContextHub-Pfad** – Definieren der [ContextHub-Konfiguration](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Segmentpfad** – Definieren des [Segmentpfads](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **Konfiguration für Targeting**

   * **Marke** – Legt eine [Marke fest, um einen Bereich für das Targeting anzugeben](/help/sites-cloud/authoring/personalization/targeted-content.md).

  >[!NOTE]
  >Für diese Option muss das Benutzerkonto der `Target Administrators`-Gruppe angehören.

### Berechtigungen {#permissions}

* **Berechtigungen**

   * **Hinzufügen von Berechtigungen**
   * **Geschlossene Benutzergruppe bearbeiten**
   * **Effektive Berechtigungen** anzeigen 

### Blueprint {#blueprint}

Diese Registerkarte ist nur für Seiten sichtbar, die als Blueprints dienen. Blueprints dienen als Grundlage für Live Copys und sind Teil des [Multi-Site-Managements](/help/sites-cloud/administering/msm/overview.md).

* **Aktuelle Live Copies** - Listet Seiten auf, die auf dieser Blueprint-Seite basieren (d. h. Live Copies von sind)

* **Rollout-Konfigurationen** - Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden

### Live Copy {#live-copy}

Diese Registerkarte ist nur für Seiten sichtbar, die als Live Copys konfiguriert sind. Wie bei Blueprints sind Live Copies Teil von [Multi-Site-Management](/help/sites-cloud/administering/msm/overview.md).

* **Synchronisieren** – Live Copy wird mit Blueprint synchronisiert; lokale Änderungen werden beibehalten.
* **Zurücksetzen** – Live Copy auf Status der Blueprint zurücksetzen; lokale Änderungen werden entfernt.
* **Aussetzen** – Live Copy von weiteren Änderungen beim Rollout aussetzen
* **Trennen** – Live Copy vom Blueprint trennen

* **Quelle**

   * Zeigt den Pfad des Blueprints für diese Live Copy an

* **Status**

   * Listet den aktuellen Live Copy-Status der Seite auf

* **Konfiguration**

   * **Live Copy-Vererbung** – Bei Auswahl dieser Option gilt die Live Copy-Konfiguration für alle untergeordneten Elemente.
   * **Rollout-Konfigurationen von übergeordneter Seite übernehmen** – Wenn diese Option aktiviert ist, wird die Rollout-Konfiguration von der übergeordneten Seite übernommen.
   * **Rollout-Konfiguration auswählen** - Definiert die Umstände, unter denen Änderungen von der Blueprint propagiert werden und nur verfügbar sind, wenn **Rollout-Konfigurationen von übergeordnetem Element übernehmen** ist nicht ausgewählt

### Vorschau {#preview}

Wenn eine Vorschau-Umgebung aktiviert ist, sehen Sie Folgendes:

* Vorschau-URL – die URL, die für den Zugriff auf die Inhalte in der Vorschau-Umgebung verwendet wird

### Progressive Web App {#progressive-web-app}

Durch eine einfache Konfiguration können Inhaltsautorinnen und -autoren jetzt PWA (Progressive Web App)-Funktionen für in AEM Sites erstellte Erlebnisse aktivieren.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Aktivieren der Funktionen progressiver Web-Apps](/help/sites-cloud/authoring/features/enable-pwa.md).

* **Konfigurieren eines installierbaren Erlebnisses**

   * **PWA aktivieren** – Aktivierung/Deaktivierung der Funktion; ermöglicht es Benutzenden, die Site als PWA zu installieren
   * **StartupURL** – die bevorzugte URL zum Start
   * **Anzeigemodus** – Legt fest, wie der Browser ausgeblendet oder den Benutzenden anderweitig auf dem lokalen Gerät präsentiert werden soll
   * **Bildschirmausrichtung** – Wie die PWA Geräteausrichtungen handhabt
   * **Themenfarbe** – Die Farbe der App, die sich darauf auswirkt, wie das Betriebssystem der lokalen Benutzenden die native Symbolleiste der Benutzeroberfläche und die Navigationssteuerelemente anzeigt
   * **Hintergrundfarbe** – Die Hintergrundfarbe der App, die beim Laden der App angezeigt wird
   * **Symbol** – Hiermit wird das Symbol definiert, das die App auf dem Gerät der Benutzenden repräsentiert

* **Cache-Verwaltung (erweitert)**

   * **Caching-Strategie und Häufigkeit der Inhaltsaktualisierung** – Definiert das Caching-Modell für Ihre PWA
   * **Dateien zum Zwischenspeichern für die Offline-Nutzung**
      * **Dateivorab-Zwischenspeicherung (technische Vorschau)** - Dateien, die auf AEM gehostet werden, werden im lokalen Browser-Cache gespeichert, wenn der Service Worker installiert und bevor er verwendet wird.
      * **Client-seitige Bibliotheken** – Client-seitige Bibliotheken zum Zwischenspeichern für Offline-Erlebnisse
      * **Pfadeinschlüsse** – Netzwerkanfragen für die definierten Pfade werden abgefangen, und zwischengespeicherte Inhalte werden entsprechend der konfigurierten Caching-Strategie und der Häufigkeit der Inhaltsaktualisierung zurückgegeben
      * **Pfadausschlüsse** – Diese Dateien werden unabhängig von den Einstellungen zum Vorab-Caching von Dateien und zu Pfadeinschlüssen niemals zwischengespeichert

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-1}

* In der Konsole **Sites**:
   * [beim Erstellen einer neuen Seite](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (ein Teil der Eigenschaften)
   * durch Klicken oder Tippen auf **Eigenschaften**
      * Für eine einzelne Seite
      * Für mehrere Seiten (nur eine Teilmenge der Eigenschaften steht zur Massenbearbeitung zur Verfügung)
* Im Seiteneditor:
   * mithilfe der Option **Seiteninformationen** (anschließend **Eigenschaften öffnen**)

### In der Sites-Konsole (einzelne Seite) {#from-the-sites-console-single-page}

durch Klicken oder Tippen auf **Eigenschaften**, um die Seiteneigenschaften festzulegen:

1. Navigieren Sie in der **Sites-Konsole** zu der Seite, für die Sie Eigenschaften anzeigen und bearbeiten möchten.
1. Wählen Sie die Option **Eigenschaften** für die gewünschte Seite aus, indem Sie wahlweise Folgendes verwenden:
   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * Die Seiteneigenschaften werden auf den entsprechenden Registerkarten angezeigt.
1. Sie können die Eigenschaften nach Bedarf anzeigen oder bearbeiten.
1. Speichern Sie dann Ihre Aktualisierungen mit **Speichern** und klicken Sie danach auf **Schließen**, um zur Konsole zurückzukehren.

### Beim Bearbeiten einer Seite {#when-editing-a-page}

Beim Bearbeiten einer Seite können Sie mithilfe von **Seiteninformationen** die Seiteneigenschaften definieren:

1. Öffnen Sie die Seite, für die Sie Eigenschaften bearbeiten möchten.
1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Auswahlmenü zu öffnen:
1. Wählen Sie **Eigenschaften öffnen** aus. Daraufhin wird ein Dialogfeld geöffnet, in dem Sie die Eigenschaften – geordnet nach der jeweiligen Registerkarte – bearbeiten können. Die folgenden Schaltflächen stehen rechts in der Symbolleiste zur Verfügung:
   * **Abbrechen**
   * **Speichern und schließen**
1. Mit der Schaltfläche **Speichern und schließen** können Sie Änderungen speichern.

### In der Sites-Konsole (mehrere Seiten) {#from-the-sites-console-multiple-pages}

In der **Sites** Console können Sie mehrere Seiten auswählen und dann die Seiteneigenschaften mithilfe der **Ansichtseigenschaften** anzeigen und/oder bearbeiten. Dies wird als Massenbearbeitung von Seiteneigenschaften bezeichnet.

Sie können mehrere Seiten für die Massenbearbeitung mit verschiedenen Methoden auswählen, darunter:

* Beim Durchsuchen der **Sites**-Konsole
* Nach Verwendung von **Suche**, um einen Seitensatz zu finden

Nach Auswahl der Seiten und anschließendes Klicken oder Tippen auf **Eigenschaften-Option**, werden die Masseneigenschaften angezeigt:

![Massenbearbeitung von Seiteneigenschaften](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

Sie können nur Massenbearbeitungen von Seiten durchführen, die:

* den gleichen Ressourcentyp haben
* nicht Teil einer Live Copy sind
   * Wenn sich eine der Seiten in einer Live Copy befindet, wird beim Öffnen der Eigenschaften eine Meldung angezeigt.

Nach dem Start der Massenbearbeitung können Sie folgende Aktionen ausführen:

* **Anzeigen**

   * Eine Liste der betroffenen Seiten
      * Bei Bedarf können Sie die Auswahl auswählen/deselektieren
      * Registerkarten
         * Wie beim Anzeigen von Eigenschaften für eine einzelne Seite werden die Eigenschaften unter Registerkarten angeordnet.
   * Eine Untergruppe von Eigenschaften
      * Eigenschaften, die auf allen ausgewählten Seiten verfügbar sind und explizit als für die Massenbearbeitung verfügbar definiert wurden, sind sichtbar.
      * Wenn Sie die Seitenauswahl auf eine Seite reduzieren, sind alle Eigenschaften sichtbar.
   * Gemeinsame Eigenschaften mit einem gemeinsamen Wert
      * Nur Eigenschaften mit einem gemeinsamen Wert werden im Ansichtsmodus angezeigt.
      * Wenn das Feld mehrwertig ist (z. B. Tags), werden nur Werte angezeigt, die *alle* gleich sind. Wenn nur einige gleich sind, werden diese nur bei der Bearbeitung angezeigt.
      * Wenn keine Eigenschaften mit einem gemeinsamen Wert vorhanden sind, wird eine Meldung angezeigt.

* **Bearbeiten**

   * Sie können die Werte in den verfügbaren Feldern aktualisieren.
      * Die neuen Werte werden bei Auswahl auf alle ausgewählten Seiten angewendet **Fertig**.
      * Wenn das Feld mehrwertig ist (z. B. Tags), können Sie entweder einen neuen Wert anhängen oder einen gemeinsamen Wert entfernen.
   * Gemeinsame Felder, die unterschiedliche Werte auf den verschiedenen Seiten aufweisen, werden durch einen speziellen Wert wie den Text gekennzeichnet `<Mixed Entries>`.
