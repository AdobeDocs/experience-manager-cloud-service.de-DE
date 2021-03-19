---
title: Wiederverwenden von Inhalten - Multi-Site-Manager und Live Copy
description: Erhalten Sie eine Einführung in die Wiederverwendung von Inhalten mit AEM leistungsstarken Live Copies und den Multi-Site-Manager-Funktionen.
feature: Multi-Site-Manager
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '2686'
ht-degree: 26%

---


# Wiederverwenden von Inhalten: Multi-Site-Manager und Live Copy {#multi-site-manager-and-live-copy}

Mit dem Multi-Site-Manager (MSM) können Sie denselben Site-Inhalt an mehreren Orten verwenden. MSM verwendet seine Live Copy-Funktion, um Folgendes zu erreichen.

* Mit MSM können Sie:
   * Erstellen von Inhalten einmal und dann
   * Verwenden Sie diesen Inhalt in anderen Bereichen (über [Live Copies](#live-copies)) derselben oder anderer Sites erneut.
* MSM unterhält dann die Live-Beziehungen zwischen dem Quellinhalt und den Live Copies, sodass:
   * Wenn Sie Änderungen am Quellinhalt vornehmen, werden die Quell- und Live-Kopien synchronisiert.
   * Sie können Änderungen nur am Inhalt der Live Copies vornehmen, indem Sie die Live-Beziehung für einzelne Unterseiten und/oder Komponenten trennen.

Diese Seite bietet einen Überblick über die Wiederverwendung von Inhalten mit MSM. Auf den folgenden Seiten werden die damit zusammenhängenden Probleme ausführlich behandelt.

* [Erstellen und Synchronisieren von Live Copies](creating-live-copies.md)
* [Konsole „Live Copy-Übersicht“](live-copy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](live-copy-sync-config.md)
* [MSM-Rollout-Konflikte](rollout-conflicts.md)
* [Best Practices für MSM](best-practices.md)

## Mögliche Szenarien {#possible-scenarios}

Es gibt viele Anwendungsfälle für MSM und Live Copies. Einige Szenarien beinhalten:

* **Multinational – Globale zu lokalen Unternehmen**

   Ein typisches, von MSM unterstütztes Nutzungsszenario ist die Wiederverwendung von Inhalten auf verschiedenen multinationalen Sites in derselben Sprache. Dies ermöglicht die Wiederverwendung des Kerninhalts und ermöglicht auch nationale Abweichungen.

   Beispielsweise wird der englische Abschnitt des Tutorials [WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) für Kunden in den USA erstellt. Die meisten Inhalte dieser Website können auch für andere WKND-Seiten verwendet werden, die englischsprachigen Kunden verschiedener Länder und Kulturen entsprechen. Der Kerninhalt bleibt auf allen Sites gleich, wobei regionale Anpassungen vorgenommen werden können.

   Die folgende Struktur kann für Standorte in den USA und Kanada verwendet werden. Beachten Sie, dass `language-masters`-Knoten die Übergeordnet-Kopie nicht nur des englischen, sondern auch anderer Sprachinhalte beibehält. Dieser Inhalt kann neben Englisch als Grundlage für zusätzliche regionale Sprachinhalte verwendet werden.

   ```xml
   /content
       |- wknd
           |- language-masters
               |- en
               |- es
               |- fr
           |- us
               |- en
               |- es
           |- ca
               |- en
               |- fr
   ```

   >[!NOTE]
   >
   >MSM übersetzt die Inhalte nicht. Er wird zur Erstellung der erforderlichen Struktur und zur Bereitstellung von Inhalten verwendet.
   >
   >
   >Ein solches Beispiel finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-cloud/administering/translation/overview.md).

* **National – Zentrale zu Zweigstellen**

   Alternativ könnte eine Firma mit einem Händlernetz separate Websites für ihre einzelnen Händler anbieten, wobei jede eine Variante des Hauptstandorts darstellt, der vom Hauptsitz bereitgestellt wird. Dies kann für ein einziges Unternehmen mit mehreren regionalen Niederlassungen oder für ein landesweites Franchisesystem mit einem zentralen Franchisegeber und mehreren lokalen Franchisenehmern eingesetzt werden.

   Die Zentrale kann die Kerninformationen bereitstellen und die regionalen Standorte können lokale Informationen wie Kontaktdetails, Geschäftszeiten und Veranstaltungen ergänzen.

   ```xml
   /content
       |- head-office-berlin
       |- branch-hamburg
       |- branch-stuttgart
       |- branch-munich
       |- branch-frankfurt
   ```

* **Mehrere Versionen**

   MSM kann Versionen einer bestimmten Unterverzweigung erstellen. Beispielsweise kann eine Support-Subsite Details zu den verschiedenen Versionen eines bestimmten Produkts enthalten, wobei die Basisinformationen konstant bleiben und nur die aktualisierten Funktionen geändert werden müssen:

   ```xml
   /content
       |- game-support
           |- polybius
               |- v5.0
               |- v4.0
               |- v3.0
               |- v2.0
               |- v1.0
   ```

   >[!TIP]
   >
   >In einem solchen Szenario stellt sich die Frage, ob eine einfache Kopie oder Verwendung von Live Copies möglich ist. Dies ist eine Bilanz von:
   >
   >* Wie viel Kerninhalt muss über mehrere Versionen aktualisiert werden?
   >
   >und
   >
   >* Wie viel der einzelnen Exemplare muss angepasst werden?


## MSM über die Benutzeroberfläche {#msm-from-the-ui}

MSM ist in der Benutzeroberfläche mit verschiedenen Optionen aus der entsprechenden Konsole direkt zugänglich.

* **Website erstellen** (**Sites**)

   * MSM unterstützt Sie bei der Verwaltung mehrerer Websites, die gemeinsame Inhalte verwenden. So werden Websites oft für internationale Audiencen bereitgestellt, sodass der Großteil der Inhalte in allen Ländern verbreitet ist, wobei eine Untergruppe der Inhalte für das jeweilige Land spezifisch ist. Mit MSM können Sie [Live Copies erstellen, die automatisch eine oder mehrere Sites auf Basis Ihrer Quellsite](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) aktualisieren. Dies hilft Ihnen auch dabei, eine gemeinsame Basisstruktur zu erzwingen, die gemeinsamen Inhalte auf mehreren Sites zu nutzen, ein gemeinsames Erscheinungsbild zu erreichen und die Maßnahmen auf die Verwaltung der Inhalte zu konzentrieren, die sich auf den verschiedenen Sites tatsächlich unterscheiden. Erstellen einer Site auf diese Weise:
      * Für die Angabe der Quelle ist eine vordefinierte Blueprint-Konfigurationen erforderlich.
      * Erstellt eine Live Copy der (vordefinierten) Quelle.
      * Stellt dem Benutzer eine **Rollout**-Schaltfläche bereit.

* **Live Copy erstellen** (**Sites**)

   * Mit MSM können Sie eine Ad-hoc-(Einmal-)Live-Kopie einer einzelnen Seite oder Unterzweigung einer Website erstellen. ](creating-live-copies.md#creating-a-live-copy-of-a-page) Duplizieren Sie beispielsweise eine Unterverzweigung, um Informationen über eine neue/aktualisierte Version eines Produkts bereitzustellen. [ Erstellen einer Live Copy auf diese Weise:
      * Erstellt eine Ad-hoc-Live Copy (keine Blueprint-Konfiguration erforderlich).
      * Kann verwendet werden, um (sofort) eine Live Copy einer beliebigen Seite/Verzweigung zu erstellen.
      * Erfordert **Synchronisieren** (stellt nicht die Schaltfläche **Rollout** bereit).

* **Eigenschaften anzeigen** (**Sites**)

   * Diese Option unterstützt Sie gegebenenfalls bei der Überwachung Ihrer Live Copy](creating-live-copies.md#monitoring-your-live-copy), indem Sie Informationen zu der zugehörigen **Live Copy** oder **Blueprint** angeben.[

* **Verweise** (**Sites**)

   * Die Leiste [References](/help/sites-cloud/authoring/getting-started/basic-handling.md#references) enthält Informationen zu **Live Copies** sowie Zugriff auf entsprechende Aktionen.

* **Live Copy-Übersicht** (**Sites**)

   * Diese Konsole ermöglicht Ihnen die [Ansicht und Verwaltung Ihres Blueprints und der zugehörigen Live Copies.](live-copy-overview.md)

* **Blueprints** (**Tools** – **Sites**)

   * Diese Konsole ermöglicht Ihnen die [Erstellung und Verwaltung Ihrer Blueprint-Konfigurationen.](creating-live-copies.md#creating-a-blueprint-configuration)

>[!NOTE]
>
>Aspekte der MSM-Funktionalität werden in verschiedenen anderen AEM Funktionen wie Launches verwendet. In diesen Fällen wird die Live Copy von dieser Funktion verwaltet.

### Verwendete Bedingungen {#terms-used}

In der folgenden Tabelle werden die wichtigsten Begriffe erläutert, die mit MSM verwendet werden. Diese werden in den folgenden Abschnitten und Seiten ausführlicher behandelt.

| Begriff | Definition | Weitere Details |
|---|---|---|
| Quelle | Die als Grundlage für Live Copies verwendeten Originalseiten | Synonym für Blueprints und/oder Blueprint-Seiten |
| Live Copy  | Die Kopie (der Quelle), die durch Synchronisierungsaktionen gemäß den Rollout-Konfigurationen verwaltet wird |  |
| Live Copy-Konfiguration | Definition der Konfigurationsdetails für eine Live Copy |  |
| Live-Beziehung | Effektive Definition der Vererbung für eine bestimmte Ressource, d. h. die Verbindung(en) zwischen der Quelle und Live Copies | Stellt sicher, dass Änderungen an der Quelle mit der Live Copy synchronisiert werden können |
| Blueprint | Synonym mit Quelle | Kann durch eine Blueprint-Konfiguration definiert werden |
| Blueprint-Konfiguration | Vordefinierte Konfiguration zum Festlegen eines Quellpfads | Wenn in einer Blueprint-Konfiguration auf eine Blueprint-Seite verwiesen wird, steht der Befehl &quot;Rollout&quot;zur Verfügung |
| Kapitel | Die Abschnitte des Entwurfs, die in die Live Copy-Kopie enthalten werden sollen | Dies sind im Allgemeinen Unterseiten des Stammordners |
| Synchronisierung | Der allgemeine Begriff für die Synchronisierung von Inhalt zwischen der Quelle und den Live Copies (sowohl **Rollout**- als auch **Synchronize**-Optionen) |  |
| Rollout | Synchronisiert die Synchronisierung von der Quelle zur Live Copy | Kann von einem Autor (auf einer Blueprint-Seite) oder von einem System-Ereignis (wie in der Rollout-Konfiguration definiert) ausgelöst werden |
| Rollout-Konfiguration | Regeln, die festlegen, welche Eigenschaften synchronisiert werden, wie und wann |  |
| Synchronisieren | Eine manuelle Anforderung der Synchronisierung, die über die Live Copy-Seiten erfolgt |  |
| Vererbung | Eine Live Copy-Seite/Komponente übernimmt Inhalt von ihrer Quellseite/Komponente, wenn eine Synchronisierung stattfindet |  |
| Aussetzen | Entfernt temporär die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite |  |
| Trennen | Entfernt die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite dauerhaft |  |
| Zurücksetzen | Eine Live Copy-Seite zurücksetzen, um alle Vererbungsabbrüche zu entfernen und die Seite wieder in den gleichen Status wie die Quellseite zurückzusetzen | Eine Rücksetzung wirkt sich auf alle von Ihnen durchgeführten Änderungen an den Seiteneigenschaften, am Absatzsystem und an den Komponenten aus. |
| Langsam | Eine Live-Kopie einer einzelnen Seite |  |
| Tief | Eine Live-Kopie einer Seite zusammen mit ihren untergeordneten Seiten |  |

<!--
>[!TIP]
>
>See [Overview of the Java API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) for the object names.
-->

## Live Copies {#live-copies}

Eine MSM Live Copy ist eine Kopie eines bestimmten Site-Inhalts, für den eine Live-Beziehung zur ursprünglichen Quelle aufrechterhalten wird:

* Die Live Copy übernimmt Inhalte von ihrer Quelle.
* Die Synchronisierung führt die tatsächliche Übertragung von Inhalten durch, wenn Änderungen an der Quelle vorgenommen werden.
* Eine Live-Kopie kann wie folgt betrachtet werden:
   * Flach: eine einzelne Seite
   * Tief: die Seite mit ihren untergeordneten Seiten
* Die Synchronisierungsregeln, so genannte Rollout-Konfigurationen, bestimmen, welche Eigenschaften synchronisiert werden und wann die Synchronisierung erfolgt.

Im vorherigen Beispiel ist `/content/wknd/language-masters/en` die globale Übergeordnet-Site in Englisch. Um den Inhalt dieser Site wiederverwenden zu können, werden MSM Live Copies erstellt:

* Der Inhalt unter `/content/wknd/language-masters/en` ist die Quelle.
* Der Inhalt unter `/content/wknd/language-masters/en` wird unter die Knoten `/content/wknd/us/en/` und `/content/wknd/ca/en` kopiert. Das sind die Live Copies.
* Autoren nehmen Änderungen an Seiten unter `/content/wknd/language-masters/en` vor.
* Bei Auslösung synchronisiert MSM diese Änderungen mit den Live Copies.

### Live Copies – Komposition {#live-copies-composition}

>[!NOTE]
>
>Die Diagramme und Beschreibungen in diesem Abschnitt stellen Schnappschüsse potenzieller Live Copies dar. Sie erheben keinen Anspruch auf Vollständigkeit, stellen jedoch einen Überblick bereit, um bestimmte Merkmale hervorzuheben.

Wenn Sie zum ersten Mal eine Live Copy erstellen, werden die ausgewählten Quellseiten in der Live Copy auf 1:1-Basis angezeigt. Danach können neue Ressourcen (Seiten und/oder Absätze) auch direkt in der Live Copy erstellt werden. Daher ist es nützlich, sich dieser Variationen und deren Auswirkungen auf die Synchronisierung bewusst zu sein. Mögliche Kompositionen umfassen:

* [Live Copy mit Live Copy-fremden Seiten](#live-copy-with-non-live-copy-pages)
* [Verschachtelte Live Copies](#nested-live-copies)

Die grundlegende Form von Live Copy hat:

* Live Copy-Seiten, die die ausgewählten Quellseiten in 1:1 widerspiegeln.
* Eine Konfigurationsdefinition
* Eine zu jeder Ressource festgelegte Live-Beziehung:
   * Verknüpfen Sie die Live Copy-Ressource mit ihrem Entwurf/ihrer Quelle.
   * Werden bei der Realisierung von Vererbung und Rollout verwendet.

Änderungen können entsprechend den Anforderungen [synchronisiert](creating-live-copies.md#synchronizing-your-live-copy) werden.

![Übersicht über die Live Copy-Komposition](../assets/live-copy-composition.png)

#### Live Copy mit Nicht-Live-Copy-Seiten {#live-copy-with-non-live-copy-pages}

Wenn Sie eine Live Copy in AEM erstellen, können Sie die Live Copy-Verzweigung sehen und durch diese navigieren und die normale AEM in der Live Copy-Verzweigung verwenden. Das bedeutet, dass Sie (oder ein Prozess) neue Ressourcen (Seiten und/oder Absätze) in der Live Copy erstellen können. z.B. ein Produkt für eine bestimmte Region oder ein bestimmtes Land.

* Solche Ressourcen verfügen über keine Live-Beziehung zu Quell-/Blueprint-Seiten und werden nicht synchronisiert.
* Es können Szenarien auftreten, die MSM als Spezialfälle behandelt. Wenn Sie (oder ein Prozess) beispielsweise eine Seite mit derselben Position und demselben Namen in der Quell-/Blaupausen- und Live Copy-Verzweigung erstellen. Weitere Informationen zu solchen Situationen finden Sie unter [MSM-Rollout-Konflikte](rollout-conflicts.md).

![Live Copy mit Seiten ohne Live Copy](../assets/live-copy-with-non-live-copy-pages.png)

#### Verschachtelte Live Copies {#nested-live-copies}

Wenn Sie (oder ein Prozess) eine [neue Seite in einer vorhandenen Live Copy](#live-copy-with-non-live-copy-pages) erstellen, kann diese neue Seite auch als Live Copy eines anderen Blueprints eingerichtet werden. Dies wird als verschachtelte Live Copy bezeichnet. In verschachtelten Live Copies wird das Verhalten der zweiten oder inneren Live Copy durch die erste oder äußere Live Copy wie folgt beeinflusst:

* Eine tiefe Rollout, die für die Live Copy der obersten Ebene ausgelöst wird, kann in die verschachtelte Live Copy fortgesetzt werden.
* Alle Links zwischen den Quellen werden in den Live Copies neu geschrieben.

Beispielsweise werden Links, die von der zweiten zur ersten Vorlage zeigen, als Links umgeschrieben, die von der verschachtelten/zweiten Live Copy zur ersten Live Copy zeigen.

![Verschachtelte Live Copies](../assets/live-copy-nested.png)

>[!NOTE]
>
>Wenn Sie eine Seite innerhalb der Live Copy-Verzweigung verschieben oder umbenennen, wird diese als verschachtelte Live Copy behandelt, damit AEM die Beziehungen verfolgen können.

#### Gestapelte Live Copies {#stacked-live-copies}

Eine Live Copy wird als gestapelte Live Copy bezeichnet, wenn sie als untergeordnetes Element einer flachen Live Copy erstellt wird. Es verhält sich auf dieselbe Weise wie eine [verschachtelte Live Copy](#nested-live-copies).

### Quelle, Blueprints und Blueprint-Konfigurationen {#source-blueprints-and-blueprint-configurations}

Jede Seite oder jeder Zweig von Seiten kann als Quelle einer Live Copy verwendet werden. MSM ermöglicht Ihnen allerdings die Definition einer Blueprint-Konfiguration, die einen Quellpfad angibt. Die Vorteile einer Blueprint-Konfiguration sind, dass sie:

* Erlauben Sie dem Autor, die Option **Rollout** für einen Blueprint zu verwenden. Das heißt, dass Änderungen explizit an Live Copies gesendet werden, die von diesem Entwurf erben.
* Erlauben Sie dem Autor, **Site** erstellen zu verwenden. Dadurch kann der Benutzer die Sprachen einfach auswählen und die Struktur der Live Copy konfigurieren.
* Definieren Sie eine standardmäßige Rollout-Konfiguration für Live Copies, die mit dem Entwurf in Beziehung stehen.

Die Quelle für eine Live Copy kann entweder normale Seiten oder Seiten sein, die von einer Blueprint-Konfiguration erfasst werden. Beide sind gültige Anwendungsfälle.

Die Quelle bildet den Entwurf für die Live Copy. Der Blueprint wird durch eine der folgenden Maßnahmen definiert:

* [Erstellen einer Blueprint-Konfiguration](creating-live-copies.md#creating-a-blueprint-configuration) : Die Konfiguration definiert im Voraus die Seiten, die zum Erstellen der Live Copy verwendet werden sollen.
* [Erstellen einer Live Copy einer Seite](creating-live-copies.md#creating-a-live-copy-of-a-page)  - Die Seiten, die zum Erstellen der Live Copy (die Quellseiten) verwendet werden, sind die Musterseiten. Die Quellseite kann durch eine Blueprint-Konfiguration referenziert werden oder nicht.

### Rollout und Synchronisieren {#rollout-and-synchronize}

Ein Rollout ist die zentrale MSM-Aktion, die Live Copies mit ihren Quellen synchronisiert. Sie können Rollouts manuell ausführen oder sie werden automatisch durchgeführt.

* Es kann eine [Rollout-Konfiguration](#rollout-configurations) definiert werden, sodass spezifische [Ereignisse](live-copy-sync-config.md#rollout-triggers) eine automatische Ausführung eines Rollouts bewirken können.
* Beim Erstellen einer Blueprint-Seite können Sie den Befehl **[Rollout](creating-live-copies.md#rolling-out-a-blueprint)** verwenden, um Änderungen an der Live Copy zu übertragen.
   * Der Befehl **Rollout** ist auf einer Blueprint-Seite verfügbar, auf die in einer Blueprint-Konfiguration verwiesen wird.

   ![Rollout](../assets/live-copy-rollout.png)

* Beim Erstellen einer Live Copy-Seite können Sie den Befehl **[Synchronisieren](creating-live-copies.md#synchronizing-a-live-copy)** verwenden, um Änderungen von der Quelle in die Live Copy zu übernehmen.
   * Der Befehl **Synchronisieren** ist immer auf der Seite &quot;Live Copy&quot;verfügbar, unabhängig davon, ob die Quell-/Blueprint-Seite von einer Blueprint-Konfiguration erfasst wird.

   ![Synchronisieren](../assets/live-copy-synchronize.png)

### Rollout-Konfigurationen {#rollout-configurations}

Eine Rollout-Konfiguration definiert, wann und wie eine Live Copy mit dem Quellinhalt synchronisiert wird. Eine Rollout-Konfiguration besteht aus einem Auslöser und einer oder mehr Synchronisierungsaktionen:

* **Auslöser** - Ein Auslöser ist ein Ereignis, das die Live-Aktionssynchronisierung bewirkt, wie zum Beispiel die Aktivierung einer Quellseite. MSM definiert die Auslöser, die Sie verwenden können.
* **Synchronisierungsaktionen** : Synchronisierungsaktionen werden auf der Live Copy durchgeführt, um sie mit der Quelle zu synchronisieren. Beispiel-Aktionen sind das Kopieren von Inhalten, das Sortieren von untergeordneten Knoten und das Aktivieren der Seite &quot;Live Copy&quot;. MSM bietet eine Reihe von Synchronisierungsaktionen.

>[!NOTE]
>
>Sie können mithilfe der Java API benutzerdefinierte Aktionen für Ihre Instanz erstellen.

Rollout-Konfigurationen können wiederverwendet werden, sodass mehr als eine Live Copy dieselbe Rollout-Konfiguration verwenden kann. Mehrere [Rollout-Konfigurationen](live-copy-sync-config.md#installed-rollout-configurations) sind in einer Standardinstallation enthalten.

### Rollout-Konflikte  {#rollout-conflicts}

Rollouts können komplizierter werden, insbesondere wenn Autoren Inhalte sowohl in der Quelle als auch in der Live Copy bearbeiten. Daher ist es nützlich, sich bewusst zu sein, wie AEM mit etwaigen [Konflikten umgehen, die während der Rollout auftreten können.](rollout-conflicts.md)

### Aussetzen und Abbrechen der Vererbung und Synchronisierung {#suspending-and-cancelling-inheritance-and-synchronization}

Jede Seite und Komponente in einer Live Copy wird über eine Live-Beziehung mit ihrer Quellseite und Komponente verknüpft. Die Live-Beziehung konfiguriert die Synchronisierung von Live Copy-Inhalten aus der Quelle.

Sie können die Live Copy-Vererbung für eine Live Copy-Seite **Aussetzen** aussetzen, damit Sie die Seiteneigenschaften und Komponenten ändern können. Wenn Sie die Vererbung aussetzen, werden die Seiteneigenschaften und Komponenten nicht mehr mit der Quelle synchronisiert.

Bei der Bearbeitung einer einzelnen Seite können Autoren zu einer Komponente die **Vererbung abbrechen**. Wird die Vererbung abgebrochen, wird die Live-Beziehung unterbrochen und die Synchronisierung tritt bei dieser Komponente nicht auf. Das Abbrechen der Vererbung und Synchronisierung ist nützlich, wenn Unterabschnitte des Inhalts angepasst werden müssen.

### Trennen von Live Copies {#detaching-a-live-copy}

Sie können auch [eine Live Copy](creating-live-copies.md#detaching-a-live-copy) von ihrem Entwurf lösen, um alle Verbindungen zu entfernen.

>[!CAUTION]
>
>Die Trennaktion ist dauerhaft und kann nicht rückgängig gemacht werden.

Die Abtrennen-Aktion entfernt die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite dauerhaft. Alle MSM-relevanten Eigenschaften werden aus der Live Copy entfernt und die Live Copy-Seiten werden zu einer eigenständigen Kopie.

>[!TIP]
>
>Ausführliche Informationen einschließlich der damit verbundenen Auswirkungen auf Unter- und übergeordnete Seiten finden Sie unter [Live Copy trennen](creating-live-copies.md#detaching-a-live-copy).

## Standardschritte zur Verwendung von MSM {#standard-steps-for-using-msm}

Die folgenden Schritte beschreiben das Standardverfahren für die Verwendung von MSM zur Wiederverwendung von Inhalten und Synchronisierung von Änderungen an Live Copies.

1. Entwickeln Sie die Inhalte Der Quell-Site.
1. Legen Sie die zu verwendende Rollout-Konfiguration fest.

   1. MSM [installiert mehrere Rollout-Konfigurationen](live-copy-sync-config.md#installed-rollout-configurations), die eine Reihe von Anwendungsfällen erfüllen können.
   1. Sie können bei Bedarf optional eine [Rollout-Konfiguration erstellen](live-copy-sync-config.md#creating-a-rollout-configuration).

1. Legen Sie fest, wo Sie die [zu verwendenden Rollout-Konfigurationen angeben](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use) müssen und nehmen Sie bei Bedarf eine Konfiguration vor.
1. Falls erforderlich, erstellen Sie eine Blueprint-Konfiguration](creating-live-copies.md#creating-a-blueprint-configuration), die den Quellinhalt der Live Copy identifiziert.[
1. [Erstellen Sie eine Live Copy.](creating-live-copies.md#creating-a-live-copy)
1. Nehmen Sie bei Bedarf Änderungen am Quellinhalt vor. Sie sollten den normalen, von Ihrer Organisation etablierten Inhaltsprüfungs- und Genehmigungsprozess anwenden.
1. [Roll ](creating-live-copies.md#rolling-out-a-blueprint) outthe blueprint, or  [synchronize the Live ](creating-live-copies.md#synchronizing-a-live-copy) Copy with the changes.

## Anpassen von MSM {#customizing-msm}

MSM stellt Tools bereit, sodass Ihre Implementierung sich an die außergewöhnlichen Komplexitäten anpassen kann, die bei der Freigabe von Inhalten auftreten können.

* **Benutzerdefinierte Rollout-Konfigurationen**  -  [Erstellen Sie eine Rollout-](live-copy-sync-config.md#creating-a-rollout-configuration) Konfiguration, wenn die installierten Rollout-Konfigurationen Ihre Anforderungen nicht erfüllen. Sie können jeden verfügbaren Rollout-Auslöser und jede verfügbare Synchronisierungsaktion verwenden.

<!--
* **Custom Synchronization Actions** - [Create a custom synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) when the installed actions do not meet your specific application requirements. MSM provides a Java API for creating custom synchronization actions.
-->

## Best Practices {#best-practices}

Die Seite [Best Practices für MSM](best-practices.md) enthält wichtige Informationen zur Implementierung.
