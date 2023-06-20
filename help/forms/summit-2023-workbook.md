---
title: Erstellen ansprechender Formulare mithilfe von Kernkomponenten und Headless
seo-title: Build Engaging Forms Using Core Components and Headless
description: Erstellen ansprechender Formulare mithilfe von Kernkomponenten und Headless
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
exl-id: e1eb0812-c92e-4a18-aabb-5a70b9e6fc7d
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '3359'
ht-degree: 99%

---

# Erstellen ansprechender Formulare mithilfe von Kernkomponenten und Headless

## Labor-Übersicht

In diesem praktischen Labor lernen Sie:

Die Verwendung von AEM Forms zur einfachen Erstellung adaptiver Formulare mithilfe der neuesten Kernkomponenten, die mit AEM Sites konsistent sind, Erlebnisse für die Omni-Channel-Datenerfassung ermöglichen, indem adaptive Formulare als Headless-Formulare an Web, Mobile und Chat übermittelt werden. Außerdem lernen Sie Best Practices rund um die Formatierung, Anpassungen und Frontend-Entwicklung kennen.

## Haupterkenntnisse

* **Geschäftliche Agilität**: Als Business-Anwenderin bzw. -Anwender kann ich mühelos Formularerlebnisse für mehrere Kanäle erstellen.

* **Unterstützung für Frontend-Entwickler**: Als Frontend-Entwicklungsperson kann ich das Anwendererlebnis mit Headless-Formularen steuern.

* **Entwicklergeschindigkeit**: Als Entwicklungsperson kann ich mühelos und konsistent Sites- und Forms-Komponenten anpassen.

## Voraussetzungen


+++AEM Forms as Cloud Service-Sandbox



