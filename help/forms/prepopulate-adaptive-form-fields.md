---
title: Vorausfüllen von Feldern in adaptiven Formularen?
description: Verwenden Sie vorhandene Daten, um Felder eines adaptiven Formulars vorab auszufüllen. Benutzende können grundlegende Informationen in einem Formular vorab ausfüllen, indem sie sich mit ihren Social-Media-Profilen anmelden.
topic-tags: develop
feature: Adaptive Forms, Foundation Components
exl-id: e2a87233-a0d5-48f0-b883-915fe56f105f
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '2007'
ht-degree: 100%

---

# Vorbefüllen von Feldern in adaptiven Formularen{#prefill-adaptive-form-fields}

>[!NOTE]
>
> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für die Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben.

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/prepopulate-adaptive-form-fields.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

## Einführung {#introduction}

Sie können die Felder eines adaptiven Formulars mit vorhandenen Daten vorbefüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Um Daten in einem adaptiven Formular vorzubefüllen, stellen Sie die Benutzerdaten als vorbefüllte XML/JSON in dem Format bereit, das der Datenstruktur zum Vorbefüllen von adaptiven Formularen entspricht.

## Struktur der Vorbefüllungsdaten {#the-prefill-structure}

Ein adaptives Formular kann eine Mischung aus gebundenen und ungebundenen Feldern enthalten. Gebundene Felder sind diejenigen, die aus der Registerkarte für die Inhaltssuche gezogen werden und einen nicht leeren Wert für die `bindRef`-Eigenschaft im Dialogfeld zum Bearbeiten von Feldern enthalten. Ungebundene Felder werden direkt aus dem Sidekick gezogen und haben einen leeren `bindRef`-Wert.

Sie können sowohl gebundene als auch ungebundene Felder eines adaptiven Formulars vorbefüllen. Die Vorbefüllungsdaten enthalten die Abschnitte „afBoundData“ und „afUnBoundData“, um sowohl gebundene als auch ungebundene Felder eines adaptiven Formulars vorzubefüllen. Der Abschnitt `afBoundData` enthält die Daten zum Vorbefüllen für gebundene Felder und Bereiche. Diese Daten müssen mit dem verknüpften Formularmodellschema konform sein:

