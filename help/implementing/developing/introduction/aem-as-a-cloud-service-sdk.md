---
title: AEM as a Cloud Service-SDK
description: Überblick über das AEM as a Cloud Service Software Development Kit
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 38%

---

# Das AEM as a Cloud Service-SDK {#aem-as-a-cloud-service-sdk}

Das AEM as a Cloud Service SDK besteht aus den folgenden Artefakten:

* **Schnellstart-JAR**: die für die lokale Entwicklung verwendete AEM-Laufzeit.
* **Java™ API-JAR** - Die Java™-JAR/Maven-Abhängigkeit, die alle zulässigen Java™-APIs verfügbar macht, die für die Entwicklung mit AEM as a Cloud Service APIs verwendet werden können. Zuvor als Uberjar bezeichnet.
* **Javadoc Jar** - Die Javadocs für das Java™ API-JAR
* **Dispatcher Tools**: der Satz von Tools, die der lokalen Entwicklung mit Dispatcher dienen. Separate Artefakte für UNIX® und Windows

Darüber hinaus verwenden einige Kunden, die zuvor mit AEM 6.5 oder früheren Versionen bereitgestellt wurden, die folgenden Artefakte. Wenn die lokale Kompilierung mit der Schnellstart-JAR-Datei nicht funktioniert und Sie vermuten, dass sie aus dem Entfernen von Schnittstellen aus AEM bereitgestellten as a Cloud Service Version stammt, wenden Sie sich an den Support. Sie können bestimmen, ob Sie Zugriff benötigen. Dies erfordert Änderungen im Backend.

* **6.5 Veraltetes Java™ API-JAR** - eine zusätzliche Schnittmenge, die seit AEM 6.5 entfernt wurde
* **6.5 Veraltetes Javadoc-JAR**: die Javadocs für den zusätzlichen Satz an Schnittstellen.

## Erstellen für das SDK {#building-for-the-sdk}

Das AEM as a Cloud Service-SDK wird zum Erstellen und Bereitstellen von benutzerdefiniertem Code verwendet. Weitere Informationen finden Sie in der [Dokumentation zum AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=de). Im Allgemeinen werden die folgenden Schritte ausgeführt:

* **Kompilieren von Code**. Wie erwartet, wird der Quell-Code kompiliert, wodurch die resultierenden Inhaltspakete erzeugt werden.
* **Erstellen von Artefakten**. Während dieses Prozesses werden Artefakte erstellt.
* **Analysieren von Bundles**. Bundles werden mithilfe des Maven-Analyzer-Plug-ins analysiert, das nach Problemen im Maven-Projekt sucht, z. B. fehlende Abhängigkeiten.
* **Bereitstellen von Artefakten**. Auf dem lokalen Server werden Artefakte bereitgestellt.

Die gleichen Schritte werden von Cloud Manager bei der Bereitstellung in Cloud-Umgebung ausgeführt. Lokale Builds ermöglichen lokale Entwicklung und Tests. Entwickler können effizient Code- oder Strukturprobleme erkennen, bevor sie sich zur Quellcodeverwaltung verpflichten und Cloud Manager-Implementierungen auslösen. Dies kann länger dauern.

## Zugriff auf das AEM as a Cloud Service-SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* Sie können das Symbol **Über Adobe Experience Manager** der AEM Admin Console prüfen, um die Version von AEM zu ermitteln, die Sie in der Produktionsumgebung ausführen.
* Das Schnellstart-JAR und die Dispatcher Tools können als ZIP-Datei aus dem [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) heruntergeladen werden. Der Zugriff auf die SDK-Listen ist auf Personen beschränkt, die Umgebungen in AEM Managed Services oder AEM as a Cloud Service haben.
* Das Java™ API-JAR und das Javadoc-JAR können über Maven-Tools heruntergeladen werden, entweder über die Befehlszeile oder mit Ihrer bevorzugten IDE.
* Die Maven-Projekt-POMs sollten auf das folgende API-JAR-Paket verweisen. Auch auf die Abhängigkeit von Unterpaketen sollte verwiesen werden.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version>
  <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Der Versionseintrag für das SDK muss mit der Version von AEM as a Cloud Service übereinstimmen. Sie können sehen, welche Version Sie verwenden, indem Sie sich bei AEM anmelden. Markieren Sie oben rechts im Bildschirm das Fragezeichen und wählen Sie **[!UICONTROL Über Adobe Experience Manager]**.


## Aktualisieren eines lokalen Projekts mit einer neuen SDK-Version {#refreshing-a-local-project-with-a-new-skd-version}

Wann sollte das lokale Projekt mit einem neuen SDK aktualisiert werden?

Adobe *empfiehlt* Aktualisierung nach einer monatlichen Wartungsversion.

Es ist *optional*, nach jeder täglichen Wartungsversion zu aktualisieren. Kunden werden darüber informiert, wenn ihre Produktionsinstanz erfolgreich auf eine neue AEM aktualisiert wurde. Bei den täglichen Wartungsversionen ist nicht zu erwarten, dass sich das neue SDK erheblich geändert hat, wenn überhaupt. Es wird dennoch empfohlen, die lokale AEM-Entwicklungsumgebung gelegentlich mit dem neuesten SDK zu aktualisieren und benutzerspezifische Programme neu zu erstellen und zu testen. Die monatliche Wartungsversion umfasst in der Regel wirkungsvollere Änderungen, sodass Entwickler sofort aktualisieren, neu erstellen und testen sollten.