<table>
        <thead>
            <tr><th>Labor-ID</th><th>URL der Autoreninstanz</th><th>URL der Veröffentlichungsinstanz</th></tr>           
        </thead>
        <tbody>
            <tr><td>L716001</td><td>https://author-p105303-e986623.adobeaemcloud.com</td><td>https://publish-p105303-e986623.adobeaemcloud.com</td></tr><tr><td>L716002</td><td>https://author-p106405-e993047.adobeaemcloud.com</td><td>https://publish-p106405-e993047.adobeaemcloud.com</td></tr><tr><td>L716003</td><td>https://author-p106406-e993049.adobeaemcloud.com</td><td>https://publish-p106406-e993049.adobeaemcloud.com</td></tr><tr><td>L716004</td><td>https://author-p106398-e993114.adobeaemcloud.com</td><td>https://publish-p106398-e993114.adobeaemcloud.com</td></tr><tr><td>L716005</td><td>https://author-p106407-e993048.adobeaemcloud.com</td><td>https://publish-p106407-e993048.adobeaemcloud.com</td></tr><tr><td>L716006</td><td>https://author-p106408-e993155.adobeaemcloud.com</td><td>https://publish-p106408-e993155.adobeaemcloud.com</td></tr><tr><td>L716007</td><td>https://author-p106343-e993067.adobeaemcloud.com</td><td>https://publish-p106343-e993067.adobeaemcloud.com</td></tr><tr><td>L716008</td><td>https://author-p106399-e993108.adobeaemcloud.com</td><td>https://publish-p106399-e993108.adobeaemcloud.com</td></tr><tr><td>L716009</td><td>https://author-p106344-e993064.adobeaemcloud.com</td><td>https://publish-p106344-e993064.adobeaemcloud.com</td></tr><tr><td>L716010</td><td>https://author-p106409-e993051.adobeaemcloud.com</td><td>https://publish-p106409-e993051.adobeaemcloud.com</td></tr><tr><td>L716011</td><td>https://author-p106345-e993060.adobeaemcloud.com</td><td>https://publish-p106345-e993060.adobeaemcloud.com</td></tr><tr><td>L716012</td><td>https://author-p106346-e993061.adobeaemcloud.com</td><td>https://publish-p106346-e993061.adobeaemcloud.com</td></tr><tr><td>L716013</td><td>https://author-p106410-e993153.adobeaemcloud.com</td><td>https://publish-p106410-e993153.adobeaemcloud.com</td></tr><tr><td>L716014</td><td>https://author-p106502-e993073.adobeaemcloud.com</td><td>https://publish-p106502-e993073.adobeaemcloud.com</td></tr><tr><td>L716015</td><td>https://author-p106401-e993112.adobeaemcloud.com</td><td>https://publish-p106401-e993112.adobeaemcloud.com</td></tr><tr><td>L716016</td><td>https://author-p106452-e993115.adobeaemcloud.com</td><td>https://publish-p106452-e993115.adobeaemcloud.com</td></tr><tr><td>L716017</td><td>https://author-p106453-e993113.adobeaemcloud.com</td><td>https://publish-p106453-e993113.adobeaemcloud.com</td></tr><tr><td>L716018</td><td>https://author-p106411-e993050.adobeaemcloud.com</td><td>https://publish-p106411-e993050.adobeaemcloud.com</td></tr><tr><td>L716019</td><td>https://author-p106454-e993116.adobeaemcloud.com</td><td>https://publish-p106454-e993116.adobeaemcloud.com</td></tr><tr><td>L716020</td><td>https://author-p106347-e993063.adobeaemcloud.com</td><td>https://publish-p106347-e993063.adobeaemcloud.com</td></tr><tr><td>L716021</td><td>https://author-p106455-e993109.adobeaemcloud.com</td><td>https://publish-p106455-e993109.adobeaemcloud.com</td></tr><tr><td>L716022</td><td>https://author-p106456-e993110.adobeaemcloud.com</td><td>https://publish-p106456-e993110.adobeaemcloud.com</td></tr><tr><td>L716023</td><td>https://author-p106466-e993291.adobeaemcloud.com</td><td>https://publish-p106466-e993291.adobeaemcloud.com</td></tr><tr><td>L716024</td><td>https://author-p106413-e993156.adobeaemcloud.com</td><td>https://publish-p106413-e993156.adobeaemcloud.com</td></tr><tr><td>L716025</td><td>https://author-p106348-e993066.adobeaemcloud.com</td><td>https://publish-p106348-e993066.adobeaemcloud.com</td></tr><tr><td>L716026</td><td>https://author-p106414-e993154.adobeaemcloud.com</td><td>https://publish-p106414-e993154.adobeaemcloud.com</td></tr><tr><td>L716027</td><td>https://author-p106349-e993065.adobeaemcloud.com</td><td>https://publish-p106349-e993065.adobeaemcloud.com</td></tr><tr><td>L716028</td><td>https://author-p106415-e993152.adobeaemcloud.com</td><td>https://publish-p106415-e993152.adobeaemcloud.com</td></tr><tr><td>L716029</td><td>https://author-p106350-e993068.adobeaemcloud.com</td><td>https://publish-p106350-e993068.adobeaemcloud.com</td></tr><tr><td>L716030</td><td>https://author-p106351-e993062.adobeaemcloud.com</td><td>https://publish-p106351-e993062.adobeaemcloud.com</td></tr><tr><td>L716031</td><td>https://author-p106417-e993158.adobeaemcloud.com</td><td>https://publish-p106417-e993158.adobeaemcloud.com</td></tr><tr><td>L716032</td><td>https://author-p106418-e993159.adobeaemcloud.com</td><td>https://publish-p106418-e993159.adobeaemcloud.com</td></tr><tr><td>L716033</td><td>https://author-p106503-e993080.adobeaemcloud.com</td><td>https://publish-p106503-e993080.adobeaemcloud.com</td></tr><tr><td>L716034</td><td>https://author-p106457-e993125.adobeaemcloud.com</td><td>https://publish-p106457-e993125.adobeaemcloud.com</td></tr><tr><td>L716035</td><td>https://author-p106504-e993081.adobeaemcloud.com</td><td>https://publish-p106504-e993081.adobeaemcloud.com</td></tr><tr><td>L716036</td><td>https://author-p106458-e993120.adobeaemcloud.com</td><td>https://publish-p106458-e993120.adobeaemcloud.com</td></tr><tr><td>L716037</td><td>https://author-p106419-e993160.adobeaemcloud.com</td><td>https://publish-p106419-e993160.adobeaemcloud.com</td></tr><tr><td>L716038</td><td>https://author-p106420-e993162.adobeaemcloud.com</td><td>https://publish-p106420-e993162.adobeaemcloud.com</td></tr><tr><td>L716039</td><td>https://author-p106517-e993235.adobeaemcloud.com</td><td>https://publish-p106517-e993235.adobeaemcloud.com</td></tr><tr><td>L716040</td><td>https://author-p106506-e993079.adobeaemcloud.com</td><td>https://publish-p106506-e993079.adobeaemcloud.com</td></tr><tr><td>L716041</td><td>https://author-p106507-e993074.adobeaemcloud.com</td><td>https://publish-p106507-e993074.adobeaemcloud.com</td></tr><tr><td>L716042</td><td>https://author-p106508-e993075.adobeaemcloud.com</td><td>https://publish-p106508-e993075.adobeaemcloud.com</td></tr><tr><td>L716043</td><td>https://author-p106421-e993163.adobeaemcloud.com</td><td>https://publish-p106421-e993163.adobeaemcloud.com</td></tr><tr><td>L716044</td><td>https://author-p106459-e993121.adobeaemcloud.com</td><td>https://publish-p106459-e993121.adobeaemcloud.com</td></tr><tr><td>L716045</td><td>https://author-p106467-e993292.adobeaemcloud.com</td><td>https://publish-p106467-e993292.adobeaemcloud.com</td></tr><tr><td>L716046</td><td>https://author-p106518-e993234.adobeaemcloud.com</td><td>https://publish-p106518-e993234.adobeaemcloud.com</td></tr><tr><td>L716047</td><td>https://author-p106511-e993076.adobeaemcloud.com</td><td>https://publish-p106511-e993076.adobeaemcloud.com</td></tr><tr><td>L716048</td><td>https://author-p106512-e993077.adobeaemcloud.com</td><td>https://publish-p106512-e993077.adobeaemcloud.com</td></tr><tr><td>L716049</td><td>https://author-p106460-e993124.adobeaemcloud.com</td><td>https://publish-p106460-e993124.adobeaemcloud.com</td></tr><tr><td>L716050</td><td>https://author-p106519-e993237.adobeaemcloud.com</td><td>https://publish-p106519-e993237.adobeaemcloud.com</td></tr><tr><td>L716051</td><td>https://author-p106513-e993084.adobeaemcloud.com</td><td>https://publish-p106513-e993084.adobeaemcloud.com</td></tr><tr><td>L716052</td><td>https://author-p106461-e993122.adobeaemcloud.com</td><td>https://publish-p106461-e993122.adobeaemcloud.com</td></tr><tr><td>L716053</td><td>https://author-p106514-e993082.adobeaemcloud.com</td><td>https://publish-p106514-e993082.adobeaemcloud.com</td></tr><tr><td>L716054</td><td>https://author-p106462-e993123.adobeaemcloud.com</td><td>https://publish-p106462-e993123.adobeaemcloud.com</td></tr><tr><td>L716055</td><td>https://author-p106463-e993127.adobeaemcloud.com</td><td>https://publish-p106463-e993127.adobeaemcloud.com</td></tr><tr><td>L716056</td><td>https://author-p106515-e993083.adobeaemcloud.com</td><td>https://publish-p106515-e993083.adobeaemcloud.com</td></tr><tr><td>L716057</td><td>https://author-p106464-e993126.adobeaemcloud.com</td><td>https://publish-p106464-e993126.adobeaemcloud.com</td></tr><tr><td>L716058</td><td>https://author-p106520-e993236.adobeaemcloud.com</td><td>https://publish-p106520-e993236.adobeaemcloud.com</td></tr><tr><td>L716059</td><td>https://author-p106423-e993161.adobeaemcloud.com</td><td>https://publish-p106423-e993161.adobeaemcloud.com</td></tr><tr><td>L716060</td><td>https://author-p106516-e993078.adobeaemcloud.com</td><td>https://publish-p106516-e993078.adobeaemcloud.com</td></tr><tr><td>L716061</td><td>https://author-p106521-e993240.adobeaemcloud.com</td><td>https://publish-p106521-e993240.adobeaemcloud.com</td></tr><tr><td>L716062</td><td>https://author-p106424-e993308.adobeaemcloud.com</td><td>https://publish-p106424-e993308.adobeaemcloud.com</td></tr><tr><td>L716063</td><td>https://author-p106468-e993295.adobeaemcloud.com</td><td>https://publish-p106468-e993295.adobeaemcloud.com</td></tr><tr><td>L716064</td><td>https://author-p106425-e993309.adobeaemcloud.com</td><td>https://publish-p106425-e993309.adobeaemcloud.com</td></tr><tr><td>L716065</td><td>https://author-p106426-e993314.adobeaemcloud.com</td><td>https://publish-p106426-e993314.adobeaemcloud.com</td></tr><tr><td>L716066</td><td>https://author-p106469-e993293.adobeaemcloud.com</td><td>https://publish-p106469-e993293.adobeaemcloud.com</td></tr><tr><td>L716067</td><td>https://author-p106522-e993238.adobeaemcloud.com</td><td>https://publish-p106522-e993238.adobeaemcloud.com</td></tr><tr><td>L716068</td><td>https://author-p106470-e993299.adobeaemcloud.com</td><td>https://publish-p106470-e993299.adobeaemcloud.com</td></tr><tr><td>L716069</td><td>https://author-p106427-e993311.adobeaemcloud.com</td><td>https://publish-p106427-e993311.adobeaemcloud.com</td></tr><tr><td>L716070</td><td>https://author-p106428-e993310.adobeaemcloud.com</td><td>https://publish-p106428-e993310.adobeaemcloud.com</td></tr><tr><td>L716071</td><td>https://author-p106471-e993298.adobeaemcloud.com</td><td>https://publish-p106471-e993298.adobeaemcloud.com</td></tr><tr><td>L716072</td><td>https://author-p106429-e993315.adobeaemcloud.com</td><td>https://publish-p106429-e993315.adobeaemcloud.com</td></tr><tr><td>L716073</td><td>https://author-p106523-e993239.adobeaemcloud.com</td><td>https://publish-p106523-e993239.adobeaemcloud.com</td></tr><tr><td>L716074</td><td>https://author-p106472-e993300.adobeaemcloud.com</td><td>https://publish-p106472-e993300.adobeaemcloud.com</td></tr><tr><td>L716075</td><td>https://author-p106430-e993312.adobeaemcloud.com</td><td>https://publish-p106430-e993312.adobeaemcloud.com</td></tr><tr><td>L716076</td><td>https://author-p106524-e993241.adobeaemcloud.com</td><td>https://publish-p106524-e993241.adobeaemcloud.com</td></tr><tr><td>L716077</td><td>https://author-p106431-e993313.adobeaemcloud.com</td><td>https://publish-p106431-e993313.adobeaemcloud.com</td></tr><tr><td>L716078</td><td>https://author-p106473-e993294.adobeaemcloud.com</td><td>https://publish-p106473-e993294.adobeaemcloud.com</td></tr><tr><td>L716079</td><td>https://author-p106474-e993297.adobeaemcloud.com</td><td>https://publish-p106474-e993297.adobeaemcloud.com</td></tr><tr><td>L716080</td><td>https://author-p106475-e993296.adobeaemcloud.com</td><td>https://publish-p106475-e993296.adobeaemcloud.com</td></tr><tr><td>L716081</td><td>https://author-p106476-e993353.adobeaemcloud.com</td><td>https://publish-p106476-e993353.adobeaemcloud.com</td></tr><tr><td>L716082</td><td>https://author-p106525-e993247.adobeaemcloud.com</td><td>https://publish-p106525-e993247.adobeaemcloud.com</td></tr><tr><td>L716083</td><td>https://author-p106526-e993244.adobeaemcloud.com</td><td>https://publish-p106526-e993244.adobeaemcloud.com</td></tr><tr><td>L716084</td><td>https://author-p106527-e993243.adobeaemcloud.com</td><td>https://publish-p106527-e993243.adobeaemcloud.com</td></tr><tr><td>L716085</td><td>https://author-p106477-e993356.adobeaemcloud.com</td><td>https://publish-p106477-e993356.adobeaemcloud.com</td></tr><tr><td>L716086</td><td>https://author-p106478-e993355.adobeaemcloud.com</td><td>https://publish-p106478-e993355.adobeaemcloud.com</td></tr><tr><td>L716087</td><td>https://author-p106528-e993245.adobeaemcloud.com</td><td>https://publish-p106528-e993245.adobeaemcloud.com</td></tr><tr><td>L716088</td><td>https://author-p106432-e993316.adobeaemcloud.com</td><td>https://publish-p106432-e993316.adobeaemcloud.com</td></tr><tr><td>L716089</td><td>https://author-p106529-e993242.adobeaemcloud.com</td><td>https://publish-p106529-e993242.adobeaemcloud.com</td></tr><tr><td>L716090</td><td>https://author-p106436-e993320.adobeaemcloud.com</td><td>https://publish-p106436-e993320.adobeaemcloud.com</td></tr><tr><td>L716091</td><td>https://author-p106480-e993301.adobeaemcloud.com</td><td>https://publish-p106480-e993301.adobeaemcloud.com</td></tr><tr><td>L716092</td><td>https://author-p106530-e993246.adobeaemcloud.com</td><td>https://publish-p106530-e993246.adobeaemcloud.com</td></tr><tr><td>L716093</td><td>https://author-p106481-e993352.adobeaemcloud.com</td><td>https://publish-p106481-e993352.adobeaemcloud.com</td></tr><tr><td>L716094</td><td>https://author-p106482-e993354.adobeaemcloud.com</td><td>https://publish-p106482-e993354.adobeaemcloud.com</td></tr><tr><td>L716095</td><td>https://author-p106531-e993248.adobeaemcloud.com</td><td>https://publish-p106531-e993248.adobeaemcloud.com</td></tr><tr><td>L716096</td><td>https://author-p106483-e993357.adobeaemcloud.com</td><td>https://publish-p106483-e993357.adobeaemcloud.com</td></tr><tr><td>L716097</td><td>https://author-p106433-e993318.adobeaemcloud.com</td><td>https://publish-p106433-e993318.adobeaemcloud.com</td></tr><tr><td>L716098</td><td>https://author-p106532-e993249.adobeaemcloud.com</td><td>https://publish-p106532-e993249.adobeaemcloud.com</td></tr><tr><td>L716099</td><td>https://author-p106434-e993317.adobeaemcloud.com</td><td>https://publish-p106434-e993317.adobeaemcloud.com</td></tr><tr><td>L716100</td><td>https://author-p106435-e993319.adobeaemcloud.com</td><td>https://publish-p106435-e993319.adobeaemcloud.com</td></tr>
        </tbody>