- Bei adaptiven Formularen mit der [XFA-Formularvorlage](#xfa-based-af) muss die XML zum Vorbefüllen mit dem Datenschema der XFA-Vorlage konform sein.
- Bei adaptiven Formularen mit [XML-Schema](#xml-schema-af) muss die XML zum Vorbefüllen mit der XML-Schemastruktur konform sein.
- Bei adaptiven Formularen mit [JSON-Schema](#json-schema-based-adaptive-forms) muss die JSON zum Vorbefüllen mit dem JSON-Schema konform sein.
- Bei adaptiven Formularen mit dem FDM-Schema muss das JSON zum Vorbefüllen mit dem FDM-Schema konform sein.
- Bei adaptiven Formularen [ohne Formularmodell](#adaptive-form-with-no-form-model) gibt es keine gebundenen Daten. Jedes Feld ist ein ungebundenes Feld und wird anhand der ungebundenen XML vorausgefüllt.

### XML-Beispielstruktur zum Vorbefüllen {#sample-prefill-xml-structure}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<afData>
  <afBoundData>
     <employeeData>
        .
     </employeeData>
  </afBoundData>

  <afUnboundData>
    <data>
      <textbox>Hello World</textbox>
         .
         .
      <numericbox>12</numericbox>
         .
         .
    </data>
  </afUnboundData>
</afData>
```

### JSON-Beispielstruktur zum Vorbefüllen {#sample-prefill-json-structure}

```javascript
{
   "afBoundData": {
      "employeeData": { }
   },
   "afUnboundData": {
      "data": {
         "textbox": "Hello World",
         "numericbox": "12"
      }
   }
}
```

Im Fall von gebundenen Feldern mit demselben „bindref“ oder ungebundenen Feldern mit demselben Namen, werden die im XML-Tag oder JSON-Objekt angegebenen Daten in alle Felder eingefügt. Beispiel: Zwei Felder in einem Formular sind dem Namen `textbox` in den Vorbefüllungsdaten zugeordnet. Wenn das erste Feld für das Textfeld „A“ enthält, wird zur Laufzeit im zweiten Textfeld automatisch „A“ ausgefüllt. Diese Verknüpfung wird als Live-Verknüpfung von Feldern adaptiver Formulare bezeichnet.

### Adaptives Formular mit XFA-Formularvorlage {#xfa-based-af}

Die Struktur von XML zum Vorbefüllen und übermittelter XML für XFA-basierte adaptive Formulare ist:

- **XML-Struktur zum Vorbefüllen**: Die XML zum Vorbefüllen für XFA-basierte adaptive Formulare muss mit dem Datenschema der XFA-Formularvorlage konform sein. Um ungebundene Felder vorzubefüllen, umschließen Sie die XML-Struktur zum Vorbefüllen in das Tag `/afData/afBoundData`.

- **Übermittelte XML-Struktur**: Wenn keine XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML Daten für gebundene und ungebundene Felder im `afData`-Wrapper-Tag. Wenn XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML dieselbe Struktur wie die XML zum Vorbefüllen. Wenn die XML zum Vorbefüllen mit dem `afData`-Stamm-Tag beginnt, hat die Ausgabe-XML ebenfalls dasselbe Format. Wenn die XML zum Vorbefüllen den `afData/afBoundData`-Wrapper nicht enthält und stattdessen direkt aus dem Schema-Root-Tag beginnt wie `employeeData`, beginnt die übermittelte XML ebenfalls mit dem `employeeData`-Tag.

Prefill-Submit-Data-ContentPackage.zip

[Datei laden](assets/prefill-submit-data-contentpackage.zip)
Beispiel mit vorbefüllten und übermittelten Daten

### XML-Schemabasierte adaptive Formulare  {#xml-schema-af}

Die Struktur von XML zum Vorbefüllen und von übermittelter XML für adaptive Formulare, die auf XML-Schemas basieren, ist wie folgt:

- **XML-Struktur zum Vorbefüllen**: Die XML zum Vorbefüllen muss mit dem verknüpften XML-Schema konform sein. Um ungebundene Felder vorzubefüllen, umschließen Sie die XML-Struktur zum Vorbefüllen in das Tag „/afData/afBoundData“.
- **Übermittelte XML-Struktur**: Wenn keine XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML Daten für gebundene und ungebundene Felder im `afData`-Wrapper-Tag. Wenn die XML zum Vorbefüllen verwendet wird, enthält die übermittelte XML dieselbe Struktur wie die XML zum Vorbefüllen. Wenn die XML zum Vorbefüllen mit dem `afData`-Stamm-Tag beginnt, hat die Ausgabe-XML dasselbe Format. Wenn die XML zum Vorbefüllen nicht den `afData/afBoundData`-Wrapper aufweist und stattdessen direkt aus dem Schemastamm-Tag beginnt wie `employeeData`, beginnt die übermittelte XML ebenfalls mit dem `employeeData`-Tag.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema targetNamespace="https://adobe.com/sample.xsd"
            xmlns="https://adobe.com/sample.xsd"
            xmlns:xs="https://www.w3.org/2001/XMLSchema">

    <xs:element name="sample" type="SampleType"/>

    <xs:complexType name="SampleType">
        <xs:sequence>
            <xs:element name="noOfProjectsAssigned" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:schema>
```

Bei Feldern, deren Modell das XML-Schema ist, werden die Daten im `afBoundData`-Tag wie im XML-Beispielschema unten dargestellt vorbefüllt. Es kann zum Vorbefüllen eines adaptiven Formulars mit mindestens einem ungebundenen Textfeld verwendet werden.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <textbox>Ignorance is bliss :) </textbox>
    </data>
  </afUnboundData>
  <afBoundData>
    <data>
      <noOfProjectsAssigned>twelve</noOfProjectsAssigned>
    </data>
  </afBoundData>
</afData>
```

>[!NOTE]
>
>Es wird empfohlen, keine ungebundenen Felder in gebundenen Bereichen zu verwenden (Bereiche mit nicht leerem `bindRef`-Wert, der durch Ziehen von Komponenten aus dem Sidekick oder der Registerkarte „Datenquellenr“ erstellt wurde). Dies kann zu Datenverlust bei diesen ungebundenen Feldern führen. Darüber hinaus wird empfohlen, dass die Namen der Felder im gesamten Formular eindeutig sind, insbesondere für ungebundene Felder.

#### Beispiel ohne „afData“- und „afBoundData“-Wrapper {#an-example-without-afdata-and-afbounddata-wrapper}

```xml
<?xml version="1.0" encoding="UTF-8"?><config>
 <assignmentDetails descriptionOfAssignment="Some Science Project" durationOfAssignment="34" financeRelatedProject="1" name="Lisa" numberOfMentees="1"/>
 <assignmentDetails descriptionOfAssignment="Kidding, right?" durationOfAssignment="4" financeRelatedProject="1" name="House" numberOfMentees="3"/>
</config>
```

### JSON-Schemabasierte adaptive Formulare {#json-schema-based-adaptive-forms}

Für adaptive Formulare, die auf dem JSON-Schema basieren, wird im Folgenden die Struktur von JSON zum Vorbefüllen und übermitteltem JSON beschrieben. Weitere Informationen finden Sie unter [Erstellen von adaptiven Formularen mit dem JSON-Schema](adaptive-form-json-schema-form-model.md).

- **Struktur von JSON zum Vorbefüllen**: Das JSON zum Vorbefüllen muss mit dem verknüpften JSON-Schema konform sein. Optional kann es in das „/afData/afBoundData“-Objekt eingeschlossen werden, wenn Sie auch ungebundene Felder vorbefüllen möchten.
- **Übermittelte JSON-Struktur**: Wenn kein JSON zum Vorbefüllen verwendet wird, enthält das übermittelte JSON im „afData-Wrapper“-Tag Daten für gebundene und ungebundene Felder. Wenn das JSON zum Vorbefüllen verwendet wird, enthält das übermittelte JSON dieselbe Struktur wie das JSON zum Vorbefüllen. Wenn das JSON zum Vorbefüllen mit dem „afData“-Stamm-Objekt beginnt, hat das Ausgabe-JSON dasselbe Format. Wenn das JSON zum Vorbefüllen keinen „afData/afBoundData“-Wrapper hat und stattdessen direkt vom Schemastammobjekt startet, z. B. Benutzer, dann startet das übermittelte JSON ebenfalls mit dem Objekt „Benutzer“.

```json
{
  "id": "https://some.site.somewhere/entry-schema#",
  "$schema": "https://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "address": {
      "type": "object",
      "properties": {
        "name": {
          "type": "string"
        },
        "age": {
          "type": "integer"
        }
      }
    }
  }
}
```

Bei Feldern, die das JSON-Schemamodell verwenden, sind die Daten im „afBoundData“-Objekt bereits vorbefüllt, wie im folgenden Beispiel-JSON gezeigt. Es kann zum Vorbefüllen eines adaptiven Formulars mit mindestens einem ungebundenen Textfeld verwendet werden. Im Folgenden finden Sie ein Beispiel für die Daten mit `afData/afBoundData`-Wrapper:

```json
{
  "afData": {
    "afUnboundData": {
      "data": { "textbox": "Ignorance is bliss :) " }
    },
    "afBoundData": {
      "data": { {
   "user": {
    "address": {
     "city": "Noida",
     "country": "India"
}}}}}}}
```

Im Folgenden finden Sie ein Beispiel ohne `afData/afBoundData`-Wrapper:

```json
{
  "user": {
    "address": {
      "city": "Noida",
      "country": "India"
    }
  }
}
```

>[!NOTE]
>
> Die Verwendung von ungebundenen Feldern in gebundenen Bedienfeldern (Bedienfelder mit nicht leerer bindRef, die durch Ziehen von Komponenten aus der Registerkarte „Sidekick“ oder „Datenquellen“ erstellt wurden) wird **nicht** empfohlen, da dies zum Verlust von Daten der ungebundenen Felder führen kann. Es wird empfohlen, eindeutige Feldnamen im gesamten Formular zu verwenden, insbesondere für ungebundene Felder.
>

### Adaptives Formular ohne Formularmodell {#adaptive-form-with-no-form-model}

Bei adaptiven Formularen ohne Formularmodell befinden sich die Daten für alle Felder unter dem `<data>`-Tag von `<afUnboundData> tag`.

Beachten Sie außerdem Folgendes:

Die XML-Tags für die Benutzerdaten, die für verschiedene Felder übermittelt werden, werden mit dem Namen der Felder generiert. Daher müssen die Feldnamen eindeutig sein.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <radiobutton>2</radiobutton>
      <repeatable_panel_no_form_model>
        <numericbox>12</numericbox>
      </repeatable_panel_no_form_model>
      <repeatable_panel_no_form_model>
        <numericbox>21</numericbox>
      </repeatable_panel_no_form_model>
      <checkbox>2</checkbox>
      <textbox>Nopes</textbox>
    </data>
  </afUnboundData>
  <afBoundData/>
</afData>
```

## Konfigurieren des Vorbefüllungs-Services {#configuring-prefill-service-using-configuration-manager}

Verwenden Sie die `alloweddataFileLocations`-Eigenschaft der **Standardkonfiguration für den Vorbefüllungs-Service**, um den Speicherort der Datendateien oder eines Regex (regulärer Ausdruck) für die Datendateispeicherorte festzulegen.

Folgende JSON-Datei zeigt ein Beispiel:

```JSON
  {
  "alloweddataFileLocations": "`file:///C:/Users/public/Document/Prefill/.*`"
  }
