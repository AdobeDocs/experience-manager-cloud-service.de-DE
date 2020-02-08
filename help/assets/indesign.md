---
title: Integrieren von AEM Assets mit InDesign Server
description: Erfahren Sie mehr über die Integration von AEM Assets mit InDesign Server.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Integrieren von AEM Assets mit InDesign Server {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager (AEM) Assets nutzt:

* Einen Proxy für den Lastenausgleich bei der Verarbeitung bestimmter Aufgaben. Ein Proxy ist eine AEM-Instanz, die mit einem Proxy Worker kommuniziert, um eine bestimmte Aufgabe zu erfüllen, sowie mit anderen AEM-Instanzen, um das Ergebnis bereitzustellen.
* Einen Proxy Worker zum Definieren und Verwalten einer bestimmten Aufgabe.
Diese Aufgaben können unterschiedlichster Art sein, beispielsweise die Nutzung von InDesign Server zur Verarbeitung von Dateien.

Um Dateien, die Sie mit Adobe InDesign erstellt haben, vollständig in AEM Assets zu laden, wird ein Proxy verwendet. Dieser verwendet einen Proxy Worker für die Kommunikation mit Adobe InDesign Server, wo [Skripte](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) ausgeführt werden, um Metadaten zu extrahieren und verschiedene Ausgabeformate für AEM Assets zu generieren. Der Proxy Worker ermöglicht die bidirektionale Kommunikation zwischen InDesign Server und den AEM-Instanzen in einer Cloud-Konfiguration.

>[!NOTE]
>
>Adobe InDesign wird in Form von zwei Produkten angeboten:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)
   >  Damit können Sie Seitenlayouts für den Druck bzw. die digitale Distribution entwerfen.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)
   >  Diese Engine ermöglicht die programmgesteuerte automatisierte Erstellung von Dokumenten, die auf denen basieren, die Sie mit InDesign entworfen haben. Die Engine fungiert als Dienst, der eine Schnittstelle seiner [ExtendScript](https://www.adobe.com/devnet/scripting.html)-Engine bereitstellt.
   >  Die Skripte werden in ExtendScript geschrieben, das Ähnlichkeiten mit JavaScript aufweist. For information about Indesign scripts see [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>



## So funktioniert die Extraktion {#how-the-extraction-works}

Der Adobe InDesign Server kann mit AEM Assets integriert werden, sodass mit InDesign erstellte INDD-Dateien hochgeladen, Darstellungen generiert, alle Medien extrahiert (z. B. Video) und als Assets gespeichert werden können:

>[!NOTE]
>
>Frühere Versionen von AEM konnten XMP und die Miniaturansicht extrahieren, während jetzt alle Medien extrahiert werden können.

1. Laden Sie Ihre INDD-Datei auf AEM Assets hoch.
1. Ein Framework sendet Befehlsskripte via SOAP (Simple Object Access Protocol) an InDesign Server.
Dieses Befehlsskript führt folgende Aktionen aus:

   * Rufen Sie die INDD-Datei ab.
   * Führt InDesign Server-Befehle aus:

      * Struktur, Text und alle Mediendateien werden extrahiert.
      * PDF- und JPG-Ausgabeformate werden generiert.
      * HTML- und IDML-Ausgabeformate werden generiert.
   * Veröffentlicht die resultierenden Dateien wieder in AEM Assets.
   >[!NOTE]
   >
   >IDML ist ein XML-Format, das *alle Funktionen* der InDesign-Datei rendert. Es wird als komprimiertes Paket mithilfe der [ZIP-Komprimierung](https://www.techterms.com/definition/zip) gespeichert.
   >
   >
   >See [Adobe Press - InDesign Interchange Formats INX and IDML](https://www.adobepress.com/articles/article.asp?p=1381880&seqNum=8) for further information.

   >[!CAUTION]
   >
   >Wenn der InDesign-Server nicht installiert oder nicht konfiguriert ist, können Sie dennoch eine INDD-Datei in AEM hochladen. Die erzeugten Darstellungen sind jedoch auf PNG und JPEG beschränkt. Sie können keine HTML-, IDML- oder Seitendarstellungen erstellen.

1. Nach der Extraktion und Ausgabegenerierung:

   * Die Struktur wird auf einer `cq:Page` repliziert (Ausgabetyp).
   * Der extrahierte Text und die Dateien werden in AEM Assets gespeichert.
   * Alle Ausgabeformate werden in AEM Assets im Asset selbst gespeichert.

## Integrieren von InDesign Server in AEM {#integrating-the-indesign-server-with-aem}

Um den InDesign-Server für die Verwendung mit AEM Assets und nach der Konfiguration des Proxys zu integrieren, müssen Sie:

1. [Installieren Sie InDesign Server](#installing-the-indesign-server).
1. Falls erforderlich, [konfigurieren Sie den AEM Assets-Workflow](#configuring-the-aem-assets-workflow).
Dies ist nur dann notwendig, wenn die Standardwerte für Ihre Instanz nicht geeignet sind.

1. Konfigurieren Sie einen [Proxy Worker für InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installieren von InDesign Server {#installing-the-indesign-server}

Um InDesign Server für die Verwendung mit AEM zu installieren und zu starten, gehen Sie wie folgt vor:

1. Laden Sie Adobe InDesign Server herunter und installieren ihn.

   >[!NOTE]
   >
   >InDesign Server (CS6 und höher).

1. Bei Bedarf können Sie die Konfiguration Ihrer InDesign Server-Instanz anpassen.

1. Starten Sie den Server über die Befehlszeile:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Dadurch wird der Server mit dem SOAP-Plug-in gestartet, das Port 8080 abhört. Alle Protokollmeldungen und Ausgaben werden direkt im Befehlsfenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie die Ausgabemeldungen in einer Datei speichern möchten, müssen Sie dazu eine Umleitung verwenden, z. B. unter Windows:
   >
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Konfigurieren des AEM Assets-Workflows {#configuring-the-aem-assets-workflow}

AEM Assets besitzt den vorkonfigurierten Workflow **DAM-Update-Asset**, der mehrere Prozessschritte speziell für InDesign bietet:

* [Extrahierung von Medien](#media-extraction)
* [Extrahierung von Seiten](#page-extraction)

<!--
BROKEN LINK This workflow is setup with default values that can be adapted for your setup on the various author instances (this is a standard workflow, so further information is available under [Editing a Workflow](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). If you are using the default values (including the SOAP port), then no configuration is needed. BROKEN LINK
-->

Nach Abschluss des Setups löst das Hochladen von InDesign-Dateien in AEM Assets (mithilfe einer der üblichen Methoden) den Workflow für die Verarbeitung des Assets und Vorbereitung der verschiedenen Ausgabeformate aus. Test your configuration by uploading an `.indd` file into AEM Assets to confirm that you see the different renditions created by IDS under `<*your_asset*>.indd/Renditions`

#### Extrahierung von Medien {#media-extraction}

Dieser Schritt steuert die Extraktion von Medien aus der INDD-Datei.

Anpassungen können Sie im Schritt **Extrahierung von Medien** auf der Registerkarte **Argumente** vornehmen.

![Argumente und Skriptpfade zum Extrahieren von Medien](assets/media_extraction_arguments_scripts.png)

Argumente und Skriptpfade zum Extrahieren von Medien

* **ExtendScript-Bibliothek** Dies ist eine einfache HTTP-GET/POST-Methodenbibliothek, die von anderen Skripten benötigt wird.

* **Skripte erweitern** Hier können Sie unterschiedliche Skriptkombinationen angeben. If you want your own scripts to be executed on the InDesign Server, save the scripts at `/apps/settings/dam/indesign/scripts`.
Informationen zu InDesign-Skripten finden Sie unter
   [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)

>[!CAUTION]
>
>Ändern Sie **nicht** die **ExtendScript-Bibliothek**.

>Diese Bibliothek bietet die HTTP-Funktionen, die für die Kommunikation mit Sling erforderlich sind. Diese Einstellung legt die Bibliothek fest, die zur Verwendung an InDesign Server gesendet werden soll.
>
Das Skript `ThumbnailExport.jsx`, das vom Workflow-Schritt „Extrahierung von Medien“ ausgeführt wird, generiert eine Miniaturansicht im JPG-Format. Diese Darstellung wird vom Arbeitsablaufschritt &quot;Prozessminiaturen&quot;verwendet, um die für AEM erforderlichen statischen Darstellungen zu generieren.

Sie können den Workflow-Schritt „Miniaturansichten verarbeiten“ so konfigurieren, dass statische Darstellungen in verschiedenen Größen generiert werden. Stellen Sie sicher, dass Sie die Voreinstellungen nicht entfernen, da sie für die AEM Assets-Benutzeroberfläche erforderlich sind. Abschließend entfernt der Workflow-Schritt „Bildvorschau-Wiedergabe löschen“ die JPG-Miniaturansicht, da sie nicht mehr benötigt wird.

#### Extrahierung von Seiten {#page-extraction}

Dabei wird eine AEM-Seite aus den extrahierten Elementen erstellt. Das Extrahieren von Daten aus einem Ausgabeformat (aktuell HTML oder IDML) erfolgt mithilfe eines Extrahierungshandlers. Diese Daten werden verwendet, um eine Seite mit PageBuilder zu erstellen.

Anpassungen können Sie im Schritt **Extrahierung von Seiten** auf der Registerkarte **Argumente** vornehmen.

![chlimage_1-96](assets/chlimage_1-96.png)

* **Handler zur Extrahierung von Seite** Wählen Sie in der Dropdownliste den zu verwendenden Handler aus. Ein Extrahierungshandler arbeitet mit einem bestimmten Ausgabeformat, das mit einem entsprechenden `RenditionPicker` ausgewählt wird (siehe `ExtractionHandler`-API).
In einer standardmäßigen AEM-Installation ist folgende Option verfügbar:

   * IDML-Export-Extrahierungshandler Bearbeitet das `IDML`-Ausgabeformat, das im Schritt „MediaExtract“ generiert wird.

* **Seitenname** Geben Sie den Namen an, den Sie der resultierenden Datei zuweisen möchten. Wenn Sie das Feld leer lassen, wird als Name „Seite“ gewählt (oder eine Ableitung, falls „Seite“ bereits vorhanden ist).

* **Seitentitel** Geben Sie den Titel an, den Sie der resultierenden Datei zuweisen möchten.

* **Stammverzeichnis der Seite** Der Pfad zum Stammverzeichnis der resultierenden Datei.
Wenn Sie das Feld leer lassen, wird der Knoten mit den Ausgabeformaten des Assets verwendet.

* **Seitenvorlage** Die zu verwendende Vorlage für das Generieren der resultierenden Seite.

* **Seitendesign** Das zu verwendende Seitendesign für das Generieren der resultierenden Seite.

### Konfigurieren von Proxy Worker für InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
Der Worker befindet sich in der Proxy-Instanz.

1. Erweitern Sie in der Tools-Konsole im linken Bereich den Eintrag **Cloud-Service-Konfigurationen**. Anschließend erweitern Sie den Eintrag **Cloud-Proxy-Konfiguration**.

1. Doppelklicken Sie auf den **IDS-Worker**, um ihn für die Konfiguration zu öffnen.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Konfigurationsdialogfeld zu öffnen und die erforderlichen Einstellungen vorzunehmen:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS-Pool** Die SOAP-Endpunkte, die mit InDesign Server kommunizieren sollen. Sie können Elemente nach Bedarf hinzufügen, entfernen und ordnen.

1. Klicken Sie zum Speichern auf OK.

### Konfigurieren von Day CQ Link Externalizer  {#configuring-day-cq-link-externalizer}

Wenn InDesign Server und AEM auf unterschiedlichen Hosts ausgeführt werden oder eine bzw. beide Anwendungen nicht die Standardanschlüsse nutzen, konfigurieren Sie in **Day CQ Link Externalizer** den Host, Port und Inhaltspfad für InDesign Server.

1. Greifen Sie auf Configuration Manager unter der URL zu `https://[aem_server]:[port]/system/console/configMgr`.
1. Locate the configuration **Day CQ Link Externalizer**, and click the **Edit** icon to open it.
1. Geben Sie den Hostnamen und Kontextpfad für InDesign Server an und klicken Sie auf **Speichern**.

   ![chlimage_1-97](assets/chlimage_1-97.png)

### Enabling Parallel Job Processing for InDesign Server(s) {#enabling-parallel-job-processing-for-indesign-server-s}

Sie können jetzt die parallele Auftragsverarbeitung für IDS aktivieren.

Dazu müssen Sie zunächst die maximale Anzahl der parallelen Aufträge (`x`) festlegen, die ein InDesign Server verarbeiten kann:

* Auf einem einzelnen Mehrprozessor-Computer ist die Anzahl der parallelen Aufträge (x), die ein InDesign Server verarbeiten kann, um eins kleiner als die Anzahl der Prozessoren, die IDS ausführen.
* Wenn Sie IDS auf mehreren Computern ausführen, müssen Sie von der Gesamtanzahl der verfügbaren Prozessoren (auf allen Computern) die Gesamtanzahl der Computer abziehen.

So konfigurieren Sie die Anzahl der parallelen IDS-Aufträge:

1. Öffnen Sie die Registerkarte **Konfigurationen** der Felix-Konsole. Beispiel: `https://[aem_server]:[port]/system/console/configMgr`.

1. Wählen Sie die IDS-Verarbeitungsschlange unter:

   `Apache Sling Job Queue Configuration`

1. Satz:

   * **Typ** - `Parallel`
   * **Maximale Anzahl paralleler Aufträge** - `<*x*>` (wie oben berechnet)

1. Speichern Sie diese Änderungen.
1. Aktivieren Sie die Unterstützung für Mehrfachsitzungen bei CS6 (und höher), indem Sie das folgende Kontrollkästchen aktivieren:

   `enable.multisession.name` checkbox

   Unter:

   `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`

1. Create a [pool of `<*x*>` IDS workers by adding SOAP endpoints to the IDS Worker configuration](#configuring-the-proxy-worker-for-indesign-server).

   Wenn mehrere Computer InDesign Server ausführen, fügen Sie SOAP-Endpunkte (Anzahl der Prozessoren pro Computer -1) für jeden Computer hinzu.

   >[!NOTE]
   Sie können IDS-Worker per Blacklist sperren, wenn Sie mit einem Worker-Pool arbeiten.
   To do so, enable the &quot;enable.retry.name&quot; checkbox, under the `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuration, which enables IDS job retrials.
   Legen Sie in der Konfiguration `com.day.cq.dam.ids.impl.IDSPoolImpl.name``max.errors.to.blacklist` außerdem einen positiven Wert für den Parameter „“ fest, der die Anzahl der Auftragswiederholungen steuert, bevor ein IDS aus der Auftrags-Handler-Liste ausgeschlossen wird.
   Standardmäßig wird der IDS-Worker nach einer konfigurierbaren Zeit (retry.interval.to.whitelist.name) in Minuten erneut validiert. Wenn der Worker online gefunden wird, wird er aus der Blacklist entfernt.

## Aktivieren der Unterstützung für InDesign Server 10.0 oder höher {#enabling-support-for-indesign-server-or-higher}

Führen Sie für InDesign Server 10.0 oder höher die folgenden Schritte durch, um Unterstützung für Mehrfachsitzungen zu aktivieren.

1. Öffnen Sie Configuration Manager über Ihre AEM Assets-Instanz `https://[aem_server]:[port]/system/console/configMgr`.
1. Edit the configuration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Select the **[!UICONTROL ids.cc.enable]** option, and click **[!UICONTROL Save]**.

>[!NOTE]
Verwenden Sie für die Integration von InDesign Server in AEM Assets einen Mehrkernprozessor, da die für die Integration notwendige Funktion „Sitzungsunterstützung“ auf Einzelkernsystemen nicht unterstützt wird.

## Konfigurieren von AEM-Anmeldeinformationen {#configure-aem-credentials}

Sie können die standardmäßigen Administrator-Anmeldeinformationen (Benutzername und Kennwort) für den Zugriff auf den InDesign Server aus Ihrer AEM-Instanz ändern, ohne die InDesign Server-Integration aufzuheben.

1. Wechseln zu `/etc/cloudservices/proxy.html`.
1. Geben Sie in diesem Dialogfeld den neuen Benutzernamen und das Kennwort ein.
1. Speichern Sie die Anmeldedaten.
