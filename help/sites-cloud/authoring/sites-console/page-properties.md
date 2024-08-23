---
title: Bearbeiten der Seiteneigenschaften
description: Erfahren Sie, wie Sie die Eigenschaften definieren, die für die Verwaltung einer Seite in AEM erforderlich sind.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 7adfe0ca7fbab1f8a5bd488e524a48be62584966
workflow-type: tm+mt
source-wordcount: '2268'
ht-degree: 100%

---

# Bearbeiten der Seiteneigenschaften {#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. So können beispielsweise einige Seiten mit einer Live Copy verbunden sein, andere nicht, und die Informationen der Live Copy sind je nach Bedarf verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt.

### Allgemein {#basic}

* **Titel und Tags**

   * **Titel** – Der Titel der Seite wird an verschiedenen Stellen angezeigt. Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.
      * Dies ist ein Pflichtfeld.
   * **Tags** – Hier können Sie der Seite Tags hinzufügen oder Tags aus der Seite entfernen, indem Sie die Liste im Auswahlfeld aktualisieren.
      * Nachdem Sie ein Tag ausgewählt haben, wird es unter dem Auswahlfeld aufgeführt. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
      * Sie können ein völlig neues Tag eingeben, indem Sie den Namen in ein leeres Auswahlfeld eingeben.
         * Der neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
         * Das neue Tag wird dann mit einem kleinen Stern auf der rechten Seite angezeigt, der es als neues Tag kennzeichnet.
      * In der Dropdown-Liste können Sie aus vorhandenen Tags auswählen.
      * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein „x“ angezeigt, mit dem Sie das Tag löschen können.
      * Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/sites-console/tags.md).
   * **In der Navigation ausblenden** – Gibt an, ob die Seite in der Seitennavigation der resultierenden Site ein- oder ausgeblendet werden soll.

* **Branding**

  Wenden Sie eine konsistente Markenidentität auf allen Seiten an, indem Sie einen Marken-Slug an jeden Seitentitel anhängen. Diese Funktion erfordert die Verwendung der Seitenkomponente ab Version 2.14.0 der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)

   * **Marken-Slug**

      * **Überschreiben**: Aktivieren Sie diese Option, um den Marken-Slug auf dieser Seite zu definieren.
         * Der Wert wird von allen untergeordneten Seiten geerbt, es sei denn, deren Werte zum **Überschreiben** sind ebenfalls festgelegt.
      * **Überschreibungswert** – Der Text des Marken-Slugs, der an den Seitentitel angehängt werden soll.
         * Der Wert wird nach einem Pipe-Zeichen an den Seitentitel angehängt, z. B. „Cycling Tuscany | Always ready for the WKND“.

* **HTML-ID**

   * **ID** – HTML-ID, die auf die Komponente angewandt wird.

