---
title: Verwalten von Umgebungen
description: Erfahren Sie mehr über die Arten von Umgebungen, die Sie erstellen können, und wie Sie sie für ein Cloud Manager-Projekt erstellen.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
source-git-commit: 1a49bcd5b76e6a3b0d5a3168cef445101dc8d149
workflow-type: tm+mt
source-wordcount: '2607'
ht-degree: 81%

---


# Verwalten von Umgebungen {#managing-environments}

Erfahren Sie mehr über die Arten von Umgebungen, die Sie erstellen können, und wie Sie sie für ein Cloud Manager-Projekt erstellen.

## Umgebungstypen {#environment-types}

Ein Benutzer mit den erforderlichen Berechtigungen kann die folgenden Umgebungstypen erstellen (im Rahmen der dem jeweiligen Mandanten zur Verfügung stehenden Möglichkeiten).

* **Produktion und Staging** - Die Produktions- und Staging-Umgebungen sind als Paar verfügbar und werden für Produktions- bzw. Testzwecke verwendet. Führen Sie Leistungs- und Sicherheitstests in der Staging-Umgebung durch. Sie hat dieselbe Größe wie die Produktion.

* **Entwicklung** - Eine Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken erstellt werden und nur produktionsfremden Pipelines zugeordnet werden.  Entwicklungsumgebungen haben nicht dieselbe Größe wie Staging- und Produktionsumgebungen und sollten nicht für Leistungs- und Sicherheitstests verwendet werden.

* **Schnelle Entwicklung**: Eine schnelle Entwicklungsumgebung (RDE) ermöglicht es Entwicklungspersonen, Änderungen schnell bereitzustellen und zu überprüfen, wodurch der Zeitaufwand für das Testen von Funktionen, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren, minimiert wird. Details zur Verwendung einer RDE finden Sie in der [Dokumentation zur schnellen Entwicklungsumgebung](/help/implementing/developing/introduction/rapid-development-environments.md).

Die Fähigkeiten der einzelnen Umgebungen hängen von den Lösungen ab, die im [Programm](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) der Umgebung ermöglicht werden.

* [Sites](/help/overview/introduction.md)
* [Assets](/help/assets/overview.md)
* [Forms](/help/forms/home.md)
* [Screens](/help/screens-cloud/introduction/introduction.md)

>[!NOTE]
>
>Die Produktions- und Staging-Umgebung werden nur als Paar erstellt. Sie können nicht nur eine Staging- oder nur eine Produktionsumgebung erstellen.

## Hinzufügen einer Umgebung {#adding-environments}

Um eine Umgebung hinzuzufügen oder zu bearbeiten, muss ein Benutzer Mitglied der **Business Owner** Rolle.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie eine Umgebung hinzufügen möchten.

