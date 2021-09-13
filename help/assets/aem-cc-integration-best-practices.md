---
title: Best Practices zur Integration mit  [!DNL Adobe Creative Cloud]
description: Best Practices für die Integration einer Experience Manager-Implementierung mit Adobe Creative Cloud zur Optimierung der Workflows zur Asset-Übertragung und zur Steigerung der Effizienz.
contentOwner: AG
mini-toc-levels: 1
feature: Collaboration,Adobe Asset Link,Desktop App
role: Architect,User,Admin
exl-id: cbed0d62-5148-45eb-b6a0-9fd164060fdc
source-git-commit: 0d0a3247e42e0f4a9b2965104814fe6bcd8e6128
workflow-type: tm+mt
source-wordcount: '3443'
ht-degree: 57%

---

# Best Practices für die Integration von Experience Manager und Adobe Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

Adobe Experience Manager Assets ist eine Digital Asset Management (DAM)-Lösung, die in Adobe Creative Cloud integriert werden kann, um DAM-Benutzer bei der Zusammenarbeit mit Kreativteams zu unterstützen und so die Zusammenarbeit beim Inhaltserstellungsvorgang zu optimieren.

Adobe Creative Cloud bietet Kreativ-Teams ein System von Lösungen und Services, um digitale Assets zu erstellen. Dieses Angebot enthält Desktop-Programme und Mobile Apps, Cloud-Services wie Speicher mit Desktop-Synchronisierung oder Web-Erlebnis sowie Marktplätze wie Adobe Stock.

Lesen Sie weiter, um mehr darüber zu erfahren, welche Integration Sie zwischen Desktop und DAM-Enterprise-System abhängig vom Nutzungsszenario und von den entsprechenden Best Practices für die Verbindungs-Workflows wählen sollten.

>[!NOTE]
>
>Die Ordnerfreigabe von Experience Managern zu Creative Clouden wird jetzt nicht mehr unterstützt und wird unten nicht mehr behandelt. Adobe empfiehlt neuere Funktionen wie Adobe Asset Link oder Experience Manager-Desktop-Programm, um kreativen Benutzern den Zugriff auf die in Experience Manager verwalteten Assets zu ermöglichen.

## Kooperationsanforderungen von Kreativen, Marketern und DAM-Benutzern {#collaboration-need-of-creatives-marketers-and-dam-users}

| Voraussetzungen | Nutzungsszenario | Betroffene Oberflächen |
|---|---|---|
| Vereinfachtes Desktop-Erlebnis für Kreative | Optimieren Sie den Zugriff auf Assets von einem DAM ([!DNL Assets]) für Kreativprofis oder, allgemeiner, für Desktop-Benutzer, die mit nativen Asset-Erstellungsanwendungen arbeiten. Sie benötigen eine einfache und unkomplizierte Möglichkeit, um Änderungen an Experience Manager zu finden, zu verwenden (zu öffnen), zu bearbeiten und zu speichern sowie neue Dateien hochzuladen. | Windows- oder Mac-Desktop, Creative Cloud-Programme |
| Bereitstellung hochwertiger, gebrauchsfertiger Assets von [!DNL Adobe Stock] | Marketer tragen zu einer schnelleren Inhaltserstellung bei, indem sie beim Beschaffen von und Suchen nach Assets helfen. Kreativprofis verwenden die genehmigten Assets direkt in ihren Kreativ-Tools. | [!DNL Assets];  [!DNL Adobe Stock] Marktplatz; Metadatenfelder |
| Verteilen und Freigeben von Assets nach Organisationen | Interne Abteilungen/Zweigstellen und externe Partner, Distributoren und Agenturen verwenden die genehmigten Assets, die von der übergeordneten Organisation freigegeben wurden. Die Organisation möchte die erstellten Assets sicher und nahtlos für eine größere Wiederverwendung freigeben. | [!DNL Brand Portal], [!DNL Asset Share Commons] |
| Vordefinierte Varianten hochgeladener Assets automatisch generieren | Automatische Verarbeitung von Assets mithilfe der einzigartigen Medien-Handling- und Transformationstechnologie von Adobe für vordefinierte Aktionen. Erstellen Sie eine benutzerdefinierte Logik, um Ihre eigenen Aktionen mithilfe von APIs und Asset-Microservices zu definieren. | Benutzeroberfläche von [!DNL Assets] |

