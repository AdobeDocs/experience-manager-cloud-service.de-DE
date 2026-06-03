---
title: Adobe-verwaltete API-Integrationen in Adobe Admin Console
description: Erfahren Sie mehr über Adobe-Managed Service-Integrationen in Adobe Admin Console für AEM as a Cloud Service, was sie tun und wie Sie sie deaktivieren oder wiederherstellen.
feature: Security
role: Admin
source-git-commit: ab959e98fdca60ea936b14cf6941ab531c32c9ac
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 2%

---


# Adobe-verwaltete API-Integrationen in Adobe Admin Console {#adobe-managed-api-integrations-in-adobe-admin-console}

Adobe bietet eine kleine Anzahl von **Service-Integrationen** in Ihrer IMS-Organisation als Teil von AEM as a Cloud Service und den zugehörigen Adobe Experience Cloud-Funktionen. Diese Integrationen werden in der [Adobe Admin Console](https://adminconsole.adobe.com/) neben Integrationen angezeigt, die Sie selbst erstellen. Adobe-Services sind dafür verantwortlich und betreiben sie in Ihrem Namen.

Als System- oder Produktadministrator für Ihre IMS-Organisation können Sie überprüfen, was jede Integration tut, welche Adobe-Funktionen davon abhängen und ob sie aktiviert bleibt. Sie können die Integration von Adobe Managed Services jederzeit deaktivieren und bei Bedarf später wiederherstellen.

## Überblick {#overview}

Verwenden Sie diesen Artikel für Folgendes:

* Identifizieren Sie von Adobe verwaltete Integrationen, die Zugriff auf Ihre AEM-Umgebungen haben.
* Machen Sie sich mit dem Zweck jeder Integration und den von ihr unterstützten Adobe-Funktionen vertraut.
* Deaktivieren oder stellen Sie Integrationen von Admin Console aus wieder her, wenn Ihr Unternehmen dies benötigt.

Adobe wendet die folgenden Grundsätze für jede hier aufgeführte Service-Integration an:

* **Transparent benannt** - Jede Integration verwendet einen für Menschen lesbaren Namen, der ihren Zweck beschreibt.
* **Dokumentiert** - Jede Integration wird hier mit der unterstützten Funktion beschrieben.
* **Geringste Berechtigung** - Jede Integration erhält nur das Produktprofil, die Rolle oder die Berechtigung, die für ihre Funktion erforderlich sind, nicht jedoch umfassende Administratorrechte.
* **Vom Kunden steuerbar** - Jede Integration ist in Ihrer Admin Console sichtbar und kann von Ihren Administratoren deaktiviert oder wiederhergestellt werden.

## Wo Sie diese Integrationen finden {#where-to-find-these-integrations}

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) mit einem Systemadministrator- oder Produktadministratorkonto für Ihre IMS-Organisation an.
1. Um alle API-Anmeldeinformationen anzuzeigen, gehen Sie zu **Benutzer** > **API-Anmeldeinformationen**. Um Integrationen zu überprüfen, die über eine bestimmte Berechtigung verfügen, navigieren Sie **Produkte** > *das im Katalog genannte Adobe-* > *das entsprechende Produktprofil*.
1. Suchen Sie nach Service-Integrationen, deren Name mit `Adobe` beginnt oder die einem Namen im folgenden Katalog entsprechen.

