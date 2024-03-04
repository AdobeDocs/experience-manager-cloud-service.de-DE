---
title: Was sind die Unterschiede zwischen AEM 6.5 Forms und AEM Cloud Services?
description: Vergleichen Sie AEM 6.5 Forms und AEM Cloud Services und lernen Sie die wichtigsten Änderungen kennen, bevor Sie ein Upgrade durchführen oder zu Cloud Service migrieren.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
role: Admin, Developer, User
feature: Adaptive Forms
contentOwner: khsingh
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: ht
source-wordcount: '1317'
ht-degree: 100%

---

# Wesentliche Änderungen für bestehende Adobe Experience Manager 6.5 Forms-Benutzende  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service enthält einige wichtige Änderungen an bestehenden Funktionen im Vergleich zu On-Premise- und [!DNL Adobe-Managed Service]-Umgebungen von Adobe Experience Manager Forms. Die wichtigsten Unterschiede sind im Folgenden aufgeführt:

## Cloud-native Fähigkeiten

* Der Service verfügt über eine Cloud-native Architektur, die eine automatische Skalierung je nach Auslastung ermöglicht, keine Ausfallzeiten für Upgrades, häufige und nachträgliche Einführung neuer Funktionen und Updates sowie Topologien, die für maximale Ausfallsicherheit und Effizienz optimiert sind.

* Der Dienst enthält keine Übermittlungsaktionen, die Daten in Adobe Experience Manager Cloud Service-Instanzen speichern. Dies macht ihn besonders sicher. Über Formulare erfasste Daten werden direkt an konfigurierte Datenspeicher gesendet.

* Darüber hinaus ist ein kostenloses CDN (Content Delivery Network) enthalten, mit dem Sie Formulare schneller bereitstellen und wiedergeben können.


## Aktualisierungen des Entwicklungsablaufs

* Der Dienst bietet ein SDK zum Entwickeln und Testen von benutzerdefiniertem Code in einer lokalen Umgebung (auf einem lokalen Computer), bevor der Code auf einem Cloud Service bereitgestellt wird. Entwicklungspersonen entwickeln und testen benutzerdefinierte Komponenten, Designs, Workflows, Anwendungen, Konfigurationen, Vorlagen und mehr mithilfe des SDK auf ihren lokalen Computern. Nach dem Testen des benutzerspezifischen Codes in der lokalen Entwicklungsumgebung stellen sie den benutzerspezifischen Code in einer [Entwicklungs- oder Staging-Umgebung von Forms CS](/help/implementing/cloud-manager/deploy-code.md) bereit, um ihn weiter zu testen, bevor sie ihn in eine Produktionsumgebung übertragen.

* Entwicklerinnen und Entwickler verwalten Code für die Cloud Service- und lokale Entwicklungsumgebung in einem gemeinsamen [Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html?lang=de). Ein auf dem AEM-Archetyp basierendes Git-Repository wird bei der Erstellung eines AEM as a Cloud Service-Programms automatisch erstellt.

  ![Automatische Erstellung des Git-Repositorys in einem AEM as a Cloud Service-Programm](/help/forms/assets/git-repo-local-and-forms-cs.png)

* Der Entwicklungsablauf für Forms as a Cloud Service wird am AEM-Archetyp für AEM Cloud Service ausgerichtet. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von Inhalt und Code in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu berücksichtigen. Verwenden Sie das Tool [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=de), um bestehende Projektpakete neu zu strukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden. So gewährleisten Sie die Kompatibilität der Pakete mit der Projektstruktur, die für Adobe Experience Manager as a Cloud Service definiert wurde.

* Kompilieren Sie vor der Verwendung Ihrer Kundenpakete mit Forms as a Cloud Service Ihren benutzerdefinierten Code erneut mit der neuesten Version von adobe-aemfd-docmanager.

* Verwenden Sie das Migrationsdienstprogramm [AEM Forms as a Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md), um Ihre adaptiven Formulare, Designs, Vorlagen und Cloud-Konfigurationen von <!-- AEM 6.3 Forms--> AEM 6.4 Forms auf OSGi und AEM 6.5 Forms auf OSGi zu [!DNL AEM] as a Cloud Service vorzubereiten und zu migrieren. Verwenden Sie das [Git-Repository Ihres Programms](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md), um vorhandene Vorlagen für adaptive Formulare zu importieren.

