---
title: Hinzufügen einer speziellen Testumgebung
description: Erfahren Sie, wie spezialisierte Testumgebungen in Cloud Manager einen dedizierten Raum für die Validierung von Funktionen unter produktionsnahen Bedingungen bieten, der sich ideal für Belastungstests und erweiterte Prüfungen vor der Bereitstellung eignet.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Private Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
exl-id: 815fb5c3-a171-4531-8727-b79183d85f06
source-git-commit: 498a58c89910f41e6b86c5429629ec9282028987
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 36%

---

# Hinzufügen einer speziellen Testumgebung{#add-special-test-enviro}

>[!NOTE]
>
>>Die in diesem Artikel beschriebene Funktion ist nur über das private Beta-Programm verfügbar. Informationen zur Anmeldung bei Private Beta finden Sie unter [Spezialisierte Testumgebung](/help/implementing/cloud-manager/release-notes/current.md#specialized-test-environment).

Die spezialisierte Testumgebung (oder DevXL) ist eine neue Art von Cloud Manager-Umgebung, die Sie erstellen können. Es wurde entwickelt, um erweiterte Anwendungsfälle wie Benutzerakzeptanztests (UAT) und Leistungsvalidierung zu unterstützen. Im Gegensatz zu herkömmlichen Entwicklungs-, Rapid Development- oder Staging-Umgebungen werden DevXL-Umgebungen außerhalb der Produktionsbereitstellungs-Pipeline ausgeführt. Auf diese Weise bieten sie Ihnen mehr Flexibilität bei gleichzeitiger strikter Isolation, um Störungen in Produktions-Workflows zu vermeiden.

DevXL wurde entwickelt, um die Größe, Skalierbarkeit und Konfigurationen einer typischen Staging-Umgebung widerzuspiegeln. Dieser Ansatz stellt sicher, dass in DevXL durchgeführte Tests realistische Einblicke in die Leistung von Code und Inhalten in produktionsähnlichen Bedingungen liefern können. Die -Umgebung unterstützt auch das direkte Kopieren von Inhalten aus der Produktion oder Staging. Sie bleibt hinsichtlich Bereitstellungs-Workflows, Zugriffssteuerungen und Netzwerkkonfigurationen mit Entwicklungsumgebungen gleichberechtigt.

## Wichtige Funktionen und Konfigurationen {#key-features}

| Kategorie | DevXL-Verhalten |
| --- | --- |
| Zweck | UAT und Leistungstests. |
| Pipeline-Typ | Nicht in der Produktions-Pipeline. |
| Umgebungsgröße | Entspricht der Staging-Umgebung. |
| Absonderung | Vollständig isoliert von anderen Umgebungen. |
| Code-Pipelines | Wie die Entwicklungsumgebung (Validierung, Erstellung, Bereitstellung). |
| Inhalt kopieren | Zulässig für Produktions-, Staging- oder spezielle Testumgebungen. |
| Inhaltswiederherstellung | Wie die Entwicklungsumgebung. |
| Zugriffsprotokolle | Wie die Entwicklungsumgebung. |
| Developer Console | Wie die Entwicklungsumgebung. |
| `IP Allow List` | Wie die Entwicklungsumgebung. |
| Vernetzung | Identisch mit der Entwicklungsumgebung (Services, Domain-Name, SSL-Zertifikate, erweitertes Netzwerk). |

Siehe auch [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md)

## Hinzufügen einer speziellen Testumgebung {#add-specialized-testing-environment}

Um eine Umgebung hinzufügen oder bearbeiten zu können, muss eine Benutzerin bzw. ein Benutzer Mitglied der Rolle **Geschäftsinhaber** sein.

**So fügen Sie eine spezielle Testumgebung hinzu:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf das Programm, für das eine Umgebung hinzugefügt werden soll.

1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie in der **[Meine](/help/implementing/cloud-manager/navigation.md#my-programs)**-Konsole auf der Karte **Umgebungen** auf **Umgebung hinzufügen**.
Wenn die Option **Umgebung hinzufügen** abgeblendet (deaktiviert) ist, kann dies auf fehlende Berechtigungen oder eine Abhängigkeit von den lizenzierten Ressourcen zurückzuführen sein.

   ![Karte „Umgebungen“](assets/no-environments.png)

   * Klicken Sie links im seitlichen Bedienfeld auf ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Umgebungen** und dann oben rechts auf der Seite „Umgebungen“ auf **Umgebung hinzufügen**.

     ![Registerkarte „Umgebungen“](assets/environments-tab.png)

1. Gehen Sie im Dialogfeld **Umgebung hinzufügen** wie folgt vor:

   * Klicken Sie **Spezialisierte Testumgebung**.
   * Geben Sie einen **Namen** für die Umgebung an. Der Umgebungsname kann nach der Erstellung der Umgebung nicht mehr geändert werden.
   * (Optional) Geben Sie eine **Beschreibung** für die Umgebung an.
   * Wählen Sie eine **Primäre** aus der Dropdown-Liste aus. Nach der Erstellung ist die primäre Region der DevXL-Umgebung (z. B. *USA (Westen der USA)* gesperrt und kann nicht geändert werden.

   ![Dialogfeld „Umgebung hinzufügen“ mit aktiviertem Optionsfeld „Spezialisierte Testumgebung“](assets/specialized-test-environment.png)

1. Klicken Sie auf **Speichern**.

   Die Seite **Überblick** zeigt nun auf der Karte **Umgebungen** Ihre neue Umgebung an. Sie können jetzt Pipelines für Ihre neue Umgebung einrichten.
