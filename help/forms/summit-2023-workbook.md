---
title: Forms mit Kernkomponenten und Headless integrieren
seo-title: Build Engaging Forms Using Core Components and Headless
description: Forms mit Kernkomponenten und Headless integrieren
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: a4d46fd14805bf68a40ffdbee9d2e5fcfdee2f95
workflow-type: tm+mt
source-wordcount: '4625'
ht-degree: 0%

---


# Forms mit Kernkomponenten und Headless integrieren

## Lab-Übersicht

In diesem praktischen Labor lernen Sie:

Verwendung von AEM Forms zur einfachen Erstellung adaptiver Formulare mithilfe der neuesten Kernkomponenten, die mit AEM Sites konsistent sind, Erlebnisse für die Omnichannel-Datenerfassung ermöglichen, indem adaptive Formulare als Headless-Formulare an Web, Mobile und Chat übermittelt werden. Außerdem lernen Sie Best Practices rund um die Formatierung, Anpassungen und Front-End-Entwicklung kennen.

## Wichtige Schritte

* **Geschäftliche Agilität**: Als Business-Anwender kann ich mühelos Formularerlebnisse für mehrere Kanäle erstellen.

* **Unterstützung für Frontend-Entwickler**: Als Frontend-Entwickler kann ich das Benutzererlebnis mit Headless-Formularen steuern.

* **EntwicklerVelocity**: Als Entwickler kann ich mühelos und konsistent Sites- und Forms-Komponenten anpassen.

## Voraussetzungen