</table>

+++

## Lektion 1

### Ziel

Machen Sie sich mit der AEM Forms as a Cloud Service-Umgebung vertraut.

### Lektionskontext

In dieser Lektion lernen Sie die AEM Forms as a Cloud Service-Umgebung kennen, indem Sie in der Benutzeroberfläche navigieren.

### Übung

1. Öffnen Sie den Browser und geben Sie die URL der Autorenumgebung von Cloud Service ein.

1. Melden Sie sich bei der Autorenumgebung von Cloud Service an. Die Anmeldedaten für Ihre Autorenumgebung werden für Sie im Labor freigegeben.

1. Nachdem Sie angemeldet sind, navigieren Sie zur AEM Forms-Benutzeroberfläche. Klicken Sie auf **Formulare**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. Klicken Sie auf **Formulare und Dokumente**. Schließen Sie alle Popups, die sich auf Voreinstellungen oder Informationen beziehen.

   ![](/help/forms/assets/screenshot2028113929.png)

   Alle verfügbaren Formulare werden angezeigt.

   ![](/help/forms/assets/screenshot2028114029.png)

## Lektion 2

### Ziel

Erstellen Sie ein adaptives Formular mit den neuesten Kernkomponenten, konfigurieren Sie es und übermitteln Sie es.

### Lektionskontext

