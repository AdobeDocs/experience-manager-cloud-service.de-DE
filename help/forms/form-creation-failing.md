---
title: Wie kann ich Fehler bei der Formularerstellung beheben?
description: Fehlerbehebung bei Fehlern bei der Formularerstellung in der as a Cloud Service AEM Forms-Umgebung.
feature: Adaptive Forms, Troubleshooting
role: User
source-git-commit: 23491130b44147753c5b98f316be5a9e5937afea
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 5%

---

# Problem beim Veröffentlichen von Formularen{#form-creation-fails}

Nach der Aktualisierung auf die as a Cloud Service AEM Forms-Version `2024.5.16461`:

**Einige Benutzer** kann beim Erstellen von Formularen ein Problem auftreten, sodass beim Erstellen eines Formulars die folgende Fehlermeldung im Erstellungsdialogfeld angezeigt wird:

`A server error occurred. Try again after sometime.`

## Ursache {#cause-form-creation-fails}

Das Problem tritt auf, weil der Autor das Formular ohne **erste Veröffentlichung der Vorlage** verwendet. Dies führt dazu, dass die `jcr:uuid` und anderen geschützten und systemgenerierten Eigenschaften an die `<template-path>/initial/jcr:content` -Knoten, der bei der nachfolgenden Formularerstellung zu Fehlern führt.

## Problemumgehung {#resolution-form-creation-fails}

Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

1. Stellen Sie sicher, dass die Vorlage, die Sie im Formular verwenden, nicht über die `jcr:uuid` und anderen systemgenerierten geschützten Eigenschaften im Pfad `<template-path>/initial/jcr:content node`.
1. Veröffentlichen Sie die Vorlage explizit mithilfe der Vorlagenkonsole.
1. Versuchen Sie jetzt, nach der Veröffentlichung Ihrer Vorlage neue Formulare mithilfe der Vorlage zu erstellen.
1. Wenn die von Ihnen verwendete Vorlage in zukünftigen Versionen aktualisiert wurde, veröffentlichen Sie die Vorlage erneut (wie in Schritt 2 beschrieben), um Probleme bei der Formularerstellung zu vermeiden.


<!--

# Issue {#form-creation-fails}

After updating to AEM Forms as a Cloud Service version `2024.5.16461.20240524T172309Z`, When a user publishes a form using an unpublished template, it fails to create a form and shows an error:

`Property is protected: jcr:uuid = 09e0d6be-f619-4405-b021-27eb1c5326d3`

## Solution {#troubleshoot-form-creation-fails}

To resolve the issue, perform the following workaround steps:

1. Publish the template explicitly using the template console.
    
    >[!NOTE]
    > Prior to this step ensure that the (unpublished) template does not have `jcr:uuid` and other system generated properties under the initial content's `jcr:content node`. To sort out it, first, sanitize the template to publish it explicitly.

    >[!NOTE]
    > This action doesn't replicate the initial content node.
1. Now, when your template is published, try creating new forms using the template.
1. If the template is changed in the future, publish it again as mentioned in the step 1.

-->










