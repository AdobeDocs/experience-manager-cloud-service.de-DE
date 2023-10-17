---
title: Erfassen von Inhalten in Cloud Service
description: Erfahren Sie, wie Sie mit Cloud Acceleration Manager Inhalte aus Ihrem Migrationssatz in eine Ziel-Cloud Service-Instanz aufnehmen können.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: a6d19de48f114982942b0b8a6f6cbdc38b0d4dfa
workflow-type: tm+mt
source-wordcount: '2191'
ht-degree: 56%

---

# Erfassen von Inhalten in Cloud Service {#ingesting-content}

## Aufnahmevorgang im Cloud Acceleration Manager {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inhaltsaufnahme"
>abstract="Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem Migrationssatz in die Cloud Service-Zielinstanz. Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=de#top-up-extraction-process" text="Auffüllextraktion"

Gehen Sie wie folgt vor, um den Migrationssatz mit Cloud Acceleration Manager zu erfassen:

1. Gehen Sie zu Cloud Acceleration Manager. Klicken Sie auf Ihre Projektkarte und dann auf die Karte für den Inhaltstransfer. Navigieren Sie zu **Aufnahmevorgänge** und klicken Sie auf **Neue Aufnahme**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Überprüfen Sie die Checkliste für die Aufnahme und stellen Sie sicher, dass alle Schritte ausgeführt wurden. Diese Schritte sind erforderlich, um eine erfolgreiche Aufnahme sicherzustellen. Fahren Sie mit dem **nächsten** Schritt nur fort, wenn die Checkliste abgeschlossen ist.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Geben Sie die erforderlichen Informationen ein, um eine Aufnahme zu erstellen.

   * Wählen Sie als Quelle den Migrationssatz aus, der die extrahierten Daten enthält.
      * Migrationssätze laufen nach längerer Inaktivität ab. Daher wird erwartet, dass die Aufnahme relativ bald nach der Extraktion erfolgt. Lesen Sie [Ablauf von Migrationssätzen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry), um mehr darüber zu erfahren.
   * Wählen Sie die Zielumgebung aus. In dieser Umgebung werden die Inhalte des Migrationssatzes aufgenommen. Wählen Sie die Ebene aus. (Author/Publish). Schnelle Entwicklungsumgebungen (Rapid Development Environments, RDE) werden nicht unterstützt.

   >[!NOTE]
   >Die folgenden Hinweise gelten für die Aufnahme von Inhalten:
   > Wenn die Quelle die Autoreninstanz war, wird empfohlen, sie in die Autorenebene auf dem Ziel aufzunehmen. Wenn die Quelle die Veröffentlichungsinstanz war, sollte das Ziel ebenfalls „Veröffentlichung“ sein.
   > Wenn es sich bei `Author` um die Zielebene handelt, wird die Authoring-Instanz während der Aufnahmedauer heruntergefahren, sodass sie Benutzenden (wie beispielsweise Autorinnen und Autoren oder anderen, die Wartungsarbeiten durchführen) nicht zur Verfügung steht. Dadurch soll das System geschützt werden, und es sollen Änderungen verhindert werden, die verloren gehen oder einen Aufnahmekonflikt verursachen könnten. Stellen Sie sicher, dass Ihr Team sich dieser Tatsache bewusst ist. Beachten Sie außerdem, dass sich die Umgebung während der Author-Aufnahme im Ruhezustand befindet.
   > Sie können den optionalen Schritt zum Vorauskopieren ausführen, um die Aufnahme erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
   > Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die Author-Aufnahme zuerst allein auszuführen. Dadurch wird die Publish-Aufnahme beschleunigt, wenn sie später ausgeführt wird.
   > Aufnahmen unterstützen kein Rapid Development Environment(RDE)-Ziel und werden nicht als mögliche Zielauswahl angezeigt, selbst wenn die Benutzerin oder der Benutzer Zugriff darauf hat.

   >[!IMPORTANT]
   > Sie können eine Aufnahme in der Zielumgebung nur initiieren, wenn Sie der lokalen Gruppe der **AEM-Admins** im Ziel-Author-Service von Cloud Service angehören. Wenn Sie eine Aufnahme nicht starten können, finden Sie unter [Aufnahme kann nicht gestartet werden](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) weitere Informationen dazu.

   * Wählen Sie die `Wipe` value
      * Die **Wischen** -Option legt den Startpunkt des Ziels für die Aufnahme fest. Wenn **Wischen** aktiviert ist, wird das Ziel, einschließlich des gesamten Inhalts, auf die in Cloud Manager angegebene AEM zurückgesetzt. Wenn diese Option nicht aktiviert ist, behält das Ziel seinen aktuellen Inhalt als Ausgangspunkt bei.
      * Beachten Sie, dass diese Option **NOT** beeinflussen, wie die Inhaltsaufnahme durchgeführt wird. Die Aufnahme verwendet immer eine Inhaltsersetzungsstrategie und _not_ eine Inhaltszusammenführungsstrategie, sodass in beiden **Wischen** und **Nicht wischen** In Fällen überschreibt die Aufnahme eines Migrationssatzes Inhalte im selben Pfad auf dem Ziel. Wenn der Migrationssatz beispielsweise Folgendes enthält: `/content/page1` und das Ziel bereits enthält `/content/page1/product1`, entfernt die Aufnahme die gesamte `page1` Pfad und zugehörige Unterseiten, einschließlich `product1`und ersetzen Sie sie durch den Inhalt im Migrationssatz. Dies bedeutet, dass bei der Durchführung einer **Nicht wischen** Aufnahme in ein Ziel, das alle Inhalte enthält, die gepflegt werden sollen.

   >[!IMPORTANT]
   > Wenn die Einstellung **Wischen** für die Aufnahme aktiviert ist, wird das gesamte bestehende Repository zurückgesetzt, einschließlich der Benutzerberechtigungen für die Ziel-Cloud Service-Instanz. Diese Zurücksetzung gilt auch für einen Administrator, der zum **Administratoren** und dieser Benutzer der Administratorgruppe erneut hinzugefügt werden, um eine Aufnahme zu starten.

