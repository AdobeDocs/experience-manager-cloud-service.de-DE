---
title: Umgebungsvariablen in Cloud Manager
description: Standard-Umgebungsvariablen können über Cloud Manager konfiguriert und verwaltet werden und zur Verwendung in OSGi-Konfigurationen für die Laufzeitumgebung bereitgestellt werden.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 32%

---


# Umgebungsvariablen in Cloud Manager {#environment-variables}

Standardumgebungsvariablen können über Cloud Manager konfiguriert und verwaltet werden. Sie werden der Laufzeitumgebung bereitgestellt und können in OSGi-Konfigurationen verwendet werden.

Umgebungsvariablen können umgebungsspezifische Werte oder Umgebungsgeheimnisse sein. Dies ist davon abhängig, was geändert wird.

## Über Umgebungsvariablen {#overview}

Umgebungsvariablen bieten eine Vielzahl von Vorteilen für Benutzer von AEM as a Cloud Service, z. B.:

* Sie ermöglichen es, das Verhalten Ihres Codes und Ihres Programms je nach Kontext und Umgebung zu variieren. Beispielsweise können sie verwendet werden, um in der Entwicklungsumgebung andere Konfigurationen als in der Produktions- oder Staging-Umgebung zu ermöglichen, um kostspielige Fehler zu vermeiden.
* Sie müssen nur einmal konfiguriert und eingerichtet werden und können bei Bedarf aktualisiert und gelöscht werden.
* Ihre Werte können jederzeit aktualisiert werden und werden sofort wirksam, ohne dass Code-Änderungen oder -Bereitstellungen erforderlich sind.
* Sie können Code von der Konfiguration trennen und die Notwendigkeit beseitigen, vertrauliche Informationen in die Versionskontrolle einzubeziehen.
* Sie verbessern die Sicherheit des AEM as a Cloud Service-Programms, da sie sich außerhalb des Codes befinden.

Typische Anwendungsfälle für die Verwendung von Umgebungsvariablen sind:

* Verbinden des AEM-Programms mit verschiedenen externen Endpunkten
* Verwenden einer Referenz beim Speichern von Kennwörtern (also nicht direkt die Code-Basis)
* Vorhandensein mehrerer Entwicklungsumgebungen in einem Programm, wobei sich einige Konfigurationen von einer Umgebung zur nächsten unterscheiden

## Umgebungsvariable hinzufügen {#add-variables}

