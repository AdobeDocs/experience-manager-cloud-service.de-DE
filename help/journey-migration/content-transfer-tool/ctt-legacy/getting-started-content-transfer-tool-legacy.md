---
title: Erste Schritte mit dem Content Transfer Tool (Veraltet)
description: Erste Schritte mit dem Content Transfer Tool
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 77%

---

# Erste Schritte mit dem Content Transfer Tool (Veraltet) {#getting-started-content-transfer-tool}


## Verfügbarkeit {#availability}

Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über [Package Manager](/help/implementing/developing/tools/package-manager.md) in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter. Weitere Informationen zur neuesten Version finden Sie in den [Versionshinweisen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

>[!NOTE]
>Laden Sie das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunter.

## Konnektivität der Quellumgebung {#source-environment-connectivity}

Die Quell-AEM-Instanz wird möglicherweise hinter einer Firewall ausgeführt, wo sie nur bestimmte Hosts erreichen kann, die zu einer Zulassungsliste hinzugefügt wurden. Damit eine Extraktion erfolgreich durchgeführt werden kann, muss von der Instanz, auf der AEM ausgeführt wird, auf die folgenden Endpunkte zugegriffen werden können:

* Die AEM as a Cloud Service-Zielumgebung: `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* Der Azure Blob Datenspeicherungs-Service: `*.blob.core.windows.net`
* Der IO-Endpunkt der Benutzerzuordnung: `usermanagement.adobe.io`

Um die Konnektivität mit der AEM as a Cloud Service-Zielumgebung zu testen, geben Sie den folgenden cURL-Befehl in der Shell der Quellinstanz ein (ersetzen Sie `program_id`, `environment_id`, und `migration_token`):

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>Wenn eine `HTTP/2 200` empfangen wurde, war eine Verbindung zu AEM as a Cloud Service erfolgreich.

## Ausführen des Content Transfer Tools {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren:

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Content-Migration**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt01.png)

1. Wählen Sie im Assistenten für die **Content-Migration** die Option **Content-Übertragung** aus.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt02.png)


1. Die Konsole unten wird angezeigt, wenn Sie den ersten Migrationssatz erstellen. Klicken Sie auf **Migrationssatz erstellen**, um einen neuen Migrationssatz zu erstellen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >Wenn Sie bereits über Migrationssätze verfügen, zeigt die Konsole die Liste der vorhandenen Migrationssätze mit ihrem aktuellen Status an.


1. Füllen Sie die Felder im Bildschirm **Migrationssatz erstellen** aus, wie nachfolgend beschrieben.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt04.png)

   1. **Name**: Geben Sie den Namen des Migrationssatzes ein.
      >[!NOTE]
      >Beim Namen des Migrationssatzes sind keine Sonderzeichen zulässig.

   1. **Cloud Service-Konfiguration**: Geben Sie die Ziel-URL der Autoreninstanz von AEM as a Cloud Service an.

      >[!NOTE]
      >Sie können während der Inhaltstransferaktivität maximal vier Migrationssätze gleichzeitig erstellen und verwalten.
      >Darüber hinaus müssen Sie für jede der spezifischen Umgebungen – *Staging*, *Entwicklung* und *Produktion* – eine separate Migration erstellen.

   1. **Zugriffs-Token**: Geben Sie das Zugriffs-Token ein.

      >[!NOTE]
      >Sie können das Zugriffs-Token über die Schaltfläche **Zugriffs-Token öffnen** abrufen. Sie müssen sicherstellen, dass Sie in der Ziel-Cloud Service-Instanz zur Gruppe &quot;Administratoren&quot;gehören.

   1. **Parameter**: Wählen Sie die folgenden Parameter aus, um den Migrationssatz zu erstellen:

      1. **Version einschließen**: Aktivieren Sie die Option. Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

         ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt05.png)

         >[!NOTE]
         >Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.


      1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen. Die Pfadauswahl akzeptiert Eingaben durch Eingabe von Text oder Auswahl.

         >[!IMPORTANT]
         >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (einige `/etc`-Pfade können in CTT ausgewählt werden)


1. Klicken Sie auf **Speichern**, nachdem Sie alle Felder im Bildschirm **Migrationssatz erstellen** ausgefüllt haben.

1. Der Migrationssatz wird im Assistenten **Inhaltstransfer** angezeigt, wie in der folgenden Abbildung dargestellt.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   Alle vorhandenen Migrationssätze werden im Assistenten **Inhaltstransfer** mit den aktuellen Status- und Statusinformationen angezeigt. Ggf. sehen Sie einige der unten beschriebenen Symbole.

   * Eine *rote Wolke* bedeutet, dass Sie den Extraktionsvorgang nicht abschließen können.
   * Eine *grüne Wolke* bedeutet, dass Sie den Extraktionsvorgang abschließen können.
   * Ein *gelbes Symbol* weist darauf hin, dass Sie den vorhandenen Migrationssatz nicht erstellt haben und dass der betreffende Migrationssatz von einem anderen Benutzer in derselben Instanz erstellt wurde.

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Eigenschaften**, um die Eigenschaften des Migrationssatzes anzuzeigen oder zu bearbeiten. Während der Bearbeitung der Eigenschaften ist es nicht möglich, den **Namen des Migrationssatzes** oder die **Service-URL** zu ändern.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png)

### Bestimmen der Größe des Migrationssatzes und des Festplattenspeichers {#migration-set-size}

Nach dem Erstellen eines Migrationssatzes wird dringend empfohlen, eine Größenüberprüfung des Migrationssatzes durchzuführen, bevor ein Extraktionsprozess gestartet wird.
Durch eine Größenüberprüfung des Migrationssatzes können Sie:
* Stellen Sie fest, ob im `crx-quickstart` -Unterverzeichnis, um die Extraktion erfolgreich abzuschließen.
* Bestimmen Sie, ob die Größe des Migrationssatzes unter die unterstützten Produktbeschränkungen fällt, und vermeiden Sie fehlgeschlagene Inhaltsaufnahmen.

Gehen Sie wie folgt vor, um eine Größenüberprüfung durchzuführen:

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Größe überprüfen**.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image1.png)

1. Dadurch wird die **Größe überprüfen** angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image2.png)

1. Klicken Sie auf **Größe überprüfen** , um den Prozess zu starten. Sie kehren dann zur Listenansicht des Migrationssatzes zurück und sollten eine Meldung mit dem Hinweis erhalten, dass **Größe überprüfen** läuft.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image3.png)


1. Einmal **Größe überprüfen** -Prozess abgeschlossen ist, ändert sich der Status in **FERTIG**. Wählen Sie denselben Migrationssatz aus und klicken Sie auf **Größe überprüfen** , um Ergebnisse anzuzeigen.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image4.png)

   Nachfolgend finden Sie ein Beispiel für **Größe überprüfen** Ergebnisse ohne Warnungen.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image5.png)

1. Wenn die Variable **Größe überprüfen** die Ergebnisse zeigen, dass entweder nicht genügend Speicherplatz vorhanden ist und/oder der Migrationssatz die Produktbeschränkungen überschreitet, **WARNUNG** wird angezeigt.

![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)

Nachfolgend finden Sie ein Beispiel für **Größe überprüfen** Ergebnisse mit Warnungen.

![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png)


## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie einen Migrationssatz erstellen, können Sie im Content Transfer Tool jetzt mehr über Extraktions- und Aufnahmeprozesse erfahren. Bevor Sie diese Prozesse erlernen, müssen Sie sich mit dem [Umgang mit großen Inhalts-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) befassen, um die Extraktions- und Aufnahmephasen der Inhaltsübertragungsaktivität zum Verschieben von Inhalten zu AEM as a Cloud Service erheblich zu beschleunigen.
