---
title: Aufnehmen von Inhalten in Cloud Service
description: Erfahren Sie, wie Sie mit Cloud Acceleration Manager Inhalte aus Ihrem Migrationssatz in eine Cloud Service-Zielinstanz aufnehmen können.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
feature: Migration
role: Admin
source-git-commit: 30386a3117f241d81eed5e55f6c6e97bbe4084f8
workflow-type: ht
source-wordcount: '3467'
ht-degree: 100%

---

# Aufnehmen von Inhalten in Cloud Service {#ingesting-content}

## Aufnahmevorgang in Cloud Acceleration Manager {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inhaltsaufnahme"
>abstract="Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem Migrationssatz in die Cloud Service-Zielinstanz. Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content#top-up-extraction-process" text="Auffüllextraktion"

Gehen Sie wie folgt vor, um den Migrationssatz mit Cloud Acceleration Manager aufzunehmen:

1. Gehen Sie zu Cloud Acceleration Manager. Klicken Sie auf Ihre Projektkarte und dann auf die Karte für den Inhaltstransfer. Navigieren Sie zu **Aufnahmevorgänge** und klicken Sie auf **Neue Aufnahme**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Überprüfen Sie die Checkliste für die Aufnahme und stellen Sie sicher, dass alle Schritte ausgeführt wurden. Diese Schritte sind erforderlich, um eine erfolgreiche Aufnahme sicherzustellen. Fahren Sie mit dem **nächsten** Schritt nur fort, wenn die Checkliste abgeschlossen ist.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Geben Sie die erforderlichen Informationen ein, um eine Aufnahme zu erstellen.

   * **Migrationssatz:** Wählen Sie als Quelle den Migrationssatz aus, der die extrahierten Daten enthält.
      * Migrationssätze laufen nach längerer Inaktivität ab. Daher wird erwartet, dass die Aufnahme relativ bald nach der Extraktion erfolgt. Lesen Sie [Ablauf von Migrationssätzen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry), um mehr darüber zu erfahren.

   >[!TIP]
   > Wenn die Extraktion ausgeführt wird, wird sie im Dialogfeld angezeigt. Nach erfolgreichem Abschluss der Extraktion startet die Aufnahme automatisch. Wenn die Extraktion fehlschlägt oder angehalten wird, wird der Aufnahmevorgang zurückgesetzt.

   * **Ziel:** Wählen Sie die Zielumgebung aus. In dieser Umgebung werden die Inhalte des Migrationssatzes aufgenommen.
      * Aufnahmen unterstützen keine Ziele des Typs „Schnelle Entwicklungsumgebung“ (RDE) oder Vorschau und erscheinen nicht als mögliche Zielwahl, selbst wenn die Benutzenden Zugriff darauf haben.
      * Während ein Migrationssatz gleichzeitig in mehrere Ziele aufgenommen werden kann, kann ein Ziel zu jedem Zeitpunkt nur das Ziel einer ausgeführten oder einer wartenden Aufnahme sein.

   * **Ebene:** Wählen Sie die Ebene aus. (Author/Publish).
      * Wenn die Quelle `Author` war, wird empfohlen, sie in die `Author`-Ebene auf dem Ziel aufzunehmen. Wenn die Quelle `Publish` war, sollte das Ziel ebenfalls `Publish` sein.

   >[!NOTE]
   > Wenn es sich bei `Author` um die Zielebene handelt, wird die Authoring-Instanz während der Aufnahmedauer heruntergefahren, sodass sie Benutzenden (wie beispielsweise Autorinnen und Autoren oder anderen, die Wartungsarbeiten durchführen) nicht zur Verfügung steht. Dadurch soll das System geschützt werden, und es sollen Änderungen verhindert werden, die verloren gehen oder einen Aufnahmekonflikt verursachen könnten. Stellen Sie sicher, dass Ihr Team sich dieser Tatsache bewusst ist. Beachten Sie außerdem, dass sich die Umgebung während der Author-Aufnahme im Ruhezustand befindet.

   >[!NOTE]
   > Wenn die Zielebene `Publish` ist, bleibt die Veröffentlichungsinstanz während der Aufnahme aktiv.  Wenn der Komprimierungsprozess jedoch während der Aufnahme ausgeführt wird, ist ein Konflikt zwischen den beiden Prozessen wahrscheinlich.  Aus diesem Grund deaktiviert der Aufnahmeprozess das Komprimierungszeitintervallskript, sodass die Komprimierung während der Aufnahme nicht gestartet wird, und prüft außerdem, ob die Komprimierung derzeit ausgeführt wird. Falls sie ausgeführt wird, wartet er, bis sie abgeschlossen ist, bevor die Aufnahme fortgesetzt wird.  Wenn die Aufnahme in der Veröffentlichungsinstanz länger als erwartet dauert, überprüfen Sie die Aufnahmeprotokolle auf entsprechende Protokollanweisungen.

   * **Bereinigen**: Wählen Sie den `Wipe`-Wert aus
      * Die Option **Bereinigen** legt den Startpunkt des Ziels für die Aufnahme fest. Wenn **Bereinigen** aktiviert ist, wird das Ziel einschließlich des gesamten Inhalts auf die in Cloud Manager angegebene AEM-Version zurückgesetzt. Wenn diese Option nicht aktiviert ist, behält das Ziel seinen aktuellen Inhalt als Ausgangspunkt bei.
      * Diese Option wirkt sich **NICHT** darauf aus, wie die Aufnahme von Inhalten durchgeführt wird. Die Aufnahme verwendet immer eine Inhaltsersetzungsstrategie und _keine_ Inhaltszusammenführungsstrategie, sodass in beiden Fällen, **Bereinigen** und **Nicht bereinigen**, bei der Aufnahme eines Migrationssatzes die Inhalte im selben Pfad zu dem Ziel überschrieben werden. Wenn der Migrationssatz beispielsweise `/content/page1` enthält und im Ziel bereits `/content/page1/product1` enthalten ist, entfernt die Aufnahme den gesamten `page1`-Pfad und zugehörige Unterseiten, einschließlich `product1`, und ersetzt sie durch den Inhalt im Migrationssatz. Dies bedeutet, dass beim Durchführen einer Aufnahme mit der Einstellung **Nicht bereinigen** in ein Ziel, das beizubehaltende Inhalte enthält, eine sorgfältige Planung erfolgen muss.
      * Nicht löschende Aufnahmen wurden speziell für den Anwendungsfall der Auffüllaufnahme entwickelt. Diese Aufnahmen sollen eine inkrementelle Menge neuer Inhalte enthalten, die sich seit der letzten Aufnahme in einem vorhandenen Migrationssatz geändert haben. Das Durchführen von nicht löschenden Aufnahmen außerhalb dieses Anwendungsfalls könnte zu sehr langen Erfassungszeiten führen.

   >[!IMPORTANT]
   > Wenn die Einstellung **Bereinigen** für die Aufnahme aktiviert ist, wird das gesamte bestehende Repository zurückgesetzt, einschließlich der Benutzerberechtigungen für die Ziel-Cloud-Service-Instanz. Diese Rücksetzung gilt auch für Admin-Benutzende, die zur Gruppe **Admins** hinzugefügt wurden, und eine solche Person muss der Admin-Gruppe erneut hinzugefügt werden, um eine Aufnahme zu starten.

   * **Vorabkopie**: Wählen Sie den `Pre-copy`-Wert aus.
      * Sie können den optionalen Schritt der Vorabkopie ausführen, um die Aufnahme erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
      * Wenn die Aufnahme mit einer Voabrkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die `Author`-Aufnahme zuerst allein auszuführen. Dadurch wird die `Publish`-Aufnahme beschleunigt, wenn sie später ausgeführt wird.

   >[!IMPORTANT]
   > Sie können eine Aufnahme in der Zielumgebung nur initiieren, wenn Sie der lokalen Gruppe der **AEM-Admins** im Ziel-Author-Service von Cloud Service angehören. Wenn Sie eine Aufnahme nicht starten können, finden Sie unter [Aufnahme kann nicht gestartet werden](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) weitere Informationen dazu.

