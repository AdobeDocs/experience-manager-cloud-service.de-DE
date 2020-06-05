---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.6.0
description: Versionshinweise für Experience Manager 2020.6.0
translation-type: tm+mt
source-git-commit: 41684858f1fe516046b9601c1d869fff180320e0
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 6%

---


# Versionshinweise für AEM as a Cloud Service 2020.6.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.6.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.6.0 is June 04, 2020.

## What&#39;s New in AEM Sites {#aem-sites}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für AEM-Sites in AEM als Cloud-Service-Version 2020.6.0.

### Neuerungen {#whats-new-2020.6.0}

Version 2.9.0 der [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) ist jetzt als Teil von AEM-Sites verfügbar, einschließlich:

* Integration zwischen [Adobe Client Data Layer](https://github.com/adobe/adobe-client-data-layer) und den Kernkomponenten
* Konfigurierbare HTML-ID-Attribute für alle Komponenten
* Eine neue Statusleistenkomponente
* Viele Fehlerbehebungen

### Fehlerbehebungen {#sites-bug-fixes}

* Komponenten im Layout-Container sind nicht sichtbar, wenn Layout-Container kopiert und erneut auf eine Seite eingefügt wird.

* Problem mit der Größenanpassung der Layoutkomponente behoben.

* Zusätzliche Funktion zum Verwalten von Routing-Angular-Seiten und AEM/Angular-Seiten.

### Barrierefreiheit {#accessibility}

* Narratier-Rolle und -Status sind jetzt für die Mauerelemente im Dialogfeld Seite **erstellen** möglich, während Sie mit dem Pfeil nach unten im Durchsuchenmodus navigieren.

* Es wurde ein Link zur Navigation hinzugefügt, über den Benutzer zum Hauptinhalt navigieren können.

* Verbesserungen an Bildschirmlesehilfen.


## Neue Funktionen in AEM-Stiftungen als Cloud-Dienst {#foundations}

Die Buildzeit von AEM-Projekten wird dadurch verbessert, dass alle Verweise in der Datei &quot;pom.xml&quot;des AEM-Projekts auf das Remote-Repository entfernt werden `https://downloads.experiencecloud.adobe.com/content/maven/public`.

Das AEM als Cloud Service SDK API-Jar, das zuvor an diesem Speicherort gehostet wurde, befindet sich jetzt in Maven Central, dem Standard-Artefakt-Repository von Maven.

## Neue Funktionen in Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in Version 2020.6.0 von AEM as a Cloud Service.

### Neuerungen {#what-is-new-cloud-manager}

* Benutzer, die in Cloud Manager die Rolle &quot; *Geschäftsinhaber* &quot;verwenden, können jetzt ein Sandbox-Programm aus der Landingpage (über die Schaltfläche &quot;Schnellaktion&quot;auf der Programm-Karte) oder aus dem Programm löschen.

   Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) .

* Sandbox-Programm-Benutzer in *Business Owner* oder *Deployment Manager* -Rolle in Cloud Manager können ihre Produktions- und Stage-Umgebung jetzt über die Benutzeroberfläche von Cloud Manager löschen. Die Option zum Löschen steht jetzt sowohl auf der Seite &quot;Übersicht über die **Programme&quot;als auch auf der Seite &quot;Umgebung** &quot; **Umgebung** zur Verfügung. Wenn Sie die Option zum Löschen entweder auf der Produktions- oder der Stufe auswählen, wird auch die andere Option im Satz gelöscht.

   Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) .

* Coach Markierungen auf der Landingpage, um den Benutzer über die grundlegende Navigation zu informieren und zu informieren.

* Coach-Markierungen auf der Seite &quot; **Programm-Übersicht** &quot;, um den Benutzer über die grundlegende Navigation innerhalb von Cloud Manager zu informieren und ihn zu informieren, um ihn zu starten.

* In Cloud Manager steht jetzt eine **LEARN** -Seite zur Verfügung, die über die Navigation oben aufgerufen werden kann. Diese Seite enthält Ressourcen, die Benutzern dabei helfen, sich über die am häufigsten verwendeten Arbeitsabläufe zu informieren, je nachdem, welche Rollen ihnen in Cloud Manager zugewiesen wurden.

* Sandbox-Programm werden jetzt mit einem **Sandbox** -Zeichen identifiziert, das auf der Programm-Karte auf der Landingpage sowie neben dem Programm-Namen auf der Seite &quot; **Programm-Übersicht** &quot;angezeigt wird.