+ + + AEM Forms als Cloud Service-Sandbox


    &lt;table>
    &lt;thead>
    &lt;tr>&lt;th>name&lt;/th>&lt;th>username&lt;/th>&lt;th>Author instance URL&lt;/th>&lt;th>Publish Instance URL&lt;/th>&lt;/tr>
    &lt;/thead>
    &lt;tbody>
    &lt;tr>&lt;td>L716001&lt;/td>&lt;td>L716+001@summitlab.us&lt;/td>&lt;td>https://author-p105303-e986623.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p105303-e986623.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716002&lt;/td>&lt;td>L716+002@summitlab.us&lt;/td>&lt;td>https://author-p106405-e993047.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106405-e993047.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716003&lt;/td>&lt;td>L716+003@summitlab.us&lt;/td>&lt;td>https://author-p106406-e993049.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106406-e993049.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716004&lt;/td>&lt;td>L716+004@summitlab.us&lt;/td>&lt;td>https://author-p106398-e993114.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106398-e993114.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716005&lt;/td>&lt;td>L716+005@summitlab.us&lt;/td>&lt;td>https://author-p106407-e993048.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106407-e993048.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716006&lt;/td>&lt;td>L716+006@summitlab.us&lt;/td>&lt;td>https://author-p106408-e993155.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106408-e993155.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716007&lt;/td>&lt;td>L716+007@summitlab.us&lt;/td>&lt;td>https://author-p106343-e993067.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106343-e993067.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716008&lt;/td>&lt;td>L716+008@summitlab.us&lt;/td>&lt;td>https://author-p106399-e993108.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106399-e993108.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716009&lt;/td>&lt;td>L716+009@summitlab.us&lt;/td>&lt;td>https://author-p106344-e993064.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106344-e993064.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716010&lt;/td>&lt;td>L716+010@summitlab.us&lt;/td>&lt;td>https://author-p106409-e993051.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106409-e993051.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716011&lt;/td>&lt;td>L716+011@summitlab.us&lt;/td>&lt;td>https://author-p106345-e993060.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106345-e993060.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716012&lt;/td>&lt;td>L716+012@summitlab.us&lt;/td>&lt;td>https://author-p106346-e993061.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106346-e993061.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716013&lt;/td>&lt;td>L716+013@summitlab.us&lt;/td>&lt;td>https://author-p106410-e993153.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106410-e993153.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716014&lt;/td>&lt;td>L716+014@summitlab.us&lt;/td>&lt;td>https://author-p106502-e993073.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106502-e993073.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716015&lt;/td>&lt;td>L716+015@summitlab.us&lt;/td>&lt;td>https://author-p106401-e993112.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106401-e993112.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716016&lt;/td>&lt;td>L716+016@summitlab.us&lt;/td>&lt;td>https://author-p106452-e993115.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106452-e993115.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716017&lt;/td>&lt;td>L716+017@summitlab.us&lt;/td>&lt;td>https://author-p106453-e993113.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106453-e993113.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716018&lt;/td>&lt;td>L716+018@summitlab.us&lt;/td>&lt;td>https://author-p106411-e993050.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106411-e993050.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716019&lt;/td>&lt;td>L716+019@summitlab.us&lt;/td>&lt;td>https://author-p106454-e993116.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106454-e993116.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716020&lt;/td>&lt;td>L716+020@summitlab.us&lt;/td>&lt;td>https://author-p106347-e993063.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106347-e993063.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716021&lt;/td>&lt;td>L716+021@summitlab.us&lt;/td>&lt;td>https://author-p106455-e993109.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106455-e993109.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716022&lt;/td>&lt;td>L716+022@summitlab.us&lt;/td>&lt;td>https://author-p106456-e993110.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106456-e993110.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716023&lt;/td>&lt;td>L716+023@summitlab.us&lt;/td>&lt;td>https://author-p106466-e993291.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106466-e993291.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716024&lt;/td>&lt;td>L716+024@summitlab.us&lt;/td>&lt;td>https://author-p106413-e993156.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106413-e993156.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716025&lt;/td>&lt;td>L716+025@summitlab.us&lt;/td>&lt;td>https://author-p106348-e993066.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106348-e993066.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716026&lt;/td>&lt;td>L716+026@summitlab.us&lt;/td>&lt;td>https://author-p106414-e993154.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106414-e993154.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716027&lt;/td>&lt;td>L716+027@summitlab.us&lt;/td>&lt;td>https://author-p106349-e993065.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106349-e993065.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716028&lt;/td>&lt;td>L716+028@summitlab.us&lt;/td>&lt;td>https://author-p106415-e993152.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106415-e993152.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716029&lt;/td>&lt;td>L716+029@summitlab.us&lt;/td>&lt;td>https://author-p106350-e993068.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106350-e993068.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716030&lt;/td>&lt;td>L716+030@summitlab.us&lt;/td>&lt;td>https://author-p106351-e993062.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106351-e993062.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716031&lt;/td>&lt;td>L716+031@summitlab.us&lt;/td>&lt;td>https://author-p106417-e993158.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106417-e993158.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716032&lt;/td>&lt;td>L716+032@summitlab.us&lt;/td>&lt;td>https://author-p106418-e993159.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106418-e993159.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716033&lt;/td>&lt;td>L716+033@summitlab.us&lt;/td>&lt;td>https://author-p106503-e993080.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106503-e993080.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716034&lt;/td>&lt;td>L716+034@summitlab.us&lt;/td>&lt;td>https://author-p106457-e993125.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106457-e993125.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716035&lt;/td>&lt;td>L716+035@summitlab.us&lt;/td>&lt;td>https://author-p106504-e993081.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106504-e993081.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716036&lt;/td>&lt;td>L716+036@summitlab.us&lt;/td>&lt;td>https://author-p106458-e993120.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106458-e993120.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716037&lt;/td>&lt;td>L716+037@summitlab.us&lt;/td>&lt;td>https://author-p106419-e993160.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106419-e993160.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716038&lt;/td>&lt;td>L716+038@summitlab.us&lt;/td>&lt;td>https://author-p106420-e993162.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106420-e993162.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716039&lt;/td>&lt;td>L716+039@summitlab.us&lt;/td>&lt;td>https://author-p106517-e993235.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106517-e993235.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716040&lt;/td>&lt;td>L716+040@summitlab.us&lt;/td>&lt;td>https://author-p106506-e993079.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106506-e993079.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716041&lt;/td>&lt;td>L716+041@summitlab.us&lt;/td>&lt;td>https://author-p106507-e993074.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106507-e993074.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716042&lt;/td>&lt;td>L716+042@summitlab.us&lt;/td>&lt;td>https://author-p106508-e993075.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106508-e993075.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716043&lt;/td>&lt;td>L716+043@summitlab.us&lt;/td>&lt;td>https://author-p106421-e993163.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106421-e993163.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716044&lt;/td>&lt;td>L716+044@summitlab.us&lt;/td>&lt;td>https://author-p106459-e993121.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106459-e993121.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716045&lt;/td>&lt;td>L716+045@summitlab.us&lt;/td>&lt;td>https://author-p106467-e993292.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106467-e993292.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716046&lt;/td>&lt;td>L716+046@summitlab.us&lt;/td>&lt;td>https://author-p106518-e993234.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106518-e993234.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716047&lt;/td>&lt;td>L716+047@summitlab.us&lt;/td>&lt;td>https://author-p106511-e993076.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106511-e993076.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716048&lt;/td>&lt;td>L716+048@summitlab.us&lt;/td>&lt;td>https://author-p106512-e993077.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106512-e993077.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716049&lt;/td>&lt;td>L716+049@summitlab.us&lt;/td>&lt;td>https://author-p106460-e993124.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106460-e993124.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716050&lt;/td>&lt;td>L716+050@summitlab.us&lt;/td>&lt;td>https://author-p106519-e993237.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106519-e993237.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716051&lt;/td>&lt;td>L716+051@summitlab.us&lt;/td>&lt;td>https://author-p106513-e993084.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106513-e993084.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716052&lt;/td>&lt;td>L716+052@summitlab.us&lt;/td>&lt;td>https://author-p106461-e993122.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106461-e993122.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716053&lt;/td>&lt;td>L716+053@summitlab.us&lt;/td>&lt;td>https://author-p106514-e993082.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106514-e993082.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716054&lt;/td>&lt;td>L716+054@summitlab.us&lt;/td>&lt;td>https://author-p106462-e993123.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106462-e993123.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716055&lt;/td>&lt;td>L716+055@summitlab.us&lt;/td>&lt;td>https://author-p106463-e993127.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106463-e993127.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716056&lt;/td>&lt;td>L716+056@summitlab.us&lt;/td>&lt;td>https://author-p106515-e993083.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106515-e993083.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716057&lt;/td>&lt;td>L716+057@summitlab.us&lt;/td>&lt;td>https://author-p106464-e993126.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106464-e993126.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716058&lt;/td>&lt;td>L716+058@summitlab.us&lt;/td>&lt;td>https://author-p106520-e993236.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106520-e993236.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716059&lt;/td>&lt;td>L716+059@summitlab.us&lt;/td>&lt;td>https://author-p106423-e993161.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106423-e993161.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716060&lt;/td>&lt;td>L716+060@summitlab.us&lt;/td>&lt;td>https://author-p106516-e993078.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106516-e993078.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716061&lt;/td>&lt;td>L716+061@summitlab.us&lt;/td>&lt;td>https://author-p106521-e993240.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106521-e993240.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716062&lt;/td>&lt;td>L716+062@summitlab.us&lt;/td>&lt;td>https://author-p106424-e993308.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106424-e993308.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716063&lt;/td>&lt;td>L716+063@summitlab.us&lt;/td>&lt;td>https://author-p106468-e993295.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106468-e993295.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716064&lt;/td>&lt;td>L716+064@summitlab.us&lt;/td>&lt;td>https://author-p106425-e993309.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106425-e993309.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716065&lt;/td>&lt;td>L716+065@summitlab.us&lt;/td>&lt;td>https://author-p106426-e993314.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106426-e993314.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716066&lt;/td>&lt;td>L716+066@summitlab.us&lt;/td>&lt;td>https://author-p106469-e993293.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106469-e993293.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716067&lt;/td>&lt;td>L716+067@summitlab.us&lt;/td>&lt;td>https://author-p106522-e993238.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106522-e993238.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716068&lt;/td>&lt;td>L716+068@summitlab.us&lt;/td>&lt;td>https://author-p106470-e993299.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106470-e993299.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716069&lt;/td>&lt;td>L716+069@summitlab.us&lt;/td>&lt;td>https://author-p106427-e993311.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106427-e993311.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716070&lt;/td>&lt;td>L716+070@summitlab.us&lt;/td>&lt;td>https://author-p106428-e993310.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106428-e993310.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716071&lt;/td>&lt;td>L716+071@summitlab.us&lt;/td>&lt;td>https://author-p106471-e993298.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106471-e993298.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716072&lt;/td>&lt;td>L716+072@summitlab.us&lt;/td>&lt;td>https://author-p106429-e993315.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106429-e993315.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716073&lt;/td>&lt;td>L716+073@summitlab.us&lt;/td>&lt;td>https://author-p106523-e993239.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106523-e993239.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716074&lt;/td>&lt;td>L716+074@summitlab.us&lt;/td>&lt;td>https://author-p106472-e993300.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106472-e993300.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716075&lt;/td>&lt;td>L716+075@summitlab.us&lt;/td>&lt;td>https://author-p106430-e993312.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106430-e993312.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716076&lt;/td>&lt;td>L716+076@summitlab.us&lt;/td>&lt;td>https://author-p106524-e993241.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106524-e993241.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716077&lt;/td>&lt;td>L716+077@summitlab.us&lt;/td>&lt;td>https://author-p106431-e993313.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106431-e993313.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716078&lt;/td>&lt;td>L716+078@summitlab.us&lt;/td>&lt;td>https://author-p106473-e993294.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106473-e993294.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716079&lt;/td>&lt;td>L716+079@summitlab.us&lt;/td>&lt;td>https://author-p106474-e993297.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106474-e993297.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716080&lt;/td>&lt;td>L716+080@summitlab.us&lt;/td>&lt;td>https://author-p106475-e993296.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106475-e993296.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716081&lt;/td>&lt;td>L716+081@summitlab.us&lt;/td>&lt;td>https://author-p106476-e993353.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106476-e993353.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716082&lt;/td>&lt;td>L716+082@summitlab.us&lt;/td>&lt;td>https://author-p106525-e993247.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106525-e993247.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716083&lt;/td>&lt;td>L716+083@summitlab.us&lt;/td>&lt;td>https://author-p106526-e993244.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106526-e993244.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716084&lt;/td>&lt;td>L716+084@summitlab.us&lt;/td>&lt;td>https://author-p106527-e993243.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106527-e993243.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716085&lt;/td>&lt;td>L716+085@summitlab.us&lt;/td>&lt;td>https://author-p106477-e993356.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106477-e993356.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716086&lt;/td>&lt;td>L716+086@summitlab.us&lt;/td>&lt;td>https://author-p106478-e993355.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106478-e993355.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716087&lt;/td>&lt;td>L716+087@summitlab.us&lt;/td>&lt;td>https://author-p106528-e993245.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106528-e993245.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716088&lt;/td>&lt;td>L716+088@summitlab.us&lt;/td>&lt;td>https://author-p106432-e993316.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106432-e993316.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716089&lt;/td>&lt;td>L716+089@summitlab.us&lt;/td>&lt;td>https://author-p106529-e993242.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106529-e993242.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716090&lt;/td>&lt;td>L716+090@summitlab.us&lt;/td>&lt;td>https://author-p106436-e993320.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106436-e993320.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716091&lt;/td>&lt;td>L716+091@summitlab.us&lt;/td>&lt;td>https://author-p106480-e993301.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106480-e993301.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716092&lt;/td>&lt;td>L716+092@summitlab.us&lt;/td>&lt;td>https://author-p106530-e993246.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106530-e993246.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716093&lt;/td>&lt;td>L716+093@summitlab.us&lt;/td>&lt;td>https://author-p106481-e993352.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106481-e993352.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716094&lt;/td>&lt;td>L716+094@summitlab.us&lt;/td>&lt;td>https://author-p106482-e993354.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106482-e993354.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716095&lt;/td>&lt;td>L716+095@summitlab.us&lt;/td>&lt;td>https://author-p106531-e993248.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106531-e993248.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716096&lt;/td>&lt;td>L716+096@summitlab.us&lt;/td>&lt;td>https://author-p106483-e993357.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106483-e993357.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716097&lt;/td>&lt;td>L716+097@summitlab.us&lt;/td>&lt;td>https://author-p106433-e993318.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106433-e993318.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716098&lt;/td>&lt;td>L716+098@summitlab.us&lt;/td>&lt;td>https://author-p106532-e993249.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106532-e993249.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716099&lt;/td>&lt;td>L716+099@summitlab.us&lt;/td>&lt;td>https://author-p106434-e993317.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106434-e993317.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716100&lt;/td>&lt;td>L716+100@summitlab.us&lt;/td>&lt;td>https://author-p106435-e993319.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106435-e993319.adobeaemcloud.com&lt;/td>&lt;/tr>
    &lt;/tbody>
    &lt;/table>

