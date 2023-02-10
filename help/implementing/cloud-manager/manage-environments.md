---
title: Verwalten von Umgebungen
description: Erfahren Sie mehr über die Typen von Umgebungen, die Sie erstellen können, und wie Sie sie für ein Cloud Manager-Projekt erstellen.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
source-git-commit: 2af14814a4e8af22cfdc1caa2ff656020c79ce77
workflow-type: tm+mt
source-wordcount: '1826'
ht-degree: 88%

---

# Verwalten von Umgebungen {#managing-environments}

Erfahren Sie mehr über die Typen von Umgebungen, die Sie erstellen können, und wie Sie sie für ein Cloud Manager-Projekt erstellen.

## Umgebungstypen {#environment-types}

Ein Benutzer mit den erforderlichen Berechtigungen kann die folgenden Umgebungstypen erstellen (im Rahmen der dem jeweiligen Mandanten zur Verfügung stehenden Möglichkeiten).

* **Produktion und Staging** - Die Produktions- und Staging-Umgebungen sind als Paar verfügbar und werden für Produktions- bzw. Testzwecke verwendet.

* **Entwicklung**: Die Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken erstellt werden und wird ausschließlich produktionsfremden Pipelines zugeordnet.

* **Schnelle Entwicklung** - Eine schnelle Entwicklungsumgebung (RDE) ermöglicht es Entwicklern, Änderungen schnell bereitzustellen und zu überprüfen, wodurch der Zeitaufwand für das Testen von Funktionen minimiert wird, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren. Siehe [Dokumentation zur raschen Entwicklung](/help/implementing/developing/introduction/rapid-development-environments.md) für Details zur Verwendung eines RDE.

Die Funktionen einzelner Umgebungen hängen von den Lösungen ab, die in der Variablen [program](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) der Umwelt.

* [Sites](/help/sites-cloud/home.md)
* [Assets](/help/assets/home.md)
* [Forms](/help/forms/home.md)
* [Screens](/help/screens-cloud/home.md)

>[!NOTE]
>
>Die Produktions- und Staging-Umgebung werden nur als Paar erstellt. Sie können nicht nur eine Staging- oder eine Produktionsumgebung erstellen.

## Hinzufügen einer Umgebung {#adding-environments}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie eine Umgebung hinzufügen möchten.