* Ein Benutzer in der SysAdmin-Rolle hat jetzt einen 1-Klick-Zugriff auf den Speicherort in der Admin-Konsole, von dem aus Benutzerrollen oder Berechtigungen für Cloud Manager verwaltet werden können. Auf der Landingpage neben der Schaltfläche &quot; **Hinzufügen Programm** &quot;steht jetzt eine Schaltfläche &quot;Zugriff **** verwalten&quot;zur Verfügung.

   Weitere Informationen finden Sie in den [SysAdmin-Aufgaben](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) .

* Ein Benutzer in der SysAdmin-Rolle hat jetzt einen 1-Klick-Zugriff auf die Autoreninstanz direkt aus Cloud Manager.

   Weitere Informationen finden Sie unter Zugriff auf Autoreninstanz [verwalten](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) .

* Das Build-Protokoll enthält jetzt die Liste der entdeckten Artefakte, einschließlich übersprungener Inhaltspakete.

* Der Schritt Erstellen überprüft jetzt, ob alle erstellten Inhaltspakete alle obligatorischen Eigenschaften enthalten - Name, Gruppe und Version.

* Der Schritt Erstellen überprüft jetzt, ob der Build mindestens ein Inhaltspaket erstellt hat.

### Fehlerbehebungen {#bug-fixes-cm}

* Unter bestimmten Umständen wurden die Symbole im Dialogfeld &quot;Programm **erstellen** &quot;falsch ausgerichtet.

* Die AEM-Versionshinweise wurden nicht einheitlich auf der Seite &quot; **Programme - Übersicht** &quot;angezeigt.

* Bei der Konfiguration der Produktionsleitung war die Option **Geplante Bereitstellung** für einige Kunden nicht sichtbar.

### Bekannte Probleme {#known-issues-cm}

* Umgebung innerhalb eines Sandbox-Programms werden ausgeblendet, wenn für einen bestimmten Zeitraum keine Aktivität erkannt wird. Dieser Status wird in Cloud Manager nicht beobachtet. Der Status kann jedoch über die Developer Console beobachtet werden. Dies wird in einer kommenden Version behandelt.

* Der Link zur Developer Console direkt aus Cloud Manager zeigt die Option zum Deaktivieren/Entfernen der Umgebung eines Sandbox-Programms nicht an. Um dies zu beheben, fügen Sie in der Developer Console einmal das Muster `#release-cm-p1234-e5678` zum Ende der URL hinzu, wobei *1234* die Programm-ID und *5678* die Umgebung-ID ist. Dies wird in einer kommenden Version behandelt.

## Neue Funktionen in Version  [!DNL Adobe Experience Manager Assets]{#aem-assets}

<!-- 
Assets RNs are being authored and are a work in progress.
PM/EM review required before publishing.
-->

**Benutzerfreundlichkeit für erweiterte Smart-Tags mit Adobe Sensei**

Mit erweiterten intelligenten Tags können Unternehmen intelligente Tagging-Modelle schulen, um Bilder zu erkennen, die auf kundenspezifischen Tags basieren, und zwar zusätzlich zu generischen Smart-Tags.

Mit dieser Version gibt es eine neue, geführte Benutzererfahrung, die bei der Einrichtung von Smart-Tags-Schulungen für Sätze kundenspezifischer Tags und deren Schulung mit Assets hilft, die in Zukunft erkannt und mit Tags versehen werden sollten. Dies ist eine intuitivere Erfahrung.
Train Enhanced Smart Tags für eine intuitive Schulung zu intelligenten Tags. Erfahren Sie, [wie intelligente Tags](/help/assets/smart-tags.md) erstellt und [konfiguriert werden können](/help/assets/smart-tags-configuration.md).

**Unterstützung der Erfassung, Vorschau und Versand von 3D-Inhalten**

Organisationen können jetzt 3D-Dateien in AEM Assets speichern und verwenden. Benutzer können eine Vielzahl von Kern-3D-Dateien hochladen, Vorschauen vornehmen und nutzen, einschließlich .obj-, .stl-, .gltf- und .glb-Dateien. Zusätzlich [!DNL Dynamic Media]können 3D-Erlebnisse über agnostische URLs oder Viewer konfiguriert und bereitgestellt werden. Dazu gehören ein [!DNL Dynamic Media] 3D-Experience Viewer, die Sites-3D-Viewer-Komponente und die Möglichkeit, 3D-Dateien über [!DNL Dynamic Media] (AR/VR) bereitzustellen. Siehe [Arbeiten mit 3D-Assets in dynamischen Medien](/help/assets/dynamic-media/assets-3d.md).

<!-- Hiding this as the GA is at a later date. 
**Adobe Asset Link support for Adobe XD**

With the latest release, [!DNL Experience Manager Assets] provides support for a new [!DNL Adobe Asset Link] plug-in that is released with [!DNL Adobe XD] v29. The integration allows designers to access and use assets from [!DNL Experience Manager] in their designs, without the need to leave [!DNL Adobe XD] application. See [Adobe Asset Link documentation](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).
-->