Wenn Sie mehrere Variablen hinzufügen möchten, empfiehlt Adobe, die erste Variable hinzuzufügen. Verwenden Sie dann ![Symbol hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **Hinzufügen** im Dialogfeld **Umgebungskonfiguration** , um die zusätzlichen Variablen hinzuzufügen. Auf diese Weise können Sie sie mit einem Update zur Umgebung hinzufügen.

Um Umgebungsvariablen hinzuzufügen, zu aktualisieren oder zu löschen, müssen Sie Mitglied der Rolle [**Bereitstellungsmanager** sein](/help/onboarding/cloud-manager-introduction.md#role-based-premissions).

**Hinzufügen einer Umgebungsvariablen:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus, das Sie verwalten möchten.
1. Klicken Sie im Seitenmenü auf **Umgebungen**.
1. Wählen Sie auf der Seite **Umgebungen** eine Zeile in der Tabelle aus, die über die Umgebung verfügt, für die Sie eine Umgebungsvariable hinzufügen möchten.
1. Klicken Sie auf der Detailseite der Umgebung auf die Registerkarte **Konfiguration** .
1. Klicken Sie auf ![Hinzufügen/Aktualisieren - Kreissymbol hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Hinzufügen/Aktualisieren**.
Wenn Sie zum ersten Mal eine Umgebungsvariable hinzufügen, klicken Sie in der Mitte der Seite auf **Konfiguration hinzufügen** .

   ![Registerkarte „Konfiguration“](assets/configuration-tab.png)

1. Geben Sie im Dialogfeld **Umgebungskonfiguration** die Details in die erste Zeile der Tabelle ein.

   | Feld | Beschreibung |
   | --- | --- |
   | Name | Ein eindeutiger Name der Konfigurationsvariablen. Er identifiziert die spezifische Variable, die in der Umgebung verwendet wird. Sie muss den folgenden Benennungskonventionen entsprechen:<ul><li>Variablen dürfen nur alphanumerische Zeichen und den Unterstrich (`_`) enthalten.</li><li>Pro Umgebung sind maximal 200 Variablen zulässig.</li><li>Jeder Name darf maximal 100 Zeichen lang sein.</li></ul> |
   | Wert | Der Wert, den die Variable enthält. |
   | ANGEWENDETER SCHRITT | Wählen Sie den Dienst aus, für den die Variable gilt. Wählen Sie **Alle** aus, damit die Variable auf alle Dienste angewendet wird.<ul><li>**Alle**</li><li>**Autor**</li><li>**Veröffentlichen**</li><li>**Vorschau**</li></ul> |
   | Typ | Wählen Sie aus, ob die Variable normal oder geheim ist. |

   ![Variable hinzufügen](assets/add-variable.png)

1. Klicken Sie auf das Symbol ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)**Hinzufügen**.

   Fügen Sie nach Bedarf weitere Variablen hinzu.

1. Klicken Sie auf **Speichern**.

   In der rechten oberen Ecke der Tabelle wird ein Netz mit dem Status **Aktualisieren** angezeigt. Links von neu hinzugefügten Variablen wird auch ein Netz angezeigt. Diese Status zeigen an, dass die Umgebung mit der Konfiguration aktualisiert wird. Nach Abschluss ist die neue Umgebungsvariable in der Tabelle sichtbar.

![Variablen aktualisieren](assets/updating-variables.png)

## Umgebungsvariable aktualisieren {#update-variables}

Nachdem Sie Umgebungsvariablen erstellt haben, können Sie sie mit ![Hinzufügen/Aktualisieren - Kreissymbol hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Hinzufügen/Aktualisieren** aktualisieren, um das Dialogfeld **Umgebungskonfiguration** zu öffnen.

Wenn Sie mehrere Variablen aktualisieren möchten, empfiehlt Adobe, dass Sie das Dialogfeld **Umgebungskonfiguration** verwenden, um alle erforderlichen Variablen gleichzeitig zu aktualisieren, bevor Sie auf **Speichern** klicken. Auf diese Weise können Sie sie mit einer Aktualisierung zur Umgebung hinzufügen.

**Aktualisieren einer Umgebungsvariablen:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus, das Sie verwalten möchten.
1. Klicken Sie im Seitenmenü auf **Umgebungen**.
1. Wählen Sie auf der Seite **Umgebungen** eine Zeile in der Tabelle aus, die über die Umgebung verfügt, für die Sie eine Variable aktualisieren möchten.
1. Klicken Sie auf der Detailseite der Umgebung auf die Registerkarte **Konfiguration** .
1. Klicken Sie auf ![Hinzufügen/Aktualisieren - Kreissymbol hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Hinzufügen/Aktualisieren**.
1. Klicken Sie im Dialogfeld **Umgebungskonfiguration** in der letzten Spalte der Zeile der Variable, die Sie ändern möchten, auf das Symbol ![Ellipse - Weitere Zeichen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) .
1. Klicken Sie im Dropdown-Menü auf **Bearbeiten**.

   ![Variable bearbeiten oder löschen](assets/edit-delete-variable.png)

1. Aktualisieren Sie den Wert der Umgebungsvariablen nach Bedarf.
Beim Bearbeiten eines Geheimnisses kann der Wert nur aktualisiert, nicht angezeigt werden.

   ![Variable bearbeiten](assets/edit-variable.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf ![Anwenden - Häkchensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg) , um die Änderung anzuwenden.
   * Klicken Sie auf das Symbol ![Rückgängig](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg) , um die Änderung rückgängig zu machen.

1. Klicken Sie auf **Speichern**.

   In der rechten oberen Ecke der Tabelle wird ein Netz mit dem Status **Aktualisieren** angezeigt. Links von aktualisierten Variablen wird auch ein Netz angezeigt. Diese Status zeigen an, dass die Umgebung mit der Konfiguration aktualisiert wird. Nach Abschluss des Vorgangs ist die aktualisierte Umgebungsvariable in der Tabelle sichtbar.

## Umgebungsvariable löschen {#delete-env-variable}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus, das Sie verwalten möchten.
1. Klicken Sie im Seitenmenü auf **Umgebungen**.
1. Wählen Sie auf der Seite **Umgebungen** eine Zeile in der Tabelle aus, die über die Umgebung verfügt, für die Sie eine Variable aktualisieren möchten.
1. Klicken Sie auf der Detailseite der Umgebung auf die Registerkarte **Konfiguration** .
1. Klicken Sie auf ![Hinzufügen/Aktualisieren - Kreissymbol hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Hinzufügen/Aktualisieren**.
1. Klicken Sie im Dialogfeld **Umgebungskonfiguration** in der letzten Spalte der Zeile der Variable, die Sie ändern möchten, auf das Symbol ![Ellipse - Weitere Zeichen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) .
1. Klicken Sie im Dropdown-Menü auf **Löschen** , um die Variable sofort zu entfernen.
1. Klicken Sie auf **Speichern**.

## Verwendung von Umgebungsvariablen {#using}

Umgebungsvariablen können Ihre `pom.xml`-Konfigurationen sicherer und flexibler machen. So müssen beispielsweise Passwörter nicht fest kodiert werden, und Ihre Konfiguration kann auf der Grundlage der Werte in Umgebungsvariablen angepasst werden.

Sie können wie folgt über XML auf Umgebungsvariablen und Geheimnisse zugreifen:

`${env.VARIABLE_NAME}`

Unter [Einrichten des Projekts](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repository-support-password-protected-maven-repositories) finden Sie ein Beispiel dafür, wie beide Variablentypen in einer `pom.xml` -Datei verwendet werden.

Weitere Informationen finden Sie in der [offiziellen Maven-Dokumentation](https://maven.apache.org/settings.html#quick-overview) .

## Verfügbarkeit von Umgebungsvariablen {#availability}

Umgebungsvariablen können an verschiedenen Stellen wie folgt verwendet werden:

| Wo Umgebungsvariablen verwendet werden können | Beschreibung |
| --- | --- |
| Authoring, Vorschau und Veröffentlichung | In der Authoring-, Vorschau- und Veröffentlichungsumgebung können sowohl reguläre Umgebungsvariablen als auch Geheimnisse verwendet werden. |
| Dispatcher | Nur normale Umgebungsvariablen können mit [der Dispatcher](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher) verwendet werden.<ul><li>Geheimnisse können nicht verwendet werden.</li><li>Umgebungsvariablen können nicht in `IfDefine` -Direktiven verwendet werden.</li><li>Validieren Sie die Verwendung von Umgebungsvariablen [lokal im Dispatcher](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools), bevor Sie sie bereitstellen.</li></ul> |
| OSGi-Konfigurationen | Sowohl normale Umgebungsvariablen als auch Geheimnisse können in [OSGi-Konfigurationen](/help/implementing/deploying/configuring-osgi.md) verwendet werden. |
| Pipeline-Variablen | Neben Umgebungsvariablen gibt es auch Pipeline-Variablen, die während der Build-Phase verfügbar gemacht werden. Erfahren Sie mehr über Pipeline-Variablen in der [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#pipeline-variables). |

