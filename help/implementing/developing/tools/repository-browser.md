---
title: Repository-Browser
seo-title: Repository Browser
description: Der Repository-Browser bietet eine schreibgeschützte Ansicht des Repositorys für alle Umgebungen in den Autoren-, Veröffentlichungs- und Vorschau-Ebenen.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
exl-id: 22473a97-8f7b-4014-b885-1233116aeda6
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 100%

---

# Repository-Browser {#repository-browser}

>[!NOTE]
>
>Der Repository-Browser ist in AEM Version 6582 und höher verfügbar.

>[!INFO]
>
>Sie können auch [diesen Clip](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html?lang=de) ansehen. Er enthält eine kurze Videoeinführung zum Debugging von AEM as a Cloud Service mit dem Repository-Browser.

## Einführung {#introduction}

Der Repository-Browser ist ein Entwicklungs-Tool, das eine schreibgeschützte Ansicht des Repositorys für alle Umgebungen auf Authoring-, Publishing- und Vorschau-Ebene bereitstellt. Er soll die Anzeige der Inhaltsstruktur erleichtern, um die Anzeige oder Fehlerbehebung von Inhalten zu vereinfachen.

Er ist über die [AEM as a Cloud Service Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) zugänglich und kann zum Durchsuchen des Repositorys einer Autoren- oder Veröffentlichungsinstanz für eine ausgewählte Umgebung verwendet werden.

### Voraussetzungen für den Zugriff {#access-prerequisites}

Die folgenden Bedingungen müssen erfüllt sein, damit auf die AEM as a Cloud Service Developer Console oder den Repository-Browser zugegriffen werden kann.

