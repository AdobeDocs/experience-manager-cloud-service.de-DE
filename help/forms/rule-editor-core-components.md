---
title: Wie kann der Regeleditor verwendet werden, um Regeln zu Formularfeldern hinzuzufügen, um dynamisches Verhalten hinzuzufügen und eine komplexe Logik basierend auf Kernkomponenten zu einem adaptiven Formular zu erstellen?
description: Der Regeleditor für adaptive Formulare ermöglicht es Ihnen, ohne Programmierung oder Skripterstellung dynamisches Verhalten und komplexe Logik in Ihre Formulare zu integrieren.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 1292f729-c6eb-4e1b-b84c-c66c89dc53ae
source-git-commit: 8585ec309b04e04b9a8dcaa43063369d1c9d5d24
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 66%

---


# Einführung in den Regeleditor für adaptive Formulare basierend auf Kernkomponenten

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service (Kernkomponenten) | Dieser Artikel |
| AEM as a Cloud Service (Foundation-Komponenten) | [Hier klicken](/help/forms/rule-editor.md) |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=de) |

In einem auf Kernkomponenten basierenden adaptiven Formular ermöglicht die Regeleditorfunktion sowohl Geschäftsbenutzern als auch Entwicklern das Schreiben von Regeln für adaptive Formularobjekte. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Mit dieser Funktion wird das Ausfüllen des Formulars weiter optimiert, sodass Genauigkeit und Geschwindigkeit gewährleistet sind.

Der Regeleditor bietet eine intuitive und vereinfachte Benutzeroberfläche zum Erstellen von Regeln. Es bietet einen visuellen Editor, der für alle Benutzer gedacht ist und es ihnen ermöglicht, Regeln zu erstellen und zu verwalten, ohne umfangreiche technische Kenntnisse zu benötigen. Dieser visuelle Ansatz erleichtert es Benutzenden, die gewünschte Logik in ihren Formularen zu verstehen und zu implementieren.

Zu den wichtigsten Aktionen, die Sie mithilfe von Regeln in adaptiven Formularobjekten ausführen können, gehören die folgenden:

* Ein Objekt ein- oder ausblenden
* Ein Objekt aktivieren oder deaktivieren
* Einen Wert für ein Objekt festlegen
* Den Wert eines Objekts validieren
* Funktionen zur Berechnung des Werts eines Objekts ausführen
* Einen Formulardatenmodelldienst aufrufen und einen Vorgang durchführen
* Eine Eigenschaft eines Objekts festlegen

<!-- Rule editor replaces the scripting capabilities in [!DNL Experience Manager 6.1 Forms] and earlier releases. However, your existing scripts are preserved in the new rule editor. For more information about working with existing scripts in the rule editor, see [Impact of rule editor on existing scripts](rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p). -->

Benutzer, die der `forms-power-users` hinzugefügt wurden, können Skripte erstellen und vorhandene bearbeiten. Benutzer in der Gruppe [!DNL forms-users] können die Skripte verwenden, aber keine Skripte erstellen oder bearbeiten.

Siehe den [Unterschied zwischen dem Foundation-Regel-Editor und dem Kernkomponenten-Regel-Editor](/help/forms/rule-editor-core-components-difference-tables.md) für einen detaillierten Vergleich.

<!--
## Difference between Rule editor in Core Components and Rule Editor in Foundation Components

{{rule-editor-diff}}

>[!NOTE]
>
> To see how to create and use custom functions in detail, refer to [Custom functions in Adaptive Forms (Core Components)](/help/forms/create-and-use-custom-functions.md) article.

-->

## Grundlegendes zu Regeln {#understanding-a-rule}

Eine Regel ist eine Kombination aus Aktionen und Bedingungen. Im Regeleditor umfassen Aktionen Aktivitäten wie das Ausblenden, Anzeigen, Aktivieren, Deaktivieren oder Berechnen des Werts eines Objekts in einem Formular. Bedingungen sind boolesche Ausdrücke, die durch Prüfungen und Vorgänge für den Status, den Wert oder die Eigenschaft eines Formularobjekts ausgewertet werden. Aktionen werden basierend auf dem bei der Auswertung einer Bedingung zurückgegebenen Wert (`True` oder `False`) ausgeführt.

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, z. B. „Wenn“, „Anzeigen“, „Ausblenden“, „Aktivieren“, „Deaktivieren“, „Wert einstellen von“ und „Validieren“, um Ihnen beim Schreiben von Regeln zu helfen. Mit jedem Regeltyp können Sie Bedingungen und Aktionen in einer Regel definieren. In diesem Dokument sind die einzelnen Regeltypen im Detail beschrieben.

Eine Regel folgt normalerweise einem der folgenden Konstrukte:

**Bedingung-Aktion** In diesem Konstrukt definiert die Regel zuerst eine Bedingung und dann die auszulösende Aktion. Das Konstrukt ist vergleichbar mit der if-then-Anweisung in Programmiersprachen.

Im Regeleditor wird das Bedingung-Aktion-Konstrukt durch den Regeltyp **Wenn** durchgesetzt.

**Aktion-Bedingung** In diesem Konstrukt definiert die Regel zuerst eine auszulösende Aktion und dann die auszuwertenden Bedingungen. Eine weitere Variante dieses Konstrukts ist Aktion-Bedingung-alternative Aktion, wobei auch dann eine alternative Aktion angegeben wird, die ausgelöst wird, wenn die Bedingung den Wert „False“ zurückgibt.

