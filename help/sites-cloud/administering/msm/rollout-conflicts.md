---
title: Rollout-Konflikte
description: Erfahren Sie, wie Sie Multi-Site-Manager-Rollout-Konflikte verwalten und lösen.
translation-type: tm+mt
source-git-commit: 4fc4dbe2386d571fa39fd6d10e432bb2fc060da1
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 29%

---


# Rollout-Konflikte {#msm-rollout-conflicts}

Konflikte können auftreten, wenn sowohl in der Blueprint-Verzweigung als auch in einer abhängigen Live Copy-Verzweigung neue Seiten mit demselben Seitennamen erstellt werden. Solche Konflikte müssen nach dem Rollout gehandhabt und aufgelöst werden.

## Konfliktbehandlung {#conflict-handling}

Wenn konkurrierende Seiten vorhanden sind (in den Zweigen &quot;blueprint&quot;und &quot;Live Copy&quot;), können Sie mit MSM definieren, wie (oder auch wenn) sie behandelt werden sollen.

Um sicherzustellen, dass der Rollout nicht gesperrt ist, können mögliche Definitionen Folgendes umfassen:

* Welche Seite (Vorlage oder Live Copy) hat bei der Aktualisierung Priorität?
* Welche Seiten werden umbenannt (und wie)?
* Auswirkungen auf veröffentlichte Inhalte

Standardmäßig werden veröffentlichte Inhalte AEM sofort einsetzbaren Verhalten nicht beeinträchtigt. Wenn also eine Seite, die manuell in der Live Copy-Verzweigung erstellt wurde, veröffentlicht wurde, wird dieser Inhalt auch nach der Bearbeitung und Einführung von Konflikten veröffentlicht.

Neben den Standardfunktionen können benutzerdefinierte Konflikt-Handler hinzugefügt werden, um unterschiedliche Regeln zu implementieren. Diese können auch das Veröffentlichen von Aktionen als Einzelprozess gestatten.

### Beispiel-Szenario {#example-scenario}

In den folgenden Abschnitten verwenden wir das Beispiel einer neuen Seite `b`, die sowohl im Entwurf als auch in der Live Copy-Verzweigung (manuell erstellt) erstellt wurde, um die verschiedenen Methoden der Konfliktlösung zu veranschaulichen:

* Blueprint: `/b`

   Eine Übergeordnet mit 1 untergeordneter Seite, `bp-level-1`

* Live Copy: `/b`

   Eine Seite, die manuell in der Live Copy-Verzweigung mit einer untergeordneten Seite erstellt wurde, `lc-level-1`

   * Aktiviert beim Veröffentlichen als `/b` zusammen mit der untergeordneten Seite

#### Vor der Rollout {#before-rollout}

|  | Blueprint vor Rollout | Live Copy Before Rollout | Vor dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar | In der Blueprint-Verzweigung erstellt, für die Einführung bereit | Manuell in der Live Copy-Verzweigung erstellt | Enthält den Inhalt der Seite `b`, die in der Live Copy-Verzweigung manuell erstellt wurde |
| Wert | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Manuell in der Live Copy-Verzweigung erstellt | enthält den Inhalt der Seite `child-level-1`, die manuell in der Live Copy-Verzweigung erstellt wurde |

## Rollout-Manager und Konfliktbehandlung {#rollout-manager-and-conflict-handling}

Mit dem Rollout-Manager können Sie das Konfliktmanagement aktivieren oder deaktivieren.

Dies erfolgt mithilfe der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) von **Day CQ WCM Rollout Manager**. Setzen Sie den Wert **Konflikte mit manuell erstellten Seiten** ( `rolloutmgr.conflicthandling.enabled`) auf &quot;true&quot;, wenn der Rollout-Manager Konflikte von einer Seite behandeln soll, die in der Live Copy mit einem Namen erstellt wurde, der im Blueprint vorhanden ist.