**Verbesserungen der Barrierefreiheit**

[!DNL Adobe Experience Manager Assets] ist nun in Übereinstimmung mit den Richtlinien der Web Content Accessibility Guidelines (WCAG) v2.1 leichter zugänglich. Die Barrierefreiheit wurde für folgende Anwendungsfälle oder Schnittstellen verbessert:

* Benutzeroberflächenelemente, Steuerelemente, Seiten und Dialoge sind für Bildschirmlesehilfen benutzerfreundlich.
* Auf Benutzeroberflächenelemente, Steuerelemente und Eingabefelder kann über die Tastatur zugegriffen werden.
* Änderung der Farbe oder des Kontrasts einiger Oberflächenelemente, um diese für Benutzer mit eingeschränkter Sicht und ohne Farbwahrnehmung leichter erkennbar zu machen. Beispielsweise weist Assets jetzt einen angemessenen Kontrast in den Bewertungssymbole für Stern auf der Seite &quot; [!UICONTROL Eigenschaften] &quot;und in der Ansicht &quot;Karten&quot;auf.

**Weitere Verbesserungen**

Die Version bietet die folgenden zusätzlichen Verbesserungen:

* Möglichkeit zur Neuverarbeitung von Assets mit Profilen zur Asset-Verarbeitung, sodass die Benutzer die volle Kontrolle über den Prozess haben (vollständige Asset-Verarbeitung ausführen, nur spezifisches Profil anwenden und entscheiden können, ob der Nachbearbeitungsvorgang ausgeführt werden soll).
* Suchergebnisse werden jetzt schneller zurückgegeben, wenn die zugrunde liegende Clusterinstanz hinter den Kulissen neu gestartet wurde (in einem solchen Fall könnte die anfängliche Suche länger dauern).
* Sortieren Sie Assets nach &quot;Name&quot;, wenn Sie Assets in der Ansicht &quot;Liste&quot;in der Benutzeroberfläche &quot;Assets&quot;und in den Suchergebnissen anzeigen. Siehe [Suchen von Assets](/help/assets/search-assets.md#sort).
* Sortieren Sie nach &quot;Erstellt&quot;(Datum), wenn Sie Assets in der Ansicht &quot;Liste&quot;in der Assets-Oberfläche und in den Suchergebnissen anzeigen. Siehe [Suchen von Assets](/help/assets/search-assets.md#sort).
* Unterstützung für die Konvertierung von EPS-Dateien in Bilder mithilfe von Asset Microservices.

### Fehlerbehebungen {#assets-bug-fixes}

<!-- TBD: Add enhancements above and bug fixes below.
Seek DM bug fixes if any.
Add Nui update as shared on Slack: https://git.corp.adobe.com/nui/app/releases/tag/22
-->

Zusätzlich zu den oben genannten neuen Funktionen bietet die aktuelle Version die folgenden Erweiterungen und Fehlerkorrekturen, die auf dem Feedback des Kunden für [!DNL Assets]Sie basieren.

* Bei MP3-Musikdateien funktioniert die Wiedergabeschaltfläche, die auf der Miniaturansicht in der DAM-Vorschau angezeigt wird, nicht. (CQ-4294731)
* Wenn Sie den Mauszeiger über die Ansicht der Karte bewegen, wird der Bildlauf durch (automatische) Fokussierung auf die Schnellaktionen durchgeführt, die auf der Karte verfügbar sind. (GRANITE-26895)
* Die Anzeige zu vieler Bilder nach dem Scrollen in einer großen Anzahl von Suchergebnissen führt zu einem Absturz des Browsers. (GRANITE-26432)
* Die [!UICONTROL Optionen]-, [!UICONTROL Scope]- und [!UICONTROL Workflows] -Fortschrittsindikatoren auf der Seite &quot;Veröffentlichung  verwalten&quot;werden von der Bildschirmlesehilfe nicht als Fortschrittsindikatoren vorgelesen. Stattdessen sehen Bildschirmlesehilfen diese Statusindikatoren als Tabulator-Liste an. (CQ-4273015)
* Wenn beim Herunterladen eines Assets die Option &quot;E-Mail&quot;aktiviert ist und selbst wenn eine gültige E-Mail-ID angegeben wurde, ist die Option &quot;Herunterladen&quot;nicht verfügbar. (CQ-4296535)

* Beim Hinzufügen von Tags auf der Seite &quot; [!UICONTROL Eigenschaften] &quot;eines Assets navigieren Benutzer durch eine Struktur von Tags. Die Baumstruktur kann nicht aufgerufen werden, da die Benutzer der Bildschirmlesehilfe beim Navigieren nichts hören. (CQ-4272964)
* Wenn Sie im Dialogfeld für die Freigabe von Links im Durchsuchen-Modus navigieren,

   * speichert die Tabelleninformationen, sobald das Dialogfeld geladen wurde.
   * kann nicht zu allen aufgelisteten automatischen Empfehlungen navigieren.
   * enthält keine automatischen Vorschläge für das Kombinationsfeld [!UICONTROL Hinzufügen E-Mail-Adresse/Suche] . (CQ-4294232)

* Ziehen-Optionen funktionieren nicht mit der Tastatur im NVDA-Durchsuchenmodus im Metadaten-Schema-Editor. (CQ-4296326)
* Auf der Benutzeroberfläche &quot;Assets&quot;sind die Einstellungen für die Ansicht nicht über die Tastatur verfügbar. (CQ-4289038)
* Als intelligente Sammlungen gespeicherte benutzerdefinierte Filter werden nicht ordnungsgemäß auf Assets angewendet. (CQ-4294942)
* Mehrere Verbesserungen bei der Suche und Indizierung und Fehlerkorrekturen zur Leistungsverbesserung. (CQ-4286373)
* Für die gelben Bewertungssymbole beträgt das Luminanzverhältnis weniger als 3:1. Es ist nicht nützlich für Benutzer mit eingeschränktem Sehvermögen und ohne Farbwahrnehmung. Die Bewertungssterne werden auf der Registerkarte &quot; [!UICONTROL Erweitert] &quot;im Bereich &quot; [!UICONTROL Bewertung] &quot;in den Asset- [!UICONTROL Eigenschaften] oder in der Ansicht der Karte angezeigt (CQ-4295106)
* Das Dropdownfeld &quot;Liste&quot;des Kombinationsfeldes (in verschiedenen Feldern auf verschiedenen Seiten) zeigt Einträge jetzt als Liste von Optionen an, die von Bildschirmlesehilfen angekündigt werden können. (CQ-4294017)
* Der Pfeil nach oben in der [!UICONTROL Zeitleiste] kann nicht über eine Tastatur aufgerufen werden, um einen Workflow auf ein Asset anzuwenden. (CQ-4289268)
* Die Optionen (mit [!UICONTROL x]) zum Entfernen der einzelnen markierten Tags unter dem Feld &quot; [!UICONTROL Tags] &quot;auf der Registerkarte &quot; [!UICONTROL Einfach] &quot;der [!UICONTROL Eigenschaften] sind jetzt für Bildschirmlesehilfen verfügbar. (CQ-4273033)
* Schreibgeschützte Formularfelder (z. B. deaktivierte Felder auf der Registerkarte [!UICONTROL &quot;] Einfach&quot;von Asset- [!UICONTROL Eigenschaften]) können jetzt über die Tastatur fokussiert werden. (CQ-4273031)
* Die Option zum Öffnen der Filter-Seitenleiste kann jetzt über die Tastatur aufgerufen werden. (CQ-4273018)
* Der Zweck verschiedener Kombinationsfeldelemente (z. B. Pfadfeld und Option zum Öffnen des Dialogfelds &quot;Auswahl&quot;auf der Registerkarte &quot;Grundeinstellungen&quot;von Asset-Eigenschaften) wird jetzt von Bildschirmlesehilfen korrekt angegeben. (CQ-4273016)
* [!UICONTROL Die Metadaten-Schema-Editor] -Seite und ihre Elemente können nicht über die Tastatur aufgerufen werden und sind nicht für Bildschirmlesehilfen geeignet. (CQ-4272953)
* Auf Videolautstärke-Steuerelemente kann nicht über eine Tastatur zugegriffen werden. (CQ-4272696)
* Viele Optionen auf der Benutzeroberfläche &quot;Assets&quot;deuten bei der Verwendung der Tastatur nicht auf den Fokus hin. (CQ-4272694)
* Bildschirmlesehilfen-Benutzer wissen nicht, dass die Zeilen in der Ansicht &quot;Liste&quot;bei Verwendung einer Tastatur ausgewählt werden können. Die Informationen werden nur angekündigt, wenn der Mauszeiger auf die Zeilen bewegt wird. (CQ-4271824)
* Einige Formularfelder wie der Benutzername und das Kennwort auf der Anmeldeseite basieren nur auf Platzhalterwerten, um eine barrierefreie Beschriftung zu erhalten. (CQ-4271716)
* Interaktive Elemente der Benutzeroberfläche, wie z. B. Links und Optionen (in Kopf- und Zoomoptionen der Assets-Seite, Ordnernavigation) können jetzt über eine Tastatur aufgerufen werden. (CQ-4271412)
* Die Titel aller durchsuchten Seiten in [!DNL Adobe Experience Manager] Assets sind jetzt eindeutig. (CQ-4271409)
