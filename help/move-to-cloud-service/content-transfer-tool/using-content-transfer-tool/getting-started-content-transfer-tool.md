---
title: Erste Schritte mit dem Content Transfer Tool
description: Erste Schritte mit dem Content Transfer Tool
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: 54ecb65e78b25aed694f00eed99015ef0226f862
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 59%

---

# Erste Schritte mit dem Content Transfer Tool {#getting-started-content-transfer-tool}

## Verbindung der Quellumgebung {#source-environment-connectivity}

Die Quell-AEM-Instanz wird möglicherweise hinter einer Firewall ausgeführt, wo sie nur bestimmte Hosts erreichen kann, die zu einer Zulassungsliste hinzugefügt wurden. Um eine Extraktion erfolgreich ausführen zu können, müssen die folgenden Endpunkte von der AEM ausgeführten Instanz aus zugänglich sein:

* Das Ziel AEM as a Cloud Service Umgebung: `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* Der Azure Blob Storage-Dienst: `*.blob.core.windows.net`
* Der IO-Endpunkt der Benutzerzuordnung: `usermanagement.adobe.io`

Um die Konnektivität zur as a Cloud Service Zielumgebung AEM zu testen, geben Sie den folgenden cURL-Befehl aus der Shell der Quellinstanz aus (ersetzen Sie `program_id`, `environment_id`und `migration_token`):

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>Wenn eine `HTTP/2 200` empfangen wurde, war eine Verbindung zu AEM as a Cloud Service erfolgreich.

## Verfügbarkeit {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Download"
>abstract="Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Versionshinweise"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software-Verteilungs-Portal"

Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter. Weitere Informationen zur neuesten Version finden Sie in den [Versionshinweisen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

>[!NOTE]
>Laden Sie das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunter.

## Ausführen des Content Transfer Tools {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Ausführen des Content Transfer Tools"
>abstract="In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Siehe Demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration" text="Tutorial – Verwenden des Content Transfer Tools"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren:

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Inhaltsmigration**.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt01.png)

1. Wählen Sie im Assistenten für die **Inhaltsmigration** die Option **Inhaltstransfer** aus.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt02.png)


1. Die Konsole unten wird angezeigt, wenn Sie den ersten Migrationssatz erstellen. Klicken Sie auf **Migrationssatz erstellen**, um einen neuen Migrationssatz zu erstellen.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >Wenn Sie bereits über Migrationssätze verfügen, zeigt die Konsole die Liste der vorhandenen Migrationssätze mit ihrem aktuellen Status an.


1. Füllen Sie die Felder im Bildschirm **Migrationssatz erstellen** aus, wie nachfolgend beschrieben.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt04.png)

   1. **Name**: Geben Sie den Namen des Migrationssatzes ein.
      >[!NOTE]
      >Beim Namen des Migrationssatzes sind keine Sonderzeichen zulässig.

   1. **Cloud Service-Konfiguration**: Geben Sie die Ziel-URL der Autoreninstanz von AEM as a Cloud Service an.

      >[!NOTE]
      >Sie können während der Inhaltstransferaktivität maximal vier Migrationssätze gleichzeitig erstellen und verwalten.
      >Darüber hinaus müssen Sie für jede der spezifischen Umgebungen – *Staging*, *Entwicklung* und *Produktion* – eine separate Migration erstellen.

   1. **Zugriffs-Token**: Geben Sie das Zugriffs-Token ein.

      >[!NOTE]
      >Sie können das Zugriffs-Token über die Schaltfläche **Zugriffs-Token öffnen** abrufen. Sie müssen dabei sicherstellen, dass Sie in der Cloud Service-Zielinstanz zur Gruppe der AEM-Administratoren gehören.

   1. **Parameter**: Wählen Sie die folgenden Parameter aus, um den Migrationssatz zu erstellen:

      1. **Version einschließen**: Aktivieren Sie die Option. Wenn Versionen enthalten sind, wird der Pfad `/var/audit` wird automatisch einbezogen, um Prüfereignisse zu migrieren.

         ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt05.png)

         >[!NOTE]
         >Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen, und Sie Hochaufnahmen mit `wipe=false`, müssen Sie die Versionsbereinigung aufgrund einer aktuellen Einschränkung im Content Transfer Tool deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung zu aktivieren, und die Auffüllungen in einem Migrationssatz durchführen, müssen Sie die Aufnahme wie folgt durchführen: `wipe=true`.


      1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen. Die Pfadauswahl akzeptiert Eingaben durch Eingabe von Text oder Auswahl.

         >[!IMPORTANT]
         >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (einige `/etc`-Pfade können in CTT ausgewählt werden)


1. Klicken Sie auf **Speichern** nachdem Sie alle Felder im **Migrationssatz erstellen** Detailbildschirm.

1. Der Migrationssatz wird im **Inhaltstransfer** -Assistenten, wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt07.png)

   Alle vorhandenen Migrationssätze werden auf der Seite **Inhaltstransfer** mit den aktuellen Status- und Statusinformationen. Ggf. sehen Sie einige der unten beschriebenen Symbole.

   * Eine *rote Wolke* bedeutet, dass Sie den Extraktionsvorgang nicht abschließen können.
   * Eine *grüne Wolke* bedeutet, dass Sie den Extraktionsvorgang abschließen können.
   * Ein *gelbes Symbol* weist darauf hin, dass Sie den vorhandenen Migrationssatz nicht erstellt haben und dass der betreffende Migrationssatz von einem anderen Benutzer in derselben Instanz erstellt wurde.

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Eigenschaften** , um die Eigenschaften des Migrationssatzes anzuzeigen oder zu bearbeiten. Beim Bearbeiten von Eigenschaften ist es nicht möglich, die **Name des Migrationssatzes** oder **Dienst-URL**.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt06.png)


## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie einen Migrationssatz erstellen, können Sie jetzt mehr über Extraktions- und Aufnahmeprozesse im Content Transfer Tool erfahren. Bevor Sie diese Prozesse kennenlernen, müssen Sie [Umgang mit großen Inhaltsverzeichnissen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) , um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität erheblich zu beschleunigen und Inhalte auf AEM as a Cloud Service zu verschieben.