+++

## Lektion 1

### Ziel

Machen Sie sich mit der as a Cloud Service AEM Forms-Umgebung vertraut.

### Lektionskontext

In dieser Lektion lernen Sie die as a Cloud Service AEM Forms-Umgebung kennen, indem Sie in der Benutzeroberfläche navigieren.

### Übung

1. Öffnen Sie den Browser und geben Sie die URL der Autorenumgebung des Cloud Service ein. Beispiel:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Melden Sie sich in der Autorenumgebung des Cloud Service gemäß den freigegebenen Anmeldedaten an. Beispiel: Benutzername: [L716+001@summitlab.us](mailto:L716%2B001@summitlab.us)
Kennwort: 
**Adobe123!**

1. Nachdem Sie angemeldet sind, navigieren Sie zur AEM Forms-Benutzeroberfläche. Klicken **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. Klicken **Forms und Dokumente**. Schließen Sie alle Popups, die sich auf Voreinstellungen oder Informationen beziehen.

   ![](/help/forms/assets/screenshot2028113929.png)

   Alle verfügbaren Formulare werden angezeigt.

   ![](/help/forms/assets/screenshot2028114029.png)

## Lektion 2

### Ziel

Erstellen Sie ein adaptives Formular mit den neuesten Kernkomponenten, konfigurieren und senden Sie es.

