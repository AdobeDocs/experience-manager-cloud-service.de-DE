---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.6.0
description: Versionshinweise für Experience Manager 2020.6.0
translation-type: tm+mt
source-git-commit: fcae90c8e24dbd2994e8700daf22f5dff039b299
workflow-type: tm+mt
source-wordcount: '1942'
ht-degree: 11%

---


# Versionshinweise für AEM as a Cloud Service 2020.6.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.6.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.6.0 is June 04, 2020.

## Neue Funktionen in AEM Sites {#aem-sites}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für AEM Sites in Version 2020.6.0 von AEM as a Cloud Service.

### Neuerungen {#whats-new-2020.6.0}

Version 2.9.0 der [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) ist jetzt als Teil der AEM Sites verfügbar, darunter:

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

## Neue Funktionen in Stiftungen in AEM als Cloud Service {#foundations}

Die Buildzeit von AEM-Projekten wird dadurch verbessert, dass alle Verweise in der Datei &quot;pom.xml&quot;des AEM-Projekts auf das Remote-Repository entfernt werden `https://downloads.experiencecloud.adobe.com/content/maven/public`.

Das AEM als Cloud Service-SDK-API-Jar, das zuvor an diesem Speicherort gehostet wurde, befindet sich jetzt in Maven Central, dem Standard-Artefakt-Repository von Maven.

## Neue Funktionen in Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in Version 2020.6.0 von AEM as a Cloud Service.

### Neuerungen {#what-is-new-cloud-manager}

* Benutzer, die in Cloud Manager die Rolle &quot; *Geschäftsinhaber* &quot;verwenden, können jetzt ein Sandbox-Programm aus der Landingpage (über die Schaltfläche &quot;Schnellaktion&quot;auf der Programm-Karte) oder aus dem Programm löschen.

   Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) .

* Sandbox-Programm-Benutzer in *Business Owner* oder *Deployment Manager* -Rolle in Cloud Manager können ihre Produktions- und Stage-Umgebung jetzt über die Benutzeroberfläche von Cloud Manager löschen. Die Option zum Löschen steht jetzt sowohl auf der Seite &quot;Übersicht über die **Programme&quot;als auch auf der Seite &quot;Umgebung** &quot; **Umgebung** zur Verfügung. Wenn Sie die Option zum Löschen entweder auf der Produktions- oder der Stufe auswählen, wird auch die andere Option im Satz gelöscht.

   Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) .

* Coachmarks auf der Landingpage, die dem Benutzer grundlegende Informationen zur Navigation liefern.

* Coach-Markierungen auf der Seite &quot; **Programm-Übersicht** &quot;, um den Benutzer über die grundlegende Navigation innerhalb von Cloud Manager zu informieren und ihn zu informieren, um ihn zu starten.

* In Cloud Manager ist jetzt eine Seite mit **LERNMATERIALIEN** verfügbar, auf die Sie über die obere Navigationsleiste zugreifen können. Die Seite enthält Ressourcen, die Benutzer über die häufigsten Workflows für ihre entsprechende Rolle in Cloud Manager informieren.

* Sandbox-Programm werden jetzt mit einem **Sandbox** -Zeichen identifiziert, das auf der Programm-Karte auf der Landingpage sowie neben dem Programm-Namen auf der Seite &quot; **Programm-Übersicht** &quot;angezeigt wird.

* Ein Benutzer in der SysAdmin-Rolle hat jetzt einen 1-Klick-Zugriff auf den Speicherort in der Admin Console, von dem aus Benutzerrollen oder Berechtigungen für Cloud Manager verwaltet werden können. Auf der Landingpage neben der Schaltfläche &quot; **Hinzufügen Programm** &quot;steht jetzt eine Schaltfläche &quot;Zugriff **** verwalten&quot;zur Verfügung.

   Weitere Informationen finden Sie in den [SysAdmin-Aufgaben](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) .

* Ein Benutzer in der SysAdmin-Rolle hat jetzt einen 1-Klick-Zugriff auf die Autoreninstanz direkt aus Cloud Manager.

   Weitere Informationen finden Sie unter Zugriff auf Autoreninstanz [verwalten](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) .

