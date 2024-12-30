---
title: AEM as a Cloud Service-SDK
description: Überblick über das AEM as a Cloud Service Software Development Kit
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8ccf03ebcb4a96b66a15dc9a1161a857888278a7
workflow-type: tm+mt
source-wordcount: '1256'
ht-degree: 100%

---

# Das AEM as a Cloud Service-SDK {#aem-as-a-cloud-service-sdk}

Das AEM as a Cloud Service-SDK besteht aus den folgenden Artefakten:

* **Schnellstart-JAR**: die für die lokale Entwicklung verwendete AEM-Laufzeit.
* **Java™-API-JAR**: die Java™-JAR-/Maven-Abhängigkeit, die alle zulässigen Java™-APIs verfügbar macht, die zur Entwicklung für AEM as a Cloud Service verwendet werden können. Zuvor als Uberjar bezeichnet.
* **Javadoc-JAR**: die Javadocs für das Java™-API-JAR.
* **Dispatcher Tools**: der Satz von Tools, die der lokalen Entwicklung mit Dispatcher dienen. Separate Artefakte für UNIX® und Windows

Darüber hinaus werden manche Kundinnen und Kunden, die zuvor AEM 6.5 oder frühere Versionen bereitgestellt haben, die unten stehenden Artefakte verwenden. Wenn die lokale Kompilierung mit der Quickstart-JAR nicht funktioniert und Sie vermuten, dass dies auf die Entfernung von Schnittstellen aus AEM zurückzuführen ist, das als Cloud-Service bereitgestellt wird, wenden Sie sich an den Kundensupport. Sie können feststellen, ob Sie Zugang benötigen. Dies erfordert Änderungen im Backend.

* **6.5 Veraltetes Java™-API-JAR**: ein zusätzlicher Satz von Schnittstellen, die seit AEM 6.5 entfernt wurden.
* **6.5 Veraltetes Javadoc-JAR**: die Javadocs für den zusätzlichen Satz an Schnittstellen.

>[!NOTE]
> 
> AEM as a Cloud Service und das SDK unterscheiden sich in verschiedenen Bereichen voneinander. Für Situationen, in denen schnelle und iterative Änderungen erforderlich sind, hat Adobe schnelle Entwicklungsumgebungen (Rapid Development Environments) eingeführt. Weitere Informationen finden Sie unter [Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md).

## Erstellen für das SDK {#building-for-the-sdk}

Das AEM as a Cloud Service-SDK wird zum Erstellen und Bereitstellen von benutzerdefiniertem Code verwendet. Siehe die [Dokumentation zum AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=de). Im Allgemeinen werden die folgenden Schritte ausgeführt:

* **Kompilieren von Code**. Wie erwartet, wird der Quell-Code kompiliert, wodurch die resultierenden Inhaltspakete erzeugt werden.
* **Erstellen von Artefakten**. Während dieses Prozesses werden Artefakte erstellt.
* **Analysieren von Bundles**. Bundles werden mithilfe des Maven-Analyzer-Plug-ins analysiert, das nach Problemen im Maven-Projekt sucht, z. B. fehlende Abhängigkeiten.
* **Bereitstellen von Artefakten**. Auf dem lokalen Server werden Artefakte bereitgestellt.

Die gleichen Schritte werden von Cloud Manager bei der Bereitstellung in Cloud-Umgebung ausgeführt. Die lokale Durchführung von Builds ermöglicht eine lokale Entwicklung und Prüfung. Entwicklerinnen und Entwickler können Code- oder Strukturprobleme effizient erkennen, bevor sie in die Versionskontrolle übernommen werden und Cloud Manager-Bereitstellungen auslösen, die länger dauern können.

>[!NOTE]
>
>Das AEM as a Cloud Service SDK sollte mit einer Distribution und Version von Java erstellt werden, die von der [Build-Umgebung von Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) unterstützt wird. Kundinnen und Kunden von AEM as a Cloud Service können das Oracle-JDK vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) herunterladen und haben erweiterte Unterstützung für Java 11 bis September 2026 durch die Lizenz- und Support-Bedingungen von Adobe für die Oracle Java-Technologie, wenn sie in Adobe Experience Manager-Projekten unterstützt wird.

## Zugriff auf das AEM as a Cloud Service-SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* Sie können das Symbol **Über Adobe Experience Manager** der AEM Admin Console prüfen, um die Version von AEM zu ermitteln, die Sie in der Produktionsumgebung ausführen.
* Das Schnellstart-JAR und die Dispatcher Tools können als ZIP-Datei aus dem [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) heruntergeladen werden. Der Zugriff auf die SDK-Listen ist auf Personen beschränkt, die Umgebungen auf AEM Managed Services oder AEM as a Cloud Service haben.
* Die Java™-API-JAR- und Javadoc-JAR-Pakete können über Maven-Tooling heruntergeladen werden, entweder mit der Befehlszeile oder mit Ihrer bevorzugten IDE.
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
>Der Versionseintrag für das SDK muss mit der Version von AEM as a Cloud Service übereinstimmen. Sie können sehen, welche Version Sie verwenden, indem Sie sich bei AEM anmelden. Klicken Sie oben rechts im Bildschirm auf das Fragezeichen und wählen Sie **[!UICONTROL Über Adobe Experience Manager]**.


## Aktualisieren eines lokalen Projekts mit einer neuen SDK-Version {#refreshing-a-local-project-with-a-new-skd-version}

Wann sollte das lokale Projekt mit einem neuen SDK aktualisiert werden?

Adobe *empfiehlt* die Aktualisierung nach einer monatlichen Wartungsversion.