In dieser Lektion erstellen Sie als Business-Anwenderin oder -Anwender ein adaptives Formular für mehrere Kanäle wie Web, Mobile und Chat, indem Sie adaptive Formulare mit standardisierten OOTB-Kernkomponenten für die Datenerfassung erstellen.

### Übung

1. Erstellen Sie einen Übermittlungsendpunkt für das Formular:

   1. Öffnen Sie <https://requestbin.com/> in einer neuen Browser-Registerkarte.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. Klicken Sie auf **Öffentlichen Container erstellen** und kopieren Sie die Endpunkt-URL.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. Erstellen Sie ein adaptives Formular mithilfe der Assistenten-Oberfläche:

   1. Navigieren Sie auf der in Lektion 1 verwendeten Browser-Registerkarte zur Web-Benutzeroberfläche von AEM Forms als Cloud Service und dort zu „Formulare und Dokumente“.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. Klicken Sie auf **Erstellen** und wählen Sie „Adaptives Formular“.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. Wählen Sie die Vorlage **Leer mit Kernkomponenten** aus dem Vorlagenauswahlbildschirm wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Klicken Sie auf die Registerkarte **Stil** und wählen Sie das Design **wknd-theme** wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Klicken Sie auf die Registerkarte **Übermitteln**, wählen Sie die Karte **An REST-Endpunkt übermitteln** und geben Sie den öffentlichen Ordner im
      Feld **URL für die POST-Anfrage** an, wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Klicken Sie auf **Erstellen**. Geben Sie einen Namen und einen Titel für Ihr Formular an. Beispiel: **Kontakt**. Klicken Sie auf **Erstellen**.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. Der Editor für adaptive Formulare wird geöffnet. Schließen Sie alle Popups oder Dialogfelder für Voreinstellungen oder Informationen. Klicken Sie in der linken Leiste auf den Komponenten-Browser und fügen Sie die **Fußzeilenkomponente** am unteren Rand des leeren Formulars hinzu.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. Die Kopfzeile ist Teil der adaptiven Formularvorlage. Dies ermöglicht eine einfache Möglichkeit, eine konsistente Kopf-/Fußzeile für alle adaptiven Formulare bereitzustellen. Alternativ können Sie auch festlegen, dass sie im Formular bearbeitbar bleibt, wie es im nächsten Schritt für die Fußzeilenkomponente angezeigt wird.

   1. Fügen Sie eine **Titelkomponente** in die Mitte des Formulars hinzu.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. Fügen Sie eine **Texteingaben**-Komponente nach der Titelkomponente hinzu.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. Fügen Sie eine **Zahleneingaben**-Komponente hinzu.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. Fügen Sie eine **Senden-Schaltflächen**-Komponente in das Formular hinzu.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. Klicken Sie auf die **Titelkomponente**, damit das **Popup-Menü** angezeigt wird. Klicken Sie im Menü auf das Symbol **Bearbeiten**, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Geben Sie `Contact Us` als Titeltext ein.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. Klicken Sie auf die **Texteingaben**-Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie im Menü auf das Symbol **Bearbeiten**, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Geben Sie **Vollständiger Name** als Feldbezeichnung ein.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. Klicken Sie auf die **Zahleneingaben**-Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie im Menü auf das Symbol **Bearbeiten**, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. Geben Sie **Telefonnummer** als Feldbezeichnung ein.
      ![](/help/forms/assets/screenshot2028123829.png)