Nachfolgend finden Sie die empfohlene Vorgehensweise zum Aktualisieren einer lokalen Umgebung:

1. Vergewissern Sie sich, dass alle nützlichen Inhalte entweder in die Quell-Code-Verwaltung für das Projekt übertragen wurden oder in einem veränderlichen Inhaltspaket für den späteren Import verfügbar sind..
1. Lokale Entwicklungstestinhalte müssen separat gespeichert werden, damit sie nicht im Rahmen des Cloud Manager-Pipeline-Builds bereitgestellt werden. Der Grund dafür ist, dass sie nur für die lokale Entwicklung verwendet wird.
1. Beenden Sie den derzeit ausgeführten Schnellstart.
1. Verschieben Sie die `crx-quickstart` in einen anderen Ordner, um ihn sicher zu halten.
1. Beachten Sie die neue AEM-Version, die in Cloud Manager vermerkt ist (sie wird verwendet, um die neue Schnellstart-JAR-Version zu identifizieren, die weiter heruntergeladen werden kann).
1. Laden Sie die Schnellstart-JAR-Datei herunter, deren Version mit der Produktions-AEM-Version übereinstimmt.
1. Erstellen Sie einen neuen Ordner und fügen Sie das neue Schnellstartjar hinzu.
1. Starten Sie den neuen Schnellstart mit den gewünschten Ausführungsmodi (entweder durch Umbenennen der Datei oder Übergabe der Ausführungsmodi über `-r`).
   * Sorgen Sie dafür, dass keine Reste des alten Schnellstarts im Ordner verbleiben.
1. Erstellen Sie das AEM-Programm..
1. Stellen Sie Ihre AEM über Package Manager auf lokalen AEM bereit.
1. Installieren Sie alle Pakete mit veränderlichem Inhalt, die für lokale Umgebungstests über Package Manager erforderlich sind.
1. Fahren Sie mit der Entwicklung fort und stellen Sie die Änderungen nach Bedarf bereit.

Wenn es Inhalte gibt, die mit jeder neuen AEM-Schnellstartversion installiert werden sollen, fügen Sie sie in einem Inhaltspaket und der Quell-Code-Verwaltung des Projekts hinzu. Installieren Sie sie dann jedes Mal.

Sie sollten das SDK häufig aktualisieren (z. B. alle zwei Wochen) und täglich den ganzen lokalen Status verwerfen, um im Programm nicht versehentlich von Stateful-Daten abzuhängen.

Wenn Sie von CryptoSupport abhängig sind ([entweder durch Konfiguration der Anmeldeinformationen von Cloud Services oder des SMTP-Mail-Dienstes in AEM oder durch Verwendung der CryptoSupport-API in Ihrer Anwendung](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), werden die verschlüsselten Eigenschaften durch einen Schlüssel verschlüsselt. Dieser Schlüssel wird beim ersten Start einer AEM automatisch generiert. Während das Cloud-Setup dafür sorgt, dass der umgebungsspezifische CryptoKey automatisch wiederverwendet wird, muss der CryptoKey in die lokale Entwicklungsumgebung injiziert werden.

Standardmäßig ist AEM so konfiguriert, dass die Schlüsseldaten im Datenordner eines Ordners gespeichert werden. Aus Gründen einer einfacheren Wiederverwendung in der Entwicklung kann der AEM beim ersten Start mit &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Dieser Prozess generiert die Verschlüsselungsdaten unter &quot;`/etc/key`&quot;.

Gehen Sie wie folgt vor, um Inhaltspakete, die die verschlüsselten Werte enthalten, wiederverwenden zu können:

* Wenn Sie die lokale Datei „quickstart.jar“ erstmals starten, müssen Sie den folgenden Parameter hinzufügen: „`-Dcom.adobe.granite.crypto.file.disable=true`“. Es ist optional, wird jedoch empfohlen, den Parameter immer hinzuzufügen.
* Erstellen Sie beim ersten Starten einer Instanz ein Paket, das einen Filter für den Stammordner enthält.`/etc/key`&quot;. Dieses Paket enthält das Geheimnis, das in allen Umgebungen wiederverwendet werden soll, in denen sie wiederverwendet werden sollen.
* Exportieren Sie alle veränderlichen Inhalte, die Geheimnisse enthalten, oder suchen Sie die verschlüsselten Werte mithilfe von `/crx/de` sodass Sie ihn zum Paket hinzufügen können, das über verschiedene Installationen hinweg wiederverwendet wird.
* Installieren Sie jedes Mal, wenn Sie eine neue Instanz starten (entweder um sie durch eine neue Version zu ersetzen oder weil mehrere Entwicklungsumgebungen die Anmeldeinformationen zum Testen gemeinsam nutzen sollten), das in den Schritten 2 und 3 erstellte Paket. Auf diese Weise können Sie den Inhalt wiederverwenden, ohne dass eine manuelle Neukonfiguration erforderlich ist. Der Grund dafür ist, dass der Kryptoschlüssel jetzt synchronisiert ist.
