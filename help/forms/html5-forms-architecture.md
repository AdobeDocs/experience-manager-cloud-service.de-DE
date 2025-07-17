---
title: Architektur von HTML5-Formularen
description: HTML5-Formulare werden als Paket innerhalb der eingebetteten AEM-Instanz bereitgestellt und stellen die Funktionalität als REST-Endpunkt über HTTP/S unter Verwendung der RESTful-Architektur von Apache Sling zur Verfügung.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: ed8349a1-f761-483f-9186-bf435899df7d
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
hide: true
hidefromtoc: true
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 97%

---

# Architektur von HTML5-Formularen{#architecture-of-html-forms}

<span class="preview"> Die HTML5 Forms-Funktion wird als Teil des Early Access-Programms angeboten. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (geschäftlichen) E-Mail-ID an aem-forms-ea@adobe.com.
</span>

## Architektur {#architecture}

Die HTML5-Formularfunktionen werden als Paket innerhalb der eingebetteten AEM-Instanz bereitgestellt. Die Bereitstellung erfolgt mithilfe einer REST-konformen [Apache Sling Architecture](https://sling.apache.org/) als REST-Endpunkt über HTTP/S.

![02-aem-forms-architecture_large](assets/02-aem-forms-architecture_large.jpg)

### Über das Sling Framework {#using-sling-framework}

[Apache Sling](https://sling.apache.org/) ist ressourcenzentriert. Es verwendet eine Anfrage-URL, um die Ressource zuerst aufzulösen. Jede Ressource verfügt über die Eigenschaft **sling:resourceType** (oder **sling:resourceSuperType**). Basierend auf dieser Eigenschaft, der Anfragemethode und den Eigenschaften der Anfrage-URL wird dann ein Sling-Skript ausgewählt, um die Anfrage zu verarbeiten. Dieses Sling-Skript kann ein JSP oder ein Servlet sein. Im Falle von HTML5-Formulare dienen **Profil**-Knoten als Sling-Ressourcen, und der **Profil-Renderer** dient als Sling-Skript, das die Anforderung bearbeitet, das mobile Formular mit einem bestimmten Profil zu rendern. Ein **Profil-Renderer** ist ein JSP, das Parameter aus einer Anforderung ausliest und den Forms OSGi-Dienst aufruft.

Weitere Informationen über REST-Endpunkte und unterstützte Anforderungsparameter finden Sie unter [Rendern einer Formularvorlage](/help/forms/rendering-form-template.md).

Wenn Benutzende eine Anfrage von einem Client-Gerät wie einem iOS- oder Android™-Browser starten, löst Sling zuerst den Profilknoten auf Basis der Anfrage-URL auf. Von diesem Profilknoten aus werden **sling:resourceSuperType** und **sling:resourceType** gelesen, um alle verfügbaren Skripte zu ermitteln, die diese Formular-Render-Anfrage verarbeiten können. Anschließend werden Sling-Anfrageselektoren zusammen mit der Anfragemethode verwendet, um das Skript zu identifizieren, das für die Verarbeitung dieser Anfrage am besten geeignet ist. Sobald die Anfrage ein Profil-Renderer-JSP erreicht, ruft das JSP den Forms OSGi-Dienst auf.

Weitere Informationen zur Sling-Skriptauflösung finden Sie unter [AEM Sling-Spickzettel](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de) oder [Apache Sling-URL-Zerlegung](https://sling.apache.org/documentation/the-sling-engine/url-decomposition.html).

#### Typischer Formular-Verarbeitungsablauf {#typical-form-processing-call-flow}

HTML5-Formulare speichert alle Zwischenobjekte zwischen, die für die Verarbeitung (Rendering oder Senden) eines Formulars bei der ersten Anforderung nötig sind. Die von den Daten abhängigen Objekte werden nicht zwischengespeichert, da sich diese wahrscheinlich ändern werden.

Formulare für Mobilgeräte verwalten zwei verschiedene Cache-Ebenen: PreRender-Cache und Render-Cache. Der PreRender-Cache enthält alle Fragmente und Bilder einer aufgelösten Vorlage und der Render-Cache enthält gerenderte Inhalte wie HTML.

![Arbeitsablauf für HTML5-Formulare](assets/cacheworkflow.png)

Arbeitsablauf für HTML5-Formulare

HTML5-Formulare speichert Vorlagen nicht zwischen, die fehlende Verweise auf Fragmente und Bilder aufweisen. Wenn HTML5-Formulare länger als gewöhnlich lädt, prüfen Sie die Server-Protokolle auf fehlende Verweise und Warnungen. Stellen Sie auch sicher, dass die maximale Größe des Objekts nicht erreicht wurde.

Der Forms OSGi-Dienst verarbeitet eine Anfrage in zwei Schritten:

* **Erstellung des Layouts und des anfänglichen Formularstatus**: Der Forms OSGi-Render-Dienst ruft die Forms-Cache-Komponente auf, um zu ermitteln, ob das Formular bereits zwischengespeichert und nicht invalidiert wurde. Wenn das Formular zwischengespeichert und validiert ist, wird das generierte HTML aus dem Cache bereitgestellt. Wenn das Formular ungültig ist, generiert der Forms OSGi-Render-Dienst das anfängliche Formularlayout und den Formularstatus im XML-Format. Diese XML-Datei wird vom Forms OSGi-Dienst in das HTML-Layout und den anfänglichen JSON-Formularstatus umgewandelt und dann für nachfolgende Anfragen zwischengespeichert.
* **Vorausgefüllte Formulare**: Wenn ein Benutzer außerdem während des Renderings anfordert, dass Formulare vorab mit Daten ausgefüllt werden sollen, ruft der Forms OSGi-Renderdienst den Forms-Dienstcontainer auf und generiert einen neuen Formularstatus mit zusammengeführten Daten. Da das Layout jedoch bereits im obigen Schritt generiert wurde, ist dieser Aufruf schneller als der erste Aufruf. Dieser Aufruf führt nur die Datenzusammenführung durch und führt die Skripte für die Daten aus.

Wenn in einem Formular ein Update vorhanden ist oder Elemente verwendet werden, wird dies von der Formular-Cachekomponente erkannt, und der Cache für dieses bestimmte Formular ist ungültig. Sobald die Verarbeitung durch den Forms OSGi-Dienst abgeschlossen ist, fügt das Profil-Renderer-JSP JavaScript-Bibliotheksverweise und -stile zu diesem Formular hinzu und gibt die Antwort an den Client zurück. Hierfür kann ein typischer Webserver wie [Apache](https://httpd.apache.org/) mit aktivierter HTML-Komprimierung verwendet werden. Ein Webserver würde die Antwortgröße, den Netzwerkverkehr und die für das Streaming zwischen dem Server und dem Client-Rechner erforderliche Zeit erheblich verringern.

Wenn ein Benutzer das Formular ausfüllt, sendet der Browser den Formularstatus im JSON-Format an den [Sendedienst-Proxy](/help/forms/service-proxy.md). Dann generiert der Sendedienst-Proxy eine Daten-XML mit JSON-Daten und sendet die Daten-XML an den Sende-Endpunkt.

## Komponenten {#components}

Sie benötigen das AEM Forms-Add-On-Paket, um HTML5-Formulare zu aktivieren. Informationen zum Installieren des AEM Forms-Add-on-Pakets finden Sie unter [Installieren und Konfigurieren von AEM Forms](/help/forms/setup-local-development-environment.md).

### OSGi-Komponenten (adobe-lc-forms-core.jar) {#osgi-components-adobe-lc-forms-core-jar}

**Adobe XFA Forms Renderer (com.adobe.livecycle.adobe-lc-forms-core)** ist der Anzeigename des HTML5 Forms OSGi-Bundles, wenn es in der Bundle-Ansicht der Felix Admin Console `(https://[host]:[port]/system/console/bundles)` angezeigt wird.

Diese Komponente enthält OSGi-Komponenten für Rendering, Cache-Verwaltung und Konfigurationseinstellungen.

#### Forms OSGi-Dienst {#forms-osgi-service}

Dieser OSGi-Dienst enthält die Logik zum Rendern einer XDP als HTML und verarbeitet die Übermittlung eines Formulars zum Generieren von Daten-XML. Dieser Dienst verwendet den Forms-Dienst-Container. Der Forms-Dienstcontainer ruft intern die native Komponente`XMLFormService.exe` auf, die anschließend die Verarbeitung durchführt.

Wenn eine Render-Anforderung eingeht, ruft diese Komponente den Forms-Servicecontainer auf, um das Layout und die Statusinformationen zu generieren, die dann weiter verarbeitet werden, um den HTML- und JSON-DOM-Status eines Formulars zu generieren.

Diese Komponente ist auch für die Generierung von Daten-XML aus dem Status-JSON des gesendeten Formulars verantwortlich.

#### Cache-Komponente {#cache-component}

HTML5-Formulare verwendet eine Zwischenspeicherung, um den Durchsatz zu maximieren und die Antwortzeit zu optimieren. Sie können die Ebene des Cache-Dienstes konfigurieren, um den Kompromiss zwischen Leistung und Platznutzung zu optimieren.

<table>
 <tbody>
  <tr>
   <th>Cache-Strategie</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Ohne</td>
   <td>Keine Artefakte zwischenspeichern<br /> </td>
  </tr>
  <tr>
   <td>Konservativ</td>
   <td>Nur Zwischenartefakte zwischenspeichern, die vor dem Rendering des Formulars generiert werden, z. B. Vorlagen mit Inline-Fragmenten und Bildern</td>
  </tr>
  <tr>
   <td>Aggressiv</td>
   <td>Den gerenderten HTML-Inhalt zwischenspeichern<br />Es werden alle Artefakte gespeichert, die in der Ebene „Konservativ“ zwischengespeichert wurden.<br /> <strong>Hinweis</strong>: Diese Strategie führt zur besten Leistung, verbraucht jedoch mehr Speicher zum Speichern der zwischengespeicherten Artefakte.</td>
  </tr>
 </tbody>
</table>

HTML5-Formulare führt eine Zwischenspeicherung im Arbeitsspeicher durch und verwendet dafür die LRU-Strategie. Wenn die Cachestrategie auf „Keine“ gestellt ist, wird kein Cachespeicher erstellt, und alle Cachedaten (falls vorhanden) werden gelöscht. Neben der Cache-Strategie können Sie auch die Gesamtgröße des Arbeitsspeicher-Caches konfigurieren, um die maximale Cache-Größe zu begrenzen. Wenn sie überschritten wird, wird der LRU-Modus verwendet, um Cache-Ressourcen freizugeben.

>[!NOTE]
>
>Der Arbeitsspeicher-Cache wird nicht zwischen Cluster-Knoten geteilt.

#### Konfigurationsdienst {#configuration-service}

Der Konfigurationsdienst ermöglicht die Anpassung der Konfigurationsparameter und Cache-Einstellungen für HTML5-Formulare.

Wenn Sie diese Einstellungen aktualisieren möchten, wählen Sie in der CQ Felix Admin Console (verfügbar unter https://&lt;&#39;[server]:[port]&#39;/system/console/configMgr) den Punkt Mobile Forms Configuration.

Sie können die Cache-Größe konfigurieren oder den Cache mithilfe des Konfigurationsdienstes deaktivieren. Sie können das Debugging auch mit dem Parameter „Debug Optionen“ aktivieren. Weitere Informationen über das Debugging von Formularen finden Sie unter [Debugging von HTML5-Formularen](/help/forms/debug.md).

### Laufzeitkomponenten (adobe-lc-forms-runtime-pkg.zip) {#runtime-components-adobe-lc-forms-runtime-pkg-zip}

Das Laufzeitpaket enthält die Client-seitigen Bibliotheken, die zum Rendern von HTML-Formularen verwendet werden.

**Wichtige Komponenten, die als Teil des Laufzeitpakets verfügbar sind:**

#### Scripting Engine {#scripting-engine}

Die XFA-Implementierung von Adobe unterstützt zwei Arten von Skriptsprachen, um die Ausführung der benutzerdefinierten Logik in Formularen zu ermöglichen: JavaScript und FormCalc.

Die Scripting Engine von HTML Forms ist in JavaScript geschrieben, um die XFA-Skript-API in beiden Sprachen zu unterstützen.

Während des Renderns wird das FormCalc-Skript auf dem Server in JavaScript übersetzt (und zwischengespeichert), sodass es für die Person, die es verwendet oder gestaltet, transparent ist.

Diese Skripting-Engine verwendet einige Funktionen von ECMAScript5 wie „Object.defineProperty“. Die Engine/Bibliothek wird als CQ-Client-Bibliothek mit dem Kategorienamen **xfaforms.profile** bereitgestellt. Sie enthält auch die **FormBridge API** zur Interaktion externer Portale oder Apps mit dem Formular. Mit FormBridge kann eine externe App bestimmte Elemente programmgesteuert ausblenden, deren Werte abrufen oder festlegen oder deren Attribute ändern.

Weitere Informationen finden Sie im Artikel [Form Bridge](/help/forms/integrate-form-bridge-forms-portal.md).

#### Layout-Engine {#layout-engine}

Das Layout und das visuelle Erscheinungsbild von HTML5-Formulare basiert auf Funktionen von SVG 1.1, jQuery, BackBone und CSS3. Das anfängliche Erscheinungsbild eines Formulars wird generiert und auf dem Server zwischengespeichert. Das Ändern dieses anfänglichen Layouts und alle weiteren schrittweisen Änderungen am Formular-Layout werden auf dem Client verwaltet. Um dies zu erreichen, enthält das Laufzeitpaket eine Layout-Engine, die in JavaScript geschrieben ist und auf jQuery/Backbone basiert. Diese Engine verwaltet das gesamte dynamische Verhalten, wie das Hinzufügen/Entfernen wiederholbarer Instanzen und das Layout von Objekten, die vergrößert werden können. Diese Layout-Engine rendert nicht mehr als eine Formularseite gleichzeitig. Benutzende sehen zu Beginn nur eine Seite, und auch die horizontale Bildlaufleiste gilt nur für die erste Seite. Wenn allerdings abwärts gescrollt wird, beginnt das Rendern der nächsten Seite. Durch dieses Seite für Seite erfolgende Rendern wird weniger Zeit benötigt, um die erste Seite in einem Browser zu rendern, und die wahrgenommene Leistung des Formulars erhöht. Diese Engine/Bibliothek ist Teil der CQ-Client-Bibliothek mit dem Kategorienamen **xfaforms.profile**.

Die Layout-Engine enthält auch eine Reihe von Widgets, die verwendet werden, um den Wert von Formularfeldern einer Benutzerin bzw. eines Benutzers zu erfassen. Diese Widgets werden als [jQuery UI-Widgets](https://api.jqueryui.com/jQuery.widget/) modelliert, die bestimmte zusätzliche Kontrakte für einen nahtlose Zusammenarbeit mit der Layout-Engine bereitstellen.

Weitere Informationen über Widgets und die entsprechenden Kontrakte finden Sie unter [Benutzerdefinierte Widgets für HTML5-Formulare](/help/forms/custom-widgets.md).

#### Stile {#styling}

Die den HTML-Elementen zugeordneten Formatierungselemente werden entweder intern oder im eingebetteten CSS-Block hinzugefügt. Einige allgemeine Formatierungselemente, die nicht vom Formular abhängig sind, sind Teil der CQ-Client-Bibliothek mit dem Kategorienamen xfaforms.profile.

Zusätzlich zu den Standardformatierungseigenschaften enthält jedes Formularelement auch bestimmte CSS-Klassen, die auf dem Elementtyp, dem Namen und anderen Eigenschaften basieren. Mithilfe dieser Klassen können Sie Elemente durch Festlegen von deren eigener CSS umformatieren.

Weitere Informationen über Standardformatierung und Klassen finden Sie in der [Einführung zu Stilen](/help/forms/css-styles.md).

#### Server-seitiges Skript und Web-Dienste {#server-side-script-and-web-services}

Skripte, die für eine Ausführung auf dem Server oder für den Aufruf eines Web-Dienstes markiert sind (unabhängig davon, wo dieser Web-Dienst ausgeführt werden soll), werden immer auf dem Server ausgeführt.

Die Client-Scripting Engine:

1. Führt einen synchronen Aufruf an den Server durch und leitet den Status des aktuellen Formulars in Form von JSON an diesen weiter
1. Führt das Skript oder den Web-Dienst auf dem Server aus
1. Erstellt einen neuen JSON-Status
1. Führt den neuen JSON-Status auf dem Client zusammen, wenn die Antwort zurückgegeben wird.

#### Lokalisierungsressourcen-Bundles {#localization-resource-bundles}

HTML5-Formulare unterstützt die Sprachen Italienisch (it), Spanisch (es), Portugiesisch (Brasilien) (pt_BR), Chinesisch (vereinfacht) (zh_CN), Chinesisch (traditionell) (begrenzte Unterstützung) (zh_TW), Koreanisch (ko_KR), Englisch (en_US), Französisch (fr_FR), Deutsch (de_DE) und Japanisch (ja). Nach dem im Anforderungsheader empfangenen Gebietsschema richtet sich, welches Ressourcenbündel an den Client geleitet wird. Dieses Ressourcenbündel wird zur Profil-JSP als CQ-Client-Bibliothek mit dem Kategorienamen **xfaforms.I18N** hinzugefügt. Sie können die Logik überschreiben, dass das Gebietsschema-Paket im Profil aufgenommen wird.

### Sling-Komponenten (adobe-lc-forms-content-pkg.zip) {#sling-components-adobe-lc-forms-content-pkg-zip}

Das Sling-Paket enthält Inhalte zu den Profilen und zum Profil-Renderer.

#### Profile {#profiles}

Profile sind die Ressourcenknoten in Sling, die ein Formular oder eine Familie von Formularen repräsentieren. Auf CQ-Ebene sind diese Profile JCR-Knoten. Die Knoten befinden sich im Ordner **/content** im JCR-Repository und können sich auch in allen Unterordnern des Ordners **/content** befinden.

#### Profil-Renderer {#profile-renderers}

Der Profilknoten hat eine Eigenschaft **Sling: resourceSuperType** mit dem Wert **xfaforms/profile**. Diese Eigenschaft sendet intern Anforderungen an das Sling-Skript für Profilknoten im Ordner **/libs/xfaforms/profile**. Diese Skripte sind JSP-Seiten, die als Container für die Zusammenfügung der HTML-Formulare und der erforderlichen JS/CSS-Artefakte dienen. Die Seiten enthalten Verweise auf:

* **xfaforms.I18N.&lt;locale>**: Diese Bibliothek enthält lokalisierte Daten.
* **xfaforms.profile**: Diese Bibliothek enthält die Implementierung für XFA Scripting und für die Layout-Engine.

Diese Bibliotheken sind als CQ-Client-Bibliotheken modelliert, um Nutzen aus den automatischen Verkettungs-, Minimierungs- und Komprimierungsfunktionen der CQ Framework JavaScript-Bibliotheken zu ziehen.
Weitere Informationen zu CQ-Client-Bibliotheken finden Sie unter [Dokumentation zu CQ Client-Bibliotheken](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de).

Wie oben beschrieben ruft der Profil-Renderer-JSP den Forms-Service über ein Sling-Include auf. Dieses JSP legt auch verschiedene Debugging-Optionen auf Basis der Admin-Konfiguration oder von Anfrageparametern ein.

HTML5-Formulare ermöglicht Entwicklern, Profile und Profil-Renderer zu erstellen, um das Erscheinungsbild der Formulare anzupassen. Beispielsweise können Entwickler HTML-Formulare in ein Bedienfeld oder einen &lt;div>-Abschnitt eines vorhandenen HTML-Portals integrieren.
Weitere Informationen über das Erstellen benutzerdefinierter Profile finden Sie unter [Erstellen eines benutzerfreundlichen Profils](/help/forms/custom-profile.md).
