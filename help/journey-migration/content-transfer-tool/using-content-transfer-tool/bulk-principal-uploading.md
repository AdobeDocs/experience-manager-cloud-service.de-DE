---
title: Massen-Upload von Prinzipalen in IMS nach Verwendung von CTT
description: Überblick über Dateien zum Massen-Upload für Gruppen und Benutzende und deren Verwendung in der Admin Console zum Erstellen von Gruppen und Benutzenden.
exl-id: 43ebd6f1-1492-461a-8d9b-2b55dcde9052
source-git-commit: b9c739a03b358de7c011e50ddbdd609c90f86b6f
workflow-type: ht
source-wordcount: '2384'
ht-degree: 100%

---

# Massen-Upload von Prinzipalen in IMS nach Verwendung von CTT {#bulk-principal-uploading}

>[!CONTEXTUALHELP]
>id="bulk-principal-uploading"
>title="Massen-Upload von Prinzipalen"
>abstract="Überblick über Dateien zum Massen-Upload für Gruppen und Benutzende und deren Verwendung in der Admin Console zum Erstellen von Gruppen und Benutzenden."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="AEM Admin Console-Dokumentation"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

## Einführung {#introduction}

Bei der Migration von Inhalten in die Cloud mithilfe von CTT und CAM werden Gruppen in der AEM-Cloud-Instanz erstellt, allerdings können Gruppen oder Benutzende so nicht in IMS platziert werden. Sie müssen in IMS vorhanden sein, damit sie kundenseitig ordnungsgemäß verwaltet werden können. Glücklicherweise bietet die Admin Console Funktionen, um IMS-Gruppen und -Benutzende massenweise zu erstellen. Die CAM-Aufnahme unterstützt diesen Prozess, indem Eingabedateien für diese Massenerstellung gespeichert werden, sodass Kundinnen und Kunden diese Admin Console-Aktion im Rahmen des gesamten Migrationsprozesses durchführen können. Es werden zwei Arten von Massen-Upload-Dateien erstellt: eine für Gruppen und eine für Benutzende.

