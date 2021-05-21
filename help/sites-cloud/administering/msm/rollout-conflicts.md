---
title: Rollout-Konflikte
description: Erfahren Sie, wie Sie Rollout-Konflikte in Multi-Site-Manager verwalten und lösen.
feature: Multi-Site-Manager
role: Administrator
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 100%

---

# Rollout-Konflikte {#msm-rollout-conflicts}

Konflikte sind möglich, wenn neue Seiten mit demselben Seitennamen im Blueprint-Zweig und in einem abhängigen Live Copy-Zweig erstellt werden. Solche Konflikte müssen nach dem Rollout gehandhabt und aufgelöst werden.

## Konfliktbehandlung  {#conflict-handling}

Wenn Konfliktseiten (in den Blueprint- und Live Copy-Zweigen) vorhanden sind, gestattet Ihnen MSM die Definition, wie (oder sogar ob) dieser Konflikt behoben werden soll.

Um sicherzustellen, dass der Rollout nicht gesperrt ist, können mögliche Definitionen Folgendes umfassen:

* Welche Seite (Blueprint oder Live Copy) während des Rollouts Vorrang hat
* Welche Seiten umbenannt werden (und wie)
* Wie dies jeglichen veröffentlichten Inhalt beeinflusst

Das vorkonfigurierte Standardverhalten von AEM besteht darin, dass veröffentlichte Inhalte davon unbeeinflusst bleiben. Wenn also eine Seite, die im Live Copy-Zweig manuell erstellt wurde, veröffentlicht wurde, wird dieser Inhalt nach der Konfliktbehandlung und dem Rollout auch weiterhin veröffentlicht.

Neben den Standardfunktionen können benutzerdefinierte Konflikt-Handler hinzugefügt werden, um unterschiedliche Regeln zu implementieren. Diese können auch das Veröffentlichen von Aktionen als Einzelprozess gestatten.

### Beispiel-Szenario {#example-scenario}

In den folgenden Abschnitten werden wir zum Veranschaulichen der verschiedenen Verfahren zur Konfliktbewältigung das Beispiel einer neuen Seite `b` verwenden, die sowohl im Blueprint- als auch im Live Copy-Zweig (manuell) erstellt wurde:

* Blueprint: `/b`

   Hauptseite mit einer untergeordneten Seite, `bp-level-1`

* Live Copy: `/b`

   Eine im Live Copy-Zweig manuell erstellte Seite mit einer untergeordneten Seite, `lc-level-1`

   * Bei Veröffentlichung als `/b` aktiviert, zusammen mit der untergeordneten Seite

#### Vor dem Rollout {#before-rollout}

|  | Blueprint vor dem Rollout | Live Copy vor dem Rollout | Vor dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar | In der Blueprint-Verzweigung erstellt, bereit für den Rollout | Manuell in der Live Copy-Verzweigung erstellt | Enthält den Inhalt der Seite `b`, die in der Live Copy-Verzweigung manuell erstellt wurde |
| Wert | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Manuell in der Live Copy-Verzweigung erstellt | Enthält den Inhalt der Seite `child-level-1`, die in der Live Copy-Verzweigung manuell erstellt wurde |

## Rollout-Manager und Konfliktbehandlung {#rollout-manager-and-conflict-handling}

Mit dem Rollout-Manager können Sie das Konflikt-Management aktivieren oder deaktivieren.

Dies erfolgt mithilfe der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) von **Day CQ WCM Rollout Manager**. Legen Sie den Wert **Konflikt mit manuell erstellten Seiten beheben** (`rolloutmgr.conflicthandling.enabled`) auf „true“ fest, wenn der Rollout-Manager Konflikte von einer Seite bewältigen soll, die in der Live Copy mit einem in der Blueprint vorhandenen Namen erstellt wurde.

