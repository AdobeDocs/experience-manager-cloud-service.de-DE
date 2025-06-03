---
title: Erste Schritte mit Refaktorierungs-Tools
description: Erfahren Sie mehr über die ersten Schritte mit den Refaktorierungs-Tools in AEM as a Cloud Service
source-git-commit: 20bb756c4a2eb37341da4582f19cf41e4d60304a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---

# Erste Schritte mit Refaktorierungs-Tools {#getting-started-refactoring-tools}

## Verfügbarkeit {#availability}

<!-- Alexandru: duplicate contextualhelp id, drafting this for now

>[!CONTEXTUALHELP]
>id="aemcloud_rs_upload"
>title="Download"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=de" text="Release Notes"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

-->

## Ausführen der Refaktorierungs-Tools {#running-refactoring-tools}

Verwenden Sie das Refaktorierungs-Tool, um Ihren Code aus Kompatibilitätsgründen mit AEM as a Cloud Service zu migrieren.

1. Wenn Sie noch kein CAM-Projekt erstellt haben, lesen Sie den Abschnitt [Erstellen und Verwalten eines Projekts in CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md#create-project).
1. Klicken Sie auf die Karte **Code** Umgestaltung“, um den Quell-Code hochzuladen.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam1.png)

1. Wenn Sie zum ersten Mal auf die **Source-Code** Ansicht zugreifen, wird ein leerer Status angezeigt, der Sie auffordert, Ihren Quellcode hochzuladen.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam2.png)

&#x200B;---

## Hochladen von Source-Code {#uploading}

Wenn Kunden zum ersten Mal auf **Refaktorierungs-Tools** zugreifen, wird ihnen in der **Source-Code-Ansicht ein leerer Status**. Gehen Sie wie folgt vor, um Ihr Projekt hochzuladen und den Inspektionsprozess zu starten:

1. **Zugriff auf die Projekt-Upload-Seite**\
   Klicken Sie auf die **Projekt-Upload**-Schaltfläche in leerem Status, um den Upload-Prozess zu starten.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam3.png)

1. **Source-Code hochladen**
   - Wählen Sie im Dialogfeld „Hochladen“ Ihre ZIP-Quellcodedatei aus.
   - Klicken Sie **Hochladen**, um zu beginnen.
   - Der Upload-Fortschritt wird im Dialogfeld angezeigt. Die Dauer hängt von der Größe Ihres Projekts ab.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam4.png)

1. **Inspektionsprozess**
   - Nach dem Hochladen beginnt **Inspektionsprozess** automatisch im Hintergrund.
   - In der **Source-Code** Ansicht wird jetzt Ihr hochgeladenes Projekt und sein Prüfungsstatus angezeigt.

1. **Inspektionsstatus** Der Inspektionsprozess vereinfacht die Ausführung von Umgestaltungswerkzeugen, indem der Aufwand für manuelle Konfigurationen reduziert wird.

   Die Inspektion zeigt einen der folgenden Status an:
   - **Läuft** - Die Überprüfung ist in Bearbeitung.
   - **Bereit** - Die Inspektion ist abgeschlossen. Sie können jetzt Umgestaltungs-Tools ausführen.
   - **Fehlgeschlagen** - Fehler aufgetreten. Klicken Sie auf das Projekt, um den Inspektionsbericht zu überprüfen und Probleme zu beheben.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam5.png)

>[!NOTE]
>Beim Hochladen eines neuen Projekts wird das vorhandene gelöscht. Stellen Sie sicher, dass alle erforderlichen Daten gespeichert werden, bevor Sie fortfahren.

>[!NOTE]
>Umgestaltungsaufträge können nur ausgeführt werden, wenn der Quell-Code-Upload erfolgreich war.

&#x200B;---

## Refaktorierungsaufträge {#refactoring-jobs}

Wenn Sie auf die Registerkarte **Umgestaltungsauftrag** klicken, wird eine Liste der vorhandenen Aufträge angezeigt. Wenn noch keine Aufträge erstellt wurden, wird ein leerer Status mit einer Aufforderung zur Auftragserstellung angezeigt.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam6.png)

### &#x200B;1. Erstellen eines neuen Umgestaltungsauftrags

- Klicken Sie auf **Schaltfläche „Neuen Auftrag erstellen**.
- Wählen Sie das/die gewünschte(n) Refaktorierungs-Tool(s) aus.
- Klicken Sie **Starten**, um den Umgestaltungsprozess zu starten.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam7.png)

>[!NOTE]
>Sie können einzelne Refaktorierungsaufträge in einen Trigger überführen oder alle verfügbaren Tools in einem Schritt ausführen, indem Sie die Option **Alle Tools zusammen** verwenden.

&#x200B;---

### &#x200B;2. Auftragsstatus

- **Läuft** - Der Vorgang ist derzeit in Bearbeitung. Status wird nach Abschluss oder Fehler automatisch aktualisiert.
- **Abgeschlossen** - Der Vorgang wurde erfolgreich abgeschlossen. Sie können jetzt die Ergebnisse überprüfen oder den umgestalteten Code herunterladen.
- **Fehlgeschlagen** - Beim Vorgang ist ein Fehler aufgetreten. Klicken Sie auf den Auftrag, um detaillierte Protokolle anzuzeigen und das Problem zu beheben.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam8.png)

Wenn der Auftrag erfolgreich abgeschlossen wurde, wird die Schaltfläche **Herunterladen** verfügbar, über die Sie Folgendes abrufen können:

- **Das umgestaltete Projekt**: Dies ist der aktualisierte Code, nachdem die Umwandlung angewendet wurde. Kunden können den neuesten Code für ihr Projekt herunterladen.
- **Aktivitätsprotokolle**: Während der Ausführung des Auftrags werden alle vom Tool ausgeführten Schritte und die vorgenommenen Änderungen als Teil dieses Vorgangs protokolliert.
- **Ergebnisbericht** Dieser Bericht enthält Elemente, die vom Tool nicht vollständig ausgeführt wurden, aber noch bearbeitet werden müssen. Alle derartigen Änderungen werden hier protokolliert.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam9.png)

>[!NOTE]
>Jeder Vorgang kann bis zu 1 Stunde dauern. Wenn der Status nicht aktualisiert wurde, wenden Sie sich an den Adobe-Support.