1. Nach Auswahl der Aufnahmeoptionen wird eine geschätzte Dauer angezeigt. Es handelt sich um eine bestmögliche Schätzung auf der Grundlage historischer Daten ähnlicher Aufnahmen.

   * Diese Schätzung wird für **nicht-löschende** Aufnahmen weder berechnet noch angezeigt, da CAM in diesem Fall nicht weiß, wie viel Inhalt auf dem Zielsystem vorhanden ist.
   * Diese Schätzung wird nur berechnet und angezeigt, wenn die Werte „Größe überprüfen“ der Extraktion erfasst wurden und verfügbar sind.
   * Dieser Wert ist eine Schätzung und sollte, obwohl er sorgfältig berechnet wurde, nicht als exakt angesehen werden. Verschiedene Faktoren können die tatsächliche Dauer ändern.
   * Während die Aufnahme läuft, ist dieser Wert auch im Dauer-Dialog verfügbar, der über die Aktion „**Dauer anzeigen**“ der Aufnahme aufgerufen werden kann.

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_estimate"
>title="Geschätzte Aufnahmedauer"
>abstract="Die ungefähre Dauer einer bestimmten Aufnahme kann angezeigt werden, um einen allgemeinen Eindruck davon zu vermitteln, wie lange die Aufnahme dauern wird. Es gibt Einschränkungen hinsichtlich der Genauigkeit."