1. Klicken Sie auf der Seite **Programmübersicht** auf der Karte **Umgebungen** auf **Umgebung hinzufügen**, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

      ![Registerkarte Umgebungen](assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen** wird Folgendes angezeigt:

   * Wählen Sie eine [**Umgebungstyp**.](#environment-types)
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Namen des Umgebungstyps angezeigt.
   * Bereitstellung einer Umgebung **Name**.
   * Bereitstellung einer Umgebung **Beschreibung**.
   * Wählen Sie eine **Primäre Region** aus der Dropdown-Liste aus.
      * Beachten Sie, dass dies nach der Erstellung nicht mehr geändert werden kann.
   * Wenn Sie eine **Produktion und Staging** -Umgebung müssen Sie einen Umgebungsnamen und eine Beschreibung für Ihre Produktions- und Staging-Umgebungen angeben.
      ![Dialogfeld „Umgebung hinzufügen“](assets/add-environment2.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Der Bildschirm **Überblick** zeigt nun in der Karte **Umgebungen** Ihre neue Umgebung an. Sie können jetzt Pipelines für Ihre neue Umgebung einrichten.

## Umgebungsdetails {#viewing-environment}

Sie können die Karte **Umgebungen** auf der Übersichtsseite verwenden, um auf zwei Arten auf Details zu Umgebungen zuzugreifen.

1. Klicken Sie auf der Seite **Überblick** auf die Registerkarte **Umgebungen** oben im Bildschirm.

   ![Registerkarte Umgebungen](assets/environments-tab2.png)

   * Alternativ können Sie auf die Schaltfläche **Alle anzeigen** auf der Karte **Umgebungen** klicken, um direkt zur Registerkarte **Umgebungen** zu gelangen.

      ![Option „Alle anzeigen“](assets/environment-showall.png)

1. **Umgebungen** öffnet und listet alle Umgebungen für das Programm auf.

   ![Registerkarte „Umgebungen“](assets/environment-view-2.png)

1. Klicken Sie auf eine Umgebung in der Liste, um deren Details anzuzeigen.

   ![Umgebungsdetails](assets/environ-preview1.png)

Alternativ können Sie auf die Schaltfläche mit den Auslassungspunkten der gewünschten Umgebung klicken und anschließend auf **Details anzeigen**.

![Anzeigen von Umgebungsdetails](assets/view-environment-details.png)

>[!NOTE]
>
>Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken Sie wie zuvor beschrieben auf **Alle anzeigen**, um alle Umgebungen des Programms anzuzeigen.

### Zugriff auf den Vorschau-Service {#access-preview-service}

Cloud Manager bietet für jede AEM as a Cloud Service-Umgebung einen Vorschau-Service (bereitgestellt als zusätzlicher Veröffentlichungs-Service).

Mithilfe des Service können Sie eine Vorschau des endgültigen Erlebnisses einer Website anzeigen, bevor diese die tatsächliche Veröffentlichungsumgebung erreicht und öffentlich verfügbar wird.

Bei der Erstellung wird auf den Vorschau-Service eine standardmäßige IP-Zulassungsliste mit der Bezeichnung `Preview Default [<envId>]` angewendet, wodurch der gesamte Traffic zum Vorschau-Service blockiert wird. Sie müssen die Anwendung der standardmäßigen IP-Zulassungsliste auf den Vorschau-Service aktiv aufheben, um den Zugriff zu ermöglichen.

![Vorschau-Service und seine Zulassungsliste](assets/preview-ip-allow.png)

Benutzer mit den erforderlichen Berechtigungen müssen die folgenden Schritte ausführen, bevor sie die Vorschau-Dienst-URL freigeben, um den Zugriff darauf sicherzustellen.

1. Erstellen Sie eine geeignete IP-Zulassungsliste, wenden Sie sie auf den Vorschau-Service an und machen Sie die Anwendung der `Preview Default [<envId>]`-Zulassungsliste sofort rückgängig.

   * Weitere Informationen finden Sie im Dokument [Anwenden und Rückgängigmachen der Anwendung von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md).

1. Verwenden Sie den Workflow zum Aktualisieren von **IP-Zulassungslisten**, um die standardmäßige IP-Adresse zu entfernen und nach Bedarf IP-Adressen hinzuzufügen. Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md).

Sobald der Zugriff auf den Vorschaudienst entsperrt ist, wird das Sperrsymbol vor dem Vorschaudienstnamen nicht mehr angezeigt.

Nach der Aktivierung können Sie Inhalte im Vorschau-Service veröffentlichen, indem Sie die Benutzeroberfläche zur Verwaltung von Veröffentlichungen in AEM verwenden. Weitere detaillierte Informationen finden Sie im Dokument [Vorschau von Inhalten](/help/sites-cloud/authoring/fundamentals/previewing-content.md).

>[!NOTE]
>
>Ihre Umgebung muss sich in AEM Version befinden `2021.05.5368.20210529T101701Z` oder neuer, um den Vorschaudienst zu verwenden. Stellen Sie sicher, dass dazu in Ihrer Umgebung eine Update-Pipeline erfolgreich ausgeführt wurde.

## Aktualisieren von Umgebungen {#updating-dev-environment}

Als Cloud-nativer Service verwaltet Adobe automatisch die Aktualisierungen Ihrer Staging- und Produktionsumgebungen innerhalb der Produktionsprogramme.

Aktualisierungen von Entwicklungsumgebungen sowie Umgebungen in Sandbox-Programmen werden jedoch innerhalb der Programme verwaltet. Wenn in einer solchen Umgebung nicht die neueste öffentlich verfügbare AEM-Version ausgeführt wird, zeigt der Status auf der Karte **Umgebungen** auf dem Bildschirm **Überblick** des Programms **Verfügbare Aktualisierung** an.

![Aktualisierungsstatus der Umgebung](assets/environ-update.png)

### Updates und Pipelines {#updates-pipelines}

Pipelines sind der einzige Weg, [Code in den Umgebungen von AEM as a Cloud Service bereitzustellen.](deploy-code.md) Aus diesem Grund ist jede Pipeline mit einer bestimmten AEM-Version verknüpft.

Wenn Cloud Manager erkennt, dass eine neuere Version von AEM verfügbar ist als die, die zuletzt mit der Pipeline bereitgestellt wurde, wird der Status **Aktualisierung verfügbar** für die Umgebung angezeigt.

Der Prozess der Aktualisierung erfolgt also in zwei Schritten:

1. Aktualisieren der Pipeline mit der neuesten AEM-Version
1. Ausführen der Pipeline zum Bereitstellen der neuen Version von AEM in einer Umgebung

### Aktualisieren von Umgebungen {#updating-your-environments}

Die Option **Aktualisieren** ist durch Klicken auf die Schaltfläche mit den Auslassungspunkten der Umgebung über die Karte **Umgebungen** für Entwicklungsumgebungen und Umgebungen in Sandbox-Programmen verfügbar.

![Option „Aktualisieren“ auf der Karte Umgebungen](assets/environ-update2.png)

Diese Option ist auch verfügbar, indem Sie auf die Registerkarte **Umgebungen** klicken und anschließend auf die Schaltfläche mit den Auslassungspunkten der Umgebung.

![Update-Option auf der Registerkarte „Umgebungen“](assets/environ-update3.png)

Ein Benutzer mit der Rolle **Implementierungs-Manager** kann diese Option verwenden, um die mit dieser Umgebung verknüpfte Pipeline auf die neueste AEM-Version zu aktualisieren.

Nachdem die Pipeline-Version auf die neueste öffentlich verfügbare AEM-Version aktualisiert wurde, wird der Benutzer aufgefordert, die zugehörige Pipeline auszuführen, um die neueste Version in der Umgebung bereitzustellen.

![Aufforderung zur Ausführung der Pipeline zur Aktualisierung der Umgebung](assets/update-run-pipeline.png)

Das Verhalten der Option **Aktualisieren** hängt von der Konfiguration und dem aktuellen Status des Programms ab.

* Wenn die Pipeline bereits aktualisiert wurde, fordert die Option **Aktualisieren** den Benutzer auf, die Pipeline auszuführen.
* Wenn die Pipeline gerade aktualisiert wird, informiert die Option **Aktualisieren** den Benutzer darüber, dass bereits eine Aktualisierung ausgeführt wird.
* Wenn keine geeignete Pipeline existiert, fordert die Option **Aktualisieren** den Benutzer auf, eine zu erstellen.

## Löschen von Entwicklungsumgebungen {#deleting-environment}

Benutzer mit den erforderlichen Berechtigungen können eine Entwicklungsumgebung löschen.

Vom Bildschirm **Überblick** des Programms klicken Sie auf der Karte **Umgebungen** auf die Schaltfläche mit den Auslassungspunkten der Entwicklungsumgebung, die Sie löschen möchten.

![Die Löschoption](assets/environ-delete.png)

Die Löschoption ist auch über die Registerkarte **Umgebungen** des Fensters **Überblick** des Programms verfügbar. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten der Umgebung und anschließend auf **Löschen**.

![Die Löschoption auf der Registerkarte „Umgebungen“](assets/environ-delete2.png)

>[!NOTE]
>
>* In einem Produktionsprogramm erstellte Produktions- und Staging-Umgebungen können nicht gelöscht werden.
>* Produktions- und Staging-Umgebungen in einem Sandbox-Programm können gelöscht werden.


## Zugriffsverwaltung {#managing-access}

Wählen Sie aus dem Menü mit den Auslassungspunkten der Umgebung auf der Karte **Umgebungen** die Option **Zugriff verwalten** aus. Sie können direkt zur Autoreninstanz gehen und den Zugriff für Ihre Umgebung verwalten.

![Verwalten der Zugriffsoption](assets/environ-access.png)

## Zugriff auf die Entwicklerkonsole {#accessing-developer-console}

Wählen Sie aus dem Menü mit den Auslassungspunkten der Umgebung auf der Karte **Umgebungen** die Option **Entwicklerkonsole** aus. Dadurch wird eine neue Registerkarte in Ihrem Browser mit der Anmeldeseite der **Entwicklerkonsole** geöffnet.

![](assets/environ-devconsole.png)

Nur Benutzer mit der Rolle **Entwickler** haben Zugriff auf die **Entwicklerkonsole**. Für Sandbox-Programme hat jedoch jeder Benutzer mit Zugriff auf das Sandbox-Programm auch Zugriff auf die **Entwicklerkonsole**.

Weitere Informationen finden Sie im Dokument [Versetzen von Sandbox-Umgebungen in den Ruhezustand und Aufheben des Ruhezustandes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/sandbox-programs.html?lang=de#hibernating-introduction).

Diese Option ist auch über die Registerkarte **Umgebung** des Fensters **Überblick** beim Klicken auf das Menü mit den Auslassungspunkten einer einzelnen Umgebung verfügbar.

## Lokale Anmeldung {#login-locally}

Wählen Sie **Lokale Anmeldung** aus dem Menü mit den Auslassungspunkten in der Karte **Umgebungen** aus, um sich lokal bei Adobe Experience Manager anzumelden.

![Lokale Anmeldung](assets/environ-login-locally.png)

Darüber hinaus können Sie sich über die Registerkarte **Umgebungen** der Seite **Überblick** lokal anmelden.

![Lokale Anmeldung über die Registerkarte Umgebungen](assets/environ-login-locally-2.png)

## Verwalten von benutzerdefinierten Domain-Namen {#manage-cdn}

Benutzerdefinierte Domain-Namen werden in Cloud Manager for Sites-Programmen sowohl für Veröffentlichungs- als auch für Vorschau-Services unterstützt. Jede Cloud Manager-Umgebung kann bis zu 250 benutzerdefinierte Domains hosten.

Um benutzerdefinierte Domain-Namen zu konfigurieren, gehen Sie zur Registerkarte **Umgebungen** und klicken Sie auf eine Umgebung, um die Details der Umgebung anzuzeigen.

![Umgebungsdetails](assets/domain-names.png)

Die folgenden Aktionen können für Ihre Umgebung im Veröffentlichungs-Service ausgeführt werden.

* [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

* [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)

* [Überprüfen des Status des benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) oder eines [SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn).

* [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn)


## Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

IP-Zulassungslisten werden in Cloud Manager für Autoren-, Veröffentlichungs- und Vorschau-Services für Sites-Programme unterstützt.

Um IP-Zulassungslisten zu verwalten, gehen Sie zur Registerkarte **Umgebungen** der Seite **Überblick** Seite Ihres Programms. Klicken Sie auf eine einzelne Umgebung, um deren Details zu verwalten.

### Anwenden einer IP-Zulassungsliste {#apply-ip-allow-list}

Beim Anwenden einer IP-Zulassungsliste werden alle in der Definition der Zulassungsliste enthaltenen IP-Adressen-Bereiche mit einem Autoren- oder Veröffentlichungs-Service in einer Umgebung verknüpft. Um eine IP-Zulassungsliste anwenden zu können, muss der betreffende Anwender die Rolle **Geschäftsinhaber** oder **Implementierungs-Manager** innehaben und angemeldet sein.

Die IP-Zulassungsliste muss in Cloud Manager vorhanden sein, damit sie auf eine Umgebung angewendet werden kann. Weitere Informationen zu IP-Zulassungslisten in Cloud Manager finden Sie im Dokument [Einführung in IP-Zulassungslisten in Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

Gehen Sie wie folgt vor, um eine IP-Zulassungsliste anzuwenden.

1. Gehen Sie von der Registerkarte **Umgebungen** des Bildschirms **Überblick** des Programms zu der bestimmten Umgebung und gehen Sie zur Tabelle **IP-Zulassungslisten**.
1. Verwenden Sie die Eingabefelder oben in der Tabelle der IP-Zulassungsliste, um die IP-Zulassungsliste und den Autoren- oder Veröffentlichungs-Service auszuwählen, auf die Sie sie anwenden möchten.
1. Klicken Sie auf **Übernehmen** und bestätigen Sie Ihre Übermittlung.

### Rückgängigmachen der Anwendung einer IP-Zulassungsliste {#unapply-ip-allow-list}

Durch das Rückgängigmachen der Anwendung einer IP-Zulassungsliste werden alle in der Definition der Zulassungsliste enthaltenen IP-Adressen-Bereiche von einem Autoren- oder Veröffentlichungs-Service in einer Umgebung getrennt. Um die Anwendung einer IP-Zulassungsliste rückgängig machen zu können, muss der betreffende Anwender die Rolle **Geschäftsinhaber** oder **Implementierungs-Manager** innehaben und angemeldet sein.

Führen Sie die folgenden Schritte aus, um die Anwendung einer IP-Zulassungsliste rückgängig zu machen.

1. Gehen Sie von der Registerkarte **Umgebungen** des Bildschirms **Überblick** des Programms zu der bestimmten Umgebung und gehen Sie zur Tabelle **IP-Zulassungslisten**.
1. Ermitteln Sie die Zeile, in der die Regel der IP-Zulassungsliste aufgeführt ist, deren Anwendung Sie rückgängig machen möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten am Ende der Zeile.
1. Wählen Sie **Anwendung rückgängig machen** aus und bestätigen Sie Ihre Übermittlung.