### Lektionskontext

In dieser Lektion erstellen Sie als Geschäftsbenutzer ein adaptives Formular für mehrere Kanäle wie Web, Mobile und Chat, indem Sie adaptive Formulare erstellen und standardisierte OOTB-Kernkomponenten für die Datenerfassung verwenden.

### Übung

1. Erstellen Sie einen Übermittlungsendpunkt für das Formular:

   1. Öffnen <https://requestbin.com/> in einer neuen Browser-Registerkarte.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. Klicken **Öffentlichen Ordner erstellen** und kopieren Sie die Endpunkt-URL.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. Erstellen Sie ein adaptives Formular über die Benutzeroberfläche des Assistenten:

   1. Navigieren Sie auf der in Lektion 1 verwendeten Browser-Registerkarte zur AEM Forms als Cloud Service-Webschnittstelle und navigieren Sie zu Forms und Dokumenten.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. Klicken **Erstellen** und wählen Sie Adaptives Formular aus.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. Wählen Sie die **Leer mit Kernkomponenten** Vorlage auf dem Vorlagenauswahlbildschirm wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Klicken Sie auf **Stil** und wählen Sie die **wknd-theme** Design wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Klicken Sie auf **Einsendung** und wählen Sie die **An REST-Endpunkt übermitteln** und geben Sie den öffentlichen Ordner im
      **URL für die POST-Anforderung** wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Klicken Sie auf **Erstellen**. Geben Sie einen Namen und einen Titel für Ihr Formular an. Beispiel: **contactus**. Klicken Sie auf **Erstellen**.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. Der Editor für adaptive Formulare wird geöffnet. Schließen Sie alle Popups oder Dialogfelder für Voreinstellungen oder Informationen. Klicken Sie in der linken Leiste auf den Komponenten-Browser und fügen Sie die **Fußzeile** -Komponente am unteren Rand des leeren Formulars.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. Die Kopfzeile ist Teil der adaptiven Formularvorlage. Dies ermöglicht eine einfache Möglichkeit, eine konsistente Kopf-/Fußzeile für alle adaptiven Formulare bereitzustellen. Alternativ können Sie auch festlegen, dass das Formular bearbeitbar bleibt, wie es im nächsten Schritt für die Fußzeilenkomponente angezeigt wird.

   1. Hinzufügen einer **Titel** -Komponente in die Mitte des Formulars.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. Hinzufügen einer **Texteingabe** -Komponente nach der Titelkomponente.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. Hinzufügen einer **Zahleneingabe** -Komponente.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. Hinzufügen einer **Senden-Schaltfläche** -Komponente in das Formular ein.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. Klicken Sie auf **Titel** -Komponente **Popup-Menü** angezeigt. Klicken Sie auf **Symbol Bearbeiten** im Menü, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Eingabe `Contact Us` als Titeltext.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. Klicken Sie auf **Texteingabe** -Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie auf **Symbol Bearbeiten** im Menü, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Eingabe **Vollständiger Name** als Feldbezeichnung.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. Klicken Sie auf **Zahleneingabe** -Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie auf **Symbol Bearbeiten** im Menü, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. Geben Sie die **Telefonnummer** als Feldbezeichnung.
      ![](/help/forms/assets/screenshot2028123829.png)


