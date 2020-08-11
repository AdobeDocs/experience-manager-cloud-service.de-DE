---
title: Bearbeiten der Seiteneigenschaften
description: Definieren der erforderlichen Eigenschaften für eine Seite
translation-type: tm+mt
source-git-commit: abb45225e880f3d08b9d26c29e243037564acef0
workflow-type: tm+mt
source-wordcount: '1675'
ht-degree: 88%

---


# Bearbeiten der Seiteneigenschaften {#editing-page-properties}

Sie können die erforderlichen Eigenschaften für eine Seite definieren. Diese können je nach Art der Seite variieren. Beispielsweise sind einige Seiten möglicherweise mit einer Live Copy verbunden und andere Seiten nicht. Entsprechend sind auch die Live Copy-Informationen verfügbar.

## Seiteneigenschaften {#page-properties}

Die Eigenschaften sind auf verschiedene Registerkarten verteilt.

### Allgemein {#basic}

* **Titel**

   * Der Titel der Seite wird an verschiedenen Stellen angezeigt. Zum Beispiel in der Liste auf der Registerkarte **Websites** und in den Karten-/Listenansichten **Sites**.
   * Dies ist ein Pflichtfeld.

* **Tags**

   * Hier können Sie der Seite Tags hinzufügen (oder davon entfernen), indem Sie die Liste im Auswahlfeld aktualisieren.
   * Wenn Sie ein Tag ausgewählt haben, wird es unter dem Auswahlfeld aufgeführt. Sie können ein Tag mit dem „x“ aus dieser Liste entfernen.
   * Ein vollkommen neues Tag kann angegeben werden, indem Sie den Namen in ein leeres Auswahlfeld eingeben.
      * Das neue Tag wird erstellt, wenn Sie die Eingabetaste drücken.
      * Das neue Tag wird dann mit einem kleinen Stern auf der rechten Seite angezeigt, der es als neues Tag kennzeichnet.
   * In der Dropdown-Liste können Sie aus vorhandenen Tags auswählen.
   * Wenn Sie den Mauszeiger über ein Tag im Auswahlfeld halten, wird ein x angezeigt, mit dessen Hilfe Sie das Tag löschen können.
   * Weitere Informationen zu Tags finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/features/tags.md).

* **In Navigation ausblenden**

   * Gibt an, ob die Seite in der Seitennavigation der resultierenden Seite ein- oder ausgeblendet sein soll.

* **HTML-ID**

   * HTML-ID, die auf die Komponente angewandt wird.

* **Seitentitel**

   * Ein Titel zur Verwendung auf der Seite. Dieser wird üblicherweise von Titel-Komponenten verwendet. Wenn dieses Feld leer bleibt, wird der **Titel** verwendet.

* **Navigationstitel**

   * Sie können einen separaten Titel für die Verwendung in der Navigation angeben (z. B. wenn Sie eine kürzere Alternative wählen möchten). Wenn dieses Feld leer bleibt, wird der **Titel** verwendet.

* **Untertitel**

   * Ein Untertitel zur Verwendung auf der Seite.

* **Beschreibung**

   * Ihre Beschreibung der Seite, der Zweck oder beliebige andere Details, die Sie hinzufügen möchten.

