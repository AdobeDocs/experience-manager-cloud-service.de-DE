---
title: Repository-Browser
seo-title: Repository Browser
description: Der Repository-Browser bietet eine schreibgeschützte Ansicht des Repositorys für alle Umgebungen in der Autoren-, Veröffentlichungs- und Vorschauschicht.
seo-description: The repository browser provides a read-only view into the repository for all environments on author, publish, and preview tiers.
source-git-commit: 76e28ca5628fb985df21f53d1c3e9898985dc736
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 3%

---


# Repository-Browser {#repository-browser}

>[!NOTE]
>
>Der Repository-Browser ist in AEM Version 6582 und höher verfügbar.

## Einführung {#introduction}

Der Repository-Browser ist ein Entwickler-Tool, das eine schreibgeschützte Ansicht des Repositorys für alle Umgebungen auf der Ebene der Autoren-, Veröffentlichungs- und Vorschaudateien bereitstellt. Sie soll die Anzeige der Inhaltsstruktur erleichtern, um die Anzeige oder Fehlerbehebung von Inhalten zu vereinfachen.

Sie ist über die Developer Console zugänglich und kann zum Durchsuchen des Repositorys einer Autoren- oder Veröffentlichungsinstanz für eine ausgewählte Umgebung verwendet werden.

### Zugriffsvoraussetzungen {#access-prerequisites}

Die folgenden Bedingungen müssen erfüllt sein, damit auf die Developer Console oder den Repository-Browser zugegriffen werden kann

So greifen Sie auf die Developer Console zu:

* Für Produktionsprogramme müssen die Benutzer über die **Cloud Manager - Rolle &quot;Entwickler&quot;** in der Admin Console
* Bei Sandbox-Programmen ist sie für jeden Benutzer verfügbar, der über ein Produktprofil verfügt, das ihm Zugriff auf AEM as a Cloud Service gewährt.

So greifen Sie auf den Repository-Browser zu:

* Die Benutzer müssen über die **Cloud Manager - Entwickler** Rolle in der Admin Console zum Anzeigen der Autoren- und Veröffentlichungsinstanzen.
* Darüber hinaus können Benutzer mit dem AEM Benutzer-Produktprofil den Repository-Browser mit minimalem Lesezugriff anzeigen. die Berechtigungen des Benutzers beim Durchsuchen des Repositorys eingehalten werden. Benutzer mit dem Produktprofil AEM Administratoren können den Repository-Browser mit vollem Lesezugriff anzeigen.

Weitere Informationen zum Einrichten von Benutzerberechtigungen finden Sie unter [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=de).

### Starten des Repository-Browsers {#launching-the-repository-browser}

Der Repository-Browser kann wie folgt gestartet werden:

1. Klicken Sie in Cloud Manager auf die drei Punkte neben der Umgebung Ihrer Wahl und wählen Sie **Entwicklerkonsole**

   ![repobrowser1](/help/implementing/developing/tools/assets/repobrowser1.png)

1. Klicken Sie anschließend auf das **Repository-Browser** tab
1. Wählen Sie einen Pod aus, der der Autoren-, Veröffentlichungs- oder Vorschau entspricht, indem Sie auf die Schaltfläche **Pod** Dropdown-Liste.

   ![repobrowser2](/help/implementing/developing/tools/assets/repobrowser2.png)

1. Starten Sie den Repository-Browser, indem Sie auf die **Repository-Browser öffnen** weiter unten. Dadurch wird der Browser gestartet, der einer repräsentativen Instanz (Pod) für die ausgewählte Ebene entspricht. Dadurch wird der Browser gestartet, der einer repräsentativen Instanz (Pod) für die ausgewählte Ebene entspricht. Beachten Sie, dass Sie die spezifische Werbeunterbrechung für diese Ebene, die gestartet wird, nicht steuern können.

## Funktionen {#features}

### Navigieren in der Hierarchie {#navigate-the-hierarchy}

Sie können das Navigationsfenster auf der linken Seite verwenden, um durch die Inhaltshierarchie zu navigieren. Wenn Sie auf jeden Ordner oder Knoten klicken, werden dessen untergeordnete Elemente angezeigt. Die Ordnerstruktur spiegelt die Sling Resource-Struktur wider, die eine Hauptmenge der JCR-Knotenstruktur ist.

