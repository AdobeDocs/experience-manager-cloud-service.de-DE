---
title: Massen-Upload von Prinzipalen in IMS nach Verwendung von CTT
description: Übersicht über Massen-Upload-Dateien für Gruppen und Benutzende und wie diese auf der Admin Console zum Erstellen von Gruppen und Benutzenden in IMS verwendet werden.
exl-id: 43ebd6f1-1492-461a-8d9b-2b55dcde9052
source-git-commit: b9c739a03b358de7c011e50ddbdd609c90f86b6f
workflow-type: tm+mt
source-wordcount: '2384'
ht-degree: 0%

---

# Massen-Upload von Prinzipalen in IMS nach Verwendung von CTT {#bulk-principal-uploading}

>[!CONTEXTUALHELP]
>id="bulk-principal-uploading"
>title="Massen-Upload von Prinzipalen"
>abstract="Übersicht über Massen-Upload-Dateien für Gruppen und Benutzende und wie diese auf der Admin Console zum Erstellen von Gruppen und Benutzenden in IMS verwendet werden."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="AEM Admin Console-Dokumentation"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

## Einführung {#introduction}

Bei der Migration von Inhalten in die Cloud mithilfe von CTT und CAM werden Gruppen in der AEM-Cloud-Instanz erstellt, es kann jedoch nichts getan werden, um Gruppen oder Benutzende in IMS zu platzieren. Sie müssen in IMS vorhanden sein, damit sie von Kunden ordnungsgemäß verwaltet werden können. Glücklicherweise gibt es Funktionen von Admin Console, um IMS-Gruppen und -Benutzer massenweise zu erstellen. Die CAM-Aufnahme unterstützt diesen Prozess, indem sie Eingabedateien für diese Massenerstellung speichert, sodass Kundinnen und Kunden diese Admin Console-Aktion als Teil ihres gesamten Migrationsprozesses durchführen können. Es werden zwei Arten von Massen-Upload-Dateien erstellt: eine für Gruppen und eine für Benutzer.

