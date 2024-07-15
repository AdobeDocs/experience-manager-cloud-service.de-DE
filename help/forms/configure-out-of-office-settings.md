---
title: Konfigurieren von Abwesenheitseinstellungen in AEM Forms
description: Delegieren Sie Aufgaben während Ihrer Abwesenheit oder wenn Sie nicht im Büro sind, um eine nahtlose Workflow-Ausführung zu ermöglichen.
exl-id: c7e436f1-8e1c-4334-b3dc-ab9800695301
feature: Adaptive Forms, Workflow
role: Admin, User
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 100%

---


# Konfigurieren von Abwesenheitseinstellungen {#configure-out-of-office-settings}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/configure-out-of-office-settings.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Für geplante Abwesenheitszeiten können Sie festlegen, was während dieser Zeit mit den Ihnen zugeordneten Elementen passieren soll.

Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Wenn Sie sich in einer anderen Zeitzone als der des Servers aufhalten, wird die Zeitzone des Client verwendet.

Sie können eine Person festlegen, an die Ihre Elemente standardmäßig gesendet werden. Zudem können Sie Ausnahmen für Elemente aus speziellen Prozessen festlegen, die an einen anderen Benutzer gesendet oder bis zu Ihrer Rückkehr in Ihrem Posteingang bleiben sollen. Wenn die angegebene Person ebenfalls abwesend ist, wird das Element an den von dieser Person angegebenen Vertreter weitergeleitet. Sind alle Benutzer abwesend, denen das Element zugewiesen werden könnte, bleibt es im Posteingang.

Sie können die Elementzuweisung auf der Basis der Workflow-Modelle differenzieren. Sie können beispielsweise ein Element aus Workflow A an Benutzer A und ein Element aus Workflow B an Benutzer B übertragen.


>[!NOTE]
>
>* Wenn Sie die Abwesenheitseinstellung aktivieren, bleiben alle Elemente, die bis zu diesem Zeitpunkt in Ihrem Posteingang verfügbar sind, weiterhin im Posteingang. Nur Elemente, die nach Aktivierung der Abwesenheitseinstellungen empfangen wurden, werden delegiert.
>* Wenn Sie die Abwesenheitseinstellung deaktivieren, werden die delegierten Elemente nicht automatisch an Sie zurückverwiesen. Mithilfe der Anforderungsfunktion können Sie Elemente an sich selbst übertragen.
>* Wenn Benutzer A Elemente an Benutzer B delegiert und Benutzer B an Benutzer C weiterdelegiert, werden die Elemente nur Benutzer C und nicht Benutzer B zugewiesen.
>* Wenn eine Schleife im Arbeitsauftrag entsteht, bleiben die Aufgaben bei der ursprünglichen Person. Eine solche Schleife besteht beispielsweise, wenn ein Element von Person A an Person B, von Person B an Person C, von Person C an Person D und schließlich von Person D an Person B delegiert wird. In einem solchen Fall verbleibt das Element bei der ursprünglichen Person. Beim obigen Beispiel ist A die ursprüngliche Person.

## Aktivieren der Abwesenheitseinstellung für Ihr Konto {#enable-out-of-office}

