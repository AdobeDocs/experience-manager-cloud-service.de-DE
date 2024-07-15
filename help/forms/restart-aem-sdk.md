---
title: Wie kann AEM SDK neu gestartet werden?
description: Best Practices für den Neustart AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 5fec2a93-1dda-4240-8690-24a6afae5c2b
source-git-commit: 62be3c6e98df9002cdfbeef50dd5475c4daa1576
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 27%

---

# Neustart des AEM SDK

Wenn Sie das AEM SDK neu starten, indem Sie die Java™-Prozesse stoppen, kann dies zu Inkonsistenzen in der AEM Entwicklungsumgebung führen. Es tritt ein Fehler auf, wie:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Neustart-aem-sdk-error](/help/forms/assets/restart-sdk-error.png)

## Lösung

Um das AEM SDK neu zu starten, wechseln Sie zum aktiven Befehlsfenster und drücken Sie den Befehl `Ctrl + C` , um das SDK neu zu starten.

Es wird empfohlen, den Befehl „Strg + C“ zu verwenden, um das SDK neu zu starten. Das Neustart des AEM SDK mithilfe alternativer Methoden, z. B. das Beenden von Java™-Prozessen, kann zu Inkonsistenzen in der AEM Entwicklungsumgebung führen.

## Siehe auch

* [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md)
* [Aktivieren der Kernkomponenten für adaptive Formulare](/help/forms/enable-adaptive-forms-core-components.md)