* **Einschaltzeit**

   * The date and time at which the published page will be made visible (rendered) on the publish environment. The page must be published, either manually or by pre-configured auto-replication.

      >[!NOTE]
      >
      > See [On and Off Times - Trigger Configuration](/help/operations/replication.md#on-and-off-times-trigger-configuration) for details of how to configure the related automatic replication.

      * Wenn diese Seite bereits [veröffentlicht wurde (manuell)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) , wird sie bis zum Rendern zur angegebenen Zeit ruhend (ausgeblendet) gehalten.
      * Wenn die Seite nicht veröffentlicht und für die automatische Replizierung konfiguriert ist, wird sie automatisch veröffentlicht und dann zur festgelegten Zeit gerendert.
      * Wenn die Seite nicht veröffentlicht und nicht für die automatische Replizierung konfiguriert ist, wird sie nicht automatisch veröffentlicht. Daher wird ein 404 angezeigt, wenn versucht wird, auf die Seite zuzugreifen.
   * Lassen Sie diese Felder (**On Time** and **Off Time**) für Seiten, die Sie sofort veröffentlichen möchten und die auf der Umgebung &quot;publish&quot;verfügbar sind, leer, bis sie deaktiviert sind (im Normalfall).

* **Ausschaltzeit**

   * Parallel zur **On-Time** definiert dies den Zeitpunkt, zu dem die veröffentlichte Umgebung auf der Veröffentlichungsseite ausgeblendet wird.
   * Lassen Sie diese Felder (**On Time** and **Off Time**) für Seiten, die Sie sofort veröffentlichen möchten und die auf der Umgebung &quot;publish&quot;verfügbar sind, leer, bis sie deaktiviert sind (im Normalfall).

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


* **Vanity-URL umleiten**

   * Gibt an, ob für die Seite eine Vanity-URL verwendet werden soll.

### Erweitert {#advanced}

* **Sprache**

   * Die Seitensprache.

* **Sprach-Stamm**

   * Muss aktiviert werden, wenn die Seite als Stamm einer Sprachkopie fungiert.

* **Umleiten**

   * Geben Sie eine Seite an, zu der die Seite automatisch umgeleitet werden soll.

* **Design**

   * Gibt an, ob die Seite in der Seitennavigation der resultierenden Seite ein- oder ausgeblendet sein soll.

* **Alias**

   * Geben Sie einen Alias an, der für diese Seite verwendet werden soll.
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

<!--
* **Inherited from &lt;*path*&gt;**

  * Indicates whether the page is inherited. and where from.
-->

* **Cloud-Konfiguration**

   * Der Pfad zur Konfiguration.

* **Zugelassene Vorlagen**

   * [Definieren Sie die Liste der Vorlagen, die in dieser](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) Zweigstelle verfügbar sein werden.

* **Aktivieren** (Authentifizierungspflicht)

   * Aktivieren (oder deaktivieren) Sie die Verwendung der Authentifizierung für den Zugriff auf die Seite.
   >[!NOTE]
   >
   >Geschlossene Benutzergruppen (CUGs) für die Seite werden auf der Registerkarte **[Berechtigungen](#permissions)**definiert.

* **Anmeldeseite**

   * Die für die Anmeldung zu verwendende Seite.

* **Konfiguration exportieren**

   * Geben Sie eine Exportkonfiguration an.

### Miniaturansicht       {#thumbnail}

Zeigt das Miniaturbild der Seite an. Sie haben folgende Möglichkeiten:

* **Vorschau generieren**

   * Erstellen Sie eine Vorschau der Seite, die als Miniatur verwendet werden soll.

* **Bild hochladen**

   * Laden Sie ein Bild hoch, das als Miniatur verwendet werden soll.

* **Bild auswählen**

   * Wählen Sie ein vorhandenes Asset aus, das als Miniatur verwendet werden soll.

* **Zurück zur letzten Version**

   * Diese Option wird verfügbar, nachdem Sie eine Änderung an der Miniatur vorgenommen haben. Wenn Sie Ihre Änderungen nicht behalten möchten, können Sie sie vor dem Speichern rückgängig machen.

### Social Media {#social-media}

* **Freigabe in Social Media**

   Definiert die auf der Seite verfügbaren Freigabeoptionen. Zeigt die Optionen an, die für die zentrale Komponente für die [Freigabe](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/sharing.html) zur Verfügung stehen.

   * **Benutzerfreigabe aktivieren für Facebook**
   * **Benutzerfreigabe aktivieren für Pinterest**
   * **Bevorzugte XF-Variante**
      * Definieren Sie die Experience Fragment-Variante, die zum Generieren von Metadaten für die Seite verwendet werden soll.

### Cloud Services {#cloud-services}

* **Cloud Service-Konfigurationen**

   * Legen Sie Eigenschaften für Cloud Services fest.

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### Personalisierung      {#personalization}

* **ContextHub-Konfigurationen**

   * Wählen Sie die ContextHub-Konfiguration und den Segmentpfad aus.

   <!--Select the [ContextHub Configuration](/help/sites-administering/contexthub-config.md) and [Segments Path](/help/sites-administering/segmentation.md).
  -->

* **Konfiguration für Targeting**

   * Wählen Sie eine [Marke, um einen Bereich für das Targeting anzugeben](/help/sites-cloud/authoring/personalization/targeted-content.md).
   >[!NOTE]
   >Für diese Option muss das Benutzerkonto der `Target Adminstrators`-Gruppe angehören.

### Berechtigungen {#permissions}

* **Berechtigungen**

   * Berechtigungen hinzufügen
   * Geschlossene Benutzergruppe bearbeiten
   * Effektive Berechtigungen anzeigen

   <!--[Add Permissions](/help/sites-administering/user-group-ac-admin.md) -->

   <!-- [Edit Closed User Group](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)-->

   <!-- View the [Effective Permissions](/help/sites-administering/user-group-ac-admin.md)-->

### Blueprint {#blueprint}

* **Blueprint**

   * Legen Sie Eigenschaften für eine Blueprint-Seite fest, die für die Verwaltung mehrerer Websites verwendet wird.

   <!--Define properties for a Blueprint page within [multi-site management](/help/sites-administering/msm.md).-->

   * Steuert die Umstände, unter denen Änderungen an die Live Copy propagiert werden.


### Live Copy       {#live-copy}

* **Live Copy**

   * Legen Sie Eigenschaften für eine Live Copy-Seite fest, die für die Verwaltung mehrerer Websites verwendet wird. <!--Define properties for a Live Copy page within [multi-site management](/help/sites-administering/msm.md).-->
   * Steuert die Umstände, unter denen Änderungen von der Blueprint-Seite propagiert werden.

### Site-Struktur       {#site-structure}

* Geben Sie Links zu Seiten an, die Site-übergreifende Funktionalität bieten, z. B. **Anmeldungsseite**, **Offline-Seite** und andere.

## Bearbeiten der Seiteneigenschaften {#editing-page-properties-1}

* In der Konsole **Sites**:
   * [beim Erstellen einer neuen Seite](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (ein Teil der Eigenschaften)
   * durch Klicken oder Tippen auf **Eigenschaften**
      * für eine einzelne Seite
      * für mehrere Seiten (bei der Massenbearbeitung steht nur ein Teil der Eigenschaften zur Verfügung)
* Im Seiteneditor:
   * mithilfe der Option **Seiteninformationen** (anschließend **Eigenschaften öffnen**)

### In der Sites-Konsole (einzelne Seite):{#from-the-sites-console-single-page}

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

### In der Sites-Konsole (mehrere Seiten):{#from-the-sites-console-multiple-pages}

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