1. Fügen Sie Validierungen zum Formular hinzu:

   1. Klicken Sie auf **Telefonnummer** -Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie auf **Schraubensymbol** im Menü, um das Feld zu konfigurieren.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. Öffnen Sie die **Registerkarte &quot;Validierungen&quot;**, markieren Sie das Feld **Erforderlich** und klicken Sie auf **Fertig**. Die Erfolgsmeldung wird angezeigt.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. Klicken **Vorschau** , um eine Vorschau des Formulars aus der Perspektive des Endbenutzers anzuzeigen.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. Füllen Sie das Formular mit Platzhalterdaten aus
      ![](/help/forms/assets/screenshot2028125629.png)

   1. Formular senden
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Überprüfen Sie im Tab Anforderungs-bin die gesendeten Daten.
      ![](/help/forms/assets/screenshot2028125829.png)

Verwenden Sie nun für die verbleibende Übung ein vorab erstelltes Registrierungsformular.

1. Öffnen Sie beispielsweise die AEM Forms-Verwaltungsoberfläche. `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`und wählen Sie das Registrierungsformular aus.

   ![](/help/forms/assets/screenshot2028115529.png)

1. Klicken Sie auf **Veröffentlichen**.

   ![](/help/forms/assets/screenshot2028115629.png)

   Die Erfolgsmeldung wird angezeigt.

   ![](/help/forms/assets/screenshot2028115729.png)

   Die Veröffentlichungs-URL des Formulars ähnelt der `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. Ersetzen Sie zum Anzeigen des veröffentlichten Formulars die Programm-ID (pXXXXXX) und die Umgebungs-ID (eXXXXXX) in der obigen URL durch die IDs Ihrer Umgebung.

## Lektion 3

### Ziel

Aktualisieren Sie Stile mithilfe der Best Practices für die Frontend-Entwicklung.

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie die Formatierung für das zuvor erstellte adaptive Formular einfach aktualisieren können.

### Übung

Lokales Repository des Designs einrichten:

1. Öffnen Sie die Eingabeaufforderung oder Shell mit Administratorrechten:

   ![](/help/forms/assets/screenshot2028115829.png)

1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zu **c:\git** Ordner

   ```Shell
   cd c:\git
   ```

1. Verwenden Sie den folgenden Befehl, um den Frontend-Code des Designs zu klonen:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Verwenden Sie den folgenden Befehl in der angegebenen Reihenfolge, um zum **aem-forms-theme-canvas** und öffnen Sie Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. Auswählen **Den Autoren aller Dateien im übergeordneten Ordner vertrauen** und klicken Sie auf **Ja, ich vertraue den Autoren**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. Um das in Ihrer Cloud Service-Veröffentlichungsumgebung gehostete Formular wiederzugeben, benennen Sie die `env_template` -Datei.  Um die Datei umzubenennen, klicken Sie mit der rechten Maustaste auf das **env_template** und wählen Sie die **Umbenennen** -Option.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest und speichern Sie die Datei:

   * **AEM_URL**: Geben Sie Ihre Veröffentlichungsumgebung für den Cloud-Service an. Beispiel: `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: Geben Sie den Pfad des Formulars an. Wenn der Formularpfad beispielsweise `/content/forms/af/registration`, würde der Wert dieser Variablen `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. Führen Sie im Fenster Eingabeaufforderung den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Wenn Sie eine Meldung erhalten, in der Sie aufgefordert werden, npm über die `npm notice Run npm nstall -g npm@9.6.0`-Befehl, ignorieren Sie die Nachricht.
   > * Führen Sie keine anderen npm-Befehle aus, es sei denn, dies wird in der Arbeitsmappe angewiesen.


1. Führen Sie nun den folgenden Befehl aus, um eine Vorschau des Formulars anzuzeigen.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   Warten Sie nach Ausführung des oben genannten Befehls auf die `webpack compiled` Nachricht. Das Formular wird auf einer Browser-Registerkarte angezeigt.

   >[!NOTE]
   >
   >Wenn nach der Ausführung des `npm run live` Befehl für mehr als 3-4 Minuten, ändern Sie `localhost` in der Browser-URL auf 127.0.0.1 und Treffer **Eingabe**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Öffnen Sie in Visual Studio Code die `PROJECT\src\site\_variables.scss` -Datei. Beachten Sie die `$error` Farbe ist ein Farbton von RED.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Senden Sie im Browser das Formular, um die rote Farbe im **Vorname** -Feld.

   ![](/help/forms/assets/screenshot2028120829.png)

1. Legen Sie die **$error** Farbe auf **#5736eb** und speichern Sie die Datei.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Aktualisieren Sie den Browser und senden Sie das Formular. Die Fehlerfarbe für das Vorname-Feld wurde entsprechend geändert.

   ![](/help/forms/assets/screenshot2028121129.png)

1. Drücken Sie in der Eingabeaufforderung die **Strg+C**, eingeben **Y** und drücken Sie **Eingabe** zum Beenden des npm-Prozesses. Es ist wichtig, den npm-Server zu stoppen, damit er nicht mit dem nächsten Satz von Übungen in Konflikt gerät.
1. Schließen Sie die Fenster Visual Studio Code und Eingabeaufforderung .

## Lektion 4

### Ziel

Wiedergabe des Formulars auf Web/Mobile- und anderen Schnittstellen als Headless-Formular.

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie das zuvor erstellte adaptive Formular mithilfe des Framework für das React-Spektrum-Design als Headless-Formular rendern können.

### Übung

Lokales Repository mithilfe des React-Starter-Projekts einrichten:

1. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.

   ![](/help/forms/assets/screenshot2028115829.png)

1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zu **c:\git** Ordner

   ```Shell
   cd c:\git
   ```

1. Verwenden Sie den folgenden Befehl, um das React-Starter-Projekt des adaptiven Formulars zu klonen:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. Verwenden Sie die folgenden Befehle in der angegebenen Reihenfolge, um zum **react-starter-kit-aem-headless-forms** und öffnen Sie Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Das Fenster Visual Studio Code wird geöffnet.

   ![](/help/forms/assets/screenshot2028117429.png)

So rendern Sie das in Ihrer Cloud Service-Veröffentlichungsumgebung gehostete Formular:

1. Benennen Sie die Datei env_template in .env -Datei um. Klicken Sie zum Umbenennen mit der rechten Maustaste auf die **env_template** und wählen Sie die **Umbenennen** -Option.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest. Speichern Sie nach dem Aktualisieren der Variablen die Datei.

   * **AEM_URL**: Geben Sie die URL der Veröffentlichungsumgebung des Cloud-Service an. Beispiel: `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: Geben Sie den Pfad des adaptiven Formulars an, das in der vorherigen Lektion erstellt wurde. Beispiel: `/content/forms/af/registration/`

      ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Öffnen Sie das Befehlsfenster, stellen Sie sicher, dass Sie sich im Ordner &quot;react-starter-kit-aem-headless-forms&quot;befinden, und führen Sie den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. Führen Sie im Fenster Eingabeaufforderung den folgenden Befehl aus:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   Der obige Befehl startet einen lokalen Entwicklungsserver, der die von AEM abgerufene Formulardefinition mit der Frontend-Bibliothek &quot;React-Spektrum&quot;per Headless-Implementierung rendert.

   >[!NOTE]
   >
   > 
   > Wenn nach der Ausführung des `npm start` Befehl für mehr als 3-4 Minuten, ändern Sie `localhost` in der Browser-URL auf 127.0.0.1 und Treffer **Eingabe**.

   ![](/help/forms/assets/screenshot2028118229.png)

