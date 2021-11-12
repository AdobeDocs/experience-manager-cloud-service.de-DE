---
title: Erlebnisse im gestaffelten Produktkatalog verwalten
description: Erfahren Sie, wie Sie die Erlebnisse im gestaffelten Produktkatalog verwalten.
source-git-commit: a98d525512dcba790d002d6a4042558962c36c97
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Erstellen von Staging-Produktkatalog-Erlebnissen {#building-experiences}

Erfahren Sie, wie Sie die Erlebnisse im gestaffelten Produktkatalog verwalten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Journey für AEM Content and Commerce [Verwalten von Produktkatalogseiten und -vorlagen](catalog-templates.md), haben Sie gelernt, wie Sie Produktkatalog-Erlebnisse basierend auf Vorlagen verwalten und erstellen.

Dieser Artikel baut auf diesen Grundlagen auf.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie das Erlebnis eines Produktkatalogs basierend auf gestaffelten Produktdaten und AEM Launches verwalten. Oft müssen Autoren parallel einen bevorstehenden Produktstart vorbereiten (z. B. eine neue Bekleidungssammlung). Dies erfordert den Zugriff auf gestaffelte Produktdaten (noch nicht verfügbar) und die Möglichkeit, den Inhalt vorzubereiten. Dieser neue Inhalt wird mit dem Produktstart live geschaltet.

    >[!NOTE]
    >
    >Diese Funktion ist nur bei Adobe Commerce- oder Cloud Edition- und Drittanbieter-Connectoren verfügbar, die Token-basierte Authentifizierung unterstützen. Weitere Informationen finden Sie unter [Erste Schritte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/storefront/getting-started.html) .

Zunächst sehen wir, wie Autoren mit CIF auf gestaffelte Produktdaten zugreifen können.

## Staging-Produktdaten verwenden {#staged-product-data}

Eine Möglichkeit, auf gestaffelte Produktdaten zuzugreifen, ist die Verwendung des Produkt-Cockpits. Öffnen Sie den Produktkatalog, indem Sie im Hauptmenü auf das Symbol Handel AEM klicken. Dadurch erhalten Sie Zugriff auf Live-Produktdaten. Öffnen Sie die Registerkarte Filter auf der linken Seite und erweitern Sie **STAGIERTER KATALOG**. Mithilfe der Vorschaudaten können Sie jetzt jederzeit auf gestaffelte Produktdaten zugreifen. Staging-Daten enthalten neue Kategorien, Produkte oder aktualisierte Felder wie den Preis.

![Bühnencockpit](assets/staged-cockpit.png)

Die Vorschau einer Storefront mit gestaffelten Daten ist über die Timewarp-Ansicht möglich. Öffnen Sie den Editor und wechseln Sie in den Modus Timewarp. Wählen Sie ein zukünftiges Datum aus. Beachten Sie die Informationen oben im Editor, dass Sie die Seite für ein bestimmtes Datum anzeigen.

![stage timewarp](assets/staged-timewarp.png)

Sie können jetzt den Katalog mit den gestaffelten Daten durchsuchen. Wenn Sie eine gestaffelte Kategorie oder Produktseite öffnen, zeigt der Editor eine visuelle Anzeige an.

![Bühnenplättchen](assets/staged-plp.png)

    >[!NOTE]
    >
    >Omnisearch hat keinen Kontext und gibt daher nur Live-Produktkatalogdaten zurück.

## AEM-Launches {#launches}

Mit AEM Launches können Sie Inhalte für gestaffelte Produktdaten erstellen. Wenn Sie nicht mit Launches vertraut sind, folgen Sie dem Dokumentations-Link unter dem [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources). Das Launch-Datum wird dann verwendet, um auf gestaffelte Produktdaten zuzugreifen.

![Staging-Launch](assets/staged-launch.png)

Beachten Sie, dass die Auswahl das Startdatum mit der gestaffelten Anzeige auf der rechten Seite einhält.

![Statusauswahl](assets/staged-picker.png)

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der Journey abgeschlossen haben, sollten Sie:

* die Konzepte des gestaffelten Produktkatalogs und -inhalts mit Launches verstehen
* über das Produkt-Cockpit und den Editor auf gestaffelte Produktkatalogdaten zugreifen können

Sie können jetzt [Produkterlebnisse](product-experience-management.md). Für AEM Inhalte und Commerce stehen jedoch viele zusätzliche Optionen zur Verfügung. Sehen Sie sich einige der zusätzlichen Ressourcen an, die im Abschnitt [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources) um mehr über die Funktionen zu erfahren, die Sie auf dieser Journey gesehen haben.

## Zusätzliche Ressourcen {#additional-resources}

* [Produkt-Cockpit](/help/commerce-cloud/authoring/product-cockpit.md)
* [Erste Schritte](/help/commerce-cloud/getting-started.md)
* [Launches](/help/sites-cloud/authoring/launches/overview.md)
