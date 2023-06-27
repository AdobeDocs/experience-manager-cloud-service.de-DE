---
title: DevOp-Strategien für Unternehmen
description: Erfahren Sie mehr über die Prozesse, Methoden und Kommunikation, die zur Erleichterung der Bereitstellung und Vereinfachung der Zusammenarbeit erforderlich sind.
exl-id: c8da1fd7-fe3e-4c7b-8fe7-1f7faf02769c
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 48%

---

# DevOp-Strategien für Unternehmen{#enterprise-devops}

DevOps umfasst die Prozesse, Methoden und Kommunikation, die erforderlich sind, um:

* Erleichterung der Bereitstellung der Software über die verschiedenen Umgebungen hinweg;
* Vereinfachen Sie die Zusammenarbeit zwischen den Entwicklungs-, Test- und Bereitstellungsteams.

DevOp-Strategien sollen unter anderem zur Vermeidung folgender Probleme beitragen:

* Manuelle Fehler;
* Vergessene Elemente, beispielsweise Dateien, Konfigurationsdetails.
* Diskrepanzen, beispielsweise zwischen der lokalen Umgebung des Entwicklers und anderen Umgebungen.

## Umgebungen {#environments}

Adobe Experience Manager (AEM) as a Cloud Service besteht gewöhnlich aus mehreren Umgebungen, die für unterschiedliche Zwecke auf unterschiedlichen Ebenen benutzt werden:

