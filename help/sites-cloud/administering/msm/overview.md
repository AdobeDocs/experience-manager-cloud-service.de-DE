---
title: Wiederverwenden von Inhalten - Multi Site Manager und Live Copy
description: Hier erhalten Sie eine Einführung in die Wiederverwendung von Inhalten mit AEM leistungsstarken Live Copies und den Funktionen von Multi Site Manager.
feature: Multi-Site-Manager
role: Administrator
exl-id: 22b4041f-1df9-4189-8a09-cbc0c89fbf2e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '2685'
ht-degree: 26%

---

# Wiederverwenden von Inhalten: Multi-Site-Manager und Live Copy {#multi-site-manager-and-live-copy}

Mit dem Multi-Site-Manager (MSM) können Sie denselben Site-Inhalt an mehreren Orten verwenden. MSM verwendet seine Live Copy-Funktion, um Folgendes zu erreichen.

* Mit MSM können Sie:
   * Inhalt ein- und ausblenden
   * Verwenden Sie diesen Inhalt in anderen Bereichen (über [Live Copies](#live-copies)) derselben oder anderer Sites erneut.
* MSM unterhält dann die Live-Beziehungen zwischen Ihrem Quellinhalt und seinen Live Copies, sodass:
   * Wenn Sie Änderungen am Quellinhalt vornehmen, werden die Quelle und die Live Copies synchronisiert.
   * Sie können nur Änderungen am Inhalt der Live Copies vornehmen, indem Sie die Live-Beziehung für einzelne Unterseiten und/oder Komponenten trennen.

Diese Seite bietet einen Überblick über die Wiederverwendung von Inhalten mit MSM. Auf den folgenden Seiten werden die damit verbundenen Probleme ausführlich beschrieben.

* [Erstellen und Synchronisieren von Live Copies](creating-live-copies.md)
* [Konsole „Live Copy-Übersicht“](live-copy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](live-copy-sync-config.md)
* [MSM-Rollout-Konflikte](rollout-conflicts.md)
* [Best Practices für MSM](best-practices.md)

## Mögliche Szenarien {#possible-scenarios}

Es gibt viele Anwendungsfälle für MSM und Live Copies. Einige Szenarien beinhalten:

* **Multinational – Globale zu lokalen Unternehmen**

   Ein typisches, von MSM unterstütztes Nutzungsszenario ist die Wiederverwendung von Inhalten auf verschiedenen multinationalen Sites in derselben Sprache. Dadurch kann der Kerninhalt wiederverwendet werden, gleichzeitig können aber auch nationale Varianten zugelassen werden.

   Beispielsweise wird der englische Abschnitt des Tutorials [WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) für Kunden in den USA erstellt. Der Großteil der Inhalte dieser Website kann auch für andere WKND-Sites verwendet werden, die englischsprachigen Kunden aus verschiedenen Ländern und Kulturen gerecht werden. Der Kerninhalt bleibt auf allen Sites gleich, wobei regionale Anpassungen vorgenommen werden können.

   Die folgende Struktur kann für Sites in den USA und Kanada verwendet werden. Beachten Sie, dass der Knoten `language-masters` die Übergeordnete Kopie nicht nur des englischen, sondern auch des anderen Sprachinhalts verwaltet. Dieser Inhalt kann neben Englisch als Grundlage für zusätzliche regionale Sprachinhalte verwendet werden.

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
   >Ein solches Beispiel finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-cloud/administering/translation/overview.md) .

* **National – Zentrale zu Zweigstellen**

   Alternativ kann ein Unternehmen mit einem Händlernetz separate Websites für seine einzelnen Händler anfordern, wobei es sich jeweils um eine Abwandlung der Hauptsite handelt, die vom Hauptbüro bereitgestellt wird. Dies kann für ein einziges Unternehmen mit mehreren regionalen Niederlassungen oder für ein landesweites Franchisesystem mit einem zentralen Franchisegeber und mehreren lokalen Franchisenehmern eingesetzt werden.

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

   MSM kann Versionen einer bestimmten Unterverzweigung erstellen. Beispielsweise kann eine Support-Untersite Details zu den verschiedenen Versionen eines bestimmten Produkts enthalten, wobei die Basisinformationen konstant bleiben und nur die aktualisierten Funktionen geändert werden müssen:

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
   >In einem solchen Szenario ist dies die Frage, ob eine einfache Kopie erstellt oder Live Copies verwendet werden soll, was eine Balance zwischen:
   >
   >* Wie viel des Kerninhalts muss über mehrere Versionen aktualisiert werden?
   >
   >und
   >
   >* Wie viel der einzelnen Kopien angepasst werden muss.


## MSM über die Benutzeroberfläche {#msm-from-the-ui}

MSM ist über die Benutzeroberfläche mit verschiedenen Optionen in der entsprechenden Konsole direkt zugänglich.

* **Website erstellen** (**Sites**)

   * MSM unterstützt Sie bei der Verwaltung mehrerer Websites, die gemeinsame Inhalte haben. Beispielsweise werden Websites oft für internationale Zielgruppen bereitgestellt, sodass der Großteil des Inhalts in allen Ländern verbreitet ist, wobei eine Untergruppe der Inhalte für das jeweilige Land spezifisch ist. Mit MSM können Sie [Live Copies erstellen, die automatisch eine oder mehrere Sites basierend auf Ihrer Quell-Site](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) aktualisieren. Dies hilft Ihnen auch dabei, eine gemeinsame Basisstruktur zu erzwingen, die gemeinsamen Inhalte auf mehreren Sites zu nutzen, ein gemeinsames Erscheinungsbild zu erreichen und die Maßnahmen auf die Verwaltung der Inhalte zu konzentrieren, die sich auf den verschiedenen Sites tatsächlich unterscheiden. Erstellen einer Site auf diese Weise:
      * Für die Angabe der Quelle ist eine vordefinierte Blueprint-Konfigurationen erforderlich.
      * Erstellt eine Live Copy der (vordefinierten) Quelle.
      * Stellt dem Benutzer eine **Rollout**-Schaltfläche bereit.

* **Live Copy erstellen** (**Sites**)

   * Mit MSM können Sie [eine Ad-hoc-Live Copy (eine einmalige) Live Copy einer einzelnen Seite oder Unterverzweigung einer Website erstellen.](creating-live-copies.md#creating-a-live-copy-of-a-page) Beispielsweise durch Duplizieren einer Unterverzweigung, um Informationen über eine neue/aktualisierte Version eines Produkts bereitzustellen. Erstellen einer Live Copy auf diese Weise:
      * Erstellt eine Ad-hoc-Live Copy (keine Blueprint-Konfiguration erforderlich).
      * Kann verwendet werden, um (sofort) eine Live Copy einer beliebigen Seite/Verzweigung zu erstellen.
      * Erfordert **Synchronisieren** (stellt nicht die Schaltfläche **Rollout** bereit).

* **Eigenschaften anzeigen** (**Sites**)

   * Gegebenenfalls hilft Ihnen diese Option bei der Überwachung Ihrer Live Copy](creating-live-copies.md#monitoring-your-live-copy) durch Angabe von Informationen zur zugehörigen **Live Copy** oder **Blueprint**.[

* **Verweise** (**Sites**)

   * Die Leiste [Verweise](/help/sites-cloud/authoring/getting-started/basic-handling.md#references) enthält Informationen zu **Live Copies** sowie Zugriff auf entsprechende Aktionen.

* **Live Copy-Übersicht** (**Sites**)

   * In dieser Konsole können Sie [Ihren Blueprint und seine Live Copies anzeigen und verwalten.](live-copy-overview.md)

* **Blueprints** (**Tools** – **Sites**)

   * Diese Konsole ermöglicht Ihnen die [Erstellung und Verwaltung Ihrer Blueprint-Konfigurationen.](creating-live-copies.md#creating-a-blueprint-configuration)

>[!NOTE]
>
>Aspekte der MSM-Funktionalität werden in mehreren anderen AEM Funktionen wie Launches verwendet. In diesen Fällen wird die Live Copy von dieser Funktion verwaltet.

### Verwendete Bedingungen {#terms-used}

Als Einführung bietet die folgende Tabelle einen Überblick über die wichtigsten Begriffe, die mit MSM verwendet werden. Diese werden in den nachfolgenden Abschnitten und Seiten ausführlicher behandelt.

| Begriff | Definition | Weitere Details |
|---|---|---|
| Quelle | Die ursprünglichen Seiten, die als Grundlage für Live Copies verwendet werden | Synonym mit Blueprint- und/oder Blueprint-Seiten |
| Live Copy  | Die Kopie (der Quelle), die durch Synchronisierungsaktionen verwaltet wird, wie in den Rollout-Konfigurationen definiert |  |
| Live Copy-Konfiguration | Definition der Konfigurationsdetails für eine Live Copy |  |
| Live-Beziehung | Effektive Definition der Vererbung für eine bestimmte Ressource, d. h. die Verbindung(en) zwischen der Quelle und Live Copies | Stellt sicher, dass Änderungen an der Quelle mit der Live Copy synchronisiert werden können |
| Blueprint | Synonym mit Quelle | Kann durch eine Blueprint-Konfiguration definiert werden |
| Blueprint-Konfiguration | Vordefinierte Konfiguration, die den Quellpfad angibt | Wenn in einer Blueprint-Konfiguration auf eine Blueprint-Seite verwiesen wird, ist der Befehl &quot;Rollout&quot;verfügbar |
| Kapitel | Die Abschnitte des Blueprints, die in die Live Copy aufgenommen werden sollen | Dies sind im Allgemeinen Unterseiten des Stamms |
| Synchronisierung | Der generische Begriff für die Synchronisierung von Inhalten zwischen der Quelle und den Live Copies (sowohl **Rollout**- als auch **Synchronisieren**-Optionen) |  |
| Rollout | Synchronisiert von der Quelle mit der Live Copy | Kann von einem Autor (auf einer Blueprint-Seite) oder von einem Systemereignis (wie durch die Rollout-Konfiguration definiert) ausgelöst werden |
| Rollout-Konfiguration | Regeln, die bestimmen, welche Eigenschaften wie und wann synchronisiert werden |  |
| Synchronisieren | Eine manuelle Synchronisierungsanforderung, erstellt über die Live Copy-Seiten |  |
| Vererbung | Eine Live Copy-Seite/-Komponente erbt Inhalt von ihrer Quellseite/-komponente, wenn eine Synchronisierung erfolgt |  |
| Aussetzen | Entfernt vorübergehend die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite |  |
| Trennen | Entfernt dauerhaft die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite |  |
| Zurücksetzen | Zurücksetzen einer Live Copy-Seite, um alle Vererbungsabbrüche zu entfernen und die Seite wieder in denselben Status wie die Quellseite zu versetzen | Eine Rücksetzung wirkt sich auf alle von Ihnen durchgeführten Änderungen an den Seiteneigenschaften, am Absatzsystem und an den Komponenten aus. |
| Flach | Eine Live Copy einer einzelnen Seite |  |
| Tief | Eine Live Copy einer Seite mit ihren untergeordneten Seiten |  |

<!--
>[!TIP]
>
>See [Overview of the Java API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) for the object names.
-->

## Live Copies {#live-copies}

Eine MSM Live Copy ist eine Kopie spezifischer Site-Inhalte, für die eine Live-Beziehung zur ursprünglichen Quelle beibehalten wird:

* Die Live Copy übernimmt Inhalte von ihrer Quelle.
* Die Synchronisierung führt die tatsächliche Übertragung von Inhalten durch, wenn Änderungen an der Quelle vorgenommen werden.
* Eine Live Copy kann wie folgt betrachtet werden:
   * Flach: eine einzelne Seite
   * Tief: die Seite mit ihren untergeordneten Seiten
* Synchronisierungsregeln, so genannte Rollout-Konfigurationen, bestimmen, welche Eigenschaften synchronisiert werden und wann die Synchronisierung erfolgt.

Im vorherigen Beispiel ist `/content/wknd/language-masters/en` die globale Übergeordnete Site in englischer Sprache. Um den Inhalt dieser Website wiederzuverwenden, werden MSM-Live Copies erstellt:

* Der Inhalt unter `/content/wknd/language-masters/en` ist die Quelle.
* Der Inhalt unter `/content/wknd/language-masters/en` wird unter die Knoten `/content/wknd/us/en/` und `/content/wknd/ca/en` kopiert. Dies sind die Live Copies.
* Autoren nehmen Änderungen an Seiten unter `/content/wknd/language-masters/en` vor.
* Wenn diese Änderungen ausgelöst werden, synchronisiert MSM diese Änderungen mit den Live Copies.

### Live Copies – Komposition {#live-copies-composition}

>[!NOTE]
>
>Die Diagramme und Beschreibungen in diesem Abschnitt stellen Momentaufnahmen potenzieller Live Copies dar. Sie erheben keinen Anspruch auf Vollständigkeit, stellen jedoch einen Überblick bereit, um bestimmte Merkmale hervorzuheben.

Wenn Sie zum ersten Mal eine Live Copy erstellen, werden die ausgewählten Quellseiten 1:1 in der Live Copy angezeigt. Danach können neue Ressourcen (Seiten und/oder Absätze) auch direkt in der Live Copy erstellt werden. Daher ist es nützlich, sich dieser Varianten bewusst zu sein und zu erfahren, wie sie sich auf die Synchronisierung auswirken. Mögliche Kompositionen umfassen:

* [Live Copy mit Live Copy-fremden Seiten](#live-copy-with-non-live-copy-pages)
* [Verschachtelte Live Copies](#nested-live-copies)

Die grundlegende Form der Live Copy hat:

* Live Copy-Seiten, die die ausgewählten Quellseiten 1:1 widerspiegeln.
* Eine Konfigurationsdefinition
* Eine zu jeder Ressource festgelegte Live-Beziehung:
   * Verknüpfen Sie die Live Copy-Ressource mit ihrem Blueprint/ihrer Quelle.
   * werden bei der Realisierung von Vererbung und Rollout verwendet.

Änderungen können entsprechend den Anforderungen [synchronisiert](creating-live-copies.md#synchronizing-your-live-copy) werden.

![Übersicht über die Live Copy-Komposition](../assets/live-copy-composition.png)

#### Live Copy mit nicht Live Copy-Seiten {#live-copy-with-non-live-copy-pages}

Wenn Sie eine Live Copy in AEM erstellen, können Sie die Live Copy-Verzweigung sehen und durch sie navigieren und die normale AEM in der Live Copy-Verzweigung verwenden. Dies bedeutet, dass Sie (oder ein Prozess) neue Ressourcen (Seiten und/oder Absätze) innerhalb der Live Copy erstellen können. z. B. ein Produkt für eine bestimmte Region oder ein bestimmtes Land.

* Solche Ressourcen verfügen über keine Live-Beziehung zu Quell-/Blueprint-Seiten und werden nicht synchronisiert.
* Es können Szenarien auftreten, die MSM als Spezialfälle behandelt. Beispiel: Wenn Sie (oder ein Prozess) eine Seite mit derselben Position und demselben Namen sowohl in der Quell-/Blueprint- als auch in der Live Copy-Verzweigung erstellen. Weitere Informationen zu solchen Situationen finden Sie unter [MSM-Rollout-Konflikte](rollout-conflicts.md) .

![Live Copy mit Nicht-Live Copy-Seiten](../assets/live-copy-with-non-live-copy-pages.png)

#### Verschachtelte Live Copies {#nested-live-copies}

Wenn Sie (oder ein Prozess) eine [neue Seite in einer vorhandenen Live Copy](#live-copy-with-non-live-copy-pages) erstellen, kann diese neue Seite auch als Live Copy eines anderen Blueprints eingerichtet werden. Dies wird als verschachtelte Live Copy bezeichnet. In verschachtelten Live Copies wird das Verhalten der zweiten oder inneren Live Copy durch die erste oder äußere Live Copy wie folgt beeinflusst:

* Ein tiefer Rollout, der für die Live Copy der obersten Ebene ausgelöst wird, kann in die verschachtelte Live Copy fortgesetzt werden.
* Alle Verknüpfungen zwischen den Quellen werden in den Live Copies neu geschrieben.

Beispielsweise werden Links, die von der zweiten zum ersten Blueprint zeigen, als Links umgeschrieben, die von der verschachtelten/zweiten Live Copy auf die erste Live Copy verweisen.

![Verschachtelte Live Copies](../assets/live-copy-nested.png)

>[!NOTE]
>
>Wenn Sie eine Seite innerhalb der Live Copy-Verzweigung verschieben oder umbenennen, wird dies als verschachtelte Live Copy behandelt, damit AEM die Beziehungen verfolgen kann.

#### Gestapelte Live Copies {#stacked-live-copies}

Eine Live Copy wird als gestapelte Live Copy bezeichnet, wenn sie als untergeordnetes Element einer flachen Live Copy erstellt wird. Sie verhält sich auf dieselbe Weise wie eine [verschachtelte Live Copy](#nested-live-copies).

### Quelle, Blueprints und Blueprint-Konfigurationen {#source-blueprints-and-blueprint-configurations}

Jede Seite oder jeder Zweig von Seiten kann als Quelle einer Live Copy verwendet werden. MSM ermöglicht Ihnen allerdings die Definition einer Blueprint-Konfiguration, die einen Quellpfad angibt. Die Vorteile einer Blueprint-Konfiguration sind, dass sie:

* Lassen Sie zu, dass der Autor die Option **Rollout** auf einem Blueprint verwendet. Dies bedeutet, dass Änderungen explizit an Live Copies gesendet werden, die von diesem Blueprint erben.
* Lassen Sie den Autor zu, **Site** erstellen. Dadurch kann der Benutzer einfach Sprachen auswählen und die Struktur der Live Copy konfigurieren.
* Definieren Sie eine standardmäßige Rollout-Konfiguration für Live Copies, die eine Beziehung zum Blueprint haben.

Die Quelle für eine Live Copy kann entweder normale Seiten oder Seiten sein, die von einer Blueprint-Konfiguration erfasst werden. Beide sind gültige Anwendungsfälle.

Die Quelle bildet den Blueprint für die Live Copy. Der Blueprint wird durch eine der folgenden Maßnahmen definiert:

* [Erstellen einer Blueprint-Konfiguration](creating-live-copies.md#creating-a-blueprint-configuration)  - Die Konfiguration definiert im Voraus die Seiten, die zum Erstellen der Live Copy verwendet werden sollen.
* [Erstellen einer Live Copy einer Seite](creating-live-copies.md#creating-a-live-copy-of-a-page)  - Die zum Erstellen der Live Copy (der Quellseiten) verwendeten Seiten sind Blueprint-Seiten. Die Quellseite wird möglicherweise von einer Blueprint-Konfiguration referenziert oder nicht.

### Rollout und Synchronisieren {#rollout-and-synchronize}

Ein Rollout ist die zentrale MSM-Aktion, die Live Copies mit ihren Quellen synchronisiert. Sie können Rollouts manuell ausführen oder sie werden automatisch durchgeführt.

* Es kann eine [Rollout-Konfiguration](#rollout-configurations) definiert werden, sodass spezifische [Ereignisse](live-copy-sync-config.md#rollout-triggers) eine automatische Ausführung eines Rollouts bewirken können.
* Beim Erstellen einer Blueprint-Seite können Sie den Befehl **[Rollout](creating-live-copies.md#rolling-out-a-blueprint)** verwenden, um Änderungen an die Live Copy zu übertragen.
   * Der Befehl **Rollout** ist auf einer Blueprint-Seite verfügbar, auf die von einer Blueprint-Konfiguration verwiesen wird.

   ![Rollout](../assets/live-copy-rollout.png)

* Beim Erstellen einer Live Copy-Seite können Sie den Befehl **[Synchronisieren](creating-live-copies.md#synchronizing-a-live-copy)** verwenden, um Änderungen von der Quelle an die Live Copy zu ziehen.
   * Der Befehl **Synchronisieren** ist immer auf der Live Copy-Seite verfügbar, unabhängig davon, ob die Quell-/Blueprint-Seite von einer Blueprint-Konfiguration erfasst wird.

   ![Synchronisieren](../assets/live-copy-synchronize.png)

### Rollout-Konfigurationen {#rollout-configurations}

Eine Rollout-Konfiguration definiert, wann und wie eine Live Copy mit dem Quellinhalt synchronisiert wird. Eine Rollout-Konfiguration besteht aus einem Auslöser und einer oder mehr Synchronisierungsaktionen:

* **Auslöser** - Ein Auslöser ist ein Ereignis, das die Live-Aktionssynchronisierung bewirkt, wie zum Beispiel die Aktivierung einer Quellseite. MSM definiert die Auslöser, die Sie verwenden können.
* **Synchronisierungsaktionen**  - Synchronisierungsaktionen werden für die Live Copy ausgeführt, um sie mit der Quelle zu synchronisieren. Beispielaktionen sind das Kopieren von Inhalten, das Sortieren von untergeordneten Knoten und das Aktivieren der Live Copy-Seite. MSM bietet eine Reihe von Synchronisierungsaktionen.

>[!NOTE]
>
>Sie können mithilfe der Java API benutzerdefinierte Aktionen für Ihre Instanz erstellen.

Rollout-Konfigurationen können wiederverwendet werden, sodass mehr als eine Live Copy dieselbe Rollout-Konfiguration verwenden kann. Mehrere [Rollout-Konfigurationen](live-copy-sync-config.md#installed-rollout-configurations) sind in einer Standardinstallation enthalten.

### Rollout-Konflikte {#rollout-conflicts}

Rollouts können kompliziert werden, insbesondere wenn Autoren Inhalte sowohl in der Quelle als auch in der Live Copy bearbeiten. Daher ist es nützlich, sich darüber im Klaren zu sein, wie AEM alle [Konflikte handhabt, die während des Rollouts auftreten können.](rollout-conflicts.md)

### Aussetzen und Abbrechen der Vererbung und Synchronisierung {#suspending-and-cancelling-inheritance-and-synchronization}

Jede Seite und Komponente in einer Live Copy ist über eine Live-Beziehung mit ihrer Quellseite und Komponente verknüpft. Die Live-Beziehung konfiguriert die Synchronisierung von Live Copy-Inhalt aus der Quelle.

Sie können **Aussetzen** der Live Copy-Vererbung für eine Live Copy-Seite aussetzen, damit Sie Seiteneigenschaften und -komponenten ändern können. Wenn Sie die Vererbung aussetzen, werden die Seiteneigenschaften und Komponenten nicht mehr mit der Quelle synchronisiert.

Bei der Bearbeitung einer einzelnen Seite können Autoren zu einer Komponente die **Vererbung abbrechen**. Wird die Vererbung abgebrochen, wird die Live-Beziehung unterbrochen und die Synchronisierung tritt bei dieser Komponente nicht auf. Das Abbrechen der Vererbung und Synchronisierung ist nützlich, wenn Unterabschnitte des Inhalts angepasst werden müssen.

### Trennen von Live Copies {#detaching-a-live-copy}

Sie können auch [eine Live Copy](creating-live-copies.md#detaching-a-live-copy) aus ihrem Blueprint entfernen, um alle Verbindungen zu entfernen.

>[!CAUTION]
>
>Die Trennaktion ist dauerhaft und kann nicht rückgängig gemacht werden.

Die Aktion &quot;Trennen&quot;entfernt die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite dauerhaft. Alle MSM-relevanten Eigenschaften werden aus der Live Copy entfernt und die Live Copy-Seiten werden zu einer eigenständigen Kopie.

>[!TIP]
>
>Ausführliche Informationen, einschließlich der damit verbundenen Auswirkungen auf Unter- und übergeordnete Seiten, finden Sie unter [Trennen einer Live Copy](creating-live-copies.md#detaching-a-live-copy) .

## Standardschritte zur Verwendung von MSM {#standard-steps-for-using-msm}

Die folgenden Schritte beschreiben das Standardverfahren für die Verwendung von MSM zur Wiederverwendung von Inhalten und Synchronisierung von Änderungen an Live Copies.

1. Entwickeln Sie die Inhalte Der Quell-Site.
1. Legen Sie die zu verwendende Rollout-Konfiguration fest.

   1. MSM [installiert mehrere Rollout-Konfigurationen](live-copy-sync-config.md#installed-rollout-configurations), die eine Reihe von Anwendungsfällen erfüllen können.
   1. Sie können bei Bedarf optional eine [Rollout-Konfiguration erstellen](live-copy-sync-config.md#creating-a-rollout-configuration).

1. Legen Sie fest, wo Sie die [zu verwendenden Rollout-Konfigurationen angeben](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use) müssen und nehmen Sie bei Bedarf eine Konfiguration vor.
1. Falls erforderlich, erstellen Sie [eine Blueprint-Konfiguration](creating-live-copies.md#creating-a-blueprint-configuration), die den Quellinhalt der Live Copy identifiziert.
1. [Erstellen Sie eine Live Copy.](creating-live-copies.md#creating-a-live-copy)
1. Nehmen Sie bei Bedarf Änderungen am Quellinhalt vor. Sie sollten den normalen, von Ihrer Organisation etablierten Inhaltsprüfungs- und Genehmigungsprozess anwenden.
1. [Roll ](creating-live-copies.md#rolling-out-a-blueprint) aus dem Blueprint oder  [synchronisiere die Live ](creating-live-copies.md#synchronizing-a-live-copy) Copy mit den Änderungen.

## Anpassen von MSM {#customizing-msm}

MSM stellt Tools bereit, sodass Ihre Implementierung sich an die außergewöhnlichen Komplexitäten anpassen kann, die bei der Freigabe von Inhalten auftreten können.

* **Benutzerdefinierte Rollout-Konfigurationen**  -  [Erstellen Sie eine Rollout-](live-copy-sync-config.md#creating-a-rollout-configuration) Konfiguration, wenn die installierten Rollout-Konfigurationen nicht Ihren Anforderungen entsprechen. Sie können jeden verfügbaren Rollout-Auslöser und jede verfügbare Synchronisierungsaktion verwenden.

<!--
* **Custom Synchronization Actions** - [Create a custom synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) when the installed actions do not meet your specific application requirements. MSM provides a Java API for creating custom synchronization actions.
-->

## Best Practices {#best-practices}

Die Seite [Best Practices für MSM](best-practices.md) enthält wichtige Informationen zur Implementierung.