AEM verfügt über ein [vordefiniertes Verhalten, wenn das Konfliktmanagement deaktiviert wurde.](#behavior-when-conflict-handling-deactivated)

## Konflikt-Handler {#conflict-handlers}

AEM verwendet Konflikthandler, um Seitenkonflikte zu lösen, die beim Ausrollen von Inhalten aus einem Entwurf in eine Live Copy auftreten. Das Umbenennen von Seiten ist die übliche (nicht nur) Methode, um solche Konflikte zu lösen. Mehrere Konflikt-Handler können aktiv sein, um eine Reihe verschiedener Verhaltensweisen zu ermöglichen.

AEM stellt Folgendes bereit:

* Den [Standard-Konflikt-Handler](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* Die Möglichkeit, einen [benutzerdefinierten Handler](#customized-handlers) zu implementieren
* Den Service-Ranking-Mechanismus, mit dem Sie die Priorität jedes einzelnen Handlers festlegen können
   * Der Service mit dem höchsten Ranking wird verwendet.

### Standard-Konflikt-Handler {#default-conflict-handler}

Der standardmäßige Konflikthandler ist `ResourceNameRolloutConflictHandler`

* Mit diesem Handler hat die Blueprint-Seite Vorrang.
* Die Dienstrang für diesen Handler ist niedrig eingestellt, d. h. unter dem Standardwert für die `service.ranking`-Eigenschaft, da die Annahme lautet, dass benutzerdefinierte Handler eine höhere Rangfolge benötigen. Allerdings ist das Ranking nicht das absolute Minimum, um bei Bedarf Flexibilität zu gewährleisten.

Dieser Konflikt-Handler gibt dem Blueprint Vorrang. Die Live Copy-Seite `/b` wird beispielsweise innerhalb der Live Copy-Verzweigung nach `/b_msm_moved` verschoben.

* Live Copy: `/b`

   Wird innerhalb der Live Copy nach `/b_msm_moved` verschoben. Dies dient als Sicherung und stellt sicher, dass keine Inhalte verloren gehen.

   * `lc-level-1` nicht verschoben.

* Blueprint: `/b`

   Wird auf die Live Copy-Seite `/b` Rollout ausgeführt.

   * `bp-level-1` wird für die Live Copy ausgeführt.

#### Nach der Rollout {#after-rollout}

|  | Blueprint nach Rollout | Live Copy After Rollout | Live Copy After Rollout | Nach dem Rollout veröffentlichen |
|---|---|---|---|---|
| Wert | `b` | `b` | `b_msm_moved` | `b` |
| Kommentar |  | Hat den Inhalt der Blueprint-Seite `b`, auf der das Rolout erfolgt ist | Hat den Inhalt der Seite `b`, die manuell in der Live Copy-Verzweigung erstellt wurde | Keine Änderung, enthält den Inhalt der Originalseite `b`, die manuell in der Live Copy-Verzweigung erstellt wurde und jetzt `b_msm_moved` heißt |
| Wert | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  |  | Keine Änderung | Keine Änderung |

### Angepasste Handler {#customized-handlers}

Mit angepassten Konflikt-Handlern können Sie Ihre eigenen Regeln implementieren. Mit dem Service-Ranking-Mechanismus können Sie zudem festlegen, wie sie mit anderen Handlern interagieren.

Benutzerdefinierte Konflikt-Handler können:

* gemäß Ihren Anforderungen benannt werden;
* Entwickeln/konfigurieren Sie sich entsprechend Ihren Anforderungen.
   * Sie können beispielsweise einen Handler entwickeln, der der Seite &quot;Live Copy&quot;Vorrang einräumt.
* Kann für die Konfiguration mit der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) entwickelt werden. Insbesondere
   * **Dienst-** Rangfolge definiert die Reihenfolge, die mit anderen Konflikthandlern verbunden ist (  `service.ranking`).
      * Der Standardwert ist `0`.

### Verhalten bei Deaktivierung der Konfliktbehandlung {#behavior-when-conflict-handling-deactivated}

Wenn Sie die Konfliktleitung manuell deaktivieren, wird auf Seiten, die in Konflikt stehen, keine Aktion von [AEM ausgeführt. ](#rollout-manager-and-conflict-handling) Seiten, die keine Konflikte aufweisen, werden erwartungsgemäß Rollout durchgeführt.

>[!CAUTION]
>
>Bei Deaktivierung der Konfliktbehandlung gibt AEM keine Hinweise darauf, dass Konflikte ignoriert werden. Da dieses Verhalten in solchen Fällen explizit konfiguriert werden muss, wird davon ausgegangen, dass es das gewünschte Verhalten ist.

In diesem Fall hat die Live Copy effektiv Vorrang. Die Blueprint-Seite `/b` wird nicht kopiert und die Live Copy-Seite `/b` bleibt unberührt.

* Blueprint: `/b`

   Wird überhaupt nicht kopiert, wird aber ignoriert.

* Live Copy: `/b`

   Steht gleich.

#### Nach der Rollout {#after-rollout-no-conflict}

|  | Blueprint nach Rollout | Live Copy After Rollout | Nach dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar |  | Keine Änderung, hat den Inhalt der Seite `b`, die manuell in der Live Copy-Verzweigung erstellt wurde | Keine Änderung, enthält den Inhalt der Seite `b`, die manuell in der Live Copy-Verzweigung erstellt wurde |
| Wert | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Keine Änderung | Keine Änderung |

### Service-Rankings {#service-rankings}

Das [OSGi](https://www.osgi.org/)-Service-Ranking kann zum Definieren der Priorität von einzelnen Konflikt-Handlern verwendet werden.
