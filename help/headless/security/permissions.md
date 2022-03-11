---
title: Überlegungen zur Berechtigung für Headless-Inhalte
description: Erfahren Sie mehr über verschiedene Berechtigungen und ACL-Überlegungen für eine Headless-Implementierung mit Adobe Experience Manager. Machen Sie sich mit den verschiedenen Rollen und möglichen Berechtigungsstufen vertraut, die sowohl für die Autoren- als auch für die Veröffentlichungsumgebung erforderlich sind.
feature: Content Fragments,GraphQL API
exl-id: 3fbee755-2fa4-471b-83fc-3f4bf056267a
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Überlegungen zur Berechtigung für Headless-Inhalte

Bei einer Headless-Implementierung gibt es mehrere Bereiche von Sicherheit und Berechtigungen, die angesprochen werden sollten. Berechtigungen und Rollen können in der AEM Umgebung umfassend betrachtet werden **Autor** oder **Veröffentlichen**. Jede Umgebung enthält unterschiedliche Personas und unterschiedliche Anforderungen.

## Überlegungen zum Autorendienst

Im Autorendienst erstellen, verwalten und veröffentlichen interne Benutzer Inhalte. Berechtigungen beziehen sich auf die verschiedenen Personen, die Inhalte verwalten.

### Berechtigungen auf Gruppenebene verwalten

Als Best Practice sollten Berechtigungen für Gruppen in AEM festgelegt werden. Diese Gruppen werden auch als lokale Gruppen bezeichnet und können in der AEM Autorenumgebung verwaltet werden.