![Bild](/help/journey-migration/content-transfer-tool/assets/estimate.png)

1. Klicken Sie auf **Aufnehmen**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Anschließend können Sie die Aufnahme in der Listenansicht der Aufnahmeaufträge überwachen und im Aktionsmenü der Aufnahme die Dauer anzeigen und protokollieren, während die Aufnahme fortschreitet.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Klicken Sie in der Zeile auf die Schaltfläche **(i)**, um weitere Informationen zum Aufnahmevorgang zu erhalten. Sie können die Dauer jedes Aufnahmeschritts anzeigen, wenn dieser ausgeführt oder abgeschlossen wird, indem Sie erst auf **…** und dann auf **Dauer anzeigen** klicken. Die Informationen aus der Extraktion werden ebenfalls angezeigt, damit klar ist, was aufgenommen wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

## Auffüllaufnahme {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Auffüllaufnahme"
>abstract="Verwenden Sie die Auffüllfunktion, um Inhalte zu verschieben, die seit der vorherigen Inhaltsübertragungsaktivität geändert wurden. Überprüfen Sie die Protokolle nach Abschluss der Aufnahme auf Fehler und Warnungen. Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder die Adobe-Kundenunterstützung kontaktieren."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs" text="Anzeigen von Protokollen"

Das Content Transfer Tool verfügt über eine Funktion, die die Extraktion von differenziellen Inhalten ermöglicht, indem eine *Auffüllung* des Migrationssatzes ausgeführt wird. Dadurch kann der Migrationssatz so geändert werden, dass nur die Inhalte einbezogen werden, die seit der vorherigen Extraktion geändert wurden, ohne dass der gesamte Inhalt erneut extrahiert werden muss.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Falls Sie den Schritt der Vorabkopie für die erste Aufnahme verwendet haben, können Sie die Vorabkopie für nachfolgende Auffüllaufnahmen überspringen (sofern die Größe des Auffüllmigrationssatzes weniger als 200 GB beträgt). Dadurch kann sich nämlich der gesamte Vorgang verlängern.

Für die Aufnahme differenzieller Inhalte nach Abschluss einiger Aufnahmen müssen Sie eine [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) ausführen und anschließend die Erfassungsmethode mit **deaktivierter** **Bereinigen**-Option verwenden. Lesen Sie unbedingt die Erläuterung zum **Bereinigen** oben, um zu vermeiden, dass Inhalte, die bereits im Ziel sind, verloren gehen.

