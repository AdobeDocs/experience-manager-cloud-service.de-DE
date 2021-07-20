---
title: Versionshinweise für Version 2021.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: e3540331e3194dce5dcd88e4f785f15ef682f062
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 92%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service wiurde am 6. Mai 2021 veröffentlicht.
Die folgende Version (2021.5.0) wurde am 27. Mai 2021 veröffentlicht.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### Neue Funktionen {#what-is-new-foundation}

* [Workflow zum Veröffentlichen der Inhaltsstruktur](/help/operations/replication.md#publish-content-tree-workflow) – Ein neues Workflow-Modell und ein neuer Schritt bieten eine höhere Leistung bei der Veröffentlichung tiefer Inhalts-Hierarchien.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* GraphQL-Endpunkte – Es ist jetzt möglich, die AEM-GraphQL-API für einzelne AEM Sites-Konfigurationen zu aktivieren und benutzerdefinierte GraphQL-Endpunkte für diese Konfigurationen zu erstellen, indem eine neue GraphQL-Konsolenbenutzeroberfläche verwendet wird. Die Benutzeroberfläche ermöglicht auch die Verwaltung von GraphQL-Endpunkten.

* Inhaltsmodelle, erweiterter Datums- und Uhrzeitdatentyp – Jetzt ist es möglich, den Datums- und Uhrzeitdatentyp so zu konfigurieren, dass nur Datums- oder nur Uhrzeit- oder Datums- und Uhrzeitinformationen für die Bearbeitung zulässig sind.

* Inhaltsmodelle, erweiterter Datentyp Tags – Jetzt ist es möglich, den Datentyp Tags so zu konfigurieren, dass die Inhaltserstellung mit einzelnen oder mehreren Tags möglich ist.

* Inhaltsmodelle, neuer Datentyp Registerkarten-Platzhalter – Der neue Datentyp Registerkarten-Platzhalter ermöglicht die Gruppierung von Datentypen in Abschnitte, die unter Registerkarten im Inhaltsfragment-Editor gerendert werden.

### Fehlerbehebungen in [!DNL Sites] {#bug-fixes-sites}

* Inhaltsfragmente – Durch Verschieben von Inhaltsfragmenten oder Ordnern werden jetzt verschachtelte Verweise innerhalb des Fragments aktualisiert. (CQ-4320815)

* GraphQL – Persistente Abfragen unterstützen jetzt benutzerdefinierte Endpunkte, die spezifisch für AEM Sites-Konfigurationen sind. (CQ-4315928)

## [!DNL Adobe Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* [!DNL Experience Manager] archiviert keine einzelnen Asset-Downloads, wo die Originaldatei heruntergeladen wird. Diese Verbesserung ermöglicht schnellere Downloads.

* Wenn ein Asset über die Option &quot;linkshare&quot;heruntergeladen wird, können Sie jetzt auswählen, ob Sie die Ausgabedarstellungen herunterladen oder nicht. Zuvor wurden alle Asset-Ausgabedarstellungen heruntergeladen.

* Administratoren können [!DNL Experience Manager] so konfigurieren, dass die Quelle von Assets nach der Erfassung von Assets in Batches gelöscht wird. Siehe [Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Ausführen einer Konsistenzprüfung zum Massenimport von Assets bietet Experience Manager jetzt weitere Informationen zu Fehlergründen. Siehe [Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Importieren von Assets mit dem Tools für den Massenimport haben Administratoren jetzt die Möglichkeit, die Quelldateien zu löschen, nachdem der Import erfolgreich war. Siehe [Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

* Beim Bearbeiten eines Metadatenschemas ermöglicht ein neues Stammpfadauswahlfeld Administratoren die schnelle und einfache Auswahl, wodurch die Konfigurationszeit verkürzt wird.

* Beim Bearbeiten eines Metadatenschemas wird ein Datentyp hinzugefügt, der einen Freiformtextbereich im Metadaten-Editor bereitstellt. Benutzer können diesen Textbereich verwenden, um Freiformtext als Metadaten eines Assets einzugeben. Siehe [Metadatenschema-Editor](/help/assets/metadata-schemas.md).

* Metadaten vieler Assets können massenhaft mithilfe einer CSV-Datei importiert und in eine CSV-Datei exportiert werden. Das Standarddatumsformat ist jetzt `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Benutzer können ein anderes Format verwenden, indem sie die Spaltenüberschrift ändern. Fügen Sie in der CSV-Datei beispielsweise `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` als Spaltenüberschrift anstelle des Wortes `Date` hinzu.

* Beim Durchsuchen von Assets in der Spaltenansicht zeigt ein visueller Indikator für jedes Asset den Status Genehmigt oder Abgelehnt an.

* Beim Durchsuchen von Assets in der Spaltenansicht werden abgelaufene Assets mit einem visuellen Indikator angezeigt.

### Fehlerbehebungen in [!DNL Assets] {#bug-fixes-assets}

* Beim Versuch, mehrere Assets oder Ordner zu verschieben, wird in der Konsole ein Fehler protokolliert und der Verschiebungsvorgang wird nicht abgeschlossen. Der Vorgang „Verschieben“ schlägt fehl, wenn der Titel nicht aktualisiert werden kann. (CQ-4322080)

* Ein Metadatenfeld kann basierend auf einer Regel so ausgeblendet werden, dass die Metadaten nicht obligatorisch sind, wenn eine vordefinierte Bedingung erfüllt ist. Solche ausgeblendeten Metadatenfelder werden jedoch als Pflichtfelder angezeigt. (CQ-4321285)

* Der Massenimport von Metadaten schlägt aufgrund eines falschen Datumsformats fehl. (CQ-4319014)

* Wenn auf der Seite Eigenschaften eine Auswahl getroffen wird, um Metadaten zu aktualisieren, reagiert die Benutzeroberfläche nur langsam, wenn das Schema viele Optionen bietet. (CQ-4318538)

* Beim Aktualisieren und Speichern von Metadatenwerten in einem einzeiligen Textfeld werden die Werte im Dropdown-Menü gelöscht, auch wenn die Bearbeitung im Dropdown-Menü deaktiviert ist. (CQ-4317077)

* Sie können die Auslassungszeichen für Anmerkungen verwenden, um Assets zu überprüfen. Wenn kleine Auslassungszeichen verwendet werden, überschneiden sie sich in der Druckversion mit der Nummer der Anmerkung. (CQ-4316792)

* Die Option für die schnelle Veröffentlichung wird nicht angezeigt, wenn nach der Suche ein Asset aus den Suchergebnissen ausgewählt wird. (CQ-4317748)

## [!DNL Adobe Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Identitätsauthentifizierungs-Methode Amtlicher Lichtbildausweis in Adobe Sign-fähigen adaptiven Formularen verwenden**

   Mit dem auf fortschrittlichen Algorithmen des maschinellen Lernens basierenden Verfahrens für amtliche Lichtbildausweise in Adobe Sign können Unternehmen auf der ganzen Welt eine hochwertige Authentifizierung der Identität ihrer Empfänger sicherstellen. Jetzt können Sie die Methode der Identitätsauthentifizierung über amtliche Lichtbildausweise in Adobe Sign-fähigen adaptiven Formularen verwenden.

   Amtlicher Lichtbildausweis ist eine erstklassige Identitätsauthentifizierungsmethode, die den Empfänger anweist, [das Bild eines staatlich ausgestellten Identitätsdokuments (Führerschein, Personalausweis, Pass) hochzuladen](https://helpx.adobe.com/de/sign/using/adobesign-authentication-government-id.html) und dieses Dokument dann bewertet, um seine Authentizität sicherzustellen.

* **Unterstützung für die Verwendung von Formularsignierlebnissen für asynchrone Übermittlungen adaptiver Formulare**

   Sie können jetzt das Formularsigniererlebnis für asynchrone Übermittlungen adaptiver Formulare verwenden. Sie können ein adaptives Formular auch in eine [!DNL Experience Manager Sites]-Seite einbetten und das Formularsigniererlebnis für Übermittlungen adaptiver Formulare verwenden.

* **Unterstützung für die Verwendung einer Variablen zum Angeben einer Anlage beim Vorausfüllen eines adaptiven Formulars für einen Schritt „Aufgabe zuweisen“**

   Beim Vorausfüllen eines adaptiven Formulars für einen Schritt „Aufgabe zuweisen“ können Sie jetzt eine Variable vom Typ „document“ verwenden, um eine Anlage als Input für das adaptive Formular auszuwählen.

* **Unterstützung für die Verwendung der Option „Literal“ zum Festlegen eines Werts für eine JSON-Typvariable**

   Sie können die Option „Literal“ verwenden, um Werte für eine JSON-Typvariable im Schritt „set variable“ eines AEM-Workflows festzulegen. Mit der Option „Literal“ können Sie eine JSON in Form einer Zeichenfolge angeben.

* **Verwenden der lokalen Entwicklungsumgebung zum Erstellen des aufzuzeichnenden Dokuments (DoR)**

   in Cloud Service-Instanzen und im AEM Forms as a Cloud Service-SDK (Lokale Entwicklungsumgebung) können Sie einen XDP als Vorlage für das aufzuzeichnende Dokument verwenden. Zuvor war die Unterstützung auf Cloud Service-Instanzen beschränkt.

### Fehlerbehebungen in [!DNL Forms] {#bug-fixes-forms}

* Wenn ein adaptives Formular, das so konfiguriert wurde, dass es kein aufzuzeichnendes Dokument (DoR) generiert, an einen AEM-Workflow gesendet wird, der zum Generieren des DoR konfiguriert ist, wird keine Fehlermeldung angezeigt und die Aufgabe kann nicht gesendet werden.

### Weitere Updates {#misc-2021-04-0-forms}

* Um die Erkennung von Inhalten zu vereinfachen, generiert der Service jetzt eine Live-Miniaturansicht für XDP-, Dynamic PDF- und Schema-Dateien.
* Hinzufügen der Möglichkeit in der AEM Forms-Benutzeroberfläche, eine PDF-Datei in einen eingefügten Ordner zu verschieben.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Unterstützung für Kategorie-UID – Dadurch werden Commerce-Integrationen von Drittanbietern für Systeme freigeschaltet, die Zeichenfolgen für Kategorie-IDs verwenden

* AEM-Erweiterung für PWA Studio inkl. Beispielintegration

* Neue CIF-Navigationskernkomponente, die die WCM-Navigationskernkomponente erweitert

* Visueller Indikator für gestaffelte Katalogdaten in der AEM-Storefront

* Der Commerce-Endpunkt kann jetzt über die Cloud Manager-Benutzeroberfläche konfiguriert werden.

### Fehlerbehebungen {#bug-fixes-commerce}

* Das Feld „Stammkategorie“ wurde auf der Registerkarte „Commerce“ in den Seiteneigenschaften von Kategorieseiten nicht angezeigt

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0.

### Veröffentlichungsdatum {#release-date-cm-april}

Das Veröffentlichungsdatum für Cloud Manager in AEM as a Cloud Service 2021.4.0 war der 08. April 2021.
Die folgende Version wurde am 06. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-april}

* Die Benutzeroberfläche der Workflows „Programm hinzufügen“ und „Programm bearbeiten“ wurde aktualisiert, um sie intuitiver zu gestalten.

* Ein Benutzer mit den erforderlichen Berechtigungen kann jetzt den Commerce-Endpunkt über die Benutzeroberfläche übermitteln.

* Umgebungsvariablen können jetzt auf einen bestimmten Service übertragen werden, entweder in der Autoren- oder der Veröffentlichungsinstanz. Erfordert AEM Version `2021.03.5104.20210328T185548Z` oder später.

* Die Schaltfläche **Git verwalten** wird auch dann auf der Karte „Pipelines“ angezeigt, wenn keine Pipelines konfiguriert wurden.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 27 aktualisiert.

* Projekte in der Adobe I/O-Entwickerkonsole, die von Cloud Manager erstellt wurden, können nicht mehr unbeabsichtigt bearbeitet oder gelöscht werden.

* Wenn ein Benutzer eine neue Umgebung hinzufügt, wird er darüber informiert, dass eine Umgebung nach ihrer Erstellung nicht mehr in eine andere Region verschoben werden kann.

* Umgebungsvariablen können jetzt auf einen bestimmten Service übertragen werden, entweder in der Autoren- oder der Veröffentlichungsinstanz. Erfordert AEM Version 2021.03.5104.20210328T185548Z oder später.

* Die Fehlermeldung beim Starten einer Pipeline nach dem Löschen einer Umgebung wurde präzisiert.

* Von Eclipse-Projekten bereitgestellte OSGi-Bundles sind jetzt von der Regel `CQBP-84--dependencies` ausgeschlossen.

### Fehlerbehebungen {#bug-fixes-cm-april}

* Beim Bearbeiten der Seite „Erlebnisprüfung“ einer Pipeline führt ein Eingabepfad, der mit einem Schrägstrich `( / )` beginnt, nicht mehr dazu, dass der Schritt im Status „Ausstehend“ feststeckt.

* Wenn beim Erstellen einer neuen Produktions-Pipeline vom Benutzer keine Überschreibung bei der Inhaltsprüfung hinzugefügt wird, findet jetzt trotzdem eine Überprüfung der standardmäßigen Homepage statt.

* Bei Problemen des Typs `CloudServiceIncompatibleWorkflowProcess` wird jetzt der richtige Schweregrad in der herunterladbaren CSV-Datei des Problems angegeben.

* Die `Runmode`-Prüfung erzeugt jetzt keine Fehlalarme mehr auf Nicht-Ordner-Knoten.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.12 wurde am 12. April 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-bpa-april}

* Im BPA-Bericht wurden doppelte Zeilen angezeigt. Dieses Problem wurde behoben.
* In der BPA-Benutzeroberfläche in AEM Version 6.4.2 wurde ein JS-Fehler ausgegeben, der die Schaltfläche „Bericht generieren“ deaktivierte. Dieses Problem wurde behoben