1. Fügen Sie Validierungen zum Formular hinzu:

   1. Klicken Sie auf die **Telefonnummern**-Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie im Menü auf das **Schraubensymbol**, um das Feld zu konfigurieren.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. Öffnen Sie die Registerkarte **Validierungen**, markieren Sie das Feld **Erforderlich**, und klicken Sie auf **Fertig**. Die Erfolgsmeldung wird angezeigt.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. Klicken Sie auf **Vorschau**, um eine Vorschau des Formulars aus der Perspektive von Endbenutzerinnen bzw. -benutzern anzuzeigen.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. Füllen Sie das Formular mit Platzhalterdaten aus
      ![](/help/forms/assets/screenshot2028125629.png)

   1. Formular senden
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Überprüfen Sie in der Registerkarte „Anfrage-Container“ die gesendeten Daten.
      ![](/help/forms/assets/screenshot2028125829.png)

Verwenden Sie nun für die verbleibende Übung ein vorab erstelltes Registrierungsformular.

1. Öffnen Sie die Verwaltungsoberfläche von AEM Forms, z. B. `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`, und wählen Sie das Registrierungsformular aus.

   ![](/help/forms/assets/screenshot2028115529.png)

1. Klicken Sie auf **Veröffentlichen**.

   ![](/help/forms/assets/screenshot2028115629.png)

   Die Erfolgsmeldung wird angezeigt.

   ![](/help/forms/assets/screenshot2028115729.png)

   Die Veröffentlichungs-URL des Formulars ähnelt `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. Ersetzen Sie zum Anzeigen des veröffentlichten Formulars die Programm-ID (pXXXXXX) und die Umgebungs-ID (eXXXXXX) in der obigen URL durch die IDs Ihrer 
Umgebung.

## Lektion 3

### Ziel

Aktualisieren Sie Stile mithilfe der Best Practices für die Frontend-Entwicklung.

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwicklungsperson, wie Sie die Formatierung für das zuvor erstellte adaptive Formular einfach aktualisieren können.

### Übung

Richten Sie ein lokales Repository des Designs ein:

1. Öffnen Sie die Eingabeaufforderung oder Shell mit Administratorrechten:

   ![](/help/forms/assets/screenshot2028115829.png)

1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zum Ordner **c:\git** zu navigieren

   ```Shell
   cd c:\git
   ```

1. Verwenden Sie den folgenden Befehl, um den Frontend-Code des Designs zu klonen:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Verwenden Sie den folgenden Befehl in der angegebenen Reihenfolge, um zum Verzeichnis **aem-forms-theme-canvas** zu navigieren und Visual Studio Code zu öffnen.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. Wählen Sie **Trust the authors of all files in the parent folder** und klicken Sie auf **Yes, I trust the authors**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. Um das in der Publishing-Umgebung Ihres Cloud-Service gehostete Formular wiederzugeben, benennen Sie die Datei `env_template` um. Um die Datei umzubenennen, klicken Sie mit der rechten Maustaste auf die Datei **env_template** und wählen Sie die Option **Umbenennen**.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest und speichern Sie die Datei:

   * **AEM_URL**: Geben Sie die Publishing-Umgebung Ihres Cloud-Service an. Beispiel: `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: Geben Sie den Pfad des Formulars an. Wenn der Formularpfad beispielsweise `/content/forms/af/registration` ist, würde der Wert dieser Variablen `registration` sein.

   ![](/help/forms/assets/screenshot2028116429.png)