![repobrowser3](/help/implementing/developing/tools/assets/repobrowser3.png)

Für die Veröffentlichung zeigt der Repository-Browser standardmäßig nur öffentliche Inhalte an, sodass bestimmte Ordner wie `/conf` oder `/home` wird nicht angezeigt.

Um diese Orte sichtbar zu machen, müssen Sie das folgende Verfahren befolgen.

1. Klicken Sie auf die drei Punkte neben der Umgebung Ihrer Wahl und wählen Sie **Zugriff verwalten**

   ![repobrowser7](/help/implementing/developing/tools/assets/repobrowser7.png)

1. Suchen Sie Ihre Veröffentlichungsinstanz und klicken Sie darauf

   ![repobrowser8](/help/implementing/developing/tools/assets/repobrowser8.png)

1. Erstellen Sie ein neues Produktprofil für Veröffentlichungsadministratoren. Im folgenden Beispiel wird es **DEV - Veröffentlichung AEM Administratoren**

   ![repobrowser9](/help/implementing/developing/tools/assets/repobrowser9.png)

1. Fügen Sie dem neuen Produktprofil die entsprechenden Benutzer hinzu, die in der Lage sein sollten, im Browser des Publishing-Repositorys mit vollem Zugriff zu navigieren

   ![repobrowser10](/help/implementing/developing/tools/assets/repobrowser10.png)

1. Warten Sie einige Minuten und öffnen Sie dann die **AEM** console
1. Fügen Sie die dem neuen Produktprofil entsprechende Gruppe als Mitglied der Administratorgruppe hinzu. Klicken Sie hierzu auf **Tools - Sicherheit - Gruppen auf der Autoreninstanz** und klicken Sie dann auf die **Administratoren** hinzugefügt. Fügen Sie dann die Gruppe wie unten gezeigt hinzu

   ![repobrowser11](/help/implementing/developing/tools/assets/repobrowser11.png)

1. Aktivieren Sie die **Administratoren** und der neuen **DEV - Veröffentlichung AEM Administratoren** -Gruppe, damit sie in der Veröffentlichungsinstanz verfügbar werden

   ![repobrowser12](/help/implementing/developing/tools/assets/repobrowser12.png)

1. Als gute Sicherheitsmaßnahme sollten Sie die neue **DEV - Veröffentlichung AEM Administratoren** aus der Administratorgruppe auf **author** sodass die neue Gruppe für die Veröffentlichung isoliert ist

   ![repobrowser13](/help/implementing/developing/tools/assets/repobrowser13.png)

1. Beim Zugriff auf den Repository-Browser für eine Veröffentlichungsinstanz sind alle Ordner sichtbar, einschließlich `/home` und `/conf`.

### JCR-Eigenschaften anzeigen {#view-jcr-properties}

Wenn Sie auf einen Knoten klicken, werden dessen JCR-Eigenschaften im rechten Bereich des Navigationsbrowsers angezeigt. Nachfolgend finden Sie ein Beispiel für die `experience-fragments` Knoten.

![repobrowser4](/help/implementing/developing/tools/assets/repobrowser41.png)

### Inhalt anzeigen {#view-content}

Sie können den Repository-Browser verwenden, um Inhalte anzuzeigen, indem Sie im Navigationsbereich auf eine Ressource klicken. Dadurch wird eine Vorschau auf der rechten Seite des Browsers auf einer Registerkarte geöffnet, die nach der entsprechenden Ressource benannt ist.

![repobrowser6](/help/implementing/developing/tools/assets/repobrowser61.png)

Die Vorschau ist derzeit für Bildtypen in der folgenden Liste verfügbar:

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

### Inhalt herunterladen {#download-content}

Sie können auch den Repository-Browser verwenden, um Inhalte herunterzuladen. Im folgenden Beispiel können Sie die **herunterladen** Link zum Herunterladen der `jcr:data` mit dem ausgewählten Knoten verknüpft ist. Diese Funktion ist für alle binären Eigenschaften verfügbar, indem Sie zu dem Knoten navigieren, der die Eigenschaftsdefinition enthält.

![repobrowser5](/help/implementing/developing/tools/assets/repobrowser52.png)