Siehe auch [Verwalten von Benutzern](https://helpx.adobe.com/de/enterprise/using/users.html) für weitere Informationen zur Verwaltung von AEM as a Cloud Service-Benutzern.

## Allgemeine Regeln für das Hochladen von Dateien {#rules}

Es gibt einige allgemeine Richtlinien zum Bearbeiten und Verwenden beider Arten von Upload-Dateien:

* Bevor diese Anweisungen befolgt werden können, muss zunächst Administratorzugriff auf die Admin Console gewährt werden.
* Beachten Sie, dass es einige verschiedene Möglichkeiten gibt, Benutzende und Gruppen in IMS zu erstellen.  Unter [IMS-Unterstützung für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/ims-support) erfahren Sie mehr über alle verfügbaren Optionen.  Hier werden nur die Massen-Upload-Methoden von Admin Console beschrieben.
* In IMS sind drei Identitätstypen möglich: Adobe ID, Enterprise ID und Federated ID.  Die Anweisungen auf dieser Seite gelten nur für **Adobe ID**.  Wenn Sie Enterprise ID oder Federated ID verwenden müssen, lesen Sie bitte die vollständige Dokumentation zu [Admin Console](https://helpx.adobe.com/ca/enterprise/using/admin-console.html) sowie die spezifische Dokumentation für den Massen-Upload von [Admin Console-](https://helpx.adobe.com/de/enterprise/using/user-groups.html) und den Massen-Upload von [Admin Console-Benutzern](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html).  Die Spezifikationen für die Upload-Dateien unterscheiden sich für diese beiden Identitätstypen etwas.
* Wenn ein einzelnes CSV-Feld mehrere Einträge zulässt (z. B. mehrere Produktprofile, mehrere Gruppen oder mehrere Administratoren), müssen die Einträge in doppelten Anführungszeichen enthalten und durch ein Komma getrennt sein, d. h. `"profile 1,profile 2"`.

   * Anführungszeichen können in diesem Fall anstelle von doppelten Anführungszeichen verwendet werden, aber die Bearbeitung der Datei in Microsoft Excel kann zu Parsing-Problemen führen. Wenn Sie diese Dateien in Excel bearbeiten, stellen Sie sicher, dass Sie doppelte Anführungszeichen anstelle von einfachen Anführungszeichen verwenden.

## Massen-Gruppen-Upload {#group-upload}

#### Anwendungsfall: Gruppen wurden nach AEM as a Cloud Service migriert, doch diese Gruppen sind nicht in IMS/Admin Console vorhanden und müssen daher über Admin Console in IMS hochgeladen werden.

Gehen Sie wie folgt vor, um nach der CTT-/CAM-Migration die Funktion „Massen-Gruppen-Upload“ von Admin Console zu verwenden:
1. Herunterladen der Bulk-Gruppendatei von CAM

   1. Wechseln Sie in CAM zu **Inhaltsübertragung** und wählen Sie **Aufnahmevorgänge** aus.
   1. Klicken Sie auf die Auslassungszeichen (…) in der Zeile der betreffenden Aufnahme und wählen Sie &quot;**anzeigen**.
   1. Wählen Sie im angezeigten Dialogfeld die Option **Massengruppendatei** aus der Dropdown-Liste unter **Datei herunterladen…** und klicken Sie auf die Schaltfläche **Herunterladen**.
   1. Speichern Sie die resultierende CSV-Datei.

1. Massendatei der Gruppe bearbeiten

   * Jede Zeile stellt eine hochzuladende Gruppe dar und hat vier Felder (die Namen der Felder bilden die erste Zeile der Datei):

      * _Benutzergruppenname_ - Der Gruppenname ist erforderlich und kann maximal 255 Zeichen enthalten.  Dieser Gruppenname muss in IMS und AEM identisch sein
      * _Beschreibung_: Dieses Feld ist optional und kann maximal 255 Zeichen enthalten.
      * _Benutzergruppen-_: In diesem Feld muss mindestens ein Gruppenadministrator angegeben werden. Mehrere Administratoren können zugewiesen werden, indem jeder Administrator durch ein Komma getrennt wird und die Liste in Anführungszeichen gesetzt wird. Der Eintrag für jeden Administrator muss den Identitätstyp des Benutzers, gefolgt von einem Bindestrich und der E-Mail-Adresse enthalten.  Zum Beispiel
        `"Adobe ID-myAdmin@example.com,Adobe ID-myOtherAdmin@example.com"`. Geben Sie nach dem Komma, das Admins trennt, kein Leerzeichen ein. Sie können keine Benutzenden (als Admins) einbeziehen, die derzeit nicht Teil des Unternehmens sind, und zwar in der Admin Console
      * _Zugewiesene Produktprofile_ - Dieses Feld ist optional. Sie können mehrere Produktprofile zuweisen, indem Sie jedes Profil durch ein Komma trennen und die Liste in Anführungszeichen setzen. Die Produktprofile, die Sie einbeziehen, müssen jedoch bereits für die Organisation eingerichtet sein. Stellen Sie sicher, dass Sie den Namen des Produktprofils und nicht den Produktnamen angeben.  Die Mitgliedschaft bei Produktprofilen, die einer Gruppe zugewiesen sind, wird von allen Benutzern übernommen, die sich in dieser Gruppe befinden.  So suchen Sie ein Produktprofil:

         1. Zu Admin Console gehen
         1. Suchen Sie Ihr Produkt (d. h. Adobe Experience Manager as a Cloud Service) und klicken Sie darauf
         1. Suchen Sie Ihre Umgebung (Instanz) und klicken Sie darauf
         1. Listen Sie die Produktprofile auf und klicken Sie auf das für Ihre AEM-Umgebung. Das Produktprofil befindet sich am oberen Rand, d. h. &quot;_AEM-Benutzer - Autor - 12345 - 012345_&quot;.

   * Beim Bearbeiten der CSV-Datei können einige Anwendungen beim Speichern zusätzliche Anführungszeichen hinzufügen, was dazu führt, dass die Verarbeitung fehlschlägt. Es empfiehlt sich, die rohe CSV in einem einfachen Texteditor zu überprüfen, um sicherzustellen, dass jedes Feld nur ein öffnendes und ein schließendes Anführungszeichen hat (und es sich nicht um „intelligente Anführungszeichen“ handeln sollte).

1. Hochladen der Massengruppendatei in die Admin Console

   1. Navigieren Sie in der Admin Console zu **Benutzer** und dann **Benutzergruppen**
   1. Klicken Sie rechts auf die Schaltfläche &quot;…“. Wählen Sie **Menü „Benutzergruppen nach CSV hinzufügen** aus und wählen Sie Ihre CSV-Datei zum Hochladen aus. Klicken Sie auf **Hochladen**
   1. Sie erhalten eine Antwort, dass die CSV (in die Admin Console) hochgeladen wurde, sie jedoch noch nicht in IMS importiert wurde
   1. Gehen Sie zum gleichen Menü &quot;…“ und wählen Sie **Ergebnisse des Massenvorgangs**. Daraufhin wird eine Liste der Massen-Upload-Versuche angezeigt und (unter **Status** wird angezeigt, ob der Massen-Upload erfolgreich war oder fehlgeschlagen ist

      * Zunächst wird die Verarbeitung angezeigt, was bedeutet, dass sie noch nicht abgeschlossen ist
      * Klicken Sie nach erfolgreichem Abschluss auf den Link **Benutzergruppen hinzufügen**, um für jede Zeile eine einfache Statusmeldung anzuzeigen.
      * Wenn der Vorgang stattdessen fehlgeschlagen ist, klicken Sie auf das kleine Symbol unter **Datei** und es enthält weitere Informationen darüber, warum der Vorgang fehlgeschlagen ist.  Die Zeilennummern der Gruppen werden ab Zeile 1 referenziert.
1. Überprüfen Sie Ihre Änderungen mit Admin Console.

## Massen-Benutzer-Upload und -Bearbeitung {#bulk-user}

Die Admin Console umfasst zwei separate Aktionen zum Hochladen und Bearbeiten von Benutzerdetails. Unmittelbar unten finden Sie Anweisungen zum Hinzufügen neuer Benutzer zu IMS. Anweisungen zum Bearbeiten vorhandener IMS-Benutzer finden Sie im folgenden Abschnitt [Massenbenutzerbearbeitung](#user-edit).

### Massen-Benutzer-Upload {#user-upload}

#### Anwendungsfall: Gruppen wurden nach AEM as a Cloud Service migriert und über einen Massen-Upload oder eine andere Methode hochgeladen.  Benutzer sind möglicherweise nicht in IMS/Admin Console vorhanden, daher müssen sie hochgeladen und über die Admin Console mit ihren Gruppen in IMS verknüpft werden.

>[!NOTE]
>
>Ein Benutzer wird in der Datei **Massen-Benutzer-Upload** angezeigt, wenn er sich in einer Gruppe befindet, die während derselben Aufnahme aufgenommen wurde, aus der die Datei erstellt wurde. Es kann auch angezeigt werden, wenn sich der Benutzer direkt auf einer ACL oder CUG des migrierten Inhalts befindet oder Mitglied einer integrierten Gruppe oder lokalen Gruppe ist, die sich auf einer ACL oder CUG des migrierten Inhalts befindet. Weitere Informationen [ diesen Fällen finden ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) unter „Gruppenmigration“.

Gehen Sie wie folgt vor, um die Funktion „Massen-Benutzer-Upload“ von Admin Console zu verwenden:

1. Herunterladen der Massen-Benutzerdatei von CAM
   1. Wechseln Sie in CAM zu **Inhaltsübertragung** und wählen Sie **Aufnahmevorgänge** aus.
   1. Klicken Sie auf die Auslassungszeichen (…) in der Zeile der betreffenden Aufnahme und wählen Sie &quot;**anzeigen**.
   1. Wählen Sie im angezeigten Dialogfeld die Option **Massenbenutzerdatei** aus der Dropdown-Liste unter **Datei herunterladen…** und klicken Sie auf die Schaltfläche **Herunterladen**.
   1. Speichern Sie die resultierende CSV-Datei
1. Massenbenutzerdatei bearbeiten
   * Jede Zeile steht für einen Benutzer, der hochgeladen werden soll, und hat fünfzehn Felder (die Namen der Felder bilden die erste Zeile der Datei). Einige Felder sind optional und werden hier nicht beschrieben. Siehe [Massenbenutzer-CSV-Format](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format).  Die Felder sind:

      * _Identitätstyp_ - Optional.  Wenn nichts angegeben wird, wird sie als Adobe ID erstellt
      * _Benutzername_ - Optional und nicht für Adobe ID-Uploads verwendet
      * _Domain_ - Optional und nicht für Adobe ID-Uploads verwendet
      * _E-_: Erforderlich.  Die E-Mail-Adresse wird bei der ersten Anmeldung des Benutzers zur Überprüfung verwendet
      * _Vorname_ - Optional.  Sollte verwendet werden, da es an mehreren Stellen mit Nachname angezeigt wird
      * _Nachname_ - Optional.  Sollte verwendet werden, da es an mehreren Stellen erscheint
      * _Ländercode_ - Optional, und nicht für Adobe ID-Uploads verwendet
      * _ID_ - Optional und nicht für Adobe ID-Uploads verwendet
      * _Produktkonfigurationen_ - Optional. Dieses Feld wird auch von allen Gruppen übernommen, denen der Benutzer angehört.
      * _Administratorrollen_ - Optional. Verwenden Sie dieses Feld, wenn der Benutzer Administrator ist. Weitere Informationen finden Sie [Bulk User CSV ](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format))
      * _Produktkonfigurationen verwaltet_ - Optional.  Weitere Informationen finden [ unter „Massenbenutzer-CSV](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format)Format“. Dieses Feld wird auch von allen Gruppen übernommen, denen der Benutzer angehört.
      * _Benutzergruppen_ - Optional. Eine Liste der Gruppen, denen der Benutzer als Mitglied zugewiesen werden soll. Jede Gruppe muss eine bereits vorhandene IMS-Gruppe sein. Wenn die Massen-Benutzerdatei von CAM heruntergeladen wird, wird dieses Feld mit den Namen der IMS-aktivierten Gruppe vorausgefüllt, der die Benutzerin oder der Benutzer vor der Migration (direkt oder indirekt) angehörte
      * _Benutzergruppen verwaltet_ - Optional.  Weitere Informationen finden [ unter „Massenbenutzer-CSV](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format)Format“. Dieses Feld wird auch von allen Gruppen übernommen, denen der Benutzer angehört.
      * _Produkte verwaltet_ - Optional.  Weitere Informationen finden [ unter „Massenbenutzer-CSV](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format)Format“. Dieses Feld wird auch von allen Gruppen übernommen, denen der Benutzer angehört.
      * _Verwaltete Verträge_ - optional.  Weitere Informationen finden Sie [Bulk User CSV ](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format))
      * _Entwicklerzugriff_ - Optional.  Weitere Informationen finden Sie [Bulk User CSV ](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format))
      * _Automatisch zugewiesene Produkte_ - Optional.  Weitere Informationen finden Sie [Bulk User CSV ](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format))

   * Beim Bearbeiten der CSV-Datei können einige Anwendungen beim Speichern zusätzliche Anführungszeichen hinzufügen, was dazu führt, dass die Verarbeitung fehlschlägt. Es empfiehlt sich, die rohe CSV in einem einfachen Texteditor zu überprüfen, um sicherzustellen, dass jedes Feld nur ein öffnendes und ein schließendes Anführungszeichen hat (und es sich nicht um „intelligente Anführungszeichen“ handeln sollte)