* E-Mail unterstützt standardmäßig nur HTTP- und HTTPS-Protokolle. [Kontaktieren Sie das Supportteam](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email), um Ports für den Versand von E-Mails und das SMTP-Protokoll für Ihre Umgebung zu aktivieren.

## Lokalisierung

* Die URL-Konvention von lokalisierten adaptiven Formularen unterstützt nun die Angabe eines Gebietsschemas in der URL. Die URL-Konvention ermöglicht das Caching lokalisierter Formulare in einem Dispatcher oder CDN. Verwenden Sie in einer Cloud Service-Umgebung das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html`, um eine lokalisierte Version eines adaptiven Formulars anstelle von `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>` anzufordern.

* Adobe empfiehlt die Verwendung von Dispatcher- oder CDN-Caching. Auf diese Weise wird das Rendern vorausgefüllter Formulare beschleunigt.


## Adaptive Formulare

* **Regeleditor**: AEM Forms as a Cloud Service bietet einen strengeren [Regeleditor](rule-editor.md#visual-rule-editor). Der Code-Editor ist in Forms as a Cloud Service nicht verfügbar.

  Das [Migrationsdienstprogramm](/help/forms/migrate-to-forms-as-a-cloud-service.md) hilft Ihnen bei der Migration Ihrer Formulare mit benutzerdefinierten Regeln (die im Code-Editor erstellt wurden). Das Dienstprogramm konvertiert solche Regeln in benutzerdefinierte Funktionen, die von Forms as a Cloud Service unterstützt werden. Sie können die wiederverwendbaren Funktionen mit dem Regeleditor verwenden, um weiterhin Ergebnisse zu erhalten, die mit Regelskripten erzielt wurden. Die Funktionen `onSubmitError` oder `onSubmitSuccess` sind jetzt als Aktionen im Regeleditor verfügbar.

<!--* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server.-->

* **Vorbefüllungsdienst:** Der Vorbefüllungs-Dienst ruft Daten vom Server ab und führt Zusammenführungen durch, um die adaptiven Formulare auf der Client-Seite vorab auszufüllen. Der Zeitaufwand für das Vorbefüllen eines adaptiven Formulars wird dadurch verringert. Sie können den [Vorbefüllungsdienst](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/adaptive-forms/prefill-service-adaptive-forms-article-use.html?lang=de) immer so konfigurieren, dass die Zusammenführungsaktion auf dem Formular-Server von Adobe Experience Manager ausgeführt wird.

* **Übermittlungsaktionen**: Die **E-Mail**-Übermittlungsaktion bietet Optionen zum Senden von Anhängen und zum Anhängen von Datensatzdokumenten (Document of Record, DoR) per E-Mail. Sie können sie anstelle der Aktion **E-Mail als PDF** verwenden, die in AEM 6.5 Forms verfügbar ist.

* **Dienst für die automatische Formularkonvertierung**: Der Dienst stellt kein Metamodell für den Dienst für die automatische Formularkonvertierung bereit. Sie können dieses [aus der Dokumentation zum Dienst für die automatische Formularkonvertierung herunterladen](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de#default-meta-model).

* **XSD-basierte adaptive Formulare**: Sie können eine XDP-Vorlage verwenden, um eine Vorlage für das Datensatzdokument zu entwerfen. Der Dienst unterstützt keine XFA-basierten adaptiven Formulare

* **Komponenten**: Der Dienst unterstützt keinen formularinternen Unterzeichnungsvorgang und enthält nicht die Zusammenfassungs- und Überprüfungskomponenten für adaptive Formulare.

* **Assistent-Benutzeroberfläche:** Sie können die [Assistent-Benutzeroberfläche](/help/forms/creating-adaptive-form-core-components.md) verwenden, um die allgemeinen Optionen schnell zu konfigurieren und einfach ein adaptives Formular zu erstellen.

## Formularportal

* Der Dienst speichert keine Metadaten für Entwürfe und übermittelte adaptive Formulare.

## Dokumentendienste:

Forms as a Cloud Service stellt RESTful-APIs für die Dokumenterstellung und Dokumentbearbeitung bereit. Sie können diese APIs verwenden, um Dokumente nach Bedarf oder stapelweise zu generieren oder zu bearbeiten:

* **Dokumentendienste: APIs zur Dokumenterstellung (Ausgabe-Service)**: In einem einzelnen API-Aufruf oder Batch können Sie nur eine Vorlage mit mehreren DATA XML-Dateien verwenden. Die Verwendung mehrerer Vorlagen mit mehreren Datendateien in einem einzelnen API-Aufruf wird nicht unterstützt.

* **APIs zur Dokumentbearbeitung (Assembler-Dienst)**:

   * Vorgänge, die auf Dokumentendiensten oder Anwendungen basieren, sind nicht verfügbar. Zum Beispiel werden Formulare für Microsoft® Word zu PDF, Microsoft® Excel zu PDF, HTML zu PDF, PostScript (PS) zu PDF, XDP zu PDF nicht unterstützt. Diese Vorgänge sind auf Microsoft® Office, Adobe Acrobat, Adobe Distiller bzw. Forms Document Service angewiesen.

   * Konvertieren Sie Dokumente, die nicht im PDF-Format vorliegen, in ein PDF-Format, bevor Sie sie mit den APIs für die Dokumentbearbeitung in der Kommunikation verwenden.  Wenn sich Ihre Dokumente beispielsweise im Format Microsoft® Office, HTML, PostScript (PS) oder XDP befinden, konvertieren Sie diese Dokumente ins PDF-Format, bevor Sie sie mit PDF-Dokumenten verwenden. Für solche Konvertierungen können Sie den Dienst [ConvertPDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html?lang=de) verwenden.

   * Sie können eine AEM 6.5 Forms-Umgebung für die folgenden Dienste verwenden: Digitale Signatur, Verschlüsselung, Reader Extension, An Drucker senden, PDF konvertieren und Barcode-Formulare.


## Datenintegration (Formulardatenmodell)

* Der Dienst unterstützt auch JDBC-Connector, Microsoft® Dynamics, SalesForce, SOAP-basierte Web-Dienste und Dienste, die OData unterstützen.

* Sie können auch AEM-Benutzerprofile verbinden, um Benutzerinformationen abzurufen und zu aktualisieren.

* Das Formulardatenmodell unterstützt nur HTTP- und HTTPS-Endpunkte zum Senden von Daten. Der Dienst unterstützt keine gegenseitige SSL-Authentifizierung für REST-Connector und keine X.509-zertifikatbasierte Authentifizierung für SOAP-Datenquellen.

* Forms as a Cloud Service ermöglicht die Verwendung von Microsoft® Azure Blob, Microsoft® Sharepoint, Microsoft® OneDrive und Diensten, die allgemeine CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) als Datenspeicher unterstützen. Sowohl die OpenAPI-Spezifikation 2.0 als auch die OpenAPI-Spezifikation 3.0 werden unterstützt.


## Elektronische Signatur

* Der Dienst bietet eine OOTB-Integration mit Adobe Sign und unterstützt DocuSign für E-Signaturen.

* Der Dienst unterstützt auch Adobe Sign-Rollen. Sie können die Rollen im Editor für adaptive Formulare für Business-Anwenderinnen und -Anwender konfigurieren, um die Signatur-Workflows einfach zu gestalten.


## HTML5-Formulare

* Sie können eine AEM 6.5 Forms-Umgebung verwenden, um:

   * Ihre XDP-basierten Formulare als HTML5 Formulare zu rendern. Der Service unterstützt keine HTML5-Formulare.

   * Daten offline zu erfassen und zu synchronisieren, wenn Sie das nächste Mal mit der [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html?lang=de)-App online gehen.

## Interaktive Kommunikation

* Sie können Kommunikations-APIs verwenden, um personalisierte Dokumente nach Bedarf oder stapelweise auf Forms as a Cloud Service zu erstellen. Sie können eine AEM 6.5 Forms-Umgebung für Anwendungsfälle der interaktiven Kommunikation und der Agenten-Benutzeroberfläche verwenden.

## Siehe auch

* [Migrieren von AEM Forms (On-Premise- und AMS-Umgebungen) zu AEM Forms as a Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [Hinzufügen oder Erstellen eines adaptiven Formulars zu einer AEM Sites-Seite](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/creating-adaptive-form-core-components.md)
* [Einführung in AEM Forms as a Cloud Service](/help/forms/home.md)
* [Einrichten einer lokalen Entwicklungsumgebung und eines ersten Entwicklungsprojekts](/help/forms/setup-local-development-environment.md)


<!--

## Additional Information

* [Introduction to AEM Forms as a Cloud Service](/help/forms/home.md)
* [Set up a local development environment and initial development project](/help/forms/setup-local-development-environment.md)

-->
