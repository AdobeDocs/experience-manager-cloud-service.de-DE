---
title: 'Integrierte  [!DNL AEM Forms]  as a Cloud Service-Gruppen '
seo-title: [!DNL AEM Forms] as a Cloud Service User Groups
description: 'Liste der vordefinierten Benutzergruppen und der jeder Gruppe zugewiesenen Berechtigungen '
seo-description: List of out of the box user groups and permissions assigned to each group
exl-id: bd66ce92-14d9-47fe-b5d3-022e3e468d25
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: 139
ht-degree: 100%

---

# Gruppen und Berechtigungen {#aem-forms-on-osgi-groups-and-privileges}

Sie können [Gruppen erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=de#accessing) und ihnen dann Richtlinien und [Benutzer](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) zuweisen. Diese Richtlinien steuern die Berechtigungen der Benutzer, die zu der jeweiligen Gruppe gehören.

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
     <li>Assets in eine AEM-Instanz hochladen</li> 
     <li>Themen erstellen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL forms-power-user]</td> 
   <td>
    <ul> 
     <li>Erstellen, Vorschau, Veröffentlichen und Senden adaptiver Formulare</li> 
     <!-- <li>Create, preview, and publish interactive communications and document fragments</li> 
     <li>Create scripts for Adaptive Forms using code editor</li> -->
     <li>Laden Sie Assets einschließlich Skripte hoch</li> 
     <li>Themen erstellen</li> 
     <li>Importieren Sie Pakete, die XDP enthalten</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
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
     <li>Erstellen und Ändern des Formulardatenmodells</li> 
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
