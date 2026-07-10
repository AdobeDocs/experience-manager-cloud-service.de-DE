---
title: Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys
description: Erfahren Sie, wie Sie eine Edge Delivery-Site mit einem privaten oder unternehmensspezifischen Git-Repository verknüpfen können.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 1dbaef34-efa3-4287-b7b1-f60db938146d
source-git-commit: dea8a3df29876df1c97454a97602045eb50121ad
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 35%

---

# Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys

Um Code aus einem privaten Git-Repository abzurufen, das bereits in Cloud Manager integriert ist, können Sie Ihre Edge Delivery-Site konfigurieren.

<!--
**Supported Git Vendors**

| Support level | Vendors | Notes |
| --- | --- | --- |
| General availability | &bull; GitHub Enterprise (self-hosted version)<br>&bull; Bitbucket (Cloud version)<br>&bull; GitLab (Cloud and self-hosted version) | Connect without enablement requests |
| Alpha program | Azure DevOps (Cloud version) | [Request access](mailto:grp-cloudmanager_byog@adobe.com) |
| Beta program | Adobe-hosted repository (created in Cloud Manager) | [Request access](mailto:grp-cloudmanager_byog@adobe.com) |
-->

**Um ein externes Git-Repository zu verwenden, konfigurieren Sie eine Edge Delivery-Site:**

{{sign-in-to-cloud-manager}}

1. Wählen Sie in der **[Meine](/help/implementing/cloud-manager/navigation.md#my-programs)**&quot; das Programm aus, für das Edge Delivery Services konfiguriert ist. Wählen Sie das Programm aus, für das Sie eine Edge Delivery-Site zur Verwendung eines externen Git-Repositorys konfigurieren möchten.
1. Klicken Sie in der linken Leiste unter **Programm** auf **![Übersichtssymbol](/help/implementing/cloud-manager/edge-delivery/assets/overview.svg) Übersicht**.
1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**.
1. Klicken Sie in der Tabelle **Edge Delivery-Sites** auf das Symbol![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site Sie für die Verwendung eines externen Repositorys konfigurieren möchten. Klicken Sie dann auf **Bring Your Own Git**.
1. Wählen **Dialogfeld „Eigenes Git**&quot; in der Dropdown-Liste **Repository-Name** ein Git-Repository mit `READY` Status aus und klicken Sie dann auf **Bestätigen**.

   Cloud Manager gibt ein einmaliges Geheim-Token zurück. Wenn Sie die Site neu konfigurieren, generiert Cloud Manager ein neues Geheimnis-Token.

1. Kopieren Sie das Token und fügen Sie es zur Site-Konfiguration in **helix-admin** hinzu, wie im [BYO Git-Handbuch](https://www.aem.live/developer/byo-git) beschrieben.
1. Klicken Sie in Cloud Manager auf ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)Symbol am Ende einer Zeile, deren Site Sie für die Verwendung eines externen Repositorys konfiguriert haben, und klicken Sie dann auf **Code synchronisieren**.
1. Wählen Sie die zu synchronisierende Verzweigung aus und klicken Sie auf **Synchronisieren**.

Jeder Commit bei einer Verzweigung löst jetzt eine automatische Synchronisierung aus. Nutzen Sie **Code synchronisieren** erneut, wenn Sie eine vollständige manuelle Synchronisierung benötigen.

## Authentifizieren von Git-Klon-Anfragen {#authenticate-git-clone-requests}

Sie können Ihr [!DNL Bring Your Own Git]-Repository aus Cloud Manager entweder mithilfe eines IMS-Tokens oder des von Cloud Manager beim Konfigurieren der Site generierten Byogit-Geheimnisses klonen. Beide Anmeldeinformationen authentifizieren sich beim Klon-Endpunkt, sodass Sie die geheimen Daten verwenden können, die helix-admin bereits für die Synchronisierung [!DNL Edge Delivery Services] Codes speichert.

Der Klon-Endpunkt akzeptiert die Anmeldeinformationen in der `Authorization`-Kopfzeile. Cloud Manager validiert das Byogit-Geheimnis anhand des für dieses Repository gespeicherten Werts. Anfragen, die weder ein gültiges IMS-Token noch ein gültiges Byogit-Geheimnis enthalten, geben eine `401` Antwort zurück.

>[!NOTE]
>
>Bestehende Workflows für IMS-authentifizierte Klone sind davon nicht betroffen. Das Byogit-Geheimnis ist eine zusätzliche Option, kein Ersatz.

**So klonen Sie das Repository mit dem byogit-Geheimnis:**

1. Kopieren Sie die geheimen Daten, die Cloud Manager bei der Konfiguration der Site zurückgibt.
1. Führen Sie den Klonbefehl aus und übergeben Sie die geheimen Daten in die `Authorization`.

   `git -c http.extraHeader="Authorization: <byogit-secret>"` Klonen von `https://cm-repo.adobe.io/api/program/<program-id>/repository/<repository-id>.git`

   Ersetzen Sie `<byogit-secret>` durch die geheimen Daten aus Cloud Manager und ersetzen Sie `<program-id>` und `<repository-id>` durch die Werte aus Ihrem Programm.