Die einfachste Möglichkeit, die Gruppenmitgliedschaft zu verwalten, besteht darin, Adobe Identity Management System (IMS)-Gruppen zu verwenden und [IMS-Gruppen für lokale AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=en#managing-permissions-in-aem).

![Berechtigungsfluss der Admin Console](assets/admin-console-aem-group-permissions.png)

Auf hoher Ebene sieht der Prozess folgendermaßen aus:

1. Fügen Sie IMS-Benutzer mithilfe der [Admin Console](https://adminconsole.adobe.com/)
1. IMS-Gruppen werden mit AEM synchronisiert, wenn sich Benutzer anmelden.
1. Weisen Sie AEM Gruppen IMS-Gruppen zu.
1. Legen Sie Berechtigungen für AEM Gruppen fest.
1. Wenn sich Benutzer bei AEM anmelden und über IMS authentifiziert werden, erben sie die Berechtigungen der AEM Gruppe.

>[!TIP]
>
> Eine ausführliche Videoeinführung zur Verwaltung von IMS und AEM Benutzern und Gruppen finden Sie [here](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html).

Zu verwalten **Gruppen** Navigieren Sie in AEM zu **Instrumente** > **Sicherheit** > **Gruppen**.

Um die Berechtigungen von Gruppen in AEM zu verwalten, navigieren Sie zu **Instrumente** > **Sicherheit** > **Berechtigungen**.

### DAM-Benutzer

&quot;DAM&quot;steht in diesem Zusammenhang für Digital Asset Management. Die **DAM-Benutzer** ist eine vordefinierte Gruppe in AEM, die für &quot;alltägliche&quot;Benutzer verwendet werden kann, die digitale Assets und Inhaltsfragmente verwalten. Diese Gruppe gewährt Berechtigungen für **Ansicht**, **add**, **update**, **delete** und **publish** Inhaltsfragmente und alle anderen Dateien in AEM Assets.

Wenn Sie IMS für die Gruppenmitgliedschaft verwenden, fügen Sie die entsprechenden IMS-Gruppen als Mitglieder des **DAM-Benutzer** hinzugefügt. Mitglieder der IMS-Gruppe erben bei der Anmeldung in der AEM die Berechtigungen der DAM-Benutzergruppe.

#### Anpassen der DAM-Benutzergruppe

Es ist am besten, die Berechtigungen einer vordefinierten Gruppe nicht direkt zu ändern. Stattdessen können Sie auch Ihre eigenen Gruppen erstellen, die nach dem Modell **DAM-Benutzer** Gruppenberechtigungen und den Zugriff auf verschiedene **Ordner** innerhalb von AEM Assets.

Für detailliertere Berechtigungen verwenden Sie die **Berechtigungen** Konsole in AEM und aktualisieren Sie den Pfad von `/content/dam` zu einem spezifischeren Pfad, d. h. `/content/dam/mycontentfragments`.

Es kann wünschenswert sein, dieser Benutzergruppe Berechtigungen zum Erstellen und Bearbeiten von Inhaltsfragmenten zu erteilen, jedoch nicht zum Löschen. Informationen zum Überprüfen und Zuweisen von Berechtigungen für die Bearbeitung, aber nicht zum Löschen finden Sie unter [Inhaltsfragmente - Überlegungen zum Löschen](/help/assets/content-fragments/content-fragments-delete.md).

### Modell-Editoren

Die Möglichkeit, **Inhaltsfragmentmodelle** sollte Administratoren überlassen werden oder eine **kleine Gruppe** von Benutzern mit erhöhten Berechtigungen. Das Ändern des Inhaltsfragmentmodells hat viele nachgelagerte Auswirkungen.

>[!CAUTION]
>
>Änderungen an Inhaltsfragmentmodellen ändern die zugrunde liegende GraphQL-API, auf die Headless-Anwendungen angewiesen sind.

Wenn Sie eine Gruppe erstellen möchten, die Inhaltsfragmentmodelle verwaltet, aber nicht den vollständigen Administratorzugriff hat, können Sie eine Gruppe mit den folgenden Zugriffssteuerungseinträgen erstellen:

| Pfad   | Berechtigung | Berechtigungen |
|-----| -------------| ---------|
| `/conf` | **zulassen** | `jcr:read` |
| `/conf/<config-name>/settings/dam/cfm` | **zulassen** | `rep:write`, `crx:replicate` |

## Berechtigungen für Veröffentlichungsdienst

Der Veröffentlichungsdienst wird als &quot;Live-Umgebung&quot;betrachtet und ist normalerweise das, mit dem GraphQL-API-Kunden interagieren. Nach der Bearbeitung und Genehmigung im Autorendienst werden Inhalte im Veröffentlichungsdienst veröffentlicht. Die Headless-Anwendung nutzt dann die genehmigten Inhalte aus dem Veröffentlichungsdienst über GraphQL-APIs.

Standardmäßig sind über die GraphQL-Endpunkte des AEM Publish-Dienstes veröffentlichte Inhalte für alle verfügbar, auch für nicht authentifizierte Benutzer.

### Inhaltsberechtigungen

Inhalte, die über AEM GraphQL-APIs verfügbar gemacht werden, können mithilfe von [Geschlossene Benutzergruppen (CUGs)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html) festgelegt auf Asset-Ordner, die angeben, welche AEM Benutzergruppen (und deren Mitglieder) auf den Inhalt der Assets-Ordner zugreifen können.

Assets-CUGs funktionieren durch:

* Verweigern Sie zunächst den Zugriff auf den Ordner und die Unterordner.
* Zulassen des Lesezugriffs auf den Ordner und die Unterordner für alle AEM Benutzergruppen, die in der CUGs-Liste aufgeführt sind

CUGs können für Asset-Ordner eingerichtet werden, die über GraphQL-APIs offen gelegte Inhalte enthalten. Der Zugriff auf Asset-Ordner in der AEM-Veröffentlichungsinstanz sollte über Benutzergruppen gesteuert werden und nicht direkt über den Benutzer. Erstellen (oder verwenden) Sie eine AEM Benutzergruppe, die Zugriff auf Asset-Ordner gewährt, die Inhalte enthalten, die von GraphQL-APIs bereitgestellt werden.

#### Authentifizierungsschema auswählen{#publish-permissions-users}

Die [AEM Headless-SDK](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) unterstützt zwei Authentifizierungstypen:

* [Token-basierte Authentifizierung](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) Verwendung von Dienstanmeldeinformationen, die an ein einzelnes technisches Konto gebunden sind.
* Grundlegende Authentifizierung mit AEM Benutzern.

### Zugriff auf die GraphQL-API

HTTP-Anforderungen, die die [geeignete Authentifizierungsberechtigungen](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) Zu den GraphQL-API-Endpunkten des AEM Publish-Service gehören Inhalt, zu dem die Anmeldeinformationen berechtigt sind, zu lesen, und anonym zugänglicher Inhalt. Andere Benutzer der GraphQL-API können den Inhalt in den CUGs-geschützten Ordnern nicht lesen.