* Das Erstellungsprotokoll enthält jetzt eine Liste der gefundenen Artefakte einschließlich übersprungener Inhaltspakete.

* Der Schritt „Erstellen“ überprüft jetzt, ob alle erstellten Inhaltspakete alle obligatorischen Eigenschaften enthalten: Name, Gruppe und Version.

* Der Schritt Erstellen überprüft jetzt, ob der Build mindestens ein Inhaltspaket erstellt hat.

### Fehlerbehebungen {#bug-fixes-cm}

* Unter bestimmten Umständen wurden die Symbole im Dialogfeld &quot;Programm **erstellen** &quot;falsch ausgerichtet.

* Die AEM-Versionshinweise wurden nicht einheitlich auf der Seite &quot; **Programme - Übersicht** &quot;angezeigt.

* When configuring the production pipeline, the **Scheduled Deployment** option was not visible for some customers.

### Bekannte Probleme {#known-issues-cm}

* Umgebung innerhalb eines Sandbox-Programms werden ausgeblendet, wenn für einen bestimmten Zeitraum keine Aktivität erkannt wird. Dieser Status wird in Cloud Manager nicht beobachtet. Der Status kann jedoch über die Developer Console beobachtet werden. Dies wird in einer kommenden Version behandelt.

* Der Link zur Developer Console direkt aus Cloud Manager zeigt die Option zum Deaktivieren/Entfernen der Umgebung eines Sandbox-Programms nicht an. Um dies zu beheben, fügen Sie in der Developer Console einmal das Muster `#release-cm-p1234-e5678` zum Ende der URL hinzu, wobei *1234* die Programm-ID und *5678* die Umgebung-ID ist. Dies wird in einer kommenden Version behandelt.

## Neue Funktionen in Version  [!DNL Adobe Experience Manager Assets]{#aem-assets}

**Benutzerfreundlichkeit für erweiterte Smart-Tags mit Adobe Sensei**

Mit erweiterten intelligenten Tags können Unternehmen intelligente Tagging-Modelle schulen, um Bilder zu erkennen, die auf kundenspezifischen Tags basieren, und zwar zusätzlich zu generischen Smart-Tags.

Mit dieser Version gibt es eine neue, geführte Benutzererfahrung, die bei der Einrichtung von Smart-Tags-Schulungen für Sätze kundenspezifischer Tags und deren Schulung mit Assets hilft, die in Zukunft erkannt und mit Tags versehen werden sollten. Das Erlebnis ist jetzt intuitiver.
Train Enhanced Smart Tags für eine intuitive Schulung zu intelligenten Tags. Erfahren Sie, [wie Sie Assets](/help/assets/smart-tags.md) Smart-Tags hinzufügen und intelligentes Tagging [konfigurieren](/help/assets/smart-tags-configuration.md).

**Unterstützung für Erfassung, Vorschau und Versand von 3D-Inhalten**