Informationen zum Zugriff auf die Developer Console von AEM as a Cloud Service finden Sie unter [Zugriff auf die Developer Console](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console#developer-console-access).

Für den Zugriff auf den Repository-Browser gelten die gleichen Voraussetzungen wie für die Developer Console von AEM as a Cloud Service (siehe oben). So zeigen Sie den Inhalt des Repository-Browsers für eine bestimmte Instanz an:

* Autoreninstanzen: Benutzende mit dem Produktprofil „AEM-Benutzer“ für die **Autoreninstanz** können den Repository-Browser mit minimalem Lesezugriff anzeigen. Die Berechtigungen der Person werden beim Durchsuchen des Repositorys respektiert. Benutzende mit dem Produktprofil „AEM-Administrator“ können den Repository-Browser mit vollem Lesezugriff benutzen.

* Veröffentlichungsinstanzen: Benutzende mit dem Produktprofil „AEM-Benutzer“ für die **Veröffentlichungsinstanz** können den Repository-Browser mit minimalem Lesezugriff anzeigen. Ohne diesen Produktprofilsatz navigieren Benutzende anonym, und einige Pfade werden aufgrund eingeschränkter Berechtigungen nicht angezeigt.

Weitere Informationen zum Einrichten von Benutzerberechtigungen finden Sie in der [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/requirements/users-and-roles.html?lang=de).

### Starten des Repository-Browsers {#launching-the-repository-browser}

Gehen Sie wie folgt vor, um den Repository-Browser zu starten:

1. Klicken Sie in Cloud Manager auf die drei Punkte neben der Umgebung Ihrer Wahl und wählen Sie **Entwicklerkonsole** aus.

   ![repobrowser1](/help/implementing/developing/tools/assets/repobrowser1.png)

1. Klicken Sie anschließend auf die Registerkarte **Repository-Browser**.
1. Wählen Sie einen Pod aus, der Author, Publish oder einer Vorschau entspricht, indem Sie auf die Dropdown-Liste **Pod** klicken.

   ![repobrowser2](/help/implementing/developing/tools/assets/repobrowser2.png)

1. Starten Sie den Repository-Browser, indem Sie auf den Link **Repository-Browser öffnen** weiter unten klicken. Der Browser, der einer repräsentativen Instanz (Pod) für die ausgewählte Ebene entspricht, wird gestartet. Sie können nicht kontrollieren, welcher Pod für diese Ebene gestartet wird.

## Funktionen {#features}

### Navigieren in der Hierarchie {#navigate-the-hierarchy}

Sie können das Navigationsfenster auf der linken Seite verwenden, um durch die Inhaltshierarchie zu navigieren. Wenn Sie auf einen Ordner oder Knoten klicken, werden dessen untergeordnete Elemente angezeigt. Die Ordnerstruktur spiegelt die Sling Resource-Struktur wider, die eine Übermenge der JCR-Knotenstruktur ist.

![repobrowser3](/help/implementing/developing/tools/assets/repobrowser3.png)

Alternativ können Sie direkt zu einem Pfad navigieren, indem Sie ihn in das Feld **Pfad** wie unten dargestellt eingeben. Durch diesen Pfad wird auch die Position in der Inhaltshierarchieansicht auf der linken Seite erweitert.

![repobrowser14](/help/implementing/developing/tools/assets/repobrowser14.png)

Wenn Sie auf einen Ordner auf der linken Seite klicken, wird das Feld „Pfad“ automatisch mit dem entsprechenden Speicherort ausgefüllt. Diese Funktionalität ist hilfreich, um den Wert für eine spätere Verwendung zu kopieren und einzufügen.

Wenn Sie auf einen Ordner klicken, wird außerdem die URL dynamisch geändert, sodass sie den Pfad zu diesem Ordner einschließt. Diese Funktionalität ermöglicht Lesezeichen-URLs.

Für die Publishing-Instanz zeigt der Repository-Browser standardmäßig nur öffentliche Inhalte an, sodass bestimmte Ordner wie `/conf` oder `/home` nicht angezeigt werden.

Gehen Sie wie folgt vor, um diese Speicherorte sichtbar zu machen.

1. Klicken Sie auf die drei Punkte neben der Umgebung Ihrer Wahl und wählen Sie **Zugriff verwalten**.

   ![repobrowser7](/help/implementing/developing/tools/assets/repobrowser7.png)

1. Suchen Sie Ihre Veröffentlichungsinstanz und klicken Sie darauf

   ![repobrowser8](/help/implementing/developing/tools/assets/repobrowser8.png)

1. Erstellen Sie ein Produktprofil für Veröffentlichungs-Admins. Im folgenden Beispiel wird es **DEV – AEM-Veröffentlichungsadministratoren** genannt.

   ![repobrowser9](/help/implementing/developing/tools/assets/repobrowser9.png)

1. Fügen Sie dem neuen Produktprofil die entsprechenden Benutzer hinzu, die in der Lage sein sollten, im Browser des Veröffentlichungs-Repositorys mit vollem Zugriff zu navigieren.

   ![repobrowser10](/help/implementing/developing/tools/assets/repobrowser10.png)

1. Warten Sie einige Minuten und öffnen Sie dann die **AEM-Autoren**-Konsole.
1. Fügen Sie die Gruppe, die dem neuen Produktprofil entspricht, als Mitglied der Admingruppe hinzu, indem Sie auf **„Tools“ > „Sicherheit“ > „Gruppen“ in der Authoring-Instanz** und dann auf die Gruppe **Admins** klicken. Fügen Sie dann die Gruppe wie unten gezeigt hinzu.

   ![repobrowser11](/help/implementing/developing/tools/assets/repobrowser11.png)

1. Aktivieren Sie die Gruppe **Administratoren** und die neue Gruppe **DEV – AEM-Veröffentlichungsadministratoren**, damit sie in der Veröffentlichungsinstanz verfügbar werden.

   ![repobrowser12](/help/implementing/developing/tools/assets/repobrowser12.png)

1. Als bewährte Sicherheitsmaßnahme sollten Sie die neue Gruppe **DEV – AEM-Veröffentlichungsadmins** aus der Admingruppe auf **Authoring** entfernen, sodass die neue Gruppe auf die Veröffentlichung beschränkt ist.

   ![repobrowser13](/help/implementing/developing/tools/assets/repobrowser13.png)

1. Beim Zugriff auf den Repository-Browser für eine Veröffentlichungsinstanz sind alle Ordner sichtbar, einschließlich `/home` und `/conf`.

### Anzeigen der JCR-Eigenschaften {#view-jcr-properties}

Wenn Sie auf einen Knoten klicken, werden dessen JCR-Eigenschaften im rechten Bereich des Navigations-Browsers angezeigt. Nachfolgend finden Sie ein Beispiel für den Knoten `experience-fragments`.

![repobrowser4](/help/implementing/developing/tools/assets/repobrowser41.png)

### Inhalt anzeigen {#view-content}

Sie können den Repository-Browser zum Anzeigen von Inhalten verwenden. Klicken Sie auf eine Ressource im Navigationsfenster, um eine Vorschau auf der rechten Seite des Browsers in einer Registerkarte zu öffnen, die nach der entsprechenden Ressource benannt ist.

![repobrowser6](/help/implementing/developing/tools/assets/repobrowser61.png)

Die Vorschau ist für die folgenden Bildtypen verfügbar:

* apng
* avif
* gif
* jpeg
* png
* svg+xml
* webp
* bmp
* x-icon
* tiff

Und für die folgenden textbasierten MIME-Typen:

* `"text/*"`
* `'application/javascript'`
* `'application/json'`
* `'application/x-sh'`

### Herunterladen von Inhalten {#download-content}

Sie können den Repository-Browser auch verwenden, um Inhalte herunterzuladen. Im folgenden Beispiel können Sie auf den Link **Herunterladen** klicken, um die `jcr:data` herunterzuladen, die mit dem ausgewählten Knoten verknüpft sind. Diese Funktion ist für alle binären Eigenschaften verfügbar, indem Sie zu dem Knoten gehen, der die Eigenschaftsdefinition enthält.

![repobrowser5](/help/implementing/developing/tools/assets/repobrowser52.png)
