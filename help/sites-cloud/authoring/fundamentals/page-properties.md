---
title: Bearbeiten der Seiteneigenschaften
description: Definieren der erforderlichen Eigenschaften für eine Seite
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 100%

---

# Bearbeiten der Seiteneigenschaften {#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden und andere Seiten nicht. Entsprechend sind auch die Live Copy-Informationen verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt.

### Einfach {#basic}

* **Titel und Tags**

   * **Titel** - Der Titel der Seite wird an verschiedenen Stellen angezeigt. Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.
      * Dies ist ein Pflichtfeld.
   * **Tags** - Hier können Sie der Seite Tags hinzufügen (oder davon entfernen), indem Sie die Liste im Auswahlfeld aktualisieren.
      * Wenn Sie ein Tag ausgewählt haben, wird es unter dem Auswahlfeld aufgeführt. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
      * Ein vollkommen neues Tag kann angegeben werden, indem Sie den Namen in ein leeres Auswahlfeld eingeben.
         * Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
         * Das neue Tag wird dann mit einem kleinen Stern auf der rechten Seite angezeigt, der es als neues Tag kennzeichnet.
      * In der Dropdown-Liste können Sie aus vorhandenen Tags auswählen.
      * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein x angezeigt, mit dessen Hilfe Sie das Tag löschen können.
      * Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/features/tags.md).
   * **In Navigation ausblenden** – Gibt an, ob die Seite in der Seitennavigation der resultierenden Seite ein- oder ausgeblendet sein soll.

* **Branding**

   Wenden Sie eine konsistente Markenidentität auf allen Seiten an, indem Sie einen Marken-Slug an jeden Seitentitel anhängen. Diese Funktion erfordert die Verwendung der Seitenkomponente ab Version 2.14.0 der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)

   * **Überschreiben** – Aktivieren Sie diese Option, um den Marken-Slug auf dieser Seite zu definieren.
      * Der Wert wird von allen untergeordneten Seiten geerbt, es sei denn, deren **Überschreiben**-Werte sind auch eingestellt.
   * **Überschreibungswert** – Der Text des Marken-Slugs, der an den Seitentitel angehängt werden soll.
      * Der Wert wird nach einem Pipe-Zeichen an den Seitentitel angehängt, z. B. „Cycling Tuscany | Always ready for the WKND“.

* **HTML-ID**

   * **ID** – HTML-ID, die auf die Komponente angewandt wird.