Die Regeltypen „Anzeigen“, „Ausblenden“, „Aktivieren“, „Deaktivieren“, „Wert festlegen“ und „Validieren“ im Regeleditor erzwingen das Aktion-Bedingung-Regelkonstrukt. Die alternative Aktion für „Anzeigen“ ist standardmäßig „Ausblenden“ und für „Aktivieren“ „Deaktivieren“ und umgekehrt. Sie können die standardmäßige alternative Aktion nicht ändern.

>[!NOTE]
>
>Die verfügbaren Regeltypen, einschließlich der Bedingungen und Aktionen, die Sie im Regeleditor definieren, hängen auch vom Typ des Formularobjekts ab, für das Sie eine Regel erstellen. Der Regeleditor zeigt nur gültige Regeltypen und Optionen zum Schreiben von Bedingungs- und Aktionsanweisungen für einen bestimmten Formularobjekttyp an. Beispielsweise sehen Sie für ein Bedienfeldobjekt nicht die Typen „Validieren“ und „Wert festlegen“.

Weitere Informationen über die im Regeleditor verfügbaren Regeltypen finden Sie unter [Verfügbare Regeltypen im Regeleditor](rule-editor.md#p-available-rule-types-in-rule-editor-p).

### Richtlinien für die Auswahl eines Regelkonstrukts {#guidelines-for-choosing-a-rule-construct}

Für die meisten Anwendungsfälle können Sie ein beliebiges Regelkonstrukt verwenden. Nachfolgend finden Sie jedoch einige Richtlinien für die Wahl des am besten geeigneten Konstrukts für Ihre Zwecke. Weitere Informationen über die verfügbaren Regeln im Regeleditor finden Sie unter [Verfügbare Regeltypen im Regeleditor](rule-editor.md#p-available-rule-types-in-rule-editor-p).

* Eine typische Faustregel bei der Erstellung einer Regel ist, sie im Kontext des Objekts zu betrachten, für das Sie eine Regel schreiben. Angenommen, Feld B soll in Abhängigkeit von einem Wert, den eine Benutzerin oder ein Benutzer in Feld A eingibt, angezeigt oder ausgeblendet werden. In diesem Fall wird eine Bedingung für Feld A ausgewertet und basierend auf dem zurückgegebenen Wert eine Aktion für Feld B ausgelöst.

  Verwenden Sie daher beim Schreiben einer Regel für Feld B (das Objekt, für das eine Bedingung ausgewertet wird) das Konstrukt „Bedingung-Aktion“ oder den Regeltyp „Wenn“. Für Feld A müssten Sie dementsprechend das Konstrukt „Aktion-Bedingung“ oder den Regeltyp „Anzeigen“ oder „Ausblenden“ verwenden.

* In manchen Fällen müssen Sie für eine Bedingung mehrere Aktionen ausführen. In solchen Fällen empfiehlt es sich, das Konstrukt „Bedingung-Aktion“ zu verwenden. In diesem Konstrukt können Sie eine Bedingung einmal auswerten und mehrere Aktionsanweisungen angeben.

  Um beispielsweise die Felder B, C und D basierend auf einer Bedingung auszublenden, durch die der von einer Benutzerin oder einem Benutzer in Feld A angegebenen Wert geprüft wird, genügt eine Regel mit dem Konstrukt „Bedingung-Aktion“ oder dem Regeltyp „Wenn“ für Feld A, wobei Aktionen für die Sichtbarkeit der Felder B, C und D angegeben werden. Andernfalls benötigen Sie drei separate Regeln für die Felder B, C und D, wobei jede Regel die Bedingung prüft und das jeweilige Feld angezeigt oder ausgeblendet wird. In diesem Beispiel ist es effizienter, den Wenn-Regeltyp für ein Objekt zu schreiben, anstatt den Regeltyp Anzeigen oder Ausblenden für drei Objekte.

* Um eine Aktion auf der Grundlage mehrerer Bedingungen Trigger, wird empfohlen, ein Aktion-Bedingung-Konstrukt zu verwenden. Um beispielsweise Feld A ein- und auszublenden, indem Sie die Bedingungen für die Felder B, C und D auswerten, verwenden Sie den Regeltyp Anzeigen oder Ausblenden für Feld A.
* Für Regeln, die genau eine Aktion für eine Bedingung enthalten, können Sie sowohl das Konstrukt „Bedingung-Aktion“ als auch das Konstrukt „Aktion-Bedingung“ verwenden.
* Wenn eine Regel auf eine Bedingung prüft und sofort eine Aktion ausführt, wenn ein Wert in einem Feld bereitgestellt oder ein Feld verlassen wird, wird empfohlen, eine Regel mit einem Bedingung-Aktion-Konstrukt oder dem Wenn-Regeltyp für das Feld zu schreiben, für das die Bedingung ausgewertet wird.
* Die Bedingung in der Wenn-Regel wird ausgewertet, wenn ein Benutzer den Wert des Objekts ändert, auf das die Wenn-Regel angewendet wird. Soll die Aktion jedoch ausgelöst werden, wenn der Wert Server-seitig geändert wird (z. B. wenn der Wert vorab ausgefüllt wird), empfehlen wir, eine Wenn-Regel zu erstellen, die die Aktion beim Initialisieren des Felds auslöst.
* Beim Schreiben von Regeln für Dropdown-Elemente, Optionsfelder oder Kontrollkästchenobjekte werden die Optionen oder Werte dieser Formularobjekte im Formular im Regeleditor vorbefüllt.

Informationen zur Verwendung der Benutzeroberfläche zum Schreiben und Verwalten von Regeln in einem Regeleditor finden Sie im Artikel [Benutzeroberfläche des Regeleditors für adaptive Forms auf der Grundlage von Kernkomponenten](/help/forms/rule-editor-core-components-user-interface.md) .

## Siehe auch

{{see-also-rule-editor}}