---
title: Best Practices zur Integration mit  [!DNL Adobe Creative Cloud]
description: Best Practices für die Integration einer Experience Manager-Implementierung mit Adobe Creative Cloud zur Optimierung der Workflows zur Asset-Übertragung und zur Steigerung der Effizienz.
contentOwner: AG
mini-toc-levels: 1
feature: Collaboration,Adobe Asset Link,Desktop App
role: Architect,Business Practitioner,Administrator
exl-id: cbed0d62-5148-45eb-b6a0-9fd164060fdc
translation-type: tm+mt
source-git-commit: 522d0363c0207afbed2c51e9d54d921ce9b66c70
workflow-type: tm+mt
source-wordcount: '3300'
ht-degree: 99%

---

# Best Practices für die Integration von AEM und Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

Adobe Experience Manager (AEM) Assets ist eine Digital Asset Management(DAM)-Lösung, die mit Adobe Creative Cloud integriert werden kann, um DAM-Benutzer bei der Zusammenarbeit mit Kreativ-Teams zu unterstützen und so die Kooperation beim Erstellen von Inhalten zu optimieren.

Adobe Creative Cloud bietet Kreativ-Teams ein System von Lösungen und Services, um digitale Assets zu erstellen. Dieses Angebot enthält Desktop-Programme und Mobile Apps, Cloud-Services wie Speicher mit Desktop-Synchronisierung oder Web-Erlebnis sowie Marktplätze wie Adobe Stock.

Lesen Sie weiter, um mehr darüber zu erfahren, welche Integration Sie zwischen Desktop und DAM-Enterprise-System abhängig vom Nutzungsszenario und von den entsprechenden Best Practices für die Verbindungs-Workflows wählen sollten.

>[!NOTE]
>
>Die Ordnerfreigabe von AEM in Creative Cloud wird nicht mehr unterstützt und nachfolgend nicht mehr behandelt. Adobe empfiehlt neuere Funktionen wie Adobe Asset Link oder AEM-Desktop-Programm, um kreativen Benutzern den Zugriff auf in AEM verwaltete Assets zu ermöglichen.

## Kooperationsanforderungen von Kreativen, Marketern und DAM-Benutzern  {#collaboration-need-of-creatives-marketers-and-dam-users}

| Voraussetzungen | Anwendungsfall | Betroffene Oberflächen |
|---|---|---|
| Vereinfachtes Desktop-Erlebnis für Kreative | Für Kreativprofis oder, ganz allgemein, für Desktop-Benutzer, die mit nativen Programmen zur Asset-Erstellung arbeiten, soll der Zugriff auf Assets von einem DAM-System (AEM Assets) optimiert werden. Sie benötigen eine einfache und unkomplizierte Möglichkeit zum Entdecken, Verwenden (Öffnen), Bearbeiten und Speichern von Änderungen in AEM sowie zum Hochladen neuer Dateien. | Windows- oder Mac-Desktop, Creative Cloud-Programme |
| Bereitstellen von hochwertigen, gebrauchsfertigen Assets aus Adobe Stock | Marketer tragen zu einer schnelleren Inhaltserstellung bei, indem sie beim Beschaffen von und Suchen nach Assets helfen. Kreativprofis verwenden die genehmigten Assets direkt in ihren Kreativ-Tools. | AEM Assets, Adobe Stock Marketplace, Metadatenfelder |
| Verteilen und Freigeben von Assets nach Organisationen | Interne Abteilungen/Zweigstellen und externe Partner, Distributoren und Agenturen verwenden die genehmigten Assets, die von der übergeordneten Organisation freigegeben wurden. Die Organisation möchte die erstellten Assets sicher und nahtlos für eine größere Wiederverwendung freigeben. | Brand Portal, Asset Share Commons |

## Adobe-Angebote zur Unterstützung von Kooperationsbedarf {#adobe-offerings-to-support-the-collaboration-need}

