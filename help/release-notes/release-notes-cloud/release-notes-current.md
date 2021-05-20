---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 7f4b26fc7aca570fb1b1922a51ed77879c3b89b9
workflow-type: tm+mt
source-wordcount: '2002'
ht-degree: 6%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] als Cloud Service.

>[!NOTE]
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen navigieren. z. B. für die 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Dokumentationsaktualisierungen, die nicht direkt mit einer Version in Zusammenhang stehen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.4.0 von [!DNL Adobe Experience Manager] wurde am 6. Mai 2021 veröffentlicht.
Die folgende Version (2021.5.0) wird am 27. Mai 2021 veröffentlicht.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### Neue Funktionen {#what-is-new-foundation}

* [Workflow](/help/operations/replication.md#publish-content-tree-workflow)  Inhaltsstruktur veröffentlichen - Ein neues Workflow-Modell und ein neuer Schritt bieten eine höhere Leistung bei der Veröffentlichung tiefer Hierarchien von Inhalten.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* GraphQL-Endpunkte - Es ist jetzt möglich, die AEM GraphQL-API für einzelne AEM Sites-Konfigurationen zu aktivieren und benutzerdefinierte GraphQL-Endpunkte für diese Konfigurationen zu erstellen, indem eine neue GraphQL-Konsolenbenutzeroberfläche verwendet wird. Die Benutzeroberfläche ermöglicht auch die Verwaltung von GraphQL-Endpunkten.

* Inhaltsmodelle, erweiterter Datums- und Uhrzeitdatentyp - Jetzt ist es möglich, den Datums- und Uhrzeitdatentyp so zu konfigurieren, dass nur noch Datums-, Uhrzeit- oder Datums- und Uhrzeitinformationen für die Bearbeitung zulässig sind.

* Inhaltsmodelle, erweiterter Datentyp Tags - jetzt ist es möglich, den Datentyp Tags so zu konfigurieren, dass das Authoring mit einzelnen oder mehreren Tags möglich ist.

* Inhaltsmodelle, neuer Tabulator-Platzhalterdatentyp - der neue Tabulator-Platzhalterdatentyp ermöglicht die Gruppierung von Datentypen in Abschnitte, die unter Registerkarten im Inhaltsfragment-Editor gerendert werden.

### Fehlerbehebungen in [!DNL Sites] {#bug-fixes-sites}

* Inhaltsfragmente: Durch Verschieben von Inhaltsfragmenten oder Ordnern werden jetzt verschachtelte Verweise innerhalb des Fragments aktualisiert. (CQ-4320815)

* GraphQL - persistente Abfragen unterstützen jetzt benutzerdefinierte Endpunkte, die spezifisch für AEM Sites-Konfigurationen sind. (CQ-4315928)

## [!DNL Adobe Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* [!DNL Experience Manager] archiviert keine einzelnen Asset-Downloads, in die die Originaldatei heruntergeladen wurde. Diese Verbesserung ermöglicht schnellere Downloads.

* Wenn ein Asset über die Option &quot;linkshare&quot;heruntergeladen wird, können Sie jetzt auswählen, ob Sie die Ausgabedarstellungen herunterladen oder nicht. Zuvor wurden alle Asset-Ausgabedarstellungen heruntergeladen.

* Administratoren können [!DNL Experience Manager] so konfigurieren, dass die Quelle von Assets nach der Erfassung von Assets in Batches gelöscht wird. Siehe [Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Ausführen einer Konsistenzprüfung zum Massenimport von Assets bietet Experience Manager jetzt weitere Informationen zu Fehlern. Siehe [Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Importieren von Assets mit dem Tools für den Massenimport haben Administratoren jetzt die Möglichkeit, die Quelldateien zu löschen, nachdem der Import erfolgreich war. Siehe [Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Bearbeiten eines Metadatenschemas ermöglicht ein neues Stammpfadauswahlfeld Administratoren die schnelle und einfache Auswahl, wodurch die Konfigurationszeit verkürzt wird.

* Metadaten vieler Assets können stapelweise mithilfe einer CSV-Datei importiert und in eine CSV-Datei exportiert werden. Das Standarddatumsformat ist jetzt `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Benutzer können ein anderes Format verwenden, indem sie die Spaltenüberschrift aktualisieren. Fügen Sie beispielsweise `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` als Spaltenüberschrift in der CSV-Datei anstelle des Wortes `Date` hinzu.

* Beim Durchsuchen von Assets in der Spaltenansicht zeigt ein visueller Indikator den Status Genehmigt oder Zurückgewiesen für jedes Asset an.

* Beim Durchsuchen von Assets in der Spaltenansicht wird eine visuelle Anzeige für abgelaufene Assets angezeigt.

* Ein Textbereich-Datentyp wird im Metadaten-Editor [!DNL Assets] verfügbar gemacht. Sie können diese Option verwenden, damit Ihre Benutzer Metadaten in ein Freiformtextfeld eingeben können.

### Fehlerbehebungen in [!DNL Assets] {#bug-fixes-assets}

* Beim Versuch, mehrere Assets oder Ordner zu verschieben, wird in der Konsole ein Fehler protokolliert und der Verschiebungsvorgang wird nicht abgeschlossen. Der Vorgang &quot;Verschieben&quot;schlägt fehl, wenn der Titel nicht aktualisiert werden kann. (CQ-4322080)

* Ein Metadatenfeld kann basierend auf einer Regel so ausgeblendet werden, dass die Metadaten nicht obligatorisch sind, wenn eine vordefinierte Bedingung erfüllt ist. Solche ausgeblendeten Metadatenfelder werden jedoch als erforderliche Felder angezeigt. (CQ-4321285)

* Der Massenimport von Metadaten schlägt aufgrund eines falschen Datumsformats fehl. (CQ-4319014)

* Wenn auf der Seite Eigenschaften eine Auswahl getroffen wird, um Metadaten zu aktualisieren, reagiert die Benutzeroberfläche nur langsam, wenn das Schema viele Optionen bereitstellt. (CQ-4318538)

* Beim Aktualisieren und Speichern von Metadatenwerten in einem einzeiligen Textfeld werden die Werte im Dropdown-Menü gelöscht, auch wenn die Bearbeitungen im Dropdown-Menü deaktiviert sind. (CQ-4317077)

* Sie können die Auslassungszeichen als Anmerkung verwenden, um Assets zu überprüfen. Wenn kleine Ellipsen verwendet werden, überschneidet sich die Ellipse mit der Anzahl der Anmerkung in der Druckversion. (CQ-4316792)

## [!DNL Adobe Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

Sie können [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) verwenden, um digitale Formulare zu erstellen, Formulare mit vorhandenen Datenquellen zu verbinden, Formulare mit Adobe Sign zu integrieren, E-Signaturen zu Formularen hinzuzufügen, Datensatzdokument (DoR) zu generieren, um gesendete Formulare als PDF-Dateien zu archivieren. Der Dienst kann auch Ihre bestehenden PDF forms in digitale Formulare konvertieren. Neben den standardmäßigen AEM Forms-Funktionen bietet der Dienst mehrere Cloud-native Funktionen wie automatische Skalierung, Ausfallzeiten bei Upgrades und Cloud-native Entwicklungsumgebungen. Lesen Sie [diesen Blogpost](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) , um mehr über die Funktionen und Funktionen von AEM Forms as a Cloud Service zu erfahren.

* **Authentifizierungsmethode zur Identitätsauthentifizierung von Behörden-IDs in Adobe Sign-aktiviertem adaptiven Forms verwenden**

   Dank fortschrittlicher maschineller Lernalgorithmen ermöglicht der Adobe Sign-Prozess zur Identifikation von Behörden weltweit Unternehmen die Sicherstellung einer hochwertigen Authentifizierung ihrer Empfängeridentität. Jetzt können Sie die Authentifizierungsmethode für die Identitätsauthentifizierung von Behörden-IDs in Adobe Sign-aktiviertem adaptiven Forms verwenden.

   Die Behörden-ID ist eine Premium-Identitätsauthentifizierungsmethode, die den Empfänger anweist, [das Bild eines staatlich ausgestellten Identitätsdokuments (Führerschein, nationale Kennung, Pass)](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html) hochzuladen und dieses Dokument dann zu bewerten, um seine Authentizität sicherzustellen.

* **Unterstützung für die Verwendung von Formularsignaturerlebnissen für asynchrone Übermittlungen adaptiver Formulare**

   Sie können jetzt das Signiererlebnis im Formular für asynchrone adaptive Formularübermittlungen verwenden. Sie können ein adaptives Formular auch in eine [!DNL Experience Manager Sites]-Seite einbetten und das Formular-Signiererlebnis für adaptive Formularübermittlungen verwenden.

* **Unterstützung für die Verwendung einer Variablen zum Angeben einer Anlage beim Vorausfüllen eines adaptiven Formulars für einen Schritt &quot;Aufgabe zuweisen&quot;**

   Beim Vorausfüllen eines adaptiven Formulars für einen Schritt &quot;Aufgabe zuweisen&quot;können Sie jetzt eine Variable vom Typ &quot;document&quot;verwenden, um eine Eingabeanlage für das adaptive Formular auszuwählen.

* **Unterstützung für die Verwendung der Literaloption zum Festlegen eines Werts für eine JSON-Typvariable**

   Sie können die Literaloption verwenden, um Werte für eine JSON-Typvariable im Schritt &quot;set variable&quot;eines AEM-Workflows festzulegen. Mit der Literaloption können Sie eine JSON in Form einer Zeichenfolge angeben.

* **Verwenden der lokalen Entwicklungsumgebung zum Erstellen des Datensatzdokuments (DoR)**

   Sie können eine XDP als Datensatzdokumentvorlage auf Cloud Service-Instanzen und AEM Forms as a Cloud Service SDK (Lokale Entwicklungsumgebung) verwenden. Zuvor war die Unterstützung nur auf Cloud Service-Instanzen beschränkt.

### Fehlerbehebungen in [!DNL Forms] {#bug-fixes-forms}

* Wenn ein adaptives Formular, das so konfiguriert wurde, dass es kein Datensatzdokument generiert, an einen AEM Workflow gesendet wird, der zum Generieren des Datensatzdokuments konfiguriert ist, wird keine Fehlermeldung angezeigt und die Aufgabe kann nicht gesendet werden.

### Weitere Updates {#misc-2021-04-0-forms}

* Um die Erkennung von Inhalten zu vereinfachen, generiert der Dienst jetzt eine Live-Miniaturansicht für XDP-, Dynamic PDF- und Schema-Dateien.
* Möglichkeit zum Verschieben einer PDF-Datei in einen Ordner in der AEM Forms-Benutzeroberfläche.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Unterstützung für Kategorie-UID - Dadurch werden Commerce-Integrationen von Drittanbietern für Systeme freigeschaltet, die Zeichenfolgen für Kategorie-IDs verwenden

* AEM Erweiterung für PWA Studio inkl. Beispielintegration

* Neue CIF-Navigationskernkomponente, die die WCM-Navigationskernkomponente erweitert

* Visueller Indikator für gestaffelte Katalogdaten in AEM Storefront

* Der Commerce-Endpunkt kann jetzt über die Cloud Manager-Benutzeroberfläche konfiguriert werden.

### Fehlerbehebungen {#bug-fixes-commerce}

* Das Feld der Stammkategorie wurde nicht auf der Registerkarte &quot;Commerce&quot;in den Seiteneigenschaften von Kategorieseiten angezeigt


## Cloud Manager {#cloud-manager}

In diesem Abschnitt werden die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0 und 2021.4.0 beschrieben.

### Veröffentlichungsdatum {#release-date-cm-may}

Die Version 2021.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Mai 2021 veröffentlicht.
Die nächste Version ist für den 3. Juni 2021 geplant.

### Neue Funktionen {#what-is-new-may}

* Die Qualitätsregel PackageOverlaps erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Das von einem Cloud Manager-Benutzer heruntergeladene Bereitstellungsprotokoll enthält jetzt Details zu Fehlern und Erfolgsszenarios.

* Beim Pushen von Code an Adobe Git wurden zeitweise auftretende Fehler behoben.

* Das Commerce-Add-on kann jetzt während des Workflows Programm bearbeiten auf Sandbox-Programme angewendet werden.

* Das Erlebnis Bearbeiten des Programms wurde aktualisiert.

* In der Tabelle &quot;Domänennamen&quot;auf der Seite &quot;Umgebungsdetails&quot;werden bis zu 250 Domänennamen per Paginierung angezeigt.

* Auf der Registerkarte &quot;Lösungen&quot;in den Workflows Programm hinzufügen und Programm bearbeiten wird die Lösung angezeigt, selbst wenn für das Programm nur eine Lösung verfügbar ist.

* Die Fehlermeldung im Build-Schrittprotokoll, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes-cm-may}

* Gelegentlich kann der Benutzer neben einer IP-Zulassungsliste einen grünen &quot;aktiven&quot;Status sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Anstatt &quot;gelöschte&quot;Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **DELETED**.

* Einige Qualitätsprobleme vom Typ Code Smell wirkten sich fälschlicherweise auf die Zuverlässigkeitsbewertung aus.

* Da Wildcard-Domänen nicht unterstützt werden, verhindert die Benutzeroberfläche das Senden einer Wildcard-Domäne durch den Benutzer.

* Wenn die Pipelineausführung zwischen Mitternacht und 1 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als die am Vortag erstellte Version.

* Während der Einrichtung des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode Git verwalten auf der Seite Überblick als Link von der Heldenkarte angezeigt.

### Veröffentlichungsdatum {#release-date-cm-april}

Die Version 2021.4.0 von Cloud Manager in AEM as a Cloud Service wurde am 8. April 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-april}

* Die Benutzeroberfläche aktualisiert die Workflows Programm hinzufügen und bearbeiten , um sie intuitiver zu gestalten.

* Ein Benutzer mit den erforderlichen Berechtigungen kann jetzt den Commerce-Endpunkt über die Benutzeroberfläche senden.

* Umgebungsvariablen können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autoren- oder auf Veröffentlichungsinstanz. Erfordert AEM Version `2021.03.5104.20210328T185548Z` oder höher.

* Die Schaltfläche **Git** verwalten wird auch dann auf der Pipelines-Karte angezeigt, wenn keine Pipelines konfiguriert wurden.

* Die Version des von Cloud Manager verwendeten AEM Projektarchetyps wurde auf Version 27 aktualisiert.

* Projekte, die in der Adobe I/O Developer Console von Cloud Manager erstellt wurden, können nicht mehr unbeabsichtigt bearbeitet oder gelöscht werden.

* Wenn ein Benutzer eine neue Umgebung hinzufügt, wird er darüber informiert, dass eine Umgebung nach ihrer Erstellung nicht mehr in eine andere Region verschoben werden kann.

* Umgebungsvariablen können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autoren- oder auf Veröffentlichungsinstanz. Erfordert AEM Version 2021.03.5104.20210328T185548Z oder höher.

* Die Fehlermeldung beim Starten einer Pipeline beim Löschen einer Umgebung wurde geklärt.

* Von Eclipse-Projekten bereitgestellte OSGi-Bundles sind jetzt von der Regel `CQBP-84--dependencies` ausgeschlossen.

### Fehlerbehebungen {#bug-fixes-cm-april}

* Beim Bearbeiten der Seite Erlebnisprüfung einer Pipeline führt ein Eingabepfad, der mit einem Schrägstrich `( / )` beginnt, nicht mehr dazu, dass der Schritt im Status &quot;Ausstehend&quot;feststeckt.

* Wenn beim Erstellen einer neuen Produktions-Pipeline vom Benutzer keine Überschreibung bei der Inhaltsprüfung hinzugefügt wird, wurde die standardmäßige Homepage nicht geprüft.

* Probleme für `CloudServiceIncompatibleWorkflowProcess` hatten den falschen Schweregrad in der herunterladbaren CSV-Datei des Problems.

* Die `Runmode`-Prüfung erzeugte Fehlalarme auf Nicht-Ordner-Knoten.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.4.0 des Content Transfer Tool wurde am 11. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-may}

* Diese Version des Content Transfer Tool erstellt Textausgabeformate für Assets, die in Cloud Service migriert werden. Textausgabeformate sind erforderlich, um die Volltextsuche in aufgenommenen Assets zu unterstützen.
* Die maximale Anzahl der Migrationssätze für das Content Transfer Tool, die ein Benutzer erstellen kann, wurde von 4 auf 10 erhöht.

### Fehlerbehebungen {#bug-fixes-ctt-may}

* Mehrere Fehlerbehebungen im Zusammenhang mit der Funktion zur automatischen Aktualisierung in der Benutzeroberfläche des Content Transfer Tool.
* Content Transfer Tool mit `wipe=true` führte zu einem falschen Zählerindex auf dem Ziel. Dieses Problem wurde behoben.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.12 von Best Practices Analyzer wurde am 12. April 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-bpa-april}

* Im BPA-Bericht wurden doppelte Zeilen angezeigt. Dieses Problem wurde behoben.
* In der BPA-Benutzeroberfläche in AEM Version 6.4.2 wurde ein JS-Fehler ausgegeben, der die Schaltfläche Bericht generieren deaktiviert hat. Dieses Problem wurde behoben