* **Weitere Titel und Beschreibungen**

   * **Seitentitel** – Ein Titel zur Verwendung auf der Seite. Dieser wird üblicherweise von Titel-Komponenten verwendet. Wenn dieses Feld leer bleibt, wird der **Titel** verwendet.
   * **Navigationstitel** – Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie eine kürzere Alternative wählen möchten). Wenn dieses Feld leer bleibt, wird der **Titel** verwendet.
   * **Untertitel** – Ein Untertitel zur Verwendung auf der Seite.
   * **Beschreibung** – Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit/Ausschaltzeit**

   * **Einschaltzeit** – Zeitpunkt (Datum und Uhrzeit), zu dem die veröffentlichte Seite in der Veröffentlichungsumgebung sichtbar (gerendert) wird. Die Seite muss entweder manuell oder durch vorkonfigurierte automatische Replikation veröffentlicht werden.

      >[!NOTE]
      >
      > Weitere Informationen zum Konfigurieren der zugehörigen automatischen Replikation finden Sie unter [Ein- und Ausschaltzeiten – Trigger-Konfiguration](/help/operations/replication.md#on-and-off-times-trigger-configuration).

      * Wenn diese Seite bereits [(manuell) veröffentlicht wurde](/help/sites-cloud/authoring/fundamentals/publishing-pages.md), wird sie bis zum Rendern am angegebenen Zeitpunkt ruhend (ausgeblendet) gehalten.
      * Wenn die Seite nicht veröffentlicht, aber für die automatische Replikation konfiguriert ist, wird sie automatisch veröffentlicht und dann zum festgelegten Zeitpunkt gerendert.
      * Wenn die Seite nicht veröffentlicht und nicht für die automatische Replikation konfiguriert ist, wird sie nicht automatisch veröffentlicht. Daher wird ein 404-Fehler angezeigt, wenn versucht wird, auf die Seite zuzugreifen.
   * **Ausschaltzeit** – Ähnlich wie und häufig in Kombination mit der **Einschaltzeit** wird hier der Zeitpunkt festgelegt, zu dem die veröffentlichte Umgebung auf der Veröffentlichungsseite ausgeblendet wird.

   * Lassen Sie diese Felder (**Einschaltzeit** und **Ausschaltzeit**) für Seiten, die Sie sofort veröffentlichen möchten und die in der Veröffentlichungsumgebung verfügbar sein sollen, leer, bis sie deaktiviert werden (der Normalfall).


* **Vanity-URL**

   * Ermöglicht die Eingabe einer Vanity-URL für diese Seite, sodass Sie eine kürzere bzw. aussagekräftigere URL verwenden können.
   * Beispiel: Wenn die Vanity-URL `welcome` für die Seite mit dem Pfad `/v1.0/startpage` auf der Website `http://example.com` verwendet wird, wäre `http://example.com/welcome` die Vanity-URL von `http://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >Vanity-URLs:
   >
   >* müssen eindeutig sein, Sie müssen also darauf achten, dass der Wert nicht bereits von einer anderen Seite verwendet wird.
   >* unterstützen keine regex-Muster.
   >* sollten nicht auf eine vorhandene Seite eingestellt sein.


   * **Hinzufügen** - Tippen oder klicken Sie, um ein Feld anzuzeigen, in dem eine Vanity-URL für die Seite definiert wird.
      * Tippen oder klicken Sie erneut, um mehrere hinzuzufügen.
      * Tippen oder klicken Sie auf das Symbol **Entfernen**, um die Vanity-URL zu löschen.
   * **Vanity-URL umleiten** - Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll.




### Erweitert {#advanced}

* **Einstellungen**

   * **Sprache** – Die Seitensprache
   * **Sprachstamm** – Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.
   * **Umleiten** – Gibt die Seite an, zu der diese Seite automatisch umgeleitet werden soll.
   * **Design** – Gibt an, ob die Seite in der Seitennavigation der resultierenden Seite ein- oder ausgeblendet sein soll.
   * **Alias** – Gibt einen Alias an, der für diese Seite verwendet werden soll.

   >[!NOTE]
   >
   >Alias legt die Eigenschaft `sling:alias` fest, um einen Alias für die Ressource zu definieren (dies betrifft nur die Ressource, nicht den Pfad).
   >
   >Beispiel: Wenn Sie einen Alias `latin-lang` für den Knoten `/content/we-retail/spanish` definieren, kann auf diese Seite über `/content/we-retail/latin-language` zugegriffen werden.
   >
   >Weitere Informationen finden Sie in „Lokalisierte Seitennamen“ unter „Best Practices für SEO- und URL-Verwaltung“.

   <!--
  >For further details see [Localized page names under SEO and URL Management Best Practices](/help/managing/seo-and-url-management.md#localized-page-names).
  -->

* **Konfiguration**

   * **Cloud-Konfiguration** – Der Pfad zur Konfiguration

* **Vorlageneinstellungen**

   * **Erlaubte Vorlagen** - [Definiert die Liste der Vorlagen, die in dieser](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) Zweigstelle verfügbar sein werden.

* **Authentifizierungspflicht**

   * **Aktivieren** - Aktivieren Sie die Verwendung der Authentifizierung für den Zugriff auf die Seite.

      >[!NOTE]
      >
      >Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](#permissions)** definiert.

   * **Anmeldeseite** - Die für die Anmeldung zu verwendende Seite

* **Export**

   * **Exportkonfiguration** – Gibt eine Exportkonfiguration an

### Miniaturansicht {#thumbnail}

Konfigurieren der Miniaturansicht der Seite

* **Vorschau generieren** – Erstellen Sie eine Vorschau der Seite, die als Miniatur verwendet werden soll.
* **Bild hochladen** – Laden Sie ein Bild hoch, das als Miniatur verwendet werden soll.
* **Bild auswählen** – Wählen Sie ein vorhandenes Asset aus, das als Miniatur verwendet werden soll.
* **Wiederherstellen** – Diese Option wird verfügbar, nachdem Sie eine Änderung an der Miniatur vorgenommen haben. Wenn Sie Ihre Änderungen nicht behalten möchten, können Sie sie vor dem Speichern rückgängig machen.

### Social Media {#social-media}

* **Freigabe in Social Media**

   Definiert die auf der Seite verfügbaren Freigabeoptionen. Zeigt die Optionen an, die für die zentrale Komponente für die [Freigabe](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/sharing.html) zur Verfügung stehen.

   * **Benutzerfreigabe aktivieren für Facebook**
   * **Benutzerfreigabe aktivieren für Pinterest**
   * **Bevorzugte XF-Variante**
      * Definieren Sie die Experience Fragment-Variante, die zum Generieren von Metadaten für die Seite verwendet werden soll.

### Cloud Services {#cloud-services}

* **Cloud Service-Konfigurationen** – Legen Sie Eigenschaften für Cloud Services fest

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### Personalisierung {#personalization}

* **ContextHub-Konfigurationen**

   * **ContextHub-Pfad** – Definieren der [ContextHub-Konfiguration](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Segmentpfad** – Definieren des [Segmentpfads](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **Konfiguration für Targeting**

   * **Marke** – Legt eine [Marke fest, um einen Bereich für das Targeting anzugeben](/help/sites-cloud/authoring/personalization/targeted-content.md).
   >[!NOTE]
   >Für diese Option muss das Benutzerkonto der `Target Administrators`-Gruppe angehören.

### Berechtigungen {#permissions}

* **Berechtigungen**

   * Berechtigungen hinzufügen
   * Geschlossene Benutzergruppe bearbeiten
   * Effektive Berechtigungen anzeigen

   <!--[Add Permissions](/help/sites-administering/user-group-ac-admin.md) -->

   <!-- [Edit Closed User Group](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)-->

   <!-- View the [Effective Permissions](/help/sites-administering/user-group-ac-admin.md)-->

### Blueprint {#blueprint}

Diese Registerkarte ist nur für Seiten sichtbar, die als Blueprints dienen. Blueprints dienen als Grundlage für Live Copies uns sind Teil des [Multi-Site-Management.](/help/sites-cloud/administering/msm/overview.md)

* **Aktuelle Live Copies** – Listet die Seiten auf, die auf dieser Blueprint-Seite basieren (d. h. Live Copies davon sind)

* **Rollout-Konfigurationen** – Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden.

### Live Copy  {#live-copy}

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
   * **Rollout-Konfiguration auswählen** – Legt fest, unter welchen Umständen Änderungen aus dem Blueprint übernommen werden, und ist nur verfügbar, wenn **Rollout-Konfigurationen von übergeordneter Seite übernehmen** nicht aktiviert ist.

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-1}

* In der Konsole **Sites**:
   * [beim Erstellen einer neuen Seite](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (ein Teil der Eigenschaften)
   * durch Klicken oder Tippen auf **Eigenschaften**
      * für eine einzelne Seite
      * für mehrere Seiten (bei der Massenbearbeitung steht nur ein Teil der Eigenschaften zur Verfügung)
* Im Seiteneditor:
   * mithilfe der Option **Seiteninformationen** (anschließend **Eigenschaften öffnen**)

### In der Sites-Konsole (einzelne Seite) {#from-the-sites-console-single-page}

durch Klicken oder Tippen auf **Eigenschaften**, um die Seiteneigenschaften festzulegen:

1. Navigieren Sie in der **Sites-Konsole** zu der Seite, für die Sie Eigenschaften anzeigen und bearbeiten möchten.
1. Wählen Sie die Option **Eigenschaften** für die gewünschte Seite aus, indem Sie wahlweise Folgendes verwenden:
   * [Schnellaktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * Die Seiteneigenschaften werden in den entsprechenden Registerkarten angezeigt.
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

>[!NOTE]
>
>Die Massenbearbeitung von Eigenschaften ist auch für Assets verfügbar. Dieses Verfahren ist sehr ähnlich, weicht aber in einigen Punkten ab. Weitere Informationen dazu finden Sie unter „Bearbeiten von Eigenschaften für mehrere Assets“.
>
>Darüber hinaus steht Ihnen die Massenbearbeitung zur Verfügung. Damit können Sie mithilfe von GQL (Google Query Language) auf mehreren Seiten nach Inhalten suchen und die Inhalte anschließend direkt im Bulk Editor bearbeiten, bevor Sie die Änderungen an den Ursprungsseiten speichern.

<!--
>Bulk editing of properties is also available for Assets. It is very similar, but differs in a few points. See [Editing Properties of Multiple Assets](/help/assets/managing-multiple-assets.md) for details.
>
>There is also the [Bulk Editor](/help/sites-administering/bulk-editor.md), which allows you to search for content from multiple pages using GQL (Google Query Language) and then edit the content directly in the bulk editor before saving your changes to the originating pages.
-->

Sie können mehrere Seiten zur Massenbearbeitung auf verschiedene Arten auswählen, einschließlich:

* Beim Navigieren in der **Sites-Konsole**
* Nach dem Verwenden der **Suche** zum Auffinden einer Gruppe aus Seiten

Nach Auswahl der Seiten und anschließendem Klicken oder Tippen auf die Option **Eigenschaften** werden die Masseneigenschaften angezeigt:

![Massenbearbeitung von Seiteneigenschaften](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

Sie können die Massenbearbeitung nur für Seiten durchführen, die:

* denselben Ressourcentyp verwenden
* nicht Teil einer Live Copy sind
   * Ist eine der Seiten Teil einer Live Copy, wird beim Öffnen der Eigenschaften eine Meldung angezeigt.

Nach dem Start der Massenbearbeitung können Sie folgende Aktionen ausführen:

* **Anzeigen**

   * Eine Liste der betroffenen Seiten
      * Sie können Seiten nach Bedarf auswählen/entfernen.
      * Registerkarten
         * Wie beim Anzeigen der Eigenschaften für eine einzelne Seite werden auch hier die Eigenschaften in Registerkarten angeordnet.
   * Eine Teilmenge der Eigenschaften
      * Eigenschaften, die auf allen ausgewählten Seiten verfügbar sind und explizit als für die Massenbearbeitung verfügbar definiert wurden, sind sichtbar.
      * Wenn Sie die Seitenauswahl auf eine Seite reduzieren, sind alle Eigenschaften sichtbar.
   * Gemeinsame Eigenschaften mit einem gemeinsamen Wert
      * Nur Eigenschaften mit einem gemeinsamen Wert werden im Ansichtsmodus angezeigt.
      * Wenn das Feld mehrwertig ist (z. B. Tags), werden nur Werte angezeigt, die *alle* gleich sind. Wenn nur einige gleich sind, werden diese nur bei der Bearbeitung angezeigt.
      * Wenn keine Eigenschaften mit einem gemeinsamen Wert vorhanden sind, wird eine Meldung angezeigt.

* **Bearbeiten**

   * Sie können die Werte in den verfügbaren Feldern aktualisieren.
      * Die neuen Werte werden auf alle gewählten Seiten angewendet, wenn Sie **Fertig** wählen.
      * Wenn das Feld mehrwertig ist (z. B. Tags), können Sie einen neuen Wert anhängen oder einen gemeinsamen Wert entfernen.
   * Gemeinsame Felder, die unterschiedliche Werte auf den verschiedenen Seiten aufweisen, werden durch einen speziellen Wert angegeben, beispielsweise `<Mixed Entries>`. Bei der Bearbeitung dieser Felder ist Vorsicht geboten, um Datenverluste zu vermeiden.

>[!NOTE]
>
>Die Seitenkomponente kann so konfiguriert werden, dass die für die Massenbearbeitung verfügbaren Felder angegeben werden. Informationen dazu finden Sie unter „Konfigurieren der Seite für Massenbearbeitung von Seiteneigenschaften“.

<!--
>The page component can be configured to specify the fields available for bulk editing. See [Configuring your page for bulk editing of page properties](/help/sites-developing/bulk-editing.md).
-->
