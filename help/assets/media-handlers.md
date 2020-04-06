---
title: Verarbeiten von Assets mit Media Handlers und Workflows
description: Informieren Sie sich über verschiedene Medien-Handler und wie diese in Workflows verwendet werden, um Aufgaben an Assets durchzuführen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Process assets Using Media Handlers and Workflows {#processing-assets-using-media-handlers-and-workflows}

Adobe Experience Manager (AEM) Assets verfügen über eine Reihe von Standard-Workflows und Media-Handlern zur Verarbeitung von Assets. Der Workflow definiert die allgemeinen Aufgaben, die an Assets durchgeführt werden, und delegiert dann spezielle Aufgaben an die Medien-Handler, z. B. Erstellung von Miniaturbildern oder Extraktion von Metadaten.

Es ist möglich, einen Workflow zu definieren, der automatisch ausgeführt wird, wenn ein Asset eines bestimmten Typs auf den Server hochgeladen wird. Die Verarbeitungsschritte werden als eine Reihe von AEM Assets Media Handlers definiert. AEM provides some [built in handlers,](#default-media-handlers) and additional ones can be either [custom developed](#creating-a-new-media-handler) or defined by delegating the process to a [command line tool](#command-line-based-media-handler).

Media Handler sind Dienste innerhalb von AEM Assets, die bestimmte Aktionen für Assets ausführen. Wenn beispielsweise eine MP3-Audiodatei in AEM hochgeladen wird, löst ein Workflow einen MP3-Handler aus, der die Metadaten extrahiert und ein Miniaturbild erstellt. Medien-Handler werden normalerweise in Verbindung mit Workflows verwendet. Die meisten gängigen MIME-Typen werden in AEM unterstützt. Spezielle Aufgaben können an Assets durchgeführt werden, indem Workflows erweitert bzw. erstellt, Medien-Handler erweitert bzw. erstellt oder Medien-Handler deaktiviert bzw. aktiviert werden.

>[!NOTE]
>
>Please refer to the [Assets supported formats](file-format-support.md) page for a description of all the formats supported by AEM Assets as well as features supported for each format.

## Standard-Medien-Handler {#default-media-handlers}

Die folgenden Media-Handler stehen in AEM Assets zur Verfügung und behandeln die am häufigsten verwendeten MIME-Typen:

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
   <td>application/vnd.openxmlformats-officedocument.wordprocessingml.Dokument<br /> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet<br /> application/vnd.openxmlformats-officedocument.presentationml.present<br /><br /> </td>
  </tr>
  <tr>
   <td>EPubHandler</td>
   <td>com.day.cq.dam.handler.standard.epub.EPubHandler</td>
   <td>application/epub/zip</td>
  </tr>
  <tr>
   <td>GenericAssetHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.GenericAssetHandler</p> </td>
   <td>Ausweichmöglichkeit, falls kein anderer Handler gefunden wurde, um Daten aus einem Asset zu extrahieren</td>
  </tr>
 </tbody>
</table>

Alle Handler führen folgende Aufgaben aus:

* Extraktion aller verfügbaren Metadaten aus einem Asset.
* Erstellung eines Miniaturbilds aus einem Asset.

Es ist möglich, die aktiven Medien-Handler anzuzeigen:

1. In your browser, navigate to `http://localhost:4502/system/console/components`.
1. Click the link `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Eine Liste mit allen aktiven Medien-Handlern wird angezeigt.

## Verwenden der Medien-Handler in Workflows, um Aufgaben zur Bearbeitung von Assets durchzuführen {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Medien-Handler sind Dienste, die normalerweise in Verbindung mit Workflows verwendet werden.

AEM bietet verschiedene Standard-Workflows zur Bearbeitung von Assets. To view them, open the Workflow console and click the **[!UICONTROL Models]** tab: the workflow titles that start with AEM Assets are the assets specific ones.

Bereits bestehende Workflows können erweitert und neue Workflows können erstellt werden, um Assets nach spezifischen Anforderungen zu bearbeiten.

Das folgende Beispiel zeigt, wie der Workflow für die **[!UICONTROL AEM Assets-Synchronisierung]** verbessert werden kann, sodass Teil-Assets für alle Assets außer PDF-Dokumente generiert werden.

### Deaktivieren/Aktivieren eines Medien-Handlers {#disabling-enabling-a-media-handler}

Die Medien-Handler können über die Apache Felix Web Management-Konsole deaktiviert bzw. aktiviert werden. Wenn der Medien-Handler deaktiviert ist, werden seine Aufgaben zur Bearbeitung von Assets nicht durchgeführt.

So aktivieren/deaktivieren Sie einen Medien-Handler:

1. In your browser, navigate to `https://<host>:<port>/system/console/components`.
1. Klicken Sie neben dem Namen des Medienhandlers auf **[!UICONTROL Deaktivieren]** . Beispiel: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Seite aktualisieren: Neben dem Medienhandler wird ein Symbol angezeigt, das angibt, dass er deaktiviert ist.
1. To enable the media handler, click **[!UICONTROL Enable]** next to the name of the media handler.

### Erstellen eines neuen Medien-Handlers {#creating-a-new-media-handler}

Um einen neuen Medientyp zu unterstützen oder eine bestimmte Aufgabe an einem Asset durchzuführen, muss ein neuer Medien-Handler erstellt werden. In diesem Abschnitt wird beschrieben, wie Sie vorgehen.

#### Wichtige Klassen und Schnittstellen {#important-classes-and-interfaces}

The best way to start an implementation is to inherit from a provided abstract implementation that takes care of most things and provides reasonable default behavior: the `com.day.cq.dam.core.AbstractAssetHandler` class.

Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. So if you inherit from this class and use the maven-sling-plugin, make sure that you set the inherit flag to `true`.

Implementieren Sie die folgenden Methoden:

* `extractMetadata()`: extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: erstellt aus dem übergebenen Asset ein Miniaturbild.
* `getMimeTypes()`: gibt die Asset-MIME-Typen zurück.

Hier eine Beispielvorlage:

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte MIME-Typen hinzufügt. Zum Hinzufügen eines neuen MIME-Typs muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler` class: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-Klasse:
   * Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie häufig verwendete Funktionen für die Extraktion von Teil-Assets.
   * Am besten ist es, zu Beginn einer Implementierung den Inhalt einer bereitgestellten abstrakten Implementierung zu übernehmen, wodurch die meisten Dinge im Voraus erledigt werden und ein angemessenes Standardverhalten erreicht wird: die com.day.cq.dam.core.AbstractAssetHandler-Klasse.
   * Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. Wenn Sie also den Inhalt dieser Klasse übernehmen und das maven-sling-Plug-in verwenden, müssen Sie das Übernahme-Flag auf true setzen.

Die folgenden Methoden müssen implementiert werden:

* `extractMetadata()`: Diese Methode extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: Diese Methode erstellt ein Miniaturbild aus dem übergebenen Asset.
* `getMimeTypes()`: Diese Methode gibt den bzw. die Asset-MIME-Typen zurück.

Hier eine Beispielvorlage:

package my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot; &amp;ast; @scr.service &amp;ast;/ public class MyMediaHandler extension com.day.cq.dam.core.AbstractAssetHandler { // implementieren Sie die entsprechenden Teile }

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte MIME-Typen hinzufügt. Zum Hinzufügen eines neuen MIME-Typs muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler` class: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler` class: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie häufig verwendete Funktionen für die Extraktion von Teilassets.

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

Mit AEM können Sie jedes Befehlszeilenwerkzeug innerhalb eines Workflows ausführen, um Assets (z. B. ImageMagick) zu konvertieren und die neue Darstellung dem Asset hinzuzufügen. Sie müssen das Befehlszeilentool auf dem Datenträger installieren, der den AEM-Server hostet, und dem Workflow einen Prozessschritt hinzufügen. The invoked process, called `CommandLineProcess`, also enables to filter according to specific MIME types and to create multiple thumbnails based on the new rendition.

Die folgenden Konvertierungen können automatisch ausgeführt und in AEM Assets gespeichert werden:

* EPS- und AI-Umwandlung mithilfe von [ImageMagick](https://www.imagemagick.org/script/index.php) und [Ghostscript](https://www.ghostscript.com/) 
* FLV-Videotranskodierung mithilfe von [FFmpeg](https://ffmpeg.org/)
* MP3-Kodierung mithilfe von [LAME](http://lame.sourceforge.net/)
* Verarbeitung von Audiodaten mithilfe von [SOX](http://sox.sourceforge.net/) 

>[!NOTE]
>
>Bei Nicht-Windows-Systemen gibt das FFMpeg-Tool einen Fehler zurück, wenn Darstellungen für ein Video-Asset generiert werden, das ein einzelnes Anführungszeichen (&#39;) im Dateinamen enthält. Wenn der Name Ihrer Videodatei ein einfaches Anführungszeichen enthält, entfernen Sie es, bevor Sie das Asset auf AEM hochladen.

The `CommandLineProcess` process performs the following operations in the order they are listed:

* Filter der Datei nach bestimmten MIME-Typen, falls angegeben.
* Erstellt ein temporäres Verzeichnis auf dem Datenträger, der den AEM-Server hostet. 
* Streamt die Originaldatei in den temporären Ordner.
* Führt den Befehl aus, der über die Argumente des Schritts definiert ist. Der Befehl wird im temporären Ordner mit den Berechtigungen des Benutzers ausgeführt, der AEM ausführt.
* Streamt das Ergebnis zurück in den Ausgabeordner des AEM-Servers.
* Löscht den temporären Ordner.
* Erstellt Miniaturbilder auf der Grundlage dieser Ausgabeformate, falls angegeben. Die Anzahl und die Abmessungen von Miniaturbildern werden durch die Argumente des Schritts definiert.

### Ein Beispiel mit ImageMagick {#an-example-using-imagemagick}

Das folgende Beispiel zeigt, wie Sie den Befehlszeilenprozessschritt so einrichten, dass jedes Mal, wenn ein Asset mit dem MIME-Typ GIF oder TIFF zu /content/dam auf dem AEM-Server hinzugefügt wird, ein gespiegeltes Bild des Originals zusammen mit drei zusätzlichen Miniaturbildern (140x100, 48x48 und 10x250) erstellt wird.

Dazu verwenden Sie ImageMagick. ImageMagick ist eine kostenlose Software zum Erstellen, Bearbeiten und Zusammenstellen von Bitmapbildern und wird in der Regel über die Befehlszeile ausgeführt.

Installieren Sie ImageMagick zunächst auf dem Datenträger, der den AEM-Server hostet:

1. Install ImageMagick: please refer to the [ImageMagick documentation](https://www.imagemagick.org/script/download.php).
1. Richten Sie das Tool so ein, dass Sie die Konvertierung über die Befehlszeile ausführen können.
1. To see if the tool is installed properly, run the following command `convert -h` on the command line.

   Es wird ein Hilfebildschirm mit allen möglichen Optionen des Konvertierungstools angezeigt.

   >[!NOTE]
   >
   >In manchen Versionen von Windows (z. B. Windows SE), kann der Konvertierungsbefehl eventuell nicht ausgeführt werden, da er in Konflikt mit dem nativen Konvertierungsdienstprogramm steht, das Teil der Windows-Installation ist. In diesem Fall verwenden Sie den vollständigen Pfad für das ImageMagick-Dienstprogramm, das verwendet wird, um Bilddateien in Miniaturbilder zu konvertieren. Beispiel: `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`. 

1. To see if the tool runs properly, add a .jpg image to the working directory and run the command convert `<image-name>.jpg -flip <image-name>-flipped.jpg` on the command line.

   Ein gespiegeltes Bild wird dem Verzeichnis hinzugefügt.

Fügen Sie dem Workflow für **[!UICONTROL DAM Update Asset]** dann den Befehlszeilen-Prozessschritt hinzu:

1. Go to the **[!UICONTROL Workflow]** console.
1. In the **[!UICONTROL Models]** tab, edit the **[!UICONTROL DAM Update Asset]** model.
1. Change the settings of the **[!UICONTROL Web enabled rendition]** step as follows:

   **Argumente**:

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. Speichern Sie den Workflow.

Fügen Sie zum Testen des geänderten Workflows ein Asset zu `/content/dam`hinzu.

1. Rufen Sie im Dateisystem ein TIFF-Bild Ihrer Wahl ab. Rename it to `myImage.tiff` and copy it to `/content/dam`, for example by using WebDAV.
1. Go to the **[!UICONTROL CQ5 DAM]** console, for example `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Open the asset **[!UICONTROL myImage.tiff]** and verify that the flipped image and the three thumbnails have been created.

#### Konfiguration des Prozessschritts CommandLineProcess {#configuring-the-commandlineprocess-process-step}

In diesem Abschnitt wird beschrieben, wie Sie die **Prozessargumente** von **CommandLineProcess** festlegen.

The values of the **Process Arguments** must be separated by a comma and must not start with a whitespace.

<table>
 <tbody>
  <tr>
   <td> Argument-Format</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td> mime:&lt;mime-type&gt;</td>
   <td><p>Optionales Argument. Der Prozess wird angewendet, wenn der Asset denselben MIME-Typ wie der des Arguments hat.</p> <p>Es können mehrere Mime-Typen definiert werden.</p> </td>
  </tr>
  <tr>
   <td> tn:&lt;width&gt;:&lt;height&gt;</td>
   <td><p>Optionales Argument. Der Prozess erstellt ein Miniaturbild mit den Abmessungen, die im Argument definiert sind.</p> <p>Several thumbnails can be defined.<br /> </p> </td>
  </tr>
  <tr>
   <td> cmd: &lt;command&gt;</td>
   <td><p>Definiert den auszuführenden Befehl. Die Syntax hängt vom Befehlszeilentool ab.</p> <p>Es kann nur ein Befehl definiert werden.</p> <p>Die folgenden Variablen können zum Erstellen des Befehls verwendet werden:<br/></p> <p><code>${filename}</code>: Name der Eingabedatei, z. B. "original.jpg"<br/><code>${file}</code>: vollständiger Pfadname der Eingabedatei, z. B. "/tmp/cqdam0816.tmp/original.jpg"<br/><code>${directory}</code>: Verzeichnis der Eingabedatei, z. B. "/tmp/cqdam0816.tmp".<br/> <code>${basename}</code>: Name der Eingabedatei ohne Erweiterung, z. B. Original<br/><code>${extension}</code>: Erweiterung der Eingabedatei, z. B. JPG<br/></p></td>
  </tr>
 </tbody>
</table>

Wenn beispielsweise ImageMagick auf dem Datenträger installiert ist, der den AEM-Server hostet, und Sie einen Prozessschritt mithilfe von **CommandLineProcess** als Implementierung erstellen und die folgenden Werte als **Prozess-Argumente** verwenden:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

dann gilt der Schritt bei der Ausführung des Workflows nur für Assets, die image/gif oder mime:image/tiff als MIME-Typ haben. Der Schritt erstellt ein gespiegeltes Bild des Originals, wandelt es in eine JPG-Datei um und erstellt drei Miniaturbilder mit den Abmessungen 140x100, 48x48 und 10x250.

Use the following **Process Arguments** to create the three standard thumbnails using ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Use the following **Process Arguments** to create the web-enabled rendition using ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>The **CommandLineProcess** step only applies to Assets (nodes of type `dam:Asset`) or descendants of an Asset.