>[!NOTE]
>
>In jedem Katalogeintrag sind das Adobe-Produkt sowie das Produktprofil, die Rolle oder die Berechtigung für diesen Integrations-Service aufgeführt. Verwenden Sie diesen Pfad, wenn Sie eine Integration überprüfen, deaktivieren oder wiederherstellen.
>
>Der in der Admin Console angezeigte Name ist die autorisierende Kennung. Wenn eine Service-Integration angezeigt wird, die unten nicht aufgeführt ist, wenden Sie sich an den [Adobe-Support](https://helpx.adobe.com/de/support.html) bevor Sie sie deaktivieren.

## Katalog der von Adobe verwalteten Integrationen {#catalog-of-adobe-managed-integrations}

In der folgenden Tabelle sind die Service-Integrationen aufgeführt, die Adobe für AEM as a Cloud Service-Kunden bereitstellt.

| Name wie in Admin Console angezeigt | Funktion | Verwendet von | Erteilte Berechtigungen | Standardmäßig aktiviert |
|---|---|---|---|---|
| **AEM Managed CDN-Integration** | Ermöglicht es dem LLM Optimizer-Service, Ihr in AEM as a Cloud Service verwaltetes CDN (**-Traffic-Routing-Regeln** in Ihrem Namen zu aktualisieren, damit KI- und Agent-Crawler (wie ChatGPT, Perplexity und Claude) ohne manuelle CDN-Änderungen durch Ihr Team an LLM Optimizer-optimierte Ursprünge weitergeleitet werden können. | **LLM Optimizer** über die Funktion [Bei Edge optimieren](https://experienceleague.adobe.com/de/docs/llm-optimizer/using/resources/optimize-at-edge/overview) | Cloud Manager **Bereitstellungs-Manager** Rolle | Ja |

Der folgende Screenshot ist ein Beispiel für die in der obigen Tabelle **Integration des von AEM verwalteten CDN.**

![AEM Managed CDN-Integration im Cloud Manager Deployment Manager-Produktprofil in Adobe Admin Console](assets/aem-managed-cdn-integration-admin-console.png)

>[!NOTE]
>
>Adobe bietet derzeit eine Service-Integration unter diesem Modell. Adobe aktualisiert diese Tabelle, wenn zusätzliche Services denselben Ansatz verwenden. Wenn Ihre Admin Console eine andere von Adobe bereitgestellte Service-Integration anzeigt, die hier nicht aufgeführt ist, verwenden Sie die Admin Console als Informationsquelle und wenden Sie sich an den [Adobe-Support](https://helpx.adobe.com/de/support.html), um weitere Informationen zu erhalten.

## Auswirkungen der Deaktivierung einer Integration {#impact-of-disabling-an-integration}

Sie können eine Adobe-Managed Service-Integration jederzeit deaktivieren. In diesem Fall funktioniert die Adobe-Funktion, die von dieser Integration abhängig ist, für Ihr Unternehmen nicht mehr, bis Sie sie wiederherstellen. Überprüfen Sie die folgende Tabelle, bevor Sie eine Integration deaktivieren.

| Integration | Funktionsweise von bei Deaktivierung | Was weiterhin funktioniert |
|---|---|---|
| **AEM Managed CDN-Integration** | <ul><li><strong>LLM Optimizer-Benutzer können die von AEM as a Cloud Service verwalteten CDN-Regeln für die agentische Datenverkehrsweiterleitung für Ihre Domains nicht mehr </strong>. Jeder nachfolgende Versuch eines LLMO-Administrators, das agentische Routing zu aktivieren, zu ändern oder zu widerrufen, schlägt bei der Autorisierung auf CDN-Ebene fehl.</li><li>Routing von KI-/Agenten-Crawlers (ChatGPT, Perplexity, Claude usw.) Für LLM Optimizer optimierte Ursprünge können erst dann (neu) konfiguriert werden, wenn die Integration reaktiviert wurde.</li><li>Bereits angewendete agentische Routing-Regeln bleiben am Edge in Kraft, können jedoch nicht geändert oder entfernt werden, ohne die Integration erneut zu aktivieren (oder sich manuell mit dem Adobe-Kunden-Support abzustimmen).</li></ul> | <ul><li>Die Autoren-, Veröffentlichungs- und Vorschau-Umgebungen von AEM as a Cloud Service stellen den Traffic weiterhin normal bereit.</li><li>Die standardmäßige (nicht-agentische) CDN-Bereitstellung Ihrer bereits bereitgestellten Sites erfolgt unverändert.</li><li>Cloud Manager-Pipelines und -Bereitstellungen funktionieren weiterhin für Benutzeroperatoren mit Berechtigungen für den Bereitstellungs-Manager.</li><li>Alle LLM Optimizer-Funktionen, die nicht vom Edge-Routing abhängen, funktionieren weiterhin.</li></ul> |

## Deaktivieren einer Integration {#how-to-disable-an-integration}

**Wer kann diese Aufgabe ausführen:** Eine IMS-Organisation **Systemadministrator** oder der **Produktadministrator** für das Adobe-Produkt, dessen Profil, Rolle oder Berechtigung Zugriff auf die Service-Integration gewährt (siehe *Berechtigungen erteilt* in der Katalogzeile).

Die Schritte sind für jede Service-Integration in diesem Artikel identisch. Nur der Navigationspfad in Admin Console ändert sich basierend auf dem Produktprofil für diese Integration.

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) an.
1. Identifizieren Sie das **Adobe** Produkt und das **Produktprofil, die Rolle oder die Berechtigung** für die Service-Integration. Beide werden in der Katalogzeile aufgeführt.
1. Navigieren Sie **Produkte** > *das Adobe-* > *das Produktprofil*.
1. Öffnen Sie die Registerkarte **API** Anmeldeinformationen oder **Benutzer** für dieses Profil.
1. Suchen Sie die Service-Integration anhand des genauen Namens in der Katalogzeile.
1. Entfernen Sie die Service-Integration aus dem Produktprofil . Die Integration ist für Ihre Organisation deaktiviert. Wenn der Adobe-Service das nächste Mal in Ihrem Namen agiert, wird die Autorisierung verweigert.

**Beispiel - AEM Managed CDN-Integration:** Wechseln Sie zu **Produkte** > **Adobe Experience Manager as a Cloud Service** > **Cloud Manager** > **Bereitstellungs-Manager**, suchen Sie nach **AEM Managed CDN Integration** und entfernen Sie sie aus dem Produktprofil.

## Wiederherstellen einer Integration {#how-to-restore-an-integration}

Wenn Sie eine Integration zuvor deaktiviert haben und erneut aktivieren möchten:

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) als System- oder Produktadministrator an.
1. Navigieren Sie zu **demselben Produkt- und Produktprofil** das im obigen Katalog für die Service-Integration identifiziert wurde. Dies ist das Profil, aus dem die Service-Integration entfernt wurde, als sie deaktiviert wurde.
1. Wählen Sie **Benutzer hinzufügen** oder **API hinzufügen** und suchen Sie dann nach der Service-Integration anhand des exakten Namens, der im Katalog aufgeführt ist.
1. Fügen Sie die Service-Integration wieder zum Produktprofil hinzu. Die Integration wird bei der nächsten geplanten oder vom Benutzer initiierten Ausführung fortgesetzt.

**Beispiel - AEM Managed CDN-Integration:** Wechseln Sie zu **Cloud Manager** > **Bereitstellungs-Manager** und fügen Sie **AEM Managed CDN-Integration** erneut mit **Benutzer hinzufügen** oder **API hinzufügen** hinzu.

>[!NOTE]
>
>Wenn Sie die Service-Integration im Dialogfeld zum Hinzufügen von Benutzern nicht finden können (z. B. weil Adobe sie aus Ihrer Organisation und nicht nur aus dem Profil entfernt hat), wenden Sie sich an den [Adobe-Kunden-Support](https://helpx.adobe.com/de/support.html), um die Bereitstellung anzufordern. Adobe fügt eine Service-Integration, die Ihr Administrator entfernt hat, nicht automatisch erneut hinzu.

