---
title: Medienbibliothek für einfache digitale Asset-Verwaltung verwenden
description: '[!DNL Experience Manager Assets] und Medienbibliothek für die Asset-Verwaltung.'
contentOwner: AG
role: Architekt, Leiter
translation-type: tm+mt
source-git-commit: 82650c72f9abbdf6c83c585af7b4f7d17b8dcd08
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---


<!--

Define Media Lib
Define req for it
Define use cases
Define what is not included

-->

# Medienbibliothek für grundlegende Asset-Verwaltung verwenden {#manage-assets-using-media-library}

[!DNL Adobe Experience Manager] Plattform bietet verschiedene Funktionen zum Verwalten digitaler Assets. Mit der Medienbibliothek können Benutzer eine kleine Anzahl von Assets in das Repository hochladen, diese auf den Webseiten suchen und verwenden und einfache Asset-Management-Aufgaben für die Assets durchführen.

Media Library ist eine leichte DAM-Lösung (Digital Asset Management), die mit einer [!DNL Adobe Experience Manager Sites]-Lizenz kostenlos erhältlich ist. [!DNL Sites] ist ein Web-Content-Management-Angebot (WCM). Die Medienbibliothek funktioniert mit allen Funktionen von Experience Manager.

[!DNL Adobe Experience Manager Assets] Lizenz ist separat erhältlich. [!DNL Experience Manager Assets] ermöglicht eine robuste Handhabung von Assets über Anwendungsfälle im Unternehmen, Anpassungen für Metadaten, Schema, Suche und Benutzeroberfläche sowie viele andere Funktionen, die über die von Media Library bereitgestellten Funktionen hinausgehen.

## Lizenzanforderungen {#avail-media-library-license}

Kunden mit einer Lizenz von [!DNL Sites] sind berechtigt, Media Library zu verwenden. Es funktioniert mit allen Komponenten von [!DNL Experience Manager].

Die Medienbibliothek wird als Teil von Sites installiert. Außer der Sites-Lizenz und -Installation ist keine zusätzliche Lizenz oder kein Paket erforderlich.

## [!DNL Assets] versus Medienbibliothek  {#assets-and-media-library}

Experience Manager Assets bietet DAM-Funktionen für Unternehmen. Die Asset-Funktionalität wird mit [!DNL Experience Manager] in einem Paket bereitgestellt. Benutzer, die keine Asset-Lizenz erworben haben, sind jedoch nicht berechtigt, die erweiterten DAM-Funktionen zu verwenden. Ohne Asset-Lizenz sind nur die DAM-Funktionen der Medienbibliothek verfügbar.

Wenn Sie eine unbeabsichtigte Verwendung von nicht lizenzierten [!DNL Assets]-Funktionen verhindern möchten, entfernen Sie alle [!DNL Assets]-spezifischen Workflows, Komponenten, Taxonomien, Optionen und den [!DNL Assets]-Admin von [!DNL Experience Manager]. Dadurch wird verhindert, dass Ihre Benutzer versehentlich [!DNL Assets] Funktionen verwenden, für die Sie keine Lizenz erteilt haben.

## Für Media Library-Benutzer verfügbare Funktionen {#media-library-features}

Die Medienbibliothek deckt im Großen und Ganzen die folgenden Anwendungsfälle ab:

* Stellen Sie grundlegende DAM-Funktionen für Webseiten bereit, die mit [!DNL Adobe Experience Manager Sites] erstellt wurden.
* Adaptive Formulare und Mitteilungen, die mit [!DNL Adobe Experience Manager Forms] erstellt wurden.
* Erlebnisse auf dem Digitalbildschirm, die mit [!DNL Adobe Experience Manager Screens] erstellt wurden.
* [!DNL Assets] HTTP REST-APIs für Operationen ohne Kopfdaten.

<!-- TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.

* Basic metadata properties
* Tag management
* Version control
* Static renditions
* Projects, tasks, workflow authoring
* Activity stream (timeline)
* Query Builder (API)
* Marketing Cloud integration
* User interface customization and extension
* Comments and annotation
-->

Zur Verwendung der Media Library-Funktion können Sie die standardmäßige [!DNL Experience Manager]-Benutzeroberfläche verwenden. Die Medienbibliothek ist Teil der [!DNL Experience Manager Sites]-Installation und es ist keine separate Schnittstelle oder kein Add-on erforderlich. Mithilfe der vorhandenen Oberfläche sind Benutzer von Media Library berechtigt, die folgenden Aufgaben durchzuführen:

* Erstellen Sie Ordner, um Assets zu organisieren.
* Hochladen von Assets.
* Veröffentlichen von Assets.
* Bearbeiten, verschieben und kopieren Sie Assets.
* Assets zum Durchsuchen, Filtern und Suchen (einschließlich Ähnlichkeitssuche).
* hinzufügen und bearbeiten Sie standardmäßig die Metadatenfelder, die auf der Registerkarte [!UICONTROL Einfach] der Seite [!UICONTROL Eigenschaften] eines Assets verfügbar sind. <!-- excluding Smart Tags -->
* hinzufügen und löschen Sie statische Darstellungen.
* Herunterladen von Ordnern, Assets und Asset-Darstellungen.
* Erstellen Sie Asset-Versionen.
* Erstellen und führen Sie Review-Aufgaben für Assets durch.
* Anmerkungen zu Assets.
* hinzufügen Assets über die Inhaltssuche auf [!DNL Sites]-Seiten.
* Verwenden [!DNL Content Fragments].

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?
-->

[!DNL Experience Manager Assets] erfüllt viele andere Anwendungsfälle von DAM, die Sie in der  [[!DNL Assets] Dokumentations-Startseite](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html?lang=de) untersuchen können. In der Medienbibliothek stehen keine oben nicht aufgeführten Anwendungsfälle zur Verfügung.

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-cloud-service.html)

