---
title: Verwalten von Prinzipalen nach der Migration
description: Erfahren Sie, wie Sie Benutzende und Gruppen in IMS und AEM einrichten
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 5%

---

# Verwalten von Prinzipalen nach der Migration {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="Verwalten von Prinzipalen nach der Migration"
>abstract="Erfahren Sie, wie Sie Benutzende und Gruppen in IMS und AEM einrichten"

In diesem Dokument werden die allgemeinen Schritte beschrieben, die Kunden unternehmen sollten, um ihre Benutzer und Gruppen in IMS einzurichten und AEM mit ihrer AEM as a Cloud Service-Umgebung zu arbeiten.

## Verwalten von Prinzipalen {#managing-principals}

Für AEM as a Cloud Service müssen Benutzer und Gruppen in erster Linie mithilfe der Admin Console verwaltet werden.  Bei der Erwägung einer Migration können einige dieser Aufgaben durchgeführt werden, bevor die Inhaltsmigration erfolgt.  Im Wesentlichen sind dies die wichtigsten Aufgabengruppen

* Erstellen von Benutzern und Gruppen in IMS
* Benutzer Gruppen in IMS zuweisen
* IMS-Gruppen AEM Gruppen zuweisen (falls erforderlich)

Die ersten beiden können vor oder nach der Inhaltsmigration durchgeführt werden.  Dies sind Schritte, die sich nur auf Benutzer und Gruppen in IMS auswirken, möglicherweise einschließlich der Integration mit einem externen IDP wie Active Directory oder LDAP.  Diese Schritte werden unter [Verwalten von Prinzipalen in IMS mit der Admin Console](/help/journey-migration/managing-principals.md) beschrieben.

Sobald der Inhalt in die AEM as a Cloud Service-Umgebung migriert wurde, kann der dritte Schritt ausgeführt werden.

### Migrieren von Gruppen

In der Aufnahmephase der Migration werden Gruppen migriert, wenn sie die ACLs oder CUG-Richtlinien für den migrierten Inhalt erfüllen müssen.  Weitere Informationen finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) .

Migrierte Gruppen (diejenigen, die nicht durch die Erstellung von Assets-Sammlungen erstellt wurden - siehe Sammlungen unten) werden als IMS-Gruppen konfiguriert.  Das bedeutet, dass jede Gruppe mit demselben Namen, die in IMS erstellt wurde (z. B. über die Admin Console), mit der Gruppe in AEM verknüpft wird und Benutzer, die Mitglieder der IMS-Gruppe sind, auch in AEM Gruppe aufgenommen werden.  Damit diese Verknüpfung erfolgt, muss die Gruppe zunächst auch in IMS erstellt werden.  Verwenden Sie die Admin Console, um in Ihrer AEM-Instanz einzeln oder stapelweise Gruppen zu erstellen, wie unter [Verwalten von Prinzipalen in IMS mit der Admin Console](/help/journey-migration/managing-principals.md) beschrieben.

Verwenden Sie die AEM Sicherheitsbenutzeroberfläche, um IMS-Gruppen lokalen AEM zuzuweisen.  Siehe [Erstellen und Konfigurieren von Gruppen](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-groups#edit-a-group).  Obwohl dieses Dokument für AEM 6.5 gilt, gilt es auch für das Hinzufügen von Gruppen zu anderen Gruppen in AEM as a Cloud Service.

### IMS-Benutzer

Da Benutzer nicht migriert werden, müssen sie in IMS erstellt werden, damit sie in AEM verwendet werden können.  Es gibt mehrere Möglichkeiten, dies zu erreichen. Es ist jedoch wichtig, dass die erstellten Benutzer den richtigen IMS-Gruppen zugewiesen werden, damit die Benutzer denselben Zugriff auf die Inhalte haben, die sie im vorherigen AEM hatten.  Eines der Tools, das dazu verwendet werden kann, ist die Massen-Upload-Funktion in der Admin Console. Verwenden Sie den Massen-Uploader, um Benutzer zusammen mit Gruppen hochzuladen, denen sie angehören müssen.  Dazu müssen die Gruppen zunächst in IMS erstellt werden, wie oben beschrieben.

Um zu erfahren, zu welchen Gruppen die einzelnen Benutzer gehören sollen, können Sie den Benutzerbericht verwenden (siehe [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)).  Dieser Bericht listet die Gruppen auf, denen jeder Benutzer angehören soll. Diese Liste kann in die Eingabedatei der Admin Console-Massen-Upload-Funktion aufgenommen werden.

### Sammlungen

Beim Erstellen einer Assets-Sammlung werden auch automatisch einige Gruppen erstellt, um den Zugriff auf diese Sammlung zu verwalten.  Diese Gruppen werden migriert, wenn sie in migrierten Sammlungen erwähnt werden, aber nicht so konfiguriert sind, dass sie direkt mit IMS-Gruppen verknüpft werden. AEM bleiben sie &quot;lokale Gruppen&quot; und können nicht über IMS verwaltet werden.

Da diese Gruppen nicht in IMS enthalten sind, kann das Massen-Upload-Tool nicht verwendet werden, um Benutzer als direkte Mitglieder zu erstellen.  IMS-Benutzer, die auch in AEM sind, können diesen Gruppen einzeln hinzugefügt werden. Für eine Massenverarbeitung ist jedoch ein zusätzlicher Schritt erforderlich.  Hier ist eine Möglichkeit, dies zu tun:
* Erstellen Sie eine neue Gruppe oder neue Gruppen in Admin Console/IMS für den Zugriff auf Sammlungen und konfigurieren Sie sie für AEM.
* Melden Sie sich als Mitglied der Gruppe(n) an, damit die Gruppe(n) in AEM erstellt wird.
* Verwenden Sie für die migrierten Sammlungen die Assets-Sammlungsbenutzeroberfläche, um die neue Gruppe als Editor/Eigentümer/Viewer hinzuzufügen.
* Fügen Sie Benutzer (oder Massen-Upload) zu den neuen Gruppen in Admin Console hinzu.
* Wenn sich der Benutzer zum ersten Mal anmeldet, wird sein IMS-Benutzer in AEM erstellt und er sollte Zugriff auf die neuen Gruppen und damit auf die ursprünglichen Sammlungsgruppen haben.

Hinweis: Für die Massenzuweisung von Benutzern müssen die oben genannten Schritte verwendet werden, um die Benutzer in IMS zu erstellen. Benutzer, die bereits in IMS vorhanden sind, können nicht erneut per Massen-Upload erstellt werden.
