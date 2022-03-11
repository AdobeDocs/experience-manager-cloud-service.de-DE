---
title: Grundlegendes zu Cloud Manager und dem Arbeitsablauf für die schnelle Site-Erstellung
description: Erfahren Sie mehr über Cloud Manager und wie dieser den neuen Prozess zur Erstellung von Schnellseiten miteinander verbindet.
exl-id: 5d264078-e552-48ca-8d82-294a646e6b1f
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 2%

---

# Grundlegendes zu Cloud Manager und dem Arbeitsablauf für die schnelle Site-Erstellung {#understand-cloud-manager}

Erfahren Sie mehr über Cloud Manager und wie dieser den neuen Prozess zur Erstellung von Schnellseiten miteinander verbindet.

>[!TIP]
>
>Wenn es sich bei Ihrer Rolle ausschließlich um eine Front-End-Entwicklung handelt, können Sie den Artikel überspringen. [Git-Repository-Zugriffsinformationen abrufen](retrieve-access.md) in dieser Journey.
>
>Wenn Sie ein AEM Administrator, ein Cloud Manager-Administrator, sowohl für die Frontend-Entwicklungs- als auch für Administratoraufgaben verantwortlich sind oder einfach den End-to-End-Prozess für die Front-End-Entwicklung im AEM verstehen möchten, lesen Sie das aktuelle Dokument weiter und fahren Sie mit dieser Journey fort.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie das AEM Tool für die schnelle Site-Erstellung funktioniert, und erhalten einen Überblick über den gesamten Fluss. Nach dem Lesen sollten Sie:

* Erfahren Sie, wie AEM Sites und Cloud Manager zusammenarbeiten, um die Front-End-Entwicklung zu erleichtern.
* Erfahren Sie, wie der Front-End-Anpassungsschritt vollständig von AEM entkoppelt ist und kein AEM Wissen erfordert.

Dieses Dokument konzentriert sich auf das Verständnis dieser grundlegenden Bestandteile der Schnellsite-Erstellungslösung, bevor Sie zum nächsten Schritt der Journey übergehen, in dem Sie mit der Konfiguration beginnen.

Es wird zwar empfohlen, diese Journey Schritt für Schritt durchzuführen. Wenn Sie bereits wissen, dass AEM Sites und Cloud Manager zusammenarbeiten und direkt mit der Konfiguration beginnen möchten, können Sie [zum nächsten Schritt des Journey überspringen.](create-site.md)

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt sowohl für den AEM-Administrator als auch für den Cloud Manager-Administrator.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Es gibt mehrere Anforderungen, bevor Sie mit der Erstellung und Anpassung von Sites mit dem Tool zur schnellen Site-Erstellung beginnen.

Da diese Journey sowohl für Frontend-Entwickler als auch für Administratoren und Kombinationen aller Rollen gedacht ist, sind hier die Anforderungen für beide aufgeführt.

Es ist wichtig zu verstehen, dass für den Frontend-Entwickler kein AEM Zugriff oder Wissen erforderlich ist.

### Kenntnisse {#knowledge}

| Kenntnisse | Rolle |
|---|---|
| Grundlegendes zu den Standardwerkzeugen und -prozessen der Front-End-Entwicklung | Frontend-Entwickler |
| Grundlegende Kenntnisse der Erstellung und Verwaltung von Websites in AEM | AEM-Administrator |
| Grundlegendes zu Cloud Manager | Cloud Manager-Administrator |

Für den Frontend-Entwickler ist kein AEM Wissen erforderlich.

### Tools {#tools}

| Tool | Rolle |
|---|---|
| Bevorzugte Front-End-Entwicklungsumgebung | Frontend-Entwickler |
| npm | Frontend-Entwickler |
| Webpack | Frontend-Entwickler |
| Zugriff auf Cloud Manager | Cloud Manager-Administrator |
| Seien Sie Mitglied von **Business Owner** Rolle in Cloud Manager | Cloud Manager-Administrator |
| Sys-Administrator in Cloud Manager sein | Cloud Manager-Administrator |
| Zugang zur Admin Console | Cloud Manager-Administrator |
| Mitglied der **Bereitstellungsmanager** Rolle in Cloud Manager | Cloud Manager-Administrator |
| Mitglied der **Bereitstellungsmanager** Rolle in Cloud Manager | Frontend-Entwickler |

Für den Frontend-Entwickler ist keine Verwendung von AEM erforderlich.