```

Um Konfigurationswerte festzulegen [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) in Ihrer Cloud Service-Instanz bereit.

>[!NOTE]
>
> - Standardmäßig wird das Vorbefüllen durch CRX-Dateien für alle Typen adaptiver Formulare ermöglicht (XSD-, XDP-, JSON-, FDM-basierte und nicht formularmodellbasierte). Vorbefüllen ist nur mit JSON- und XML-Dateien zulässig.
> - Das CRX-Protokoll verwaltet die Sicherheit der vorbefüllten Daten, daher ist es standardmäßig zulässig. Beim Vorbefüllen über andere Protokolle mit dem generischen Regex kann es zu Sicherheitslücken kommen. Geben Sie in der Konfiguration eine sichere URL-Konfiguration zum Schutz Ihrer Daten an.

## Die Besonderheit wiederholbarer Bereiche {#the-curious-case-of-repeatable-panels}

Im Allgemeinen werden gebundene (Formularschema) und ungebundene Felder im selben adaptiven Formular erstellt. Im Folgenden werden allerdings einige Ausnahmen genannt, die gelten, falls die gebundenen Bereiche wiederholbar sind:

- Ungebundene wiederholbare Bereiche werden bei adaptiven Formularen mit XFA-Formularvorlage, XSD, JSON- oder FDM-Schema nicht unterstützt.
- Verwenden Sie keine ungebundenen Felder in gebundenen, wiederholbaren Bedienfeldern.

>[!NOTE]
>
> Generell sollten Sie keine gebundenen und ungebundenen Felder mischen, wenn sich diese in Daten überschneiden, die von Benutzenden in ungebundenen Feldern eingegeben werden. Wenn möglich, sollten Sie das XML-Schema oder die XFA-Formularvorlage ändern und einen Eintrag für ungebundene Felder hinzufügen, sodass diese auch gebunden werden und ihre Daten wie andere Felder in den übermittelten Daten verfügbar sind.

## Unterstützte Protokolle zum Vorbefüllen von Benutzerdaten {#supported-protocols-for-prefilling-user-data}

Adaptive Formulare können mit Benutzerdaten im Vorbefüllungsdatenformat über folgende Protokolle vorbefüllt werden, wenn sie mit gültigem Regex konfiguriert sind:

### „crx://“-Protokoll  {#the-crx-protocol}

```javascript
http
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=crx:///tmp/fd/af/myassets/sample.xml
```

Der angegebene Knoten muss die Eigenschaft `jcr:data` aufweisen und die Daten enthalten.

### „file://“-Protokoll  {#the-file-protocol-nbsp}

```javascript
https://`servername`/content/forms/af/someAF.html?wcmmode=disabled&dataRef=file:///C:/Users/form-user/Downloads/somesamplexml.xml
```

Die referenzierte Datei muss sich auf demselben Server befinden.

### „https://“-Protokoll  {#the-http-protocol}

```javascript
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=https://servername/somesamplexmlfile.xml
```

### „service://“-Protokoll  {#the-service-protocol}

```javascript
https://`servername`/content/forms/af/abc.html?wcmmode=disabled&dataRef=service://[SERVICE_NAME]/[IDENTIFIER]
```

- SERVICE_NAME verweist auf den Namen des OSGI-Vorbefüllungs-Service. Weitere Informationen finden Sie unter [Erstellen und Ausführen eines Vorausfüllungsdienstes](prepopulate-adaptive-form-fields.md#create-and-run-a-prefill-service).
- IDENTIFIER bezieht sich auf alle Metadaten, die vom OSGI-Vorbefüllungs-Service erforderlich sind, um die Daten zum Vorbefüllen aufzurufen. Eine Kennung für die angemeldete Benutzerin bzw. den angemeldeten Benutzer ist ein Beispiel für Metadaten, die verwendet werden können.

>[!NOTE]
>
> Die Übergabe von Authentifizierungsparametern wird nicht unterstützt.

### Festlegen des Datenattributs in „slingRequest“ {#setting-data-attribute-in-slingrequest}

Sie können auch das `data`-Attribut in `slingRequest` festlegen, wo das `data`-Attribut eine Zeichenfolge mit XML oder JSON ist, wie in folgendem Beispiel-Code dargestellt (Beispiel ist für XML):

```javascript
<%
           String dataXML="<afData>" +
                            "<afUnboundData>" +
                                "<data>" +
                                    "<first_name>"+ "Tyler" + "</first_name>" +
                                    "<last_name>"+ "Durden " + "</last_name>" +
                                    "<gender>"+ "Male" + "</gender>" +
                                    "<location>"+ "Texas" + "</location>" +
                                    "</data>" +
                            "</afUnboundData>" +
                        "</afData>";
        slingRequest.setAttribute("data", dataXML);