1. Klicken Sie auf **Aufnehmen**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Anschließend können Sie die Aufnahme in der Listenansicht Aufnahmen überwachen und im Aktionsmenü der Aufnahme die Dauer anzeigen und protokollieren, während die Aufnahme fortgesetzt wird.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Klicken Sie in der Zeile auf die Schaltfläche **(i)**, um weitere Informationen zum Aufnahmevorgang zu erhalten. Sie können die Dauer jedes Aufnahmeschritts anzeigen, wenn dieser ausgeführt oder abgeschlossen wird, indem Sie erst auf **…** und dann auf **Dauer anzeigen** klicken. Die Informationen aus der Extraktion werden ebenfalls angezeigt, damit klar ist, was aufgenommen wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

## Auffüllaufnahme {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Auffüllaufnahme"
>abstract="Verwenden Sie die Auffüllfunktion, um Inhalte zu verschieben, die seit der vorherigen Inhaltsübertragungsaktivität geändert wurden. Überprüfen Sie nach Abschluss der Aufnahme die Protokolle auf Fehler/Warnungen. Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder die Adobe-Kundenunterstützung kontaktieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=de" text="Anzeigen von Protokollen"

Das Content Transfer Tool verfügt über eine Funktion, die die Extraktion von differenziellen Inhalten ermöglicht, indem eine *top-up* des Migrationssatzes. Dadurch kann der Migrationssatz so geändert werden, dass nur der Inhalt einbezogen wird, der seit der vorherigen Extraktion geändert wurde, ohne dass der gesamte Inhalt erneut extrahiert werden muss.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Schritt &quot;Vorab-Kopie&quot;für die erste Aufnahme verwendet haben, können Sie die Vorkopie für nachfolgende Auffüllaufnahme überspringen (wenn die Größe des Auffüllmigrationssatzes kleiner als 200 GB ist). Der Grund dafür ist, dass dies dem gesamten Prozess Zeit hinzufügen kann.

