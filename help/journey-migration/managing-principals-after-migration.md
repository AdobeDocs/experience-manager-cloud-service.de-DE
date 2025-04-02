---
title: Verwalten von Prinzipalen nach der Migration
description: Erfahren Sie, wie Sie Benutzende und Gruppen in IMS und AEM einrichten
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: 50c8dd725e20cbd372a7d7858fc67b0f53a8d6d4
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 81%

---

# Verwalten von Prinzipalen nach der Migration {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="Verwalten von Prinzipalen nach der Migration"
>abstract="Erfahren Sie, wie Sie Benutzende und Gruppen in IMS und AEM einrichten"

In diesem Dokument werden die allgemeinen Schritte beschrieben, die Kundinnen und Kunden ausführen sollten, um ihre Benutzenden und Gruppen im IMS und in AEM einzurichten und mit ihrer AEM as a Cloud Service-Umgebung zu arbeiten.

Informationen zur Gruppenmigration und zum Bericht zur Prinzipalmigration, der bei jeder Aufnahme verfügbar ist, finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Eine Anleitung zur Verwendung von Massen-Gruppen- und -Benutzerdateien in der Admin Console finden Sie unter [Massen-Upload von Prinzipalen in IMS nach Verwendung von CTT](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md).

## Verwalten von Prinzipalen {#managing-principals}

Für AEM as a Cloud Service müssen Benutzende und Gruppen in erster Linie mithilfe der Admin Console verwaltet werden.  Beim Erwägen einer Migration können einige dieser Aufgaben durchgeführt werden, bevor die Inhaltsmigration erfolgt.  Von diesen Hauptaufgabengruppen

* Erstellen von Benutzenden und Gruppen im IMS
* Zuweisen von Benutzenden zu Gruppen im IMS
* Zuweisen von IMS-Gruppen zu AEM-Gruppen (falls erforderlich)

können die ersten beiden im Grunde vor oder nach der Inhaltsmigration durchgeführt werden. Sie umfassen die Schritte, die sich nur auf Benutzende und Gruppen im IMS auswirken, möglicherweise einschließlich der Integration in ein externes IDP wie Active Directory oder LDAP.  Diese Schritte werden unter [Verwalten von Prinzipalen im IMS mit der Admin Console](/help/journey-migration/managing-principals.md) beschrieben.

Sobald der Inhalt in die AEM as a Cloud Service-Umgebung migriert wurde, kann der dritte Schritt ausgeführt werden.

### Migrieren von Gruppen

In der Aufnahmephase der Migration werden Gruppen migriert, wenn sie die ACLs- oder CUG-Richtlinien für den migrierten Inhalt erfüllen müssen.  Weitere Informationen finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Migrierte Gruppen (diejenigen, die nicht von der Assets-Sammlung oder der Erstellung privater Ordner erstellt wurden - siehe Sammlungen und private Ordner unten) werden als IMS-Gruppen konfiguriert.  Das bedeutet, dass jede Gruppe mit demselben Namen, die im IMS erstellt wurde (z. B. über die Admin Console), mit der Gruppe in AEM verknüpft wird und Benutzende, die Mitglieder der IMS-Gruppe sind, auch in AEM in diese Gruppe aufgenommen werden.  Damit diese Verknüpfung erfolgt, muss die Gruppe zunächst auch im IMS erstellt werden.  Verwenden Sie die Admin Console, um in Ihrer AEM-Instanz einzelne oder mehrere Gruppen zu erstellen, wie unter [Verwalten von Prinzipalen im IMS mit der Admin Console](/help/journey-migration/managing-principals.md) beschrieben.

Verwenden Sie die Benutzeroberfläche „AEM-Sicherheit“, um IMS-Gruppen lokalen AEM-Gruppen zuzuweisen.  Gehen Sie dazu auf die Seite „Tools“ in AEM, klicken Sie auf „Sicherheit“ und wählen Sie „Gruppen“ aus.

### IMS-Benutzende

Da Benutzende nicht migriert werden, müssen sie im IMS erstellt werden, damit sie in AEM verwendet werden können.  Dies kann auf verschiedene Arten erfolgen. Es ist jedoch wichtig, dass die erstellten Benutzenden den richtigen IMS-Gruppen zugewiesen werden, damit sie denselben Zugriff auf die Inhalte haben wie im vorherigen AEM-System.  Eines der Tools, die dazu verwendet werden können, ist die Funktion „Massen-Upload“ in der Admin Console. Verwenden Sie den Massen-Uploader, um Benutzende zusammen mit Gruppen hochzuladen, denen sie angehören müssen.  Hierzu müssen die Gruppen zunächst im IMS erstellt werden, wie oben beschrieben.

Um zu erfahren, zu welchen Gruppen die einzelnen Benutzenden gehören sollen, können Sie den Benutzerbericht verwenden (siehe [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)).  In diesem Bericht sind die Gruppen aufgeführt, denen jede Person angehören sollte. Diese Liste ist normalerweise in der Massen-Benutzereingabedatei der Funktion „Massen-Upload“ der Admin Console enthalten.

### Sammlungen und private Ordner

Beim Erstellen einer Assets-Sammlung oder eines privaten Ordners werden automatisch einige Gruppen erstellt, um den Zugriff auf diesen Assets-Inhalt zu verwalten.  Diese Gruppen werden migriert, wenn sie im migrierten Inhalt erwähnt werden, sie sind jedoch nicht so konfiguriert, dass sie eine direkte Verbindung zu IMS-Gruppen herstellen. In AEM bleiben sie „lokale Gruppen“ und können nicht über IMS verwaltet werden.

Da diese Gruppen nicht im IMS enthalten sind, kann das Tool für den Massen-Upload nicht verwendet werden, um Benutzende als ihre direkten Mitglieder zu erstellen.  IMS-Benutzende, die auch in AEM vorhanden sind, können diesen Gruppen einzeln hinzugefügt werden. Für das Hinzufügen mehrerer Benutzender auf einmal ist jedoch ein zusätzlicher Schritt erforderlich.  Eine Möglichkeit dazu ist Folgende:
* Erstellen Sie in Admin Console/IMS eine neue Gruppe oder neue Gruppen für den Zugriff auf Sammlungen/private Ordner und konfigurieren Sie sie für AEM.
* Melden Sie sich als Mitglied der Gruppe(n) an, damit die Gruppe(n) in AEM erstellt wird/werden.
* Verwenden Sie für die migrierten Sammlungen oder privaten Ordner die Assets-Benutzeroberfläche, um die neue Gruppe als Editor/Inhaber/Betrachter hinzuzufügen.
* Fügen Sie Benutzende zu den neuen Gruppen in der Admin Console hinzu oder laden Sie sie per Massen-Upload hoch.
* Wenn sich der Benutzer zum ersten Mal anmeldet, wird sein IMS-Benutzer in AEM erstellt und er sollte Zugriff auf die neue(n) Gruppe(n) und damit auf die ursprüngliche(n) Sammlung(en) oder private Ordnergruppen haben.

Hinweis: Zur Massenzuweisung von Benutzenden müssen die oben genannten Schritte ausgeführt werden, um die Benutzenden im IMS zu erstellen. Benutzende, die bereits im IMS vorhanden sind, können nicht erneut per Massen-Upload erstellt werden. Allerdings kann diese Art von Änderungen mit dem Massen-Editor vorgenommen werden (siehe [Massen-Upload von Benutzenden in der Admin Console](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html) unter **Benutzerdetails bearbeiten**).