Erstellen Sie zunächst einen Aufnahmeauftrag und stellen Sie sicher, dass **Bereinigen** während der Aufnahme deaktiviert ist, wie unten gezeigt:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Fehlerbehebung {#troubleshooting}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_troubleshooting"
>title="Fehlerbehebung für die Inhaltsaufnahme"
>abstract="In den Aufnahmeprotokollen und der Dokumentation finden Sie Lösungen zu häufigen Ursachen für Aufnahmefehler und können sehen, welche Möglichkeiten es gibt, das Problem zu beheben und die Aufnahme erneut auszuführen. Nach der Korrektur können Sie die Aufnahme erneut ausführen."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers" text="Validieren von Inhaltsübertragungen"

### CAM kann das Migrations-Token nicht abrufen {#cam-unable-to-retrieve-the-migration-token}

Der automatische Abruf des Migrations-Tokens kann aus verschiedenen Gründen fehlschlagen, wie z. B. wenn Sie in der Cloud Service-Zielumgebung [eine IP-Zulassungsliste über Cloud Manager einrichten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md). In solchen Fällen wird das folgende Dialogfeld angezeigt, wenn Sie versuchen, eine Aufnahme zu starten:

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

Rufen Sie das Migrations-Token manuell ab, indem Sie im Dialogfeld auf den Link „Token abrufen“ klicken. Es wird eine weitere Registerkarte geöffnet, auf der das Token angezeigt wird. Sie können dann das Token kopieren und in das Feld **Migrations-Token-Eingabefeld** einfügen. Jetzt sollten Sie in der Lage sein, die Aufnahme zu starten.

>[!NOTE]
>
>Das Token steht Benutzenden zur Verfügung, die der lokalen Gruppe der **AEM-Admins** im Ziel-Authoring-Service von Cloud Service angehören.

### Aufnahme kann nicht gestartet werden {#unable-to-start-ingestion}

Sie können eine Aufnahme in der Zielumgebung nur initiieren, wenn Sie der lokalen Gruppe der **AEM-Admins** im Ziel-Authoring-Service von Cloud Service angehören. Wenn Sie nicht zur Gruppe der AEM-Admins gehören, wird beim Versuch, eine Aufnahme zu starten, ein Fehler wie unten dargestellt angezeigt. Sie können Ihren Administrator bitten, Sie entweder zu den lokalen **AEM Administratoren** hinzuzufügen oder ihn nach dem Token selbst fragen, das Sie dann in das Feld **Eingabefeld für das Migrations-Token** einfügen können.

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Migrationsdienst kann nicht erreicht werden {#unable-to-reach-migration-service}

Nachdem eine Aufnahme angefordert wurde, wird den Benutzenden möglicherweise eine Meldung wie die folgende angezeigt: „Der Migrations-Service in der Zielumgebung ist derzeit nicht erreichbar. Versuchen Sie es später erneut oder kontaktieren Sie den Adobe-Support.“

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Diese Meldung weist darauf hin, dass Cloud Acceleration Manager nicht in der Lage war, den Migrations-Service der Zielumgebung zu erreichen, um die Aufnahme zu starten. Hierfür kann es verschiedene Gründe geben.

>[!NOTE]
> 
> Das Feld „Migrations-Token“ wird angezeigt, da in einigen Fällen das Abrufen dieses Tokens tatsächlich nicht zulässig ist. Durch die manuelle Bereitstellung kann die Benutzerin oder der Benutzer die Aufnahme schnell und ohne zusätzliche Hilfe starten. Wenn das Token bereitgestellt, aber die Meldung weiterhin angezeigt wird, war das Abrufen des Tokens nicht das Problem.

* AEM as a Cloud Service verwaltet den Umgebungsstatus und muss den Migrations-Service gelegentlich aus einer Reihe normaler Gründe neu starten. Wenn der Service gerade neu gestartet wird, ist er nicht erreichbar, wird aber bald wieder verfügbar sein.
* Möglicherweise wird ein anderer Prozess in der Instanz ausgeführt. Wenn z. B. durch [AEM-Versionsaktualisierungen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) eine Aktualisierung durchgeführt wird, ist das System möglicherweise ausgelastet und der Migrations-Service ist nicht regelmäßig verfügbar. Sobald dieser Vorgang abgeschlossen ist, kann erneut versucht werden, die Aufnahme zu starten.
* Wenn eine [IP-Zulassungsliste über Cloud Manager angewendet wurde](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md), hindert sie Cloud Acceleration Manager daran, den Migrations-Service zu erreichen. Eine IP-Adresse kann nicht für Aufnahmen hinzugefügt werden, da diese Adresse dynamisch ist. Derzeit besteht die einzige Lösung darin, die IP-Zulassungsliste während des Aufnahme- und Indizierungsprozesses zu deaktivieren.
* Es kann andere Gründe geben, die untersucht werden müssen. Wenn die Aufnahme oder Indizierung weiterhin fehlschlägt, wenden Sie sich an die Kundenunterstützung von Adobe.

### AEM-Versionsaktualisierungen und Aufnahmen {#aem-version-updates-and-ingestions}

[AEM-Versionsaktualisierungen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) werden automatisch auf Umgebungen angewendet, um sie mit der neuesten AEM as a Cloud Service-Version auf dem neuesten Stand zu halten. Wenn während eines Aufnahmevorgangs eine Aktualisierung ausgelöst wird, kann dies zu unvorhersehbaren Ergebnissen führen, einschließlich der Beschädigung der Umgebung.

Wenn die „AEM-Versionsaktualisierungen“ im Zielprogramm integriert sind, versucht der Aufnahmevorgang, die Warteschlange zu deaktivieren, bevor er gestartet wird. Wenn die Aufnahme abgeschlossen ist, wird der Status des Versionsaktualisierers so zurückgegeben, wie er vor dem Start der Aufnahmen war.

>[!NOTE]
>
> Es ist nicht mehr erforderlich, ein Support-Ticket zu protokollieren, um „AEM-Versionsaktualisierungen“ zu deaktivieren.

Wenn „AEM-Versionsaktualisierungen“ aktiv ist (d. h. Aktualisierungen werden ausgeführt oder in die Warteschlange gestellt), beginnt die Aufnahme nicht und die Benutzeroberfläche zeigt die folgende Meldung an. Sobald die Aktualisierungen abgeschlossen sind, kann die Aufnahme gestartet werden. Cloud Manager kann zur Anzeige des aktuellen Status der Pipelines des Programms verwendet werden.

>[!NOTE]
>
> „AEM-Versionsaktualisierungen“ wird in der Pipeline der Umgebung ausgeführt und wartet, bis die Pipeline leer ist. Wenn Aktualisierungen länger als erwartet in die Warteschlange bleiben, überprüfen Sie, ob die Pipeline nicht unbeabsichtigt durch einen benutzerdefinierten Workflow gesperrt wird.

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_active.png)

### Aufnahmefehler aufgrund eines fehlenden Bereitschaftszustands der Cloud-Umgebung {#ingestion-failure-due-to-cloud-environment-not-in-ready-state}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_cloud_environment_not_in_ready_state"
>title="Cloud-Umgebung nicht bereit"
>abstract="In seltenen Fällen kann es in der Ziel-Cloud-Umgebung zu unerwarteten Problemen kommen, die dazu führen, dass die Aufnahme fehlschlägt."

In seltenen Fällen kann es in der für die Aufnahme vorgesehenen Cloud Service-Zielumgebung zu unerwarteten Problemen kommen. Die Aufnahme schlägt fehl, da sich die Umgebung nicht im erwarteten Bereitschaftszustand befindet. Überprüfen Sie das Aufnahmeprotokoll, um weitere Details zum Fehlerstatus anzuzeigen.

Stellen Sie sicher, dass die Autorenumgebung verfügbar ist, und warten Sie einige Minuten, bevor Sie einen weiteren Aufnahmeversuch unternehmen. Wenn das Problem weiterhin besteht, wenden Sie sich unter Angabe des Fehlerstatus an den Kunden-Support.

### Fehler bei Auffüllaufnahme aufgrund einer Verletzung der Eindeutigkeitsbeschränkung {#top-up-ingestion-failure-due-to-uniqueness-constraint-violation}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_uuid"
>title="Verletzung der Eindeutigkeitsbeschränkung"
>abstract="Eine häufige Ursache für einen Fehler bei der Aufnahme mit der Einstellung „Nicht bereinigen“ ist ein Konflikt bei Knoten-IDs. Es darf nur einer der in Konflikt stehenden Knoten vorhanden sein."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Auffüllaufnahme"

Eine häufige Ursache für einen [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)-Fehler ist ein Konflikt bei Knoten-IDs. Um den Fehler zu identifizieren, laden Sie das Aufnahmeprotokoll über die Benutzeroberfläche von Cloud Acceleration Manager herunter und suchen Sie nach einem Eintrag wie dem Folgenden:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] having value a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Jeder Knoten in AEM muss über eine eindeutige UUID verfügen. Dieser Fehler weist darauf hin, dass ein Knoten, der gerade aufgenommen wird, dieselbe UUID hat wie ein Knoten, der in einem anderen Pfad in der Zielinstanz vorhanden ist. Hierfür kann es zwei Gründe geben:

