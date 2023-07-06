---
title: Verwalten von Umgebungen
description: Erfahren Sie mehr über die Typen von Umgebungen, die Sie erstellen können, und wie Sie sie für Ihr Cloud Manager-Projekt erstellen.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2274'
ht-degree: 37%

---


# Verwalten von Umgebungen {#managing-environments}

Erfahren Sie mehr über die Typen von Umgebungen, die Sie erstellen können, und wie Sie sie für Ihr Cloud Manager-Projekt erstellen.

## Umgebungstypen {#environment-types}

Ein Benutzer mit den erforderlichen Berechtigungen kann die folgenden Umgebungstypen erstellen (im Rahmen der dem jeweiligen Mandanten zur Verfügung stehenden Möglichkeiten).

* **Produktion + Staging**: Die Produktions- und Staging-Umgebungen sind gemeinsam verfügbar und werden für Produktions- bzw. Testzwecke verwendet.

* **Entwicklung**: Die Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken erstellt werden und wird ausschließlich produktionsfremden Pipelines zugeordnet.

* **Schnelle Entwicklung** - Eine schnelle Entwicklungsumgebung (RDE) ermöglicht es einem Entwickler, Änderungen schnell bereitzustellen und zu überprüfen, wodurch der Zeitaufwand für das Testen von Funktionen minimiert wird, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren. Siehe [Dokumentation zur raschen Entwicklung](/help/implementing/developing/introduction/rapid-development-environments.md) für Details zur Verwendung eines RDE.

Die Fähigkeiten der einzelnen Umgebungen hängen von den Lösungen ab, die im [Programm](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) der Umgebung ermöglicht werden.

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

