---
title: Warten eines AEM-Connectors
description: Erfahren Sie, wie Sie Ihren AEM-Connector nach der ersten Übermittlung verwalten und aktualisieren können.
exl-id: 8122a8c8-6577-4907-8f6e-52711eed3970
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 100%

---

Warten eines AEM-Connectors
============================

In diesem Artikel finden Sie nützliche Informationen zum Warten von AEM-Connectoren. Lesen Sie diese zusammen mit den Artikeln zum [Implementieren](implement.md) und [Übermitteln](submit.md) von Connectoren.

Selbst nach der ersten Übermittlung kann es für einen Partner Gründe geben, seinen AEM-Connector zu aktualisieren, entweder aufgrund der Einführung einer neuen AEM-Version oder unabhängig davon, etwa um Funktionen zu ergänzen oder Fehler zu beheben. In diesem Artikel wird das Verfahren für beide Szenarien erläutert und außerdem das typische Vorgehen eines Kunden zum Überprüfen von Connectoren bei einem Upgrade von AEM beschrieben.

AEM as a Cloud Service-Anwendungen werden täglich durch AEM-Wartungs-Patches aktualisiert. Größere Änderungen werden monatlich im Rahmen von Feature-Releases aktiviert. Auch wenn AEM-Updates grundsätzlich abwärtskompatibel sein und somit die Ausführung von Anwendungen nicht beeinträchtigen sollten, wird Anbietern empfohlen, regelmäßig zu überprüfen, ob sich ihre Connectoren erwartungsgemäß verhalten. Der Zugriff auf ein AEM-Programm/eine AEM-Umgebung wird vom Partner-Team festgelegt.
