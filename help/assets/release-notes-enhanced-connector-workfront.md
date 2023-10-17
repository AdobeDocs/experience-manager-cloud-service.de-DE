---
title: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
description: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: f5f2c460815d273fe445c6f415dee7776cc18fce
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 84%

---

# Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!DNL Workfront for Experience Manager enhanced connector]

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für die neueste Version 1.9.14 von [!DNL Workfront for Experience Manager enhanced connector] 13. Oktober 2023.

## Die Highlights der Version {#release-highlights}

Die neueste Version der [!DNL Workfront for Experience Manager enhanced connector] umfasst die folgenden Fehlerbehebungen:

* Wenn Ereignisabonnements unter Erweiterte Einstellungen deaktiviert sind, können Sie weiterhin die Optionen für **Abonnieren von Dokumentaktualisierungsereignissen zur Aktualisierung AEM Asset-Metadaten**, **Alle Projekt-Assets nach Abschluss des Projekts in Brand Portal veröffentlichen**, und **Kommentarsynchronisierung aktivieren**.

* Einige der in Experience Manager gespeicherten Assets werden bei der Vorschau in Workfront nicht ordnungsgemäß dargestellt.

* Bei der Neukonfiguration der Experience Manager-Verbindung mit Workfront werden Ereignisabonnements wie die Aktualisierung von Kommentaren, das Löschen und das Aktualisieren von Dokumenten nicht erfolgreich erstellt.

* Wesentliche API-Leistungsverbesserungen für die Erstellung verknüpfter Ordner, Aktualisierung, Aktivierung verknüpfter Ordner, Aktivierung und Deaktivierung der Kommentarsynchronisierung, erweiterte Speicherung der Einstellungen im Connector.


