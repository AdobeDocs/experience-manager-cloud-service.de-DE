---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.8.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.8.0
feature: Versionshinweise
exl-id: 70674e16-f9ba-4777-98fe-34161e90a481
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: ht
source-wordcount: '425'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.8.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.8.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. August 2020 veröffentlicht.

## Neue Funktionen {#whats-new-cloud-manager}

* Content Audit ist eine Funktion, die in den Produktions-Pipelines von Cloud Manager Sites aktiviert ist. Die Konfiguration der Produktions-Pipeline für Programm mit Sites enthält jetzt eine dritte Registerkarte mit dem Namen **Content Audit**. Bei jeder Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests ein neuer Content Audit-Schritt in die Pipeline aufgenommen, der die Site anhand einer Reihe von Dimensionen wie Leistung, SEO (Suchmaschinenoptimierung), Barrierefreiheit, Best Practices und PWA (Progressive Web App) bewertet.


   >[!NOTE]
   >Content Audit wurde inzwischen in Experience Audit umbenannt.

   Weitere Informationen finden Sie unter [Experience Audit-Tests](/help/implementing/cloud-manager/experience-audit-testing.md).

* Neu erstellte Umgebungen in Assets-Programmen werden jetzt automatisch mit Smart Content Services konfiguriert.

* Der Ruhezustand von im Ruhezustand befindlichen Umgebungen kann auf der Seite **Überblick** von Cloud Manager aufgehoben werden.

* Möglichkeit zur Durchführung von Erlebnisprüfungen auf Seiten, die über Google Lighthouse bereitgestellt werden. Als Teil der Cloud Manager-Pipeline können bis zu 25 Seiten anhand von Erlebnis-KPIs geprüft und validiert werden. Die Bewertungen werden in der Cloud Manager-Benutzeroberfläche angezeigt.

### Fehlerbehebungen {#bug-fixes-cm}

* Einige unnötige und unerwünschte SonarQube-Plug-ins wurden im Rahmen der Überprüfung der Code-Qualität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Verzweigungsname falsch formatiert.

* In einigen Fällen wurden abgeschlossene Pipeline-Ausführungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Ausführungen der Pipeline verhindert wurden.

* Pipeline-Ausführungen blieben gelegentlich aufgrund interner Kommunikationsprobleme *stecken*.

* Bei der Bereitstellung einer neuen Organisation erhielten einige Benutzer mit anderen administrativen Rollen als Systemadministratoren fälschlicherweise Zugriff auf Cloud Manager.

* Unter bestimmten Umständen wurde der Vorgang zur Indexaktualisierung mehrmals parallel gestartet, was zu einem Implementierungsfehler führte.

* Die QuickInfo auf den Programmkarten war nicht immer korrekt.

* Die Benutzeroberfläche erlaubte fälschlicherweise, dass Vorgänge in einer Umgebung gestartet wurden, während sie gelöscht wurde.

* Auf der **Übersichtsseite von Cloud Manager** traten Farbabweichungen auf.

### Bekannte Probleme {#known-issues-cm}

* Es sind ungültige Seiten enthalten, die den Content Audit-Durchschnittswert unter den erwarteten Wert bringen.

* Auf der Registerkarte „Content Audit“ wird die Basis-URL unter Verwendung der Autoren-Domain anstelle der Veröffentlichungs-Domain falsch angezeigt.

* Um den Schritt „Content Audit“ zu aktivieren, müssen Benutzer die Pipeline bearbeiten und optional Seiten hinzufügen. Wenn keine Seiten hinzugefügt werden, wird die Homepage geprüft.
