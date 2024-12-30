---
title: Verwalten von Umgebungen
description: Erfahren Sie mehr über die Arten von Umgebungen, die Sie erstellen können, und wie Sie sie für ein Cloud Manager-Projekt erstellen.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '2357'
ht-degree: 100%

---


# Verwalten von Umgebungen {#managing-environments}

Erfahren Sie mehr über die Arten von Umgebungen, die Sie erstellen können, und wie Sie sie für ein Cloud Manager-Projekt erstellen.

## Umgebungstypen {#environment-types}

Benutzende mit den erforderlichen Berechtigungen können die folgenden Umgebungstypen erstellen (im Rahmen der dem jeweiligen Mandanten zur Verfügung stehenden Möglichkeiten):

* **Produktion + Staging**: Die Produktions- und Staging-Umgebungen sind gemeinsam verfügbar und werden für Produktions- bzw. Testzwecke verwendet. Führen Sie Leistungs- und Sicherheitstests in der Staging-Umgebung durch. Sie hat dieselbe Größe wie die Produktion.

* **Entwicklung**: Die Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken erstellt werden und wird ausschließlich produktionsfremden Pipelines zugeordnet.  Entwicklungsumgebungen haben nicht dieselbe Größe wie Staging- und Produktionsumgebungen und sollten nicht für Leistungs- und Sicherheitstests verwendet werden.

* **Schnelle Entwicklung**: Eine schnelle Entwicklungsumgebung (RDE) ermöglicht es Entwicklungspersonen, Änderungen schnell bereitzustellen und zu überprüfen, wodurch der Zeitaufwand für das Testen von Funktionen, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren, minimiert wird. Details zur Verwendung einer RDE finden Sie in der [Dokumentation zur schnellen Entwicklungsumgebung](/help/implementing/developing/introduction/rapid-development-environments.md).

Die Fähigkeiten der einzelnen Umgebungen hängen von den Lösungen ab, die im [Programm](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) der Umgebung ermöglicht werden.

* [Sites](/help/overview/introduction.md)
* [Assets](/help/assets/overview.md)
* [Formulare](/help/forms/home.md)
* [Screens](/help/screens-cloud/introduction/introduction.md)

>[!NOTE]
>
>Die Produktions- und Staging-Umgebung werden nur als Paar erstellt. Sie können nicht nur eine Staging- oder nur eine Produktionsumgebung erstellen.

## Hinzufügen einer Umgebung {#adding-environments}

