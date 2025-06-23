---
title: Erste Schritte mit Refaktorierungs-Tools
description: Erfahren Sie mehr über die ersten Schritte mit den Refaktorierungs-Tools in AEM as a Cloud Service
exl-id: 84394bdd-2b92-4f5d-b08a-7dc2c681baa4
source-git-commit: c89acee0c5090f32136306b41a669d7241002a37
workflow-type: ht
source-wordcount: '542'
ht-degree: 100%

---

# Erste Schritte mit Refaktorierungs-Tools {#getting-started-refactoring-tools}

## Verfügbarkeit {#availability}

<!-- Alexandru: duplicate contextualhelp id, drafting this for now

>[!CONTEXTUALHELP]
>id="aemcloud_rs_upload"
>title="Download"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html" text="Release Notes"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

-->

## Ausführen der Refaktorierungs-Tools {#running-refactoring-tools}

Verwenden Sie das Refaktorierungs-Tool, um Ihren Code aus Gründen der Kompatibilität mit AEM as a Cloud Service zu migrieren.

1. Wenn Sie kein CAM-Projekt erstellt haben, lesen Sie [Erstellen und Verwalten eines Projekts in CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md#create-project).
1. Klicken Sie auf die Karte **Code-Refaktorierung**, um den Quell-Code hochzuladen.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam1.png)

1. Wenn Sie zum ersten Mal auf die **Source-Code-Ansicht** zugreifen, wird ein leerer Status mit der Aufforderung angezeigt, Ihren Quell-Code hochzuladen.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam2.png)

---

## Hochladen von Source-Code {#uploading}

Wenn Kundinnen oder Kunden zum ersten Mal auf **Refaktorierungs-Tools** zugreifen, wird ihnen in der **Source-Code-Ansicht** ein leerer Status angezeigt. Gehen Sie wie folgt vor, um Ihr Projekt hochzuladen und den Inspektionsprozess zu starten:

1. **Zugriff auf die Seite zum Projekt-Upload**\
   Klicken Sie auf die Schaltfläche **Projekt-Upload** in leerem Status, um den Upload-Prozess zu starten.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam3.png)

1. **Hochladen Ihres Quell-Codes**
   - Wählen Sie im Dialogfeld „Hochladen“ Ihre ZIP-Quell-Code-Datei aus.
   - Klicken Sie **Hochladen**, um zu beginnen.
   - Der Fortschritt des Uploads wird im Dialogfeld angezeigt. Die Dauer hängt von der Größe Ihres Projekts ab.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam4.png)

1. **Inspektionsprozess**
   - Nach dem Hochladen beginnt der **Inspektionsprozess** automatisch im Hintergrund.
   - In der **Quell-Code-Ansicht** wird jetzt Ihr hochgeladenes Projekt und der Status seiner Inspektion angezeigt.

1. **Inspektionsstatus**: Der Inspektionsprozess vereinfacht die Ausführung von Umgestaltungswerkzeugen, indem der Aufwand für manuelle Konfigurationen reduziert wird.

   Die Inspektion zeigt einen der folgenden Status an:
   - **Wird ausgeführt** – Die Inspektion läuft.
   - **Bereit** – Die Inspektion ist abgeschlossen. Sie können jetzt Umgestaltungs-Tools ausführen.
   - **Fehlgeschlagen** – Es ist ein Fehler aufgetreten. Klicken Sie auf das Projekt, um den Inspektionsbericht zu überprüfen und Probleme zu beheben.

   ![Bild](/help/journey-migration/refactoring-tools/assets/rscam5.png)

>[!NOTE]
>Beim Hochladen eines neuen Projekts wird das vorhandene gelöscht. Stellen Sie sicher, dass alle erforderlichen Daten gespeichert werden, bevor Sie fortfahren.

>[!NOTE]
>Refaktorierungsaufträge können nur ausgeführt werden, wenn das Hochladen des Quell-Codes erfolgreich war.

---

## Refaktorierungsaufträge {#refactoring-jobs}

Wenn Sie auf die Registerkarte **Refaktorierungsauftrag** klicken, wird eine Liste der vorhandenen Aufträge angezeigt. Wenn noch keine Aufträge erstellt wurden, wird ein leerer Status mit einer Aufforderung zur Auftragserstellung angezeigt.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam6.png)

### &#x200B;1. Erstellen eines neuen Refaktorierungsauftrags

- Klicken Sie auf die Schaltfläche **Neuen Auftrag erstellen**.
- Wählen Sie die gewünschten Refaktorierungs-Tools aus.
- Klicken Sie auf **Start**, um die Synchronisierung zu starten.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam7.png)

>[!NOTE]
>Sie können einzelne Refaktorierungsaufträge per Trigger auslösen oder alle verfügbaren Tools in einem Schritt ausführen, indem Sie die Option **Alle Tools zusammen** verwenden.

---

### &#x200B;2. Auftragsstatus

- **Wird ausgeführt** – Der Auftrag läuft derzeit. Der Status wird nach Abschluss oder Fehler automatisch aktualisiert.
- **Abgeschlossen** – Der Auftrag wurde erfolgreich abgeschlossen. Sie können jetzt die Ergebnisse überprüfen oder den umgestalteten Code herunterladen.
- **Fehlgeschlagen** – Beim Auftrag ist ein Fehler aufgetreten. Klicken Sie auf den Auftrag, um detaillierte Protokolle anzuzeigen und das Problem zu beheben.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam8.png)

Wenn der Auftrag erfolgreich abgeschlossen wurde, wird die Schaltfläche **Herunterladen** verfügbar, über die Sie Folgendes abrufen können:

- **Das refaktorierte Projekt**: Dies ist der aktualisierte Code nach Anwendung der Transformation. Kundinnen und Kunden können den neuesten Code für ihr Projekt herunterladen.
- **Aktivitätsprotokolle**: Während der Ausführung des Auftrags werden alle vom Tool ausgeführten Schritte und die vorgenommenen Änderungen als Teil dieses Vorgangs protokolliert.
- **Ergebnisbericht**: Dieser Bericht enthält die Elemente, die vom Tool nicht vollständig ausgeführt wurden, sondern noch bearbeitet werden müssen. Alle derartigen Änderungen werden hier protokolliert.

![Bild](/help/journey-migration/refactoring-tools/assets/rscam9.png)

>[!NOTE]
>Jeder Auftrag kann bis zu 1 Stunde dauern. Wenn der Status nicht aktualisiert wird, wenden Sie sich an den Adobe-Support.