* Ein Knoten wird zwischen einer Extraktion und einer nachfolgenden [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) an der Quelle verschoben.
   * _ERINNERUNG_: Bei Auffüllextraktionen bleibt der Knoten im Migrationssatz erhalten, auch wenn er in der Quelle nicht mehr existiert.
* Ein Knoten am Zielort wird zwischen einer Aufnahme und einer nachfolgenden Auffüllaufnahme verschoben.

Dieser Konflikt muss manuell behoben werden. Dabei muss eine Person, die mit dem Inhalt vertraut ist, entscheiden, welche der beiden Knoten gelöscht werden muss, wobei andere Inhalte, die darauf verweisen, zu berücksichtigen sind. Zur Lösung des Problems kann es erforderlich sein, dass die Auffüllextraktion ohne den fehlerhaften Knoten wiederholt wird.

### Fehler bei der Auffüllaufnahme, da der Knoten, auf den verwiesen wird, nicht gelöscht werden kann {#top-up-ingestion-failure-due-to-unable-to-delete-referenced-node}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_referenced_node"
>title="Referenzierter Knoten kann nicht gelöscht werden"
>abstract="Eine häufige Ursache für einen Fehler bei der Aufnahme mit der Einstellung „Nicht bereinigen“ ist ein Versionskonflikt für einen bestimmten Knoten in der Zielinstanz. Die Versionen des Knotens müssen in Ordnung gebracht werden."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Auffüllaufnahme"

