---
title: Metadatenschema-Referenz
description: 'Erfahren Sie mehr über die Standard-Konventionen für das Beschreiben von Asset-Metadaten, darunter Dublin Core, IPTC und weitere Metadatenschemen. '
contentOwner: AG
translation-type: ht
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Metadatenschema-Referenz {#metadata-schemata-reference}

Die folgende Referenz enthält Informationen zu bestimmten Metadatenschemata (in alphabetischer Reihenfolge) sowie eine Liste mit Eigenschaften und den zugehörigen Definitionen.

## Dublin Core {#dublin-core}

Dublin Core-Metadaten bieten ein standardisiertes Set aus Konventionen für die Beschreibung von Assets, um die Suche nach ihnen zu erleichtern. In AEM Assets beschreibt Dublin Core digitale Assets wie Videos, Audio, Bilder und Dokumente.

Das einfache Dublin Core Metadata Element Set (DCMES) enthält 15 Metadatenelemente, die in der folgenden Tabelle aufgeführt werden. Jedes Dublin Core-Element ist optional und kann wiederholt werden. Sie können Dublin Core-Metadateninformationen genauso wie solche für medientypspezifische Metadaten hinzufügen oder löschen.

Zusätzlich zum DCMES wurden auch noch andere Metadatenelemente von der Dublin Core Initiative erstellt. Weitere Informationen finden Sie unter [Dublin Core Initiative](https://dublincore.org/).

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>contributor</td> 
   <td>Die Personen oder das Unternehmen, diedafür verantwortlich sind, zum Inhalt beizutragen.</td> 
  </tr>
  <tr>
   <td>coverage</td> 
   <td>Der geografische Standort oder Zeitraum, den das Asset abdeckt.<br /> </td> 
  </tr>
  <tr>
   <td>creator</td> 
   <td>Die Personen oder das Unternehmen, die dafür verantwortlich sind, den Inhalt zu erstellen.</td> 
  </tr>
  <tr>
   <td>date</td> 
   <td>Datum oder Zeitraum, mit dem das Asset verknüpft ist.<br /> </td> 
  </tr>
  <tr>
   <td>description</td> 
   <td>Weitere Informationen zum Asset.</td> 
  </tr>
  <tr>
   <td>format</td> 
   <td>Das Dateiformat, das physische Medium oder die Dimensionen des Assets. AEM verwendet <code>dc:format</code>, um den MIME-Typ des Assets zu kennzeichnen.<br /> </td> 
  </tr>
  <tr>
   <td>identifier</td> 
   <td>Eine eindeutige Referenz zum Asset.</td> 
  </tr>
  <tr>
   <td>language</td> 
   <td>Die Sprache des Assets (z. B. „en“ für Englisch).</td> 
  </tr>
  <tr>
   <td>publisher</td> 
   <td>Die Personen oder das Unternehmen, die dafür verantwortlich sind, das Asset verfügbar zu machen.</td> 
  </tr>
  <tr>
   <td>relation</td> 
   <td>Ein zugehöriges Asset.</td> 
  </tr>
  <tr>
   <td>rights</td> 
   <td>Informationen dazu, wer die Rechte für dieses Asset besitzt.</td> 
  </tr>
  <tr>
   <td>source</td> 
   <td>Ein zugehöriges Asset, aus dem das Asset abgeleitet wurde.</td> 
  </tr>
  <tr>
   <td>subject</td> 
   <td>Das Thema des Assets.<br /> </td> 
  </tr>
  <tr>
   <td>title</td> 
   <td>Ein Name für das Asset.</td> 
  </tr>
  <tr>
   <td>type</td> 
   <td>Die Art oder das Genre des Assets.</td> 
  </tr>
 </tbody>
</table>

## IPTC {#iptc}

Der International Press Telecommunications Council (IPTC) ist eine Arbeitsgemeinschaft aus Nachrichtenagenturen aus der ganzen Welt. Eines seiner Ziele ist die Entwicklung und Aufrechterhaltung technischer Standards. Der IPTC definiert ein Set aus Fotometadaten-Standards für Bilder, das fast universell von Fotografen anerkannt wird. Diese Metadatenstandards waren Bestandteil des umfassenderen Standards IPTC Information Interchange Model (IIM), der in den 1990er Jahren aufgestellt wurde.

Obwohl die IPTC-Kopfzeileninformationen größtenteils von XMP abgelöst wurden, sind ein IPTC-Kernschema und ein Erweiterungsschema für XMP verfügbar. In Bildprogrammen werden XMP- und IPTC-Eigenschaften synchronisiert.
