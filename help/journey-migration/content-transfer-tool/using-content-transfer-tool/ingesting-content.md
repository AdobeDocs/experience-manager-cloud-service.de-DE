---
title: Aufnahme von Inhalten in Target
description: Erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte aus Ihrem Migrationssatz in eine Cloud Service-Instanz aufnehmen können.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 44%

---

# Aufnahme von Inhalten in Target {#ingesting-content}

## Aufnahme-Prozess im Content Transfer Tool {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inhaltsaufnahme"
>abstract="Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem Migrationssatz in die Cloud Service-Zielinstanz. Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de" text="Auffüllaufnahme"

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool aufzunehmen:

>[!NOTE]
>Haben Sie ein Support-Ticket für diesen Aufnahmevorgang erstellt? Weitere Informationen zu diesen und anderen Überlegungen zur erfolgreichen Aufnahme finden Sie unter [Wichtige Überlegungen vor Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de#important-considerations).

1. Gehen Sie zum Cloud Acceleration Manager. Klicken Sie auf Ihre Projektkarte und dann auf die Karte Inhaltstransfer . Navigieren Sie zu **Aufnahmevorgänge** und klicken **Neue Erfassung**

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Überprüfen Sie die Checkliste für die Aufnahme und stellen Sie sicher, dass alle Schritte abgeschlossen sind. Diese Schritte sind erforderlich, um eine erfolgreiche Erfassung sicherzustellen. Fahren Sie mit dem **Nächste** Schritt nur dann, wenn die Checkliste abgeschlossen ist.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Geben Sie die erforderlichen Informationen an, um eine Aufnahme zu erstellen.

   * Wählen Sie als Quelle den Migrationssatz aus, der die extrahierten Daten enthält.
      * Migrationssätze laufen nach längerer Inaktivität ab. Daher wird erwartet, dass die Aufnahme relativ bald nach der Extraktion erfolgt. Lesen Sie [Ablauf von Migrationssätzen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry), um mehr darüber zu erfahren.
   * Wählen Sie die Zielumgebung aus. In dieser Umgebung wird der Inhalt des Migrationssatzes erfasst. Wählen Sie die Ebene aus. (Author/Publish). Schnelle Entwicklungsumgebungen (Rapid Development Environments, RDE) werden nicht unterstützt.

   >[!NOTE]
   >Die folgenden Hinweise gelten für die Aufnahme von Inhalten:
   > Wenn die Quelle die Autoreninstanz war, wird empfohlen, sie in die Autorenebene auf dem Ziel aufzunehmen. Wenn die Quelle die Veröffentlichungsinstanz war, sollte das Ziel ebenfalls „Veröffentlichung“ sein.
   > Wenn die Zielebene `Author`festgelegt ist, wird die Autoreninstanz während der Erfassungsdauer heruntergefahren und steht Benutzern (z. B. Autoren oder anderen, die Wartungsarbeiten durchführen) nicht mehr zur Verfügung. Der Grund besteht darin, das System zu schützen und alle Änderungen zu verhindern, die entweder verloren gehen oder einen Aufnahmekonflikt verursachen könnten. Stellen Sie sicher, dass Ihr Team sich dieser Tatsache bewusst ist. Beachten Sie außerdem, dass die Umgebung während der Autorenaufnahme im Ruhezustand angezeigt wird.
   > Sie können den optionalen Vorabkopie-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Siehe [Erfassen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) für weitere Details.
   > Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.
   > Einstiege unterstützen kein Ziel in der Rapid Development Environment (RDE) und erscheinen nicht als mögliche Zielauswahl, selbst wenn der Benutzer Zugriff darauf hat.

   >[!IMPORTANT]
   > Die folgenden wichtigen Hinweise gelten für die Aufnahme von Inhalten:
   > Sie können eine Aufnahme nur dann in die Zielumgebung starten, wenn Sie zum lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst. Wenn Sie eine Aufnahme nicht starten können, lesen Sie [Aufnahme kann nicht gestartet werden](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) für weitere Details.
   > Wenn die Einstellung **Wischen** vor der Erfassung aktiviert ist, löscht er das gesamte vorhandene Repository und erstellt ein Repository, in das Sie Inhalte aufnehmen können. Dieser Workflow bedeutet, dass alle Einstellungen einschließlich der Berechtigungen auf der Zielinstanz von Cloud Service zurückgesetzt werden. Diese Zurücksetzung gilt auch für einen Administrator, der zum **Administratoren** hinzugefügt. Sie müssen zur Administratorgruppe hinzugefügt werden, um eine Aufnahme starten zu können.

1. Klicks **Aufnehmen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Sie können dann die Aufnahmephase in der Listenansicht „Aufnahmevorgänge“ überwachen. Verwenden Sie das Aktionsmenü der Aufnahme, um das Protokoll im Verlauf der Aufnahme anzuzeigen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Klicken Sie auf **i)** -Schaltfläche in der Zeile, um weitere Informationen zum Erfassungsauftrag zu erhalten. Sie können die Dauer jedes Schritts der Aufnahme anzeigen, wenn dieser ausgeführt oder abgeschlossen wird, indem Sie auf **...** und klicken Sie anschließend auf **Anzeigedauer**. Die Informationen aus der Extraktion zeigen auch, dass sie erkennen, was aufgenommen wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

