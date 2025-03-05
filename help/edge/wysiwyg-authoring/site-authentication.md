---
title: Konfigurieren der Site-Authentifizierung für die Inhaltserstellung
description: Erfahren Sie, wie AEM Live die Token-basierte Authentifizierung unterstützt und wie Sie AEM so konfigurieren können, dass die Authentifizierung mit WYSIWYG Authoring verwendet wird.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: b2838da2-79c7-49b1-a101-15c21e80197e
source-git-commit: 7b46af35b202446fdea67e4125d74c3965d302d9
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 2%

---

# Konfigurieren der Site-Authentifizierung für die Inhaltserstellung {#site-authentication}

Erfahren Sie, wie AEM Live die Token-basierte Authentifizierung unterstützt und wie Sie AEM so konfigurieren können, dass die Authentifizierung mit WYSIWYG Authoring verwendet wird.

## Überblick {#overview}

AEM Live unterstützt die Token-basierte Authentifizierung. Die Site-Authentifizierung wird normalerweise sowohl auf die Vorschau- als auch auf die Veröffentlichungs-Site angewendet, kann aber auch so konfiguriert werden, dass nur eine der Sites einzeln geschützt wird.

>[!NOTE]
>
>Wenn Sie die Site-Authentifizierung aktivieren möchten, müssen Sie sie auch in Ihren AEM-Authoring-Umgebungen konfigurieren

## Voraussetzungen {#requirements}

Um die Site-Authentifizierung für die Verwendung mit der Inhaltserstellung zu konfigurieren, müssen Sie zunächst die folgenden Aufgaben ausführen:

* In diesem Dokument wird davon ausgegangen, dass Sie bereits eine Site für Ihr Projekt auf der Grundlage des [Entwicklerhandbuchs Erste Schritte für das WYSIWYG-Authoring mit Edge Delivery Services&quot; erstellt haben](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)
* Sie müssen die [-Funktion bereits für Ihr Projekt aktiviert haben.](/help/edge/wysiwyg-authoring/repoless.md)

## Konfigurieren der Site-Authentifizierung {#configure-authentication}

Weitere Informationen zum Konfigurieren der [ finden Sie ](https://www.aem.live/docs/authentication-setup-site) Dokument „Konfigurieren der Site-Authentifizierung“.

Beachten Sie bei der Konfiguration der Authentifizierung die folgenden Informationen:

* Die ID des technischen Kontos
* Ihr Site-Authentifizierungstoken

Diese Elemente sind erforderlich, um die Konfiguration der Site-Authentifizierung für Ihre AEM-Authoring-Umgebung abzuschließen.

## Konfigurieren der Authoring-Umgebung {#authoring-environment}

Sobald die Site-Authentifizierung konfiguriert ist, können Sie sie in Ihrer AEM-Authoring-Umgebung aktivieren.

1. Melden Sie sich bei der AEM-Autoreninstanz an, wechseln Sie zu **Tools** -> **Cloud Services** -> **Edge Delivery Services-** und wählen Sie die automatisch für Ihre Site erstellte Konfiguration aus und tippen oder klicken Sie auf **Eigenschaften** in der Symbolleiste.
1. Wählen Sie im Fenster **Edge Delivery Services** Konfiguration die Registerkarte **Authentifizierung** und geben Sie das **Site Authentication Token** ein, das Sie zuvor kopiert haben.

   ![Edge Delivery Services-Konfiguration](/help/edge/wysiwyg-authoring/assets/site-authentication/configure-aem-author.png)

1. Stellen Sie sicher, dass **Die ID des technischen Kontos** mit der zuvor kopierten ID übereinstimmt.

   * Dieses Feld ist schreibgeschützt und vordefiniert.
   * Das technische Konto ist für alle Sites in einer einzigen AEM-Autorenumgebung gleich.

1. Tippen oder klicken Sie auf **Speichern und schließen**.
