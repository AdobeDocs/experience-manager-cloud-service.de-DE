---
title: Warten eines AEM-Connectors
description: Erfahren Sie, wie Sie Ihren AEM-Connector nach der ersten Übermittlung aktualisieren.
exl-id: 8122a8c8-6577-4907-8f6e-52711eed3970
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 86%

---

Warten eines AEM-Connectors
============================

In diesem Artikel finden Sie nützliche Informationen zum Warten von AEM-Connectoren. Lesen Sie diese zusammen mit den Artikeln zum [Implementieren](implement.md) und [Übermitteln](submit.md) von Connectoren.

Selbst nach der ersten Übermittlung kann es für einen Partner Gründe geben, seinen AEM-Connector zu aktualisieren, entweder aufgrund der Einführung einer neuen AEM-Version oder unabhängig davon, etwa um Funktionen zu ergänzen oder Fehler zu beheben. In diesem Artikel wird das Verfahren für beide Szenarien erläutert und außerdem das typische Vorgehen eines Kunden zum Überprüfen von Connectoren bei einem Upgrade von AEM beschrieben.

AEM as a Cloud Service-Anwendungen werden täglich durch AEM-Wartungs-Patches aktualisiert. Größere Änderungen werden monatlich im Rahmen von Feature-Releases aktiviert. Auch wenn AEM-Updates grundsätzlich abwärtskompatibel sein und somit die Ausführung von Anwendungen nicht beeinträchtigen sollten, wird Anbietern empfohlen, regelmäßig zu überprüfen, ob sich ihre Connectoren erwartungsgemäß verhalten. Der Zugriff auf ein AEM Programm/eine Umgebung wird vom Partnerteam bestimmt.
