---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.6.0
description: Versionshinweise zu as a Cloud Service für 2020.6.0 [!DNL Adobe Experience Manager].
exl-id: fd6ebe2b-6d98-498c-a45d-b9a9c34e6be7
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1938'
ht-degree: 94%

---

# Versionshinweise für AEM as a Cloud Service 2020.6.0 {#release-notes}

Auf dieser Seite werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.6.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.6.0 von [!DNL Experience Manager] as a Cloud Service wurde am 4. Juni 2020 veröffentlicht.

## Neue Funktionen in AEM Sites {#aem-sites}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für AEM Sites in Version 2020.6.0 von AEM as a Cloud Service.

### Neue Funktionen {#whats-new-2020.6.0}

Version 2.9.0 der [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) ist jetzt als Teil von AEM Sites verfügbar, einschließlich folgenden Optionen:

* Integration zwischen der [Adobe Client-Datenschicht](https://github.com/adobe/adobe-client-data-layer) und den Kernkomponenten
* Konfigurierbare HTML-ID-Attribute für alle Komponenten
* Neue Fortschrittsbalkenkomponente
* Viele Fehlerbehebungen

### Fehlerbehebungen {#sites-bug-fixes}

* Komponenten im Layout-Container sind nicht sichtbar, wenn der Layout-Container kopiert und erneut auf einer Seite eingefügt wird.

* Problem mit der Größenanpassung der Layout-Komponente behoben.

* Es wurde die Möglichkeit hinzugefügt, das Routing von reinen Angular-Seiten und AEM-/Angular-Seiten zu verwalten.

### Barrierefreiheit {#accessibility}

* Rolle und Status des Erzählenden sind jetzt für die Masonry-Elemente im Dialogfeld **Seite erstellen** möglich, während Sie im Browser-Modus mit dem Abwärtspfeil navigieren.

* Es wurde ein Link zur Navigation hinzugefügt, über den Benutzer zum Hauptinhalt springen können.

* Verbesserungen der Sprachausgabe.

## Neue Funktionen in Foundations in AEM as a Cloud Service {#foundations}

Die Erstellungszeiten von AEM-Projekten werden verbessert, indem alle Verweise in der Datei „pom.xml“ des AEM-Projekts auf die Remote-Repository-`https://downloads.experiencecloud.adobe.com/content/maven/public` entfernt werden.

Die AEM as a Cloud Service SDK-API-JAR-Datei, die zuvor an diesem Speicherort gehostet wurde, befindet sich jetzt in Maven Central, dem Standard-Artefakt-Repository von Maven.

## Neue Funktionen in Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in AEM as a Cloud Service Version 2020.6.0.

### Neue Funktionen {#what-is-new-cloud-manager}

* Benutzende mit der Rolle *Business Owner* in Cloud Manager können jetzt ein Sandbox-Programm von der Landingpage (über die Schaltfläche für den Schnellzugriff auf der Programmkarte) oder aus dem Programm heraus löschen.

  Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html?lang=de).

* Benutzende von Sandbox-Programmen mit der Rolle *Geschäftsinhaber* oder *Bereitstellungs-Manager* in Cloud Manager können jetzt ihren Satz von Produktions- und Staging-Umgebungen löschen, der über die Cloud Manager-Benutzeroberfläche festgelegt wurde. Die Löschoption ist jetzt sowohl auf der Seite **Programmübersicht** als auch auf der Seite **Umgebungen** auf der Umgebungskarte verfügbar. Durch Auswahl der Löschoption für die Produktions- oder Staging-Umgebung wird die jeweils andere Umgebung im Satz ebenfalls gelöscht.

  Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html?lang=de).

* Coachmarks auf der Landingpage, die dem Benutzer grundlegende Informationen zur Navigation liefern.

* Coachmarks auf der Seite **Programm-Übersicht** informieren den Benutzer über die grundlegende Navigation in Cloud Manager, um ihm den Einstieg zu erleichtern.

* In Cloud Manager ist jetzt eine Seite mit **LERNMATERIALIEN** verfügbar, auf die Sie über die obere Navigationsleiste zugreifen können. Die Seite enthält Ressourcen, die Benutzer über die häufigsten Workflows für ihre entsprechende Rolle in Cloud Manager informieren.

* Sandbox-Programme werden jetzt anhand eines **Sandbox**-Symbols identifiziert, das auf der Programmkarte auf der Landingpage sowie neben dem Programmnamen auf der Seite **Programmübersicht angezeigt** wird.

