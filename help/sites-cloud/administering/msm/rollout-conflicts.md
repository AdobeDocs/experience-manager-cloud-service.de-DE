---
title: Rollout-Konflikte
description: Erfahren Sie, wie Sie Rollout-Konflikte in Multi-Site Manager verwalten und lösen.
feature: Multi Site Manager
role: Admin
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
solution: Experience Manager Sites
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 99%

---

# Rollout-Konflikte {#msm-rollout-conflicts}

Konflikte sind möglich, wenn neue Seiten mit demselben Seitennamen im Blueprint-Zweig und in einem abhängigen Live Copy-Zweig erstellt werden. Solche Konflikte müssen beim Rollout gehandhabt und gelöst werden.

## Konfliktbehandlung {#conflict-handling}

Wenn Konfliktseiten (in den Blueprint- und Live Copy-Zweigen) vorhanden sind, ermöglicht Ihnen MSM die Definition, wie (oder ob überhaupt) dieser Konflikt gelöst werden soll.

Um sicherzustellen, dass der Rollout nicht gesperrt ist, können mögliche Definitionen Folgendes umfassen:

* Welche Seite (Blueprint oder Live Copy) während des Rollouts Vorrang hat
* Welche Seiten werden umbenannt und wie
* Wie sich dies auf veröffentlichte Inhalte auswirkt

Das Standardverhalten des vorkonfigurierten Adobe Experience Manager (AEM) sieht vor, dass veröffentlichte Inhalte nicht beeinträchtigt werden. Wenn also eine Seite, die im Live Copy-Zweig manuell erstellt wurde, veröffentlicht worden ist, wird dieser Inhalt nach der Konfliktbehandlung und dem Rollout auch weiterhin veröffentlicht.

Neben der Standardfunktion können auch benutzerdefinierte Konflikt-Handler hinzugefügt werden, um verschiedene Regeln zu implementieren. Diese können auch die Veröffentlichung von Aktionen als individuellen Prozess ermöglichen.

### Beispiel-Szenario {#example-scenario}

In den folgenden Abschnitten wird ein Beispiel für eine neue Seite `b` verwendet, die sowohl im Blueprint als auch im Live Copy-Zweig (manuell) erstellt wurde, um die verschiedenen Methoden der Konfliktlösung zu veranschaulichen:

* Blueprint: `/b`

  Eine Hauptseite mit einer untergeordneten Seite, `bp-level-1`

* Live Copy: `/b`

  Eine im Live Copy-Zweig manuell erstellte Seite; mit einer untergeordneten Seite, `lc-level-1`

   * Bei Veröffentlichung als `/b` aktiviert, zusammen mit der untergeordneten Seite

#### Vor dem Rollout {#before-rollout}

|  | Blueprint vor dem Rollout | Live Copy vor dem Rollout | Vor dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar | In der Blueprint-Verzweigung erstellt, bereit für den Rollout | Manuell im Live Copy-Zweig erstellt | Enthält den Inhalt der Seite `b`, die in der Live Copy-Verzweigung manuell erstellt wurde |
| Wert | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Manuell im Live Copy-Zweig erstellt | Enthält den Inhalt der Seite `child-level-1`, die in der Live Copy-Verzweigung manuell erstellt wurde |

## Rollout-Manager und Konfliktbehandlung {#rollout-manager-and-conflict-handling}

Mit dem Rollout-Manager können Sie das Konflikt-Management aktivieren oder deaktivieren.

Dies erfolgt mithilfe der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) von **Day CQ WCM Rollout Manager**. Legen Sie den Wert **Konflikt mit manuell erstellten Seiten beheben** (`rolloutmgr.conflicthandling.enabled`) auf „true“ fest, wenn der Rollout-Manager Konflikte von einer Seite bewältigen soll, die in der Live Copy mit einem in der Blueprint vorhandenen Namen erstellt wurde.

