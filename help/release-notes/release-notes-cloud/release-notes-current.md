---
title: Versionshinweise für die Version 2020.8.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.8.0.'
translation-type: tm+mt
source-git-commit: 85f5262c2af7502e98fcb60b51b9b13d2c2c0f2c
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 8%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.8.0 beschrieben.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neuerungen {#what-is-new-commerce}

* Die Funktion Produktkonsole ist jetzt verfügbar. Auf diese Weise können Marketingexperten/Autoren in AEM Ansicht und Navigation in Kategorien und Produkten durchführen, die im Commerce-Backend gespeichert sind. Support for properties for catogories and products in the Product Console also provided.

* Produkt- und Kategorie-Picker wurden verbessert, damit Marketingexperten Produkte über SKU auswählen oder Kategorien über Kategorien-ID auswählen können.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 06. August 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Content Audit ist eine Funktion, die auf den Produktionslinien der Cloud Manager-Sites aktiviert ist. Die Konfiguration der Produktionspipeline für Programm mit Sites enthält jetzt eine dritte Registerkarte mit dem Namen **Content Audit**. Bei jeder Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests ein neuer Content-Audit-Schritt in die Pipeline aufgenommen, der die Site anhand einer Reihe von Dimensionen wie Leistung, SEO (Suchmaschinenoptimierung), Barrierefreiheit, Best Practices und PWA (Progressive Web App) bewertet.

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* Neu erstellte Umgebung in Assets-Programmen werden jetzt automatisch mit Smart Content Services konfiguriert.

* Hibernated-Umgebung können auf der Seite &quot; **Übersicht** &quot;von Cloud Manager entfernt werden.

* Authentifizierungsgebundene private Maven-Repositorys werden jetzt unterstützt.

### Fehlerbehebungen {#bug-fixes-cm}

* Einige unnötige und unerwünschte SonarQube-Plugins wurden im Rahmen der Überprüfung der Codequalität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Zweigname falsch formatiert.

* In einigen Fällen wurden abgeschlossene Pipeline-Hinrichtungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Hinrichtungen der Pipeline verhindert wurden.

* Hinrichtungen von Pipeline würden gelegentlich aufgrund interner Kommunikationsprobleme *feststecken* .

* Bei der Bereitstellung einer neuen Organisation erhielten einige Benutzer mit Administratorrollen, die keine Systemadministratoren waren, fälschlicherweise Zugriff auf Cloud Manager.

* Unter bestimmten Umständen wurde der Aktualisierungsindexauftrag mehrmals parallel gestartet, was zu einem Bereitstellungsfehler führte.

* Die QuickInfo auf den Programm-Karten waren nicht einheitlich korrekt.

* Die Benutzeroberfläche erlaubte irrtümlicherweise den Versuch, Vorgänge auf einer Umgebung auszuführen, während diese gelöscht wurde.

* Auf der Seite &quot; **Übersicht** &quot;des Cloud-Managers wurde eine Farbabweichung festgestellt.

### Bekannte Probleme {#known-issues-cm}

* Es sind ungültige Seiten enthalten, die die durchschnittliche Inhaltsprüfung unter den gewünschten Werten bringen.

* Auf der Registerkarte &quot;Content Audit&quot;wird die Basis-URL fälschlicherweise unter Verwendung der Autorendomäne anstelle der Veröffentlichungsdomäne angezeigt.

* Um den Schritt &quot;Content Audit&quot;zu aktivieren, müssen Benutzer die Pipeline bearbeiten und optional Seiten hinzufügen. Wenn keine Seiten hinzugefügt werden, wird die Homepage geprüft.