* Ein Benutzer mit der SysAdmin-Rolle hat jetzt 1-Klick-Zugriff auf den Speicherort in Admin Console, von der aus Benutzerrollen oder Berechtigungen für Cloud Manager verwaltet werden können. Eine Schaltfläche **Zugriff verwalten** ist jetzt auf der Landingpage neben der Schaltfläche **Programm hinzufügen** verfügbar.

  Weitere Details finden Sie unter [SysAdmin-Aufgaben](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=de#sysadmin-tasks).

* Benutzende mit der SysAdmin-Rolle können jetzt direkt aus Cloud Manager per 1-Klick-Zugriff auf die Autoreninstanz zugreifen.

  Weitere Informationen finden Sie unter [Verwalten des Zugriffs auf die Autoreninstanz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=de#manage-access-aem).

* Das Erstellungsprotokoll enthält jetzt eine Liste der gefundenen Artefakte, einschließlich übersprungener Inhaltspakete.

* Der Build-Schritt überprüft jetzt, ob alle generierten Inhaltspakete alle obligatorischen Eigenschaften enthalten - Name, Gruppe und Version.

* Der Schritt „Erstellen“ überprüft jetzt, ob der Build mindestens ein Inhaltspaket erstellt hat.

### Fehlerbehebungen {#bug-fixes-cm}

* Unter bestimmten Umständen wurden die Symbole im Dialogfeld **Programm erstellen** falsch ausgerichtet.

* Die AEM-Versionskennung wurde auf der Seite **Programmübersicht** nicht konsistent angezeigt.

* Bei der Konfiguration der Produktions-Pipeline war die Option **Geplante Bereitstellung** für einige Kunden nicht sichtbar.

### Bekannte Probleme {#known-issues-cm}

* Umgebungen innerhalb eines Sandbox-Programms werden in den Ruhezustand versetzt, wenn für eine bestimmte Dauer keine Aktivität festgestellt wird. Dieser Status wird in Cloud Manager nicht verfolgt. Der Status kann jedoch über die Developer Console verfolgt werden. Dies wird in einer kommenden Version adressiert.

* Der Link zur Developer Console direkt aus Cloud Manager zeigt die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an. Um dies zu beheben, fügen Sie in der Developer Console das Muster `#release-cm-p1234-e5678` am Ende der URL hinzu, wobei *1234* die Programm-ID und *5678* die Umgebungs-ID ist. Dies wird in einer kommenden Version adressiert.

## Neue Funktionen in Version [!DNL Adobe Experience Manager Assets] {#aem-assets}

**Geführtes Benutzererlebnis für erweiterte Smart-Tags auf der Grundlage von Adobe AI**

Mit den optimierten Smart-Tags können Unternehmen Smart-Tagging-Modelle trainieren, um neben generischen Smart-Tags auch Bilder zu erkennen, die auf kundenspezifischen Unternehmens-Tags basieren.

In dieser Version gibt es ein neues, geführtes Benutzererlebnis, mit dessen Hilfe Smart-Tags-Training für Sätze kundenspezifischer Tags eingerichtet und mit Assets trainiert werden kann, die in Zukunft erkannt und mit diesen versehen werden sollen. Das Erlebnis ist jetzt intuitiver.
Trainieren Sie erweiterte Smart-Tags für ein intuitiveres Training für Smart-Tags. Siehe [Hinzufügen von Smart-Tags zu Assets](/help/assets/smart-tags.md).

**Unterstützung der Aufnahme, Vorschau und Bereitstellung von 3D-Inhalten**

Organisationen können jetzt 3D-Dateien in AEM Assets speichern und verwenden. Benutzer können eine Vielzahl von 3D-Dateiformaten hochladen, nutzen und in Vorschauen anzeigen, einschließlich .obj-, .stl-, .gltf- und .glb-Dateien. Zusammen mit [!DNL Dynamic Media] können Sie 3D-Erlebnisse mit agnostischen URLs oder Viewern konfigurieren und bereitstellen. Dies umfasst einen [!DNL Dynamic Media] 3D Experience Viewer, eine Sites 3D Viewer-Komponente und die Möglichkeit, 3D-Dateien über [!DNL Dynamic Media] (AR/VR) bereitzustellen. Siehe [Arbeiten mit 3D-Assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

**Unterstützung von Adobe Asset Link für Adobe XD**

Mit der neuesten Version bietet [!DNL Experience Manager Assets] Unterstützung für ein neues [!DNL Adobe Asset Link]-Plug-in, das mit [!DNL Adobe XD] V29.3 veröffentlicht wird. Durch die Integration können Designer auf Assets von [!DNL Experience Manager] zugreifen und diese in ihren Designs verwenden, ohne [!DNL Adobe XD] verlassen zu müssen. Weitere Informationen finden Sie in der [Dokumentation zu Adobe Asset Link für Adobe XD](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link-for-xd.html).

Mit dieser Version können kreative Benutzer und Designer in [!DNL AEM Assets] verwaltete Assets jetzt mit [!DNL Adobe Asset Link] in einer Reihe von Creative Cloud-Programmen verwenden, darunter [!DNL Adobe XD], [!DNL Photoshop], [!DNL Illustrator] und [!DNL InDesign].

**Verbesserte Barrierefreiheit**

[!DNL Adobe Experience Manager Assets] ist mit den Richtlinien der Web Content Accessibility Guidelines (WCAG) V2.1 kompatibel und leichter zugänglich. Die Barrierefreiheit wurde für folgende Anwendungsfälle oder Schnittstellen verbessert:

Die Elemente der Benutzeroberfläche sind für Vorlese-Progrmme benutzerfreundlich, können über eine Tastatur aufgerufen werden und haben einen besseren Kontrast. Im Folgenden finden Sie eine detaillierte Liste der Verbesserungen:

* Die Fortschrittsanzeigen für [!UICONTROL Optionen], [!UICONTROL Umfang] und [!UICONTROL Workflows] auf der Seite [!UICONTROL Veröffentlichung verwalten] werden vom Vorlese-Programm nicht als Fortschrittsanzeigen ausgelesen. Stattdessen nehmen die Benutzer der Sprachausgabe diese Statusanzeigen als eine Registerkartenliste wahr. (CQ-4273015)

* Beim Hinzufügen von Tags auf der Seite [!UICONTROL Eigenschaften] eines Assets navigieren Benutzer durch eine Baumstruktur von Tags. Die Baumstruktur ist nicht barrierefrei, da die Benutzer der Sprachausgabe beim Navigieren nichts hören. (CQ-4272964)

* Wenn Sie im Dialogfeld für die Freigabe von Links im Durchsuchen-Modus navigieren,

   * liest das Vorlese-Programm die Tabelleninformationen sofort beim Laden des Dialogs.
   * kann das Vorlese-Programm nicht zu allen aufgelisteten automatischen Vorschlägen navigieren.
   * liest das Vorlese-Programm nicht die automatischen Vorschläge für das Kombinationsfeld [!UICONTROL E-Mail-Adresse hinzufügen/Suchen]. (CQ-4294232)

* Die Seite [!UICONTROL Metadatenschema-Editor] und deren Elemente können nicht über die Tastatur aufgerufen werden und sind nicht für das Vorlese-Programm geeignet. (CQ-4272953) Benutzer können die Komponenten über die Tastatur im NVDA-Modus „Durchsuchen“ ziehen. (CQ-4296326)

* Auf der Assets-Benutzeroberfläche sind die Ansichtseinstellungen nicht über die Tastatur zugänglich. (CQ-4289038)

* Das Leuchtdichteverhältnis für die gelb :1 Bewertungssymbole beträgt weniger als 3 %. Das ist für Benutzer mit eingeschränktem Sehvermögen oder ohne Farbwahrnehmung nicht hilfreich. Die Bewertungssterne werden auf der Registerkarte in Asset oder in der Kartenansicht angezeigt

* Farbe und Kontrast einiger Elemente der Benutzeroberfläche werden aktualisiert, sodass Benutzer mit eingeschränkter Sehkraft oder Benutzer ohne Farbwahrnehmung diese Elemente der Benutzeroberfläche unterscheiden können. Beispielsweise wird die Farbe der Symbole für die Bewertung von Sternen im Abschnitt [!UICONTROL Bewertung] auf der Registerkarte [!UICONTROL Erweitert] in den [!UICONTROL Eigenschaften] eines Assets und in der Kartenansicht für einen angemessenen Kontrast geändert. (CQ-4295106)

* Die Vorlese-Programme können nun die Einträge des Popup-Menüs „Liste“ des Kombinationsfelds (in verschiedenen Feldern auf verschiedenen Seiten) als Liste der Optionen lesen. (CQ-4294017)

* Um einen Workflow auf ein Asset anzuwenden, können Sie über eine Tastatur auf den Richtungspfeil in der [!UICONTROL Timeline] zugreifen. (CQ-4289268)

* Benutzer können ausgewählte Tags im Feld [!UICONTROL Tags] auf der Registerkarte [!UICONTROL Standard] auf der Seite [!UICONTROL Eigenschaften] eines Assets mit dem Symbol `x` entfernen. Die Vorlese-Programme geben nun den Zweck und die Anzahl der ausgewählten Tags an (CQ-4273033).

* Die schreibgeschützten Formularfelder können mithilfe einer Tastatur ausgewählt werden. Beispielsweise die deaktivierten Felder auf der Registerkarte [!UICONTROL Standard] auf der Seite [!UICONTROL Eigenschaften] eines Assets. (CQ-4273031)

* Greifen Sie jetzt über eine Tastatur auf die Optionen zum Filtern von Assets in der linken Seitenleiste zu. (CQ-4273018)

* Das Vorlese-Programm kündigt den Zweck verschiedener Kombinationsfeldelemente wie das Feld „Pfad“ und die Option zum Öffnen des Dialogfelds „Auswahl“ auf der Registerkarte [!UICONTROL Standard] auf der Seite [!UICONTROL Eigenschaften] eines Assets an. (CQ-4273016)

* Auf die Lautstärkeregler für Videos kann über eine Tastatur zugegriffen werden. (CQ-4272696)

* Viele ausführbare Optionen auf der Assets-Benutzeroberfläche zeigen bei der Verwendung der Tastatur keinen Fokus an. (CQ-4272694)

* Benutzer von Vorlese-Anwendungen erfahren jetzt, wenn die Zeilen in der Listenansicht über eine Tastatur ausgewählt werden können. Die Informationen werden nur angesagt, wenn der Mauszeiger über die Zeilen bewegt wird. (CQ-4271824)

* Einige Formularfelder, wie z. B. die Felder für Benutzername und Kennwort auf der Anmeldeseite, benötigen Platzhalterwerte, um eine zugängliche Bezeichnung anzubieten. (CQ-4271716)

* Interaktive Elemente der Benutzeroberfläche, wie z. B. Links und Optionen (in Kopfzeilen- und Zoom-Optionen der Assets-Seite, Ordnernavigation) können jetzt über eine Tastatur aufgerufen werden. (CQ-4271412)

* Die Titel aller durchsuchten Seiten in [!DNL Adobe Experience Manager] Assets sind jetzt eindeutig. (CQ-4271409)

**Weitere Verbesserungen**

Die Version enthält die folgenden zusätzlichen Verbesserungen:

* Möglichkeit zur erneuten Verarbeitung von Assets mit Asset-Verarbeitungsprofilen, sodass Benutzer die volle Kontrolle über den Prozess haben (vollständige Asset-Verarbeitung ausführen, nur ein bestimmtes Verarbeitungsprofil anwenden und entscheiden, ob der Nachbearbeitungs-Workflow ausgeführt werden soll).
* Suchanfragen geben jetzt schneller Ergebnisse zurück, wenn die zugrunde liegende Cluster-Instanz hinter den Kulissen neu gestartet wurde (der erste Suchlauf konnte in einem solchen Fall zuvor länger dauern).
* Sortieren Sie nach „Name“, wenn Sie Assets in der Listenansicht in der Assets-Benutzeroberfläche und in den Suchergebnissen anzeigen. Siehe [Suchen von Assets](/help/assets/search-assets.md#sort).
* Sortieren Sie bei der Anzeige von Assets in der Listenansicht auf der Assets-Benutzeroberfläche und in den Suchergebnissen nach „Erstellt“ (Datum). Siehe [Suchen von Assets](/help/assets/search-assets.md#sort).
* Unterstützung für die Konvertierung von EPS-Dateien in Bilder mithilfe von Asset Microservices.

### Fehlerbehebungen {#assets-bug-fixes}

Zusätzlich zu den oben genannten neuen Funktionen bietet die aktuelle Version die folgenden Verbesserungen und Fehlerkorrekturen auf der Grundlage von Kunden-Feedback für [!DNL Assets].

* Bei MP3-Musikdateien funktioniert die Wiedergabeschaltfläche nicht, die auf der Miniatur in der DAM-Vorschau angezeigt wird. (CQ-4294731)
* Wenn Sie den Mauszeiger über die Kartenansicht bewegen, scrollt der Bildschirm infolge der (automatischen) Fokussierung auf die in der Karte verfügbaren Schnellzugriff-Funktionen. (GRANITE-26895)
* Das Anzeigen zu vieler Bilder nach dem Scrollen einer großen Anzahl von Suchergebnissen führt zum Absturz des Browsers. (GRANITE-26432)
* Wenn beim Herunterladen eines Assets die E-Mail-Option aktiviert ist, ist die Option zum Herunterladen nicht verfügbar, auch wenn eine gültige E-Mail-Adresse angegeben wurde. (CQ-4296535)
* Als Smart-Sammlungen gespeicherte benutzerdefinierte Filter werden nicht korrekt auf Assets angewendet. (CQ-4294942)
* Mehrere Verbesserungen bei der Suche und Indizierung und Fehlerkorrekturen zur Verbesserung der Leistung. (CQ-4286373)
* Auf die Registerkarte „Ordnereigenschaften“ kann in Assets nicht zugegriffen werden und es wird ein 500-Fehler zurückgegeben. (CQ-4295701)
