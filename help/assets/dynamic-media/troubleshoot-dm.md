---
title: Fehlerbehebung bei Dynamic Media
description: Tipps zur Fehlerbehebung bei der Verwendung von Dynamic Media.
topic: '"Administrator, Business Practitioner"'
role: Administrator,Business Practitioner
exl-id: 3e8a085f-57eb-4009-a5e8-1080b4835ae2
translation-type: tm+mt
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 78%

---

# Fehlerbehebung bei Dynamic Media {#troubleshooting-dynamic-media-scene-mode}

Das folgende Thema beschreibt die Fehlerbehebung bei Dynamic Media.

## Konfiguration für Dynamic Media {#new-dm-config}

Siehe [Fehlerbehebung für eine neue Dynamic Media-Konfiguration](/help/assets/dynamic-media/config-dm.md#troubleshoot-dm-config).

## Allgemein (alle Assets) {#general-all-assets}

Die folgenden allgemeinen Tipps und Tricks gelten für alle Assets.

### Asset-Synchronisierungsstatuseigenschaften  {#asset-synchronization-status-properties}

Die folgenden Asset-Eigenschaften können in CRXDE Lite überprüft werden, um die erfolgreiche Synchronisierung des Assets von Adobe Experience Manager nach Dynamic Media zu bestätigen:

| **Eigenschaft** | **Beispiel** | **Beschreibung** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a|364266`** | Allgemeiner Indikator dafür, dass der Knoten mit Dynamic Media verknüpft ist. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** oder Fehlertext | Status des Hochladens der Assets in Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Muss ausgefüllt werden, um URLs für Remote-Assets von Dynamic Media zu generieren. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **Erfolg** oder **fehlgeschlagen:`<error text>`** | Synchronisierungsstatus für Sets (Rotationssets, Bildsets usw.), Bildvorgaben, Viewer-Vorgaben oder Imagemap-Updates für ein Asset oder Bilder, die bearbeitet wurden. |

### Protokollierung der Synchronisierung {#synchronization-logging}

Synchronisierungsfehler und -probleme werden bei `error.log` (Experience Manager-Serververzeichnis `/crx-quickstart/logs/`) protokolliert. Anhand der protokollierten Informationen lassen sich die Hauptursachen der meisten Probleme ermitteln. Sie können die Protokollierung aber auch im Paket `com.adobe.cq.dam.ips` über die Sling Console ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) auf DEBUG heraufsetzen, um mehr Informationen zu erfassen.

### Versionskontrolle {#version-control}

Beim Ersetzen eines vorhandenen Dynamic Media-Assets (gleicher Name und Speicherort) können Sie beide Assets beibehalten oder eine Version ersetzen/erstellen:

* Beim Beibehalten beider Werte wird ein Asset mit einem eindeutigen Namen für die URL des veröffentlichten Assets erstellt. Beispiel: `image.jpg` ist das ursprüngliche Asset und `image1.jpg` ist das neu hochgeladene Asset.

* Das Erstellen einer Version wird in Dynamic Media nicht unterstützt. Die neue Version ersetzt das vorhandene Asset in Versand.

## Bilder und Sets   {#images-and-sets}

Falls Sie Probleme mit Bildern und Sets haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Kein Zugriff auf Schaltfläche „URL kopieren“/„Code einbetten“ in der Asset-Detailansicht</td>
   <td>
    <ol>
     <li><p>Öffnen Sie CRX/DE:</p>
      <ul>
       <li>Überprüfen Sie, ob die Vorgabe im JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> definiert ist. Dieser Speicherort gilt, wenn Sie von Experience Manager 6.x auf 6.4 aktualisiert und die Migration abgebrochen haben. Andernfalls ist der Speicherort <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li>
       <li>Überprüfen Sie, ob das Asset im JCR unter „Metadaten“ für <code>dam:scene7FileStatus</code><strong></strong> den Wert <code>PublishComplete</code> aufweist.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Seite aktualisieren/zu einer anderen Seite navigieren und wieder zurückkehren (JSP für die Seitenleiste muss neu kompiliert werden)</p> <p>Wenn dies das Problem nicht behebt:</p>
    <ul>
     <li>Veröffentlichen Sie das Asset.</li>
     <li>Laden Sie das Asset erneut und veröffentlichen Sie es.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Karussell-Hotspot verschiebt sich nach dem Wechsel zwischen Folien</td>
   <td><p>Prüfen Sie, ob alle Folien dieselbe Größe haben.</p> </td>
   <td><p>Verwenden Sie für das Karussell nur Bilder derselben Größe.</p> </td>
  </tr>
  <tr>
   <td>Bild wird im Viewer für Dynamic Media nicht als Vorschau angezeigt</td>
   <td><p>Überprüfen Sie, ob das Asset <code>dam:scene7File</code> in den Metadateneigenschaften (CRXDE Lite) enthält.</p> </td>
   <td><p>Überprüfen Sie, ob alle Elemente verarbeitet wurden.</p> </td>
  </tr>
  <tr>
   <td>Hochgeladenes Asset wird nicht in der Asset-Auswahl angezeigt</td>
   <td><p>Überprüfen Sie, ob das Asset die Eigenschaft <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite) aufweist.</p> </td>
   <td><p>Überprüfen Sie, ob alle Elemente verarbeitet wurden.</p> </td>
  </tr>
  <tr>
   <td>Banner wird in der Kartenansicht als <strong>Neu</strong> angezeigt, wenn das Asset noch nicht gestartet wurde</td>
   <td>Überprüfen Sie <code>jcr:content</code> &gt; <code>dam:assetState</code> für das Asset. Wenn <code>unprocessed</code>, dann wurde es nicht vom Workflow abgeholt</td>
   <td>Warten Sie, bis das Asset vom Workflow abgeholt wurde.</td>
  </tr>
  <tr>
   <td>Bilder oder Sets zeigen weder Viewer-URL noch eingebetteten Code an</td>
   <td>Prüfen Sie, ob die Viewer-Vorgabe veröffentlicht wurde.</td>
   <td><p>Wechseln Sie zu <strong>Tools</strong> &gt; <strong>Assets</strong> &gt; <strong>Viewer-Vorgaben</strong> und veröffentlichen Sie die Viewer-Vorgabe.</p> </td>
  </tr>
 </tbody>
</table>

## Video {#video}

Falls Sie Probleme mit Videos haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Video kann nicht als Vorschau angezeigt werden</td>
   <td>
    <ul>
     <li>Prüfen Sie, ob dem Ordner ein Videoprofil zugewiesen ist (falls nicht unterstütztes Dateiformat). Falls nicht unterstützt, wird nur ein Bild angezeigt.</li>
     <li>Das Videoprofil muss mehr als eine Kodierungsvorgabe enthalten, damit ein AVS-Set generiert werden kann (einzelne Kodierungen werden als Videoinhalt für MP4-Dateien behandelt; nicht unterstützte Dateien werden wie nicht verarbeitete Dateien behandelt).</li>
     <li>Überprüfen Sie anhand von <code>dam:scene7FileAvs</code> von <code>dam:scene7File</code> in den Metadaten, ob die Verarbeitung des Videos abgeschlossen wurde.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Weisen Sie dem Ordner ein Videoprofil zu.</li>
     <li>Bearbeiten Sie das Videoprofil, damit es mehr als eine Kodierungsvorgabe enthält.</li>
     <li>Warten Sie, bis die Verarbeitung des Videos abgeschlossen ist.</li>
     <li>Bevor Sie das Video erneut laden, vergewissern Sie sich, dass der Dynamic Media-Kodierungs-Video-Workflow nicht ausgeführt wird.<br/> </li>
     <li>Laden Sie das Video erneut hoch.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Video ist nicht kodiert</td>
   <td>
    <ul>
     <li>Überprüfen Sie, ob Dynamic Media Cloud Service konfiguriert ist.</li>
     <li>Prüfen Sie, ob dem Upload-Ordner ein Videoprofil zugeordnet ist.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Prüfen Sie, ob die Dynamic Media-Konfiguration unter Cloud Services ordnungsgemäß eingerichtet ist.</li>
     <li>Überprüfen Sie, ob der Ordner ein Videoprofil hat. Überprüfen Sie außerdem das Videoprofil.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Die Videoverarbeitung dauert zu lang</td>
   <td><p>So prüfen Sie, ob die Videokodierung noch läuft oder ob ein Fehler aufgetreten ist:</p>
    <ul>
     <li>Überprüfen Sie den Videostatus <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Videoausgabedarstellung fehlt</td>
   <td><p>Wenn das Video hochgeladen wurde, aber keine kodierten Ausgabedarstellungen vorhanden sind:</p>
    <ul>
     <li>Prüfen Sie, ob dem Ordner ein Videoprofil zugewiesen ist.</li>
     <li>Prüfen Sie anhand von <code>dam:scene7FileAvs</code> in den Metadaten, ob die Verarbeitung des Videos abgeschlossen wurde.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Weisen Sie dem Ordner ein Videoprofil zu.</li>
     <li>Warten Sie, bis die Verarbeitung des Videos abgeschlossen ist.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## Viewer {#viewers}

Falls Sie Probleme mit einem Viewer haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Viewer-Vorgaben werden nicht veröffentlicht</td>
   <td><p>Wechseln Sie zur Diagnoseseite des Beispiel-Managers: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></p> <p>Überwachen Sie die berechneten Werte. Wenn Sie richtig arbeiten, sehen Sie Folgendes:</p> <p><code>_DMSAMPLE status: 0 unsyced assets - activation not necessary
       _OOTB status: 0 unsyced assets - 0 unactivated assets</code></p> <p><strong>Hinweis</strong>: Nach der Konfiguration der Dynamic Media-Cloud-Einstellungen kann es bis zu 10 Minuten dauern, bis die Assets im Viewer synchronisiert werden.</p> <p>Falls weiterhin nicht aktivierte Assets vorhanden sind, klicken Sie auf eine der Schaltflächen <strong>Alle nicht aktivierten Assets auflisten</strong>, um die Details anzuzeigen.</p> </td>
   <td>
    <ol>
     <li>Navigieren Sie in den Admin Tools zur Viewer-Vorgabeliste: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></li>
     <li>Wählen Sie alle Viewer-Vorgaben aus und klicken Sie auf <strong>Veröffentlichen</strong>.</li>
     <li>Navigieren Sie zurück zum Beispiel-Manager und prüfen Sie, ob die Anzahl der nicht aktivierten Assets jetzt mit null angegeben wird.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Für das Bildmaterial der Viewer-Vorgabe wird für eine Vorschau in den Asset-Details oder für „URL kopieren“/„Code einbetten“ der Code 404 zurückgegeben</td>
   <td><p>Gehen Sie in CRXDE Lite wie folgt vor:</p>
    <ol>
     <li>Navigieren Sie zum <code>&lt;sync-folder&gt;/_CSS/_OOTB</code>-Ordner im Synchronisierungsordner für Dynamic Media (z. B. <code>/content/dam/_CSS/_OOTB</code>).</li>
     <li>Suchen Sie den Metadaten-Knoten des problematischen Assets (z. B. <code>&lt;sync-folder&gt;/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/</code>).</li>
     <li>Prüfen Sie, ob die Eigenschaften <code>dam:scene7*</code> vorhanden sind. Wenn das Asset erfolgreich synchronisiert und veröffentlicht wurde, sehen Sie, dass <code>dam:scene7FileStatus</code> auf <strong>PublishComplete</strong> eingestellt ist.</li>
     <li>Versuchen Sie, das Bildmaterial direkt aus Dynamic Media anzufordern, indem Sie die Werte der folgenden Eigenschaften und Zeichenketten verketten.
      <ul>
       <li><code>dam:scene7Domain</code></li>
       <li><code>"is/content"</code></li>
       <li><code>dam:scene7Folder</code></li>
       <li><code>&lt;asset-name&gt;</code></li>
       <li>Beispiel: <code>https://&lt;server&gt;/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png</code></li>
      </ul> </li>
    </ol> </td>
   <td><p>Wenn die Beispiel-Assets oder Viewer-Vorgabengrafiken nicht synchronisiert oder veröffentlicht wurden, starten Sie den gesamten Kopieren/Synchronisierungsprozess neu:</p>
    <ol>
     <li>Navigieren Sie zu <code>/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code>
     </li>
     <li>Wählen Sie die folgenden Aktionen in der angegebenen Reihenfolge aus:
      <ol>
       <li>Synchronisierte Ordner löschen</li>
       <li>Ordner "Vorgabe löschen"(unter <code>/conf</code>).
       <li>Async-Auftrag für DM-Setup auslösen</li>
      </ol> </li>
     <li>Warten Sie auf Benachrichtigung über erfolgreiche Synchronisierung in Ihrem Experience Manager-Posteingang.
     </li>
    </ol> </td>
  </tr>
 </tbody>
</table>