1. Auf der Seite **Programmübersicht** klicken Sie auf der Karte **Umgebungen** auf **Umgebung hinzufügen**, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

     ![Registerkarte Umgebungen](assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen** wird Folgendes angezeigt:

   * Wählen Sie einen [**Umgebungstyp**.](#environment-types)
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Namen des Umgebungstyps angezeigt.
   * Geben Sie einen **Namen** für die Umgebung an.
   * Geben Sie eine **Beschreibung** für die Umgebung an.
   * Wenn Sie eine **Produktion + Staging**-Umgebung hinzufügen, müssen Sie einen Umgebungsnamen und eine Beschreibung sowohl für die Produktions- als auch für die Staging-Umgebung angeben.
   * Wählen Sie in der Dropdown-Liste eine **primäre Region** aus.
      * Die primäre Region kann nach der Erstellung nicht mehr geändert werden.
      * Je nach den verfügbaren Berechtigungen können Sie [mehrere Regionen](#multiple-regions) konfigurieren.

   ![Dialogfeld „Umgebung hinzufügen“](assets/add-environment2.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Der Bildschirm **Überblick** zeigt nun in der Karte **Umgebungen** Ihre neue Umgebung an. Sie können jetzt Pipelines für Ihre neue Umgebung einrichten.

## Mehrere Veröffentlichungsregionen {#multiple-regions}

Benutzende mit der **Geschäftsinhaber**-Rolle können Produktions- und Staging-Umgebungen so konfigurieren, dass neben der primären Region bis zu drei weitere Veröffentlichungsregionen einbezogen werden. Zusätzliche Veröffentlichungsregionen können die Verfügbarkeit verbessern. Weitere Details finden Sie in der [Zusätzlichen Dokumentation zu Veröffentlichungsregionen](/help/operations/additional-publish-regions.md).

>[!TIP]
>
>Sie können die [Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/api-usage/creating-programs-and-environments/#creating-aem-cloud-service-environments) verwenden, um eine aktuelle Liste der verfügbaren Regionen abzurufen.

### Hinzufügen mehrerer Veröffentlichungsregionen zu einer neuen Umgebung {#add-regions}

Wenn Sie eine Umgebung hinzufügen, können Sie zusätzlich zur primären Region weitere Regionen konfigurieren.

1. Wählen Sie die **primäre Region**.
   * Die primäre Region kann nach der Erstellung der Umgebung nicht mehr geändert werden.
1. Wenn Sie die Option **Zusätzliche Veröffentlichungsregionen hinzufügen** wählen, wird eine neue Dropdown-Option **Zusätzliche Veröffentlichungsregionen** angezeigt.
1. Wählen Sie in der Dropdown-Liste **Zusätzliche Veröffentlichungsregionen** eine zusätzliche Region aus.
1. Die ausgewählte Region wird unter der Dropdown-Liste hinzugefügt, um ihre Auswahl anzugeben.
   * Wählen Sie die `X` neben dem ausgewählten Bereich, damit Sie die Auswahl aufheben können.
1. Wählen Sie eine andere Region aus der Dropdown-Liste **Zusätzliche Veröffentlichungsregionen**, um eine weitere Region hinzuzufügen.
1. Auswählen **Speichern** wenn Sie bereit sind, Ihre Umgebung zu erstellen.

![Auswählen mehrerer Regionen](assets/select-multiple-regions.png)

Die ausgewählten Regionen gelten sowohl für Produktions- als auch für Staging-Umgebungen.

Wenn Sie keine zusätzlichen Regionen angeben, [können Sie dies später tun, nachdem die Umgebungen erstellt wurden.](#edit-regions)

Wenn Sie [erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) für das Programm bereitstellen möchten, wird empfohlen, diese Bereitstellung vor dem Hinzufügen zusätzlicher Veröffentlichungsregionen zu den Umgebungen mithilfe der Cloud Manager-API durchzuführen. Andernfalls wird der Traffic der zusätzlichen Veröffentlichungsregionen über den Proxy der primären Region geleitet.

### Bearbeiten mehrerer Veröffentlichungsregionen {#edit-regions}

Wenn Sie anfangs keine weiteren Regionen angegeben haben, können Sie dies auch nach der Erstellung der Umgebungen tun, sofern Sie über die erforderlichen Berechtigungen verfügen.

Sie können auch zusätzliche Veröffentlichungsregionen entfernen. Sie können jedoch in einer Transaktion Regionen nur entweder hinzufügen oder entfernen. Wenn Sie eine Region hinzufügen und eine andere Region entfernen müssen, fügen Sie zuerst eine hinzu, speichern Ihre Änderung und entfernen dann die andere (oder umgekehrt).

1. Klicken Sie in der Programmübersichtskonsole Ihres Programms auf die Schaltfläche mit den Auslassungspunkten für Ihre Produktionsumgebung und wählen Sie im Menü **Bearbeiten**.

   ![Umgebung bearbeiten](assets/select-edit-environment.png)

1. Nehmen Sie im Dialog **Produktionsumgebung bearbeiten** die erforderlichen Änderungen an den zusätzlichen Veröffentlichungsregionen vor.
   * Verwenden Sie die Dropdown-Liste **Zusätzliche Veröffentlichungsregionen**, um weitere Regionen auszuwählen.
   * Klicken Sie auf das X neben den ausgewählten zusätzlichen Veröffentlichungsregionen, um deren Auswahl aufzuheben.

   ![Umgebung bearbeiten](assets/edit-environment.png)

1. Auswählen **Speichern** , um die Änderungen zu speichern.

Änderungen an der Produktionsumgebung gelten sowohl für die Produktions- als auch für die Staging-Umgebung. Änderungen an mehreren Veröffentlichungsregionen können nur in der Produktionsumgebung bearbeitet werden.

Wenn Sie [erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) für das Programm bereitstellen möchten, wird empfohlen, diese Bereitstellung vor dem Hinzufügen zusätzlicher Veröffentlichungsregionen zu den Umgebungen durchzuführen. Andernfalls wird der Traffic der zusätzlichen Veröffentlichungsregionen über den Proxy der primären Region geleitet.

## Umgebungsdetails {#viewing-environment}

Sie können die Karte **Umgebungen** auf der Übersichtsseite auf zwei Arten verwenden, um auf Details zu Umgebungen zuzugreifen.

1. Klicken Sie auf der Seite **Überblick** auf die Registerkarte **Umgebungen** oben auf dem Bildschirm.

   ![Registerkarte „Umgebungen“](assets/environments-tab2.png)

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
>Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken Sie auf **Alle anzeigen** wie zuvor beschrieben, um alle Umgebungen des Programms zu sehen.

### Zugriff auf den Vorschau-Service {#access-preview-service}

Cloud Manager bietet für jede AEM as a Cloud Service-Umgebung einen Vorschau-Service (bereitgestellt als zusätzlicher Publishing-Service).

Mithilfe des Service können Sie eine Vorschau des endgültigen Erlebnisses einer Website anzeigen, bevor diese die tatsächliche Publishing-Umgebung erreicht und öffentlich verfügbar wird.

Bei der Erstellung wird auf den Vorschau-Service eine standardmäßige IP-Zulassungsliste mit der Bezeichnung `Preview Default [<envId>]` angewendet, wodurch der gesamte Traffic zum Vorschau-Service blockiert wird. Heben Sie die Anwendung der standardmäßigen IP-Zulassungsliste im Vorschau-Service auf, damit Sie den Zugriff aktivieren können.

![Vorschau-Service und seine Zulassungsliste](assets/preview-ip-allow.png)

Benutzende mit den erforderlichen Berechtigungen müssen die folgenden Schritte ausführen, bevor sie die Vorschau-Service-URL freigeben können, damit der Zugriff darauf möglich ist.

1. Erstellen Sie eine entsprechende IP-Zulassungsliste, wenden Sie sie auf den Vorschau-Service an und heben Sie sofort die Anwendung der `Preview Default [<envId>]`-Zulassungsliste wieder auf.

   * Siehe [Anwenden und Aufheben der Anwendung von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) für weitere Details.

1. Verwenden Sie den Workflow zum Aktualisieren von **IP-Zulassungslisten**, um die standardmäßige IP-Adresse zu entfernen und nach Bedarf IP-Adressen hinzuzufügen. Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md).

Nachdem der Zugriff auf den Vorschau-Service entsperrt wurde, erscheint das Sperrsymbol nicht mehr vor dem Namen des Vorschau-Services.

Nach der Aktivierung können Sie Inhalte im Vorschau-Service veröffentlichen, indem Sie die Benutzeroberfläche zur Verwaltung von Veröffentlichungen in AEM verwenden. Siehe [Vorschau von Inhalten](/help/sites-cloud/authoring/fundamentals/previewing-content.md) für weitere Informationen.

>[!NOTE]
>
>Ihre Umgebung muss auf AEM Version `2021.05.5368.20210529T101701Z` oder höher ausgeführt werden, um den Vorschau-Service nutzen zu können. Vergewissern Sie sich, dass in Ihrer Umgebung eine Aktualisierungs-Pipeline erfolgreich ausgeführt wurde, damit Sie den Vorschau-Service verwenden können.

### Status weiterer Veröffentlichungsregionen {#additional-region-status}

Wenn Sie zusätzliche Veröffentlichungsregionen aktiviert haben, können Sie den Status dieser Regionen über die **Umgebungen** Karte.

1. Im **Übersicht** Seite, suchen Sie die **Umgebungen** Karte.

1. Im **Umgebungen** -Karte, **Status** gibt an, ob es Probleme mit den konfigurierten zusätzlichen Veröffentlichungsregionen gibt. Klicken Sie auf **Info** für Details zu den Regionen.

   ![Zusätzliche Statusinformationen zu Veröffentlichungsregionen auf der Karte Umgebungen](assets/additional-publish-region-status-environments-card.png)

Alternativ können Sie über die **Umgebungen** Registerkarte.

1. Im **Übersicht** Seite, wählen Sie die **Umgebungen** Registerkarte.

1. Im **Umgebungen** wählen Sie im linken Navigationsbereich die Umgebung aus, die Sie abfragen möchten.

1. Sobald eine Umgebung ausgewählt ist:

   * Die **Umgebungsinformationen** zeigt an, welche Regionen für die ausgewählte Umgebung konfiguriert sind.
   * Die **Status** Spalte **Umgebungssegmente** gibt an, ob es Probleme mit den konfigurierten zusätzlichen Veröffentlichungsregionen gibt. Bewegen Sie den Mauszeiger über den Status, um Details zu Problemen zu erhalten.

   ![Zusätzliche Statusinformationen zu Veröffentlichungsregionen auf der Registerkarte Umgebungen](assets/additional-publish-region-status-environments-tab.png)

Wenn Probleme mit zusätzlichen Veröffentlichungsregionen gemeldet werden:

1. Sei geduldig! Cloud Manager versucht kontinuierlich, die Region wiederherzustellen, und kann jederzeit verfügbar sein.
1. Wenn das Problem nach mehreren Stunden besteht, können Sie den zusätzlichen Veröffentlichungsbereich entfernen und ihn (entweder dieselbe Region oder eine andere Region) erneut hinzufügen, um eine vollständige Bereitstellung Trigger.

Wie lange Sie darauf warten, dass sich das System von selbst erholt, bevor Sie zusätzliche Maßnahmen ergreifen, hängt von den Auswirkungen ab, die der Ausfall dieser Region auf Ihre Systeme hat.

In jedem Fall [Traffic wird immer in die nächstgelegene Region weitergeleitet, die online ist.](/help/operations/additional-publish-regions.md) Wenn weiterhin Probleme auftreten, wenden Sie sich an die Adobe-Kundenunterstützung.

## Aktualisieren von Umgebungen {#updating-dev-environment}

Als Cloud-nativer Service verwaltet Adobe automatisch die Aktualisierungen Ihrer Staging- und Produktionsumgebungen innerhalb der Produktionsprogramme.

Aktualisierungen von Entwicklungsumgebungen sowie Umgebungen in Sandbox-Programmen werden jedoch innerhalb der Programme verwaltet. Wenn in einer solchen Umgebung nicht die neueste öffentlich verfügbare AEM-Version ausgeführt wird, zeigt der Status auf der Karte **Umgebungen** auf dem Bildschirm **Überblick** des Programms **Aktualisierung verfügbar** an.

![Aktualisierungsstatus der Umgebung](assets/environ-update.png)

### Updates und Pipelines {#updates-pipelines}

Pipelines sind der einzige Weg, [Code in den Umgebungen von AEM as a Cloud Service bereitzustellen.](deploy-code.md) Aus diesem Grund ist jede Pipeline mit einer bestimmten AEM-Version verknüpft.

Wenn Cloud Manager erkennt, dass eine neuere Version von AEM verfügbar ist als die, die zuletzt mit der Pipeline bereitgestellt wurde, wird der Status **Aktualisierung verfügbar** für die Umgebung angezeigt.

Der Prozess der Aktualisierung erfolgt also in zwei Schritten:

1. Aktualisieren der Pipeline mit der neuesten AEM-Version
1. Ausführen der Pipeline zum Bereitstellen der neuen Version von AEM in einer Umgebung

### Aktualisieren von Umgebungen {#updating-your-environments}

Die Option **Aktualisieren** ist für Entwicklungsumgebungen und Umgebungen in Sandbox-Programmen über die Karte **Umgebungen** durch Klicken auf die Schaltfläche mit den Auslassungspunkten für die Umgebung verfügbar.

![Option „Aktualisieren“ auf der Karte „Umgebungen“](assets/environ-update2.png)

Diese Option ist auch verfügbar, indem Sie auf die Registerkarte **Umgebungen** klicken und anschließend auf die Schaltfläche mit den Auslassungspunkten für die Umgebung.

![Update-Option auf der Registerkarte „Umgebungen“](assets/environ-update3.png)

Ein Benutzer mit der **Bereitstellungsmanager** oder **Business Owner** Rolle kann diese Option verwenden, um die mit dieser Umgebung verknüpfte Pipeline auf die neueste AEM zu aktualisieren.

Nachdem die Pipeline-Version auf die neueste öffentlich verfügbare AEM-Version aktualisiert wurde, wird der Benutzer aufgefordert, die zugehörige Pipeline auszuführen, um die neueste Version in der Umgebung bereitzustellen.

![Aufforderung zur Ausführung der Pipeline zur Aktualisierung der Umgebung](assets/update-run-pipeline.png)

Das Verhalten der Option **Aktualisieren** hängt von der Konfiguration und dem aktuellen Status des Programms ab.

* Wenn die Pipeline bereits aktualisiert wurde, fordert die Option **Aktualisieren** den Benutzer auf, die Pipeline auszuführen.
* Wenn die Pipeline gerade aktualisiert wird, informiert die Option **Aktualisieren** den Benutzer darüber, dass bereits eine Aktualisierung ausgeführt wird.
* Wenn keine geeignete Pipeline existiert, fordert die Option **Aktualisieren** den Benutzer auf, eine zu erstellen.

## Löschen von Entwicklungsumgebungen {#deleting-environment}

Ein Benutzer mit der **Bereitstellungsmanager** oder **Business Owner** Rolle kann eine Entwicklungsumgebung löschen.

Klicken Sie im Bildschirm **Überblick** des Programms auf der Karte **Umgebungen** auf die Schaltfläche mit den Auslassungspunkten für die Entwicklungsumgebung, die Sie löschen möchten.

![Die Löschoption](assets/environ-delete.png)

Die Löschoption ist auch über die Registerkarte **Umgebungen** des Fensters **Überblick** des Programms verfügbar. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten für die Umgebung und anschließend auf **Löschen**.

![Die Löschoption auf der Registerkarte „Umgebungen“](assets/environ-delete2.png)

>[!NOTE]
>
>* In einem Produktionsprogramm erstellte Produktions- und Staging-Umgebungen können nicht gelöscht werden.
>* Produktions- und Staging-Umgebungen in einem Sandbox-Programm können gelöscht werden.

## Zugriffsverwaltung {#managing-access}

Wählen Sie aus dem Menü mit den Auslassungspunkten der Umgebung auf der Karte **Umgebungen** die Option **Zugriff verwalten** aus. Sie können direkt zur Autoreninstanz gehen und den Zugriff für Ihre Umgebung verwalten.

![Verwalten der Zugriffsoption](assets/environ-access.png)

>[!TIP]
>
>Siehe [Team- und Produktprofile in AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md), wenn Sie erfahren möchten, wie Sie mit Team- und Produktprofilen in AEM as a Cloud Service den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren oder einschränken können. 

## Zugriff auf die Entwicklerkonsole {#accessing-developer-console}

Wählen Sie aus dem Menü mit den Auslassungspunkten der Umgebung auf der Karte **Umgebungen** die Option **Entwicklerkonsole** aus. In Ihrem Browser wird eine neue Registerkarte mit der Anmeldeseite zur **Developer Console** geöffnet.

![Anmelden bei der Developer Console](assets/environ-devconsole.png)

Nur eine Benutzerin bzw. ein Benutzer mit der Rolle **Entwickler** hat Zugriff auf die **Developer Console**. Für Sandbox-Programme hat jedoch jede Person mit Zugriff auf das Sandbox-Programm auch Zugriff auf die **Developer Console**.

Weitere Details finden Sie unter [Aktivieren und Deaktivieren des Ruhezustands von Sandbox-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/introduction-sandbox-programs.html?lang=de#hibernation).

Diese Option ist auch über die Registerkarte **Umgebung** des Fensters **Überblick** beim Klicken auf das Menü mit den Auslassungspunkten einer einzelnen Umgebung verfügbar.

## Lokale Anmeldung {#login-locally}

Auswählen **Lokale Anmeldung** aus dem Suchmenü der Umgebung im **Umgebungen** -Karte, um sich lokal bei Adobe Experience Manager anzumelden.

![Lokale Anmeldung](assets/environ-login-locally.png)

Darüber hinaus können Sie sich auch über die Registerkarte **Umgebungen** der Seite **Überblick** lokal anmelden.

![Lokale Anmeldung über die Registerkarte Umgebungen](assets/environ-login-locally-2.png)

## Verwalten von benutzerdefinierten Domain-Namen {#manage-cdn}

Benutzerdefinierte Domain-Namen werden in Cloud Manager for Sites-Programmen sowohl für Veröffentlichungs- als auch für Vorschau-Services unterstützt. Jede Cloud Manager-Umgebung kann bis zu 250 benutzerdefinierte Domains hosten.

Um benutzerdefinierte Domain-Namen zu konfigurieren, gehen Sie zur Registerkarte **Umgebungen** und klicken Sie auf eine Umgebung, um die Details der Umgebung anzuzeigen.

Benutzerinnen oder Benutzer müssen über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzuzufügen.

![Umgebungsdetails](assets/domain-names.png)

Die folgenden Aktionen können für Ihre Umgebung im Veröffentlichungs-Service ausgeführt werden.

* [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

* [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)

* [Überprüfen des Status des benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) oder eines [SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn).

* [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn)


## Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

IP-Zulassungslisten werden in Cloud Manager für Author-, Publish- und Vorschau-Services für Sites-Programme unterstützt.

Um IP-Zulassungslisten zu verwalten, gehen Sie zur Registerkarte **Umgebungen** der Seite **Überblick** Ihres Programms. Klicken Sie auf eine einzelne Umgebung, damit Sie deren Details verwalten können.

### Anwenden einer IP-Zulassungsliste {#apply-ip-allow-list}

Beim Anwenden einer IP-Zulassungsliste werden alle in der Definition der Zulassungsliste enthaltenen IP-Adressen-Bereiche mit einem Author- oder Publish-Service in einer Umgebung verknüpft. Um eine IP-Zulassungsliste anwenden zu können, muss die betreffende Person die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** innehaben und angemeldet sein.

Die IP-Zulassungsliste muss in Cloud Manager vorhanden sein, damit sie auf eine Umgebung angewendet werden kann. Weitere Informationen zu IP-Zulassungslisten in Cloud Manager finden Sie in der [Einführung in IP-Zulassungslisten in Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

**So wenden Sie eine IP-Zulassungsliste an:**

1. Navigieren Sie von der Registerkarte **Umgebungen** des Bildschirms **Überblick** des Programms zu der gewünschten Umgebung und dann zur Tabelle **IP-Zulassungslisten**.
1. Verwenden Sie die Eingabefelder oben in der Tabelle der IP-Zulassungslisten-Zulassungsliste, damit Sie die IP- und den Autoren- oder Veröffentlichungsdienst auswählen können, auf den Sie sie anwenden möchten.
1. Klicken Sie auf **Anwenden** und bestätigen Sie Ihre Übermittlung.

### Aufheben der Anwendung einer IP-Zulassungsliste {#unapply-ip-allow-list}

Durch das Aufheben der Anwendung einer IP-Zulassungsliste werden alle in der Definition der Zulassungsliste enthaltenen IP-Adressbereiche von einem Author- oder Publish-Service in einer Umgebung getrennt. Eine Person mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** muss angemeldet sein, um die Anwendung einer IP-Zulassungsliste aufheben zu können.

**So heben Sie die Anwendung einer IP-Zulassungsliste auf:**

1. Navigieren Sie von der Registerkarte **Umgebungen** des Bildschirms **Überblick** des Programms zu der gewünschten Umgebung und dann zur Tabelle **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile, in der die Regel der IP-Zulassungsliste aufgeführt ist, deren Anwendung Sie aufheben möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten am Ende der Zeile.
1. Wählen Sie **Anwendung rückgängig machen** aus und bestätigen Sie Ihre Übermittlung.
