---
title: Adobe AEM Zielgruppe HTTP Window
description: 'Adobe AEM Zielgruppe HTTP Window '
translation-type: tm+mt
source-git-commit: c193b38718622cd2e960a8e8833c2d295822dc33
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 4%

---


# Einführung {#introduction}

Auf dieser Seite werden die konfigurierbaren Parameter im Adobe AEM Zielgruppe HTTP Window beschrieben.

## Parameter {#parameters}

![Zielgruppe HTTP](assets/httpwindow.png "WindowTarget HTTP Window")

Das Fenster enthält die folgenden konfigurierbaren Parameter:

| Parameter | Beschreibung |
|---|---|
| Adobe Target-API-URL | Die URL der Adobe Target-API. |
| Absolute URL aktivieren | Bestimmt, ob entweder der Hostteil der URL oder die vollständige URL verwendet wird. Aktivieren Sie das Kontrollkästchen, wenn Sie die vollständige URL (nicht gekürzt) verwenden möchten. Standardmäßig ist das Kontrollkästchen deaktiviert. |
| Verbindungs-Zeitüberschreitung | Der Timeout (in Millisekunden), bis eine Verbindung hergestellt ist. Der Standardwert ist 60000 Millisekunden. Der Wert 0 wird als unendlicher Timeout interpretiert. |
| Socket-Zeitüberschreitung | Der Timeout (in Millisekunden), der auf Daten oder einen maximalen Inaktivitätszeitraum zwischen zwei aufeinander folgenden Datenpaketen wartet. Der Standardwert ist 30000 Millisekunden. |
| Adobe Target Recommendations URL Ersetzen des Regex-Tokens | Steuert das Token in der Adobe Target-Endpunkt-URL, das ersetzt werden muss, um auf die Zielgruppe Recommendations-API-URL zu verweisen. |
| Adobe Target Recommendations-URL durch Token ersetzen | Ersatz für den im obigen Parameter beschriebenen Regex, sodass die resultierende URL auf die Zielgruppe Recommendations-API verweist. |
