---
title: Erstellen eines benutzerdefinierten Profils für HTML5-Formulare
description: Ein HTML5-Formularprofil ist ein Ressourcenknoten in Apache Sling. Es enthält eine benutzerdefinierte Version von HTML5-Formular-Render-Diensten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 9cd22244-9aa6-4b5f-96cf-c9cb3d6f9c8a
feature: HTML5 Forms,Mobile Forms
exl-id: cf86c810-c466-4894-acc2-d4faf49754cc
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 96%

---

# Erstellen eines benutzerdefinierten Profils für HTML5-Formulare {#creating-a-custom-profile-for-html-forms}

<span class="preview"> Die HTML5 Forms-Funktion wird als Teil des Early Access-Programms angeboten. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (geschäftlichen) E-Mail-ID an aem-forms-ea@adobe.com.
</span>

Ein Profil ist ein Ressourcenknoten in [Apache Sling](https://sling.apache.org/). Es enthält eine benutzerdefinierte Version des HTML5-Formularen-Render-Dienstes. Sie können den Render-Service für HTML5-Formulare verwenden, um Erscheinungsbild, Verhalten und Interaktionen von HTML5-Formularen anzupassen. Ein Profilknoten ist im Ordner `/content` im JCR-Repository vorhanden. Sie können den Knoten direkt im Ordner `/content` oder in einem beliebigen Unterordner des Ordners `/content` platzieren.

Der Profilknoten hat die **sling:resourceSuperType**-Eigenschaft und der Standardwert ist **xfaforms/profile**. Das Render-Skript für den Knoten ist unter /libs/xfaforms/profile verfügbar.

Die Sling-Skripte sind JSP-Skripte. Diese JSP-Skripte dienen als Container für die Zusammenstellung der HTML für das angeforderte Formular und der erforderlichen JS-/CSS-Artefakte. Die Sling-Skripte werden auch als **Profil-Renderer-Skripte bezeichnet**. Der Profil-Renderer ruft den Forms-OSGi-Service auf, um das angeforderte Formular zu rendern.

Das Profilskript für GET- und POST-Anfragen befindet sich in „html.jsp“ und „html.POST.jsp“. Sie können eine oder mehrere Dateien kopieren und verändern, um Ihre Anpassungen zu überschreiben. Nehmen Sie keine Änderungen an Ort und Stelle vor, denn die Aktualisierung des Patches überschreibt solche Änderungen.

Ein Profil enthält verschiedenen Module. Die Module sind formRuntime.jsp, config.jsp, toolbar.jsp, formBody.jsp, nav_footer.jsp und footer.jsp.

## formRuntime.jsp {#formruntime-jsp-br}

Die „formRuntime.jsp“-Module enthalten Verweise auf die Client-Bibliotheken. Sie stellen außerdem Methoden dar, um Gebietsschema-Informationen von einer Anforderung zu extrahieren und lokalisierte Nachrichten in die Anforderung einzufügen. Sie können eigene benutzerdefinierte JavaScript-Bibliotheken oder Stile in „formRuntime.jsp“ einfügen.

## config.jsp {#config-jsp}

Das Modul config.jsp enthält verschiedene Konfigurationen wie Protokollierung, Proxy-Dienste und Verhaltensversion. Sie können Ihre eigene Konfiguration und Widget-Anpassung zum Modul config.jsp hinzufügen. Sie können auch Konfigurationen wie beispielsweise benutzerdefinierte Widget-Registrierung zum „config.jsp“-Modul hinzufügen.

## toolbar.jsp {#toolbar-jsp}

Die Datei „toolbar.jsp“ enthält den Code zur Erstellung von farbigen Symbolleisten. Um die Symbolleiste zu entfernen, müssen Sie toolbar.jsp aus html.jsp entfernen.

## formBody.jsp {#formbody-jsp}

Das Modul „formBody.jsp“ dient zur HTML-Darstellung des XFA-Formulars.

## nav_footer.jsp {#nav-footer-jsp}

Zunächst rendert das HTML5-Formular nur die erste Seite des Formulars. Wenn jemand durch das Formular blättert, wird der Rest der Formulare geladen. Dadurch wird der Ladevorgang verkürzt. Die Komponente „nav_footer.jsp“ enthält alle Stile und erforderlichen Elemente, um das schrittweise Laden der Seiten beim Scrollen zu erleichtern.

## footer.jsp {#footer-jsp}

Das Modul footer.jsp ist leer. Damit können Sie Skripte hinzufügen, die nur für die Benutzerinteraktion verwendet werden.

## Erstellen von benutzerdefinierten Profilen {#creating-custom-profiles}

Um ein benutzerdefiniertes Profil zu erstellen, führen Sie die folgenden Schritte aus:

### Profilknoten erstellen {#create-profile-node}

1. Navigieren Sie zur CRX DE-Schnittstelle unter der URL `https://'[server]:[port]'/crx/de` und melden Sie sich mit Administratorberechtigungen an.

1. Im linken Fensterbereich navigieren Sie zum Speicherort: */content/xfaforms/profiles*.

1. Kopieren Sie „node default“ und fügen Sie den Knoten in einen anderen Ordner (*/content/profiles*) mit dem Namen *hrform* ein.

1. Wählen Sie den neuen Knoten *hrform* und fügen Sie eine String-Eigenschaft hinzu: *sling:resourceType* mit dem Wert: *hrform/demo*.

1. Klicken Sie im Symbolleistenmenü auf Alle speichern, um die Änderungen zu speichern.

### Erstellen des Profil-Renderer-Skripts {#create-the-profile-renderer-script}

Nachdem Sie ein benutzerdefiniertes Profil erstellt haben, fügen Sie Render-Informationen zu diesem Profil hinzu. Nach Erhalt einer Anfrage für das neue Profil prüft CRX das Vorhandensein des Ordners „/apps“, damit die JSP-Seite gerendert werden kann. Erstellen Sie die JSP-Seite im Ordner „/apps“.

1. Navigieren Sie im linken Fensterbereich zum Ordner `/apps`.
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/apps` und wählen Sie die Erstellung eines Ordners mit dem Namen **hrform**.
1. Erstellen Sie innerhalb des Ordners **hrform** einen Ordner namens **demo**.
1. Klicken Sie auf die Schaltfläche **Alle speichern**.
1. Navigieren Sie zu `/libs/xfaforms/profile/html.jsp` und kopieren Sie den Knoten **html.jsp**.
1. Fügen Sie den Knoten **html.jsp** in den oben erstellten Ordner `/apps/hrform/demo` mit demselben Namen **html.jsp** ein und klicken Sie auf **Speichern**.
1. Wenn Sie andere Profil-Skript-Komponenten haben, führen Sie die Schritte 1-6 aus, um die Komponenten in den Ordner „/apps/hrform/demo“ zu kopieren.

1. Um zu überprüfen, dass das Profil erstellt wurde, rufen Sie die URL `https://'[server]:[port]'/content/xfaforms/profiles/hrform.html` auf.

Um Ihre Formulare zu überprüfen,**Importieren Sie Ihre Formulare** aus Ihrem lokalen Dateisystem in AEM Forms und[ zeigen Sie eine Vorschau des Formulars](/help/forms/previewing-forms.md) in der Autoreninstanz des AEM-Servers an.
