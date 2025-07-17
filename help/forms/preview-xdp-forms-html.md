---
title: Generieren einer HTML5-Vorschau eines XDP-Formulars
description: Auf der Registerkarte für die HTML-Vorschau in LiveCycle Designer können Sie das Formular so darstellen, wie es in einem Browser angezeigt würde.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 548f302b-57f0-4bdc-8a99-1a4967caa32f
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 96%

---

# Generieren einer HTML5-Vorschau eines XDP-Formulars{#generate-html-preview-of-an-xdp-form}

<span class="preview"> Die HTML5 Forms-Funktion wird als Teil des Early Access-Programms angeboten. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (geschäftlichen) E-Mail-ID an aem-forms-ea@adobe.com.
</span>

Beim Erstellen eines Formulars in AEM Forms Designer können Sie nicht nur die PDF-Ausgabedarstellung eines Formulars, sondern auch eine HTML5-Ausgabedarstellung davon in der Vorschau anzeigen. Sie können die Registerkarte **HTML-Vorschau** verwenden, um ein Formular so wie in einem Browser anzuzeigen.

## Aktivieren der HTML-Vorschau für XDP-Formulare in Designer {#html-preview-of-forms-in-forms-designer}

Um Designer für die Erstellung einer HTML-Vorschau für XDP-Formulare zu aktivieren, müssen Sie folgende Konfigurationen durchführen:

* Konfigurieren des Apache Sling-Authentifizierungsdienstes 
* Abgesicherten Modus deaktivieren
* Details zum AEM Forms-Server bereitstellen

### Apache Sling Authentifizierungsdienst konfigurieren  {#configure-apache-sling-authentication-service}

1. Navigieren Sie zu `https://'[server]:[port]'/system/console/configMgr` in AEM Forms, wenn es unter OSGi ausgeführt wird oder
   `https://'[server]:[port]'/lc/system/console/configMgr` in AEM Forms, wenn es unter JEE ausgeführt wird.
1. Wählen Sie die Konfiguration **Apache Sling-Authentifizierungsdienst**, um ihn im Modus „Bearbeiten“ zu öffnen.

1. Je nachdem, ob Sie AEM Forms unter OSGi oder JEE ausführen, müssen Sie Folgendes im Feld **Authentifizierungsanforderungen** hinzufügen: 

   *  von AEM Forms für JEE

      * -/content/xfaforms
      * -/etc/clientlibs

   * AEM Forms on OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >Kopieren Sie nicht den angegebenen Wert in das Feld „Authentifizierungsanforderungen“, da dies die Sonderzeichen im Wert beschädigen kann. Geben Sie die stattdessen den spezifizierten Wert in das Feld ein.

1. Geben Sie einen Benutzernamen und ein Kennwort für **[!UICONTROL Anonymer Benutzername]** und **[!UICONTROL Anonymes Benutzerkennwort]** ein. Die angegebenen Anmeldeinformationen werden verwendet, um die anonyme Authentifizierung zu nutzen und Zugriff auf anonyme Benutzende zuzulassen.
1. Klicken Sie auf **Speichern**, um die Konfiguration zu speichern.

### Deaktivieren des abgesicherten Modus {#disable-protected-mode}

Der **abgesicherte Modus** ist standardmäßig aktiviert. Behalten Sie dies in Produktionsumgebungen bei. Sie können den Modus in Entwicklungsumgebungen deaktivieren, um eine HTML5-Vorschau in Designer anzuzeigen. Gehen Sie wie folgt vor, um ihn zu deaktivieren:

1. Melden Sie sich bei der AEM-Web-Konsole als Administrator an.

   * URL für AEM Forms unter OSGi: `https://'[server]:[port]'/system/console/configMgr`
   * URL für AEM Forms unter JEE: `https://'[server]:[port]'/lc/system/console/configMgr`

1. Öffnen Sie **[!UICONTROL Konfigurationen von Mobile-Formularen]** für die Bearbeitung.
1. Deaktivieren Sie die Option **[!UICONTROL Abgesicherter Modus]** und klicken Sie auf **[!UICONTROL Speichern]**. 

### Angeben von Details zum AEM Forms-Server {#provide-details-of-aem-forms-server}