Um eine Umgebung hinzufügen oder bearbeiten zu können, muss eine Benutzerin oder ein Benutzer Mitglied der Rolle **Geschäftsinhaber** sein.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf das Programm, für das eine Umgebung hinzugefügt werden soll.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf der Karte **Umgebungen** auf **Umgebung hinzufügen**, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch über das Symbol ![Daten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) auf der Registerkarte **Umgebungen** verfügbar.

     ![Registerkarte Umgebungen](assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen**:

   * Wählen Sie einen [**Umgebungstyp**](#environment-types).
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Namen des Umgebungstyps angezeigt.
   * Geben Sie einen **Namen** für die Umgebung an.
      * Der Umgebungsname kann nach der Erstellung der Umgebung nicht mehr geändert werden.
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
   * Wählen Sie das `X` neben der ausgewählten Region aus, um sie wieder abzuwählen.
1. Wählen Sie eine andere Region aus der Dropdown-Liste **Zusätzliche Veröffentlichungsregionen**, um eine weitere Region hinzuzufügen.
1. Wählen Sie **Speichern** aus, wenn Sie bereit sind, Ihre Umgebung zu erstellen.

![Auswählen mehrerer Regionen](assets/select-multiple-regions.png)

Die ausgewählten Regionen gelten sowohl für Produktions- als auch für Staging-Umgebungen.

Wenn Sie keine zusätzlichen Regionen angeben, [können Sie dies auch später tun, nachdem die Umgebungen erstellt wurden](#edit-regions).

Wenn Sie [erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) für das Programm bereitstellen möchten, wird empfohlen, diese Bereitstellung vor dem Hinzufügen zusätzlicher Veröffentlichungsregionen zu den Umgebungen mithilfe der Cloud Manager-API durchzuführen. Andernfalls wird der Traffic der zusätzlichen Veröffentlichungsregionen über den Proxy der primären Region geleitet.

### Bearbeiten mehrerer Veröffentlichungsregionen {#edit-regions}

Wenn Sie anfangs keine weiteren Regionen angegeben haben, können Sie dies auch nach der Erstellung der Umgebungen tun, sofern Sie über die erforderlichen Berechtigungen verfügen.

Sie können auch zusätzliche Veröffentlichungsregionen entfernen. Sie können jedoch in einer Transaktion Regionen nur entweder hinzufügen oder entfernen. Wenn Sie eine Region hinzufügen und eine andere Region entfernen müssen, fügen Sie zuerst eine hinzu, speichern Ihre Änderung und entfernen dann die andere (oder umgekehrt).

1. Klicken Sie in der Konsole „Programmübersicht“ Ihres Programms auf https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg für Ihre Produktionsumgebung und wählen Sie im Menü die Option **Bearbeiten** aus.

   ![Umgebung bearbeiten](assets/select-edit-environment.png)

1. Nehmen Sie im Dialog **Produktionsumgebung bearbeiten** die erforderlichen Änderungen an den zusätzlichen Veröffentlichungsregionen vor.
   * Verwenden Sie die Dropdown-Liste **Zusätzliche Veröffentlichungsregionen**, um weitere Regionen auszuwählen.
   * Klicken Sie auf das X neben den ausgewählten zusätzlichen Veröffentlichungsregionen, um deren Auswahl aufzuheben.

   ![Umgebung bearbeiten](assets/edit-environment.png)

1. Wählen Sie **Speichern** aus, um die Änderungen zu speichern.

Änderungen an der Produktionsumgebung gelten sowohl für die Produktions- als auch für die Staging-Umgebung. Änderungen an mehreren Veröffentlichungsregionen können nur in der Produktionsumgebung bearbeitet werden.

Wenn Sie [erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) für das Programm bereitstellen möchten, wird empfohlen, diese Bereitstellung vor dem Hinzufügen zusätzlicher Veröffentlichungsregionen zu den Umgebungen durchzuführen. Andernfalls wird der Traffic der zusätzlichen Veröffentlichungsregionen über den Proxy der primären Region geleitet.

## Umgebungsdetails {#viewing-environment}

Auf der Seite **Übersicht** haben Sie zwei Möglichkeiten, um auf die Details zu einer Umgebung zuzugreifen.

1. Klicken Sie auf der Seite **Überblick** im linken Seitenmenü auf die Registerkarte **Umgebungen**.

   ![Registerkarte „Umgebungen“](assets/environments-tab2.png)

   * Alternativ können Sie auf die Schaltfläche **Alle anzeigen** auf der Karte **Umgebungen** klicken, um direkt zur Registerkarte **Umgebungen** zu gelangen.

     ![Option „Alle anzeigen“](assets/environment-showall.png)

1. **Umgebungen** öffnet und listet alle Umgebungen für das Programm auf.

   ![Registerkarte „Umgebungen“](assets/environments-tab2.png)

1. Klicken Sie auf eine Umgebung in der Liste, um deren Details anzuzeigen.

   ![Umgebungsdetails](assets/environ-preview1.png)

Klicken Sie alternativ auf https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg für die gewünschte Umgebung und wählen Sie anschließend **Details anzeigen** aus.

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

Nach der Aktivierung können Sie Inhalte im Vorschau-Service veröffentlichen, indem Sie die Benutzeroberfläche zur Verwaltung von Veröffentlichungen in AEM verwenden. Siehe [Vorschau von Inhalten](/help/sites-cloud/authoring/sites-console/previewing-content.md) für weitere Informationen.

>[!NOTE]
>
>Ihre Umgebung muss auf AEM Version `2021.05.5368.20210529T101701Z` oder höher ausgeführt werden, um den Vorschau-Service nutzen zu können. Vergewissern Sie sich, dass in Ihrer Umgebung eine Aktualisierungs-Pipeline erfolgreich ausgeführt wurde, damit Sie den Vorschau-Service verwenden können.

### Status zusätzlicher Veröffentlichungsregionen {#additional-region-status}

Wenn Sie zusätzliche Veröffentlichungsregionen aktiviert haben, können Sie den Status dieser Regionen über die Karte **Umgebungen** überprüfen.

1. Suchen Sie auf der Seite **Übersicht** die Karte **Umgebungen**.

1. Auf der Karte **Umgebungen** gibt die Spalte **Status** an, ob es Probleme mit den konfigurierten zusätzlichen Veröffentlichungsregionen gibt. Klicken Sie auf das Symbol **Info**, um Details zu den Regionen zu erhalten.

   ![Status von zusätzlichen Veröffentlichungsregionen auf der Karte „Umgebungen“](assets/additional-publish-region-status-environments-card.png)

Alternativ können Sie auf die gleichen Informationen über die Registerkarte **Umgebungen** zugreifen.

1. Wählen Sie auf der Seite **Übersicht** die Registerkarte **Umgebungen** aus.

1. Wählen Sie auf der Registerkarte **Umgebungen** im linken Seitenmenü die Umgebung aus, die abgefragt werden soll.

1. Wenn eine Umgebung ausgewählt ist:

   * Die Tabelle **Umgebungsinformationen** zeigt an, welche Regionen für die ausgewählte Umgebung konfiguriert sind.
   * Die Spalte **Status** der Tabelle **Umgebungssegmente** gibt an, ob es Probleme mit den konfigurierten zusätzlichen Veröffentlichungsregionen gibt. Bewegen Sie den Mauszeiger über den Status, um Details zu Problemen zu erhalten.

   ![Status von zusätzliche Veröffentlichungsregionen auf der Registerkarte „Umgebungen“](assets/additional-publish-region-status-environments-tab.png)

Wenn Probleme mit zusätzlichen Veröffentlichungsregionen gemeldet werden:

1. Haben Sie Geduld. Cloud Manager versucht kontinuierlich, die Region wiederherzustellen, und sie kann jederzeit wieder verfügbar werden.
1. Wenn das Problem nach mehreren Stunden weiterhin besteht, können Sie den zusätzlichen Veröffentlichungsbereich entfernen und ihn erneut hinzufügen (entweder dieselbe Region oder eine andere Region), um eine vollständige Bereitstellung auszulösen.

Wie lange Sie darauf warten sollten, dass sich das System von selbst erholt, bevor Sie zusätzliche Maßnahmen ergreifen, hängt von den Auswirkungen ab, die der Ausfall dieser Region auf Ihre Systeme hat.

In jedem Fall wird [Traffic immer in die nächstgelegene Region weitergeleitet, die online ist](/help/operations/additional-publish-regions.md). Wenn weiterhin Probleme auftreten, wenden Sie sich an die Adobe-Kundenunterstützung.

## Aktualisieren von Umgebungen {#updating-dev-environment}

Als Cloud-nativer Service verwaltet Adobe automatisch die Aktualisierungen Ihrer Entwicklungs-, Staging- und Produktionsumgebungen innerhalb der Produktionsprogramme.

Aktualisierungen von Umgebungen in Sandbox-Programmen werden jedoch innerhalb der Programme verwaltet. Wenn in einer solchen Umgebung nicht die neueste öffentlich verfügbare AEM-Version ausgeführt wird, zeigt der Status auf der Karte **Umgebungen** auf dem Bildschirm **Überblick** des Programms **Aktualisierung verfügbar** an.

![Aktualisierungsstatus der Umgebung](assets/environ-update.png)

### Updates und Pipelines {#updates-pipelines}

Pipelines sind der einzige Weg, [Code in den Umgebungen von AEM as a Cloud Service bereitzustellen](deploy-code.md). Aus diesem Grund ist jede Pipeline mit einer bestimmten AEM-Version verknüpft.

Wenn Cloud Manager erkennt, dass eine neuere Version von AEM verfügbar ist als die, die zuletzt mit der Pipeline bereitgestellt wurde, wird der Status **Aktualisierung verfügbar** für die Umgebung angezeigt.

Der Prozess der Aktualisierung erfolgt also in zwei Schritten:

1. Aktualisieren der Pipeline mit der neuesten AEM-Version
1. Ausführen der Pipeline zum Bereitstellen der neuen Version von AEM in einer Umgebung

### Aktualisieren von Umgebungen {#updating-your-environments}

>[!NOTE]
> Seit 2024 werden Entwicklungsinstanzen und einige Sandbox-Programme bereits automatisch aktualisiert, sodass Aktualisierungen für sie nicht manuell verwaltet werden müssen. Aufgrund dieses Übergangs ist die Option zur manuellen Aktualisierung der Umgebung für Entwicklungsinstanzen möglicherweise für _einige_ Ihrer Programme nicht verfügbar.

Die Option **Aktualisieren** ist für einige Entwicklungsumgebungen und Umgebungen in Sandbox-Programmen über die Karte **Umgebungen** durch Klicken auf https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg für die Umgebung verfügbar.

![Option zum Aktualisieren auf der Karte „Umgebungen“](assets/environ-update2.png)

Diese Option ist auch verfügbar, indem Sie auf die Registerkarte **Umgebungen** des Programms und anschließend auf https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg für die Umgebung klicken.

![Update-Option auf der Registerkarte „Umgebungen“](assets/environ-update3.png)

Eine Benutzerin bzw. ein Benutzer mit der Rolle **Bereitstellungs-Manager** oder **Geschäftsinhaber** kann diese Option verwenden, um die mit dieser Umgebung verknüpfte Pipeline auf die neueste AEM-Version zu aktualisieren.

Nachdem die Pipeline-Version auf die neueste öffentlich verfügbare AEM-Version aktualisiert wurde, wird der Benutzer aufgefordert, die zugehörige Pipeline auszuführen, um die neueste Version in der Umgebung bereitzustellen.

![Aufforderung zur Ausführung der Pipeline zur Aktualisierung der Umgebung](assets/update-run-pipeline.png)

Das Verhalten der Option **Aktualisieren** hängt von der Konfiguration und dem aktuellen Status des Programms ab.

* Wenn die Pipeline bereits aktualisiert wurde, fordert die Option **Aktualisieren** den Benutzer auf, die Pipeline auszuführen.
* Wenn die Pipeline gerade aktualisiert wird, informiert die Option **Aktualisieren** den Benutzer darüber, dass bereits eine Aktualisierung ausgeführt wird.
* Wenn keine geeignete Pipeline existiert, fordert die Option **Aktualisieren** die Benutzenden auf, eine zu erstellen.

## Löschen von Entwicklungsumgebungen {#deleting-environment}

Eine Benutzerin bzw. ein Benutzer mit der Rolle **Bereitstellungs-Manager** oder **Geschäftsinhaber** kann eine Entwicklungsumgebung löschen.

Klicken Sie im Bildschirm **Überblick** des Programms auf der Karte **Umgebungen** auf https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg für die Entwicklungsumgebung, die gelöscht werden soll.

![Die Löschoption](assets/environ-delete.png)

Die Löschoption ist auch über die Registerkarte **Umgebungen** des Fensters **Überblick** des Programms verfügbar. Klicken Sie auf https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg für die Umgebung und wählen Sie anschließend **Löschen** aus.

![Die Löschoption auf der Registerkarte „Umgebungen“](assets/environ-delete2.png)

>[!NOTE]
>
>* In einem Produktionsprogramm erstellte Produktions- und Staging-Umgebungen können nicht gelöscht werden.
>* Produktions- und Staging-Umgebungen in einem Sandbox-Programm können gelöscht werden.

## Verwalten des Zugriffs {#managing-access}

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

Wählen Sie **Lokale Anmeldung** aus dem Menü mit den Auslassungspunkten auf der Karte **Umgebungen** aus, um sich lokal bei Adobe Experience Manager anzumelden.

![Lokale Anmeldung](assets/environ-login-locally.png)

Darüber hinaus können Sie sich auch über die Registerkarte **Umgebungen** der Seite **Überblick** lokal anmelden.

![Lokale Anmeldung über die Registerkarte „Umgebungen“](assets/environ-login-locally-2.png)

## Verwalten von benutzerdefinierten Domain-Namen {#manage-cdn}

Benutzerdefinierte Domain-Namen werden in Programmen von Cloud Manager for Sites sowohl für Veröffentlichungs- als auch für Vorschau-Services unterstützt.

>[!TIP]
>
>Weitere Informationen finden Sie in der [Einführung in benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

## Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

IP-Zulassungslisten werden in Cloud Manager für Author-, Publish- und Vorschau-Services für Sites-Programme unterstützt.

Um IP-Zulassungslisten zu verwalten, gehen Sie zur Registerkarte **Umgebungen** der Seite **Überblick** Ihres Programms. Klicken Sie auf eine einzelne Umgebung, damit Sie deren Details verwalten können.

### Übernehmen einer IP-Zulassungsliste {#apply-ip-allow-list}

Beim Anwenden einer IP-Zulassungsliste werden alle in der Definition der Zulassungsliste enthaltenen IP-Bereiche mit einem Autoren- oder Veröffentlichungs-Service in einer Umgebung verknüpft.

>[!TIP]
>
>Weitere Informationen finden Sie in der [Einführung in IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).