* [Entwicklung](#development)
* [Qualitätssicherung](#quality-assurance)
* [Staging  ](#staging)
* [Produktion](#production-author-and-publish)

>[!NOTE]
>
>Die Produktionsumgebung muss mindestens eine Autoren- und eine Veröffentlichungsumgebung umfassen.
>
>Es wird empfohlen, alle anderen Umgebungen ebenfalls mit einer Autoren- und einer Veröffentlichungsumgebung zu gestalten, um die Produktionsumgebung widerzuspiegeln und frühe Test zu ermöglichen.

### Entwicklung {#development}

Die Entwickler sind für die Entwicklung und Anpassung des vorgeschlagenen Projekts (Website, Mobile Apps, DAM-Implementierung usw.) mit allen erforderlichen Funktionen verantwortlich. Sie:

* entwickeln und passen die notwendigen Elemente an, beispielsweise Vorlagen, Komponenten, Arbeitsabläufe, Anwendungen;
* setzen das Design um;
* entwickeln die erforderlichen Dienste und Skripte, damit Sie die erforderlichen Funktionen implementieren können.

Die Konfiguration der [development](/help/implementing/developing/introduction/development-guidelines.md) -Umgebung kann von verschiedenen Faktoren abhängen, in der Regel besteht sie jedoch aus:

* Ein integriertes Entwicklungssystem mit Versionskontrolle zur Bereitstellung einer integrierten Codebasis. Diese integrierte Codebasis wird verwendet, um Code aus den einzelnen Entwicklungsumgebungen zusammenzuführen und zu konsolidieren, die von den einzelnen Entwicklern verwendet werden.
* eine persönliche Umgebung für jeden Entwickler, für gewöhnlich auf einem lokalen Rechner. In angemessenen Abständen wird der Code mit dem Versionskontrollsystem synchronisiert

Je nach Größe Ihres Systems kann die Entwicklungsumgebung sowohl über Autoren- als auch Veröffentlichungsinstanzen verfügen.

### Qualitätssicherung {#quality-assurance}

Diese Umgebung wird vom Qualitätssicherungs-Team zur umfassenden Prüfung des neuen Systems, sowohl in Bezug auf Design als auch Funktion, verwendet. Sie sollte über eine Autoren- und eine Veröffentlichungsumgebung mit geeignetem Inhalt verfügen und sämtliche notwendigen Dienste zur Durchführung einer Reihe von Tests bereitstellen.

### Staging   {#staging}

Die Staging-Umgebung sollte ein Spiegel der Produktionsumgebung sein - Konfiguration, Code und Inhalt:

* Sie wird zum Testen von Skripten verwendet, die zur Umsetzung der eigentlichen Bereitstellung genutzt werden.
* Sie kann für endgültige Tests (Design, Funktionalität und Schnittstellen) vor der Bereitstellung in den Produktionsumgebungen verwendet werden.
* Obwohl es nicht immer möglich ist, die Staging-Umgebung völlig identisch mit der Produktionsumgebung zu gestalten, sollten die beiden so ähnlich wie möglich sein, um Leistungs- und Belastungstests zu ermöglichen.

### Produktion - Autoren- und Veröffentlichungsumgebung   {#production-author-and-publish}

Die Produktionsumgebung besteht aus den Umgebungen, in denen [Autoren- und Veröffentlichungsinstanz](/help/sites-cloud/authoring/getting-started/concepts.md) Ihre Implementierung.

Eine Produktionsumgebung besteht aus mindestens einer Autoreninstanz und einer Veröffentlichungsinstanz:

* [Autoreninstanz](#author) für die Eingabe von Inhalt;
* [Veröffentlichungsinstanz](#publish) für Inhalte, die den Besuchern/Benutzern zugänglich gemacht werden.

Je nach Größe des Projekts besteht es oft aus mehreren Autoren, Herausgebern oder beidem. Auf niedrigerer Ebene kann das Repository in mehrere Instanzen gebündelt werden.

#### Autor {#author}

Normalerweise befinden sich Autoreninstanzen hinter der internen Firewall. Diese interne Firewall ist die Umgebung, in der Sie und Ihre Kollegen Bearbeitungsaufgaben ausführen, z. B. die folgenden:

* Verwalten des gesamten Systems;
* Eingeben von Inhalten;
* Konfigurieren des Layouts und Designs des Inhalts;
* Aktivieren der Inhalte in der Veröffentlichungsumgebung.

Aktivierte Inhalte werden gebündelt und in der Replikationswarteschlange der Autorenumgebung abgelegt. Der Replikationsprozess überträgt den Inhalt dann in die Veröffentlichungsumgebung.

Um in einer Veröffentlichungsumgebung generierte Daten rückgängig zu machen, fragt ein Replikations-Listener in der Autorenumgebung die Veröffentlichungsumgebung ab und ruft diese Inhalte aus dem Postausgang für die Rückwärtsreplikation der Veröffentlichungsumgebung ab.

#### Veröffentlichen  {#publish}

Normalerweise befindet sich eine Veröffentlichungsumgebung in der &quot;DMZ (Demilitarisierte Zone)&quot;. In dieser Umgebung greifen Besucher auf Ihren Inhalt zu (z. B. über eine Website oder eine Mobile App) und interagieren mit ihm, sei es öffentlich oder in Ihrem Intranet. Die Veröffentlichungsumgebung:

* enthält alle aus der Autorenumgebung replizierten Inhalte;
* macht Inhalte für Besucher zugänglich;
* speichert Benutzerdaten, die von den Besuchern erstellt werden, wie Kommentare oder andere Formen von Beiträgen;
* kann so konfiguriert werden, dass solche Benutzerdaten einem Postausgang für die umgekehrte Replikation in die Autorenumgebung hinzugefügt werden.

Die Veröffentlichungsumgebung erzeugt Ihren Inhalt dynamisch in Echtzeit und der Inhalt kann für jeden einzelnen Benutzer personalisiert werden.

## Code-Verschiebung   {#code-movement}

Übergeben Sie Code immer von unten nach oben:

* Der Code wird zunächst in der lokalen Umgebung entwickelt und dann in die Entwicklungsumgebungen integriert,
* gefolgt von gründlichen Tests in den QS-Umgebungen
* und wird dann abermals in den Staging-Umgebungen getestet.
* Der Code sollte erst danach in den Produktionsumgebungen bereitgestellt werden.

Normalerweise wird der Code (z. B. benutzerdefinierte Webanwendungsfunktionen und Designvorlagen) durch den Export und Import von Paketen zwischen den verschiedenen Inhalts-Repositorys übertragen. Wo angemessen, kann die Replikation als automatischer Prozess konfiguriert werden.

Projekte zur Bereitstellung von Trigger-Code AEM as a Cloud Service häufig:

* Automatisch: zur Übertragung an die Entwicklungs- und QS-Umgebungen.
* Manuell: Bereitstellungen in den Staging- und Produktionsumgebungen erfolgen kontrollierter, häufig manuell. bei Bedarf jedoch auch Automatisierung möglich ist.

![Code-Verschiebung](assets/code-movement.png)

## Inhaltsverschiebung {#content-movement}

Inhalte, die für die Produktion erstellt werden, sollten **immer** in der Autoreninstanz der Produktion verfasst werden.

Der Inhalt sollte nicht der Codeverschiebung von niedrigeren Umgebungen zu höheren Umgebungen folgen. Es empfiehlt sich also nicht, Inhalte auf lokalen Computern oder in niedrigeren Umgebungen zu erstellen und sie dann in die Produktionsumgebung zu verschieben. Der Grund dafür ist, dass es zu Fehlern und Inkonsistenzen führen kann.

Die Produktionsinhalte sollten von der Produktionsumgebung in die Staging-Umgebung verschoben werden, um zu gewährleisten, dass die Staging-Umgebung eine effiziente und genaue Testumgebung bietet.

>[!NOTE]
>
>Diese Methode bedeutet nicht, dass Staging-Inhalte kontinuierlich mit der Produktion synchronisiert werden müssen. regelmäßige Aktualisierungen sind ausreichend, insbesondere vor dem Testen einer neuen Iteration des Codes. Inhalte in den QS- und Entwicklungsumgebungen müssen nicht so häufig aktualisiert werden. Es muss nur eine gute Darstellung des Produktionsinhalts sein.

Inhalt kann übertragen werden:

* zwischen verschiedenen Umgebungen - durch den Export und Import von Paketen;
* Zwischen verschiedenen Instanzen - durch direktes Replizieren (AEM as a Cloud Service Replikation) des Inhalts (mithilfe einer HTTP- oder HTTPS-Verbindung).

![Inhaltsverschiebung](assets/content-movement.png)