<!-- Alexandru: hiding temporarily, until it's reviewed 

1. The **Migration Set ingestion** dialog box displays. Content can be ingested to either Author instance or Publish instance at a time. Select the instance to ingest content to. Click on **Ingest** to start the ingestion phase. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >If ingesting with pre-copy is used (for S3 or Azure Data Store), it is recommended to run Author ingestion first alone. This will speed up the Publish ingestion when it is run later. 

   >[!IMPORTANT]
   >When the **Wipe existing content on Cloud instance before ingestion** option is enabled, it deletes the entire existing repository and creates a new repository to ingest content into. This means that it resets all settings including permissions on the target Cloud Service instance. This is also true for an admin user added to the **administrators** group.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Additionally, click on **Customer Care** to log a ticket, as shown in the figure below. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)
   
   Also, see [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Auffüllaufnahme {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Auffüllaufnahme"
>abstract="Verwenden Sie die Auffüllfunktion, um Inhalte zu verschieben, die seit der vorherigen Inhaltstransferaktivität geändert wurden. Überprüfen Sie nach Abschluss der Aufnahme die Protokolle auf Fehler/Warnungen. Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder die Adobe-Kundenunterstützung kontaktieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=de" text="Anzeigen von Protokollen"

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Schritt &quot;Vorab-Kopie&quot;für die erste vollständige Erfassung verwendet haben, können Sie die Vorkopie für nachfolgende Auffüllaufnahme überspringen (wenn die Größe des AuffüllMigrationssatzes kleiner als 200 GB ist). Der Grund dafür ist, dass dadurch dem gesamten Prozess Zeit hinzugefügt werden kann.

Nachdem der Aufnahmevorgang abgeschlossen ist, müssen Sie zum Erfassen des Delta-Inhalts eine [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)und verwenden Sie dann die Auffüllaufnahme-Methode.

Erstellen Sie zunächst einen Aufnahmeauftrag und stellen Sie sicher, dass **Wischen** ist während der Aufnahmephase deaktiviert, wie unten dargestellt:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Fehlerbehebung {#troubleshooting}

### CAM kann das Migrations-Token nicht abrufen {#cam-unable-to-retrieve-the-migration-token}

Der automatische Abruf des Migrations-Tokens kann aus verschiedenen Gründen fehlschlagen, wie z. B. wenn Sie in der Cloud Service-Zielumgebung [eine IP-Zulassungsliste über Cloud Manager einrichten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md). In solchen Fällen sehen Sie das folgende Dialogfeld, wenn Sie versuchen, eine Aufnahme zu starten:

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

Rufen Sie das Migrationstoken manuell ab, indem Sie im Dialogfeld auf den Link &quot;Token abrufen&quot;klicken. Es wird eine weitere Registerkarte geöffnet, auf der das Token angezeigt wird. Sie können dann das Token kopieren und in das Feld **Migrations-Token-Eingabefeld** einfügen. Jetzt sollten Sie in der Lage sein, die Aufnahme zu starten.

>[!NOTE]
>
>Das Token steht Benutzern zur Verfügung, die zur lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst.

### Aufnahme kann nicht gestartet werden {#unable-to-start-ingestion}

Sie können eine Aufnahme nur dann in die Zielumgebung starten, wenn Sie zum lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst. Wenn Sie nicht zur Gruppe der AEM-Administratoren gehören, wird beim Versuch, eine Aufnahme zu starten, ein Fehler wie unten dargestellt angezeigt. Sie können Ihren Administrator bitten, Sie entweder zu den lokalen **AEM Administratoren** hinzuzufügen oder ihn nach dem Token selbst fragen, das Sie dann in das Feld **Eingabefeld für das Migrations-Token** einfügen können.

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Migrationsdienst kann nicht erreicht werden {#unable-to-reach-migration-service}

Nachdem eine Aufnahme angefordert wurde, kann dem Benutzer eine Meldung wie die folgende angezeigt werden: &quot;Der Migrationsdienst in der Zielumgebung ist nicht erreichbar. Wenn ja, versuchen Sie es später erneut oder kontaktieren Sie den Support von Adobe.&quot;

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Diese Meldung weist darauf hin, dass der Cloud Acceleration Manager nicht in der Lage war, den Migrationsdienst der Zielumgebung zu erreichen, um die Aufnahme zu starten. Diese Situation kann aus verschiedenen Gründen auftreten.

>[!NOTE]
> 
> Das Feld „Migrations-Token“ wird angezeigt, da in einigen Fällen das Abrufen dieses Tokens tatsächlich nicht zulässig ist. Durch die manuelle Bereitstellung kann die Benutzerin oder der Benutzer die Aufnahme schnell und ohne zusätzliche Hilfe starten. Wenn das Token bereitgestellt wird und die Nachricht weiterhin angezeigt wird, war das Abrufen des Tokens nicht das Problem.

* AEM as a Cloud Service behält den Umgebungsstatus bei und muss gelegentlich den Migrationsdienst aus verschiedenen normalen Gründen neu starten. Wenn dieser Dienst neu gestartet wird, kann er nicht erreicht werden, ist aber schließlich verfügbar.
* Es ist möglich, dass ein anderer Prozess in der Instanz ausgeführt wird. Wenn z. B. der Release-Server ein Update anwendet, ist das System möglicherweise ausgelastet und der Migrationsdienst ist regelmäßig nicht verfügbar. Daher wird dringend empfohlen, Aktualisierungen während einer Erfassung auszusetzen, da dies die Staging- oder Produktionsinstanz beschädigen kann.
* Wenn eine [IP-Zulassungsliste wurde angewendet](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) Cloud Manager verhindert, dass Cloud Acceleration Manager den Migrationsdienst erreicht. Eine IP-Adresse kann nicht für die Aufnahme hinzugefügt werden, da ihre Adresse dynamisch ist. Derzeit besteht die einzige Lösung darin, die IP-Zulassungsliste während der Aufnahme zu deaktivieren.
* Es kann andere Gründe geben, die untersucht werden müssen. Wenn die Aufnahme weiterhin fehlschlägt, wenden Sie sich an die Kundenunterstützung von Adobe.

### Automatische Aktualisierungen über Release Orchestrator sind weiterhin aktiviert

Release Orchestrator hält Umgebungen durch die automatische Anwendung von Aktualisierungen automatisch auf dem aktuellen Stand. Wenn die Aktualisierung bei der Ausführung einer Aufnahme ausgelöst wird, kann dies zu unvorhersehbaren Ergebnissen führen, einschließlich der Beschädigung der Umgebung. Ein guter Grund, ein Support-Ticket vor der Aufnahme zu protokollieren (siehe &quot;Hinweis&quot;oben), damit die zeitweilige Deaktivierung des Freigabe-Dispatches geplant werden kann.

Wenn der Release-Server beim Start einer Aufnahme noch ausgeführt wird, wird diese Meldung in der Benutzeroberfläche angezeigt. Sie können trotzdem fortfahren und das Risiko eingehen, indem Sie das Feld markieren und die Taste erneut drücken.

>[!NOTE]
>
> Die Veröffentlichungsumgebungen werden jetzt in Entwicklungsumgebungen bereitgestellt, sodass auch Aktualisierungen in diesen Umgebungen angehalten werden sollten.

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

### Fehler bei Auffüllaufnahme Aufgrund der Eindeutigkeitsbeschränkung

Eine häufige Ursache für einen [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)-Fehler ist ein Konflikt bei Knoten-IDs. Um den Fehler zu identifizieren, laden Sie das Aufnahmeprotokoll über die Benutzeroberfläche von Cloud Acceleration Manager herunter und suchen Sie nach einem Eintrag wie dem Folgenden:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] having value a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Jeder Knoten in AEM muss über eine eindeutige UUID verfügen. Dieser Fehler weist darauf hin, dass ein aufgenommener Knoten dieselbe uuid wie ein Knoten hat, der an anderer Stelle in einem anderen Pfad der Zielinstanz vorhanden ist.
Diese Situation kann auftreten, wenn ein Knoten zwischen einer Extraktion und einer nachfolgenden [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process).
Es kann auch vorkommen, wenn ein Knoten am Ziel zwischen einer Aufnahme und einer nachfolgenden Auffüllaufnahme verschoben wird.

Dieser Konflikt muss manuell behoben werden. Dabei muss eine Person, die mit dem Inhalt vertraut ist, entscheiden, welche der beiden Knoten gelöscht werden muss, wobei andere Inhalte, die darauf verweisen, zu berücksichtigen sind. Zur Lösung des Problems kann es erforderlich sein, dass die Auffüllextraktion ohne den fehlerhaften Knoten wiederholt wird.

### Fehler bei der Auffüllaufnahme aufgrund der nicht zu löschenden referenzierten Knotens

Eine weitere häufige Ursache für eine [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) Fehler ist ein Versionskonflikt für einen bestimmten Knoten in der Zielinstanz. Um den Fehler zu identifizieren, laden Sie das Aufnahmeprotokoll über die Benutzeroberfläche von Cloud Acceleration Manager herunter und suchen Sie nach einem Eintrag wie dem Folgenden:
>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakIntegrity0001: Unable to delete referenced node: 8a2289f4-b904-4bd0-8410-15e41e09 76a8

Dies kann vorkommen, wenn ein Knoten auf dem Ziel zwischen einer Aufnahme und einer nachfolgenden Auffüllaufnahme so geändert wird, dass eine neue Version erstellt wurde. Wenn für die Aufnahme &quot;Include-Versionen&quot;aktiviert sind, kann es zu einem Konflikt kommen, da das Ziel jetzt über eine neuere Version verfügt, auf die der Versionsverlauf und andere Inhalte verweisen. Der Aufnahmevorgang kann den fehlerhaften Versionsknoten nicht löschen, da darauf verwiesen wird.

Zur Lösung des Problems kann es erforderlich sein, dass die Auffüllextraktion ohne den fehlerhaften Knoten wiederholt wird. Oder erstellen Sie einen kleinen Migrationssatz des fehlerhaften Knotens, wobei &quot;Include versions&quot;deaktiviert ist.

Best Practices weisen darauf hin, dass bei einer Aufnahme mit wp=false und &quot;include versions&quot;=true so wenig wie möglich Änderungen am Zielinhalt vorgenommen werden müssen, bis die Journey abgeschlossen ist. Andernfalls können diese Konflikte auftreten.


## Wie geht es weiter {#whats-next}

Nachdem Sie die Aufnahme von Inhalten in die Target-Komponente abgeschlossen haben, können Sie die Protokolle jedes Schritts (Extraktion und Aufnahme) anzeigen und nach Fehlern suchen. Weitere Informationen finden Sie unter [Anzeigen von Protokollen für einen Migrationssatz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=de).
