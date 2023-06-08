---
title: Das Inhaltskopie-Werkzeug
description: Mit dem Werkzeug zum Kopieren von Inhalten können Benutzer bei Bedarf veränderliche Inhalte aus ihren AEM as a Cloud Service Produktionsumgebungen in niedrigere Umgebungen für Testzwecke kopieren.
exl-id: f060821d-d559-45d2-b3b1-1b2277694ec4
source-git-commit: d056ad0f29cfd2448164e3e866f2cedbe1bf6fc2
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 60%

---

# Das Inhaltskopie-Werkzeug {#content-copy}

Mit dem Werkzeug zum Kopieren von Inhalten können Benutzer bei Bedarf veränderliche Inhalte aus ihren AEM as a Cloud Service Produktionsumgebungen in niedrigere Umgebungen für Testzwecke kopieren.

## Einführung {#introduction}

Aktuelle, echte Daten sind für Tests, Validierung und Benutzerakzeptanz nützlich. Mit dem Content Copy-Tool können Sie Inhalte aus einer Produktions-AEM in eine Staging-, Entwicklungs- oder [Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) -Umgebung für solche Tests.

Der zu kopierende Inhalt wird durch ein Content-Set definiert. Ein Inhaltssatz besteht aus einer Liste von JCR-Pfaden, die den veränderlichen Inhalt enthalten, der aus einer Quellbearbeitungsdienstumgebung in eine Zielbearbeitungsdienstumgebung innerhalb desselben Cloud Manager-Programms kopiert werden soll. Die folgenden Pfade sind in einem Content-Set zulässig.

```text
/content
/conf/**/settings/wcm
/conf/**/settings/dam/cfm/models
/conf/**/settings/graphql/persistentQueries
/etc/clientlibs/fd/themes
```

Beim Kopieren von Inhalten ist die Quellumgebung die Datenquelle.

* Wenn der Inhalt in der Zielumgebung geändert wurde, wird er durch den Inhalt in der Quelle überschrieben, wenn die Pfade übereinstimmen.
* Wenn die Pfade unterschiedlich sind, wird der Inhalt der Quelle mit dem Inhalt des Ziels zusammengeführt.

## Berechtigungen {#permissions}

Um das Inhaltskopie-Werkzeug verwenden zu können, sind sowohl in der Quell- als auch in der Zielumgebung bestimmte Berechtigungen erforderlich.

