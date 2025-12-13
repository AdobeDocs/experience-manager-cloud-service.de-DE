---
title: Welche Benutzergruppen sind in AEM Forms as a Cloud Service vorkonfiguriert verfügbar?
description: Liste der vorkonfigurierten Benutzergruppen und der jeder Gruppe zugewiesenen Berechtigungen
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: bd66ce92-14d9-47fe-b5d3-022e3e468d25
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 81%

---

# Gruppen und Berechtigungen {#aem-forms-on-osgi-groups-and-privileges}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können [Gruppen erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=de#accessing) und ihnen dann Richtlinien und [Benutzer](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=de#accessing) zuweisen. Diese Richtlinien steuern die Berechtigungen der Benutzer, die zu der jeweiligen Gruppe gehören.

Nachdem Sie [!DNL AEM Forms] as a Cloud Service eingerichtet haben, stehen die in der folgenden Tabelle aufgelisteten Gruppen (wie [!DNL forms-users] und forms-power-user) automatisch für die Zuweisung zur Verfügung:

<table>
 <tbody>
  <tr>
   <td>Gruppe</td> 
   <td>Berechtigungen</td> 
  </tr>
  <tr>
   <td>[!DNL forms-users] <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Erstellen, Vorschau, Veröffentlichen und Senden adaptiver Formulare</li> 
    <!-- <li>Create, preview, and publish interactive communications and document fragments</li> -->
     <li>Hochladen von Assets in eine AEM-Instanz</li> 
     <li>Erstellen von Designs</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>[!DNL forms-power-user]</td> 
   <td>
    <ul> 
     <li>Create, preview, publish, and submit Adaptive Forms</li> 
     <li>Create, preview, and publish interactive communications and document fragments</li> 
     <li>Create scripts for Adaptive Forms using code editor</li> 
     <li>Upload assets including scripts</li> 
     <li>Create themes</li> 
     <li>Import packages containing XDP</li> 
    </ul> </td> 
  </tr>
 <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Review submissions</li> 
     <li>Approve or reject submissions</li> 
    </ul> </td> 
  </tr> -->
  <tr>
   <td>[!DNL template-authors] <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Erstellen und Vorschau von Vorlagen für adaptive Formulare <!-- or interactive communications --></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>[!DNL fdm-authors]</p> </td> 
   <td>
    <ul> 
     <li>Erstellen und Ändern eines Formulardatenmodells</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>cm-agent-users</td> 
   <td>
    <ul> 
     <li>Access Correspondence Management letters or interactive communications using Agent UI</li> 
    </ul> </td> 
  </tr> --> 
  <!-- <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> -->
    <!-- <li>Create an inbox application</li>  -->
    <!-- <li>Create a workflow model</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL workflow-users]</td> 
   <td>
    <ul> 
     <li>Use AEM inbox applications<br /> -->
     <!-- 
     <strong>Note: </strong>You must have cm-agent-users and [!DNL workflow-users] group assignments to access Interactive Communications Agent UI in AEM inbox.</li>  -->
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL fd-administrators]</td> 
   <td>
    <ul> 
     <!-- <li>Configure PDF Generator</li> --> 
     <!-- <li>Configure Watched folder</li> -->
     <li>Verwalten von Workflow-Programmen</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Anwendbarkeit und Anwendungsfälle

### Versicherung

## Ist AEM Forms Enterprise-Grade für Versicherungsgeschäfte geeignet?

Ja. AEM Forms bietet Unternehmensfunktionen wie rollenbasierte Zugriffskontrolle, Audit-Protokolle, Workflow-Orchestrierung, Dokumenterstellung und Bereitstellungsflexibilität, die für groß angelegte Versicherungsvorgänge erforderlich sind.

## Siehe auch

* [Einstieg in eine Cloud Service-Umgebung](/help/forms/setup-forms-cloud-service.md)
* [Einrichten einer lokalen Entwicklungsumgebung](/help/forms/setup-local-development-environment.md)
* [Migrieren von AEM 6.5 Forms zu Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [Erstellen eines eigenständigen adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
* [Hinzufügen eines adaptiven Formulars zu einer Sites-Seite](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

<!--

>[!MORELIKETHIS]
>
>* [Use AEM Forms workflow for business process automation](/help/forms/aem-forms-workflow.md)

-->