Um differenziellen Inhalt nach Abschluss einiger Aufnahmen zu erfassen, müssen Sie eine [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)und verwenden Sie dann die Erfassungsmethode mit der **Wischen** option **disabled**. Lesen Sie unbedingt die **Wischen** Erläuterung oben, um zu vermeiden, dass Inhalte bereits am Ziel verloren gehen.

Erstellen Sie zunächst einen Aufnahmeauftrag und stellen Sie sicher, dass **Wischen** ist während der Aufnahme deaktiviert, wie unten dargestellt:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Fehlerbehebung {#troubleshooting}

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
* Möglicherweise wird ein anderer Prozess in der Instanz ausgeführt. Wenn beispielsweise [AEM Versionsaktualisierungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html?lang=de) eine Aktualisierung ausführt, das System möglicherweise ausgelastet ist und der Migrationsdienst regelmäßig nicht verfügbar ist. Sobald dieser Vorgang abgeschlossen ist, kann der Beginn der Aufnahme erneut versucht werden.
* Wenn eine [IP-Zulassungsliste über Cloud Manager angewendet wurde](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md), hindert sie Cloud Acceleration Manager daran, den Migrations-Service zu erreichen. Eine IP-Adresse kann nicht für Aufnahmen hinzugefügt werden, da diese Adresse dynamisch ist. Derzeit besteht die einzige Lösung darin, die IP-Zulassungsliste während der Aufnahme zu deaktivieren.
* Es kann andere Gründe geben, die untersucht werden müssen. Wenn die Aufnahme weiterhin fehlschlägt, wenden Sie sich an die Kundenunterstützung von Adobe.

### AEM-Versionsaktualisierungen und -verschreibungen

[AEM Versionsaktualisierungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html?lang=de) werden automatisch auf Umgebungen angewendet, um sie mit der neuesten AEM as a Cloud Service Version auf dem neuesten Stand zu halten. Wenn während eines Aufnahmevorgangs eine Aktualisierung ausgelöst wird, kann dies zu unvorhersehbaren Ergebnissen führen, einschließlich der Beschädigung der Umgebung.

Wenn die &quot;AEM Versionsaktualisierungen&quot;im Zielprogramm integriert ist, versucht der Aufnahmevorgang, die Warteschlange zu deaktivieren, bevor sie gestartet wird. Wenn die Aufnahme abgeschlossen ist, wird der Status des Versionsaktualisierers so zurückgegeben, wie er vor dem Start der Aufnahme(en) war.

>[!NOTE]
>
> Es ist nicht mehr erforderlich, ein Support-Ticket zu protokollieren, um &quot;AEM Versionsaktualisierungen&quot;zu deaktivieren.

Wenn &quot;AEM Versionsaktualisierungen&quot;aktiv ist (d. h. Aktualisierungen werden ausgeführt oder in die Warteschlange gestellt), beginnt die Aufnahme nicht und die Benutzeroberfläche zeigt die folgende Meldung an. Sobald die Aktualisierungen abgeschlossen sind, kann die Aufnahme gestartet werden. Cloud Manager kann verwendet werden, um den aktuellen Status der Pipelines des Programms anzuzeigen.

>[!NOTE]
>
> &quot;AEM Versionsaktualisierungen&quot;wird in der Pipeline der Umgebung ausgeführt und wartet, bis die Pipeline gelöscht ist. Wenn Updates länger als erwartet in die Warteschlange gestellt werden, stellen Sie sicher, dass die Pipeline in einem benutzerdefinierten Workflow nicht unbeabsichtigt gesperrt wird.

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_active.png)

