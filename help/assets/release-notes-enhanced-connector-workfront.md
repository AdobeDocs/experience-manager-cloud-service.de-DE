---
title: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
description: Versionshinweise für  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 86%

---

# Versionshinweise für [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!DNL Workfront for Experience Manager enhanced connector]

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für die neueste Version 1.9.6 von [!DNL Workfront for Experience Manager enhanced connector] ist der 9. Dezember 2022.

## Die Highlights der Version {#release-highlights}

Die neueste Version von [!DNL Workfront for Experience Manager enhanced connector] enthält die folgenden Verbesserungen und Fehlerbehebungen:

**Verbesserung**

<!--

* Workfront enhanced connector now allows you to use new search parameters to be more specific while defining folder names on large repositories.

-->

* Der erweiterte Workfront-Connector unterstützt jetzt die Volltextsuche nach Assets und Ordnern.

**Fehlerbehebungen**

* Die Metadaten der Dokumentversion werden nicht ordnungsgemäß zwischen Workfront und Experience Manager synchronisiert.
* Probleme beim Erstellen eines Ordners, der mit Experience Manager in Workfront verknüpft ist, wenn der Ordner ein Schema verwendet, für das in der globalen Konfiguration eine Definition fehlt.
* Das Formular des Metadatenschema-Editors reagiert nicht mehr, wenn Sie auf ein Feld klicken, da die Ladezeit länger als erwartet ist. Es wurde eine spezifische OSGi-Konfiguration für benutzerdefinierte Formulare hinzugefügt, um das Problem zu beheben. Die Namen der benutzerdefinierten Formulare, die Sie dem Metadatenschema-Editor hinzufügen, sind in den Protokollen verfügbar.

>[!IMPORTANT]
>
>Adobe empfiehlt eine [Aktualisierung auf die neueste Version 1.9.6](../assets/update-workfront-enhanced-connector.md) des [!DNL Workfront for Experience Manager enhanced connector].

## Bekannte Probleme {#known-issues}

* Beim Konfigurieren von projektverknüpften Ordnern mit AEM 6.4 speichert Experience Manager die Werte für die Felder **[!UICONTROL Unterordner]** und **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** nicht. Der Wert für das Feld **[!UICONTROL Unterordner]** wird auf **[!UICONTROL undefiniert]** und der Wert für das Feld **[!UICONTROL Verknüpften Ordner in Projekten mit Portfolio erstellen]** wird nach dem Speichern der Konfiguration automatisch auf **[!UICONTROL Standardportfolio]** aktualisiert.

* Wenn Sie das klassische Workfront-Erlebnis verwenden, können Sie mit der Option **[!UICONTROL Senden an]** in der Dropdown-Liste **[!UICONTROL Mehr]** das Ziel in Experience Manager nicht auswählen. Die Option **[!UICONTROL Senden an]** funktioniert korrekt, wenn sie die Dropdown-Liste **[!UICONTROL Dokumentaktionen]** verwenden. Die Option **[!UICONTROL Senden an]** funktioniert sowohl in der Dropdown-Liste **[!UICONTROL Mehr]** als auch in der Dropdown-Liste **[!UICONTROL Dokumentaktionen]**, die in der neuen Workfront-Version verfügbar ist.

## Frühere Versionen {#previous-releases}

### Version November 2022 {#november-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] Version 1.9.5, die am 11. November veröffentlicht wurde, enthält folgende Aktualisierungen:

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

* Wenn Sie einen Upload über einen verknüpften Ordner durchführen oder die in Workfront verfügbare `Send To`-Aktion verwenden, um Assets in Experience Manager as a Cloud Service hochzuladen, werden die Assets beschädigt und können nicht in Adobe Photoshop geöffnet werden.

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
>* [Integrieren von [!DNL Workfront for Experience Manager enhanced connector] mit Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=de)