| Funktion „Inhaltskopie“ | AEM Administratorgruppe | Rolle &quot;Bereitstellungs-Manager&quot; |
|---|---|---|
| Erstellen und Ändern von [Content-Sets](#create-content-set) | Erforderlich | Nicht erforderlich |
| Starten oder Abbrechen des [Inhaltskopie-Prozesses](#copy-content) | Erforderlich | Erforderlich |

## Erstellen eines Content-Sets {#create-content-set}

Bevor ein Inhalt kopiert werden kann, muss ein Inhaltsset definiert werden. Nach der Definition können Content-Sets zum Kopieren von Inhalten wiederverwendet werden. Gehen Sie wie folgt vor, um ein Content-Set zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie vom Bildschirm **Umgebungen** zur Seite **Content-Sets**.

1. Tippen oder klicken Sie rechts oben auf dem Bildschirm auf **Content-Set hinzufügen**.

   ![Content-Sets](assets/content-sets.png)

1. Geben Sie auf der Registerkarte **Details** des Assistenten einen Namen und eine Beschreibung für das Content-Set ein und tippen oder klicken Sie auf **Weiter**.

   ![Content-Set-Details](assets/add-content-set-details.png)

1. Auf der Registerkarte **Inhaltspfade** des Assistenten geben Sie die Pfade der veränderbaren Inhalte an, die in das Content-Set aufgenommen werden sollen.

   1. Geben Sie den Pfad in das Feld **Einschlusspfad hinzufügen** ein.
   1. Tippen oder klicken Sie auf die Schaltfläche **Pfad hinzufügen**, um den Pfad zum Content-Set hinzuzufügen.
   1. Tippen oder klicken Sie bei Bedarf erneut auf die Schaltfläche **Pfad hinzufügen**.
      * Es sind bis zu fünfzig Pfade erlaubt.

   ![Hinzufügen von Pfaden zu Content-Sets](assets/add-content-set-paths.png)

1. Wenn Sie Ihr Content-Set verfeinern oder einschränken möchten, können Sie Unterpfade ausschließen.

   1. Tippen oder klicken Sie in der Liste der enthaltenen Pfade auf das Symbol **Ausschluss-Unterpfade hinzufügen** neben dem Pfad, den Sie einschränken möchten.
   1. Geben Sie den Unterpfad ein, der unterhalb des ausgewählten Pfads ausgeschlossen werden soll.
   1. Tippen oder klicken Sie auf **Pfad ausschließen**.
   1. Tippen oder klicken Sie erneut auf **Ausschluss-Unterpfade hinzufügen**, um bei Bedarf weitere Pfade zum Ausschluss hinzuzufügen.
      * Ausgeschlossene Pfade müssen relativ zum eingeschlossenen Pfad sein.
      * Die Anzahl der ausgeschlossenen Pfade ist unbegrenzt.

   ![Ausschließen von Pfaden](assets/add-content-set-paths-excluded.png)

1. Sie können die angegebenen Pfade bei Bedarf ändern.

   1. Tippen oder klicken Sie auf das X neben den ausgeschlossenen Unterpfaden, um sie zu löschen.
   1. Tippen oder klicken Sie auf die Ellipsen-Schaltfläche neben den Pfaden, um die Optionen **Bearbeiten** und **Löschen** anzuzeigen.

   ![Bearbeiten der Pfadliste](assets/add-content-set-excluded-paths.png)

1. Tippen oder klicken Sie auf **Erstellen**, um das Content-Set zu erstellen.

Das Content-Set kann jetzt zum Kopieren von Inhalten zwischen Umgebungen verwendet werden.

## Bearbeiten eines Content-Sets {#edit-content-set}

Hierbei führen Sie ähnliche Schritte wie beim Erstellen eines Content-Sets aus. Anstatt auf **Content-Set hinzufügen** zu tippen oder zu klicken, wählen Sie ein vorhandenes Set aus der Konsole aus und wählen Sie im Menü mit den Auslassungspunkten die Option **Bearbeiten**.

![Bearbeiten des Content-Sets](assets/edit-content-set.png)

Beachten Sie, dass Sie beim Bearbeiten Ihres Inhaltssets die konfigurierten Pfade möglicherweise erweitern müssen, um die ausgeschlossenen Unterpfade anzuzeigen.

## Kopieren von Inhalten {#copy-content}

Nachdem ein Content-Set erstellt wurde, können Sie es zum Kopieren von Inhalten verwenden. Führen Sie die folgenden Schritte aus, um Inhalte zu kopieren.

>[!NOTE]
> Die Inhaltskopie sollte nicht in einer Umgebung initiiert werden, während eine [Inhaltstransfer](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md) -Vorgang wird in dieser Umgebung ausgeführt.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie vom Bildschirm **Umgebungen** zur Seite **Content-Sets**.

1. Wählen Sie ein Content-Set aus der Konsole aus, und wählen Sie im Menü mit den Auslassungspunkten **Inhalt kopieren**.

   ![Inhaltskopie](assets/copy-content.png)

   >[!NOTE]
   >
   >Eine Umgebung ist unter Umständen nicht auswählbar, wenn:
   >
   >* die Benutzenden nicht über die entsprechenden Berechtigungen verfügen.
   >* in der Umgebung eine laufende Pipeline oder ein Vorgang zum Kopieren von Inhalten in Bearbeitung ist.
   >* Die Umgebung ruht in den Ruhezustand oder fängt an.


1. Geben Se im Dialog **Inhalt kopieren** die Quelle und das Ziel für die Inhaltskopie-Aktion an.

   ![Kopieren von Inhalten](assets/copying-content.png)

   * Inhalte können nur aus einer höheren Umgebung in eine niedrigere Umgebung oder zwischen Entwicklungs-/RDE-Umgebungen kopiert werden, in denen die Hierarchie der Umgebungen wie folgt lautet (von der höchsten zur niedrigsten):
      * Produktion
      * Staging  
      * Entwicklung/RDE

1. Bei Bedarf können Sie auch **Zugriffssteuerungslisten einschließen** in Ihrem Kopierprozess.

1. Tippen oder klicken Sie auf **Kopieren**.

Der Kopiervorgang wird gestartet. Der Status des Kopiervorgangs wird für das ausgewählte Content-Set in der Konsole angezeigt.

## Aktivität „Inhalt kopieren“ {#copy-activity}

Sie können den Status der Kopierprozesse auf der Seite **Aktivität „Inhalt kopieren“** überwachen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie im Bildschirm **Umgebungen** zur Seite **Aktivität „Inhalt kopieren“**.

![Aktivität „Inhalt kopieren“](assets/copy-content-activity.png)

### Inhaltskopie-Status {#statuses}

Sobald das Kopieren von Inhalten beginnt, kann der Prozess einen der folgenden Status haben.

| Status | Beschreibung |
|---|---|
| In Bearbeitung | Die Inhaltskopie wird gerade durchgeführt |
| Fehlgeschlagen | Die Inhaltskopie ist fehlgeschlagen |
| Abgeschlossen | Die Inhaltskopie wurde erfolgreich abgeschlossen |
| Abgebrochen | Benutzer bricht einen Vorgang zum Kopieren von Inhalten ab, nachdem er ihn gestartet hat |

### Abbrechen eines Kopierprozesses {#canceling}

Wenn Sie einen Vorgang zum Kopieren von Inhalten nach dessen Start abbrechen müssen, haben Sie die Möglichkeit, ihn abzubrechen.

Gehen Sie dazu im **Aktivität &quot;Inhalt kopieren&quot;** Seite, wählen Sie die **Abbrechen** -Aktion aus dem Auslassungsmenü des Kopiervorgangs, den Sie zuvor gestartet haben.

![Inhaltskopie abbrechen](assets/content-copy-cancel.png)

>[!NOTE]
>
>Wenn Sie einen Vorgang zum Abbrechen einer Inhaltskopie abbrechen, kann dies zu einer Teilkopie des Inhalts in der Zielumgebung führen. Dadurch kann die Zielumgebung unbrauchbar bleiben.
>
>Wenn sich Ihre Umgebung aufgrund einer Stornierung in einem solchen Zustand befindet, wenden Sie sich zwecks Hilfe an die Adobe-Kundenunterstützung.

## Einschränkungen {#limitations}

Für das Werkzeug zum Kopieren von Inhalten gelten die folgenden Einschränkungen.

* Inhalte können nicht aus einer niedrigeren Umgebung in eine höhere Umgebung kopiert werden.
* Inhalte können nur aus und in Authoring-Dienste kopiert werden.
* Eine programmübergreifende Inhaltskopie ist nicht möglich.
* Die Ausführung gleichzeitiger Inhaltskopievorgänge in derselben Umgebung ist nicht möglich.
* Pro Content-Set können bis zu fünfzig Pfade angegeben werden. Für ausgeschlossene Pfade gibt es keine Beschränkung.
* Das Werkzeug zum Kopieren von Inhalten sollte nicht als Klonen- oder Spiegelwerkzeug verwendet werden, da es keine verschobenen oder gelöschten Inhalte auf der Quelle verfolgen kann.
* Das Werkzeug zum Kopieren von Inhalten verfügt über keine Versionierungsfunktion und kann geänderten Inhalt oder neu erstellten Inhalt in der Quellumgebung in einem Inhaltsset seit dem letzten Vorgang zum Kopieren von Inhalten nicht automatisch erkennen.
   * Wenn Sie Ihre Zielumgebung nur mit Inhaltsänderungen aktualisieren möchten, die seit dem letzten Vorgang der Inhaltskopie vorgenommen wurden, müssen Sie einen Inhaltssatz erstellen und die Pfade auf der Quellinstanz angeben, in der Änderungen seit dem letzten Vorgang der Inhaltskopie vorgenommen wurden.
* Versionsinformationen sind in einer Inhaltskopie nicht enthalten.
