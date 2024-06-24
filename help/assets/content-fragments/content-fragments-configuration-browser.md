---
title: Inhaltsfragmente – Konfigurations-Browser (Assets – Inhaltsfragmente)
description: Erfahren Sie, wie Sie Inhaltsfragmentfunktionen im Konfigurations-Browser aktivieren.
exl-id: 9fc911de-1d33-4811-8f58-ea21ce94bedb
feature: Content Fragments
role: User, Admin, Developer
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 100%

---

# Inhaltsfragmente – Konfigurations-Browser{#content-fragments-configuration-browser}

Erfahren Sie, wie Sie bestimmte Inhaltsfragmentfunktionen im Konfigurations-Browser aktivieren, um die leistungsstarken Funktionen von AEM für die Headless-Bereitstellung zu nutzen.

## Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz {#enable-content-fragment-functionality-instance}

Bevor Sie Inhaltsfragmente verwenden können, müssen Sie den **Konfigurations-Browser** verwenden, um Folgendes zu aktivieren:

* **Inhaltsfragmentmodelle** – obligatorisch
* **GraphQL: Beständige Abfragen** – optional

>[!CAUTION]
>
>Wenn Sie **Inhaltsfragmentmodelle** nicht aktivieren:
>
>* ist die Option **Erstellen** nicht zum Erstellen von Modellen verfügbar.
>* können Sie nicht [die Sites-Konfiguration auswählen, um den entsprechenden Endpunkt zu erstellen](/help/headless/graphql-api/graphql-endpoint.md).

Um die Funktion für Inhaltsfragmente zu aktivieren, müssen Sie die folgenden Schritte ausführen:

* Aktivieren Sie die Verwendung der Inhaltsfragmentfunktionen im Konfigurationsbrowser.
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an.

### Aktivieren der Funktionen für Inhaltsfragmente im Konfigurations-Browser {#enable-content-fragment-functionality-in-configuration-browser}

Um bestimmte [Inhaltsfragment-Funktionen](#creating-a-content-fragment-model) zu nutzen, **müssen** Sie diese zunächst über den **Konfigurations-Browser** aktivieren:

>[!NOTE]
>
>Siehe [Konfigurations-Browser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

>[!NOTE]
>
>[Unterkonfigurationen](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (eine Konfiguration, die in einer anderen Konfiguration verschachtelt ist) werden vollständig zur Verwendung mit Inhaltsfragmenten, Inhaltsfragmentmodellen und GraphQL-Abfragen unterstützt.
>
>Beachten Sie Folgendes:
>
>
>* Nach dem Erstellen von Modellen in einer Unterkonfiguration ist es NICHT möglich, das Modell in eine andere Unterkonfiguration zu verschieben oder zu kopieren.
>
>* Ein GraphQL-Endpunkt basiert (weiterhin) auf einer übergeordneten (Stamm-)Konfiguration.
>
>* Persistierte Abfragen werden (weiterhin) gespeichert und sind für die übergeordnete (Stamm-)Konfiguration relevant.


1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann den **Konfigurations-Browser**.

1. Öffnen Sie über **Erstellen** das Dialogfeld, in dem Sie:

   1. einen **Titel** angeben,
   1. Der **Name** wird zum Knotennamen im Repository.
      * Er wird automatisch auf der Grundlage des Titels generiert und gemäß den [AEM-Benennungskonventionen](/help/implementing/developing/introduction/naming-conventions.md) angepasst.
      * Sie können sie bei Bedarf anpassen.
   1. Um ihre Verwendung zu aktivieren, wählen Sie
      * **Inhaltsfragmentmodelle**
      * **GraphQL – Persistente Abfragen**

      ![Konfiguration definieren](assets/cfm-conf-01.png)

1. Wählen Sie **Erstellen** aus, um die Definition zu speichern.

<!-- 1. Select the location appropriate to your website. -->

### Anwenden der Konfiguration auf Ihren Assets-Ordner {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **Global** für die Inhaltsfragmentfunktionalität aktiviert ist, gilt sie für jeden Assets-Ordner.

Um andere Konfigurationen (d. h. nicht global) mit einem vergleichbaren Assets-Ordner zu verwenden, müssen Sie die Verbindung definieren. Diese Verbindung erfolgt durch Auswahl der entsprechenden **Konfiguration** auf der Registerkarte **Cloud Services** der **Ordnereigenschaften** des entsprechenden Ordners.

![Konfiguration anwenden](assets/cfm-conf-02.png)