1. Verwenden der Admin Console zum Importieren der Massen-Benutzerdatei

   1. Navigieren Sie in der Admin Console zu Benutzer .
   1. Klicken Sie auf **Schaltfläche „Benutzer nach CSV hinzufügen**
   1. CSV-Datei für Massenbenutzer, die von CAM heruntergeladen wurde, per Drag-and-Drop ziehen oder auswählen
   1. Klicken Sie auf **Schaltfläche** Hochladen“
   1. Sie erhalten eine Antwort, dass die CSV (in die Admin Console) hochgeladen wurde, sie jedoch noch nicht in IMS importiert wurde.
   1. Gehen Sie zum Menü &quot;…“ auf der rechten Seite und wählen Sie **Ergebnisse des Massenvorgangs**.  Es wird eine Liste der Massen-Upload-Versuche angezeigt und (unter **Status** wird angezeigt, ob der Massen-Upload erfolgreich war oder fehlgeschlagen ist.

      * Zunächst wird die Verarbeitung angezeigt, was bedeutet, dass sie noch nicht abgeschlossen ist
      * Klicken Sie nach erfolgreichem Abschluss auf den Link **Benutzer hinzufügen**, um für jede Zeile eine einfache Statusmeldung anzuzeigen
      * Wenn er stattdessen fehlgeschlagen ist, klicken Sie auf das kleine Symbol unter **Datei** und Sie erhalten ein paar weitere Informationen darüber, warum er fehlgeschlagen ist. Die Zeilennummern der Benutzenden werden ab Zeile 1 referenziert.

1. Überprüfen Sie Ihre Änderungen mit der Admin Console.

>[!NOTE]
>
>Nach einer Nicht-Löschaufnahme können Benutzer, die zuvor migriert und dann in IMS erstellt wurden, in der Bulk User Upload-Datei angezeigt werden. Dies könnte viele Gründe haben. In diesem Fall schlägt das erneute Hochladen des Benutzers fehl. Versuchen Sie stattdessen, den Benutzer aus der Massen-Benutzer-Upload-Datei zu entfernen. Wenn der Benutzer zu verschiedenen Gruppen hinzugefügt werden muss, verwenden Sie die Massen-Benutzer-Bearbeitungsdatei wie unten beschrieben.

### Massenbearbeitung von Benutzern {#user-edit}

#### Anwendungsfall: Gruppen und Benutzer wurden nach AEM as a Cloud Service migriert und über einen Massen-Upload oder eine andere Methode hochgeladen. Jetzt müssen einige Änderungen an mehreren Benutzern gleichzeitig vorgenommen werden, z. B. das Hinzufügen zu einer vorhandenen IMS-Gruppe.

Gehen Sie wie folgt vor, um die Massenbearbeitungsfunktion von Admin Console zu verwenden:

1. Herunterladen der Massenbenutzerdatei von der Admin Console

   1. Navigieren Sie in der Admin Console zu Benutzer .
   1. Klicken Sie rechts auf die Schaltfläche &quot;…“.  Wählen **Benutzerdetails per CSV bearbeiten** aus dem Menü aus
   1. Klicken Sie **CSV-Vorlage herunterladen** und wählen Sie **Aktuelle Benutzer** aus.  Eine CSV-Datei sollte im lokalen Ordner „Downloads“ angezeigt werden.

1. Massenbenutzerdatei bearbeiten

   1. Navigieren Sie in der Admin Console zu Benutzer .
   1. Bearbeiten Sie die CSV-Datei mit einem Texteditor (empfohlen) oder einer Tabellenkalkulationsanwendung wie Excel. Die Verwendung einer Anwendung kann unvorhersehbare Änderungen an den Daten vornehmen. Daher wird empfohlen, nach allen Änderungen einen Texteditor zur Überprüfung der Formatierung der Datei zu verwenden
   1. Die Beschreibungen der Felder in dieser Datei entsprechen denen oben unter „Massen-Benutzer-Upload“
   1. Alle nicht bearbeiteten Benutzer entfernen
   1. Wenn Sie das Feld Benutzergruppen ändern, lassen Sie die aktuellen Gruppen bestehen und fügen Sie neue hinzu, falls erforderlich. Wenn Sie eine vorhandene Gruppe entfernen, wird der Benutzer aus dieser Gruppe in IMS entfernt
   1. Beim Bearbeiten der CSV-Datei können einige Anwendungen beim Speichern zusätzliche Anführungszeichen hinzufügen, was dazu führt, dass die Verarbeitung fehlschlägt. Es empfiehlt sich, die CSV-Rohdatei in einem einfachen Texteditor zu überprüfen, um sicherzustellen, dass jedes Feld nur ein öffnendes und ein schließendes Anführungszeichen hat (und es sich nicht um „intelligente Anführungszeichen“ handeln sollte)

1. Hochladen der Massenbenutzerdatei in die Admin Console

   1. Navigieren Sie in der Admin Console zu Benutzer .
   1. Klicken Sie rechts auf die Schaltfläche &quot;…“. Wählen **Benutzerdetails per CSV bearbeiten** aus dem Menü aus
   1. Drag-and-Drop oder Auswahl der bearbeiteten CSV-Datei für Massenbenutzer
   1. Klicken Sie auf Hochladen .
   1. Sie erhalten eine Antwort, dass die CSV (in die Admin Console) hochgeladen wurde, sie jedoch noch nicht in IMS importiert wurde
   1. Gehen Sie zum Menü &quot;…“ auf der rechten Seite und wählen Sie **Ergebnisse des Massenvorgangs**. Daraufhin wird eine Liste der Massen-Upload-Versuche angezeigt und Sie erfahren (unter Status), ob der Massen-Upload erfolgreich war oder fehlgeschlagen ist.

      * Zunächst wird die Verarbeitung angezeigt, was bedeutet, dass sie noch nicht abgeschlossen ist
      * Klicken Sie nach erfolgreichem Abschluss auf den Link **Benutzerdetails bearbeiten**, um für jede Zeile eine einfache Statusmeldung anzuzeigen
      * Wenn er stattdessen fehlgeschlagen ist, klicken Sie auf das kleine Symbol unter **Datei** und es werden etwas mehr Informationen darüber angezeigt, warum er fehlgeschlagen ist. Die Zeilennummern der Benutzenden werden ab Zeile 1 referenziert.

1. Überprüfen Sie Ihre Änderungen mit Admin Console.
