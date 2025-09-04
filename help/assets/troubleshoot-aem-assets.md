---
title: Fehlerbehebung in AEM Assets
description: Beheben Sie häufige AEM Assets-Probleme mithilfe der Artikel-Links für wichtige AEM Assets s=Bereiche wie Uploads, Metadaten, Suche, Bereitstellung usw.
hidefromtoc: true
hide: true
source-git-commit: c8f1c40e4300b26141cc394a9208641769da1f1e
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---


# Fehlerbehebung bei AEM Assets-Problemen {#troubleshoot-aem-assets}

AEM Assets as a Cloud Service bietet eine Cloud-native PaaS-Lösung für Unternehmen, mit der sie nicht nur ihre Digital-Asset-Management- und Dynamic-Media-Vorgänge durchführen, sondern auch intelligente Funktionen der nächsten Generation wie KI/ML nutzen können. Alles innerhalb eines Systems, das immer aktuell, verfügbar und lernbereit ist.

Es können jedoch Probleme auftreten, die sich auf Asset-Uploads, Metadaten, Suche oder Bereitstellung und andere wichtige Bereiche von AEM Assets auswirken. Dieser Artikel enthält Schritte zur Fehlerbehebung, mit denen Sie diese häufigen AEM Assets-Probleme diagnostizieren und beheben können.

<table>
  <tbody>
  <tr>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27140">Ausgabedarstellungen fehlen in der ZIP-Datei zum Asset-Download in AEM</a> </td>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26616">Inhaltsfragmente sind nicht in der AEM Assets-Lizenz enthalten</a> </td>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26928">Kommentieren in der Assets-Ansicht trotz Lesezugriff eingeschränkt</a> </td> 
    </tr>
    <tr>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26715"> (Dynamic Media)-Rotationssets bleiben im Verarbeitungsstatus in AEM Dynamic Media stecken</a> </td>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26639">DAM-Ausgabedarstellungen (Digital Asset Management) stimmen nicht mit den Originaldateien in AEM überein</a> </td>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26873">Ausgabedarstellungen für smartes Zuschneiden werden in AEMaaCS nicht generiert</a> </td> 
    </tr>
    <tr>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26533">(Dynamic Media) Beheben von Problemen beim Hochladen, Verarbeiten und Rendern von Videos in AEM</a> </td>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26922">(Asset Link) Adobe Asset Link lässt Links bei Verwendung von InDesign in einem nicht zugänglichen Status</a> </td>
    <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26677">Fehlende Übereinstimmung der Videominiaturen zwischen Dynamic Media- und DAM-Kartenansicht in AEMaaCS</a> </td> 
    </tr>
    <tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26610">Fehler bei der Asset-Verarbeitung für große MP4-Dateien in AEM as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26871">(Dynamic Media) Der Dynamic Media-Video-Player funktioniert nicht in niedrigeren Umgebungen</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26103">(Dynamic Media mit OpenAPI) Aktivieren des eingeschränkten Assets-Zugriffs auf Dynamic Media mit Open APIs basierend auf IMS-Benutzergruppen</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-23916">Wenn eine TIFF-Datei mit ZIP-Komprimierungsformat in AEM Assets hochgeladen wird, werden keine Ausgabedarstellungen generiert</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM kürzt extrahierten Text aus großen PDFs nach 100.000-Token</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-17628">(Dynamic Media) Ändern der Dynamic Media-URL für DM Assets</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26655">Beheben von Problemen mit der Sichtbarkeit von Metadatenschemata für Benutzende ohne Administratorrechte in AEMaaCS</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26637">(Dynamic Media) Problem mit der Hintergrundfarbänderung für TIFF-Bildausgabedarstellungen in Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26528">AEMaaCS-Problem mit der Asset-Rotation macht nachfolgende Rotationen unsichtbar</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26367">(Dynamic Media) Beheben eines Bildfehlers beim smarten Zuschneiden in Adobe Experience Manager 6.5 Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26450">Erhöhen der Obergrenze für den Asset-Upload für einzelne Teile für die Photoshop Firefly-API-Integration</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26461">(Dynamic Media) Beheben von Diskrepanzen bei Namen von Dynamic Media-Assets in AEM-Umgebungen für PDF-Dateien</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26233">Bestimmte Bilder zeigen in Adobe Experience Manager (AEM) as a Cloud Service - Asset keine Ausgabedarstellungen für Miniaturansichten an</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25294">(Dynamic Media) Die Seite „Allgemeine Dynamic Media-Einstellungen“ wird nicht geöffnet</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26197">(Dynamic Media) Beheben von Audioproblemen in Videodateien mit Dynamic Media in AEM</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25925">Automatisches Tagging neu hochgeladener Assets in AEM as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25889">Die Smart-Tags-Funktion funktioniert nach der Migration von JWT zu OAuth in AEM nicht</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25903">Beheben von Problemen mit freigegebenen Links in AEM Managed Services</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25607">(Dynamic Media) Asset-Verarbeitungsfehler in AEM Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25885">(Dynamic Media) Asset-Synchronisierungsfehler in Adobe Experience Manager (AEM) Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25829">Aktualisieren von benutzerdefinierten Miniaturansichten für Video-Assets in AEM as a Cloud Service</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25828">Diskrepanz bei Bildmetadaten in Adobe Experience Manager (AEM) Assets</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-21865">Drag-and-Drop eines Asset-Ordners in die AEM Assets-Web-Benutzeroberfläche schlägt fehl</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25525">(Dynamic Media) Beheben von Problemen mit der Asset-Verarbeitung in AEM as a Cloud Service</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25518">Einschränkungen bei der Textextraktion für große PDFs in Adobe Experience Manager as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25562">(Asset Link) Beheben von Verbindungsproblemen mit Adobe Experience Manager (AEM)-Asset-Links in InDesign</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25506">(Asset Link) Netzwerkfehler im Adobe Asset Link-Plug-in: Server ist nicht erreichbar</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-25471">Benutzerempfehlungen für die Synchronisierung von Dynamic Media (Dynamic Media)</a></td>
  <td><a href="https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26902">(Dynamic Media) Exportieren von Assets und Metadaten aus Dynamic Media mithilfe der -API</a></td>
  <td></td>
</tr>

</tbody>
  <table>


