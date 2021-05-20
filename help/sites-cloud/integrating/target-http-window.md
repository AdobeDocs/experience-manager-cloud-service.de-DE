---
title: Adobe AEM Target-HTTP-Fenster
description: 'Adobe AEM Target-HTTP-Fenster '
source-git-commit: c193b38718622cd2e960a8e8833c2d295822dc33
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---


# Einführung {#introduction}

Auf dieser Seite werden die konfigurierbaren Parameter im Adobe AEM Target-HTTP-Fenster beschrieben.

## Parameter {#parameters}

![Target-HTTP-Fenster](assets/httpwindow.png "Target-HTTP-Fenster")

Das Fenster enthält die folgenden konfigurierbaren Parameter:

| Parameter | Beschreibung |
|---|---|
| Adobe Target-API-URL | Die URL der Adobe Target-API. |
| Absolute URL aktivieren | Bestimmt, ob entweder der Host-Teil der URL oder die vollständige URL verwendet wird. Aktivieren Sie das Kontrollkästchen, wenn Sie die vollständige URL (nicht gekürzt) verwenden möchten. Standardmäßig ist das Kontrollkästchen deaktiviert. |
| Verbindungs-Zeitüberschreitung | Der Timeout (in Millisekunden), bis eine Verbindung hergestellt ist. Der Standardwert ist 60.000 Millisekunden. Der Wert 0 wird als unendlicher Timeout interpretiert. |
| Socket-Zeitüberschreitung | Der Timeout (in Millisekunden), in dem auf Daten gewartet wird, oder ein maximaler Inaktivitätszeitraum zwischen zwei aufeinander folgenden Datenpaketen. Der Standardwert ist 30000 Millisekunden. |
| Adobe Target Recommendations-URL – Regex-Token-Ersetzung | Steuert das Token in der Adobe Target-Endpunkt-URL, das ersetzt werden muss, um auf die Target Recommendations-API-URL zu verweisen. |
| Adobe Target Recommendations-URL – Token-Ersetzung | Ersatz für den im obigen Parameter beschriebenen Regex, sodass die resultierende URL auf die Target Recommendations-API verweist. |