Es ist *optional*, nach jeder täglichen Wartungsversion zu aktualisieren. Kundinnen und Kunden werden darüber informiert, wenn ihre Produktionsinstanz erfolgreich auf eine neue AEM-Version aktualisiert wurde. Bei den täglichen Wartungsversionen ist nicht zu erwarten, dass sich das neue SDK erheblich verändert hat (wenn überhaupt). Es wird dennoch empfohlen, die lokale AEM-Entwicklungsumgebung gelegentlich mit dem neuesten SDK zu aktualisieren und benutzerspezifische Programme neu zu erstellen und zu testen. Die monatliche Wartungsversion umfasst in der Regel wirkungsvollere Änderungen, sodass Entwicklerinnen und Entwickler umgehend aktualisieren, neu erstellen und testen sollten.

Nachfolgend finden Sie die empfohlene Vorgehensweise zum Aktualisieren einer lokalen Umgebung:

1. Vergewissern Sie sich, dass alle nützlichen Inhalte entweder in die Quell-Code-Verwaltung für das Projekt übertragen wurden oder in einem veränderlichen Inhaltspaket für den späteren Import verfügbar sind.
1. Inhalte lokaler Entwicklungstests müssen separat gespeichert werden, damit sie nicht im Rahmen des Cloud Manager-Pipeline-Build bereitgestellt werden. Der Grund dafür ist, dass sie nur für die lokale Entwicklung verwendet werden.
1. Beenden Sie den derzeit laufenden Schnellstart.
1. Verschieben Sie den Ordner `crx-quickstart` zur sicheren Aufbewahrung in einen anderen Ordner.
1. Beachten Sie die neue AEM-Version, die in Cloud Manager vermerkt ist (sie wird verwendet, um die neue Schnellstart-JAR-Version für den weiteren Download zu identifizieren).
1. Laden Sie im Software Distribution-Portal die Schnellstart-JAR-Datei herunter, deren Version mit der AEM-Version Ihrer Produktionsumgebung übereinstimmt.
1. Erstellen Sie einen ganz neuen Ordner und platzieren Sie darin die neue Schnellstart-JAR.
1. Starten Sie den neuen Schnellstart mit den gewünschten Ausführungsmodi (entweder durch Umbenennen der Datei oder Übergabe der Ausführungsmodi über `-r`).
   * Sorgen Sie dafür, dass keine Reste des alten Schnellstarts im Ordner verbleiben.
1. Erstellen Sie Ihre AEM-Anwendung.
1. Stellen Sie Ihre AEM-Anwendung mithilfe von Package Manager auf lokalem AEM bereit.
1. Installieren Sie über Package Manager alle Pakete mit veränderlichen Inhalten, die für lokale Umgebungstests benötigt werden.
1. Entwickeln Sie nach Bedarf weiter und stellen Sie Änderungen bereit.

Wenn es Inhalte gibt, die mit jeder neuen AEM-Schnellstartversion installiert werden sollen, fügen Sie sie in einem Inhaltspaket und der Quell-Code-Verwaltung des Projekts hinzu. Installieren Sie sie dann jedes Mal.

Sie sollten das SDK häufig aktualisieren (z. B. alle zwei Wochen) und täglich den ganzen lokalen Status verwerfen, um in der Anwendung nicht versehentlich von Stateful-Daten abzuhängen.

Wenn Sie von CryptoSupport abhängig sind ([entweder durch Konfiguration der Anmeldeinformationen von Cloud-Services oder des SMTP-Mail-Dienstes in AEM oder durch Verwendung der CryptoSupport-API in Ihrer Anwendung](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), werden die verschlüsselten Eigenschaften durch einen Schlüssel verschlüsselt. Dieser Schlüssel wird beim ersten Start einer AEM-Umgebung automatisch generiert. Während die Cloud-Implementierung dafür sorgt, dass der umgebungsspezifische CryptoKey automatisch wiederverwendet wird, muss der CryptoKey in die lokale Entwicklungsumgebung injiziert werden.

Standardmäßig ist AEM so konfiguriert, dass die Schlüsseldaten im Datenordner eines Ordners gespeichert werden. Im Sinne einer einfacheren Wiederverwendung in der Entwicklung kann der AEM-Prozess beim ersten Start mit „`-Dcom.adobe.granite.crypto.file.disable=true`“ initialisiert werden. Dieser Vorgang erzeugt die Verschlüsselungsdaten bei „`/etc/key`“.

Gehen Sie wie folgt vor, um Inhaltspakete, die die verschlüsselten Werte enthalten, wiederverwenden zu können:

* Wenn Sie die lokale Datei „quickstart.jar“ erstmals starten, müssen Sie den folgenden Parameter hinzufügen: „`-Dcom.adobe.granite.crypto.file.disable=true`“. Es ist optional, wird jedoch empfohlen, den Parameter immer hinzuzufügen.
* Erstellen Sie beim ersten Starten einer Instanz ein Paket, das einen Filter für den Stammordner „`/etc/key`“ enthält. Dieses Paket enthält das Geheimnis, das in allen Umgebungen wiederverwendet wird, in denen sie wiederverwendet werden sollen.
* Exportieren Sie alle veränderbaren Inhalte, die Geheimnisse enthalten, oder suchen Sie mithilfe von `/crx/de` die verschlüsselten Werte, damit Sie sie dem Paket hinzufügen können, das über mehrere Installationen hinweg wiederverwendet wird.
* Installieren Sie das in den Schritten 2 und 3 erstellte Paket jedes Mal, wenn Sie eine neue Instanz starten (entweder um sie durch eine neue Version zu ersetzen oder weil mehrere Entwicklungsumgebungen die Anmeldeinformationen zum Testen gemeinsam nutzen sollen). Auf diese Weise können Sie den Inhalt wiederverwenden, ohne dass eine manuelle Neukonfiguration erforderlich ist. Das liegt daran, dass der CryptoKey jetzt synchronisiert ist.
