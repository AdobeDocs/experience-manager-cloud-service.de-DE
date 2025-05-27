---
title: Konfigurieren der Site-Authentifizierung für die Inhaltserstellung
description: Erfahren Sie, wie AEM Live die Token-basierte Authentifizierung unterstützt und wie Sie AEM so konfigurieren können, dass die Authentifizierung mit WYSIWYG-Authoring verwendet wird.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: b2838da2-79c7-49b1-a101-15c21e80197e
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '324'
ht-degree: 100%

---

# Konfigurieren der Site-Authentifizierung für die Inhaltserstellung {#site-authentication}

Erfahren Sie, wie AEM Live die Token-basierte Authentifizierung unterstützt und wie Sie AEM so konfigurieren können, dass die Authentifizierung mit WYSIWYG-Authoring verwendet wird.

## Überblick {#overview}

AEM Live unterstützt die Token-basierte Authentifizierung. Die Site-Authentifizierung wird normalerweise sowohl auf die Vorschau- als auch auf die Veröffentlichungs-Site angewendet, kann aber auch so konfiguriert werden, dass nur eine der Sites einzeln geschützt wird.

>[!NOTE]
>
>Wenn Sie die Site-Authentifizierung aktivieren möchten, müssen Sie sie auch in Ihren AEM-Authoring-Umgebungen konfigurieren.

## Voraussetzungen {#requirements}

Um die Site-Authentifizierung für die Inhaltserstellung zu konfigurieren, müssen Sie zunächst die folgenden Aufgaben ausführen:

* In diesem Dokument wird vorausgesetzt, dass Sie bereits eine Site für Ihr Projekt auf Grundlage des [Erste-Schritte-Handbuchs für Entwickelnde zum WYSIWYG-Authoring mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) erstellt haben.
* Sie müssen die [Funktion zum Einrichten ohne Repository bereits für Ihr Projekt aktiviert](/help/edge/wysiwyg-authoring/repoless.md) haben.

## Konfigurieren der Site-Authentifizierung {#configure-authentication}

Weitere Informationen zum Konfigurieren der Site-Authentifizierung finden Sie im Dokument [Konfigurieren der Site-Authentifizierung](https://www.aem.live/docs/authentication-setup-site?lang=de#).

Notieren Sie sich beim Konfigurieren der Authentifizierung die folgenden Informationen:

* ID des technischen Kontos
* Site-Authentifizierungs-Token

Diese Elemente sind erforderlich, um die Konfiguration der Site-Authentifizierung für Ihre AEM-Authoring-Umgebung abzuschließen.

## Konfigurieren der Authoring-Umgebung {#authoring-environment}

Sobald die Site-Authentifizierung konfiguriert ist, können Sie sie in Ihrer AEM-Authoring-Umgebung aktivieren.

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **Tools** -> **Cloud Services** -> **Edge Delivery Services-Konfiguration**. Wählen Sie die automatisch für Ihre Site erstellte Konfiguration aus und tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Wählen Sie im Fenster **Edge Delivery Services-Konfiguration** die Registerkarte **Authentifizierung** aus und geben Sie das zuvor notierte **Site-Authentifizierungs-Token** an.

   ![Edge Delivery Services-Konfiguration](/help/edge/wysiwyg-authoring/assets/site-authentication/configure-aem-author.png)

1. Stellen Sie sicher, dass die **ID des technischen Kontos** mit der zuvor notierten ID übereinstimmt.

   * Dieses Feld ist schreibgeschützt und vordefiniert.
   * Das technische Konto ist für alle Sites einer AEM-Autorenumgebung gleich.

1. Tippen oder klicken Sie auf **Speichern und schließen**.