1. Führen Sie im Eingabeaufforderungsfenster den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Wenn Sie eine Meldung erhalten, in der Sie aufgefordert werden, npm über den Befehl `npm notice Run npm nstall -g npm@9.6.0`zu aktualisieren, ignorieren Sie die Meldung.
   > * Führen Sie keine anderen npm-Befehle aus, es sei denn, Sie werden dazu in der Arbeitsmappe angewiesen.

1. Führen Sie nun den folgenden Befehl aus, um eine Vorschau des Formulars anzuzeigen.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   Warten Sie nach Ausführung des oben genannten Befehls auf die Nachricht `webpack compiled`. Das Formular wird auf einer Browser-Registerkarte angezeigt.

   >[!NOTE]
   >
   >Wenn nach der Ausführung des Befehls `npm run live` für mehr als 3–4 Minuten ein leerer Browser-Bildschirm erscheint, ändern Sie `localhost` in der Browser-URL zu 127.0.0.1 und betätigen Sie die **Eingabetaste**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Öffnen Sie in Visual Studio Code die Datei `PROJECT\src\site\_variables.scss`. Beachten Sie, dass die Farbe `$error` ein Farbton von ROT ist.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Übermitteln Sie das Formular im Browser, um die rote Farbe im Feld **Vorname** zu sehen.

   ![](/help/forms/assets/screenshot2028120829.png)

1. Legen Sie die Farbe für **$error** auf **#5736eb** fest und speichern Sie die Datei.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Aktualisieren Sie den Browser und übermitteln Sie das Formular. Sie sehen, dass sich die Fehlerfarbe im Vorname-Feld entsprechend geändert hat.

   ![](/help/forms/assets/screenshot2028121129.png)

1. Drücken Sie in der Eingabeaufforderung **Strg+C**, geben Sie **Y** ein und drücken Sie die **Eingabetaste** zum Beenden des npm-Prozesses. Es ist wichtig, den npm-Server anzuhalten, damit er nicht mit dem nächsten Satz von Übungen in Konflikt gerät.
1. Schließen Sie Visual Studio Code und das Eingabeaufforderungsfenster.

## Lektion 4

### Ziel

Rendern Sie das Formular auf Web-/Mobile- und anderen Benutzeroberflächen als Headless-Formular.

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwicklungsperson, wie Sie das zuvor erstellte adaptive Formular mithilfe des React-Spektrum-Design-Frameworks als Headless-Formular rendern können.

### Übung

Richten Sie ein lokales Repository mithilfe des React-Starter-Projekts ein:

1. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.

   ![](/help/forms/assets/screenshot2028115829.png)

1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zum Ordner **c:\git** zu navigieren

   ```Shell
   cd c:\git
   ```

1. Verwenden Sie den folgenden Befehl, um das React-Starter-Projekt des adaptiven Formulars zu klonen:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. Verwenden Sie die folgenden Befehle in der angegebenen Reihenfolge, um zum Verzeichnis **react-starter-kit-aem-headless-forms** zu navigieren, und öffnen Sie Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Das Fenster „Visual Studio Code“ wird geöffnet.

   ![](/help/forms/assets/screenshot2028117429.png)

So rendern Sie das in der Publishing-Umgebung Ihres Cloud-Service gehostete Formular:

1. Benennen Sie die Datei „env_template“ in eine Datei „.env“ um. Klicken Sie zum Umbenennen mit der rechten Maustaste auf die Datei **env_template** und wählen Sie die Option **Umbenennen**.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest. Speichern Sie die Datei nach dem Aktualisieren der Variablen.

   * **AEM_URL**: Geben Sie die URL der Publishing-Umgebung des Cloud-Service an. Beispiel: `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: Geben Sie den Pfad des adaptiven Formulars an, das in der vorherigen Lektion erstellt wurde. Beispiel: `/content/forms/af/registration/`

     ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Öffnen Sie das Befehlsfenster, stellen Sie sicher, dass Sie sich im Verzeichnis „react-starter-kit-aem-headless-forms“ befinden, und führen Sie den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. Führen Sie im Eingabeaufforderungsfenster den folgenden Befehl aus:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   Der obige Befehl startet einen lokalen Entwicklungs-Server, der die von AEM abgerufene Formulardefinition mithilfe der Frontend-Bibliothek von React Spectrum auf eine Headless-Weise rendert.

   >[!NOTE]
   >
   > 
   > Wenn nach der Ausführung des Befehls `npm start` für mehr als 3–4 Minuten ein leerer Browser-Bildschirm erscheint, ändern Sie `localhost` in der Browser-URL zu 127.0.0.1 und drücken Sie die **Eingabetaste**.

   ![](/help/forms/assets/screenshot2028118229.png)

Überprüfen wir die Ausführung der Regeln in diesem Headless-Formular:

1. Wählen Sie die Option **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten**. Die nachfolgende Option zum Anwenden einer Kreditkarte ist deaktiviert.

   ![](/help/forms/assets/screenshot2028126229.png)

1. Heben Sie die Option **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten** auf, um die Kreditkartenoption zu aktivieren.

   ![](/help/forms/assets/screenshot2028126329.png)

Jetzt nehmen wir als Business-Anwenderin bzw. -Anwender Änderungen am Formular auf dem Server vor und zeigen die Änderungen automatisch im Headless-Formular an.

1. Öffnen Sie die AEM Forms-Verwaltungsoberfläche im Browser.
\
1. Wählen Sie das **Registrierungsformular** aus und klicken Sie auf **Bearbeiten.** Das Formular wird im Editor für adaptive Formulare geöffnet.

   ![](/help/forms/assets/screenshot2028118529.png)

1. Wählen Sie das Feld **Telefonnummer** und klicken Sie auf das **Symbol „Bearbeiten“ (Bleistiftsymbol)** in der Symbolleiste. Wenn Sie die Popup-Symbolleiste nicht sehen können, wechseln Sie in den Bearbeitungsmodus, indem Sie auf die Schaltfläche **Bearbeiten** oben rechts, links von der Schaltfläche **Vorschau**, klicken.

   ![](/help/forms/assets/screenshot2028119629.png)

1. Ändern Sie die Beschriftung in „Mobiltelefonnummer“. Klicken Sie auf eine leere Stelle im Formular, damit die am Formular vorgenommenen Änderungen gespeichert werden.

   ![](/help/forms/assets/screenshot2028119729.png)

Veröffentlichen wir das aktualisierte Formular, um die Änderungen in die Publishing-Umgebung zu übertragen.

1. Wählen Sie in der Registerkarte der Verwaltungsoberfläche von AEM Forms das Registrierungsformular aus und klicken Sie auf **Veröffentlichung rückgängig machen**. Wenn Sie die Schaltfläche **Veröffentlichung rückgängig machen** nicht sehen, fahren Sie mit Schritt 3 fort, um die Änderungen direkt zu veröffentlichen.

   ![](/help/forms/assets/screenshot2028119829.png)

1. Klicken Sie auf **Veröffentlichung aufheben**. Klicken Sie auf **Schließen** im entsprechenden Dialogfeld.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. Nachdem der Browser aktualisiert wurde, wählen Sie das Registrierungsformular aus und klicken Sie auf **Veröffentlichen**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. Klicken Sie auf **Veröffentlichen**. Klicken Sie auf **Schließen** im entsprechenden Dialogfeld.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Aktualisieren Sie die Browser-Registerkarte mit dem angezeigten Headless-Formular. Beachten Sie, dass die Beschriftung für die Telefonnummer in „Mobiltelefonnummer“ geändert wurde.

   ![](/help/forms/assets/screenshot2028120529.png)

1. Öffnen Sie das Eingabeaufforderungsfenster, das zum Starten des Projekts **react-starter-kit-aem-headless-forms** genutzt wird, drücken Sie **Strg+C**,
geben Sie **Y** ein und drücken Sie die Eingabetaste, um den npm-Prozess zu beenden. Es ist wichtig, den npm-Server anzuhalten, damit er nicht mit dem nächsten Satz von Übungen in Konflikt gerät.

1. Schließen Sie Visual Studio Code und das Eingabeaufforderungsfenster.


## Lektion 5

### Ziel

Rendern des Formulars als Headless-Formular mithilfe der Google Material-Benutzeroberfläche

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwicklerperson, wie Sie das zuvor erstellte adaptive Formular mithilfe der Google Material-Benutzeroberfläche als Headless-Formular wiedergeben.

### Übung

Richten Sie das lokale Repository mithilfe des Ausgangsprojekts der Material-Benutzeroberfläche ein:

1. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.

   ![](/help/forms/assets/screenshot2028115829.png)


1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zum Ordner **c:\git** zu navigieren:

   ```Shell
   cd c:\git
   ```

1. Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus, um einen Ordner mit dem Namen „mui“ zu erstellen und zu diesem Ordner zu navigieren:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Verwenden Sie den folgenden Befehl, um das React-Starter-Projekt des adaptiven Formulars zu klonen:

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. Verwenden Sie die folgenden Befehle in der aufgeführten Reihenfolge, um zum Ordner **react-starter-kit-aem-headless-forms** zu navigieren und den Code in Visual Studio Code zu öffnen:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

So rendern Sie das in der Publishing-Umgebung Ihres Cloud-Service gehostete Formular:

1. Benennen Sie die Datei **env_template** in eine Datei **.env** um. Klicken Sie zum Umbenennen mit der rechten Maustaste auf die Datei **env_template** und wählen Sie **Umbenennen**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest. Speichern Sie die Datei nach dem Aktualisieren der Variablen. Verwenden Sie die Tastenkombination **Strg+S**, um die Datei zu speichern.

   * **AEM_URL**: Geben Sie die URL der Publishing-Umgebung des Cloud-Service an.

   * **AEM_FORM_PATH**: Geben Sie den Pfad des adaptiven Formulars an, das in der vorherigen Lektion erstellt wurde. Beispiel: /content/forms/af/registration/

     ![](/help/forms/assets/screenshot2028126929.png)

1. Öffnen Sie das Befehlsfenster, stellen Sie sicher, dass Sie sich im Verzeichnis **react-starter-kit-aem-headless-forms** befinden, und führen Sie den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. Führen Sie im Eingabeaufforderungsfenster den folgenden Befehl aus:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   Der Befehl startet einen lokalen Entwicklungs-Server und rendert die von AEM abgerufene Formulardefinition mithilfe der 
Frontend-Bibliothek der Google Material-Benutzeroberfläche auf eine Headless-Weise.

   >[!NOTE]
   >
   >Wenn nach der Ausführung des Befehls `npm start` für mehr als 3–4 Minuten ein leerer Browser-Bildschirm erscheint, ändern Sie `localhost` in der Browser-URL zu 127.0.0.1 und drücken Sie die **Eingabetaste**

   ![](/help/forms/assets/screenshot2028127229.png)

1. So bewerten Sie die Ausführung derselben Business-Logik in dieser Formularausgabedarstellung:

   Wählen Sie **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten**. Die nachfolgende Option **Möchten Sie das We.Finance Corporate Kreditkarten-Formular beantragen?** wird deaktiviert.

   ![](/help/forms/assets/screenshot2028127329.png)

## Lektion 6

### Ziel

Erstellen Sie ein alternatives Look-and-Feel des Headless-Formulars mithilfe der Komponentenvarianten der Material-Benutzeroberfläche

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwicklungsperson, wie Sie mithilfe der Material-Benutzeroberfläche eine alternative Darstellung verschiedener Komponenten für das adaptive Formular erstellen, das zuvor von einer Business-Anwenderin oder einem -Anwender erstellt wurde.

### Übung

Aktualisieren Sie die Variation der Komponenten im Headless-Projekt. So ändern Sie die Variante der Texteingabekomponente der materiellen Benutzeroberfläche in `OutlinedInput`:

1. Navigieren Sie in Visual Code zur Texteingabekomponente, indem Sie die Datei `index.tsx` unter `src/components/textinput/index.tsx` öffnen.

1. Fügen Sie `//` am Anfang der Code-Zeile 103 hinzu. Die Zeile wird dadurch in einen Kommentar umgewandelt.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Fügen Sie in Zeile 104 Folgendes hinzu, um eine andere Variante der Komponente zu verwenden und die Datei zu speichern. Verwenden Sie die Tastenkombination **Strg+S**, um die Datei zu speichern.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   Es ist wichtig, die richtige Groß-/Kleinschreibung für die Variante „OutlinedInput“ zu verwenden, da die Kompilierung andernfalls fehlschlagen würde. Die Kompilierung der lokalen Entwicklungsumgebung beginnt automatisch in der Eingabeaufforderung. Warten Sie, bis die folgende Meldung angezeigt wird

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Aktualisieren Sie den Browser, wenn er nicht automatisch aktualisiert wird, um zu sehen, wie die Texteingabe-Komponente eine andere Variante verwendet.

   ![](/help/forms/assets/screenshot2028127729.png)


   Diese Änderung erfolgt für Endbenutzerinnen und -benutzer ohne Änderung der Formulardefinition auf dem AEM Forms-Server und ist spezifisch für den betreffenden Headless-Kanal. Beispiel: Web-Kanal in diesem Labor.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Schließen Sie Visual Studio Code und das Eingabeaufforderungsfenster.