AEM verfügt über ein [vordefiniertes Verhalten, wenn das Konflikt-Management deaktiviert wurde](#behavior-when-conflict-handling-deactivated).

## Konflikt-Handler {#conflict-handlers}

AEM nutzt Konflikt-Handler zum Lösen von Seitenkonflikten, die beim Rollout von Inhalten von einer Blueprint zu einer Live Copy vorliegen. Das Umbenennen von Seiten ist die übliche (aber nicht die einzige) Methode, um solche Konflikte zu lösen. Es können mehrere Konflikt-Handler verwendet werden, um eine Auswahl verschiedener Verhaltensweisen zu ermöglichen.

AEM bietet:

* Den [standardmäßigen Konflikt-Handler](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* Die Möglichkeit, einen [benutzerdefinierten Handler](#customized-handlers) zu implementieren
* Den Service-Ranking-Mechanismus, mit dem Sie die Priorität jedes einzelnen Handlers festlegen können
   * Der Service mit dem höchsten Ranking wird verwendet.

### Standard-Konflikt-Handler {#default-conflict-handler}

Der standardmäßige Konflikt-Handler ist `ResourceNameRolloutConflictHandler`.

* Mit diesem Handler hat die Blueprint-Seite Vorrang.
* Das Service-Ranking für diesen Handler ist niedrig eingestellt. Das heißt, unterhalb des Standardwerts für die Eigenschaft `service.ranking`, weil man davon ausgeht, dass kundenspezifische Handler ein höheres Ranking benötigen. Allerdings ist das Ranking nicht das absolute Minimum, um bei Bedarf Flexibilität zu gewährleisten.

Dieser Konflikt-Handler hat Vorrang vor dem Blueprint. Die Live Copy-Seite `/b` wird beispielsweise innerhalb des Live Copy-Zweiges nach `/b_msm_moved` verschoben.

* Live Copy: `/b`

  wird innerhalb der Live Copy nach `/b_msm_moved` verschoben. Dies dient als Sicherung und stellt sicher, dass keine Inhalte verloren gehen.

   * `lc-level-1` wird nicht verschoben.

* Blueprint: `/b`

  wird beim Rollout auf die Live Copy-Seite `/b` verschoben.

   * `bp-level-1` wird beim Rollout zur Live Copy verschoben.

#### Nach dem Rollout {#after-rollout}

|  | Blueprint nach dem Rollout | Live Copy nach dem Rollout | Live Copy nach dem Rollout | Nach dem Rollout veröffentlichen |
|---|---|---|---|---|
| Wert | `b` | `b` | `b_msm_moved` | `b` |
| Kommentar |  | Enthält den Inhalt der Blueprint-Seite `b`, die beim Rollout verschoben wurde | Enthält den Inhalt der Seite `b`, die in der Live Copy-Verzweigung manuell erstellt wurde | Keine Änderung, enthält den Inhalt der Originalseite `b`, die manuell im Live Copy-Zweig erstellt wurde und jetzt `b_msm_moved` heißt |
| Wert | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  |  | Keine Änderung | Keine Änderung |

### Angepasste Handler {#customized-handlers}

Mit benutzerdefinierten Konflikt-Handlern können Sie Ihre eigenen Regeln implementieren. Mit dem Mechanismus des Service-Rankings können Sie auch festlegen, wie sie mit anderen Handlern interagieren.

Benutzerdefinierte Konflikt-Handler können:

* gemäß Ihren Anforderungen benannt werden;
* gemäß Ihren Anforderungen entwickelt/konfiguriert werden.
   * Sie können beispielsweise einen Handler entwickeln, der der Live Copy-Seite Vorrang einräumt.
* Er kann mithilfe der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) konfiguriert werden. Insbesondere:
   * Das **Service-Ranking** legt die Reihenfolge in Bezug auf die anderen Konflikt-Handler fest (`service.ranking`).
      * Der Standardwert ist `0`.

### Verhalten, wenn die Konflikt-Behandlung deaktiviert ist {#behavior-when-conflict-handling-deactivated}

Wenn Sie die [Konfliktbehandlung manuell deaktivieren](#rollout-manager-and-conflict-handling), führt AEM keine Maßnahmen für konfliktbehaftete Seiten durch. Für Seiten, die keine Konflikte aufweisen, wird der Rollout erwartungsgemäß durchgeführt.

>[!CAUTION]
>
>Bei Deaktivierung der Konfliktbehandlung gibt AEM keine Hinweise darauf, dass Konflikte ignoriert werden. Da dieses Verhalten in solchen Fällen explizit konfiguriert werden muss, wird davon ausgegangen, dass dies das gewünschte Verhalten ist.

In diesem Fall hat die Live Copy effektiv Vorrang. Die Blueprint-Seite `/b` wird nicht kopiert und die Live Copy-Seite `/b` bleibt unberührt.

* Blueprint: `/b`

  Wird überhaupt nicht kopiert, sondern ignoriert.

* Live Copy: `/b`

  Bleibt gleich.

#### Nach dem Rollout {#after-rollout-no-conflict}

|  | Blueprint nach dem Rollout | Live Copy nach dem Rollout | Nach dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar |  | Keine Änderung, enthält den Inhalt der Seite `b`, die im Live Copy-Zweig manuell erstellt wurde | Keine Änderung, enthält den Inhalt der Seite `b`, die im Live Copy-Zweig manuell erstellt wurde |
| Wert | `/bp-level-1,` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Keine Änderung | Keine Änderung |

### Service-Rangfolge {#service-rankings}

Die [OSGi](https://www.osgi.org/)-Service-Rangfolge kann zum Definieren der Priorität von einzelnen Konflikt-Handlern verwendet werden.
