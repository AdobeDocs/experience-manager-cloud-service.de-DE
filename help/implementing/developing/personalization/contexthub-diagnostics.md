---
title: ContextHub-Diagnosen
description: ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten.
exl-id: c8d4e160-ea02-49f3-9e31-119445ef5a68
feature: Developing, Personalization
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 100%

---

# ContextHub-Diagnosen {#contexthub-diagnostics}

ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten. Um die Seite zu öffnen, gehen Sie zur `contexthub.diagnostics.html`-Seite Ihrer AEM-Autoreninstanz, z. B.:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

Die Seite „ContextHub-Diagnose“ enthält Informationen zu den erstellten Speicher- und UI-Modulen sowie zu den geladenen Client-Bibliotheksordnern und Links zu nützlichen Seiten.

>[!NOTE]
>
>Damit Diagnoseinformationen zurückgegeben werden können, muss der Debug-Modus aktiviert sein, da andernfalls die Diagnoseseite leer ist. In [diesem Dokument](configuring-contexthub.md#debugging-contexthub) finden Sie Details zum Aktivieren des Debug-Modus.

## Stores {#stores}

Der Abschnitt „Stores“ listet alle ContextHub-Stores auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der [Store-Typ](sample-stores.md), auf dem der Store basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Speichertyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Speichertyp implementieren.

## Modules {#modules}

Der Abschnitt „Modules“ listet alle ContextHub Benutzeroberflächenmodule auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der [Benutzeroberflächenmodultyp](sample-modules.md), auf dem das Benutzeroberflächenmodul basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der UI-Modultyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den UI-Modultyp implementieren.

## Clientlibs {#clientlibs}

Der Abschnitt „Clientlibs“ listet alle [Ordner von Client-Bibliotheken](/help/implementing/developing/introduction/clientlibs.md) auf, die ContextHub geladen hat. Die Client-Bibliotheken werden wie folgt kategorisiert:

* **kernel.js:** Client-Bibliotheken, die das ContextHub-Framework, die Segment-Engine und Storetypen implementieren.
* **ui.js:** Client-Bibliotheken, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** CSS-Dateien, die aus Client-Bibliotheken geladen werden.

## URLs {#urls}

Der Abschnitt „URLs“ enthält Links zu ContextHub-Features:

* **Konfigurationseditor:** Öffnet die [ContextHub-Konfigurationsseite](configuring-contexthub.md), wo Sie Stores, Benutzeroberflächenmodi und Benutzeroberflächenmodule konfigurieren können.
* **Konfiguration von ContextHub-Modulen:** Öffnet die Datei `/etc/cloudsettings/default/contexthub.config.kernel.js`, die die JavaScript-Objektdarstellung der ContextHub-Speicher-Konfigurationen enthält.
* **Konfiguration der ContextHub-Benutzeroberfläche:** Öffnet die Datei `/etc/cloudsettings/default/contexthub.config.ui.js`, die die JavaScript-Objektdarstellung der ContextHub-Benutzeroberflächen-Modus-Konfigurationen enthält.
* **kernel.js:** Öffnet die `/etc/cloudsettings/default/contexthub.kernel.js`-Datei, die den Quell-Code der Client-Bibliotheken enthält, die das ContextHub-Framework, die Segment-Engine und die Store-Typen implementieren.
* **ui.js:** Öffnet die `/etc/cloudsettings/default/contexthub.ui.js`-Datei, die den Quell-Code der Client-Bibliotheken enthält, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** Öffnet die `/etc/cloudsettings/default/contexthub.styles.css`-Datei, die die CSS-Stile für die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodule enthält.