1. Navigieren Sie in Designer zu **Werkzeuge** > **Optionen**.
1. Wählen Sie im Fenster „Optionen“ die Seite **Serveroptionen**, stellen Sie die folgenden Details bereit und klicken Sie auf **OK**.

   * **Server URL**: AEM Forms-Server URL.

   * **HTTP-Port-Nummer**: AEM-Server-Port. Der Standardwert ist 4502.
   * **HTML-Vorschaukontext:** Pfad des Profils, der für die Wiedergabe der XFA-Formulare verwendet wird. Die folgenden Standardprofile werden verwendet, um das Formular in Designer in der Vorschau anzuzeigen. Sie können außerdem den Pfad zu einem benutzerdefinierten Profil angeben.

      * `/content/xfaforms/profiles/default.html` (AEM Forms on OSGi)

      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms on JEE)

   * **Forms Manager-Kontext:** Kontextpfad, an dem die Forms Manager-Benutzeroberfläche bereitgestellt wird. Die Standardwerte lauten:

      * `/aem/forms` (AEM Forms on OSGi)
      * `/lc/forms` (AEM Forms on JEE)

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der AEM Forms-Server läuft. Die HTML-Vorschau stellt eine Verbindung zum CRX-Server her, um eine Vorschau zu *erzeugen*.

   ![AEM Forms Designer-Optionen ](assets/server_options.png)

   AEM Forms Designer-Optionen

1. Um ein Formular in HTML in der Vorschau anzuzeigen, klicken Sie auf die Registerkarte **HTML-Vorschau**.

   >[!NOTE]
   >
   >
   >
   >
   >    * Wenn die Registerkarte für die HTML-Vorschau geschlossen ist, drücken Sie F4, um sie zu öffnen. Sie können die HTML-Vorschau auch über das Menü „Ansicht“ wählen, um die betreffende Registerkarte zu öffnen.
   >    * Die HTML-Vorschau unterstützt keine PDF-Dokumente. Die HTML-Vorschau ist nur für XDP-Dokumente vorgesehen.
   >
   >

   >[!CAUTION]
   >
   >Um das tatsächliche Benutzererlebnis zu testen, sollten Sie Ihre Formulare auch in externen Browsern (Google Chrome, Microsoft Edge, Mozilla Firefox usw.) ausprobieren. Jeder Browser verwendet eine andere Engine zum Rendern von HTML, sodass es einige Unterschiede in der Vorschau eines Formulars in Designer und einem externen Browser geben kann.

## Anzeigen einer Vorschau eines Formulars mit Beispieldaten {#to-preview-a-form-using-sample-data}

In Designer können Sie das Formular mithilfe von XML-Beispieldaten in der Vorschau anzeigen und testen. Es wird empfohlen, das Formular häufig mit Beispieldaten zu testen, um sicherzustellen, dass es korrekt wiedergegeben wird.

Falls Ihnen keine Beispieldaten vorliegen, können Sie welche von Designer erstellen lassen oder auch selbst erstellen. (Siehe [So generieren Sie automatisch Beispieldaten für die Vorschau eines Formulars](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) und [So erstellen Sie Beispieldaten für die Vorschau eines Formulars](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2))

Durch das Testen Ihres Formulars mit einer Beispieldatenquelle wird sichergestellt, dass die Daten und Felder zugeordnet werden und sich wiederholende Teilformulare erwartungsgemäß wiederholt werden. Sie können ein ausgeglichenes Formular-Layout erstellen, das für jedes Objekt den geeigneten Platz zur Anzeige der zusammengeführten Daten bietet.

1. Wählen Sie **Datei > Formulareigenschaften**.

1. Klicken Sie auf die Registerkarte **Vorschau** und geben Sie im Feld „Datendatei“ den vollständigen Pfad zu einer Testdatendatei ein. Sie können auch auf die Schaltfläche „Durchsuchen“ klicken, um zur gewünschten Datei zu gelangen.

1. Klicken Sie auf **OK**. Wenn Sie das nächste Mal eine Vorschau des Formulars auf der Registerkarte **HTML-Vorschau** anzeigen, werden die Datenwerte der XML-Musterdatei in den entsprechenden Objekten dargestellt.

## Vorschau von Formularen in einem Repository {#html-preview-of-forms-in-forms-manager}

In AEM Forms können Sie die Formulare und Dokumente eines Repositorys in der Vorschau anzeigen. Die Vorschau zeigt genau, wie die Formulare aussehen und sich verhalten, wenn sie von den Endbenutzenden verwendet werden.