Organisationen können jetzt 3D-Dateien in AEM Assets speichern und verwenden. Benutzer können verschiedene Kern-3D-Dateien hochladen, Vorschau vornehmen und verwenden, einschließlich OBJ-, STL-, GLTF- und GLB-Dateien. Zusätzlich [!DNL Dynamic Media]können Sie 3D-Erlebnisse mit agnostischen URLs oder Viewern konfigurieren und bereitstellen. Dazu gehören ein [!DNL Dynamic Media] 3D-Experience Viewer, die Sites-3D-Viewer-Komponente und die Möglichkeit, 3D-Dateien über [!DNL Dynamic Media] (AR/VR) bereitzustellen. Siehe [Arbeiten mit 3D-Assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

**Adobe Asset Link-Unterstützung für Adobe XD**

Ab der neuesten Version [!DNL Experience Manager Assets] unterstützt es ein neues [!DNL Adobe Asset Link] Plugin, das mit [!DNL Adobe XD] Version 29.3 veröffentlicht wird. Die Integration ermöglicht Designern den Zugriff auf Assets und deren Verwendung in [!DNL Experience Manager] ihren Entwürfen, ohne dass die Anwendung verlassen [!DNL Adobe XD] muss. Weitere Informationen zu Adobe XD finden Sie unter [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html).

Mit dieser Version können kreative Benutzer und Designer jetzt mit Assets arbeiten, die in [!DNL AEM Assets] einer Reihe von Creative Cloud-Desktop-Apps verwaltet werden, einschließlich [!DNL Adobe Asset Link] , [!DNL Adobe XD], [!DNL Photoshop]und [!DNL Illustrator][!DNL InDesign].

**Verbesserungen der Barrierefreiheit**

[!DNL Adobe Experience Manager Assets] ist nun in Übereinstimmung mit den Richtlinien der Web Content Accessibility Guidelines (WCAG) v2.1 leichter zugänglich. Die Barrierefreiheit wurde für folgende Anwendungsfälle oder Schnittstellen verbessert:

Die Elemente der Benutzeroberfläche sind für Bildschirmlesehilfen benutzerfreundlich, können über eine Tastatur aufgerufen werden und haben einen besseren Kontrast. Im Folgenden finden Sie eine detaillierte Liste der Verbesserungen:

* Die [!UICONTROL Fortschrittsleisten]&quot;Optionen&quot;, &quot; [!UICONTROL Umfang]&quot;und &quot; [!UICONTROL Workflows] &quot;auf der Seite &quot;Veröffentlichung  verwalten&quot;werden von der Bildschirmlesehilfe nicht als Fortschrittsleiste gelesen. Stattdessen sehen Bildschirmlesehilfen diese Statusindikatoren als Tabulator-Liste an. (CQ-4273015)

* Beim Hinzufügen von Tags auf der Seite &quot; [!UICONTROL Eigenschaften] &quot;eines Assets navigieren Benutzer durch eine Struktur von Tags. Die Baumstruktur kann nicht aufgerufen werden, da die Benutzer der Bildschirmlesehilfe beim Navigieren nichts hören. (CQ-4272964)

* Wenn Sie im Dialogfeld für die Freigabe von Links im Durchsuchen-Modus navigieren,

   * Speichert die Tabelleninformationen sofort beim Laden des Dialogfelds.
   * Es ist nicht möglich, zu allen aufgelisteten automatischen Empfehlungen zu navigieren.
   * Die angezeigten automatischen Vorschläge für das Kombinationsfeld [!UICONTROL Hinzufügen E-Mail-Adresse/Suche] werden nicht erwähnt. (CQ-4294232)

* Die [!UICONTROL Metadaten-Schema-Editor] -Seite und die zugehörigen Elemente können jetzt auch über eine Tastatur aufgerufen werden und sind für eine Bildschirmlesehilfe geeignet. (CQ-4272953) Benutzer können die Komponenten über die Tastatur im NVDA-Durchsuchenmodus ziehen. (CQ-4296326)

* Auf der Benutzeroberfläche &quot;Assets&quot;sind die Einstellungen für die Ansicht nicht über die Tastatur verfügbar. (CQ-4289038)

* Für die gelben Bewertungssymbole beträgt das Luminanzverhältnis weniger als 3:1. Es ist nicht nützlich für Benutzer mit eingeschränktem Sehvermögen und ohne Farbwahrnehmung. Die Bewertungssterne werden auf der Registerkarte im Asset oder in der Ansicht der Karte angezeigt

* Farbe und Kontrast einiger Elemente der Benutzeroberfläche werden aktualisiert, sodass Benutzer mit eingeschränkter Sicht oder Benutzer ohne Farbwahrnehmung diese Elemente der Benutzeroberfläche unterscheiden können. Beispielsweise wird die Farbe der Symbole für die Bewertung von Sternen im Bereich [!UICONTROL Bewertung] auf der Registerkarte [!UICONTROL Erweitert] in den [!UICONTROL Eigenschaften] eines Assets und in der Ansicht der Karte entsprechend geändert. (CQ-4295106)

* Die Bildschirmlesehilfen können nun die Einträge des Popupmenüs &quot;Liste&quot;des Kombinationsfelds (in verschiedenen Feldern auf verschiedenen Seiten) als Liste der Optionen lesen. (CQ-4294017)

* Um einen Workflow auf ein Asset anzuwenden, können Sie über eine Tastatur auf den Chevron-Pfeil in der [!UICONTROL Zeitleiste] zugreifen. (CQ-4289268)

* Benutzer können ausgewählte Tags im Feld [!UICONTROL Tags] auf der Registerkarte [!UICONTROL Einfach] auf der Seite [!UICONTROL Eigenschaften] eines Assets mit `x` Symbol entfernen. Die Bildschirmlesehilfen geben nun den Zweck und die Anzahl der ausgewählten Tags an (CQ-4273033).

* Die schreibgeschützten Formularfelder können mithilfe einer Tastatur ausgewählt werden. Beispielsweise die deaktivierten Felder auf der Registerkarte &quot; [!UICONTROL Einfach] &quot;auf der Seite &quot; [!UICONTROL Eigenschaften] &quot;eines Assets. (CQ-4273031)

* Greifen Sie jetzt über eine Tastatur auf die Optionen zum Filtern von Assets in der linken Seitenleiste zu. (CQ-4273018)

* Die Bildschirmlesehilfe kündigt den Zweck verschiedener Kombinationsfeldelemente wie das Feld Pfad und die Option zum Öffnen des Dialogfelds Auswahl auf der Registerkarte [!UICONTROL Einfach] auf der Seite [!UICONTROL Eigenschaften] eines Assets an. (CQ-4273016)

* Auf die Lautstärkeregler für Videos kann über eine Tastatur zugegriffen werden. (CQ-4272696)

* Viele Optionen auf der Benutzeroberfläche &quot;Assets&quot;deuten bei der Verwendung der Tastatur nicht auf den Fokus hin. (CQ-4272694)

* Bildschirmlesehilfen-Benutzer erfahren jetzt, wann die Zeilen in der Ansicht der Liste über eine Tastatur ausgewählt werden können. Die Informationen werden angekündigt, wenn Sie mit der Maus auf die Zeilen zeigen. (CQ-4271824)

* Einige Formularfelder wie der Benutzername und das Kennwort auf der Anmeldeseite basieren auf Platzhalterwerten, um eine barrierefreie Beschriftung zu erhalten. (CQ-4271716)

* Interaktive Elemente der Benutzeroberfläche, wie z. B. Links und Optionen wie zum Beispiel für Kopf- und Zoomoptionen der Assets-Seite oder der Ordnernavigation, können jetzt über eine Tastatur aufgerufen werden. (CQ-4271412)

* Die Titel aller durchsuchten Seiten in [!DNL Adobe Experience Manager] Assets sind jetzt eindeutig. (CQ-4271409)

**Weitere Verbesserungen**

Die Version bietet die folgenden weiteren Verbesserungen:

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

Zusätzlich zu den oben genannten neuen Funktionen bietet die aktuelle Version die folgenden Fehlerbehebungen, die auf dem Feedback des Kunden basieren [!DNL Assets].

* Bei MP3-Musikdateien funktioniert die Wiedergabeschaltfläche, die auf der Miniaturansicht in der DAM-Vorschau angezeigt wird, nicht. (CQ-4294731)
* Wenn Sie den Mauszeiger über die Ansicht der Karte bewegen, wird der Bildlauf durch (automatische) Fokussierung auf die Schnellaktionen durchgeführt, die auf der Karte verfügbar sind. (GRANITE-26895)
* Das Anzeigen zu vieler Bilder nach dem Scrollen in vielen Suchergebnissen führt zu einem Browserabsturz. (GRANITE-26432)
* Wenn beim Herunterladen eines Assets die Option &quot;E-Mail&quot;aktiviert ist und selbst wenn eine gültige E-Mail-ID angegeben wurde, ist die Option &quot;Herunterladen&quot;nicht verfügbar. (CQ-4296535)
* Als intelligente Sammlungen gespeicherte benutzerdefinierte Filter werden nicht ordnungsgemäß auf Assets angewendet. (CQ-4294942)
* Mehrere Verbesserungen bei der Suche und Indizierung und Fehlerkorrekturen zur Leistungsverbesserung. (CQ-4286373)