>[!NOTE]
>
>AEM 6.4 hat das Ende des erweiterten Supports erreicht. Weitere Informationen finden Sie in unseren [technischen Supportzeiträumen](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Die unterstützten Versionen finden Sie [hier](https://experienceleague.adobe.com/docs/?lang=de).


>[!IMPORTANT]
>
>Adobe empfiehlt eine [Aktualisierung auf die neueste Version 1.9.14](/help/assets/workfront-connector-install.md) des [!DNL Workfront for Experience Manager enhanced connector].

## Bekannte Probleme {#known-issues}

* Beim Konfigurieren von projektverknüpften Ordnern mit AEM 6.4 speichert Experience Manager die Werte für die Felder **[!UICONTROL Unterordner]** und **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** nicht. Der Wert für das Feld **[!UICONTROL Unterordner]** wird auf **[!UICONTROL undefiniert]** und der Wert für das Feld **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** wird nach dem Speichern der Konfiguration automatisch auf **[!UICONTROL Standardportfolio]** aktualisiert.

* Wenn Sie das klassische Workfront-Erlebnis verwenden, können Sie mit der Option **[!UICONTROL Senden an]** in der Dropdown-Liste **[!UICONTROL Mehr]** das Ziel in Experience Manager nicht auswählen. Die Option **[!UICONTROL Senden an]** funktioniert korrekt über die Dropdown-Liste **[!UICONTROL Dokumentenaktionen]**. Die Option **[!UICONTROL Senden an]** funktioniert korrekt für die Dropdown-Liste **[!UICONTROL Mehr]** und die Dropdown-Liste **[!UICONTROL Dokumentenaktionen]**, die in dem neuen Workfront-Erlebnis verfügbar sind.

## Frühere Versionen {#previous-releases}

### Version September 2023 {#september-2023-release}

* Der erweiterte Connector für Experience Manager ruft alle Ereignisabonnements von Workfront ab, während ein Ereignisabonnement für ein Projekt gelöscht wird, was sich auf die Leistung der Anwendung auswirkt.

* Wenn ein Asset von Workfront an Experience Manager gesendet wird, wird der Asset-MIME-Typ nicht auf `dc:format` -Attribut in Experience Manager.

* Workfront-Projekt-IDs, die auf dem erweiterten Connector für Experience Manager gespeichert werden, umfassen Duplikate.

### Version August 2023 {#august-2023-release}

* Verknüpfte Ordner können nicht in Experience Manager erstellt werden, da dem verknüpften Ordner kein Benutzerkonto zugeordnet ist.

* Wettlaufsituationen bei Metadaten-Aktualisierungen für ein Asset in Experience Manager.

### Version vom Juni 2023 {#june-2023-release}

* Wenn Sie erweiterte Netzwerke konfiguriert haben, treten beim Senden von Inhalten von Adobe Workfront an AEM as a Cloud Service Probleme auf.


### Version Mai 2023 {#may-2023-release}

* Workfront gibt eine 409-HTTP-Antwort für doppelte Ereignis-Abonnements zurück, die auf einem REST-Aufruf von Experience Manager an Workfront basiert. Dies führt zu einer Null Pointer-Ausnahme.

### Version April 2023 {#april-2023-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.9, veröffentlicht am 10. April 2023, enthält folgende Aktualisierungen:

* Experience Manager zeigt eine `DateTimeParseException`-Ausnahme an, wenn es während der Erstellung eines verknüpften Ordners das Datum der letzten Änderung von Workfront erhält.

* Probleme beim Erstellen mehrerer verknüpfter Projektordner innerhalb einer kurzen Dauer.

* Es ist nicht möglich, eine Schwellenwertbegrenzung für die Anzahl neuer Ordner zu konfigurieren, die mit Projekten verknüpft sind.

### Version März 2023 {#march-2023-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.8, veröffentlicht am 03. März 2023, enthält folgende Aktualisierungen:

* Leistungsverbesserungen in Experience Manager beim Erstellen von projektbezogenen Ordnern in Workfront.

* Das Löschen von Kommentaren in Workfront wird jetzt in Experience Manager angezeigt.

* Die Möglichkeit zur Verwaltung der Blockierung von Neukundinnen oder Neukunden auf Experience Manager as a Cloud Service durch Konfiguration des Connectors.


### Version Januar 2023 {#january-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.7, veröffentlicht am 02. Februar 2023, enthält folgende Aktualisierungen:

* Der Metadaten-Editor listet die benutzerdefinierten Workfront-Formulareigenschaften nach der Installation der Version 1.9.6 nicht auf.

* Die Dev-Konsole zeigt die Fehlermeldung `/content/dam/jcr:content/metadata/wfProjectURL not found` an, nachdem der erweiterte Workfront-Connector installiert und die Assets-Startseite geöffnet wurde.

### Version Dezember 2022 {#december-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.6, veröffentlicht am 9. Dezember, enthält folgende Aktualisierungen:

**Verbesserung**

<!--

* Workfront enhanced connector now lets you use new search parameters to be more specific while defining folder names on large repositories.

-->

* Der erweiterte Workfront-Connector unterstützt jetzt die Volltextsuche nach Assets und Ordnern.

**Fehlerbehebungen**

* Die Metadaten der Dokumentversion werden nicht ordnungsgemäß zwischen Workfront und Experience Manager synchronisiert.
* Probleme beim Erstellen eines Ordners, der mit Experience Manager in Workfront verknüpft ist, wenn der Ordner ein Schema verwendet, für das in der globalen Konfiguration eine Definition fehlt.
* Das Formular des Metadatenschema-Editors reagiert nicht mehr beim Klicken auf ein Feld, wenn die Ladezeit länger als erwartet ist. Es wurde eine spezifische OSGi-Konfiguration für benutzerdefinierte Formulare hinzugefügt, um das Problem zu beheben. Die Namen der benutzerdefinierten Formulare, die Sie dem Metadatenschema-Editor hinzufügen, sind in den Protokollen verfügbar.

### Version vom November 2022 {#november-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.5, veröffentlicht am 11. November, enthält folgende Aktualisierungen:

* Wenn Sie in Workfront nur einen Wert für ein Feld mit mehreren Werten definieren, wird der Feldwert nicht richtig Experience Manager zugeordnet.

* Experience Manager zeigt beim Zugriff auf die Asset-Ordner im Bildschirm **[!UICONTROL Verknüpfen externer Dateien und Ordner]** aufgrund ungültiger Berechtigungen für `/content/dam/collections` die Meldung `SERVER_ERROR` an.

* Durch Aktivieren der Option **[!UICONTROL Veröffentlichen von Assets in Brand Portal]** auf der Seite mit der erweiterten Connector-Konfiguration von Workfront wird ein falsches Ereignis erstellt. Das Ereignis wird selbst nach dem Deaktivieren der Option nicht gelöscht.

  Gehen Sie folgendermaßen vor, um das Problem zu lösen:

   1. Aktualisieren Sie auf Version 1.9.5 des erweiterten Connectors.

   1. Deaktivieren Sie die Option **[!UICONTROL Veröffentlichen von Assets in Brand Portal]** in den erweiterten Einstellungen.

   1. Aktivieren Sie die Option **[!UICONTROL Assets in Brand Portal veröffentlichen]**.

   1. Löschen Sie die falschen Ereignisabonnements.

      1. Ausführen von GET-Aufrufen an `/attask/eventsubscription/api/v1/subscriptions?page=<page-number>`

         Führen Sie für jede Seitenzahl einen API-Aufruf aus.

      1. Suchen Sie nach dem folgenden Text, um Ereignisabonnements zu finden, die der folgenden URL entsprechen und keine `objId` aufweisen:

         ```
              "objId": "",
             "url": "<your-aem-domain>/bin/workfront-tools/events/linkedfolderprojectupdate<your-aem-domain>/
         ```

         Stellen Sie sicher, dass der Inhalt zwischen `"objId": "",` und `"url"` der JSON-Antwort entspricht. Die empfohlene Methode dazu besteht darin, dies aus jedem Ereignisabonnement zu kopieren, das über eine `objId` verfügt, und dann die Nummer zu löschen.

      1. Notieren Sie die Ereignisabonnement-ID.

      1. Löschen Sie das falsche Ereignisabonnement. Führen Sie einen Delete-API-Aufruf für `<your-aem-domain>/attask/eventsubscription/api/v1/subscriptions/<event-subscription-ID-from-previous-step>` durch.

         `200` als Antwort-Code gibt das erfolgreiche Löschen falscher Ereignisabonnements an.
  >[!NOTE]
  >
  >Wenn Sie die falschen Ereignisabonnements bereits gelöscht haben, bevor Sie die in diesem Verfahren genannten Schritte ausführen, können Sie den letzten Schritt dieses Verfahrens überspringen.

### Version Oktober 2022 {#october-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.4 vom 7. Oktober enthält folgende Aktualisierungen:

* Aufgrund einer großen Anzahl von Ereignissen kann die Registerkarte „Ereignisabonnements“ auf der Seite mit der erweiterten Connector-Konfiguration nicht angezeigt werden.

* Workfront kann die Liste der in einem Projekt vorhandenen Ordner nicht abrufen, was zur Erstellung doppelter Ordner führt.

### Version September 2022 {#september-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.3 vom 16. September enthält folgende Aktualisierungen:

* Dateien mit einer Größe von mehr als 8 GB können nicht hochgeladen werden.
* Probleme beim automatischen Veröffentlichen von Assets, die von Workfront an AEM gesendet werden.
* Das Feld „Stammpfad“ ist beim Bearbeiten eines standardmäßigen Metadatenschema-Formulars nicht für das Feld „Tags“ verfügbar.
* Probleme beim Hinzufügen neuer Versionen in Workfront mithilfe von AEM Workflows.
* Wenn Sie eine AEM Suche nach in Workfront verfügbaren Assets durchführen, zeigt AEM eine Fehlermeldung an.
* Wenn Sie einen AEM-Workflow für die Aufgabenerstellung aus einem Asset erstellen und keinen Namen einer übergeordneten Aufgabe definieren, wird die Aufgabe in Workfront nicht erstellt.

### Version August 2022 {#august-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.2 vom 3. August enthält folgende Aktualisierungen:

* Mit dem Workflow-Schritt **[!UICONTROL Dokument hochladen]** kann kein Dokument an Workfront angehängt werden.

* Mit dem Workflow-Schritt **[!UICONTROL Dokument hochladen]** kann kein Dokument an Aufgaben und Probleme in Workfront angehängt werden. Mit dem Workflow-Schritt kann ein Dokument erfolgreich an Projekte angehängt werden.

### Version vom Juli 2022 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.1 enthält die folgenden Aktualisierungen:

* Die Authentifizierung zwischen Experience Manager und Workfront-Anwendungen mithilfe des Workfront-API-Schlüssels für Instanzen, die zu Adobe IMS migriert wurden, wird nun unterstützt.

* Wenn Sie externe Dateien oder Ordner verknüpfen, zeigt die Workfront-Anwendung die Fehlermeldung `SERVER_ERROR` an. Die Fehlermeldung bezieht sich auf die Ausnahme „Nicht autorisiert“ aufgrund von nicht übereinstimmenden API-Schlüsseln.

* Wenn Sie den Workflow „Aufgabe erstellen“ für ein Asset ausführen, wird die Ausnahme „Null Pointer“ in den Protokollmeldungen angezeigt.

* Wenn Sie die `Replace Spaces with DASH`-Konfigurationsoption unter „Erweiterte Einstellungen“ in Experience Manager aktivieren, führt dies zu einer doppelten Ordnererstellung in Workfront.

### Version vom Juni 2022 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] umfasst jetzt die folgenden Updates:

* Wenn Sie einen Upload über einen verknüpften Ordner durchführen oder die in Workfront verfügbare Aktion `Send To` verwenden, um Assets in Experience Manager as a Cloud Service hochzuladen, werden die Assets beschädigt und können nicht in Adobe Photoshop geöffnet werden.

### Version vom März 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] umfasst jetzt die folgenden Updates:

* Sie können jetzt zwischen Adobe Workfront und AEM Assets as a Cloud Service verknüpfte Ordner erstellen, auch wenn es mehrere Konfigurationen für verknüpfte Projektordner gibt.

* Es wurde Unterstützung für die Paginierung von Ereignisabonnements hinzugefügt.

* Es wurde Unterstützung für AEM 6.4.x hinzugefügt.

* Es wurde Unterstützung für Proxy-Umgebungen hinzugefügt.

* Verschiedene Fehlerkorrekturen auf der Grundlage von Partner- und Kunden-Feedback.

>[!MORELIKETHIS]
>
>* [Integrieren von [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=de)