Überprüfen wir die Ausführung der Regeln in dieser Headless-Form:

1. Wählen Sie die **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten.** -Option. Die nachfolgende Option zum Anwenden einer Kreditkarte ist deaktiviert.

   ![](/help/forms/assets/screenshot2028126229.png)

1. Deaktivieren **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten.** um die Kreditkartenoption zu aktivieren.

   ![](/help/forms/assets/screenshot2028126329.png)

Nehmen wir als Geschäftsbenutzer Änderungen am Formular auf dem Server vor und zeigen Sie die Änderungen automatisch im Headless-Formular an.

1. Öffnen Sie die AEM Forms-Verwaltungsoberfläche im Browser. Beispiel: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Wählen Sie die **registrierung** Formular und klicken Sie auf **Bearbeiten.** Das Formular wird im Editor für adaptive Formulare geöffnet.

   ![](/help/forms/assets/screenshot2028118529.png)

1. Wählen Sie die **Telefonnummer** und klicken Sie auf **Symbol &quot;Bearbeiten&quot;(Bleistiftsymbol)** in der Symbolleiste. Wenn Sie die Popup-Symbolleiste nicht sehen können, wechseln Sie in den Bearbeitungsmodus, indem Sie auf **Bearbeiten** Schaltfläche oben rechts, von links nach **Vorschau** Schaltfläche.

   ![](/help/forms/assets/screenshot2028119629.png)