* **Weitere Titel und Beschreibungen**

   * **Seitentitel** – Ein Titel zur Verwendung auf der Seite. Wird normalerweise von Titelkomponenten verwendet. Wenn dies leer gelassen wird, wird der **Titel** verwendet.
   * **Navigationstitel**: Sie können einen eigenen Titel für die Navigation angeben (z. B. wenn Sie einen kürzeren Titel wünschen). Wenn dies leer gelassen wird, wird der **Titel** verwendet.
   * **Untertitel**: Ein Untertitel zur Verwendung auf der Seite.
   * **Beschreibung** – Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit/Ausschaltzeit**

  >[!NOTE]
  >
  > Weitere Informationen zum Konfigurieren der zugehörigen automatischen Replikation finden Sie unter [Ein- und Ausschaltzeiten – Trigger-Konfiguration](/help/operations/replication.md#on-and-off-times-trigger-configuration).

  >[!NOTE]
  >Wenn entweder die **Einschaltzeit** oder die **Ausschaltzeit** in der Vergangenheit liegt und die automatische Replikation konfiguriert ist, wird die entsprechende Aktion sofort ausgelöst.

   * **Einschaltzeit**: Zeitpunkt (Datum und Uhrzeit), zu dem die veröffentlichte Seite in der Publishing-Umgebung sichtbar (gerendert) wird. Die Seite muss entweder manuell oder durch vorkonfigurierte automatische Replikation veröffentlicht werden.

      * Wenn diese Seite bereits [(manuell) veröffentlicht wurde](/help/sites-cloud/authoring/sites-console/publishing-pages.md), wird sie bis zum Rendern am angegebenen Zeitpunkt ruhend (ausgeblendet) gehalten.
      * Wenn die Seite nicht veröffentlicht, aber für die automatische Replikation konfiguriert ist, wird sie automatisch veröffentlicht und dann zum festgelegten Zeitpunkt gerendert.
      * Wenn die Seite nicht veröffentlicht und nicht für die automatische Replikation konfiguriert ist, wird sie nicht automatisch veröffentlicht. Daher wird ein 404-Fehler angezeigt, wenn versucht wird, auf die Seite zuzugreifen.

   * **Ausschaltzeit**: Ähnlich wie und häufig in Kombination mit der **Einschaltzeit** wird hier der Zeitpunkt festgelegt, zu dem die Publishing-Umgebung auf der Veröffentlichungsseite ausgeblendet wird.

   * Lassen Sie diese Felder (**Einschaltzeit** und **Ausschaltzeit**) für Seiten, die Sie sofort veröffentlichen möchten und die in der Veröffentlichungsumgebung verfügbar sein sollen, leer, bis sie deaktiviert werden (der Normalfall).

* **Vanity-URL**

   * Ermöglicht die Eingabe einer Vanity-URL für diese Seite, was es Ihnen ermöglicht, eine kürzere bzw. aussagekräftigere URL zu verwenden.
   * Beispiel: Wenn die Vanity-URL `welcome` für die Seite mit dem Pfad `/v1.0/startpage` auf der Website `http://example.com` verwendet wird, wäre `http://example.com/welcome` die Vanity-URL von `http://example.com/content/v1.0/startpage`

  >[!CAUTION]
  >
  >Vanity-URLs:
  >
  >* müssen eindeutig sein, Sie müssen also darauf achten, dass der Wert nicht bereits von einer anderen Seite verwendet wird.
  >* unterstützen keine Regex-Muster.
  >* sollten nicht auf eine vorhandene Seite eingestellt sein.

   * **Hinzufügen** – Wählen Sie dies aus, um ein Feld anzuzeigen, in dem eine Vanity-URL für die Seite definiert wird.
      * Wählen Sie es erneut aus, um mehrere hinzuzufügen.
      * Wählen Sie das Symbol **Entfernen** aus, um die Vanity-URL zu löschen.
   * **Vanity-URL umleiten** – Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll.

### Erweitert {#advanced}

* **Einstellungen**

   * **Sprache** – Die Seitensprache
   * **Sprachstamm** – Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.
   * **Redirect** – Gibt die Seite an, zu der diese Seite automatisch mit einem HTML `302 Found`-Status weitergeleitet werden soll.
      * **Ständige Umleitung** – Wenn diese Option aktiviert ist, wird die Seite zum Zielpfad weitergeleitet, der zusammen mit dem HTML-Status `301 Moved Permanently` bereitgestellt wird.
   * **Design** – Gibt an, ob die Seite in der Seitennavigation der resultierenden Seite ein- oder ausgeblendet sein soll.
   * **Alias** – Gibt einen Alias an, der für diese Seite verwendet werden soll.
      * Beispiel: Wenn Sie einen Alias `private` für die Seite `/content/wknd/us/en/magazine/members-only` definieren, kann auf diese Seite über `/content/wknd/us/en/magazine/private` zugegriffen werden.
      * Durch die Erstellung eines Alias wird die Eigenschaft `sling:alias`, die sich nur auf die Ressource und nicht auf den Repository-Pfad auswirkt, auf dem Seitenknoten festgelegt.
      * Seiten, auf die im Editor über Aliasnamen zugegriffen wird, können nicht veröffentlicht werden. [Veröffentlichungsoptionen](/help/sites-cloud/authoring/sites-console/publishing-pages.md) im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.
      * Siehe [„Lokalisierte Seitennamen“ unter „Best Practices für SEO- und URL-Verwaltung“](/help/overview/seo-and-url-management.md#localized-page-names).

* **Konfiguration**

   * **Von &lt;path> geerbt** – Aktivierung/Deaktivierung der Vererbung; stellt die Verfügbarkeit der **Cloud-Konfiguration** zur Auswahl

   * **Cloud-Konfiguration** – Der Pfad zur gewählten Konfiguration

* **Vorlageneinstellungen**

   * **Erlaubte Vorlagen**: [Definiert die Liste der Vorlagen, die innerhalb dieses Unterzweigs verfügbar sind](/help/sites-cloud/authoring/page-editor/templates.md#enabling-and-allowing-a-template-template-author)

* **Authentifizierungspflicht**

   * **Aktivieren** - Aktivieren Sie die Verwendung der Authentifizierung für den Zugriff auf die Seite.

     >[!NOTE]
     >
     >Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](#permissions)** definiert.

   * **Anmeldeseite** - Die für die Anmeldung zu verwendende Seite

* **Export**

   * **Exportkonfiguration** – Gibt eine Exportkonfiguration an

* **SEO**

   * **Kanonische URL**: Kann verwendet werden, um die kanonische URL der Seite zu überschreiben; wenn Sie das Feld leer lassen, dient die URL der Seite als ihre kanonische URL

   * **Robots-Tags** – Wählen Sie die Robots-Tags aus, um das Verhalten der Suchmaschinen-Crawler zu steuern.

     >[!NOTE]
     >
     >Einige der Optionen stehen in Konflikt miteinander. Im Falle eines Konflikts hat die Option mit größerer Berechtigung Vorrang.

   * **Sitemap generieren**: Wenn ausgewählt, wird eine sitemap.xml für diese Seite und ihre Unterseiten generiert

### Bilder {#images}

* **Vorgestelltes Bild**

  Wählen Sie das anzuzeigende Bild aus und konfigurieren Sie es. Dies wird in Komponenten verwendet, die auf die Seite verweisen. z. B. Teaser, Seitenlisten usw.

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

* **Aktuelle Live Copies**: Listet Seiten auf, die auf dieser Blueprint-Seite basieren (das heißt, Live Copies dieser Seite sind).

* **Rollout-Konfigurationen**: Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden.

### Live Copy {#live-copy}

Diese Registerkarte ist nur für Seiten sichtbar, die als Live Copys konfiguriert sind. Wie Blueprints sind Live Copys Teil des [Multi-Site-Managements](/help/sites-cloud/administering/msm/overview.md).

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
   * **Rollout-Konfiguration auswählen**: Legt fest, unter welchen Umständen Änderungen aus dem Blueprint übernommen werden, und ist nur verfügbar, wenn **Rollout-Konfigurationen von übergeordneter Seite erben** nicht aktiviert ist.

### Vorschau {#preview}

Wenn eine Vorschau-Umgebung aktiviert ist, sehen Sie Folgendes:

* Vorschau-URL – die URL, die für den Zugriff auf die Inhalte in der Vorschau-Umgebung verwendet wird

### Progressive Web App {#progressive-web-app}

Durch eine einfache Konfiguration können Inhaltsautorinnen und -autoren jetzt PWA (Progressive Web App)-Funktionen für in AEM Sites erstellte Erlebnisse aktivieren.

>[!NOTE]
>
>Siehe [Aktivieren der Progressive Web App-Funktionen](/help/sites-cloud/authoring/sites-console/enable-pwa.md).

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
      * **Vorab-Caching von Dateien (technische Vorschau)**: In AEM gehostete Dateien werden beim Installieren des Service-Worker und vor dessen Verwendung im lokalen Browser-Cache gespeichert
      * **Client-seitige Bibliotheken** – Client-seitige Bibliotheken zum Zwischenspeichern für Offline-Erlebnisse
      * **Pfadeinschlüsse** – Netzwerkanfragen für die definierten Pfade werden abgefangen, und zwischengespeicherte Inhalte werden entsprechend der konfigurierten Caching-Strategie und der Häufigkeit der Inhaltsaktualisierung zurückgegeben
      * **Pfadausschlüsse** – Diese Dateien werden unabhängig von den Einstellungen zum Vorab-Caching von Dateien und zu Pfadeinschlüssen niemals zwischengespeichert

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-1}

* In der Konsole **Sites**:
   * [beim Erstellen einer neuen Seite](/help/sites-cloud/authoring/sites-console/creating-pages.md#creating-a-new-page) (ein Teil der Eigenschaften)
   * durch Klicken oder Tippen auf **Eigenschaften**
      * Für eine einzelne Seite
      * Für mehrere Seiten (nur eine Teilmenge der Eigenschaften steht zur Massenbearbeitung zur Verfügung)
* Im Seiteneditor:
   * mithilfe der Option **Seiteninformationen** (anschließend **Eigenschaften öffnen**)

### In der Sites-Konsole (einzelne Seite) {#from-the-sites-console-single-page}

durch Klicken oder Tippen auf **Eigenschaften**, um die Seiteneigenschaften festzulegen:

1. Navigieren Sie in der **Sites-Konsole** zu der Seite, für die Sie Eigenschaften anzeigen und bearbeiten möchten.
1. Wählen Sie die Option **Eigenschaften** für die gewünschte Seite aus, indem Sie wahlweise Folgendes verwenden:
   * [Schnellaktionen](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/basic-handling.md#selecting-resources)
   * Die Seiteneigenschaften werden in den entsprechenden Registerkarten angezeigt.
1. Sie können die Eigenschaften nach Bedarf anzeigen oder bearbeiten.
1. Speichern Sie dann Ihre Aktualisierungen mit **Speichern** und klicken Sie danach auf **Schließen**, um zur Konsole zurückzukehren.

### Beim Bearbeiten einer Seite {#when-editing-a-page}

Beim Bearbeiten einer Seite können Sie mithilfe von **Seiteninformationen** die Seiteneigenschaften definieren:

1. Öffnen Sie die Seite, für die Sie Eigenschaften bearbeiten möchten.
1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Auswahlmenü zu öffnen:
1. Wählen Sie **Eigenschaften öffnen**. Daraufhin wird ein Dialogfeld geöffnet, in dem Sie die Eigenschaften bearbeiten können. Die Eigenschaften werden nach der entsprechenden Registerkarte sortiert. Die folgenden Schaltflächen stehen rechts in der Symbolleiste zur Verfügung:
   * **Abbrechen**
   * **Speichern und schließen**
1. Mit der Schaltfläche **Speichern und schließen** können Sie Änderungen speichern.

### In der Sites-Konsole (mehrere Seiten) {#from-the-sites-console-multiple-pages}

In der **Sites** Console können Sie mehrere Seiten auswählen und dann die Seiteneigenschaften mithilfe der **Ansichtseigenschaften** anzeigen und/oder bearbeiten. Dies wird als Massenbearbeitung von Seiteneigenschaften bezeichnet.

Sie können mehrere Seiten für die Massenbearbeitung mit verschiedenen Methoden auswählen, darunter:

* Beim Durchsuchen der **Sites**-Konsole
* Nach Verwendung von **Suche**, um einen Seitensatz zu finden

Nach Auswahl der Seiten und anschließendem Klicken oder Tippen auf die Option **Eigenschaften** werden die Masseneigenschaften angezeigt:

![Massenbearbeitung von Seiteneigenschaften](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

Sie können nur Massenbearbeitungen von Seiten durchführen, die:

* den gleichen Ressourcentyp haben
* nicht Teil einer Live Copy sind
   * Ist eine der Seiten Teil einer Live Copy, wird beim Öffnen der Eigenschaften eine Meldung angezeigt.

Nach dem Start der Massenbearbeitung können Sie folgende Aktionen ausführen:

* **Anzeigen**

   * eine Liste der betroffenen Seiten
      * Bei Bedarf können Sie Seiten auswählen oder ihre Auswahl aufheben
      * Registerkarten
         * Wie beim Anzeigen von Eigenschaften für eine einzelne Seite werden die Eigenschaften unter Registerkarten angeordnet.
   * Eine Untergruppe von Eigenschaften
      * Eigenschaften, die auf allen ausgewählten Seiten verfügbar sind und explizit als für die Massenbearbeitung verfügbar definiert wurden, sind sichtbar.
      * Wenn Sie die Seitenauswahl auf eine Seite reduzieren, sind alle Eigenschaften sichtbar.
   * Gemeinsame Eigenschaften mit einem gemeinsamen Wert
      * Nur Eigenschaften mit einem gemeinsamen Wert werden im Ansichtsmodus angezeigt.
      * Wenn es sich um ein mehrwertiges Feld handelt (z. B. Tags), werden die Werte nur angezeigt, wenn *alle* übereinstimmen. Wenn nur einige übereinstimmen, werden sie nur bei der Bearbeitung angezeigt.
      * Wenn keine Eigenschaften mit einem gemeinsamen Wert vorhanden sind, wird eine Meldung angezeigt.

* **Bearbeiten**

   * Sie können die Werte in den verfügbaren Feldern aktualisieren.
      * Die neuen Werte werden auf alle gewählten Seiten angewendet, wenn Sie **Fertig** wählen.
      * Wenn das Feld mehrwertig ist (z. B. Tags), können Sie entweder einen neuen Wert anhängen oder einen gemeinsamen Wert entfernen.
   * Felder, die häufig vorkommen, aber auf den verschiedenen Seiten unterschiedliche Werte haben, werden durch einen speziellen Wert angegeben, beispielsweise `<Mixed Entries>`.
