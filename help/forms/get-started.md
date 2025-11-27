---
title: Erste Schritte mit HTML5-Formularen
description: Um zu beginnen, stellen Sie das AEM Forms-Add-on-Paket bereit und importieren Sie bestehende HTML5-Formulare in AEM.
content-type: reference
topic-tags: hTML5_forms
discoiquuid: f276d150-8936-4bfb-8475-7ca36815b233
feature: HTML5 Forms,Mobile Forms
exl-id: a3245f05-6ea3-4f90-8981-bfa89d2e7335
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 67%

---

# Erste Schritte mit HTML5-Formularen {#getting-started-with-html-forms}

<span class="preview"> Die HTML5-Formularfunktion wird als Teil des Early-Access-Programms angeboten. Um Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (Arbeits-)E-Mail-ID an aem-forms-ea@adobe.com.
</span>

HTML5-Formulare bieten zahlreiche, für Mobilgeräte geeignete Funktionen. So können Sie Ihre aktuellen Lösungen und Workflows auf Tablets oder Smartphones mit HTML5-Browsern erweitern. Zu den Funktionen gehören:

* **HTML5-basiertes Rendern von XFA-Formularvorlagen:** Zusätzlich zu den Standard-PDF-Formularen können Sie jetzt auch Ihre vorhandenen XFA-basierten Formulare im HTML5-Format rendern. Diese Funktion ermöglicht Ihnen, Ihre Clientplattform auf Mobilgeräte (Apple iPad, Android-Tablets und -Smartphones usw.) auszuweiten, die HTML5 unterstützen und Adobe Reader mit XFA-Formularen nicht unterstützen. Weitere Informationen zum HTML5-basierten Rendering finden Sie unter [Einführung in HTML5-Formulare](/help/forms/introductionhtml5.md).

* **Verwaltung von Formularen:** AEM bietet außerdem neue Funktionen, um das Organisieren und Verwalten von Formularen zu vereinfachen. Sie können Formulare aktivieren, deaktivieren, veröffentlichen und in der Vorschau anzeigen.<!--For more information, see [Introduction to managing forms](/help/forms/using/introduction-managing-forms.md).-->

## Konfigurieren der Umgebung für HTML5 Forms {#installing-html-forms}

Führen Sie die folgenden Schritte aus, um die Formularübermittlung und das ordnungsgemäße Rendern von HTML5 Forms zu aktivieren:

* **Dispatcher-Filter hinzufügen:** Aktualisieren Sie Ihre `src/conf.dispatcher.d/filters/filters.any`, um die erforderlichen Anfragen für HTML5 Forms zuzulassen. Fügen Sie die folgenden Filterregeln hinzu:

  ```
  /0103 { /type "allow" /method '(HEAD|POST)' /url "/content/xfaforms/profiles/default.submit.html" }  # allow POSTs to form selectors under content
  /0104 { /type "allow" /method '(GET|HEAD|POST)' /url "/*.xdp.html" }
  ```

* **Paket zur Übermittlung hinzufügen:** Fügen Sie in Ihrem Projekt ein Paket im Ordner &quot;`src/main/content/jcr_root/content`&quot; hinzu, um die Formularübermittlungsfunktion zu unterstützen.

* **HTML5 Forms importieren:** Importieren Sie Ihre Formulare aus Ihrem lokalen Dateisystem in AEM Forms.