>[!TIP]
>
>Wenn Sie nicht mit Cloud Manager-Rollen und Rollenverwaltung vertraut sind, finden Sie weitere Informationen im Dokument Rollenbasierte Berechtigungen im Abschnitt [Zusätzliche Ressourcen](#additional-resources) Abschnitt.

## Cloud Manager {#cloud-manager}

Cloud Manager ist eine wesentliche Komponente AEM as a Cloud Service und dient als zentraler Einstiegspunkt für die Plattform.

Um Kunden mit Enterprise-Entwicklungs-Setups zu unterstützen, ist AEM as a Cloud Service vollständig in Cloud Manager und die speziell dafür vorgesehenen CI/CD-Pipelines integriert. Das Tool zur schnellen Site-Erstellung erweitert diese Funktionen, um dedizierte Front-End-Entwicklungs-Pipelines zu unterstützen.

Für diese Journey ist kein vollständiges Verständnis von Cloud Manager erforderlich. Auf hoher Ebene besteht Cloud Manager aus mehreren Strukturebenen.

![Cloud Manager-Struktur](assets/cloud-manager-structure.png)

* **MANDANTEN** - Jeder Kunde hat einen Mandanten.
* **PROGRAMME** - Jeder Mandant verfügt über ein oder mehrere Programme, die häufig die lizenzierten Lösungen des Kunden widerspiegeln.
* **UMGEBUNGEN** - Jedes Programm verfügt über mehrere Umgebungen, wie z. B. die Produktion für Live-Inhalte, eine für Staging- und eine für Entwicklungszwecke.
* **REPOSITORY** - Die Umgebungen verfügen über Git-Repositorys, in denen Anwendung und Frontend-Code gepflegt werden.
* **TOOLS UND WORKFLOWS** - Pipelines verwalten die Bereitstellung von Code aus den Repositorys in den Umgebungen.

Ein Beispiel ist oft hilfreich, um diese Hierarchie zu kontextualisieren.

* WKND Travel and Adventure Enterprises könnte ein **Mandant** , das sich auf die Medien zum Thema Reisen konzentriert.
* Der Mieter von WKND Travel and Adventure Enterprises könnte über zwei **Programme**: ein Sites-Programm für WKND Magazine und ein Assets-Programm für WKND Media.
* Die WKND Magazine- und WKND-Medienprogramme hätten beide Entwicklungs-, Staging- und Produktionsprogramme **Umgebungen**.

## Der Front-End-Entwicklungs-Fluss zur schnellen Site-Erstellung {#flow}

Der Gesamtfluss ist einfach und intuitiv, auch wenn Sie noch keine umfassende Erfahrung mit Cloud Manager haben.

1. Der AEM Administrator meldet sich in eine AEM Umgebung an und erstellt mithilfe einer Site-Vorlage eine neue Site.
1. Der Cloud Manager-Administrator erstellt eine Frontend-Pipeline in Cloud Manager. Die Pipeline koordiniert die Bereitstellung von Code aus einem Git-Repository in einer AEM Umgebung.
1. Der AEM Administrator exportiert das Site-Design aus der AEM Instanz des Programms und stellt es dem Frontend-Entwickler bereit.
1. Der Cloud Manager-Administrator gewährt dem Frontend-Entwickler Zugriff auf das AEM Git-Repository, in dem Anpassungen vorgenommen werden können.
1. Der Frontend-Entwickler ruft Zugriffsberechtigungen ab, um auf Git und die Pipeline zuzugreifen.
1. Der Frontend-Entwickler passt das Design an, testet es mithilfe eines Proxys mit tatsächlichem Inhalt von der Site und sendet die Änderungen an das Git-Repository.
1. Der Frontend-Entwickler führt die Pipeline aus, um die Designanpassungen in der Produktionsumgebung des Programms bereitzustellen.

![Schneller Site-Erstellungsfluss](assets/qsc-flow.png)

Der Hauptvorteil der Verwendung des Tools für die schnelle Site-Erstellung besteht darin, dass der reine Frontend-Entwickler nur für die tatsächliche Anpassung verantwortlich ist. Der Frontend-Entwickler hat keine Interaktion mit AEM oder benötigt AEM.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der Journey zur AEM Schnellseitenerstellung abgeschlossen haben, sollten Sie Folgendes tun:

* Erfahren Sie, wie AEM Sites und Cloud Manager zusammenarbeiten, um die Front-End-Entwicklung zu erleichtern.
* Erfahren Sie, wie der Front-End-Anpassungsschritt vollständig von AEM entkoppelt ist und kein AEM Wissen erfordert.

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit der Journey zur AEM SchnellSite-Erstellung fort, indem Sie das Dokument erneut überprüfen. [Erstellen einer Site aus Vorlage,](create-site.md) Hier erfahren Sie, wie Sie mithilfe einer Vorlage schnell eine neue AEM erstellen können.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zur Schnellseitenerstellung zu wechseln, indem Sie das Dokument lesen [Erstellen einer Site aus Vorlage,](create-site.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Wenn Sie weitere Details zu den Funktionen von Cloud Manager wünschen, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
* [Rollenbasierte Berechtigungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html) - Cloud Manager verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Weitere Informationen zu diesen Rollen und deren Verwaltung finden Sie in diesem Dokument .
* [npm](https://www.npmjs.com) - AEM Designs, die zum schnellen Erstellen von Sites verwendet werden, basieren auf npm.
* [Webpack](https://webpack.js.org) - AEM Themen, die zum schnellen Erstellen von Sites verwendet werden, basieren auf Webpack.
