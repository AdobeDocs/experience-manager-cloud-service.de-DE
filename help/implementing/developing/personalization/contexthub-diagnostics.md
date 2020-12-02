---
title: ContextHub-Diagnosen
description: ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten
translation-type: tm+mt
source-git-commit: 1c518830f0bc9d9c7e6b11bebd6c0abd668ce040
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 62%

---


# ContextHub-Diagnosen {#contexthub-diagnostics}

ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten Um die Seite zu öffnen, wechseln Sie zur Seite `contexthub.diagnostics.html` Ihrer AEM Autoreninstanz, z. B.:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

Die „Seite ContextHub-Diagnose“ enthält Informationen zu den erstellten Stores und Benutzeroberflächenmodulen, den geladenen Client-Bibliotheksordnern und Links zu nützlichen Seiten.

>[!NOTE]
>
>Damit Diagnoseinformationen zurückgegeben werden können, muss der Debug-Modus aktiviert sein, da andernfalls die Diagnoseseite leer ist. In [diesem Dokument](configuring-contexthub.md#debugging-contexthub) finden Sie Details zum Aktivieren des Debug-Modus.

## Stores {#stores}

Der Abschnitt „Stores“ listet alle ContextHub-Stores auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der[ Storetyp](sample-stores.md), auf dem der Store basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Storetyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Storetyp implementieren.

## Modules  {#modules}

Der Abschnitt „Modules“ listet alle ContextHub Benutzeroberflächenmodule auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Titel:** Der  [UI-Modul-](sample-modules.md) Typ, auf dem das UI-Modul basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Benutzeroberflächenmodultyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Benutzeroberflächenmodultyp implementieren.

## Clientlibs  {#clientlibs}

Im Clientlibs-Abschnitt werden alle [Clientbibliotheksordner](/help/implementing/developing/introduction/clientlibs.md), die ContextHub geladen hat, Liste. Die Clientbibliotheken werden wie folgt kategorisiert:

* **kernel.js:** Client-Bibliotheken, die das ContextHub-Framework, die Segment-Engine und Storetypen implementieren.
* **ui.js:** Client-Bibliotheken, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** CSS-Dateien, die aus Client-Bibliotheken geladen werden.

## URLs      {#urls}

Der Abschnitt „URLs“ enthält Links zu ContextHub-Features:

* **Configuration Editor:** Öffnet die  [ContextHub-Konfigurationsseite, auf der Sie ](configuring-contexthub.md) Stores, UI-Modi und UI-Module konfigurieren können.
* **Konfiguration der ContextHub-Module:** Öffnet die  `/etc/cloudsettings/default/contexthub.config.kernel.js` Datei, die die Javascript-Objektdarstellung der ContextHub-Speicherkonfigurationen enthält.
* **Konfiguration der ContextHub-Benutzeroberfläche:** Öffnet die  `/etc/cloudsettings/default/contexthub.config.ui.js` Datei, die die Javascript-Objektdarstellung der ContextHub-UI-Moduskonfigurationen enthält.
* **kernel.js:** Öffnet die  `/etc/cloudsettings/default/contexthub.kernel.js` Datei, die den Quellcode der Client-Bibliotheken enthält, die das ContextHub-Framework, die Segment-Engine und die Store-Typen implementieren.
* **ui.js:** Öffnet die  `/etc/cloudsettings/default/contexthub.ui.js` Datei, die den Quellcode der Clientbibliotheken enthält, die die ContextHub-UI- und UI-Modultypen implementieren.
* **style.css:** Öffnet die  `/etc/cloudsettings/default/contexthub.styles.css` Datei, die die CSS-Stile für die ContextHub-UI- und UI-Module enthält.
