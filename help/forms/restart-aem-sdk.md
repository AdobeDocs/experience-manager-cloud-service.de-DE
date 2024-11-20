---
title: Neustarten des AEM SDK
description: Best Practices für den Neustart des AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 5fec2a93-1dda-4240-8690-24a6afae5c2b
source-git-commit: 62be3c6e98df9002cdfbeef50dd5475c4daa1576
workflow-type: ht
source-wordcount: '107'
ht-degree: 100%

---

# Neustarten des AEM SDK

Wenn Sie das AEM SDK neu starten, indem Sie die Java™-Prozesse stoppen, kann dies zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen. Es tritt ein Fehler wie der folgende auf:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Fehler beim AEM SDK-Neustart](/help/forms/assets/restart-sdk-error.png)

## Lösung

Wechseln Sie zum aktiven Befehlsfenster und drücken Sie die Tastenkombination `Ctrl + C`, um das AEM SDK neu zu starten.

Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mithilfe alternativer Methoden, z. B. durch Beenden von Java™-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

## Siehe auch

* [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md)
* [Aktivieren der Kernkomponenten für adaptive Formulare](/help/forms/enable-adaptive-forms-core-components.md)