%>
```

Sie können eine einfache XML- oder JSON-Zeichenfolge schreiben, die alle Ihre Daten enthält, und sie in slingRequest festlegen. Sie können dies einfach in der Renderer-JSP für jede Komponente durchführen, die Sie auf der Seite aufnehmen möchten, auf der Sie das „slingRequest“-Datenattribut festlegen können.

Beispiel: Sie wünschen ein spezifisches Design für Ihre Seite mit einem bestimmten Kopfzeilentyp. Um dies zu erreichen, können Sie eine eigene `header.jsp` schreiben, die Sie in Ihre Seitenkomponente aufnehmen, und das `data`-Attribut festlegen.

Ein weiteres gutes Beispiel ist ein Szenario, bei dem Sie Daten bei der Anmeldung über Social Madia-Konten wie Facebook, Twitter oder LinkedIn vorbefüllen möchten. In diesem Fall können Sie eine einfache JSP in `header.jsp` aufnehmen, die Daten aus dem Benutzerkonto abruft und den Datenparameter festlegt.

prefill-page component.zip

[Datei abrufen](assets/prefill-page-component.zip)
Beispieldatei „prefill.jsp“ in der Seitenkomponente

## Benutzerdefinierter Vorbefüllungs-Service von [!DNL AEM Forms]  {#aem-forms-custom-prefill-service}

Sie können den benutzerdefinierten Vorbefüllungs-Service für die Szenarien verwenden, in denen Sie permanent Daten aus einer vordefinierten Quelle lesen. Der Vorbefüllungs-Service liest Daten aus definierten Datenquellen und befüllt die Felder des adaptiven Formulars mit dem Inhalt der Vorbefüllungsdatendatei vor. Außerdem können Sie vorbefüllte Daten dauerhaft mit einem adaptiven Formular verknüpfen.

### Erstellen und Ausführen eines Vorbefüllungs-Service {#create-and-run-a-prefill-service}

Der Vorbefüllungs-Service ist ein OSGi-Service und wird über das OSGi-Paket bereitgestellt. Sie erstellen das OSGi-Bundle, laden es hoch und installieren es in die [!DNL AEM Forms]-Pakete. Bevor Sie mit der Erstellung des Pakets beginnen:

- [Laden Sie das  [!DNL AEM Forms] Client SDK](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) herunter
- Laden Sie das Textbausteinpaket herunter

- Platzieren Sie die Datendatei (Vorbefüllungsdaten) in das CRX-Repository. Sie können die Datei an einem beliebigen Ort in den \contents des CRX-Repositorys platzieren.

[Datei laden](assets/prefill-sumbit-xmlsandcontentpackage.zip)

#### Erstellen eines Vorbefüllungs-Service {#create-a-prefill-service}

Das Textbausteinpaket (Vorbefüllungs-Service-Beispielpaket) enthält folgende Beispielimplementierung des [!DNL AEM Forms]-Vorbefüllungs-Service. Öffnen Sie das Textbausteinpaket in einem Code-Editor. Öffnen Sie beispielsweise das Textbausteinprojekt zur Bearbeitung in Eclipse. Nachdem Sie das Textbausteinpaket in einem Code-Editor geöffnet haben, führen Sie folgende Schritte aus, um den Service zu erstellen.

1. Öffnen Sie die Datei „src\main\java\com\adobe\test\Prefill.java“ zur Bearbeitung.
1. Legen Sie im Code folgenden Wert fest:

   - `nodePath:` Die Knotenpfadvariable, die auf den CRX-Repository-Speicherort verweist, enthält den Pfad der Daten-(Vorbefüllungs)-Datei. Beispiel: /content/prefilldata.xml
   - `label:` Der Parameter „label“ gibt den Anzeigenamen des Service an. Beispiel: Standardvorbefüllungs-Service

1. Speichern und schließen Sie die Datei `Prefill.java`.
1. Fügen Sie das Paket `AEM Forms Client SDK` zum Erstellungspfad des Textbausteinprojektes hinzu.
1. Kompilieren Sie das Projekt und erstellen Sie die .jar-Datei für das Paket.

#### Starten und Verwenden des Vorbefüllungs-Service {#start-and-use-the-prefill-service}

Um den Vorbefüllungs-Service zu starten, laden Sie die JAR-Datei in die [!DNL AEM Forms]-Web-Konsole hoch und aktivieren Sie den Service. Jetzt wird der Service im Editor für adaptive Formulare angezeigt. Verknüpfen eines Vorbefüllungs-Service mit einem adaptiven Formular:

1. Öffnen Sie das adaptive Formular im Forms-Editor und öffnen Sie den Bereich „Eigenschaften“ für den Formularcontainer.
1. In der Eigenschaftenkonsole navigieren Sie zu „[!DNL AEM Forms]-Container“ > „Standard“ > „Vorbefüllungs-Service“.
1. Wählen Sie den Vorbefüllungs-Service und klicken Sie auf **[!UICONTROL Speichern]**. Dieser Service ist mit dem Formular verknüpft.

<!-- ## Prepopulate data at client {#prefill-at-client}

When you prefill an Adaptive Form, the [!DNL AEM Forms] server merges data with an Adaptive Form and delivers the filled form to you. By default, the data merge action takes place at the server.

You can configure the [!DNL AEM Forms] server to perform the data merge action at the client instead of the server. It significantly reduces the time required to prefill and render Adaptive Forms. By default, the feature is disabled. You can enable it from the Configuration Manager or command line.

* To enable or disable from configuration manager:
  1. Open AEM Configuration Manager.
  1. Locate and open the Adaptive Form and Interactive Communication Web Channel Configuration
  1. Enable the Configuration.af.clientside.datamerge.enabled.name option
* To enable or disable from the command line:
  * To enable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=true \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

  * To disable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=false \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

   To take full advantage of the prepopulate data at client option, update your prefill service to return [FileAttachmentMap](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) and [CustomContext](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) -->