---
title: AEM as a Cloud Service-SDK
description: Überblick über das AEM as a Cloud Service Software Development Kit.
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 100%

---

# Das AEM as a Cloud Service-SDK {#aem-as-a-cloud-service-sdk}

Das AEM as a Cloud Service-SDK besteht aus den folgenden Artefakten:

* **Schnellstart-JAR**: die für die lokale Entwicklung verwendete AEM-Laufzeit.
* **Java™-API-JAR**: die Java™-JAR-/Maven-Abhängigkeit, die alle zulässigen Java™-APIs verfügbar macht, die zur Entwicklung für AEM as a Cloud Service verwendet werden können. Zuvor als Uberjar bezeichnet.
* **Javadoc-JAR**: die Javadocs für das Java™-API-JAR.
* **Dispatcher Tools**: der Satz von Tools, die der lokalen Entwicklung mit Dispatcher dienen. Separate Artefakte für UNIX® und Windows.

Darüber hinaus werden manche Kundinnen und Kunden, die zuvor AEM 6.5 oder frühere Versionen bereitgestellt haben, die unten stehenden Artefakte verwenden. Wenn die lokale Kompilierung mit der Quickstart-JAR nicht funktioniert und Sie vermuten, dass dies auf die Entfernung von Schnittstellen aus AEM zurückzuführen ist, das als Cloud-Service bereitgestellt wird, wenden Sie sich an den Kunden-Support. Sie können feststellen, ob Sie Zugang benötigen. Dies erfordert Änderungen im Backend.

* **6.5 Veraltetes Java™-API-JAR**: ein zusätzlicher Satz von Schnittstellen, die seit AEM 6.5 entfernt wurden.
* **6.5 Veraltetes Javadoc-JAR**: die Javadocs für den zusätzlichen Satz an Schnittstellen.

>[!NOTE]
> 
> AEM as a Cloud Service und das SDK unterscheiden sich in verschiedenen Bereichen voneinander. Für Situationen, in denen schnelle und iterative Änderungen erforderlich sind, hat Adobe schnelle Entwicklungsumgebungen (Rapid Development Environments) eingeführt. Weitere Informationen finden Sie unter [Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md).

## Erstellen für das SDK {#building-for-the-sdk}

Das AEM as a Cloud Service-SDK wird zum Erstellen und Bereitstellen von benutzerdefiniertem Code verwendet. Siehe die [Dokumentation zum AEM-Projektarchetyp](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/using). Im Allgemeinen werden die folgenden Schritte ausgeführt:

* **Code kompilieren**: Der Quell-Code wird kompiliert, wodurch die resultierenden Inhaltspakete erzeugt werden.
* **Artefakte erstellen**: Während dieses Prozesses werden Artefakte erstellt.
* **Pakete analysieren**: Pakete werden mithilfe des Maven-Analyzer-Plug-ins analysiert, das nach Problemen im Maven-Projekt sucht, z. B. fehlenden Abhängigkeiten.
* **Artefakte bereitstellen**: Auf dem lokalen Server werden Artefakte bereitgestellt.

Cloud Manager führt dieselben Schritte bei der Bereitstellung in Cloud-Umgebungen aus. Die lokale Durchführung von Builds ermöglicht eine lokale Entwicklung und Prüfung. Entwicklerinnen und Entwickler können Code- oder Strukturprobleme effizient erkennen, bevor sie in die Versionskontrolle übernommen werden. Dadurch werden Verzögerungen verhindert, die durch das Auslösen von Cloud Manager-Bereitstellungen verursacht werden, die länger dauern können.

>[!NOTE]
>
>Das AEM as a Cloud Service SDK sollte mit einer Distribution und Version von Java erstellt werden, die von der [Build-Umgebung von Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) unterstützt wird. Kundinnen und Kunden von AEM as a Cloud Service können das Oracle JDK über das [Software-Verteilungsportal ](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) herunterladen. Sie haben erweiterte Unterstützung für Java 11 bis September 2026 durch die Lizenz- und Support-Bedingungen von Adobe für die Oracle Java-Technologie in Adobe Experience Manager-Projekten.

## Zugriff auf das AEM as a Cloud Service-SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* Sie können das Symbol **Über Adobe Experience Manager** der AEM Admin Console überprüfen, um die Version von AEM zu ermitteln, die Sie in der Produktionsumgebung ausführen.
* Das Schnellstart-JAR und die Dispatcher Tools können als ZIP-Datei aus dem [Software-Verteilungsportal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) heruntergeladen werden. Der Zugriff auf die SDK-Listen ist auf Personen beschränkt, die Umgebungen auf AEM Managed Services oder AEM as a Cloud Service haben.
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
>Der Versionseintrag für das SDK muss mit der Version von AEM as a Cloud Service übereinstimmen. Sie können sehen, welche Version Sie verwenden, indem Sie sich bei AEM anmelden. Klicken Sie oben rechts im Bildschirm auf das Fragezeichen und dann auf **[!UICONTROL Über Adobe Experience Manager]**.


## Aktualisieren eines lokalen Projekts mit einer neuen SDK-Version {#refreshing-a-local-project-with-a-new-skd-version}

Wann sollte das lokale Projekt mit einem neuen SDK aktualisiert werden?

Adobe *empfiehlt* die Aktualisierung nach einer monatlichen Wartungsversion.