Führen Sie folgende Schritte aus, um die Abwesenheitseinstellung für Ihr Konto zu aktivieren und Ihre Posteingangselemente an einen anderen Benutzer zu delegieren:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Wählen Sie das Symbol ![Posteingang](assets/bell.svg) und dann **[!UICONTROL Alle anzeigen]** aus. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie den ![Ansichtselektor](assets/viewlist.svg) oder das Symbol ![Ansichtselektor](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann **[!UICONTROL Einstellungen]** aus. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Öffnen Sie im Dialogfeld „Einstellungen“ die Registerkarte **[!UICONTROL Abwesenheit]**.
1. Wählen Sie die Schaltfläche **[!UICONTROL Aktivieren/Deaktivieren]** aus, um die Abwesenheitseinstellung zu aktivieren.
1. Geben Sie die Zeiten für **[!UICONTROL Startzeit]** und **[!UICONTROL Endzeit]** an. Die Elemente werden nur während des angegebenen Zeitraums delegiert. Lassen Sie das Feld **[!UICONTROL Ende]** leer, um Elemente auf unbestimmte Zeit zu übertragen.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Meine Aufgaben während dieser Zeit weiterleiten]**. Wenn Sie die Option nicht auswählen und keine Bevollmächtigten angeben, werden Ihre Elemente nicht an andere Benutzende weitergeleitet. Obwohl Sie abwesend sind und die Einstellung aktiviert ist, bleiben alle Elemente in Ihrem Posteingang.
1. Wählen Sie **[!UICONTROL Bevollmächtigten hinzufügen]** aus. Geben Sie im Feld **[!UICONTROL Bevollmächtigter]** einen Benutzer an, an den die Elemente delegiert werden sollen. Bestimmen Sie das **[!UICONTROL Workflow-Modell]**, um Elemente an den ausgewählten Benutzer zu delegieren. Sie können mehrere Workflow-Modelle auswählen.

   Wenn Sie einem bestimmten Benutzer alle Elemente unabhängig vom Workflow-Modell zuweisen möchten, wählen Sie in der Dropdown-Liste des Workflow-Modells die Option **[!UICONTROL Alle Workflows]**. <br>

   Um einer bestimmten Person Elemente für alle Workflow-Modelle mit Ausnahme einiger weniger zuzuweisen, wählen Sie **[!UICONTROL Alle Workflows]** in der Dropdown-Liste „Workflow-Modell“ aus, wählen Sie dann **[!UICONTROL + Ausnahmen hinzufügen]** und geben Sie die Workflow-Modelle an, die ausgeschlossen werden sollen.
   <br>

   Wiederholen Sie den Schritt, um weitere Empfänger hinzuzufügen. <br>

   >[!NOTE]
   >
   >Die Reihenfolge der Empfänger ist wichtig. Wenn einem Benutzer, der die Abwesenheitseinstellung aktiviert hat, ein Element zugewiesen wird, wird das Element entsprechend der erstellten Empfängerliste weitergeleitet. Dabei gilt die Reihenfolge, in der die Empfänger hinzugefügt wurden. Erfüllt ein Element die Kriterien, wird es an die jeweilige Person weitergeleitet, ohne dass weitere Beauftragte auf der Liste geprüft werden.


1. Wählen Sie **[!UICONTROL Speichern]** aus. Die Einstellung wird zum angegebenen Startzeitpunkt wirksam. Selbst wenn Sie sich während Ihrer Abwesenheit am System anmelden, gelten Sie erst wieder als anwesend, wenn Sie die Einstellungen ändern.

Nun werden alle während des Abwesenheitszeitraums empfangenen Elemente automatisch dem ausgewählten Empfänger zugewiesen.
![Abwesenheit](assets/out-of-office.png)

>[!NOTE]
>
>(Nur bei Formular-zentrierten Workflow-Elementen) Aktivieren Sie die Option **[!UICONTROL Zulassen, dass der Beauftragte mithilfe von Abwesenheits-Einstellungen delegiert]** des Schritts **[!UICONTROL Aufgabe zuweisen]**. Nur Elemente, bei denen diese Option aktiviert ist, werden an andere Benutzende delegiert.
>(Nur bei Formular-zentrierten Workflow-Elementen) Aktivieren Sie die Option **[!UICONTROL Zulassen, dass der Beauftragte mithilfe von Abwesenheits-Einstellungen delegiert]** des Schritts **[!UICONTROL Aufgabe zuweisen]**. Nur Elemente, bei denen die zuvor genannte Option aktiviert ist, werden an andere Benutzende delegiert.

## Einschränkungen {#limitations}

* Die Zuweisung von Elementen an eine Gruppe wird nicht unterstützt.
* Die Aktivierung von Abwesenheitszeiten für Projektaufgaben wird derzeit nicht unterstützt.