Eine weitere häufige Ursache für einen Fehler bei der [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) ist ein Versionskonflikt für einen bestimmten Knoten in der Zielinstanz. Um den Fehler zu identifizieren, laden Sie das Aufnahmeprotokoll über die Benutzeroberfläche von Cloud Acceleration Manager herunter und suchen Sie nach einem Eintrag wie dem Folgenden:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakIntegrity0001: Löschen des Verweisknotens nicht möglich: 8a2289f4-b904-4bd0-8410-15e41e0976a8

Dies kann vorkommen, wenn ein Knoten im Ziel zwischen einer Aufnahme und einer nachfolgenden Aufnahme mit der Einstellung **Nicht bereinigen** geändert wird, sodass eine neue Version erstellt wurde. Wenn der Migrationssatz mit aktivierter Option „Versionen einschließen“ extrahiert wurde, kann es zu einem Konflikt kommen, da das Ziel jetzt über eine neuere Version verfügt, auf die der Versionsverlauf und andere Inhalte verweisen. Der Aufnahmevorgang kann den fehlerhaften Versionsknoten nicht löschen, da auf diesen verwiesen wird.

Zur Lösung des Problems kann es erforderlich sein, dass die Auffüllextraktion ohne den fehlerhaften Knoten wiederholt wird. Oder erstellen Sie einen kleinen Migrationssatz des fehlerhaften Knotens, wobei die Option „Versionen einschließen“ deaktiviert ist.

Wenn eine Aufnahme mit der Einstellung **Nicht bereinigen** mit einem Migrationssatz durchgeführt werden muss, der Versionen enthält, ist es entsprechend den Best Practices wichtig, dass der Inhalt am Zielort so wenig wie möglich geändert wird, bis der Migrationsprozess abgeschlossen ist. Andernfalls können diese Konflikte auftreten.