| Wertangebot für die betroffenen Benutzer | Adobe-Angebot | Betroffene Oberflächen |
|---|---|---|
| Kreativbenutzer entdecken Assets aus AEM, öffnen und verwenden diese, führen Bearbeitungen durch und laden AEM-Änderungen sowie neue Dateien in AEM hoch, ohne Creative Cloud-Programme verlassen zu müssen. | [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator und InDesign |
| Geschäftsbenutzer vereinfachen das Öffnen und Verwenden von Assets, führen Bearbeitungen durch und laden AEM-Änderungen sowie neue Dateien aus der Desktop-Umgebung in AEM hoch. Sie nutzen eine generische Integration, um jeden Asset-Typ in nativen Desktop-Programmen, auch Adobe-fremden, zu öffnen. | [[!DNL Experience Manager] -Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de) | AEM-Desktop-Programm auf Windows- und Mac-Desktop |
| Marketer und Geschäftsbenutzer können Adobe Stock-Assets in AEM entdecken, in einer Vorschau anzeigen, lizenzieren sowie speichern und verwalten. Lizenzierte und gespeicherte Assets liefern ausgewählte Adobe Stock-Metadaten für eine bessere Governance. | [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md) | AEM-Web-Oberfläche |

Dieser Artikel konzentriert sich in erster Linie auf die ersten beiden Aspekte der Zusammenarbeit. Die Verteilung und Beschaffung von Vermögenswerten im entsprechende Maß wird kurz als Verwendungsfall genannt. Für solche Lösungen sollten Sie Adobe Brand Portal oder Asset Share Commons beachten. Alternative Lösungen wie [AEM Assets Brand Portal](https://helpx.adobe.com/de/experience-manager/brand-portal/user-guide.html), Lösungen, die basierend auf [Asset Share](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Komponenten erstellt werden können, und [Link-Freigabe](share-assets.md), die allesamt die [AEM Assets-Web-Benutzeroberfläche](/help/assets/manage-digital-assets.md) verwenden, sind auf Grundlagen bestimmter Anforderungen zu prüfen.

![Creative Cloud-Verbindungen für AEM: Festlegen der zu verwendenden Funktion](assets/creative-connections-aem.png)

Festlegen der zu verwendenden Funktion

### Zuordnen von Nutzungsszenarien und Adobe-Lösungen   {#mapping-of-use-cases-and-adobe-solutions}

| Anwendungsfall | Adobe Asset Link | AEM-Desktop-Programm | Bemerkungen oder alternative Methoden |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Entdecken – Durchsuchen von AEM-Ordnern | Ja | AEM-Web-Benutzeroberfläche und Desktop-Aktionen | Deaktivieren Sie beim Durchsuchen der Netzwerkfreigabe die Miniaturansichten, um das Herunterladen binärer Asset-Dateien zu vermeiden. |
| Entdecken – Zugreifen auf AEM-Sammlungen | Ja | AEM-Web-Benutzeroberfläche und Desktop-Aktionen |  |
| Entdecken – Suchen nach Assets aus AEM | Ja | AEM-Web-Benutzeroberfläche und Desktop-Aktionen |  |
| Verwenden – Öffnen von Assets | Ja | Ja – für jede App | [Öffnen über die Web-Benutzeroberfläche](/help/assets/manage-digital-assets.md#previewing-assets) oder den Finder |
| Verwenden – Platzieren von Assets aus AEM in ein Dokument | Ja – Einbetten | Ja – Verknüpfen oder Einbetten | Das AEM-Desktop-Programm ermöglicht den Zugriff auf Assets als Dateien im lokalen Dateisystem. Diese Links in den nativen Programmen werden durch lokale Pfade dargestellt. |
| Bearbeiten – Öffnen zur Bearbeitung | Ja – Checkout-Aktion | Ja – Öffnen-Aktion (über die Netzwerkfreigabe) | Beim [Checkout in AAL](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) wird standardmäßig das Asset für das Creative Cloud-Speicherkonto des Benutzers (synchronisiert durch das Creative Cloud-Programm) gespeichert. |
| Bearbeiten – laufende Arbeiten außerhalb von AEM | Ja – Asset im mit dem Desktop synchronisierten Creative Cloud-Speicherkonto des Benutzers verfügbar. | Ja |  |
| Bearbeiten – Hochladen von Änderungen | Ja – [Checkin-Aktion](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) mit optionalem Kommentar | Ja |  |
| Hochladen – einzelne Datei | Ja – Hochladen des aktuellen aktiven Dokuments | Ja | [Hochladen über die Web-Oberfläche](/help/assets/manage-digital-assets.md#uploading-assets) |
| Hochladen – mehrere Dateien/hierarchische Ordnerstrukturen | Nein | Ja | [Hochladen über die Web-Oberfläche](/help/assets/manage-digital-assets.md#uploading-assets); benutzerdefiniertes Skript oder Tool |
| Sonstiges – Benutzer und Anmeldung | Erkennung des Creative Cloud-Benutzers, der beim Creative Cloud-Desktop-Programm angemeldet ist (SSO) | AEM-Benutzer/-Anmeldung | Benutzer beider Lösungen werden mit dem AEM-Benutzerkontingent verrechnet. |
| Sonstiges – Netzwerk und Zugriff | Zugriff vom Desktop des Benutzers auf AEM-Implementierungen über das Netzwerk erforderlich | Zugriff vom Desktop des Benutzers auf AEM-Implementierungen über das Netzwerk erforderlich | Adobe Asset Link gibt keine Netzwerk-Proxy-Umgebung frei. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

Um Nutzungsszenarien zum Verteilen von Assets zu unterstützen, sollten andere Lösungen in Betracht gezogen werden:

* [AEM Assets Brand ](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) Portalfor ein konfigurierbares Add-on zu Assets zum Veröffentlichen von Assets.

* Benutzerdefinierte Lösungen, erstellt auf Grundlage der [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)-Code-Basis
* AEM-[Linkfreigabe](/help/assets/share-assets.md), um Assets ad hoc mithilfe von Links freizugeben
* [AEM Assets-Web-Oberfläche](/help/assets/manage-digital-assets.md) mit Bereichen für externe Parteien, die durch Einrichtung einer AEM-Zugriffssteuerung abgesichert sind, und mit notwendigem IT-/Netzwerkkonfigurationsanpassungen, wodurch diese externen Benutzer Zugriff auf AEM erhalten

## Grundlegende Konzepte und Nutzungsszenarien {#key-concepts-and-use-cases}

### Glossar der allgemeinen Begriffe {#glossary-of-common-terms}

* **Laufende Arbeit oder laufende kreative Arbeit (Work-In-Progress, WIP):** Eine Phase im Asset-Lebenszyklus, in der ein Asset mehrfach geändert wird und in der Regel noch nicht zur Freigabe für breitere Teams bereit ist.
* **Fertige Kreativ-Assets:** Assets, die für ein breiteres Team freigegeben werden können oder die vom Kreativ-Team für die Freigabe mit Marketing- oder LOB-Teams ausgewählt/genehmigt wurden.

* **Asset-Genehmigungen:** Der Genehmigungsprozess, der für Assets ausgeführt wird, die bereits auf DAM hochgeladen wurden. Dazu gehören in der Regel Markengenehmigungen, Genehmigungen usw.
* **Abgeschlossenes Asset:** Ein Asset, für das alle    Genehmigungen/Metadaten-Tagging durchgeführt wurden und das bereit für die Verwendung durch das breitere Team ist. Ein solches Asset wird in DAM gespeichert und allen (bzw. allen interessierten) Benutzern zur Verfügung gestellt. Es kann in Marketing-Kanälen oder von Kreativ-Teams verwendet werden, um Designs zu erstellen.

* **Kleinere Asset-Aktualisierung/-Änderung:** Schnelle, kleine Änderung an einem digitalen Asset. Diese wird häufig aufgrund einer Retuschieranfrage oder einer kleineren Bearbeitungsanfrage, einer Asset-Überprüfung oder einer Genehmigung (z. B. Neupositionierung, Änderung der Textgröße, Anpassung der Sättigung/Helligkeit, Farbe usw.) durchgeführt.
* **Größere Asset-Aktualisierung/-Änderung:** Änderung eines digitalen Assets, die viel Arbeit erfordert und manchmal über einen längeren Zeitraum erfolgen muss. Diese umfasst in der Regel mehrere Änderungen. Das Asset muss während der Aktualisierung mehrmals gespeichert werden. Bei umfangreichen Asset-Aktualisierungen wird das Asset in der Regel in eine WIP-Phase versetzt.
* **DAM:** Digital Asset Management. In diesem Dokument wird der Begriff synonym mit AEM Experience Manager-Assets verwendet, sofern nicht ausdrücklich anders angegeben.
* **Kreativer Benutzer:** Kreativprofi, der digitale Assets mit Creative Cloud-Programmen und -Services erstellt. In einigen Fällen kann ein kreativer Benutzer Mitglied eines Kreativ-Teams sein, das möglicherweise Creative Cloud verwendet, aber keine digitalen Assets erstellt (z. B. Creative Director oder Creative Team Manager).
* **DAM-Benutzer:** Ein typischer Benutzer eines DAM-Systems. Je nach Organisation kann ein DAM-Benutzer ein Marketing- oder Nicht-Marketing-Benutzer sein, z. B. Branchenbenutzer, Bibliothekar, Vertriebsmitarbeiter usw.

### Überlegungen zur Integration von AEM und Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Dies ist eine kurze Zusammenfassung von Best Practices für die AEM- und Creative Cloud-Integration. Lesen Sie den Rest dieses Dokuments, um detaillierte Informationen dazu zu erhalten.

* **Für kreative Benutzer, die in Photoshop, InDesign oder Illustrator arbeiten:** Adobe Asset Link bietet ein optimales Benutzererlebnis, einschließlich der ordnungsgemäßen Abwicklung laufender Arbeiten von aus AEM ausgecheckten Assets.
* **Für einen vereinfachten Desktop-Zugriff auf Assets bei beliebigen allgemeinen Dateiformaten oder Programmen:** Verwenden Sie das AEM-Desktop-Programm.
* **Verstehen, warum und wann Assets in DAM gespeichert werden:** Aktualisierungen, die dem breiteren Team in Ihrer Organisation zur Verfügung zu stellen sind.
* **Beachten des Volumens freigegebener Assets:** Wenn Ihr Anwendungsfall die Asset-Verteilung ist, könnten Governance und Sicherheit die wichtigsten Aspekte sein. Erwägen Sie die Verwendung von Tools, die für eine skalierte Vorgehensweise entwickelt wurden, wie z. B. Brand Portal.
* **Wissenswertes über den Asset-Lebenszyklus:** Sie müssen wissen, welche Assets in Ihrer Organisation von den verschiedenen Teams genutzt werden.
* **Sorgfältige Verarbeitung häufiger Asset-Speichervorgänge:** Adobe Asset Link übernimmt diese Aufgabe für Sie – mit PS, AI und ID. Führen Sie für andere Programme keine laufenden Arbeitsaufgaben im zugeordneten/freigegebenen Ordner aus, es sei denn, Sie benötigen alle Änderungen in DAM.

### Zugreifen auf Adobe Stock Assets über AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

[Die Integration von AEM und Adobe Stock](/help/assets/aem-assets-adobe-stock.md) ermöglicht AEM-Anwendern die Suche, Vorschau, Lizenzierung und Speicherung von Assets aus Adobe Stock in AEM. Lizenzierte und gespeicherte Adobe Stock-Assets verfügen über ausgewählte Adobe Stock-Metadaten, mit denen Suchvorgänge über zusätzliche Filter durchgeführt werden können.

Einige wichtige Punkte zu dieser Integration:

* Wenn Assets aus Adobe Stock in AEM gespeichert werden, werden sie zu regulären AEM Assets. Die Binärdateien werden dabei im AEM-Repository gespeichert. Einige zu Adobe Stock gehörige Metadaten werden für das Asset in AEM gespeichert. Ansonsten verläuft die Erfassung wie bei jeder anderen Datei. Wenn beispielsweise Smart-Tags aktiv sind, werden die Tags beim Speichern diesen Assets hinzugefügt.
* Das in AEM gespeicherte Asset ist eine Kopie, kein Link zurück zu Adobe Stock.

**Arbeiten mit Assets in Creative Cloud, die aus Adobe Stock in AEM gespeichert wurden.** Diese Integration ist zwar unabhängig von Adobe Asset Link, aber Adobe Asset Link erkennt diese so aus Adobe Stock gespeicherten Assets und zeigt zusätzliche Metadaten sowie ein Adobe Stock-Symbol auf diesen Assets in der Adobe Asset Link-Erweiterungsoberfläche in Photoshop, Illustrator bzw. InDesign an. Die Dateien sind zum Durchsuchen, Öffnen usw. verfügbar, da sie durch Speichern in AEM zu regulären AEM Assets werden.
Kreative Benutzer, die in Creative Cloud-Programmen mit vorhandener Adobe Asset Link-Erweiterung arbeiten, haben zusätzlich zum Zugriff auf bereits lizenzierte Assets von Adobe Stock in AEM auch Zugriff auf das Creative Cloud Libraries-Bedienfeld, um Adobe Stock-Assets zu suchen, in einer Vorschau anzuzeigen und zu lizenzieren.
Lizenzierte und in AEM gespeicherte Assets aus Adobe Stock werden breiter gefassten Teams zur Verfügung gestellt, die auf die AEM Assets-Implementierung zugreifen. Kreative hingegen, die Assets aus Adobe Stock über das Creative Cloud Libraries-Bedienfeld lizenzieren, können sich die Assets selbst lediglich standardmäßig in ihrem Creative Cloud-Konto zur Verfügung stellen.

## Informationen zum Speichern von Assets in DAM {#about-storing-assets-in-a-dam}

Für das Entwickeln eines effizienten Workflows zwischen Kreativ-Teams und Marketing-/Branchen-Teams sowie für die Auswahl der besten Begleitfunktionen ist es wichtig zu verstehen, wann und warum Assets in DAM gespeichert werden.

### Warum Assets in DAM gespeichert werden   {#why-assets-are-stored-in-dam}

Das Speichern von Assets in DAM macht sie leicht zugänglich und auffindbar. Es wird sichergestellt, dass die Assets von verschiedenen Benutzern in der gesamten Organisation oder im gesamten System genutzt werden, z. B. von Kunden, Partnern usw.

Die meisten Organisationen entscheiden sich dafür, nur Assets zu speichern, die für nachgelagerte Marketing-/Branchenprozesse (Veröffentlichen in Kanälen wie dem Internet über AEM Sites oder anderen Kanälen wie Marketing Cloud oder Advertising Cloud, die von Adobe Experience Cloud bereitgestellt und von Analytics Cloud bewertet werden, Bereitstellung für Benutzer/Partner usw.) relevant sind. Außerdem speichern Organisationen Assets, für die möglicherweise ein Prüfungs-/Genehmigungsprozess in DAM erfolgt. Auf diese Weise werden hauptsächlich Assets in DAM gespeichert, die mit hoher Wahrscheinlichkeiten genutzt werden, und das Speichern von Assets im Leerlauf wird vermieden.

Die Speicherung von Assets hängt außerdem von Überlegungen zu technischen Aspekten und zur Ressourcennutzung ab. DAM bietet zusätzliche Services rund um gespeicherte Assets, darunter Extrahieren von Metadaten, Versionierung, Erstellen von Vorschauen/Transcodierung, Verwalten von Referenzen und Hinzufügen von Informationen zur Zugriffssteuerung. Diese Services erfordern zusätzlich Zeit und Infrastrukturressourcen.

Häufig ist das Speichern aller Assets und Aktualisierungen nicht empfehlenswert. Beispiel: Wenn Aktualisierungen von schlechter Qualität sind und einen unverhältnismäßigen Ressourcenverbrauch aufweisen, sollten die Assets nicht in DAM gespeichert werden.

#### Wann Assets in DAM gespeichert werden   {#when-assets-are-stored-in-dam}

Kreativ-Teams (und Organisationen) sind in der Regel nicht daran interessiert, Assets in jeder Phase des Asset-Lebenszyklus zu speichern. Beispielsweise vermeiden sie das Speichern von Assets in den folgenden Fällen:

* Assets, die noch nicht abgeschlossen sind, oder zum Experimentieren verwendet werden
* Assets, die den Prüfungszyklus des Kreativ-Teams/internen Teams nicht bestehen
* Verglichen mit dem betreffenden Asset verfügt das Team über bessere Beispiele für seine Arbeit, um sie externen Teams vorzustellen.

In der Regel werden Assets der folgenden Klassen in DAM gespeichert:

* Assets, die einen bestimmten Reifegrad erreicht haben und als bereit zur Freigabe für andere Benutzer gelten
* Assets, die vorab vom Kreativ-Team ausgewählt wurden
* Bestimmte Asset-Formate, die vom Marketing-Team verwendet werden können oder abhängig von einem bestimmten Vertrag bzw. einer Vereinbarung angefordert wurden (z. B. aus RAW-Dateien konvertierte JPG-Dateien, TIFF-Dateien/-Bilder aus PSD-Originaldateien)

#### Wann Aktualisierungen von Assets in DAM gespeichert werden   {#when-updates-to-assets-are-stored-in-dam}

In der Regel sollten nur Aktualisierungen von Assets in DAM gespeichert werden, die für den Großteil der DAM-Benutzer relevant sind. Dadurch wird sichergestellt, dass Benutzern (Marketing- und ähnliche Funktionen) in der DAM-Asset-Zeitleiste nur relevante Versionen angezeigt werden.

Normalerweise handelt es sich dabei um Änderungen in Bezug auf die wichtigsten Meilensteine im Asset-Lebenszyklus. Beispielsweise sollte das ursprüngliche fertige Marketing-Asset oder eine offizielle Aktualisierung basierend auf Anfragen/Überprüfungen durch das Kreativ-Team in DAM gespeichert und versioniert werden.

Die Aktualisierung des Kreativ-Teams zur Überprüfung durch das Marketing-Team nach einer Änderungsanfrage für ein vorhandenes Asset in DAM ist ein Beispiel für eine relevante Aktualisierung. Diese sollte als Referenzmaterial oder zum Zurücksetzen auf die letzte Version in DAM gespeichert und versioniert werden.

Es folgen Beispiele für Updates, die normalerweise nicht relevant sind:

* Frühe Versionen von Assets, die hochgeladen wurden, bevor sie für die Marketingüberprüfung bereit waren
* Häufige kreative Änderungen am Asset in der WIP-Phase, bevor die Kreativ- und Marketing-Teams das Asset für fertig erklären

### Benutzerzugriff auf DAM {#user-access-to-dam}

AEM Assets unterstützt zwei Arten von Benutzern, die auf deren Zugriff auf die AEM Assets-Implementierung basieren. Normalerweise haben Benutzer innerhalb des Unternehmensnetzwerks (Firewall) direkten Zugriff auf DAM. Andere Benutzer außerhalb des Unternehmensnetzwerks haben dagegen keinen direkten Zugriff. Der Benutzertyp bestimmt, welche Integrationen aus technischer Sicht verwendet werden können.

#### Kreative Benutzer mit direktem Zugriff auf DAM   {#creative-users-with-direct-access-to-dam}

In der Regel haben interne Kreativ-Teams oder Agenturen/Kreativprofis, die an das interne Netzwerk angeschlossen sind, Zugriff auf die DAM-Instanz, einschließlich AEM-Anmeldung. Die AEM- und Netzwerkinfrastruktur kann eingerichtet werden, um externen Parteien – normalerweise vertrauenswürdige Organisationen wie Agenturen, die für einen Kunden arbeiten – direkten Zugriff zu ermöglichen, damit diese über das Netzwerk (z. B. über VPN oder IP-Zulassungsliste) auf AEM zugreifen können

In solchen Fällen bietet Adobe Asset Link oder das AEM-Desktop-Programm einfachen Zugriff auf abgeschlossene/genehmigte Assets und ermöglicht das Speichern fertiger Kreativ-Assets in DAM.

#### Kreative Benutzer ohne Zugriff auf DAM {#creative-users-without-access-to-dam}

Externe Agenturen oder Freiberufler ohne direkten Zugriff auf die DAM-Instanz benötigen möglicherweise Zugriff auf genehmigte Assets oder möchten ihre neuen Designs in DAM hinzufügen.

Stellen Sie mit den folgenden Strategien Zugriff auf abgeschlossene/genehmigte Assets bereit:

* Verwenden des Desktop-Programms, wenn Asset Link nicht funktioniert.
* Verwenden von [AEM Assets Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html), um Assets sicher an externe Partner zu verteilen.
* Verwenden einer benutzerdefinierten Implementierung eines Verteilungs- und Quellportals basierend auf [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* Verwenden der in AEM eingerichteten Zugriffssteuerung und der erforderlichen Netzwerkinfrastruktur (z. B. VPN und IP-Zulassungsliste), um externen Parteien Zugriff auf einen speziellen Inhaltsbereich in Ihrem DAM-System zu gewähren. Sie können über die AEM-Web-Benutzeroberfläche Assets abrufen und neue Inhalte in Ihr DAM-System hochladen.

#### Laufende Arbeiten an Assets über AEM {#work-in-progress-on-assets-from-aem}

Wie in diesem Dokument erläutert, wird empfohlen, umfangreiche Aktualisierungen für Assets, auch als laufende Arbeiten bezeichnet, durchzuführen, ohne dass alle in der lokalen Datei gespeicherten Bearbeitungen ebenfalls als Änderungen in AEM hochgeladen wurden. Dies beschleunigt die Arbeit von Desktop-Benutzern, schränkt die verwendete Netzwerkbandbreite ein und sorgt dafür, dass die Assets-Zeitleiste „sauber“ bleibt und auf kontrollierte, größere Aktualisierungen ausgerichtet ist.

Adobe Asset Link bietet eine gute Unterstützung für dieses Nutzungsszenario:

* Wenn Benutzer in Photoshop, InDesign oder Illustrator eine Datei bearbeiten möchten, checken sie das jeweilige Asset aus.
* Das Asset wird im Hintergrund heruntergeladen, in die vom Creative Cloud-Desktop-Programme mit der Festplatte synchronisierten Creative Cloud-Konten der Benutzer platziert und das Checkout-Flag wird in AEM auf dem Asset umgeschaltet, um Bearbeitungskonflikte zu minimieren.
* Von diesem Zeitpunkt an arbeiten die Benutzer in einer Datei, die lokal am synchronisierten Speicherort abgelegt ist. Sie können weiterarbeiten und die erforderlichen Änderungen so oft wie gewünscht speichern.
* Da sich das Asset im Creative Cloud-Konto befindet, ist es auch auf etwaigen anderen Benutzergeräten verfügbar (z. B. zum Öffnen oder Bearbeiten in einer dedizierten Creative Cloud-Mobile-App). Außerdem kann es für andere Creative Cloud-Benutzer zwecks Zusammenarbeit freigegeben werden.
* Wenn kreative Benutzer keine weiteren Änderungen vornehmen möchten, können sie diese Datei in ihrem Creative Cloud-Programm mit einem optionalen Kommentar einchecken. Das entsprechende Asset in AEM wird versioniert und mit der neuen Binärdatei aktualisiert. AEM-Benutzer wie Marketer oder Branchenbenutzer haben über die Zeitleisten-Benutzeroberfläche von AEM Assets Zugriff auf wichtige Asset-Änderungen oder Meilensteine.

Das AEM-Desktop-Programm bietet eine Netzwerkfreigabe für in der nativen App geöffnete Assets. Standardmäßig werden alle lokalen Änderungen nach kurzer Zeit automatisch in AEM hochgeladen. Mit einer solchen Konfiguration werden häufig gespeicherte Inhalte während der laufenden Arbeit in AEM hochgeladen und versioniert, sodass beträchtlicher Netzwerkverkehr und potenzielle skalierbarkeitsbezogene Herausforderungen entstehen – ganz zu schweigen von den unnötigen Versionen in AEM.

In diesem Fall wird empfohlen, die AEM-Desktop-Programm-Option zum Deaktivieren automatischer Aktualisierungen zu verwenden und Asset-Änderungen manuell in AEM hochzuladen. Dabei wird die Aktion zum Hochladen von Assets in der Asset-Status-Benutzeroberfläche des Programms genutzt.

#### Massen-Upload in DAM {#bulk-upload-to-dam}

In einigen Szenarien müssen Sie möglicherweise eine größere Anzahl von Dateien gleichzeitig in DAM hochladen. Beispiele dafür sind:

* Hochladen der Ergebnisse von  Fotoshootings oder größeren Projekten
* Hochladen von Assets von Kreativagenturen
* Hochladen von Assets aus einem größeren Satz, wenn die Auswahl außerhalb von DAM erfolgt

Hinweis: Diese Beschreibung bezieht sich auf das betriebsbedingte Hochladen von Dateien (z. B. jede Woche oder bei jedem    Fotoshooting) als normaler Vorgang im Workflow eines Desktop-Benutzers. Das Migrieren großer Assets wird hier nicht behandelt.

Sie können die folgenden Upload-Funktionen nutzen:

* Um große/hierarchische Ordner stapelweise hochzuladen, verwenden Sie das AEM-Desktop-Programm mit Funktionen zum [Hochladen von Ordnern](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html#bulkupload). Sie können auch hierarchische Ordnerstrukturen hochladen. Das Hochladen von Assets erfolgt im Hintergrund und ist daher nicht an eine Webbrowser-Sitzung gebunden.
* Um einige Dateien aus einem einzelnen Ordner hochzuladen, ziehen Sie die Dateien direkt in die Weboberfläche oder verwenden Sie die Option „Erstellen“ in der Web-Benutzeroberfläche von AEM Assets.
* Je nach Ihren Geschäftsanforderungen können Sie auch benutzerdefinierte Upload-Programme verwenden.

#### Verwalten digitaler Assets direkt auf dem Desktop {#managing-digital-assets-directly-from-desktop}

Wenn Sie digitale Assets in Netzwerk-Dateifreigaben verwalten, kann stattdessen einfach die vom AEM-Desktop-Programm zugeordnete Netzwerkfreigabe verwendet werden. Beim Übergang von Netzwerk-Dateifreigaben stellt die Web-Benutzeroberfläche von AEM einen umfangreichen Satz von Digital-Asset-Management-Funktionen bereit, die weit über die Möglichkeiten einer Netzwerkfreigabe hinausgehen (Suche, Sammlungen, Metadaten, Zusammenarbeit, Vorschauen usw.). Außerdem bietet das AEM-Desktop-Programm einen praktischen Link zur Verbindung des Server-seitigen DAM-Repositorys mit Arbeiten auf dem Desktop.

Verwenden Sie das AEM-Desktop-Programm nicht für die direkte Verwaltung von Assets in der Netzwerkfreigabe von AEM Assets. Vermeiden Sie beispielsweise die Nutzung des AEM-Desktop-Programms zum Verschieben/Kopieren mehrerer Dateien. Verwenden Sie stattdessen die Web-Benutzeroberfläche von AEM Assets, um Ordner aus dem Finder/Explorer in die Netzwerkfreigabe zu ziehen, oder verwenden Sie die Funktion „Ordner hochladen“ von AEM Assets.

<!-- 
#### Asset migration {#asset-migration}

To plan and execute asset migrations from existing system to a new system or migration of large volume of assets stored on servers, see the [Migration Guide](/help/assets/assets-migration-guide.md). AEM desktop app and AEM to Creative Cloud integrations do not support such migrations. Due to the large volumes of assets to be ingested, and additional requirements around metadata mapping, transformation, and ingestion, migrations should be handled using different tools and approaches.
-->
