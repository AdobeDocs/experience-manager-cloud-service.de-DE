---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
translation-type: tm+mt
source-git-commit: 92de2936fd6eb66198f0a096dd2e0020f14fccb8
workflow-type: tm+mt
source-wordcount: '1906'
ht-degree: 5%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (aktuelle) Version von [!DNL Experience Manager] als Cloud Service erläutert.

>[!NOTE]
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Letzte Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Adobe Experience Manager] als Cloud Service 2021.4.0 ist der 6. Mai 2021.
Die folgende Version (2021.5.0) wird am 27. Mai 2021 veröffentlicht.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### Neue Funktionen {#what-is-new-foundation}

* [Arbeitsablauf](/help/operations/replication.md#publish-content-tree-workflow)  zum Veröffentlichen der Inhaltsstruktur - Ein neues Workflow-Modell und ein Schritt bieten eine höhere Leistung beim Veröffentlichen von tiefen Hierarchien von Inhalten.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* GraphQL Endpoints - jetzt ist es möglich, die AEM GraphQL API für einzelne AEM Sites Konfigurationen zu aktivieren und benutzerdefinierte GraphQL Endpunkte für diese Konfigurationen zu erstellen, indem eine neue GraphQL-Konsolenschnittstelle verwendet wird. Die Benutzeroberfläche ermöglicht auch die Verwaltung von GraphQL-Endpunkten.

* Inhaltsmodelle, erweiterter Datums- und Uhrzeitdatentyp - es ist jetzt möglich, den Datums- und Uhrzeittyp so zu konfigurieren, dass nur Daten zu Datum, Uhrzeit oder Uhrzeit und Uhrzeit erstellt werden können.

* Inhaltsmodelle, verbesserter Tag-Datentyp - der Datentyp Tags kann jetzt so konfiguriert werden, dass das Authoring von einzelnen oder mehreren Tags möglich ist.

* Inhaltsmodelle, neuer Datentyp &quot;Tabstoppplatzhalter&quot;- der neue Datentyp &quot;Tabulatorplatzhalter&quot;ermöglicht die Gruppierung von Datentypen in Abschnitte, die im Inhaltsfragmenteditor unter Registerkarten gerendert werden.

### Fehlerbehebungen in [!DNL Sites] {#bug-fixes-sites}

* Inhaltsfragmente - Durch Verschieben von Inhaltsfragmenten oder Ordnern werden jetzt verschachtelte Verweise innerhalb des Fragments aktualisiert (CQ-4320815)

* GraphQL - Fortbestehende Abfragen unterstützen jetzt benutzerdefinierte Endpunkte, die für AEM Sites-Konfigurationen spezifisch sind (CQ-4315928)

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* [!DNL Experience Manager] archiviert keine einzelnen Asset-Downloads, bei denen die Originaldatei heruntergeladen wurde. Diese Verbesserung ermöglicht schnellere Downloads.

* Wenn ein Asset über die Option &quot;linkshare&quot;heruntergeladen wird, können Sie jetzt festlegen, ob die Darstellungen heruntergeladen oder nicht heruntergeladen werden sollen. Zuvor wurden alle Asset-Darstellungen heruntergeladen.

* Administratoren können [!DNL Experience Manager] so konfigurieren, dass die Quelle von Assets nach der Erfassung von Massenelementen gelöscht wird. Siehe [Erfassung von Massenelementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Durchführen einer Gesundheitsprüfung zum Massenimport von Assets bietet Experience Manager jetzt weitere Informationsgründe für Fehler. Siehe [Erfassung von Massenelementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Importieren von Assets mit dem Massenimport-Tool haben Administratoren jetzt die Möglichkeit, die Quelldateien zu löschen, nachdem der Import erfolgreich war. Siehe [Erfassung von Massenelementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Bearbeiten eines Metadaten-Schemas ermöglicht ein neues Stammpfadauswahl-Feld Administratoren eine schnelle und einfache Auswahl, wodurch die Konfigurationszeit verkürzt wird.

* Metadaten vieler Assets können stapelweise mithilfe einer CSV-Datei importiert und in eine CSV-Datei exportiert werden. Das Standarddatumsformat ist jetzt `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Benutzer können ein anderes Format verwenden, indem sie die Spaltenüberschrift aktualisieren. Fügen Sie beispielsweise `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` als Spaltenüberschrift in der CSV-Datei anstelle des Wortes `Date` hinzu.

* Beim Durchsuchen von Assets in der Ansicht &quot;Spalte&quot;zeigt ein visueller Indikator den Status der einzelnen Assets an, die genehmigt oder abgelehnt wurden.

* Beim Durchsuchen von Assets in der Ansicht &quot;Spalte&quot;wird ein visueller Indikator für abgelaufene Assets angezeigt.

* Ein Textbereich-Datentyp wird im Metadateneditor für [!DNL Assets] bereitgestellt. Sie können diese Option verwenden, um Ihren Benutzern die Eingabe von Metadaten in ein Textfeld ohne Formulare zu ermöglichen.

### Fehlerbehebungen in [!DNL Assets] {#bug-fixes-assets}

* Beim Versuch, mehrere Assets oder Ordner zu verschieben, wird ein Fehler in der Konsole protokolliert und der Vorgang zum Verschieben ist nicht abgeschlossen. Der Verschieben-Vorgang schlägt fehl, wenn der Titel nicht aktualisiert werden kann. (CQ-4322080)

* Ein Metadatenfeld kann basierend auf einer Regel ausgeblendet werden, die besagt, dass die Metadaten bei Erfüllung einer vordefinierten Bedingung nicht obligatorisch sind. Solche unsichtbaren Metadatenfelder werden jedoch als erforderliche Felder angezeigt. (CQ-4321285)

* Der Import von Massenmetadaten schlägt fehl, weil das Datumsformat nicht korrekt ist. (CQ-4319014)

* Wenn auf der Seite &quot;Eigenschaften&quot;eine Auswahl zum Aktualisieren von Metadaten vorgenommen wird, reagiert die Benutzeroberfläche nur langsam, wenn das Schema viele Optionen bereitstellt. (CQ-4318538)

* Beim Aktualisieren und Speichern von Metadatenwerten in einem einzeiligen Textfeld werden die Werte im Dropdown-Menü gelöscht, auch wenn Bearbeitungen im Dropdown-Menü deaktiviert sind. (CQ-4317077)

* Sie können Auslassungspunkte als Anmerkung verwenden, um Assets zu überprüfen. Wenn eine kleine Ellipse verwendet wird, überschneidet sich die Ellipse mit der Nummer der Anmerkung in der Druckversion. (CQ-4316792)

## [!DNL Adobe Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

Sie können [AEM Forms als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) verwenden, um digitale Formulare zu erstellen, Formulare mit vorhandenen Datenquellen zu verbinden, Formulare mit Adobe Sign zu integrieren und E-Signaturen zu Formularen hinzuzufügen, Dokument aus Datensatz (DoR) zu generieren, um gesendete Formulare als PDF-Dateien zu archivieren. Der Dienst kann auch Ihre vorhandenen PDF forms in digitale Formulare konvertieren. Zusätzlich zu den standardmäßigen AEM Forms-Funktionen bietet der Dienst mehrere Cloud-native Funktionen wie automatische Skalierung, kostenlose Ausfallzeiten für Upgrades und Cloud-native Umgebung für die Entwicklung. Lesen Sie [diesen Blog-Beitrag](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html), um mehr über die Funktionen und Funktionen von AEM Forms als Cloud Service zu erfahren.

* **Authentifizierungsmethode zur Identitätsauthentifizierung mit einer öffentlichen ID in Adobe Sign-aktiviertem adaptiven Forms verwenden**

   Mit fortschrittlichen maschinellen Lernalgorithmen ermöglicht der Adobe Sign-ID-Prozess Firmen auf der ganzen Welt eine hochwertige Authentifizierung der Identität ihres Empfängers. Jetzt können Sie die Authentifizierungsmethode für die Identitätsauthentifizierung mit einer Behördenkennung in Adobe Sign-aktiviertem adaptiven Forms verwenden.

   Öffentliche ID ist eine Premium-Identitätsauthentifizierungsmethode, die den Empfänger anweist, [das Dokument eines staatlich ausgestellten Identitätsnachweises (Führerschein, nationale ID, Reisepass)](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html) hochzuladen und dieses Dokument dann zu bewerten, um seine Authentizität sicherzustellen.

* **Unterstützung für die Verwendung von In-Form-Signaturen für asynchrone Übermittlungen von adaptiven Formularen**

   Sie können jetzt die Formularsignaturerfahrung für asynchrone adaptive Formularübermittlungen verwenden. Sie können ein adaptives Formular auch in eine [!DNL Experience Manager Sites]-Seite einbetten und das Formular-Signaturerlebnis für adaptive Formularübermittlungen verwenden.

* **Unterstützung für die Verwendung einer Variablen zum Angeben einer Anlage beim Vorausfüllen eines adaptiven Formulars für einen Zuweisungsschritt**

   Beim Vorausfüllen eines adaptiven Formulars für einen Zuweisungsschritt können Sie jetzt eine Dokument-Typvariable verwenden, um eine Eingabehilfe für das adaptive Formular auszuwählen.

* **Unterstützung für die Verwendung der Literaloption zum Festlegen des Werts für eine JSON-Typvariable**

   Sie können mit der Option &quot;Literal&quot;Werte für eine JSON-Typvariable im Schritt &quot;Set Variable&quot;eines AEM Arbeitsablaufs festlegen. Mit der Option &quot;Literal&quot;können Sie eine JSON in Form einer Zeichenfolge angeben.

* **Dokument of Record (DoR) mithilfe der Umgebung für die lokale Entwicklung erstellen**

   Sie können eine XDP als Dokument einer Datensatzvorlage für Cloud Service-Instanzen und AEM Forms als Cloud Service-SDK (Local Development Umgebung) verwenden. Zuvor war die Unterstützung nur auf Cloud Service-Instanzen beschränkt.

### Fehlerbehebungen in [!DNL Forms] {#bug-fixes-forms}

* Wenn ein adaptives Formular, das so konfiguriert wurde, dass kein Dokument aus Datensatz generiert wird, an einen AEM Workflow gesendet wird, der zum Generieren des Dokuments aus Datensatz konfiguriert ist, wird keine Fehlermeldung angezeigt und die Aufgabe kann nicht gesendet werden.

### Weitere Updates {#misc-2021-04-0-forms}

* Um die Erkennung von Inhalten zu vereinfachen, generiert der Dienst jetzt eine Live-Miniaturansicht für XDP-, Dynamische PDF- und Schema-Dateien.
* hinzufügen Möglichkeit, eine PDF-Datei in einen Ordner in der AEM Forms-Benutzeroberfläche zu verschieben.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Unterstützung für Kategorie-UID - Hierdurch werden Commerce-Integrationen von Drittanbietern für Systeme freigeschaltet, die Strings für Kategorien-IDs verwenden

* AEM Erweiterung für PWA Studio incl. Beispielintegration

* Neue CIF-Navigationskernkomponente, die die WCM-Navigationskernkomponente erweitert

* Visueller Indikator für gestaffelte Katalogdaten im AEM Store

* Der Commerce-Endpunkt kann jetzt über die Benutzeroberfläche von Cloud Manager konfiguriert werden.

### Fehlerbehebungen {#bug-fixes-commerce}

* Das Feld &quot;Stamm-Kategorie&quot;wurde nicht auf der Registerkarte &quot;Handel&quot;in den Seiteneigenschaften der Kategorien angezeigt


## Cloud Manager {#cloud-manager}

In diesem Abschnitt werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2021.5.0 und 2021.4.0 erläutert.

### Veröffentlichungsdatum {#release-date-cm-may}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.5.0 ist der 06. Mai 2021.
Die nächste Version ist für den 03. Juni 2021 geplant.

### Neue Funktionen {#what-is-new-may}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, und zwar in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Das von einem Cloud Manager-Benutzer heruntergeladene Bereitstellungsprotokoll enthält jetzt Details zu Fehlern und Erfolgsszenarien.

* Zwischenweise auftretende Fehler beim Verschieben von Code in Adobe git wurden nun behoben.

* Das Commerce-Add-on kann jetzt während des Workflows Programm bearbeiten auf Sandbox-Programm angewendet werden.

* Das Erlebnis &quot;Programm bearbeiten&quot;wurde aktualisiert.

* Die Tabelle &quot;Domänennamen&quot;auf der Seite &quot;Umgebung-Details&quot;zeigt bis zu 250 Domänennamen per Paginierung an.

* Auf der Registerkarte &quot;Lösungen&quot;in Hinzufügen Programm und im Workflows &quot;Programm bearbeiten&quot;wird die Lösung angezeigt, auch wenn nur eine Lösung für das Programm verfügbar ist.

* Die Fehlermeldung im Protokoll des Buildschritts, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes-cm-may}

* Gelegentlich wird dem Benutzer neben einer IP-Zulassungsliste ein grüner &quot;Aktiv&quot;-Status angezeigt, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Statt &#39;gelöschte&#39; Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **DELETED**.

* Einige Qualitätsprobleme mit Code-Geruch haben die Zuverlässigkeitsbewertung fälschlicherweise beeinflusst.

* Da Platzhalterdomänen nicht unterstützt werden, verhindert die Benutzeroberfläche, dass der Benutzer eine Platzhalterdomäne sendet.

* Wenn eine Pipeline-Ausführung zwischen Mitternacht und 1am UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als eine Version, die am Vortag erstellt wurde.

* Während der Einrichtung des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode Git verwalten als Link von der Heldenkarte auf der Seite Überblick angezeigt.

### Veröffentlichungsdatum {#release-date-cm-april}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.4.0 ist der 08. April 2021.

### Neue Funktionen {#what-is-new-april}

* Die Benutzeroberfläche wird aktualisiert, um das Hinzufügen- und Bearbeiten-Programm-Workflows intuitiver zu gestalten.

* Ein Benutzer mit erforderlichen Berechtigungen kann jetzt den Commerce-Endpunkt über die Benutzeroberfläche senden.

* Umgebung können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autor oder auf Veröffentlichung. Erfordert AEM Version `2021.03.5104.20210328T185548Z` oder höher.

* Die Schaltfläche **Git** verwalten wird auf der Pipelines-Karte angezeigt, auch wenn keine Pipelines konfiguriert wurden.

* Die Version des von Cloud Manager verwendeten AEM Projektarchivs wurde auf Version 27 aktualisiert.

* Projekte, die in der Adobe I/O Developer Console von Cloud Manager erstellt wurden, können nicht mehr unbeabsichtigt bearbeitet oder gelöscht werden.

* Wenn ein Benutzer eine neue Umgebung hinzufügt, wird ihm mitgeteilt, dass eine Umgebung nach dem Erstellen nicht in einen anderen Bereich verschoben werden kann.

* Umgebung können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autor oder auf Veröffentlichung. Erfordert AEM Version 2021.03.5104.20210328T185548Z oder höher.

* Die Fehlermeldung beim Starten einer Pipeline beim Löschen einer Umgebung wurde geklärt.

* OSGi-Pakete, die von Eclipse-Projekten bereitgestellt werden, sind nun von der Regel `CQBP-84--dependencies` ausgeschlossen.

### Fehlerbehebungen {#bug-fixes-cm-april}

* Beim Bearbeiten der Experience Audit-Seite einer Pipeline führt ein Eingabepfad, der mit einem Schrägstrich `( / )` beginnt, nicht mehr dazu, dass der Schritt im ausstehenden Status blockiert wird.

* Wenn eine neue Produktions-Pipeline erstellt wird und der Benutzer keine Überschreibung der Inhaltsprüfung hinzufügt, wurde die Standard-Homepage nicht geprüft.

* Bei Problemen mit `CloudServiceIncompatibleWorkflowProcess` war die CSV-Datei für die herunterladbare Ausgabe nicht korrekt.

* Die `Runmode`-Prüfung ergab Falsch-Positiv-Werte für Nicht-Ordner-Knoten.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Das Veröffentlichungsdatum für Best Practices Analyzer v2.1.12 ist der 12. April 2021.

### Fehlerbehebungen {#bug-fixes-bpa-april}

* Duplikat-Zeilen wurden in den BPA-Berichten angezeigt. Dieses Problem wurde behoben.
* Die BPA-Benutzeroberfläche in AEM Version 6.4.2 gab einen JS-Fehler aus, der die Schaltfläche Bericht erstellen deaktiviert hatte. Dieses Problem wurde behoben