Es ist *optional*, nach jeder täglichen Wartungsversion zu aktualisieren. Kundinnen und Kunden werden darüber informiert, wenn ihre Produktionsinstanz erfolgreich auf eine neue AEM-Version aktualisiert wurde. Bei den täglichen Wartungsversionen ist nicht zu erwarten, dass sich das neue SDK erheblich verändert hat (wenn überhaupt). Adobe empfiehlt dennoch, die lokale AEM-Entwicklungsumgebung gelegentlich mit dem neuesten SDK zu aktualisieren und benutzerspezifische Programme neu zu erstellen und zu testen. Die monatliche Wartungsversion umfasst in der Regel wirkungsvollere Änderungen, sodass Entwicklerinnen und Entwickler umgehend aktualisieren, neu erstellen und testen sollten.

**So aktualisieren Sie ein lokales Projekt mit einer neuen SDK-Version**:

1. Stellen Sie sicher, dass alle nützlichen Inhalte in die Versionskontrolle übernommen werden. Oder in einem veränderbaren Inhaltspaket für den späteren Import gespeichert werden.
1. Inhalte lokaler Entwicklungstests müssen separat gespeichert werden, damit sie nicht im Rahmen des Cloud Manager-Pipeline-Build bereitgestellt werden. Der Grund dafür ist, dass sie nur für die lokale Entwicklung verwendet werden.
1. Stoppen Sie den derzeit laufenden Schnellstart.
1. Verschieben Sie den Ordner `crx-quickstart` zur sicheren Aufbewahrung in einen anderen Ordner.
1. Beachten Sie die neue AEM-Version, die in Cloud Manager vermerkt ist (sie wird verwendet, um die neue Schnellstart-JAR-Version für den weiteren Download zu identifizieren).
1. Laden Sie im Software-Verteilungsportal die Schnellstart-JAR herunter, deren Version mit der AEM-Version übereinstimmt.
1. Erstellen Sie einen ganz neuen Ordner und platzieren Sie darin die neue Schnellstart-JAR.
1. Starten Sie den neuen Schnellstart mit den gewünschten Ausführungsmodi (entweder durch Umbenennen der Datei oder durch Übergabe der Ausführungsmodi über `-r`).
Sorgen Sie dafür, dass keine Reste des alten Schnellstarts im Ordner verbleiben.
1. Erstellen Sie Ihre AEM-Anwendung.
1. Stellen Sie Ihre AEM-Anwendung mithilfe des Paket-Managers auf lokalem AEM bereit.
1. Installieren Sie über den Paket-Manager alle Pakete mit veränderlichen Inhalten, die für lokale Umgebungstests benötigt werden.
1. Entwickeln Sie nach Bedarf weiter und stellen Sie Änderungen bereit.

Wenn es Inhalte gibt, die mit jeder neuen AEM-Schnellstartversion installiert werden sollen, fügen Sie sie in einem Inhaltspaket und der Quell-Code-Verwaltung des Projekts hinzu. Installieren Sie sie dann jedes Mal.

Adobe empfiehlt, das SDK häufig zu aktualisieren, z. B. alle zwei Wochen. Entsorgen Sie außerdem täglich den ganzen lokalen Status, um in der Anwendung nicht versehentlich von Stateful-Daten abzuhängen.

Wenn Sie CryptoSupport für Cloud-Services, die SMTP-Mail-Konfiguration oder die CryptoSupport-API verwenden, werden verschlüsselte Eigenschaften mit einem Schlüssel gesichert. Weitere Informationen finden Sie in der [Dokumentation zur CryptoSupport-API](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html). Dieser Schlüssel wird beim ersten Start einer AEM-Umgebung automatisch generiert. Während die Cloud-Implementierung dafür sorgt, dass der umgebungsspezifische CryptoKey automatisch wiederverwendet wird, muss der CryptoKey in die lokale Entwicklungsumgebung injiziert werden.

Standardmäßig ist AEM so konfiguriert, dass die Schlüsseldaten im Datenordner eines Ordners gespeichert werden. Im Sinne einer einfacheren Wiederverwendung in der Entwicklung kann der AEM-Prozess beim ersten Start mit „`-Dcom.adobe.granite.crypto.file.disable=true`“ initialisiert werden. Dieser Vorgang erzeugt die Verschlüsselungsdaten bei „`/etc/key`“.

**So verwenden Sie Inhaltspakete wieder, die die verschlüsselten Werte enthalten:**

* Wenn Sie die lokale Datei „quickstart.jar“ erstmals starten, müssen Sie den folgenden Parameter hinzufügen: „`-Dcom.adobe.granite.crypto.file.disable=true`“. Adobe empfiehlt optional, ihn immer hinzuzufügen.
* Erstellen Sie beim ersten Starten einer Instanz ein Paket, das einen Filter für den Stammordner „`/etc/key`“ enthält. Dieses Paket enthält das Geheimnis, das in allen Umgebungen wiederverwendet wird, in denen Sie sie wiederverwenden wollen.
* Exportieren Sie alle veränderlichen Inhalte, die Geheimnisse enthalten. Oder suchen Sie mithilfe von `/crx/de` die verschlüsselten Werte, damit Sie sie dem Paket hinzufügen können, das über mehrere Installationen hinweg wiederverwendet wird.
* Installieren Sie das in den Schritten 2 und 3 erstellte Paket jedes Mal, wenn Sie eine neue Instanz starten (entweder um sie durch eine neue Version zu ersetzen oder weil mehrere Entwicklungsumgebungen die Anmeldeinformationen zum Testen gemeinsam nutzen sollen). Auf diese Weise können Sie den Inhalt wiederverwenden, ohne dass eine manuelle Neukonfiguration erforderlich ist. Das liegt daran, dass der CryptoKey jetzt synchronisiert ist.