## Adobe-Angebote zur Unterstützung von Kooperationsbedarf {#adobe-offerings-to-support-the-collaboration-need}

| Wertangebot für die betroffenen Benutzer | Adobe-Angebot | Betroffene Oberflächen |
|---|---|---|
| Kreative Benutzer können Assets aus [!DNL Experience Manager] entdecken, öffnen und verwenden, Änderungen bearbeiten und in [!DNL Experience Manager] hochladen sowie neue Dateien in [!DNL Experience Manager] hochladen, ohne ihre [!DNL Creative Cloud]-App verlassen zu müssen. | [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator und InDesign. |
| Geschäftsbenutzer vereinfachen das Öffnen und Verwenden von Assets, bearbeiten und laden Änderungen auf [!DNL Experience Manager] hoch und laden neue Dateien aus der Desktop-Umgebung in [!DNL Experience Manager] hoch. Sie nutzen eine generische Integration, um jeden Asset-Typ in nativen Desktop-Programmen, auch Adobe-fremden, zu öffnen. | [[!DNL Experience Manager] -Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de) | Experience Manager-Desktop-Programm auf einem Windows- und Mac-Desktop |
| Marketer und Geschäftsbenutzer können die Adobe Stock-Assets in Experience Manager entdecken, in der Vorschau anzeigen, lizenzieren, speichern und verwalten. Lizenzierte und gespeicherte Assets liefern ausgewählte Adobe Stock-Metadaten für eine bessere Governance. | [Integration von Experience Manager und Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] Webschnittstelle |
| Verbesserung der Zusammenarbeit zwischen Digital Product Designers und Marketing-Experten. Ermöglichen es Designern, die digitalen Assets in Design- und Wireframe-Modellen auf der Adobe XD-Arbeitsfläche zu verwenden. | [[!DNL Adobe Asset Link]  für  [!DNL Adobe XD]](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link-for-xd.html) | [!DNL Adobe XD] |
| Marketingexperten können automatisch Varianten und Derivate basierend auf hochgeladenen Assets und vordefinierten Aktionen erstellen, die mithilfe der Anpassung erstellt wurden. Verwenden Sie diese Automatisierung, um die Content-Geschwindigkeit zu erhöhen und den manuellen Aufwand zu reduzieren. | [Inhaltsautomatisierung](/help/assets/cc-api-integration.md) | [!DNL Experience Manager Assets] Webschnittstelle |

Dieser Artikel konzentriert sich in erster Linie auf die ersten beiden Aspekte der Zusammenarbeit. Die Verteilung und Beschaffung von Vermögenswerten im entsprechende Maß wird kurz als Verwendungsfall genannt. Für solche Lösungen sollten Sie Adobe Brand Portal oder Asset Share Commons beachten. Alternativlösungen wie [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), Lösungen, die basierend auf [Asset Share Commons](https://opensource.adobe.com/asset-share-commons/)-Komponenten erstellt werden können, [Linkfreigabe](share-assets.md). Die Verwendung der [Experience Manager Assets-Web-Benutzeroberfläche](/help/assets/manage-digital-assets.md) sollte basierend auf bestimmten Anforderungen überprüft werden.

![Creative Cloud-Verbindungen für Experience Manager: Festlegen der zu verwendenden Funktion](assets/creative-connections-aem.png)

Festlegen der zu verwendenden Funktion

### Zuordnen von Nutzungsszenarien und Adobe-Lösungen {#mapping-of-use-cases-and-adobe-solutions}

| Nutzungsszenario | Adobe Asset Link | Experience Manager-Desktop-Programm | Bemerkungen oder alternative Methoden |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Discover - Durchsuchen von Ordnern | Ja | Experience Manager-Web-Benutzeroberfläche + Desktop-Aktionen | Deaktivieren Sie beim Durchsuchen der Netzwerkfreigabe die Miniaturansichten, um das Herunterladen binärer Asset-Dateien zu vermeiden. |
| Discover - Zugriff auf Sammlungen | Ja | Experience Manager-Web-Benutzeroberfläche + Desktop-Aktionen |  |
| Discover - Suchen nach Assets | Ja | Experience Manager-Web-Benutzeroberfläche + Desktop-Aktionen |  |
| Verwenden – Öffnen von Assets | Ja | Ja – für jede App | [Öffnen über die Web-Benutzeroberfläche](/help/assets/manage-digital-assets.md#previewing-assets) oder den Finder |
| Verwenden - Platzieren eines Assets aus einem Experience Manager in ein Dokument | Ja – Einbetten | Ja – Verknüpfen oder Einbetten | Das Experience Manager-Desktop-Programm bietet Zugriff auf Assets als Dateien im lokalen Dateisystem. Diese Links in den nativen Programmen werden durch lokale Pfade dargestellt. |
| Bearbeiten – Öffnen zur Bearbeitung | Ja – Checkout-Aktion | Ja – Öffnen-Aktion (über die Netzwerkfreigabe) | Beim [Checkout in AAL](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) wird standardmäßig das Asset für das Creative Cloud-Speicherkonto des Benutzers (synchronisiert durch das Creative Cloud-Programm) gespeichert. |
| Bearbeiten - laufende Arbeiten außerhalb des Experience Managers | Ja – Asset im mit dem Desktop synchronisierten Creative Cloud-Speicherkonto des Benutzers verfügbar. | Ja |  |
| Bearbeiten – Hochladen von Änderungen | Ja – [Checkin-Aktion](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) mit optionalem Kommentar | Ja |  |
| Hochladen – einzelne Datei | Ja – Hochladen des aktuellen aktiven Dokuments | Ja | [Hochladen über die Web-Oberfläche](/help/assets/manage-digital-assets.md#uploading-assets) |
| Hochladen – mehrere Dateien/hierarchische Ordnerstrukturen | Nein | Ja | [Hochladen über die Web-Oberfläche](/help/assets/manage-digital-assets.md#uploading-assets); benutzerdefiniertes Skript oder Tool |
| Sonstiges – Benutzer und Anmeldung | Erkennung des Creative Cloud-Benutzers, der beim Creative Cloud-Desktop-Programm angemeldet ist (SSO) | Experience Manager/Login | Die Anwender beider Lösungen werden mit dem Benutzerkontingent des Experience Managers angerechnet. |
| Sonstiges – Netzwerk und Zugriff | Erfordert Zugriff vom Desktop des Benutzers auf die Bereitstellung von Experience Managern über das Netzwerk | Erfordert Zugriff vom Desktop des Benutzers auf die Bereitstellung von Experience Managern über das Netzwerk | Adobe Asset Link gibt keine Netzwerk-Proxy-Umgebung frei. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

Beachten Sie die folgenden Optionen, um Anwendungsfälle für die Asset-Verteilung zu unterstützen:

* [Experience Manager Assets Brand ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) Portal für ein konfigurierbares Add-on zu Assets zum Veröffentlichen von Assets.

* Benutzerdefinierte Lösungen, erstellt auf Grundlage der [Asset Share Commons](https://opensource.adobe.com/asset-share-commons/)-Code-Basis
* Experience Manager [Linkfreigabe](/help/assets/share-assets.md) zum Ad-hoc-Freigeben von Assets über Links.
* [Assets-Weboberfläche ](/help/assets/manage-digital-assets.md) mit Bereichen für externe Parteien, die durch die Einrichtung der Experience Manager-Zugriffssteuerung gesichert sind, und mit notwendigen IT-/Netzwerkkonfigurationsanpassungen, sodass diese externen Benutzer Zugriff auf Experience Manager haben.

## Grundlegende Konzepte und Nutzungsszenarien {#key-concepts-and-use-cases}

### Glossar der allgemeinen Begriffe {#glossary-of-common-terms}

* **Laufende Arbeit oder laufende kreative Arbeit (Work-In-Progress, WIP):** Eine Phase im Asset-Lebenszyklus, in der ein Asset mehrfach geändert wird und in der Regel noch nicht zur Freigabe für breitere Teams bereit ist.
* **Fertige Kreativ-Assets:** Assets, die für ein breiteres Team freigegeben werden können oder die vom Kreativ-Team für die Freigabe mit Marketing- oder LOB-Teams ausgewählt/genehmigt wurden.

* **Asset-Genehmigungen:** Der Genehmigungsprozess, der für Assets ausgeführt wird, die bereits auf DAM hochgeladen wurden. Dazu gehören in der Regel Markengenehmigungen, Genehmigungen usw.
* **Abgeschlossenes Asset:** Ein Asset, für das alle Genehmigungen/Metadaten-Tagging durchgeführt wurden und das bereit für die Verwendung durch das breitere Team ist. Ein solches Asset wird in DAM gespeichert und allen (bzw. allen interessierten) Benutzern zur Verfügung gestellt. Es kann in Marketing-Kanälen oder von Kreativ-Teams verwendet werden, um Designs zu erstellen.

* **Kleinere Asset-Aktualisierung/-Änderung:** Schnelle, kleine Änderung an einem digitalen Asset. Diese wird häufig aufgrund einer Retuschieranfrage oder einer kleineren Bearbeitungsanfrage, einer Asset-Überprüfung oder einer Genehmigung (z. B. Neupositionierung, Änderung der Textgröße, Anpassung der Sättigung/Helligkeit, Farbe usw.) durchgeführt.
* **Größere Asset-Aktualisierung/-Änderung:** Änderung eines digitalen Assets, die viel Arbeit erfordert und manchmal über einen längeren Zeitraum erfolgen muss. Diese umfasst in der Regel mehrere Änderungen. Das Asset muss während der Aktualisierung mehrmals gespeichert werden. Bei umfangreichen Asset-Aktualisierungen wird das Asset in der Regel in eine WIP-Phase versetzt.
* **DAM:** Digital Asset Management. In diesem Dokument wird der Begriff synonym mit Experience Manager-Assets verwendet, sofern nicht ausdrücklich anders angegeben.
* **Kreativer Benutzer:** Kreativprofi, der digitale Assets mit Creative Cloud-Programmen und -Services erstellt. In einigen Fällen kann ein kreativer Benutzer Mitglied eines Kreativ-Teams sein, das möglicherweise Creative Cloud verwendet, aber keine digitalen Assets erstellt (z. B. Creative Director oder Creative Team Manager).
* **DAM-Benutzer:** Ein typischer Benutzer eines DAM-Systems. Je nach Organisation kann ein DAM-Benutzer ein Marketing- oder Nicht-Marketing-Benutzer sein, z. B. Branchenbenutzer, Bibliothekar, Vertriebsmitarbeiter usw.

### Überlegungen zur Integration von Experience Manager und Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Dies ist eine kurze Zusammenfassung der Best Practices für die Integration von Experience Manager und Creative Cloud. Lesen Sie den Rest dieses Dokuments, um detaillierte Informationen dazu zu erhalten.

* **Für kreative Benutzer, die in Photoshop, InDesign oder Illustrator arbeiten:**  Adobe Asset Link bietet das beste Benutzererlebnis, einschließlich der ordnungsgemäßen Handhabung der laufenden Arbeiten an Assets, die von Experience Manager ausgecheckt wurden
* **Zum Vereinfachen des Zugriffs auf Assets vom Desktop aus für beliebige allgemeine Dateiformate oder Anwendungen:**  Verwenden Sie das Experience Manager-Desktop-Programm
* **Verstehen, warum und wann Assets in DAM gespeichert werden:** Aktualisierungen, die dem breiteren Team in Ihrer Organisation zur Verfügung zu stellen sind.
* **Beachten des Volumens freigegebener Assets:** Wenn Ihr Anwendungsfall die Asset-Verteilung ist, könnten Governance und Sicherheit die wichtigsten Aspekte sein. Erwägen Sie die Verwendung von Tools, die für eine skalierte Vorgehensweise entwickelt wurden, wie z. B. Brand Portal.
* **Wissenswertes über den Asset-Lebenszyklus:** Sie müssen wissen, welche Assets in Ihrer Organisation von den verschiedenen Teams genutzt werden.
* **Sorgfältige Verarbeitung häufiger Asset-Speichervorgänge:** Adobe Asset Link übernimmt diese Aufgabe für Sie – mit PS, AI und ID. Führen Sie für andere Programme keine laufenden Arbeitsaufgaben im zugeordneten/freigegebenen Ordner aus, es sei denn, Sie benötigen alle Änderungen in DAM.

### Zugriff auf Adobe Stock-Assets über Experience Manager Assets {#access-to-adobe-stock-assets-from-aem-assets}

[Die Experience Manager- und Adobe Stock-](/help/assets/aem-assets-adobe-stock.md) Integration bietet Experience Manager die Möglichkeit, Assets aus Adobe Stock in Experience Manager zu suchen, in der Vorschau anzuzeigen, zu lizenzieren und zu speichern. Lizenzierte und gespeicherte Adobe Stock-Assets verfügen über ausgewählte Adobe Stock-Metadaten, mit denen Suchvorgänge über zusätzliche Filter durchgeführt werden können.

Einige wichtige Punkte zu dieser Integration:

* Wenn Assets aus dem Adobe-Bestand auf dem Experience Manager gespeichert werden, werden sie zu regulären Experience Manager-Assets, wobei die Binärdatei im Experience Manager-Repository gespeichert wird. Einige mit Adobe Stock verknüpfte Metadaten werden für das Asset in Experience Manager gespeichert. Andernfalls sieht der Aufnahmevorgang genauso aus wie für jede andere Datei. Wenn beispielsweise Smart-Tags aktiv sind, werden die Tags beim Speichern diesen Assets hinzugefügt.
* Das in Experience Manager gespeicherte Asset ist eine Kopie, kein Link zurück zu Adobe Stock.

**Arbeiten mit Assets, die aus Adobe Stock in Experience Manager gespeichert wurden, in Creative Cloud**. Diese Integration ist zwar unabhängig von Adobe Asset Link, aber Adobe Asset Link erkennt diese so aus Adobe Stock gespeicherten Assets und zeigt zusätzliche Metadaten sowie ein Adobe Stock-Symbol auf diesen Assets in der Adobe Asset Link-Erweiterungsoberfläche in Photoshop, Illustrator bzw. InDesign an. Die Dateien stehen zum Durchsuchen, Öffnen usw. zur Verfügung, da es sich bei ihnen um normale Experience Manager-Assets handelt, wenn sie in Experience Manager gespeichert werden.
Kreative Benutzer, die in Creative Cloud-Apps mit vorhandener Adobe Asset Link-Erweiterung arbeiten, können nicht nur auf bereits lizenzierte Assets von Adobe Stock in Experience Manager zugreifen, sondern auch das Bedienfeld Creative Cloud-Bibliotheken verwenden, um Adobe Stock-Assets zu suchen, in einer Vorschau anzuzeigen und zu lizenzieren.
Assets aus Adobe Stock, die lizenziert und in Experience Manager gespeichert sind, stehen breiter gefassten Teams zur Verfügung, die auf die Bereitstellung von Experience Manager Assets zugreifen. Kreative hingegen, die Assets aus Adobe Stock über das Bedienfeld Creative Cloud-Bibliotheken lizenzieren, stellen sie sich selbst nur standardmäßig in ihrem Creative Cloud-Konto zur Verfügung.

## Informationen zum Speichern von Assets in DAM {#about-storing-assets-in-a-dam}

Für das Entwickeln eines effizienten Workflows zwischen Kreativ-Teams und Marketing-/Branchen-Teams sowie für die Auswahl der besten Begleitfunktionen ist es wichtig zu verstehen, wann und warum Assets in DAM gespeichert werden.

### Warum Assets in DAM gespeichert werden {#why-assets-are-stored-in-dam}

Das Speichern von Assets in DAM macht sie leicht zugänglich und auffindbar. Es wird sichergestellt, dass die Assets von verschiedenen Benutzern in der gesamten Organisation oder im gesamten System genutzt werden, z. B. von Kunden, Partnern usw.

Die meisten Unternehmen speichern nur Assets, die für nachgelagerte Marketing-/LOB-Prozesse relevant sind (Veröffentlichung in Kanälen wie Webkanälen über Experience Manager-Sites oder andere von Adobe Experience Cloud bereitgestellte Kanäle - Marketing Cloud, Advertising Cloud, gemessen von Analytics Cloud, Bereitstellung für Benutzer/Partner usw.). Außerdem speichern Organisationen Assets, für die möglicherweise ein Prüfungs-/Genehmigungsprozess in DAM erfolgt. Auf diese Weise werden hauptsächlich Assets in DAM gespeichert, die mit hoher Wahrscheinlichkeiten genutzt werden, und das Speichern von Assets im Leerlauf wird vermieden.

Die Speicherung von Assets hängt außerdem von Überlegungen zu technischen Aspekten und zur Ressourcennutzung ab. DAM bietet zusätzliche Services rund um gespeicherte Assets, darunter Extrahieren von Metadaten, Versionierung, Erstellen von Vorschauen/Transcodierung, Verwalten von Referenzen und Hinzufügen von Informationen zur Zugriffssteuerung. Diese Services erfordern zusätzlich Zeit und Infrastrukturressourcen.

Häufig ist das Speichern aller Assets und Aktualisierungen nicht empfehlenswert. Beispiel: Wenn Aktualisierungen von schlechter Qualität sind und einen unverhältnismäßigen Ressourcenverbrauch aufweisen, sollten die Assets nicht in DAM gespeichert werden.

#### Wann Assets in DAM gespeichert werden {#when-assets-are-stored-in-dam}

Kreativ-Teams (und Organisationen) sind in der Regel nicht daran interessiert, Assets in jeder Phase des Asset-Lebenszyklus zu speichern. Beispielsweise vermeiden sie das Speichern von Assets in den folgenden Fällen:

* Assets, die noch nicht abgeschlossen sind, oder zum Experimentieren verwendet werden
* Assets, die den Prüfungszyklus des Kreativ-Teams/internen Teams nicht bestehen
* Verglichen mit dem betreffenden Asset verfügt das Team über bessere Beispiele für seine Arbeit, um sie externen Teams vorzustellen.

In der Regel werden Assets der folgenden Klassen in DAM gespeichert:

* Assets, die einen bestimmten Reifegrad erreicht haben und als bereit zur Freigabe für andere Benutzer gelten
* Assets, die vorab vom Kreativ-Team ausgewählt wurden
* Bestimmte Asset-Formate, die vom Marketing-Team verwendet werden können oder abhängig von einem bestimmten Vertrag bzw. einer Vereinbarung angefordert wurden (z. B. aus RAW-Dateien konvertierte JPG-Dateien, TIFF-Dateien/-Bilder aus PSD-Originaldateien)

#### Wann Aktualisierungen von Assets in DAM gespeichert werden {#when-updates-to-assets-are-stored-in-dam}

In der Regel sollten nur Aktualisierungen von Assets in DAM gespeichert werden, die für den Großteil der DAM-Benutzer relevant sind. Dadurch wird sichergestellt, dass Benutzern (Marketing- und ähnliche Funktionen) in der DAM-Asset-Zeitleiste nur relevante Versionen angezeigt werden.

Normalerweise handelt es sich dabei um Änderungen in Bezug auf die wichtigsten Meilensteine im Asset-Lebenszyklus. Beispielsweise sollte das ursprüngliche fertige Marketing-Asset oder eine offizielle Aktualisierung basierend auf Anfragen/Überprüfungen durch das Kreativ-Team in DAM gespeichert und versioniert werden.

Die Aktualisierung des Kreativ-Teams zur Überprüfung durch das Marketing-Team nach einer Änderungsanfrage für ein vorhandenes Asset in DAM ist ein Beispiel für eine relevante Aktualisierung. Diese sollte als Referenzmaterial oder zum Zurücksetzen auf die letzte Version in DAM gespeichert und versioniert werden.

Es folgen Beispiele für Updates, die normalerweise nicht relevant sind:

* Frühe Versionen von Assets, die hochgeladen wurden, bevor sie für die Marketingüberprüfung bereit waren
* Häufige kreative Änderungen am Asset in der WIP-Phase, bevor die Kreativ- und Marketing-Teams das Asset für fertig erklären

### Benutzerzugriff auf DAM {#user-access-to-dam}

Experience Manager Assets unterstützt zwei Benutzertypen, die auf dem Zugriff auf die Experience Manager Assets-Bereitstellung basieren. Normalerweise haben Benutzer innerhalb des Unternehmensnetzwerks (Firewall) direkten Zugriff auf DAM. Andere Benutzer außerhalb des Unternehmensnetzwerks haben dagegen keinen direkten Zugriff. Der Benutzertyp bestimmt, welche Integrationen aus technischer Sicht verwendet werden können.

#### Kreative Benutzer mit direktem Zugriff auf DAM {#creative-users-with-direct-access-to-dam}

Normalerweise haben interne Kreativteams oder Agenturen/Kreativprofis, die in das interne Netzwerk im internen Netzwerk integriert sind, haben Zugriff auf die DAM-Instanz, einschließlich der Anmeldung von Experience Managern. Experience Manager- und Netzwerkinfrastruktur können eingerichtet werden, um externen Parteien - normalerweise vertrauenswürdige Organisationen wie Agenturen, die für einen Kunden arbeiten - direkten Zugriff zu ermöglichen, damit diese über das Netzwerk, z. B. über VPN oder IP-Zulassungsliste, auf Experience Manager zugreifen können.

In solchen Fällen ermöglicht Adobe Asset Link oder das Experience Manager-Desktop-Programm einen einfachen Zugriff auf abgeschlossene/genehmigte Assets und das Speichern von fertigen Kreativ-Assets in DAM.

#### Kreative Benutzer ohne Zugriff auf DAM {#creative-users-without-access-to-dam}

Externe Agenturen oder Freiberufler ohne direkten Zugriff auf die DAM-Instanz benötigen möglicherweise Zugriff auf genehmigte Assets oder möchten ihre neuen Designs in DAM hinzufügen.

Stellen Sie mit den folgenden Strategien Zugriff auf abgeschlossene/genehmigte Assets bereit:

* Verwenden des Desktop-Programms, wenn Asset Link nicht funktioniert.
* Verwenden Sie [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), um Assets sicher an externe Partner zu verteilen.
* Verwenden einer benutzerdefinierten Implementierung eines Verteilungs- und Quellportals basierend auf [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* Verwenden Sie die Zugriffssteuerung, die in Experience Manager eingerichtet ist, und die erforderliche Netzwerkinfrastruktur (z. B. VPN und IP-Zulassungsauflistung), um externen Parteien Zugriff auf einen speziellen Inhaltsbereich in Ihrem DAM zu gewähren. Sie können die Experience Manager-Web-Benutzeroberfläche verwenden, um Assets abzurufen und neue Inhalte in Ihr DAM hochzuladen.

#### Laufende Arbeiten an Assets vom Experience Manager {#work-in-progress-on-assets-from-aem}

Wie in diesem Dokument erläutert, wird empfohlen, umfangreiche Aktualisierungen für Assets durchzuführen, die manchmal als laufende Arbeit bezeichnet werden, ohne dass alle in der lokalen Datei gespeicherten Änderungen ebenfalls als Änderungen in Experience Manager hochgeladen werden. Dies beschleunigt die Arbeit von Desktop-Benutzern, schränkt die verwendete Netzwerkbandbreite ein und sorgt dafür, dass die Assets-Zeitleiste „sauber“ bleibt und auf kontrollierte, größere Aktualisierungen ausgerichtet ist.

Adobe Asset Link bietet eine gute Unterstützung für dieses Nutzungsszenario:

* Wenn Benutzer in Photoshop, InDesign oder Illustrator eine Datei bearbeiten möchten, checken sie das jeweilige Asset aus.
* Das Asset wird im Hintergrund heruntergeladen, in das Benutzerkonto Creative Cloud übertragen, das vom Creative Cloud-Desktop-Programm auf die Festplatte synchronisiert wird, und das Checkout-Flag wird im Experience Manager zum Asset umgeschaltet, um Bearbeitungskonflikte zu minimieren
* Von diesem Zeitpunkt an arbeiten die Benutzer in einer Datei, die lokal am synchronisierten Speicherort abgelegt ist. Sie können weiterarbeiten und die erforderlichen Änderungen so oft wie gewünscht speichern.
* Da sich das Asset im Creative Cloud-Konto befindet, ist es auch auf etwaigen anderen Benutzergeräten verfügbar (z. B. zum Öffnen oder Bearbeiten in einer dedizierten Creative Cloud-Mobile-App). Außerdem kann es für andere Creative Cloud-Benutzer zwecks Zusammenarbeit freigegeben werden.
* Wenn kreative Benutzer keine weiteren Änderungen vornehmen möchten, können sie diese Datei in ihrem Creative Cloud-Programm mit einem optionalen Kommentar einchecken. Das entsprechende Asset in Experience Manager wird versioniert und mit der neuen Binärdatei aktualisiert. Experience Manager-Benutzer wie Marketingexperten oder LOB-Benutzer haben über die Experience Manager-Asset-Timeline-Benutzeroberfläche Zugriff auf wichtige Asset-Änderungen oder Meilensteine.

Das Experience Manager-Desktop-Programm bietet eine Netzwerkfreigabe für Assets, die im nativen Programm geöffnet wurden. Standardmäßig werden alle lokal vorgenommenen Änderungen nach kurzer Zeit automatisch in Experience Manager hochgeladen. Mit einer solchen Konfiguration würden häufige Speichervorgänge während der laufenden Phase in den Experience Manager hochgeladen und versioniert, was zu einer Menge Netzwerkverkehr und potenziellen Skalierbarkeitsproblemen führt - ganz zu schweigen von unnötigen Versionen im Experience Manager.

Hier wird empfohlen, eine Option im Experience Manager-Desktop-Programm zu verwenden, um automatisierte Aktualisierungen zu deaktivieren und Asset-Änderungen manuell in den Experience Manager hochzuladen. Dabei wird die Aktion zum Hochladen von Änderungen in der Asset-Status-Benutzeroberfläche des Programms genutzt.

#### Massen-Upload in DAM {#bulk-upload-to-dam}

In einigen Szenarien müssen Sie möglicherweise eine größere Anzahl von Dateien gleichzeitig in DAM hochladen. Beispiele dafür sind:

* Hochladen der Ergebnisse von Fotoshootings oder größeren Projekten
* Hochladen von Assets von Kreativagenturen
* Hochladen von Assets aus einem größeren Satz, wenn die Auswahl außerhalb von DAM erfolgt

Hinweis: Diese Beschreibung bezieht sich auf das betriebsbedingte Hochladen von Dateien (z. B. jede Woche oder bei jedem Fotoshooting) als normaler Vorgang im Workflow eines Desktop-Benutzers. Das Migrieren großer Assets wird hier nicht behandelt.

Sie können die folgenden Upload-Funktionen nutzen:

* Um große/hierarchische Ordner stapelweise hochzuladen, verwenden Sie das Experience Manager-Desktop-Programm mit der Funktion [Ordner-Upload](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#bulk-upload-assets) . Sie können auch hierarchische Ordnerstrukturen hochladen. Das Hochladen von Assets erfolgt im Hintergrund und ist daher nicht an eine Webbrowser-Sitzung gebunden.
* Um einige Dateien aus einem einzigen Ordner hochzuladen, ziehen Sie die Dateien direkt auf die Web-Oberfläche oder verwenden Sie die Option Erstellen in der Experience Manager Assets-Web-Benutzeroberfläche.
* Je nach Ihren Geschäftsanforderungen können Sie auch benutzerdefinierte Upload-Programme verwenden.

#### Verwalten digitaler Assets direkt auf dem Desktop {#managing-digital-assets-directly-from-desktop}

Wenn Sie digitale Assets mit Netzwerk-Dateifreigaben verwalten, können Sie die vom Experience Manager-Desktop-Programm zugeordnete Netzwerkfreigabe einfach als bequemen Ersatz verwenden. Beim Übergang von der Freigabe von Netzwerkdateien bietet die Experience Manager-Web-Oberfläche eine umfangreiche Auswahl an Digital-Asset-Management-Funktionen, die weit über die Möglichkeiten einer Netzwerkfreigabe hinausgehen (Suche, Sammlungen, Metadaten, Zusammenarbeit, Vorschau usw.). Das Experience Manager-Desktop-Programm bietet einen praktischen Link, um das serverseitige DAM-Repository mit der Arbeit auf dem Desktop zu verbinden.

Vermeiden Sie die Verwendung des Experience Manager-Desktop-Programms zum Verwalten von Assets direkt in der Netzwerkfreigabe von Experience Manager Assets. Vermeiden Sie beispielsweise die Verwendung des Experience Manager-Desktop-Programms zum Verschieben/Kopieren mehrerer Dateien. Verwenden Sie stattdessen die Web-Benutzeroberfläche von Experience Manager Assets , um Ordner aus dem Finder/Explorer in die Netzwerkfreigabe zu ziehen, oder verwenden Sie die Funktion Experience Manager Assets-Ordner-Upload .
