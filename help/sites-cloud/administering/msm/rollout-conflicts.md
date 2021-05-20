---
title: Rollout-Konflikte
description: Erfahren Sie, wie Sie Rollout-Konflikte mit Multi Site Manager verwalten und lösen.
feature: Multi-Site-Manager
role: Administrator
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 29%

---

# Rollout-Konflikte {#msm-rollout-conflicts}

Konflikte können auftreten, wenn neue Seiten mit demselben Seitennamen sowohl in der Blueprint-Verzweigung als auch in einer abhängigen Live Copy-Verzweigung erstellt werden. Solche Konflikte müssen nach dem Rollout gehandhabt und aufgelöst werden.

## Konfliktbehandlung {#conflict-handling}

Wenn in Konflikt stehende Seiten vorhanden sind (in den Blueprint- und Live Copy-Verzweigungen), können Sie mit MSM definieren, wie diese verarbeitet werden sollen (oder auch wenn dies der Fall ist).

Um sicherzustellen, dass der Rollout nicht gesperrt ist, können mögliche Definitionen Folgendes umfassen:

* Welche Seite (Blueprint oder Live Copy) hat während des Rollouts Priorität
* Welche Seiten werden umbenannt (und wie)
* Auswirkungen auf veröffentlichte Inhalte

Das Standardverhalten von AEM vordefinierten ist, dass veröffentlichte Inhalte nicht betroffen sind. Wenn also eine Seite veröffentlicht wurde, die manuell in der Live Copy-Verzweigung erstellt wurde, wird dieser Inhalt nach der Konfliktbehandlung und dem Rollout weiterhin veröffentlicht.

Neben den Standardfunktionen können benutzerdefinierte Konflikt-Handler hinzugefügt werden, um unterschiedliche Regeln zu implementieren. Diese können auch das Veröffentlichen von Aktionen als Einzelprozess gestatten.

### Beispiel-Szenario {#example-scenario}

In den folgenden Abschnitten verwenden wir das Beispiel einer neuen Seite `b`, die sowohl im Blueprint- als auch im Live Copy-Zweig (manuell erstellt) erstellt wurde, um die verschiedenen Methoden zur Konfliktbehebung zu veranschaulichen:

* Blueprint: `/b`

   Eine Übergeordnete Seite mit einer untergeordneten Seite, `bp-level-1`

* Live Copy: `/b`

   Eine Seite, die manuell in der Live Copy-Verzweigung mit einer untergeordneten Seite, `lc-level-1`, erstellt wurde

   * Wird bei der Veröffentlichung zusammen mit der untergeordneten Seite als `/b` aktiviert.

#### Vor dem Rollout {#before-rollout}

|  | Blueprint vor Rollout | Live Copy vor Rollout | Vor dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar | Erstellt in Blueprint-Verzweigung, bereit für Rollout | Manuell in der Live Copy-Verzweigung erstellt | Enthält den Inhalt der Seite `b` , die manuell in der Live Copy-Verzweigung erstellt wurde |
| Wert | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Manuell in der Live Copy-Verzweigung erstellt | enthält den Inhalt der Seite `child-level-1` , die manuell in der Live Copy-Verzweigung erstellt wurde |

## Rollout-Manager und Konfliktbehandlung {#rollout-manager-and-conflict-handling}

Mit dem Rollout-Manager können Sie das Konfliktmanagement aktivieren oder deaktivieren.

Dies erfolgt mithilfe der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) von **Day CQ WCM Rollout Manager**. Setzen Sie den Wert **Konflikt mit manuell erstellten Seiten verarbeiten** ( `rolloutmgr.conflicthandling.enabled`) auf &quot;true&quot;, wenn der Rollout-Manager Konflikte von einer in der Live Copy erstellten Seite mit einem im Blueprint vorhandenen Namen verarbeiten soll.