1. Ändern Sie den Titel in Mobiltelefonnummer. Klicken Sie auf eine leere Stelle im Formular und die am Formular vorgenommenen Änderungen werden gespeichert.

   ![](/help/forms/assets/screenshot2028119729.png)

Veröffentlichen wir das aktualisierte Formular, um die Änderungen in die Veröffentlichungsumgebung zu übertragen.

1. Wählen Sie im Tab Verwaltungsoberfläche von AEM Forms das Registrierungsformular aus und klicken Sie auf **Veröffentlichung rückgängig machen**. Wenn die Variable **Veröffentlichung rückgängig machen** auf, fahren Sie mit Schritt 3 fort, um die Änderungen direkt zu veröffentlichen.

   ![](/help/forms/assets/screenshot2028119829.png)

1. Klicken Sie auf **Veröffentlichung aufheben**. Klicken **Schließen** im entsprechenden Dialogfeld.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. Nachdem der Browser aktualisiert wurde, wählen Sie das Registrierungsformular aus und klicken Sie auf **Veröffentlichen**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. Klicken Sie auf **Veröffentlichen**. Klicken **Schließen** im entsprechenden Dialogfeld.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Aktualisieren Sie die Browser-Registerkarte mit dem Headless-Formular. Beachten Sie, dass die Bezeichnung für die Telefonnummer in Mobiltelefonnummer geändert wurde.

   ![](/help/forms/assets/screenshot2028120529.png)

1. Öffnen Sie das Fenster Eingabeaufforderung , das zum Starten des **react-starter-kit-aem-headless-forms** Projekt, drücken **Strg+C**, und geben Sie **Y** und drücken Sie die Eingabetaste, um den npm-Prozess zu beenden. Es ist wichtig, den npm-Server zu stoppen, damit er nicht mit dem nächsten Satz von Übungen in Konflikt gerät.

1. Schließen Sie die Fenster Visual Studio Code und Eingabeaufforderung .


## Lektion 5

### Ziel

Wiedergabe des Formulars als Headless-Formular über die Google Material-Benutzeroberfläche

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie das zuvor erstellte adaptive Formular mithilfe der Google Material-Benutzeroberfläche als Headless-Formular wiedergeben.

### Übung

Richten Sie das lokale Repository mithilfe des Starterprojekts der Materialbenutzeroberfläche ein:

1. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.

   ![](/help/forms/assets/screenshot2028115829.png)


1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zu **c:\git** Ordner:

   ```Shell
   cd c:\git
   ```

1. Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus, um einen Ordner mit dem Namen mui zu erstellen und mithilfe der folgenden Befehle zum Ordner mui zu navigieren:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Verwenden Sie den folgenden Befehl, um das React-Starter-Projekt des adaptiven Formulars zu klonen:

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. Verwenden Sie den folgenden Befehl in der angegebenen Reihenfolge, um zum **react-starter-kit-aem-headless-forms** und öffnen Sie den Code in Visual Studio Code:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

So rendern Sie das in Ihrer Cloud Service-Veröffentlichungsumgebung gehostete Formular:

1. Benennen Sie die **env_template** Datei in **.env** -Datei. Klicken Sie zum Umbenennen mit der rechten Maustaste auf die **env_template** Datei und wählen Sie **Umbenennen**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest. Speichern Sie nach dem Aktualisieren der Variablen die Datei. Verwenden Sie die **STRG + S** Wechseln Sie die Kombination, um die Datei zu speichern.

   * **AEM_URL**: Geben Sie die URL der Veröffentlichungsumgebung des Cloud-Service an. Beispiel: [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: Geben Sie den Pfad des adaptiven Formulars an, das in der vorherigen Lektion erstellt wurde. Beispiel: /content/forms/af/registration/

      ![](/help/forms/assets/screenshot2028126929.png)

1. Öffnen Sie das Befehlsfenster, um sicherzustellen, dass Sie sich im **react-starter-kit-aem-headless-forms** und führen Sie den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. Führen Sie im Fenster Eingabeaufforderung den folgenden Befehl aus:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   Der Befehl startet einen lokalen Entwicklungsserver und rendert die von AEM abgerufene Formulardefinition per Frontend-Bibliothek der Google-Benutzeroberfläche.

   >[!NOTE]
   >
   >Wenn nach der Ausführung des `npm start` Befehl für mehr als 3-4 Minuten, ändern Sie `localhost` in der Browser-URL auf 127.0.0.1 und Treffer **Eingabe**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. So bewerten Sie die Ausführung derselben Geschäftslogik in dieser Formularausgabe:

   Auswählen **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten.**. Die nachfolgende Option **Möchten Sie sich für das We.Finance Corporate Credit Card Formular bewerben?** wird deaktiviert.

   ![](/help/forms/assets/screenshot2028127329.png)

## Lektion 6

### Ziel

Erstellen Sie ein alternatives Erscheinungsbild des Headless-Formulars mithilfe der Komponentenvarianten der Materialbenutzeroberfläche

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie mithilfe der Materialbenutzeroberfläche eine alternative Darstellung verschiedener Komponenten für das adaptive Formular erstellen, das zuvor vom Business-Anwender erstellt wurde.

### Übung

Aktualisieren Sie die Variation der Komponenten im Headless-Projekt. So ändern Sie die Variante der Texteingabekomponente der materiellen Benutzeroberfläche in `OutlinedInput`:

1. Navigieren Sie in Visual Code zur Texteingabekomponente, indem Sie die `index.tsx` Datei unter `src/components/textinput/index.tsx`.

1. Hinzufügen `//` am Anfang der Codezeile 103. Die Zeile wird in einen Kommentar umgewandelt.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Fügen Sie in Zeile 104 Folgendes hinzu, um eine andere Variante der Komponente zu verwenden und die Datei zu speichern. Verwenden Sie die **STRG + S** Wechseln Sie die Kombination, um die Datei zu speichern.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   Es ist wichtig, die richtige Groß-/Kleinschreibung für die Variante &quot;OutlineInput&quot;zu verwenden, da die Kompilierung andernfalls fehlschlagen würde. Die Kompilierung der lokalen Entwicklungsumgebung beginnt automatisch in der Eingabeaufforderung. Warten Sie, bis die folgende Meldung angezeigt wird

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Aktualisieren Sie den Browser, wenn er nicht automatisch aktualisiert wird, um zu sehen, wie die Texteingabe-Komponente eine andere Variante verwendet.

   ![](/help/forms/assets/screenshot2028127729.png)


   Diese Änderung erfolgt für Endbenutzer ohne Änderung der Formulardefinition auf dem AEM Forms-Server und ist spezifisch für den betreffenden Headless-Kanal. Beispiel: Webkanal in diesem Labor.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Schließen Sie Visual Studio Code und Eingabeaufforderung Windows.

## Häufig gestellte Fragen (FAQs)

+++ Ist der Assistent für adaptive Formulare öffentlich verfügbar?

Ja, es ist mit AEM Forms als Cloud Service verfügbar.

+++


+++ Sind Kernkomponenten öffentlich verfügbar?

Ja, die Kernkomponenten des adaptiven Forms sind mit AEM Forms als Cloud Service verfügbar.

+++

+++ Sind Headless-Formulare öffentlich verfügbar?

Ja, Headless-Formulare sind mit AEM Forms als Cloud Service verfügbar.

+++

+++ Benötigen Headless-Formulare eine separate Lizenz?

Nein, Headless-Formulare verwenden dieselbe Lizenzwertmetrik, die Anzahl der Formularübermittlungen.

+++

+++ Sind Kernkomponenten und Headless-Formulare in AEM 6.5 Forms verfügbar?

Ja, sowohl Kernkomponenten für adaptive Formulare als auch Headless-Formulare sind mit AEM Forms 6.5 Service Pack 16 und höher verfügbar.

+++


## Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie adaptive Formulare erstellen und über Headless-Formulare an mehrere Kanäle senden, sollten Sie versuchen, Ihre neuen Fähigkeiten in die Tat umzusetzen. Viel Spaß und machen Sie weiter, indem Sie außergewöhnliche Erlebnisse für die Datenerfassung erstellen und Ihren Endbenutzern, wo sie sind, im Maßstab bereitstellen.

## Ressourcen

* [Einführung in die Kernkomponenten des adaptiven Formulars](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [Erstellen eines adaptiven Formulars mit Kernkomponenten](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Aktualisierungsstile für die auf Kernkomponenten basierende AF](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless-adaptive Formulare](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Verwenden des Headless-React-Starter-Kits](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)


