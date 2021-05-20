---
title: ContextHub-Diagnosen
description: ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten
exl-id: c8d4e160-ea02-49f3-9e31-119445ef5a68
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 100%

---

# ContextHub-Diagnosen {#contexthub-diagnostics}

ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten Um die Seite zu öffnen, gehen Sie zur `contexthub.diagnostics.html`-Seite Ihrer AEM-Autorenrinstanz, z. B.:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

Die „Seite ContextHub-Diagnose“ enthält Informationen zu den erstellten Stores und Benutzeroberflächenmodulen, den geladenen Client-Bibliotheksordnern und Links zu nützlichen Seiten.

>[!NOTE]
>
>Damit Diagnoseinformationen zurückgegeben werden können, muss der Debug-Modus aktiviert sein, da andernfalls die Diagnoseseite leer ist. In [diesem Dokument](configuring-contexthub.md#debugging-contexthub) finden Sie Details zum Aktivieren des Debug-Modus.

## Stores  {#stores}

Der Abschnitt „Stores“ listet alle ContextHub-Stores auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der[Store-Typ](sample-stores.md), auf dem der Store basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Storetyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Storetyp implementieren.

## Modules  {#modules}

Der Abschnitt „Modules“ listet alle ContextHub Benutzeroberflächenmodule auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der [Benutzeroberflächenmodultyp](sample-modules.md), auf dem das Benutzeroberflächenmodul basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Benutzeroberflächenmodultyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Benutzeroberflächenmodultyp implementieren.

## Clientlibs  {#clientlibs}

Der Abschnitt „Clientlibs“ listet alle [Ordner der Client-Bibliothek](/help/implementing/developing/introduction/clientlibs.md) auf, die ContextHub geladen hat. Die Client-Bibliotheken werden wie folgt kategorisiert:

* **kernel.js:** Client-Bibliotheken, die das ContextHub-Framework, die Segment-Engine und Storetypen implementieren.
* **ui.js:** Client-Bibliotheken, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** CSS-Dateien, die aus Client-Bibliotheken geladen werden.

## URLs  {#urls}

Der Abschnitt „URLs“ enthält Links zu ContextHub-Features:

* **Konfigurationseditor:** Öffnet die [ContextHub-Konfigurationsseite](configuring-contexthub.md), wo Sie Stores, Benutzeroberflächenmodi und Benutzeroberflächenmodule konfigurieren können.
* **Konfigurieren von ContextHub-Modulen:** Öffnet die `/etc/cloudsettings/default/contexthub.config.kernel.js`-Datei, die die JavaScript-Objektdarstellung der ContextHub-Store-Konfigurationen enthält.
* **Konfigurieren von ContextHub-Benutzeroberfläche:** Öffnet die `/etc/cloudsettings/default/contexthub.config.ui.js`-Datei, die die JavaScript-Objektdarstellung der ContextHub-Benutzeroberflächenmoduskonfigurationen enthält.
* **kernel.js:** Öffnet die `/etc/cloudsettings/default/contexthub.kernel.js`-Datei, die den Quell-Code der Client-Bibliotheken enthält, die das ContextHub-Framework, die Segment-Engine und die Store-Typen implementieren.
* **ui.js:** Öffnet die `/etc/cloudsettings/default/contexthub.ui.js`-Datei, die den Quell-Code der Client-Bibliotheken enthält, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** Öffnet die `/etc/cloudsettings/default/contexthub.styles.css`-Datei, die die CSS-Stile für die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodule enthält.