AEM verfügt über ein [vordefiniertes Verhalten, wenn das Konfliktmanagement deaktiviert wurde.](#behavior-when-conflict-handling-deactivated)

## Konflikt-Handler {#conflict-handlers}

AEM verwendet Konflikt-Handler, um Seitenkonflikte zu beheben, die beim Rollout von Inhalten von einem Blueprint zu einer Live Copy auftreten. Das Umbenennen von Seiten ist die übliche (nicht nur) Methode zur Lösung solcher Konflikte. Mehrere Konflikt-Handler können aktiv sein, um eine Reihe verschiedener Verhaltensweisen zu ermöglichen.

AEM stellt Folgendes bereit:

* Den [Standard-Konflikt-Handler](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* Die Möglichkeit, einen [benutzerdefinierten Handler](#customized-handlers) zu implementieren
* Den Service-Ranking-Mechanismus, mit dem Sie die Priorität jedes einzelnen Handlers festlegen können
   * Der Service mit dem höchsten Ranking wird verwendet.

### Standard-Konflikt-Handler {#default-conflict-handler}

Der standardmäßige Konflikt-Handler ist `ResourceNameRolloutConflictHandler` .

* Mit diesem Handler hat die Blueprint-Seite Vorrang.
* Der Service-Rang für diesen Handler ist niedrig eingestellt, d. h. unter dem Standardwert für die Eigenschaft `service.ranking`, da die Annahme ist, dass benutzerdefinierte Handler einen höheren Rang benötigen. Allerdings ist das Ranking nicht das absolute Minimum, um bei Bedarf Flexibilität zu gewährleisten.

Dieser Konflikt-Handler gibt dem Blueprint Vorrang. Die Live Copy-Seite `/b` wird beispielsweise innerhalb der Live Copy-Verzweigung nach `/b_msm_moved` verschoben.

* Live Copy: `/b`

   Wird innerhalb der Live Copy nach `/b_msm_moved` verschoben. Dies dient als Sicherung und stellt sicher, dass keine Inhalte verloren gehen.

   * `lc-level-1` wird nicht verschoben.

* Blueprint: `/b`

   Wird auf der Live Copy-Seite `/b` bereitgestellt.

   * `bp-level-1` wird für die Live Copy bereitgestellt.

#### Nach dem Rollout {#after-rollout}

|  | Blueprint nach Rollout | Live Copy nach Rollout | Live Copy nach Rollout | Nach dem Rollout veröffentlichen |
|---|---|---|---|---|
| Wert | `b` | `b` | `b_msm_moved` | `b` |
| Kommentar |  | Hat den Inhalt der Blueprint-Seite `b`, die bereitgestellt wurde | Hat den Inhalt der Seite `b` , die manuell in der Live Copy-Verzweigung erstellt wurde | Keine Änderung, enthält den Inhalt der ursprünglichen Seite `b` , die manuell in der Live Copy-Verzweigung erstellt wurde und jetzt `b_msm_moved` heißt |
| Wert | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  |  | Keine Änderung | Keine Änderung |

### Angepasste Handler {#customized-handlers}

Mit angepassten Konflikt-Handlern können Sie Ihre eigenen Regeln implementieren. Mit dem Service-Ranking-Mechanismus können Sie zudem festlegen, wie sie mit anderen Handlern interagieren.

Benutzerdefinierte Konflikt-Handler können:

* gemäß Ihren Anforderungen benannt werden;
* Sie müssen entsprechend Ihren Anforderungen entwickelt/konfiguriert werden.
   * Sie können beispielsweise einen Handler entwickeln, der der Live Copy-Seite Vorrang einräumt.
* Kann für die Konfiguration mit der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) entwickelt werden. Insbesondere gilt Folgendes:
   * **Die** Dienstbewertung definiert die Reihenfolge, die mit anderen Konflikt-Handlern verbunden ist (  `service.ranking`).
      * Der Standardwert ist `0`.

### Verhalten bei deaktivierter Konfliktbehandlung {#behavior-when-conflict-handling-deactivated}

Wenn Sie [die Konfliktbehandlung manuell deaktivieren, führt](#rollout-manager-and-conflict-handling) AEM keine Aktionen auf Konfliktseiten durch. Nicht miteinander in Konflikt stehende Seiten werden erwartungsgemäß eingeführt.

>[!CAUTION]
>
>Wenn die Konfliktbehandlung deaktiviert ist, gibt AEM keinen Hinweis darauf, dass Konflikte ignoriert werden. Da dieses Verhalten in solchen Fällen explizit konfiguriert werden muss, wird davon ausgegangen, dass es sich um das gewünschte Verhalten handelt.

In diesem Fall hat die Live Copy effektiv Vorrang. Die Blueprint-Seite `/b` wird nicht kopiert und die Live Copy-Seite `/b` bleibt unberührt.

* Blueprint: `/b`

   Wird überhaupt nicht kopiert, wird jedoch ignoriert.

* Live Copy: `/b`

   Bleibt gleich.

#### Nach dem Rollout {#after-rollout-no-conflict}

|  | Blueprint nach Rollout | Live Copy nach Rollout | Nach dem Rollout veröffentlichen |
|---|---|---|---|
| Wert | `b` | `b` | `b` |
| Kommentar |  | Keine Änderung, hat den Inhalt der Seite `b` , die manuell in der Live Copy-Verzweigung erstellt wurde | Keine Änderung, enthält den Inhalt der Seite `b` , die manuell in der Live Copy-Verzweigung erstellt wurde |
| Wert | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Kommentar |  | Keine Änderung | Keine Änderung |

### Service-Rankings {#service-rankings}

Das [OSGi](https://www.osgi.org/)-Service-Ranking kann zum Definieren der Priorität von einzelnen Konflikt-Handlern verwendet werden.