Weitere Informationen zur Verwaltung von AEM as a Cloud Service-Benutzenden finden Sie zudem unter [Verwalten von Benutzenden](https://helpx.adobe.com/de/enterprise/using/users.html).

## Allgemeine Regeln für das Hochladen von Dateien {#rules}

Es gibt einige allgemeine Richtlinien zum Bearbeiten und Verwenden der beiden Arten von Upload-Dateien:

* Um diesen Anweisungen folgen zu können, muss zunächst Administratorzugriff auf die Admin Console gewährt werden.
* Es gibt verschiedene Möglichkeiten, um Benutzende und Gruppen in IMS zu erstellen.  Unter [IMS-Unterstützung für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/ims-support) erfahren Sie mehr über alle verfügbaren Optionen.  Hier werden nur die Massen-Upload-Methoden der Admin Console beschrieben.
* In IMS sind drei Identitätstypen möglich: Adobe ID, Enterprise ID und Federated ID.  Die Anweisungen auf dieser Seite gelten nur für die **Adobe ID**.  Wenn Sie die Enterprise ID oder Federated ID verwenden müssen, lesen Sie bitte die vollständige Dokumentation zur [Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) sowie die spezifische Dokumentation zum [Admin Console-Massen-Upload von Gruppen](https://helpx.adobe.com/de/enterprise/using/user-groups.html) und zum [Admin Console-Massen-Upload von Benutzenden](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html).  Die Spezifikationen für die Upload-Dateien weichen bei diesen beiden Identitätstypen etwas voneinander ab.
* Wenn ein einzelnes CSV-Feld mehrere Einträge zulässt (z. B. mehrere Produktprofile, mehrere Gruppen oder mehrere Admins), müssen die Einträge in Anführungszeichen eingeschlossen und durch ein Komma voneinander getrennt werden, z. B. `"profile 1,profile 2"`.

   * Statt doppelter können in diesem Fall auch einfache Anführungszeichen verwendet werden. Allerdings kann dann die Bearbeitung der Datei in Microsoft Excel zu Analyseproblemen führen. Wenn Sie diese Dateien in Excel bearbeiten, achten Sie darauf, doppelte Anführungszeichen anstelle von einfachen zu verwenden.

## Massen-Upload von Gruppen {#group-upload}

#### Anwendungsfall: Gruppen wurden nach AEM as a Cloud Service migriert, doch diese Gruppen sind nicht in IMS/in der Admin Console vorhanden und müssen daher über die Admin Console in IMS hochgeladen werden.

Gehen Sie wie folgt vor, um nach der CTT-/CAM-Migration die Admin Console-Funktion zum Massen-Upload von Gruppen zu verwenden:
1. Herunterladen der Massengruppendatei aus CAM

   1. Navigieren Sie in CAM zu **Content-Übertragung** und wählen Sie **Aufnahmeaufträge** aus.
   1. Klicken Sie auf die Auslassungspunkte (…) in der Zeile der betreffenden Aufnahme und wählen Sie **Prinzipalzusammenfassung anzeigen** aus.
   1. Wählen Sie im angezeigten Dialogfeld in der Dropdown-Liste unter **Datei herunterladen…** die Option **Massengruppendatei** aus und klicken Sie auf die Schaltfläche **Herunterladen**.
   1. Speichern Sie die resultierende CSV-Datei.

1. Bearbeiten der Massengruppendatei

   * Jede Zeile steht für eine hochzuladende Gruppe und hat vier Felder (die Namen der Felder bilden die erste Zeile der Datei):

      * _Name der Benutzergruppe_: Der Gruppenname ist erforderlich und darf maximal 255 Zeichen enthalten.  Dieser Gruppenname muss in IMS und AEM identisch sein.
      * _Beschreibung_: Dieses Feld ist optional und darf maximal 255 Zeichen enthalten.
      * _Benutzergruppen-Administrator_: In diesem Feld muss mindestens eine Person als Gruppen-Admin angegeben werden. Es können mehrere Admins zugewiesen werden, indem jeder Admin-Eintrag durch ein Komma getrennt und die Liste in Anführungszeichen gesetzt wird. Jeder Admin-Eintrag muss den Identitätstyp der Person enthalten, gefolgt von einem Bindestrich und der E-Mail-Adresse.  Zum Beispiel
        `"Adobe ID-myAdmin@example.com,Adobe ID-myOtherAdmin@example.com"`. Geben Sie nach dem Komma, das Admins voneinander trennt, kein Leerzeichen ein. Sie können keine Benutzenden (als Admins) einbeziehen, die derzeit nicht Teil der Organisation in der Admin Console sind.
      * _Zugewiesene Produktprofile_: Dieses Feld ist optional. Sie können mehrere Produktprofile zuweisen, indem Sie jedes Profil durch ein Komma trennen und die Liste in Anführungszeichen setzen. Die Produktprofile, die Sie einbeziehen, müssen jedoch bereits für die Organisation eingerichtet sein. Stellen Sie sicher, dass Sie den Namen des Produktprofils und nicht den Produktnamen angeben.  Die Zugehörigkeit zu Produktprofilen, die einer Gruppe zugewiesen sind, wird von allen Benutzenden in dieser Gruppe übernommen.  So suchen Sie ein Produktprofil:

         1. Gehen Sie zur Admin Console.
         1. Suchen Sie Ihr Produkt (d. h. Adobe Experience Manager as a Cloud Service) und klicken Sie darauf.
         1. Suchen Sie Ihre Umgebung (Instanz) und klicken Sie darauf.
         1. Listen Sie die Produktprofile auf und klicken Sie auf das für Ihre AEM-Umgebung. Das Produktprofil steht oben, z. B. _AEM-Benutzer – Autor – 12345 – 012345_.

   * Beim Bearbeiten der CSV-Datei können in bestimmten Anwendungen beim Speichern zusätzliche Anführungszeichen hinzugefügt werden, wodurch die Verarbeitung fehlschlägt. Es empfiehlt sich, die CSV-Rohdatei in einem einfachen Texteditor zu überprüfen, um sicherzustellen, dass jedes Feld nur je ein öffnendes und ein schließendes Anführungszeichen aufweist (und es darf sich dabei nicht um typografische Anführungszeichen handeln).

1. Hochladen der Massengruppendatei in die Admin Console

   1. Navigieren Sie in der Admin Console zu **Benutzer** und dann zu **Benutzergruppen**
   1. Klicken Sie rechts auf die Schaltfläche mit den Auslassungspunkten (…). Wählen Sie im Menü die Option **Benutzergruppen per CSV-Datei hinzufügen** und dann die CSV-Datei für den Upload aus. Klicken Sie auf **Hochladen**.
   1. Es wird eine Meldung angezeigt, dass die CSV-Datei (in die Admin Console) hochgeladen, aber noch nicht in IMS importiert wurde.
   1. Navigieren Sie wieder zum Menü mit den Auslassungspunkten (…) und wählen Sie **Ergebnisse des Massenvorgangs** aus. Daraufhin wird eine Liste der Massen-Upload-Versuche angezeigt, in der Sie unter **Status** sehen können, ob der Massen-Upload gerade läuft, erfolgreich war oder fehlgeschlagen ist.

      * Zunächst wird der Status „Wird verarbeitet“ angezeigt. Dies bedeutet, dass die Verarbeitung noch nicht abgeschlossen ist.
      * Klicken Sie nach erfolgreichem Abschluss auf den Link **Benutzergruppen hinzufügen**, um für jede Zeile eine einfache Statusmeldung zu sehen.
      * Wenn der Vorgang stattdessen fehlgeschlagen ist, klicken Sie auf das kleine Symbol unter **Datei**. Sie erhalten so weitere Informationen darüber, warum der Vorgang fehlgeschlagen ist.  Die Gruppenzeilennummern werden ab Zeile 1 referenziert.
1. Überprüfen Sie Ihre Änderungen mit der Admin Console.

## Massen-Upload und -bearbeitung von Benutzenden {#bulk-user}

Die Admin Console umfasst zwei separate Aktionen zum Hochladen und Bearbeiten von Benutzerdetails. Die nachfolgenden Anweisungen beziehen sich auf das Hinzufügen von neuen Benutzenden zu IMS. Anweisungen zum Bearbeiten von vorhandenen IMS-Benutzenden finden Sie im Abschnitt [Massenbearbeitung von Benutzenden](#user-edit).

### Massen-Upload von Benutzenden {#user-upload}

#### Anwendungsfall: Gruppen wurden nach AEM as a Cloud Service migriert und per Massen-Upload oder mithilfe einer anderen Methode hochgeladen.  Möglicherweise sind Benutzende nicht in IMS/in der Admin Console vorhanden und müssen daher hochgeladen und über die Admin Console mit ihren Gruppen in IMS verknüpft werden.

>[!NOTE]
>
>Eine Benutzerin bzw. ein Benutzer wird in der Datei zum **Massen-Upload von Benutzenden** angezeigt, wenn diese Person zu einer Gruppe gehört, die während derselben Aufnahme aufgenommen wurde, aus der die Datei erstellt wurde. Dies ist ebenfalls möglich, wenn sich die Person direkt in einer ACL oder CUG des migrierten Inhalts befindet oder Mitglied einer integrierten oder lokalen Gruppe ist, die in der ACL oder CUG des migrierten Inhalts enthalten ist. Weitere Informationen zu diesen Fällen finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Gehen Sie wie folgt vor, um die Admin Console-Funktion zum Massen-Upload von Benutzenden zu verwenden:

1. Herunterladen der Massenbenutzerdatei aus CAM
   1. Navigieren Sie in CAM zu **Content-Übertragung** und wählen Sie **Aufnahmeaufträge** aus.
   1. Klicken Sie auf die Auslassungspunkte (…) in der Zeile der betreffenden Aufnahme und wählen Sie **Prinzipalzusammenfassung anzeigen** aus.
   1. Wählen Sie im angezeigten Dialogfeld in der Dropdown-Liste unter **Datei herunterladen** die Option **Massenbenutzerdatei** aus und klicken Sie auf die Schaltfläche **Herunterladen**.
   1. Speichern Sie die resultierende CSV-Datei.
1. Bearbeiten der Massenbenutzerdatei
   * Jede Zeile steht für eine hochzuladende Person und hat fünfzehn Felder (die Namen der Felder bilden die erste Zeile der Datei). Einige Felder sind optional und werden hier nicht beschrieben. Siehe [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format).  Die Felder lauten:

      * _Identitätstyp_: Optional.  Ist hier nichts angegeben, wird die Adobe ID als Identitätstyp erstellt.
      * _Benutzername_: Optional. Wird nicht für Adobe ID-Uploads verwendet.
      * _Domain_: Optional. Wird nicht für Adobe ID-Uploads verwendet.
      * _E-Mail_: Erforderlich.  Die E-Mail-Adresse wird bei der ersten Anmeldung der Person zur Überprüfung verwendet.
      * _Vorname_: Optional.  Sollte verwendet werden, da der Vorname an mehreren Stellen zusammen mit dem Nachnamen angezeigt wird.
      * _Nachname_: Optional.  Sollte verwendet werden, da der Nachname an mehreren Stellen angezeigt wird.
      * _Ländercode_: Optional. Wird nicht für Adobe ID-Uploads verwendet.
      * _ID_: Optional. Wird nicht für Adobe ID-Uploads verwendet.
      * _Produktkonfigurationen_: Optional. Dieses Feld wird auch von allen Gruppen übernommen, denen die Person angehört.
      * _Administratorrollen_: Optional. Verwenden Sie dieses Feld für Admin-Benutzende. Weitere Informationen finden Sie unter [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format).
      * _Verwaltete Produktkonfigurationen_: Optional.  Weitere Informationen finden Sie unter [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format). Dieses Feld wird auch von allen Gruppen übernommen, denen die Person angehört.
      * _Benutzergruppen_: Optional. Eine Liste der Gruppen, denen die Person als Mitglied zugewiesen werden soll. Bei jeder Gruppe muss es sich um eine bereits vorhandene IMS-Gruppe handeln. Wenn die Massenbenutzerdatei aus CAM heruntergeladen wird, wird dieses Feld mit den Namen der IMS-aktivierten Gruppe vorausgefüllt, zu der die Person vor der Migration (direkt oder indirekt) gehörte.
      * _Verwaltete Benutzergruppen_: Optional.  Weitere Informationen finden Sie unter [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format). Dieses Feld wird auch von allen Gruppen übernommen, denen die Person angehört.
      * _Verwaltete Produkte_: Optional.  Weitere Informationen finden Sie unter [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format). Dieses Feld wird auch von allen Gruppen übernommen, denen die Person angehört.
      * _Verwaltete Verträge_: Optional.  Weitere Informationen finden Sie unter [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format).
      * _Entwicklerzugriff_: Optional.  Weitere Informationen finden Sie unter [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format).
      * _Automatisch zugewiesene Produkte_: Optional.  Weitere Informationen finden Sie unter [Massenbenutzerdatei im CSV-Format](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html#csv-format).

   * Beim Bearbeiten der CSV-Datei können in bestimmten Anwendungen beim Speichern zusätzliche Anführungszeichen hinzugefügt werden, wodurch die Verarbeitung fehlschlägt. Es empfiehlt sich, die CSV-Rohdatei in einem einfachen Texteditor zu überprüfen, um sicherzustellen, dass jedes Feld nur je ein öffnendes und ein schließendes Anführungszeichen aufweist (und es darf sich dabei nicht um typografische Anführungszeichen handeln).

1. Verwenden der Admin Console zum Importieren der Massenbenutzerdatei

   1. Navigieren Sie in der Admin Console zu „Benutzer“.
   1. Klicken Sie auf die Schaltfläche **Benutzer über CSV hinzufügen**.
   1. Ziehen Sie eine aus CAM heruntergeladene Massenbenutzerdatei im CSV-Format per Drag-and-Drop oder wählen Sie eine aus.
   1. Klicken Sie auf die Schaltfläche **Hochladen**.
   1. Es wird eine Meldung angezeigt, dass die CSV-Datei (in die Admin Console) hochgeladen, aber noch nicht in IMS importiert wurde.
   1. Navigieren Sie rechts zum Menü mit den Auslassungspunkten (…) und wählen Sie **Ergebnisse des Massenvorgangs** aus. Daraufhin wird eine Liste der Massen-Upload-Versuche angezeigt, in der Sie unter **Status** sehen können, ob der Massen-Upload gerade läuft, erfolgreich war oder fehlgeschlagen ist.

      * Zunächst wird der Status „Wird verarbeitet“ angezeigt. Dies bedeutet, dass die Verarbeitung noch nicht abgeschlossen ist.
      * Klicken Sie nach erfolgreichem Abschluss auf den Link **Benutzergruppen hinzufügen**, um für jede Zeile eine einfache Statusmeldung zu sehen.
      * Wenn der Vorgang stattdessen fehlgeschlagen ist, klicken Sie auf das kleine Symbol unter **Datei**. Sie erhalten so weitere Informationen darüber, warum der Vorgang fehlgeschlagen ist.  Die Benutzerzeilennummern werden ab Zeile 1 referenziert.

1. Überprüfen Sie Ihre Änderungen mit der Admin Console.

>[!NOTE]
>
>Nach einer nicht löschenden Aufnahme können Benutzende, die zuvor migriert und dann in IMS erstellt wurden, in der Massen-Upload-Datei für Benutzende angezeigt werden. Dies kann vielerlei Gründe haben. In diesem Fall schlägt der erneute Benutzer-Upload fehl. Versuchen Sie stattdessen, die Person aus der Massen-Upload-Datei für Benutzende zu entfernen. Wenn die Person zu verschiedenen Gruppen hinzugefügt werden muss, verwenden Sie die Massenbearbeitungsdatei für Benutzende wie unten beschrieben.

### Massenbearbeitung von Benutzenden {#user-edit}

#### Anwendungsfall: Gruppen und Benutzende wurden nach AEM as a Cloud Service migriert und per Massen-Upload oder mithilfe einer anderen Methode hochgeladen.  Nun müssen einige Änderungen an mehreren Benutzenden gleichzeitig vorgenommen werden, z. B. um sie einer vorhandenen IMS-Gruppe hinzuzufügen.

Gehen Sie wie folgt vor, um die Admin Console-Funktion zur Massenbearbeitung von Benutzenden zu verwenden:

1. Herunterladen der Massenbenutzerdatei aus der Admin Console

   1. Navigieren Sie in der Admin Console zu „Benutzer“.
   1. Klicken Sie rechts auf die Schaltfläche mit den Auslassungspunkten (…). Wählen Sie im Menü die Option **Benutzerdetails über CSV bearbeiten** aus.
   1. Klicken Sie auf **CSV-Vorlage herunterladen** und wählen Sie **Aktuelle Benutzer** aus.  Im lokalen Ordner „Downloads“ sollte eine CSV-Datei angezeigt werden.

1. Bearbeiten der Massenbenutzerdatei

   1. Navigieren Sie in der Admin Console zu „Benutzer“.
   1. Bearbeiten Sie die CSV-Datei mit einem Texteditor (empfohlen) oder einer Tabellenkalkulationsanwendung wie Excel. Der Einsatz einer Anwendung kann zu unvorhersehbaren Änderungen an den Daten führen. Daher wird empfohlen, die Formatierung der Datei nach allen Änderungen mit einem Texteditor zu überprüfen.
   1. Die Beschreibungen der Felder in dieser Datei entsprechen denen oben unter „Massen-Upload von Benutzenden“.
   1. Entfernen Sie alle nicht bearbeiteten Benutzenden.
   1. Wenn Sie das Feld „Benutzergruppen“ ändern, lassen Sie die aktuellen Gruppen bestehen und fügen Sie ggf. neue hinzu. Wenn Sie eine vorhandene Gruppe entfernen, wird die Benutzerin bzw. der Benutzer aus dieser Gruppe in IMS entfernt.
   1. Beim Bearbeiten der CSV-Datei können in bestimmten Anwendungen beim Speichern zusätzliche Anführungszeichen hinzugefügt werden, wodurch die Verarbeitung fehlschlägt. Es empfiehlt sich, die CSV-Rohdatei in einem einfachen Texteditor zu überprüfen, um sicherzustellen, dass jedes Feld nur je ein öffnendes und ein schließendes Anführungszeichen aufweist (und es darf sich dabei nicht um typografische Anführungszeichen handeln).

1. Hochladen der Massenbenutzerdatei in die Admin Console

   1. Navigieren Sie in der Admin Console zu „Benutzer“.
   1. Klicken Sie rechts auf die Schaltfläche mit den Auslassungspunkten (…). Wählen Sie im Menü die Option **Benutzerdetails über CSV bearbeiten** aus.
   1. Ziehen Sie die bearbeitete Massenbenutzerdatei im CSV-Format per Drag-and-Drop oder wählen Sie sie aus.
   1. Klicken Sie auf die Schaltfläche „Hochladen“.
   1. Es wird eine Meldung angezeigt, dass die CSV-Datei (in die Admin Console) hochgeladen, aber noch nicht in IMS importiert wurde.
   1. Navigieren Sie rechts zum Menü mit den Auslassungspunkten (…) und wählen Sie **Ergebnisse des Massenvorgangs** aus. Daraufhin wird eine Liste der Massen-Upload-Versuche angezeigt, in der Sie unter „Status“ sehen können, ob der Massen-Upload gerade läuft, erfolgreich war oder fehlgeschlagen ist.

      * Zunächst wird der Status „Wird verarbeitet“ angezeigt. Dies bedeutet, dass die Verarbeitung noch nicht abgeschlossen ist.
      * Klicken Sie nach erfolgreichem Abschluss auf den Link **Benutzerdetails bearbeiten**, um für jede Zeile eine einfache Statusmeldung zu sehen.
      * Wenn der Vorgang stattdessen fehlgeschlagen ist, klicken Sie auf das kleine Symbol unter **Datei**. Dadurch werden weitere Informationen dazu angezeigt, warum der Vorgang fehlgeschlagen ist.  Die Benutzerzeilennummern werden ab Zeile 1 referenziert.

1. Überprüfen Sie Ihre Änderungen mit der Admin Console.