### Fehler bei Auffüllaufnahme Aufgrund der Eindeutigkeitsbeschränkung

Eine häufige Ursache für einen [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)-Fehler ist ein Konflikt bei Knoten-IDs. Um den Fehler zu identifizieren, laden Sie das Aufnahmeprotokoll über die Benutzeroberfläche von Cloud Acceleration Manager herunter und suchen Sie nach einem Eintrag wie dem Folgenden:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] having value a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Jeder Knoten in AEM muss über eine eindeutige UUID verfügen. Dieser Fehler zeigt an, dass ein aufgenommener Knoten dieselbe uuid wie ein Knoten hat, der an anderer Stelle in einem anderen Pfad der Zielinstanz vorhanden ist.
Hierzu kann es kommen, wenn ein Knoten quellseitig zwischen einer Extraktion und einer nachfolgenden [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) verschoben wird.
Dies kann auch vorkommen, wenn ein Knoten auf dem Ziel zwischen einer Aufnahme und einer nachfolgenden Auffüllaufnahme verschoben wird.

Dieser Konflikt muss manuell behoben werden. Dabei muss eine Person, die mit dem Inhalt vertraut ist, entscheiden, welche der beiden Knoten gelöscht werden muss, wobei andere Inhalte, die darauf verweisen, zu berücksichtigen sind. Zur Lösung des Problems kann es erforderlich sein, dass die Auffüllextraktion ohne den fehlerhaften Knoten wiederholt wird.

### Fehler bei der Auffüllaufnahme aufgrund der nicht zu löschenden referenzierten Knotens

Eine weitere häufige Ursache für eine [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) Fehler ist ein Versionskonflikt für einen bestimmten Knoten in der Zielinstanz. Um den Fehler zu identifizieren, laden Sie das Aufnahmeprotokoll über die Benutzeroberfläche von Cloud Acceleration Manager herunter und suchen Sie nach einem Eintrag wie dem Folgenden:
>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakIntegrity0001: Unable to delete referenced node: 8a2289f4-b904-4bd0-8410-15e41e09 76a8

Dies kann vorkommen, wenn ein Knoten im Ziel zwischen einer Aufnahme und einer nachfolgenden **Nicht wischen** -Aufnahme, sodass eine neue Version erstellt wurde. Wenn der Migrationssatz mit aktivierten &quot;Include-Versionen&quot;extrahiert wurde, kann es zu einem Konflikt kommen, da das Ziel jetzt über eine neuere Version verfügt, auf die der Versionsverlauf und andere Inhalte verweisen. Der Aufnahmevorgang kann den fehlerhaften Versionsknoten nicht löschen, da darauf verwiesen wird.

Zur Lösung des Problems kann es erforderlich sein, dass die Auffüllextraktion ohne den fehlerhaften Knoten wiederholt wird. Oder erstellen Sie einen kleinen Migrationssatz des fehlerhaften Knotens, wobei &quot;Include versions&quot;deaktiviert ist.

Best Practices weisen darauf hin, dass **Nicht wischen** Die Aufnahme muss mithilfe eines Migrationssatzes durchgeführt werden, der Versionen enthält (d. h. extrahiert mit &quot;include versions&quot;=true). Es ist wichtig, dass der Zielinhalt so wenig wie möglich geändert wird, bis die Migration-Journey abgeschlossen ist. Andernfalls können diese Konflikte auftreten.


## Wie geht es weiter {#whats-next}

Wenn die Aufnahme erfolgreich war, beginnt AEM Indizierung automatisch. Siehe [Indizierung nach der Migration von Inhalten](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md) für weitere Informationen.

Nachdem Sie die Aufnahme von Inhalten in Cloud Service abgeschlossen haben, können Sie die Protokolle jedes Schritts (Extraktion und Aufnahme) anzeigen und nach Fehlern suchen. Weitere Informationen finden Sie unter [Anzeigen von Protokollen für einen Migrationssatz](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md).
