---
title: Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows
description: Informieren Sie sich über verschiedene Medien-Handler und wie diese in Workflows verwendet werden, um Aufgaben an Assets durchzuführen.
contentOwner: AG
translation-type: ht
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows {#processing-assets-using-media-handlers-and-workflows}

Adobe Experience Manager (AEM) Assets enthält einen Satz von standardmäßigen Workflows und Medien-Handlern zur Bearbeitung von Assets. Der Workflow definiert die allgemeinen Aufgaben, die an Assets durchgeführt werden, und delegiert dann spezielle Aufgaben an die Medien-Handler, z. B. Erstellung von Miniaturbildern oder Extraktion von Metadaten.

Es ist möglich, einen Workflow zu definieren, der automatisch ausgeführt wird, wenn ein Asset eines bestimmten Typs auf den Server hochgeladen wird. Die Prozessschritte sind in Form von AEM Assets-Medien-Handlern definiert. AEM bietet einige [integrierte Handler](#default-media-handlers) und zusätzliche Handler können entweder [speziell entwickelt](#creating-a-new-media-handler) oder definiert werden, indem der Prozess an ein [Befehlszeilen-Tool](#command-line-based-media-handler) delegiert wird.

Medien-Handler sind Dienste innerhalb von AEM Assets, die spezielle Aktionen an Assets durchführen. Wenn beispielsweise eine MP3-Audiodatei in AEM hochgeladen wird, löst ein Workflow einen MP3-Handler aus, der die Metadaten extrahiert und ein Miniaturbild erstellt. Medien-Handler werden normalerweise in Verbindung mit Workflows verwendet. Die meisten gängigen MIME-Typen werden in AEM unterstützt. Spezielle Aufgaben können an Assets durchgeführt werden, indem Workflows erweitert bzw. erstellt, Medien-Handler erweitert bzw. erstellt oder Medien-Handler deaktiviert bzw. aktiviert werden.

>[!NOTE]
>
>Eine Beschreibung aller Formate, die von AEM Assets unterstützt werden, sowie Funktionen, die für jedes Format unterstützt werden, finden Sie im Artikel [Von Assets unterstützte Dateiformate](file-format-support.md).

## Standard-Medien-Handler {#default-media-handlers}

Die folgenden Medien-Handler sind in AEM Assets verfügbar und handhaben die gängigsten MIME-Typen:

<!-- TBD: Apply correct formatting once table is moved to MD.
-->

<table>
 <tbody>
  <tr>
   <td>Handler-Name</td>
   <td>Dienstname (in der Systemkonsole)</td>
   <td>Unterstützte MIME-Typen</td>
  </tr>
  <tr>
   <td>TextHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.TextHandler</p> </td>
   <td>text/plain</td>
  </tr>
  <tr>
   <td>PdfHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pdf.PdfHandler</p> </td>
   <td><p>application/pdf<br /> application/illustrator</p> </td>
  </tr>
  <tr>
   <td>JpegHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.JpegHandler</p> </td>
   <td>image/jpeg</td>
  </tr>
  <tr>
   <td>Mp3Handler</td>
   <td><p>com.day.cq.dam.handler.standard.mp3.Mp3Handler</p> </td>
   <td><p>audio/mpeg</p> </td>
  </tr>
  <tr>
   <td>ZipHandler</td>
   <td><p>com.day.cq.dam.handler.standard.zip.ZipHandler</p> </td>
   <td><p>application/java-archive</p> <p>application/zip</p> </td>
  </tr>
  <tr>
   <td>PictHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pict.PictHandler</p> </td>
   <td><p>image/pict</p> </td>
  </tr>
  <tr>
   <td>StandardImageHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.StandardImageHandler</p> </td>
   <td><p>image/gif</p> <p>image/png</p> <p>application/photoshop</p> <p>image/jpeg</p> <p>image/tiff</p> <p>image/x-ms-bmp</p> <p>image/bmp</p> </td>
  </tr>
  <tr>
   <td>MSOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler</td>
   <td>application/msword<br /> </td>
  </tr>
  <tr>
   <td>MSPowerPointHandler</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler</td>
   <td>application/vnd.ms-powerpoint<br /> </td>
  </tr>
  <tr>
   <td>OpenOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler</td>
   <td>application/vnd.openxmlformats-officedocument.wordprocessingml.document<br /> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet<br /> application/vnd.openxmlformats-officedocument.presentationml.presentation<br /> <br /> </td>
  </tr>
  <tr>
   <td>EPubHandler</td>
   <td>com.day.cq.dam.handler.standard.epub.EPubHandler</td>
   <td>application/epub+zip</td>
  </tr>
  <tr>
   <td>GenericAssetHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.GenericAssetHandler</p> </td>
   <td>Ausweichmöglichkeit, falls kein anderer Handler gefunden wurde, der Daten aus einem Asset extrahiert</td>
  </tr>
 </tbody>
</table>

Alle Handler führen folgende Aufgaben aus:

* Extraktion aller verfügbaren Metadaten aus einem Asset.
* Erstellung eines Miniaturbilds aus einem Asset.

Es ist möglich, die aktiven Medien-Handler anzuzeigen:

1. Navigieren Sie im Browser zu `http://localhost:4502/system/console/components`.
1. Klicken Sie auf den Link `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Eine Liste mit allen aktiven Medien-Handlern wird angezeigt.

## Verwenden der Medien-Handler in Workflows, um Aufgaben zur Bearbeitung von Assets durchzuführen {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Medien-Handler sind Dienste, die normalerweise in Verbindung mit Workflows verwendet werden.

AEM bietet verschiedene Standard-Workflows zur Bearbeitung von Assets. Um sie anzuzeigen, öffnen Sie die Workflow-Konsole und klicken Sie auf die Registerkarte **[!UICONTROL Modelle]**: Die Workflow-Namen, die mit AEM Assets beginnen, sind Asset-spezifische Workflows.

Bereits bestehende Workflows können erweitert und neue Workflows können erstellt werden, um Assets nach spezifischen Anforderungen zu bearbeiten.

Das folgende Beispiel zeigt, wie der **[!UICONTROL AEM Assets-Synchronisierungs-Workflow]** erweitert werden kann, damit Teil-Assets für alle Assets außer PDF-Dokumente erstellt werden.

### Deaktivieren/Aktivieren eines Medien-Handlers {#disabling-enabling-a-media-handler}

Die Medien-Handler können über die Apache Felix Web Management-Konsole deaktiviert bzw. aktiviert werden. Wenn der Medien-Handler deaktiviert ist, werden seine Aufgaben zur Bearbeitung von Assets nicht durchgeführt.

So aktivieren/deaktivieren Sie einen Medien-Handler:

1. Navigieren Sie im Browser zu `https://<host>:<port>/system/console/components`.
1. Klicken Sie neben dem Namen des Medien-Handlers auf **[!UICONTROL Deaktivieren]**. Beispiel: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Aktualisieren Sie die Seite: Neben dem Medien-Handler wird ein Symbol angezeigt, das angibt, dass er deaktiviert ist.
1. Um den Medien-Handler zu aktivieren, klicken Sie neben dem Namen des Medien-Handlers auf **[!UICONTROL Aktivieren]**.

### Erstellen eines neuen Medien-Handlers {#creating-a-new-media-handler}

Um einen neuen Medientyp zu unterstützen oder eine bestimmte Aufgabe an einem Asset durchzuführen, muss ein neuer Medien-Handler erstellt werden. In diesem Abschnitt wird beschrieben, wie Sie vorgehen.

#### Wichtige Klassen und Schnittstellen     {#important-classes-and-interfaces}

Am besten ist es, zu Beginn einer Implementierung den Inhalt einer bereitgestellten abstrakten Implementierung zu übernehmen, wodurch die meisten Dinge im Voraus erledigt werden und ein angemessenes Standardverhalten erreicht wird: die `com.day.cq.dam.core.AbstractAssetHandler`-Klasse.

Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. Wenn Sie also den Inhalt dieser Klasse übernehmen und das maven-sling-Plug-in verwenden, müssen Sie die Übernahmemarkierung auf `true` setzen.

Implementieren Sie die folgenden Methoden:

* `extractMetadata()`: extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: erstellt ein Miniaturbild aus einem Asset.
* `getMimeTypes()`: gibt die Asset-MIME-Typen zurück.

Hier eine Beispielvorlage:

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler`-Schnittstelle: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte MIME-Typen hinzufügt. Wenn ein neuer MIME-Typ hinzugefügt werden soll, muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler`-Klasse: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-Klasse:
   * Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie übliche Funktionen für die Extrahierung von Teil-Assets.
   * Am besten ist es, zu Beginn einer Implementierung den Inhalt einer bereitgestellten abstrakten Implementierung zu übernehmen, wodurch die meisten Dinge im Voraus erledigt werden und ein angemessenes Standardverhalten erreicht wird: die com.day.cq.dam.core.AbstractAssetHandler-Klasse.
   * Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. Wenn Sie also den Inhalt dieser Klasse übernehmen und das maven-sling-Plug-in verwenden, müssen Sie das Übernahme-Flag auf true setzen.

Die folgenden Methoden müssen implementiert werden:

* `extractMetadata()`: Diese Methode extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: Diese Methode erstellt ein Miniaturbild aus dem übergebenen Asset.
* `getMimeTypes()`: Diese Methode gibt den/die Asset-MIME-Typ(en) zurück.

Hier eine Beispielvorlage:

package my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot; &amp;ast; @scr.service &amp;ast;/ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // die relevanten Teile implementieren }

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler`-Schnittstelle: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte MIME-Typen hinzufügt. Wenn ein neuer MIME-Typ hinzugefügt werden soll, muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler`-Klasse: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-Klasse: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie übliche Funktionen für die Extrahierung von Teil-Assets.

<!--
#### Example: create a specific Text Handler {#example-create-a-specific-text-handler}

In this section, you will create a specific Text Handler that generates thumbnails with a watermark.

Proceed as follows:

Refer to [Development Tools](../sites-developing/dev-tools.md) to install and set up Eclipse with a Maven plugin and for setting up the dependencies that are needed for the Maven project.

After you perform the following procedure, when you upload a txt file into AEM, the file's metadata are extracted and two thumbnails with a watermark are generated.

1. In Eclipse, create `myBundle` Maven project:

    1. In the Menu bar, click **[!UICONTROL File > New > Other]**.
    1. In the dialog, expand the Maven folder, select Maven Project and click **[!UICONTROL Next]**.
    1. Check the Create a simple project box and the Use default Workspace locations box, then click **[!UICONTROL Next]**.
    1. Define the Maven project:

        * Group Id: com.day.cq5.myhandler
        * Artifact Id: myBundle
        * Name: My AEM bundle
        * Description: This is my AEM bundle

    1. Click **[!UICONTROL Finish]**.

1. Set the Java Compiler to version 1.5:

    1. Right-click the `myBundle` project, select Properties.
    1. Select Java Compiler and set following properties to 1.5:

        * Compiler compliance level
        * Generated .class files compatibility
        * Source compatibility

    1. Click **[!UICONTROL OK]**. In the dialog window, click Yes.

1. Replace the code in the pom.xml file with the following code:

1. Create the package `com.day.cq5.myhandler` that contains the Java classes under `myBundle/src/main/java`:

    1. Under myBundle, right-click `src/main/java`, select New, then Package.
    1. Name it `com.day.cq5.myhandler` and click Finish.

1. Create the Java class `MyHandler`:

    1. In Eclipse, under `myBundle/src/main/java`, right-click the `com.day.cq5.myhandler` package, select New, then Class.
    1. In the dialog window, name the Java Class MyHandler and click Finish. Eclipse creates and opens the file MyHandler.java.
    1. In `MyHandler.java` replace the existing code with the following and then save the changes:

   ```java
   package com.day.cq5.myhandler;
   import java.awt.Color;
   import java.awt.Rectangle;
   import java.awt.image.BufferedImage;
   import java.io.IOException;
   import java.io.InputStream;
   import java.io.InputStreamReader;
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   import org.apache.commons.io.IOUtils;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   import com.day.cq.dam.api.metadata.ExtractedMetadata;
   import com.day.cq.dam.core.AbstractAssetHandler;
   import com.day.image.Font;
   import com.day.image.Layer;
   import com.day.cq.wcm.foundation.ImageHelper;

   /**
    * The <code>MyHandler</code> can extract text files
    * @scr.component inherit="true" immediate="true" metatype="false"
    * @scr.service
    *
    **/

   public class MyHandler extends AbstractAssetHandler {
    /** * Logger instance for this class. */
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class);
    /** * Music icon margin */
    private static final int MARGIN = 10;
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */
    public String[] getMimeTypes() {
     return new String[] {"text/plain"};
    }

    public ExtractedMetadata extractMetadata(Node asset) {
     ExtractedMetadata extractedMetadata = new ExtractedMetadata();
     InputStream data = getInputStream(asset);
     try {
      // read text data
      InputStreamReader reader = new InputStreamReader(data);
      char[] buffer = new char[4096];
      String text = "";
      while (reader.read(buffer) != -1) {
       text += new String(buffer);
      }
      reader.close();
      long wordCount = this.wordCount(text);
      extractedMetadata.setProperty("text", text);
      extractedMetadata.setMetaDataProperty("Word Count",wordCount);
      setMimetype(extractedMetadata, asset);
     } catch (Throwable t) {
      log.error("handling error: " + t.toString(), t);
     } finally {
      IOUtils.closeQuietly(data);
     }
     return extractedMetadata; }
    // ----------------------< helpers >----------------------------------------
    protected BufferedImage getThumbnailImage(Node node) {
     ExtractedMetadata metadata = extractMetadata(node);
     final String text = (String) metadata.getProperty("text");
     // create text layer
     final Layer layer = new Layer(500, 600, Color.WHITE);
     layer.setPaint(Color.black);
     Font font = new Font("Arial", 12);
     String displayText = this.getDisplayText(text, 600, 12);
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0);
     }
     // create watermark and merge with text layer
     Layer watermarkLayer;
     try {
      final Session session = node.getSession();
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png");
      watermarkLayer.setX(MARGIN);
      watermarkLayer.setY(MARGIN);
      layer.merge(watermarkLayer);
     } catch (RepositoryException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
     } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace(); }
     layer.crop(new Rectangle(510, 600));
     return layer.getImage(); }
    // ---------------< private >-----------------------------------------------
    /**
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px)
     * * @return the text which will fit into the box
     */
    private String getDisplayText(String text, int height, int fontheight) {
     String trimmedText = text.trim();
     int numOfLines = height / fontheight;
     String lines[] = trimmedText.split("\n");
     if (lines.length <= numOfLines) {
      return trimmedText;
     } else {
      String cuttetText = "";
      for (int i = 0; i < numOfLines; i++) {
       cuttetText += lines[i] + "\n";
      }
      return cuttetText;
     }
    }
    /**
     * * This method counts the number of words in a string
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */
    private long wordCount(String text) {
     // We need to keep track of the last character, if we have two white spaces in a row we dont want to double count
     // The starting of the document is always a whitespace
     boolean prevWhiteSpace = true;
     boolean currentWhiteSpace = true;
     char c; long numwords = 0;
     int j = text.length();
     int i = 0;
     while (i < j) {
      c = text.charAt(i++);
      if (c == 0) { break; }
      currentWhiteSpace = Character.isWhitespace(c);
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; }
      prevWhiteSpace = currentWhiteSpace;
     }
     // If we do not end with a white space then we need to add one extra word
     if (!currentWhiteSpace) { numwords++; }
     return numwords;
    }
   }
   ```

1. Compile the Java class and create the bundle:

    1. Right-click the myBundle project, select **[!UICONTROL Run As]**, then **[!UICONTROL Maven Install]**.
    1. The bundle `myBundle-0.0.1-SNAPSHOT.jar` (containing the compiled class) is created under `myBundle/target`.

1. In CRX Explorer, create a new node under `/apps/myApp`. Name = `install`, Type = `nt:folder`.
1. Copy the bundle `myBundle-0.0.1-SNAPSHOT.jar` and store it under `/apps/myApp/install` (for example with WebDAV). The new text handler is now active in AEM.
1. In your browser, open the Apache Felix Web Management Console. Select the Components tab and disable the default text handler `com.day.cq.dam.core.impl.handler.TextHandler`.

-->

## Befehlszeilenbasierter Medien-Handler {#command-line-based-media-handler}

Mit AEM können Sie ein beliebiges Befehlszeilen-Tool (z. B. ImageMagick) innerhalb eines Workflows ausführen, um Assets zu konvertieren und dem Asset das neue Ausgabeformat hinzuzufügen. Sie müssen das Befehlszeilen-Tool auf dem Datenträger installieren, der den AEM-Server hostet, und dem Workflow einen Prozessschritt hinzufügen. Der aufgerufene Prozess `CommandLineProcess` ermöglicht zudem die Filterung nach spezifischen MIME-Typen und die Erstellung mehrerer Miniaturbilder auf der Grundlage des neuen Ausgabeformats.

Die folgenden Konvertierungen können automatisch ausgeführt und in AEM Assets gespeichert werden:

* EPS- und AI-Umwandlung mithilfe von [ImageMagick](https://www.imagemagick.org/script/index.php) und [Ghostscript](https://www.ghostscript.com/)
* FLV-Videotranskodierung mithilfe von [FFmpeg](https://ffmpeg.org/)
* MP3-Kodierung mithilfe von [LAME](http://lame.sourceforge.net/)
* Verarbeitung von Audiodaten mithilfe von [SOX](http://sox.sourceforge.net/)

>[!NOTE]
>
>Auf Nicht-Windows-Systemen gibt das FFMpeg-Tool einen Fehler aus, wenn Ausgabeformate für ein Video-Asset erstellt werden, dessen Dateiname ein einfaches Anführungszeichen (&#39;) enthält. Wenn der Name Ihrer Videodatei ein einfaches Anführungszeichen enthält, entfernen Sie es, bevor Sie das Asset auf AEM hochladen.

Der Prozess `CommandLineProcess` führt folgende Vorgänge in der angegebenen Reihenfolge aus:

* Filtert die Datei nach bestimmten MIME-Typen, falls angegeben.
* Erstellt ein temporäres Verzeichnis auf dem Datenträger, der den AEM-Server hostet.
* Streamt die Originaldatei in das temporäre Verzeichnis.
* Führt den Befehl aus, der über die Argumente des Schritts definiert ist. Der Befehl wird innerhalb des temporären Verzeichnisses ausgeführt, nachdem die Genehmigung des Benutzers eingeholt wurde, der AEM ausführt.
* Streamt das Ergebnis zurück in den Ausgabeordner des AEM-Servers.
* Löscht das temporäre Verzeichnis.
* Erstellt Miniaturbilder auf der Grundlage dieser Ausgabeformate, falls angegeben. Die Anzahl und die Abmessungen von Miniaturbildern werden durch die Argumente des Schritts definiert.

### Ein Beispiel mit ImageMagick     {#an-example-using-imagemagick}

Das folgende Beispiel zeigt, wie Sie den Befehlszeilenprozessschritt so einrichten, dass jedes Mal, wenn ein Asset mit dem MIME-Typ GIF oder TIFF zu /content/dam auf dem AEM-Server hinzugefügt wird, ein gespiegeltes Bild des Originals zusammen mit drei zusätzlichen Miniaturbildern (140x100, 48x48 und 10x250) erstellt wird.

Zu diesem Zweck verwenden Sie ImageMagick. ImageMagick ist eine kostenlose Software zum Erstellen, Bearbeiten und Zusammenstellen von Bitmapbildern und wird in der Regel über die Befehlszeile ausgeführt.

Installieren Sie ImageMagick zunächst auf dem Datenträger, der den AEM-Server hostet:

1. Installieren Sie ImageMagick: Siehe [ImageMagick-Dokumentation](https://www.imagemagick.org/script/download.php).
1. Richten Sie das Tool ein, damit Sie den Befehl „convert“ über die Befehlszeile ausführen können.
1. Um festzustellen, ob das Tool ordnungsgemäß installiert wurde, führen Sie den Befehl `convert -h` über die Befehlszeile aus.

   Es wird ein Hilfebildschirm mit allen möglichen Optionen des Konvertierungs-Tools angezeigt.

   >[!NOTE]
   >
   >In manchen Versionen von Windows (z. B. Windows SE) kann der Konvertierungsbefehl eventuell nicht ausgeführt werden, da er in Konflikt mit dem nativen Konvertierungsdienstprogramm steht, das Teil der Windows-Installation ist. In diesem Fall verwenden Sie den vollständigen Pfad für das ImageMagick-Dienstprogramm, das verwendet wird, um Bilddateien in Miniaturbilder zu konvertieren. Beispiel: `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Um zu überprüfen, ob das Tool ordnungsgemäß ausgeführt wird, fügen Sie ein .jpg-Bild in das Arbeitsverzeichnis ein und führen Sie dann den Konvertierungsbefehl `<image-name>.jpg -flip <image-name>-flipped.jpg` über die Befehlszeile aus.

   Ein gespiegeltes Bild wird dem Verzeichnis hinzugefügt.

Fügen Sie dann den Befehlszeilenprozessschritt dem Workflow **[!UICONTROL DAM-Update-Asset]** hinzu:

1. Rufen Sie die Konsole **[!UICONTROL Workflow]** auf.
1. Bearbeiten Sie auf der Registerkarte **[!UICONTROL Modelle]** das Modell **[!UICONTROL DAM-Update-Asset]**.
1. Ändern Sie die Einstellungen des Schritts **[!UICONTROL Web-aktivierte Ausgabe]** wie folgt:

   **Argumente**:

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. Speichern Sie den Workflow.

Fügen Sie zum Testen des geänderten Workflows ein Asset zu `/content/dam` hinzu.

1. Rufen Sie im Dateisystem ein TIFF-Bild Ihrer Wahl ab. Benennen Sie es in `myImage.tiff` um und kopieren Sie es in `/content/dam`, z. B. mithilfe von WebDAV.
1. Rufen Sie die Konsole **[!UICONTROL CQ5 DAM]** auf, z. B. `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Öffnen Sie das Asset **[!UICONTROL myImage.tiff]** und prüfen Sie, ob das gespiegelte Bilder und die drei Miniaturbilder erstellt wurden.

#### Konfiguration des Prozessschritts CommandLineProcess {#configuring-the-commandlineprocess-process-step}

In diesem Abschnitt wird beschrieben, wie die **Prozess-Argumente** des **CommandLineProcess** festgelegt werden.

Die Werte der **Prozess-Argumente** müssen durch Kommas getrennt werden und dürfen nicht mit einem Leerzeichen beginnen.

<table>
 <tbody>
  <tr>
   <td> Argument-Format</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td> mime:&lt;MIME-Typ&gt;</td>
   <td><p>Optionales Argument. Der Prozess wird angewendet, wenn das Asset denselben MIME-Typ wie das Argument hat.</p> <p>Es können mehrere MIME-Typen definiert werden.</p> </td>
  </tr>
  <tr>
   <td> tn:&lt;Breite&gt;:&lt;Höhe&gt;</td>
   <td><p>Optionales Argument. Der Prozess erstellt ein Miniaturbild mit den Abmessungen, die im Argument definiert sind.</p> <p>Es können mehrere Miniaturbilder definiert werden.<br /> </p> </td>
  </tr>
  <tr>
   <td> cmd: &lt;Befehl&gt;</td>
   <td><p>Definiert den auszuführenden Befehl. Die Syntax hängt vom Befehlszeilen-Tool ab.</p> <p>Nur ein Befehl kann definiert werden.</p> <p>Die folgenden Variablen können zum Erstellen des Befehls verwendet werden:<br/></p> <p><code>${filename}</code>: Name der Eingabedatei, z. B. „original.jpg“<br/><code>${file}</code>: der vollständige Pfadname der Eingabedatei, z. B. „/tmp/cqdam0816.tmp/original.jpg“<br/><code>${directory}</code>: Verzeichnis der Eingabedatei, z. B. „/tmp/cqdam0816.tmp“.<br/> <code>${basename}</code>: Name der Eingabedatei ohne Erweiterung, z. B. original<br/><code>${extension}</code>: Erweiterung der Eingabedatei, z. B. JPG.<br/></p></td>
  </tr>
 </tbody>
</table>

Wenn beispielsweise ImageMagick auf dem Datenträger installiert ist, der den AEM-Server hostet, und Sie einen Prozessschritt mithilfe von **CommandLineProcess** als Implementierung erstellen und die folgenden Werte als **Prozess-Argumente** verwenden:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

dann gilt der Schritt bei der Ausführung des Workflows nur für Assets, die image/gif oder mime:image/tiff als MIME-Typ haben. Der Schritt erstellt ein gespiegeltes Bild des Originals, wandelt es in eine JPG-Datei um und erstellt drei Miniaturbilder mit den Abmessungen 140x100, 48x48 und 10x250.

Verwenden Sie die folgenden **Prozess-Argumente**, um die drei Standard-Miniaturbilder mithilfe von ImageMagick zu erstellen:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Verwenden Sie die folgenden **Prozess-Argumente**, um die Web-fähige Ausgabe mithilfe von ImageMagick zu erstellen:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>Der Schritt **CommandLineProcess** gilt nur für Assets (Knoten des Typs `dam:Asset`) oder untergeordnete Elemente eines Assets.