### Aufnahmefehler aufgrund von Eigenschaftswerten für große Knoten {#ingestion-failure-due-to-large-node-property-values}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_bson"
>title="Eigenschaft für große Knoten"
>abstract="Eine häufige Ursache für einen Aufnahmefehler ist die Überschreitung der maximalen Größe von Knoteneigenschaftswerten. Befolgen Sie die Dokumentation, auch die zum BPA-Bericht, um Abhilfe zu schaffen."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool" text="Migrationsvoraussetzungen"

Die in MongoDB gespeicherten Knoteneigenschaftswerte dürfen 16 MB nicht überschreiten. Wenn ein Knotenwert die unterstützte Größe überschreitet, schlägt die Aufnahme fehl und das Protokoll enthält entweder:

* einen `BSONObjectTooLarge`-Fehler und gibt an, welcher Knoten das Maximum überschritten hat, oder
* einen `BsonMaximumSizeExceededException`-Fehler, der angibt, dass ein Knoten vorhanden ist, der wahrscheinlich Unicode-Zeichen enthält, die die maximale Größe überschreiten **

Dies ist eine MongoDB-Beschränkung.

In der Notiz `Node property value in MongoDB` in [Voraussetzungen für das Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md) finden Sie weitere Informationen und einen Link zu einem Oak-Tool, mit dem Sie alle großen Knoten finden können. Sobald alle Knoten mit großen Größen beseitigt sind, führen Sie die Extraktion und Aufnahme erneut durch.

