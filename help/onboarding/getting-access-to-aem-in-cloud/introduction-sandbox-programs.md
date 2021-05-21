---
title: 'Einführung in Sandbox-Programme '
description: Einführung in Sandbox-Programme
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: 3b57acc47dd60d050ceebebb12bd9080b7fc5cf5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 88%

---

# Einführung in Sandbox-Programme {#sandbox-programs}

## Einführung {#introduction}

Ein Sandbox-Programm ist einer von zwei Programmtypen, die in AEM Cloud Service verfügbar sind; der andere ist ein Produktionsprogramm.

Sandboxes werden normalerweise für Schulungen, laufende Demos, Aktivierungen oder Proof of Concepts (POCs) erstellt. Sie sind nicht dazu gedacht, Live-Traffic zu übertragen. Sie unterliegen nicht den [AEM as a Cloud Service-Verpflichtungen](https://www.adobe.com/legal/service-commitments.html).

Die in einer Sandbox erstellten Umgebungen sind nicht für automatische Skalierung konfiguriert. Daher sind diese Umgebungen nicht für Leistungs- oder Belastungstests geeignet.

Sandbox-Programme umfassen Sites und Assets und werden automatisch mit einem Git-Repository, einer Entwicklungsumgebung und einer Nicht-Produktions-Pipeline gefüllt.  Das Git-Repository wird basierend auf dem AEM-Projektarchetyp mit einem Beispielprojekt gefüllt.

Weitere Informationen zu den Programmtypen finden Sie unter [Einführung zu Programmen und Programmtypen](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md).

### Attribute von Sandbox-Programmen {#attributes-sandbox}

Sandbox-Programme haben die folgenden Attribute:

1. **Programmerstellung:** Die Erstellung von Sandbox-Programmen umfasst die automatische:
   * Einrichtung eines Projekts mit Beispiel-Code und -Inhalt
   * Schaffung einer Entwicklungsumgebung
   * Erstellung einer Nicht-Produktions-Pipeline, die in der Entwicklungsumgebung bereitgestellt wird (übergeordnete Verzweigung, die in der Entwicklungsumgebung bereitgestellt wird)

1. **Lösungen:** Sandbox-Programme beinhalten AEM Sites und Assets.

1. **AEM-Updates:** AEM-Updates können in Sandbox-Programmen manuell auf Umgebungen angewendet werden und werden nicht automatisch gesendet.
Weitere Informationen finden Sie unter [AEM-Updates für Sandbox-Umgebungen](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md#aem-updates-sandbox).

1. **Ruhezustand:** Umgebungen in einem Sandbox-Programm werden automatisch in den Ruhezustand versetzt, wenn in einem bestimmten Zeitraum keine Aktivität erkannt wurde. Sandboxes werden nach 8 Stunden Inaktivität in den Ruhezustand versetzt. Danach können sie wieder aus dem Ruhezustand geholt werden. In den Ruhezustand versetzte Umgebungen können manuell wieder aktiviert werden.
Weitere Informationen finden Sie unter [Versetzen von Sandbox-Umgebungen in den Ruhezustand und Aufheben des Ruhezustandes](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md).

1. **Löschen**: Sandboxes werden nach 6 Monaten, nachdem sie sich im kontinuierlichen Ruhezustand befinden, gelöscht. Danach können sie neu erstellt werden.
