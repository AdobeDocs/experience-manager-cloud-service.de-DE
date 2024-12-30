---
title: AEM as a Cloud Service in Unified Shell
description: Erfahren Sie mehr über die Vorteile von AEM as a Cloud Service in Unified Shell
exl-id: ea739307-dc99-4621-a239-dbe60ab6b52e
feature: Release Information
role: Admin
source-git-commit: 55cf6a10c2cb4c62aa8f89fac7f9d1fb4c012d26
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 100%

---

# AEM as a Cloud Service in Unified Shell {#aem-as-a-cloud-service-on-unified-shell}

## Überblick {#overview}

AEM as a Cloud Service (Author Service) ist in Unified Shell integriert, um das Benutzererlebnis zu verbessern und es mit allen anderen Experience Cloud-Programmen zu vereinheitlichen. Die Auswirkungen dieser Integration sind wie unten dargestellt in der oberen Kopfzeile des Programms zu sehen.

![Grafik](/help/overview/assets/unifiedshell_header.png)

Die Vorteile sind:

* Single-Sign-on für alle Experience Cloud-Programme
* Einfacher Wechsel zwischen Organisationen und Programmen
* Verbesserte Produkthilfe
* Einfache Feedback-Schaltfläche im Produkt, mit der Probleme gemeldet oder Ideen mit Adobe geteilt werden können
* Zugriff auf globale Produktankündigungen und Benachrichtigungen zusätzlich zu Benachrichtigungen, die speziell für AEM as a Cloud Service gelten

## Deaktivieren von Unified Shell {#disabling-unified-shell}

Standardmäßig ist Unified Shell in AEM as a Cloud Service aktiviert. Wenn die obere Kopfzeile jedoch angepasst wurde, wird empfohlen, Unified Shell zu deaktivieren, um Probleme mit den Anpassungen zu vermeiden. Gehen Sie wie folgt vor, um Unified Shell zu deaktivieren:

>[!NOTE]
>Unified Shell kann nur durch ein Konto mit Administratorrechten deaktiviert werden.

1. Klicken Sie auf **Tools > Cloud Services**.

   Admins sehen die Karte der Unified Shell-Konfiguration wie folgt:

   ![Bild](/help/overview/assets/unifiedshell2.png)

1. Klicken Sie auf **Unified Shell-Konfiguration**. Deaktivieren Sie dann das unten dargestellte Kontrollkästchen, um Unified Shell zu deaktivieren:

   ![Grafik](/help/overview/assets/unifiedshell3.png)

>[!NOTE]
>
>Unified Shell kann auch über Ihren Projekt-Code deaktiviert werden. Siehe [Struktur der AEM-UI - Unified Shell](/help/implementing/developing/introduction/ui-structure.md#unified-shell).

## Wechseln zum dunklen Design {#changing-to-dark-theme}

Um zum dunklen Design zu wechseln, klicken Sie auf Ihr Profilsymbol. Diese Aktion zeigt ein Popover-Fenster an, wie unten dargestellt. Mit dem Umschalter können Sie zu einem dunklen Design für Unified Shell wechseln.

>[!INFO]
>
>Das dunkle Design gilt nur für Unified Shell (die obere Leiste).

![Grafik](/help/overview/assets/unifiedshell4.png)

## Identifizieren der AEM as a Cloud Service-Umgebung {#identify-aemaacs-environment}

AEM as a Cloud Service bietet drei Umgebungstypen: Produktion, Staging und Entwicklung. Weitere Informationen finden Sie unter [Umgebungstypen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=de). Bei dieser Integration mit Unified Shell wird der Umgebungstyp, in dem ein Benutzer bzw. eine Benutzerin beim Autoren-Service angemeldet ist, in der oberen Leiste in einem Feld dargestellt (siehe unten).

![Grafik](/help/overview/assets/unifiedshell_header_label.png)

## Zugriff auf den AEM-Posteingang {#accessing-the-aem-inbox}

Der AEM-Posteingang kann durch Klicken auf das Glockensymbol in Unified Shell aufgerufen werden.

>[!INFO]
>
> Die auf dem Glockensymbol angegebene Zahl bezeichnet die ungelesenen Benachrichtigungen in allen Lösungen innerhalb einer IMS-Organisation und die im AEM-Posteingang aufgelisteten Aufgaben.

![Grafik](/help/overview/assets/unifiedshell5.png)

Klicken Sie im Popover-Fenster auf die Schaltfläche „Posteingang“, damit Sie zu Ihrem AEM-Posteingang wechseln können:

![Bild](/help/overview/assets/unifiedshell6.png)

