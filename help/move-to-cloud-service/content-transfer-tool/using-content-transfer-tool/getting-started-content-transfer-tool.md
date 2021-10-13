---
title: Erste Schritte mit dem Content Transfer Tool
description: Erste Schritte mit dem Content Transfer Tool
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: 19c84c9acaf8202dcb96ff25b4d674555ebc2d92
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 70%

---

# Erste Schritte mit dem Content Transfer Tool {#getting-started-content-transfer-tool}

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

      1. **Version einschließen**: Aktivieren Sie die Option. Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

      ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt05.png)

      >[!NOTE]
      >Wenn Sie Versionen als Teil eines Migrationssatzes einbeziehen möchten und mit `wipe=false` Auffüllungen durchführen, müssen Sie die Versionsbereinigung aufgrund einer aktuellen Einschränkung im Content Transfer Tool deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu halten und Auffüllungen in einem Migrationssatz durchzuführen, müssen Sie die Aufnahme als `wipe=true` durchführen.

      1. **Zuordnung von IMS-Benutzern und -Gruppen einschließen**: Wählen Sie die Option aus, um die Zuordnung von IMS-Benutzern und -Gruppen einzuschließen.
Weitere Informationen finden Sie unter [Tool für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de).

      1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen. Die Pfadauswahl akzeptiert Eingaben durch Eingabe von Text oder Auswahl.

         >[!IMPORTANT]
         >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (einige `/etc`-Pfade können in CTT ausgewählt werden)




1. Klicken Sie auf **Speichern**, nachdem Sie alle Felder im Detailbildschirm **Migrationssatz erstellen** ausgefüllt haben.

1. Der Migrationssatz wird im Assistenten **Inhaltstransfer** angezeigt, wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   Alle vorhandenen Migrationssätze werden im Assistenten **Inhaltstransfer** mit ihren aktuellen Status- und Statusinformationen angezeigt. Ggf. sehen Sie einige der unten beschriebenen Symbole.

   * Eine *rote Wolke* bedeutet, dass Sie den Extraktionsvorgang nicht abschließen können.
   * Eine *grüne Wolke* bedeutet, dass Sie den Extraktionsvorgang abschließen können.
   * Ein *gelbes Symbol* weist darauf hin, dass Sie den vorhandenen Migrationssatz nicht erstellt haben und dass der betreffende Migrationssatz von einem anderen Benutzer in derselben Instanz erstellt wurde.

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Eigenschaften** , um die Eigenschaften des Migrationssatzes anzuzeigen oder zu bearbeiten. Beim Bearbeiten von Eigenschaften ist es nicht möglich, den **Migrationssatznamen** oder die **Dienst-URL** zu ändern.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt06.png)


## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie einen Migrationssatz erstellen, können Sie jetzt mehr über Extraktions- und Aufnahmeprozesse im Content Transfer Tool erfahren. Bevor Sie diese Prozesse kennenlernen, müssen Sie [Handling Large Content Repositories](help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) lesen, um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität erheblich zu beschleunigen und Inhalte auf AEM as a Cloud Service zu verschieben.