## Häufig gestellte Fragen (FAQs)

+++ Ist der Assistent für adaptive Formulare öffentlich verfügbar?

Ja, er ist mit AEM Forms as a Cloud Service verfügbar.

+++


+++ Sind Kernkomponenten öffentlich verfügbar?

Ja, die Kernkomponenten der adaptiven Formulare sind mit AEM Forms as a Cloud Service verfügbar.

+++

+++ Sind Headless-Formulare öffentlich verfügbar?

Ja, Headless-Formulare sind mit AEM Forms as a Cloud Service verfügbar.

+++

+++ Benötigen Headless-Formulare eine separate Lizenz?

Nein, Headless-Formulare verwenden dieselbe Metrik für den Lizenzwert, nämlich die Anzahl der Formularübertragungen.

+++

+++ Sind Kernkomponenten und Headless-Formulare in AEM 6.5 Forms verfügbar?

Ja, sowohl Kernkomponenten für adaptive Formulare als auch Headless-Formulare sind mit AEM Forms 6.5 Service Pack 16 und höher verfügbar.

+++


## Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie adaptive Formulare erstellen und über Headless-Formulare an mehrere Kanäle senden, sollten Sie versuchen, Ihre neuen Fähigkeiten in die Tat umzusetzen. Viel Spaß beim Erstellen und Bereitstellen von umfangreichen, außergewöhnlichen Datenerfassungserlebnissen für Ihre Endbenutzerinnen und -benutzer, wo auch immer sie sich befinden!

## Ressourcen

* [Einführung zu Kernkomponenten für adaptive Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de)

* [Erstellen eines adaptiven Formulars mit Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=de)

* [Aktualisierungsstile für die auf Kernkomponenten basierenden adaptiven Formulare](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=de)

* [Adaptive Headless-Formulare](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de)

* [Verwenden des Headless-React-Starter-Kits](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=de)
