---
title: Wie können Fehler bei der Formularerstellung behoben werden?
description: Fehlerbehebung bei Fehlern bei der Formularerstellung in der AEM Forms as a Cloud Service-Umgebung.
feature: Adaptive Forms
role: User
exl-id: 169ea727-0941-4a1d-bc33-d9fe208b27ab
source-git-commit: 0b693cb51a96011235fa87a5899426c6b0c2509a
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 5%

---

# Problem beim Veröffentlichen von Formularen{#form-creation-fails}

Nach dem Update auf AEM Forms as a Cloud Service Version `2024.5.16461`:

**Bei einigen Benutzern** beim Erstellen von Formularen möglicherweise Probleme auftreten. Wenn ein Benutzer ein Formular erstellt, wird im Dialogfeld zum Erstellen die folgende Fehlermeldung angezeigt:

`A server error occurred. Try again after sometime.`

## Ursache {#cause-form-creation-fails}

Das Problem tritt auf, weil der Autor das Formular veröffentlicht, ohne **darin verwendete Vorlage** veröffentlichen. Dadurch werden die `jcr:uuid` und andere geschützte und systemgenerierte Eigenschaften zum `<template-path>/initial/jcr:content` hinzugefügt, was zu Fehlern bei der nachfolgenden Formularerstellung führt.

## Problemumgehung {#resolution-form-creation-fails}

Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

1. Stellen Sie sicher, dass die Vorlage, die Sie im Formular verwenden, nicht die `jcr:uuid` und andere systemgenerierte geschützte Eigenschaften am `<template-path>/initial/jcr:content node` hat.
1. Publish verwendet die Vorlage explizit in der Vorlagenkonsole.
1. Versuchen Sie jetzt nach der Veröffentlichung Ihrer Vorlage, neue Formulare mithilfe der Vorlage zu erstellen.
1. Wenn die von Ihnen verwendete Vorlage in zukünftigen Versionen aktualisiert wird, führen Sie die Publish-Vorlage erneut aus (wie in Schritt 2 angegeben), um Probleme mit der Formularerstellung zu vermeiden.


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