1. Aus dem **Programmübersicht** Seite, klicken Sie auf **Umgebung hinzufügen** auf **Umgebungen** -Karte, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

     ![Registerkarte Umgebungen](assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen** wird Folgendes angezeigt:

   * Wählen Sie einen [**Umgebungstyp**.](#environment-types)
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Namen des Umgebungstyps angezeigt.
   * Geben Sie einen **Namen** für die Umgebung an.
   * Geben Sie eine **Beschreibung** für die Umgebung an.
   * Wenn Sie eine **Produktion und Staging** -Umgebung müssen Sie einen Umgebungsnamen und eine Beschreibung für Ihre Produktions- und Staging-Umgebungen angeben.
   * Wählen Sie in der Dropdown-Liste eine **primäre Region** aus.
      * Der primäre Bereich kann nach der Erstellung nicht mehr geändert werden.
      * Je nach den verfügbaren Berechtigungen können Sie [mehrere Regionen](#multiple-regions).

   ![Dialogfeld „Umgebung hinzufügen“](assets/add-environment2.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Der Bildschirm **Überblick** zeigt nun in der Karte **Umgebungen** Ihre neue Umgebung an. Sie können jetzt Pipelines für Ihre neue Umgebung einrichten.

## Mehrere Veröffentlichungsregionen {#multiple-regions}

Ein Benutzer mit der **Business Owner** Rolle kann Produktions- und Staging-Umgebungen so konfigurieren, dass neben der primären Region bis zu drei weitere Veröffentlichungsregionen einbezogen werden. Zusätzliche Veröffentlichungsregionen können die Verfügbarkeit verbessern. Siehe [Zusätzliche Dokumentation zu Veröffentlichungsregionen](/help/operations/additional-publish-regions.md) für weitere Details.

>[!TIP]
>
>Sie können die [Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/api-usage/creating-programs-and-environments/#creating-aem-cloud-service-environments) , um eine aktuelle Liste der verfügbaren Regionen abzurufen.

### Hinzufügen mehrerer Veröffentlichungsbereiche zu einer neuen Umgebung {#add-regions}

Wenn Sie eine Umgebung hinzufügen, können Sie zusätzlich zur primären Region weitere Regionen konfigurieren.

1. Wählen Sie die **Primäre Region**.
   * Der primäre Bereich kann nach der Erstellung der Umgebung nicht mehr geändert werden.
1. Auswählen der Option **Zusätzliche Veröffentlichungsregionen hinzufügen** und eine neue **Zusätzliche Veröffentlichungsregionen** -Option angezeigt.
1. Im **Zusätzliche Veröffentlichungsregionen** in der Dropdown-Liste einen zusätzlichen Bereich auswählen.
1. Die ausgewählte Region wird unter der Dropdown-Liste hinzugefügt, um ihre Auswahl anzugeben.
   * Tippen oder klicken Sie auf `X` neben dem ausgewählten Bereich, damit Sie die Auswahl aufheben können.
1. Wählen Sie einen weiteren Bereich aus dem **Zusätzliche Veröffentlichungsregionen** Dropdown, um einen weiteren Bereich hinzuzufügen.
1. Tippen oder klicken Sie auf **Speichern** wenn Sie bereit sind, Ihre Umgebung zu erstellen.

![Auswählen mehrerer Regionen](assets/select-multiple-regions.png)

Die ausgewählten Regionen gelten sowohl für Produktions- als auch für Staging-Umgebungen.

Wenn Sie keine weiteren Regionen angeben, [Sie können dies später tun, nachdem die Umgebungen erstellt wurden.](#edit-regions)

Wenn Sie Bereitstellung [erweiterte Vernetzung](/help/security/configuring-advanced-networking.md) Für das Programm wird empfohlen, diese Bereitstellung vor dem Hinzufügen zusätzlicher Veröffentlichungsbereiche zu den Umgebungen mithilfe der Cloud Manager-API durchzuführen. Andernfalls durchläuft der Traffic der zusätzlichen Veröffentlichungsregionen den Proxy der primären Region.

### Bearbeiten mehrerer Veröffentlichungsbereiche {#edit-regions}

Wenn Sie anfangs keine weiteren Regionen angegeben haben, können Sie dies nach der Erstellung der Umgebungen tun, sofern Sie über die erforderlichen Berechtigungen verfügen.

Sie können auch zusätzliche Veröffentlichungsbereiche entfernen. Sie können jedoch nur Regionen in einer Transaktion hinzufügen oder entfernen. Wenn Sie eine Region hinzufügen und eine Region entfernen müssen, fügen Sie zuerst Ihre Änderung hinzu, speichern Sie sie und entfernen Sie sie dann (oder umgekehrt).

1. Klicken Sie in der Konsole Programmübersicht Ihres Programms auf die Suchschaltfläche für Ihre Produktionsumgebung und wählen Sie **Bearbeiten** aus dem Menü.

   ![Umgebung bearbeiten](assets/select-edit-environment.png)

1. Im **Bearbeiten der Produktionsumgebung** die erforderlichen Änderungen an den zusätzlichen Veröffentlichungsregionen vornehmen.
   * Verwenden Sie die **Zusätzliche Veröffentlichungsregionen** zur Auswahl zusätzlicher Regionen.
   * Klicken Sie auf das X neben den ausgewählten zusätzlichen Veröffentlichungsbereichen, um deren Auswahl aufzuheben.

   ![Umgebung bearbeiten](assets/edit-environment.png)

1. Tippen oder klicken Sie auf **Speichern**, um die Änderungen zu speichern.

Änderungen an der Produktionsumgebung gelten sowohl für die Produktions- als auch für die Staging-Umgebung. Änderungen an mehreren Veröffentlichungsbereichen können nur in der Produktionsumgebung bearbeitet werden.

Wenn Sie Bereitstellung [erweiterte Vernetzung](/help/security/configuring-advanced-networking.md) Für das Programm wird empfohlen, diese Bereitstellung durchzuführen, bevor den Umgebungen zusätzliche Veröffentlichungsbereiche hinzugefügt werden. Andernfalls durchläuft der Traffic der zusätzlichen Veröffentlichungsregionen den Proxy der primären Region.

## Umgebungsdetails {#viewing-environment}

Sie können die **Umgebungen** auf der Übersichtsseite, um auf die Details einer Umgebung auf zwei Arten zuzugreifen.

1. Aus dem **Übersicht** klicken Sie auf die **Umgebungen** oben im Bildschirm.

   ![Registerkarte „Umgebungen“](assets/environments-tab2.png)

   * Alternativ können Sie auf die **Alle anzeigen** Schaltfläche auf der **Umgebungen** -Karte, um direkt zum **Umgebungen** Registerkarte.

     ![Option „Alle anzeigen“](assets/environment-showall.png)

1. **Umgebungen** öffnet und listet alle Umgebungen für das Programm auf.

   ![Registerkarte „Umgebungen“](assets/environment-view-2.png)

1. Klicken Sie auf eine Umgebung in der Liste, um Details anzuzeigen.

   ![Umgebungsdetails](assets/environ-preview1.png)

Alternativ können Sie auf die Schaltfläche mit den Auslassungspunkten der gewünschten Umgebung klicken und anschließend auf **Details anzeigen**.

![Anzeigen von Umgebungsdetails](assets/view-environment-details.png)

>[!NOTE]
>
>Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken **Alle anzeigen** wie zuvor beschrieben, um alle Umgebungen des Programms zu sehen.

### Zugriff auf den Vorschau-Service {#access-preview-service}

Cloud Manager bietet für jede AEM as a Cloud Service Umgebung einen Vorschaudienst (bereitgestellt als zusätzlicher Veröffentlichungsdienst).

Mithilfe des Service können Sie eine Vorschau des endgültigen Erlebnisses einer Website anzeigen, bevor diese die tatsächliche Veröffentlichungsumgebung erreicht und öffentlich verfügbar wird.

Bei der Erstellung wird dem Vorschaudienst eine standardmäßige IP-Zulassungsliste vom Typ &quot;&quot;zugewiesen, die `Preview Default [<envId>]`, wodurch der gesamte Traffic an den Vorschaudienst blockiert wird. Heben Sie die Anwendung der standardmäßigen IP-Zulassungsliste im Vorschaudienst auf, damit Sie den Zugriff aktivieren können.

![Vorschau-Service und seine Zulassungsliste](assets/preview-ip-allow.png)

Benutzer mit den erforderlichen Berechtigungen müssen die folgenden Schritte ausführen, bevor sie die Vorschau-Dienst-URL freigeben, um den Zugriff darauf sicherzustellen.

1. Erstellen Sie eine entsprechende IP-Zulassungsliste, wenden Sie sie auf den Vorschaudienst an und heben Sie die Anwendung sofort auf. `Preview Default [<envId>]` Zulassungsliste.

   * Siehe [Anwenden und Aufheben der Anwendung von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) für weitere Details.

1. Verwenden Sie den Workflow zum Aktualisieren von **IP-Zulassungslisten**, um die standardmäßige IP-Adresse zu entfernen und nach Bedarf IP-Adressen hinzuzufügen. Siehe [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md) , um mehr zu erfahren.

Nachdem der Zugriff auf den Vorschaudienst entsperrt wurde, wird das Sperrsymbol vor dem Vorschaudienstnamen nicht mehr angezeigt.

Nach der Aktivierung können Sie Inhalte im Vorschau-Service veröffentlichen, indem Sie die Benutzeroberfläche zur Verwaltung von Veröffentlichungen in AEM verwenden. Siehe [Vorschau des Inhalts](/help/sites-cloud/authoring/fundamentals/previewing-content.md) für weitere Details.

>[!NOTE]
>
>Ihre Umgebung muss auf AEM Version `2021.05.5368.20210529T101701Z` oder höher ausgeführt werden, um den Vorschau-Service nutzen zu können. Vergewissern Sie sich, dass in Ihrer Umgebung eine Aktualisierungs-Pipeline erfolgreich ausgeführt wurde, damit Sie den Vorschaudienst verwenden können.

## Aktualisieren von Umgebungen {#updating-dev-environment}

Als Cloud-nativer Service verwaltet Adobe automatisch die Aktualisierungen Ihrer Staging- und Produktionsumgebungen innerhalb der Produktionsprogramme.

Aktualisierungen der Entwicklungsumgebungen und der Umgebungen in Sandbox-Programmen werden jedoch innerhalb der Programme verwaltet. Wenn in einer solchen Umgebung nicht die neueste öffentlich verfügbare AEM ausgeführt wird, wird der Status auf der **Umgebungen** auf der Karte **Übersicht** Programmbildschirm **Verfügbare Aktualisierung**.

![Aktualisierungsstatus der Umgebung](assets/environ-update.png)

### Updates und Pipelines {#updates-pipelines}

Pipelines sind der einzige Weg, [Code in den Umgebungen von AEM as a Cloud Service bereitzustellen.](deploy-code.md) Aus diesem Grund ist jede Pipeline mit einer bestimmten AEM-Version verknüpft.

Wenn Cloud Manager erkennt, dass eine neuere Version von AEM verfügbar ist als die, die zuletzt mit der Pipeline bereitgestellt wurde, wird die **Verfügbare Aktualisierung** Status für die Umgebung.

Der Prozess der Aktualisierung erfolgt also in zwei Schritten:

1. Aktualisieren der Pipeline mit der neuesten AEM-Version
1. Ausführen der Pipeline zum Bereitstellen der neuen Version von AEM in einer Umgebung

### Aktualisieren von Umgebungen {#updating-your-environments}

Die **Aktualisieren** -Option verfügbar über **Umgebungen** Karte für Entwicklungsumgebungen und -umgebungen in Sandbox-Programmen durch Klicken auf die Suchschaltfläche der Umgebung.

![Option „Aktualisieren“ auf der Karte Umgebungen](assets/environ-update2.png)

Diese Option ist auch verfügbar, indem Sie auf **Umgebungen** und wählen Sie dann die Suchschaltfläche der Umgebung aus.

![Update-Option auf der Registerkarte „Umgebungen“](assets/environ-update3.png)

Ein Benutzer mit der Rolle **Bereitstellungs-Manager** kann diese Option verwenden, um die mit dieser Umgebung verknüpfte Pipeline auf die neueste AEM-Version zu aktualisieren.

Nachdem die Pipeline-Version auf die neueste öffentlich verfügbare AEM-Version aktualisiert wurde, wird der Benutzer aufgefordert, die zugehörige Pipeline auszuführen, um die neueste Version in der Umgebung bereitzustellen.

![Aufforderung zur Ausführung der Pipeline zur Aktualisierung der Umgebung](assets/update-run-pipeline.png)

Das Verhalten der Option **Aktualisieren** hängt von der Konfiguration und dem aktuellen Status des Programms ab.

* Wenn die Pipeline bereits aktualisiert wurde, fordert die Option **Aktualisieren** den Benutzer auf, die Pipeline auszuführen.
* Wenn die Pipeline gerade aktualisiert wird, informiert die Option **Aktualisieren** den Benutzer darüber, dass bereits eine Aktualisierung ausgeführt wird.
* Wenn keine geeignete Pipeline existiert, fordert die Option **Aktualisieren** den Benutzer auf, eine zu erstellen.

## Löschen von Entwicklungsumgebungen {#deleting-environment}

Benutzer mit der erforderlichen Berechtigung können eine Entwicklungsumgebung löschen.

Aus dem **Übersicht** Bildschirm des Programms auf der **Umgebungen** klicken Sie auf die Suchschaltfläche der Entwicklungsumgebung, die Sie löschen möchten.

![Die Löschoption](assets/environ-delete.png)

Die Löschoption ist auch über die Registerkarte **Umgebungen** des Fensters **Überblick** des Programms verfügbar. Klicken Sie auf die Suchschaltfläche der Umgebung und wählen Sie **Löschen**.

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
>Siehe [AEM as a Cloud Service Team und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md) , wenn Sie erfahren möchten, wie AEM as a Cloud Service Team und Produktprofile den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und beschränken können.

## Zugriff auf die Entwicklerkonsole {#accessing-developer-console}

Wählen Sie aus dem Menü mit den Auslassungspunkten der Umgebung auf der Karte **Umgebungen** die Option **Entwicklerkonsole** aus. In Ihrem Browser wird eine neue Registerkarte mit der Anmeldeseite zum **Entwicklerkonsole**.

![Melden Sie sich bei der Developer Console an](assets/environ-devconsole.png)

Nur Benutzer mit der **Entwickler** Rolle hat Zugriff auf die **Entwicklerkonsole**. Bei Sandbox-Programmen hat jedoch jeder Benutzer mit Zugriff auf das Sandbox-Programm Zugriff auf **Entwicklerkonsole**.

Siehe [Ruhezustand und Deaktivieren des Ruhezustands von Sandbox-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/introduction-sandbox-programs.html#hibernation) für weitere Details.

Diese Option ist auch über die Registerkarte **Umgebung** des Fensters **Überblick** beim Klicken auf das Menü mit den Auslassungspunkten einer einzelnen Umgebung verfügbar.

## Lokale Anmeldung {#login-locally}

Auswählen **Lokale Anmeldung** aus dem Suchmenü der Umgebung im **Umgebungen** -Karte, damit Sie sich lokal bei Adobe Experience Manager anmelden können.

![Lokale Anmeldung](assets/environ-login-locally.png)

Außerdem können Sie sich lokal über die **Umgebungen** des **Übersicht** Seite.

![Lokale Anmeldung über die Registerkarte Umgebungen](assets/environ-login-locally-2.png)

## Verwalten von benutzerdefinierten Domain-Namen {#manage-cdn}

Benutzerdefinierte Domain-Namen werden in Cloud Manager for Sites-Programmen sowohl für Veröffentlichungs- als auch für Vorschau-Services unterstützt. Jede Cloud Manager-Umgebung kann bis zu 250 benutzerdefinierte Domains hosten.

Um benutzerdefinierte Domänennamen zu konfigurieren, navigieren Sie zum **Umgebungen** und klicken Sie auf eine Umgebung, um Details zur Umgebung anzuzeigen.

![Umgebungsdetails](assets/domain-names.png)

Die folgenden Aktionen können für Ihre Umgebung im Veröffentlichungs-Service ausgeführt werden.

* [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

* [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)

* [Überprüfen des Status des benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) oder eines [SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn).

* [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn)


## Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

IP-Zulassungslisten werden in Cloud Manager für Autoren-, Veröffentlichungs- und Vorschaudienste für Sites-Programme unterstützt.

Um IP-Zulassungslisten zu verwalten, navigieren Sie zum **Umgebungen** des **Übersicht** Seite Ihres Programms. Klicken Sie auf eine einzelne Umgebung, damit Sie deren Details verwalten können.

### Anwenden einer IP-Zulassungsliste {#apply-ip-allow-list}

Beim Anwenden einer IP-Zulassungsliste werden alle in der Definition der Zulassungsliste enthaltenen IP-Bereiche mit einem Autoren- oder Veröffentlichungsdienst in einer Umgebung verknüpft. Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** -Rolle muss angemeldet sein, um eine IP-Zulassungsliste anwenden zu können.

Die IP-Zulassungsliste muss in Cloud Manager vorhanden sein, um sie auf eine Umgebung anwenden zu können. Weitere Informationen zu IP-Zulassungslisten in Cloud Manager finden Sie unter [Einführung in IP-Zulassungslisten in Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

**So wenden Sie eine IP-Zulassungsliste an:**

1. Gehen Sie von der Registerkarte **Umgebungen** des Bildschirms **Überblick** des Programms zu der bestimmten Umgebung und gehen Sie zur Tabelle **IP-Zulassungslisten**.
1. Verwenden Sie die Eingabefelder oben in der Tabelle der IP-Zulassungslisten-, damit Sie die IP-Zulassungsliste und den Autoren- oder Veröffentlichungsdienst auswählen können, auf den Sie sie anwenden möchten.
1. Klicken Sie auf **Anwenden** und bestätigen Sie Ihre Übermittlung.

### Aufheben der Anwendung einer IP-Zulassungsliste {#unapply-ip-allow-list}

Wenn Sie die Anwendung einer IP-Zulassungsliste aufheben, werden alle in der Definition der Zulassungsliste enthaltenen IP-Bereiche von einem Autoren- oder Publisher-Dienst in einer Umgebung getrennt. Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** -Rolle muss angemeldet sein, damit die Anwendung einer IP-Zulassungsliste aufgehoben werden kann.

**So heben Sie die Anwendung einer IP-Zulassungsliste auf:**

1. Gehen Sie von der Registerkarte **Umgebungen** des Bildschirms **Überblick** des Programms zu der bestimmten Umgebung und gehen Sie zur Tabelle **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile, in der die IP-Zulassungsliste-Regel, deren Anwendung Sie aufheben möchten, aufgeführt ist.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten am Ende der Zeile.
1. Wählen Sie **Anwendung rückgängig machen** aus und bestätigen Sie Ihre Übermittlung.
