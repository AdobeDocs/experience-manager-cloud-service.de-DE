---
title: Inhaltsfragmente – Konfigurations-Browser
description: Erfahren Sie, wie Sie bestimmte Inhaltsfragmentfunktionen im Konfigurationsbrowser aktivieren können, um AEM leistungsstarken Funktionen für kostenlose Versand zu nutzen.
feature: Inhaltsfragmente
role: Business Practitioner
exl-id: 9fc911de-1d33-4811-8f58-ea21ce94bedb
translation-type: tm+mt
source-git-commit: 0c7b66e636e36a8036a590e949aea42e33a4e289
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 73%

---

# Inhaltsfragmente – Konfigurations-Browser {#content-fragments-configuration-browser}

Erfahren Sie, wie Sie bestimmte Inhaltsfragmentfunktionen im Konfigurationsbrowser aktivieren können, um AEM leistungsstarken Funktionen für kostenlose Versand zu nutzen.

## Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz {#enable-content-fragment-functionality-instance}

Bevor Sie Inhaltsfragmente verwenden können, müssen Sie den **Konfigurations-Browser** verwenden, um Folgendes zu aktivieren:

* **Inhaltsfragmentmodelle** – obligatorisch
* **Persistente GraphQL-Abfragen** – optional

>[!CAUTION]
>
>Wenn Sie **Inhaltsfragmentmodelle** nicht aktivieren:
>
>* Die Option **Create** steht nicht zur Erstellung neuer Modelle zur Verfügung.
>* können Sie nicht [die Sites-Konfiguration auswählen, um den zugehörigen Endpunkt](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint) zu erstellen.


Gehen Sie wie folgt vor, um die Inhaltsfragmentfunktionen zu aktivieren:

* Aktivieren Sie die Verwendung der Inhaltsfragmentfunktionen im Konfigurations-Browser.
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an.

### Aktivieren der Funktionen für Inhaltsfragmente im Konfigurations-Browser {#enable-content-fragment-functionality-in-configuration-browser}

Um [bestimmte Inhaltsfragmentfunktionen zu verwenden](#creating-a-content-fragment-model), **müssen** Sie diese zunächst über den **Konfigurations-Browser** aktivieren:

>[!NOTE]
>
>Weitere Informationen finden Sie auch unter [Konfigurations-Browser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!CAUTION]
>
>Unterkonfigurationen (eine in einer Konfiguration verschachtelte Konfiguration) werden für die Verwendung mit Inhaltsfragmenten nicht unterstützt.

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann den **Konfigurations-Browser**.

1. Öffnen Sie über **Erstellen** das Dialogfeld, in dem Sie:

   1. einen **Titel** angeben,
   1. Um ihre Verwendung zu aktivieren, wählen Sie
      * **Inhaltsfragmentmodelle**
      * **Persistente GraphQL-Abfragen**

      ![Konfiguration definieren](assets/cfm-conf-01.png)


1. Wählen Sie **Erstellen** aus, um die Definition zu speichern.

<!-- 1. Select the location appropriate to your website. -->

### Wenden Sie die Konfiguration auf Ihren Assets-Ordner an {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **Global** für die Inhaltsfragmentfunktionalität aktiviert ist, gilt sie für jeden Assets-Ordner.

Um eine andere Konfiguration (d. h. nicht „Global“) mit einem vergleichbaren Assets-Ordner zu verwenden, müssen Sie die Verbindung definieren. Wählen Sie dazu die entsprechende **Konfiguration** in der Registerkarte **Cloud Services** der **Ordnereigenschaften** des entsprechenden Ordners aus.

![Konfiguration anwenden](assets/cfm-conf-02.png)