AEM verfügt über ein [vordefiniertes Verhalten, wenn das Konflikt-Management deaktiviert wurde](#behavior-when-conflict-handling-deactivated).

## Konflikt-Handler {#conflict-handlers}

AEM nutzt Konflikt-Handler zum Lösen von Seitenkonflikten, die beim Rollout von Inhalten von einer Blueprint zu einer Live Copy vorliegen. Das Umbenennen von Seiten ist die übliche (nicht die einzige) Methode, um solche Konflikte zu lösen. Mehrere Konflikt-Handler können aktiv sein, um eine Reihe verschiedener Verhaltensweisen zu ermöglichen.

AEM stellt Folgendes bereit:

* Den [Standard-Konflikt-Handler](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* Die Möglichkeit, einen [benutzerdefinierten Handler](#customized-handlers) zu implementieren
* Den Service-Ranking-Mechanismus, mit dem Sie die Priorität jedes einzelnen Handlers festlegen können
   * Der Service mit dem höchsten Ranking wird verwendet.

### Standard-Konflikt-Handler {#default-conflict-handler}

Der standardmäßige Konflikt-Handler ist `ResourceNameRolloutConflictHandler`.

* Mit diesem Handler hat die Blueprint-Seite Vorrang.
* Das Service-Ranking für diesen Handler wurde als niedrig festgelegt (d. h. unterhalb des Standardwerts für die Eigenschaft `service.ranking`), da davon ausgegangen wird, dass benutzerdefinierte Handler ein höheres Ranking benötigen. Allerdings ist das Ranking nicht das absolute Minimum, um bei Bedarf Flexibilität zu gewährleisten.

Dieser Konflikt-Handler gibt dem Blueprint Vorrang. Die Live Copy-Seite `/b` wird beispielsweise innerhalb des Live Copy-Zweiges nach `/b_msm_moved` verschoben.

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
| Kommentar |  | Enthält den Inhalt der Blueprint-Seite `b`, die beim Rollout verschoben wurde | Enthält den Inhalt der Seite `b`, die in der Live Copy-Verzweigung manuell erstellt wurde | Keine Änderung, enthält den Inhalt der Originalseite `b`, die manuell in der Live Copy-Verzweigung erstellt wurde und jetzt `b_msm_moved` heißt |
| Wert | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  |  | Keine Änderung | Keine Änderung |

### Angepasste Handler {#customized-handlers}

Mit angepassten Konflikt-Handlern können Sie Ihre eigenen Regeln implementieren. Mit dem Service-Ranking-Mechanismus können Sie zudem festlegen, wie sie mit anderen Handlern interagieren.

Benutzerdefinierte Konflikt-Handler können:

* gemäß Ihren Anforderungen benannt werden;
* gemäß Ihren Anforderungen entwickelt/konfiguriert werden.
   * Sie können beispielsweise einen Handler entwickeln, der der Live Copy-Seite Vorrang einräumt.
* so konzipiert sein, dass die Konfiguration unter Verwendung der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) erfolgt. Insbesondere gilt:
   * Das **Service-Ranking** legt die Reihenfolge in Bezug auf die anderen Konflikt-Handler fest (`service.ranking`).
      * Der Standardwert ist `0`.

### Verhalten, wenn die Konflikt-Behandlung deaktiviert ist {#behavior-when-conflict-handling-deactivated}

Wenn Sie die [Konfliktbehandlung manuell deaktivieren](#rollout-manager-and-conflict-handling), führt AEM keine Maßnahmen für konfliktbehaftete Seiten durch. Für Seiten, die keine Konflikte aufweisen, wird der Rollout erwartungsgemäß durchgeführt.

>[!CAUTION]
>
>Bei Deaktivierung der Konfliktbehandlung gibt AEM keine Hinweise darauf, dass Konflikte ignoriert werden. Da dieses Verhalten in solchen Fällen explizit konfiguriert werden muss, wird davon ausgegangen, dass dies das gewünschte Verhalten ist.

In diesem Fall hat die Live Copy effektiv Vorrang. Die Blueprint-Seite `/b` wird nicht kopiert und die Live Copy-Seite `/b` bleibt unberührt.

* Blueprint: `/b`

   wird überhaupt nicht kopiert, sondern ignoriert.

* Live Copy: `/b`

   Bleibt gleich.

#### Nach dem Rollout {#after-rollout-no-conflict}

|  | Blueprint nach dem Rollout | Live Copy nach dem Rollout | Nach dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar |  | Keine Änderung. Enthält den Inhalt der Seite `b`, die in der Live Copy-Verzweigung manuell erstellt wurde | Keine Änderung. Enthält den Inhalt der Seite `b`, die in der Live Copy-Verzweigung manuell erstellt wurde |
| Wert | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Keine Änderung | Keine Änderung |

### Service-Rankings {#service-rankings}

Das [OSGi](https://www.osgi.org/)-Service-Ranking kann zum Definieren der Priorität von einzelnen Konflikt-Handlern verwendet werden.