Um diese Einschränkung möglicherweise zu vermeiden, führen Sie den [Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) auf der AEM-Quellinstanz aus und überprüfen Sie die Ergebnisse, insbesondere das Muster [„Nicht unterstützte Repository-Struktur“ (Unsupported Repository Structure, URS)](https://experienceleague.adobe.com/de/docs/experience-manager-pattern-detection/table-of-contents/urs).

>[!NOTE]
>
>[Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) Version 2.1.50 oder höher meldet große Knoten, die Unicode-Zeichen enthalten, die die maximale Größe überschreiten. Stellen Sie sicher, dass Sie die neueste Version ausführen. BPA-Versionen vor 2.1.50 identifizieren und melden diese großen Knoten nicht. Diese müssen separat mit dem oben erwähnten, erforderlichen Oak-Tool ermittelt werden.

### Aufnahmefehler aufgrund unerwarteter zeitweise auftretender Fehler {#ingestion-failure-due-to-unexpected-intermittent-errors}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_intermittent_errors"
>title="Unerwartete zeitweise auftretende Fehler"
>abstract="Manchmal kann es unerwartet zeitweise auftretende, nachgelagerte Dienstfehler geben, und leider besteht die einzige Abhilfe darin, die Aufnahme einfach erneut zu versuchen."

Manchmal kann es unerwartet zeitweise auftretende Probleme aufgrund fehlgeschlagener Aufnahmen geben. In diesem Fall besteht die einzige Abhilfe leider darin, die Aufnahme erneut zu versuchen. Prüfen Sie das Aufnahmeprotokoll, um die Ursache des Fehlers zu ermitteln und festzustellen, ob es sich um einen der unten aufgeführten Fehler handelt, bei denen ein erneuter Versuch durchgeführt werden sollte.

#### Probleme mit MongoDB {#mongo-db-issues}

* `Atlas prescale timeout error` – In der Aufnahmephase wird versucht, die Ziel-Cloud-Datenbank vorab auf eine geeignete Größe zu skalieren, die der Größe des aufzunehmenden Migrationssatzinhalts entspricht. In seltenen Fällen wird dieser Vorgang nicht innerhalb des erwarteten Zeitraums abgeschlossen.
* `Exhausted mongo restore retries` – Die Versuche, eine lokale Sicherungskopie des aufgenommenen Migrationssatzinhalts in die Cloud-Datenbank wiederherzustellen, sind ausgeschöpft. Dies weist auf ein allgemeines Konsistenz-/Netzwerkproblem mit MongoDB hin, das sich häufig nach einigen Minuten selbst behebt.
* `Mongo network error` – Manchmal kann das Herstellen einer Verbindung mit MongoDB fehlschlagen, was dazu führt, dass der Aufnahmeprozess vorzeitig beendet und als fehlgeschlagen gemeldet wird. Es sollte dann einfach ein erneuter Versuch der Aufnahme unternommen werden.
* `Mongo server selection error` – Dies ist ein seltener Client-seitiger Mongo-Timeout-Fehler, der aus einer Reihe von zugrunde liegenden Gründen auftreten kann. Ein nachfolgender erneuter Versuch wird das Problem höchstwahrscheinlich beheben.

### Aufnahme aufgehoben {#ingestion-rescinded}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_rescinded"
>title="Aufnahme aufgehoben"
>abstract="Die Extraktion, auf die die Aufnahme gewartet hat, wurde nicht erfolgreich abgeschlossen. Die Aufnahme wurde aufgehoben, da sie nicht ausgeführt werden konnte."

Bei einer Aufnahme, die mit einer laufenden Extraktion als Migrationssatz für die Quelle erstellt wurde, wird geduldig gewartet, bis diese Extraktion erfolgreich ist, und zu diesem Zeitpunkt normal gestartet. Wenn die Extraktion fehlschlägt oder gestoppt wird, werden die Aufnahme und der dazugehörige Indizierungsvorgang nicht gestartet, sondern zurückgesetzt. Überprüfen Sie in diesem Fall die Extraktion, um festzustellen, warum sie fehlgeschlagen ist, beheben Sie das Problem und beginnen Sie erneut mit dem Extrahieren. Sobald die feste Extraktion ausgeführt wird, kann eine neue Aufnahme geplant werden.

### Gelöschtes Asset nach erneuter Aufnahme nicht vorhanden

Im Allgemeinen wird eine Änderung der Cloud-Umgebungsdaten zwischen den einzelnen Aufnahmen nicht empfohlen.

Wenn ein Asset mithilfe der Touch-optimierten Assets-Benutzeroberfläche aus dem Cloud Service-Ziel gelöscht wird, werden die Knotendaten gelöscht, aber der Asset-Blob mit dem Image wird nicht sofort gelöscht. Es ist zum Löschen markiert, sodass es nicht mehr in der Benutzeroberfläche angezeigt wird. Es verbleibt allerdings im Datenspeicher, bis die Speicherbereinigung erfolgt und der Blob entfernt wird.

Wenn ein zuvor migriertes Asset gelöscht und die nächste Aufnahme ausgeführt wird, bevor die Speicherbereinigung den Löschvorgang für das Asset abgeschlossen hat, wird beim Aufnehmen desselben Migrationssatzes das gelöschte Asset nicht wiederhergestellt. Wenn die Aufnahme die Cloud-Umgebung für das Asset überprüft, liegen keine Knotendaten vor. Daher werden im Zuge der Aufnahme die Knotendaten in die Cloud-Umgebung kopiert. Bei Überprüfung des Blob-Speichers wird jedoch festgestellt, dass der Blob vorhanden ist, und das Kopieren des Blobs übersprungen. Daher sind die Metadaten nach der Aufnahme vorhanden, wenn Sie das Asset über die Touch-optimierte Benutzeroberfläche betrachten, das Image aber nicht. Beachten Sie, dass Migrationssätze und die Inhaltsaufnahme nicht für diesen Fall entwickelt wurden. Sie zielen darauf ab, der Cloud-Umgebung neue Inhalte hinzuzufügen und nicht zuvor migrierte Inhalte wiederherzustellen.

## So geht es weiter {#whats-next}

Wenn die Aufnahme erfolgreich war, startet AEM die Indizierung automatisch. Siehe [Indizierung nach der Migration von Inhalten](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md) für weitere Informationen.

Nachdem Sie die Aufnahme von Inhalten in Cloud Service abgeschlossen haben, können Sie die Protokolle jedes Schritts (Extraktion und Aufnahme) anzeigen und nach Fehlern suchen. Weitere Informationen finden Sie unter [Anzeigen von Protokollen für einen Migrationssatz](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md).
