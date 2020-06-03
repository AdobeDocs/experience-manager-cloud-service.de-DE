---
title: AEM as a Cloud Service-SDK
description: Noch auszufüllen
translation-type: tm+mt
source-git-commit: df6e6bc95b5f0489d0da034c27d8f3a4314a6e27
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 100%

---


# Das AEM as a Cloud Service-SDK {#aem-as-a-cloud-service-sdk}

Das AEM as a Cloud Service-SDK besteht aus den folgenden Artefakten:

* **Schnellstart-JAR**: die für die lokale Entwicklung verwendete AEM-Laufzeit.
* **Java-API-JAR**: die Java-JAR-/Maven-Abhängigkeit, die alle zulässigen Java-APIs verfügbar macht, die zur Entwicklung für AEM as a Cloud Service verwendet werden können. Zuvor als Uberjar bezeichnet.
* **Javadoc-JAR**: die Javadocs für das Java-API-JAR.
* **Dispatcher Tools**: der Satz von Tools, die der lokalen Entwicklung mit Dispatcher dienen. Separate Artefakte für Unix und Windows.

Darüber hinaus werden manche Kunden, die zuvor AEM 6.5 oder frühere Versionen bereitgestellt haben, die unten stehenden Artefakte verwenden. Wenn eine lokale Kompilierung mit dem Schnellstart-JAR nicht funktioniert und Sie vermuten, dass dies mit Schnittstellen zusammenhängt, die aus als Cloud Service bereitgestelltem AEM entfernt wurden, wenden Sie sich an den Kunden-Support, um herauszufinden, ob Sie Zugriff benötigen. Das macht Änderungen im Backend erforderlich.

* **6.5 Veraltetes Java-API-JAR**: ein zusätzlicher Satz von Schnittstellen, die seit AEM 6.5 entfernt wurden.
* **6.5 Veraltetes Javadoc-JAR**: die Javadocs für den zusätzlichen Satz an Schnittstellen.

## Zugriff auf das AEM as a Cloud Service-SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* Sie können das Symbol **Über Adobe Experience Manager** der AEM Admin Console prüfen, um die Version von AEM zu ermitteln, die Sie in der Produktionsumgebung ausführen.
* Das Schnellstart-JAR und die Dispatcher Tools können als ZIP-Datei aus dem [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)heruntergeladen werden. Beachten Sie, dass der Zugriff auf die SDK-Listen auf diejenigen mit AEM Managed Services- oder AEM as a Cloud Service-Umgebungen beschränkt ist.
* Die Java-API-JAR- und Javadoc-JAR-Pakete können über Maven-Tooling heruntergeladen werden, entweder mit der Befehlszeile oder mit Ihrer bevorzugten IDE.
* Die Maven-Projekt-POMs sollten auf das folgende API-JAR-Paket verweisen. Auf diese Abhängigkeit muss auch in allen Teilpaket-POMs verwiesen werden.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version>
  <scope>provided</scope>
</dependency>
```

>[!NOTE] Der Versionseintrag für das SDK sollte mit der Version von AEM as a Cloud Service übereinstimmen. Sie können anzeigen, welche Version Sie verwenden, indem Sie sich bei AEM anmelden, das Fragezeichen in der oberen rechten Ecke des Bildschirms aufrufen und **[!UICONTROL Über Adobe Experience Manager]** auswählen.


## Aktualisieren eines lokalen Projekts mit einer neuen SDK-Version {#refreshing-a-local-project-with-a-new-skd-version}

Wann sollte das lokale Projekt mit einem neuen SDK aktualisiert werden?

Es wird *empfohlen*, das Projekt mindestens nach jeder monatlichen Wartungsversion zu aktualisieren.

Es ist *optional*, nach jeder täglichen Wartungsversion zu aktualisieren. Kunden werden darüber informiert, wenn ihre Produktionsinstanz erfolgreich auf eine neue AEM-Version aktualisiert wurde. Bei den täglichen Wartungsversionen ist nicht zu erwarten, dass sich das neue SDK erheblich verändert hat (wenn überhaupt). Es wird dennoch empfohlen, die lokale AEM-Entwicklungsumgebung gelegentlich mit dem neuesten SDK zu aktualisieren und benutzerspezifische Anwendungen neu zu erstellen und zu testen. Die monatliche Wartungsversion umfasst in der Regel wirkungsvollere Änderungen, sodass Entwickler umgehend aktualisieren, neu erstellen und testen sollten.

Nachfolgend finden Sie die empfohlene Vorgehensweise zum Aktualisieren einer lokalen Umgebung:

1. Vergewissern Sie sich, dass alle nützlichen Inhalte entweder in die Quell-Code-Verwaltung für das Projekt übertragen wurden oder in einem veränderlichen Inhaltspaket für den späteren Import verfügbar sind.
1. Inhalte lokaler Entwicklungstests müssen separat gespeichert werden, damit sie nicht im Rahmen des Cloud Manager-Pipeline-Build bereitgestellt werden. Das liegt daran, dass sie nur der lokalen Entwicklung dienen.
1. Beenden Sie den derzeit ausgeführten Schnellstart.
1. Verschieben Sie den Ordner `crx-quickstart` in einen anderen Ordner, um ihn für alle Fälle aufzubewahren.
1. Notieren Sie die neue AEM-Version, die in Cloud Manager aufgeführt ist (mit dieser Version wird die neue Schnellstart-JAR-Version identifiziert, die später heruntergeladen werden soll).
1. Laden Sie im Software Distribution-Portal das Schnellstart-JAR-Paket herunter, dessen Version mit der AEM-Version Ihrer Produktionsumgebung übereinstimmt.
1. Erstellen Sie einen ganz neuen Ordner und platzieren Sie darin das neue Schnellstart-JAR-Paket.
1. Starten Sie den neuen Schnellstart mit den gewünschten Ausführungsmodi (entweder durch Umbenennen der Datei oder Übergabe an Ausführungsmodi per `-r`).
   * Sorgen Sie dafür, dass keine Reste des alten Schnellstarts im Ordner verbleiben.
1. Erstellen Sie die AEM-Anwendung.
1. Stellen Sie Ihre AEM-Anwendung via Package Manager im lokalen AEM bereit.
1. Installieren Sie über Package Manager alle Pakete mit veränderlichem Inhalt, die für lokale Umgebungstests benötigt werden.
1. Entwickeln Sie nach Bedarf weiter und stellen Sie Änderungen bereit.

Wenn es Inhalte gibt, die mit jeder neuen AEM-Schnellstartversion installiert werden sollen, fügen Sie sie in einem Inhaltspaket und der Quell-Code-Verwaltung des Projekts hinzu. Installieren Sie sie dann jedes Mal.

Sie sollten das SDK häufig aktualisieren (z. B. alle zwei Wochen) und täglich den ganzen lokalen Status verwerfen, um in der Anwendung nicht versehentlich von Stateful-Daten abzuhängen.

Wenn Sie CryptoSupport verwenden ([entweder durch Konfiguration der Anmeldeinformationen von Cloud Services oder des SMTP-Mail-Diensts in AEM bzw. durch Verwendung der CryptoSupport-API in Ihrer Anwendung](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), werden die verschlüsselten Eigenschaften durch einen Schlüssel verschlüsselt, der beim ersten Start einer AEM-Umgebung automatisch generiert wird. Während die Cloud-Implementierung dafür sorgt, dass der umgebungsspezifische CryptoKey automatisch wiederverwendet wird, muss der CryptoKey in die lokale Entwicklungsumgebung injiziert werden.

Standardmäßig ist AEM so konfiguriert, dass die Schlüsseldaten im Datenordner eines Ordners gespeichert werden. Aus Gründen einer einfacheren Wiederverwendung in der Entwicklung kann der AEM-Prozess beim ersten Start mit &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot; initialisiert werden. Dadurch werden bei &quot;`/etc/key`&quot; die Verschlüsselungsdaten generiert.

Damit Sie Inhaltspakete, die die verschlüsselten Werte enthalten, wiederverwenden können, müssen Sie die folgenden Schritte ausführen:

* Wenn Sie die lokale Datei „quickstart.jar“ erstmals starten, müssen Sie den folgenden Parameter hinzufügen: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Es ist optional, wird jedoch empfohlen, den Parameter immer hinzuzufügen.
* Erstellen Sie beim ersten Starten einer Instanz ein Paket, das einen Filter für den Stammordner &quot;`/etc/key`&quot; enthält. Es wird das Geheimnis enthalten, das in allen Umgebungen wiederverwendet wird, in denen sie wiederverwendet werden sollen.
* Exportieren Sie alle veränderlichen Inhalte, die Geheimnisse enthalten, oder suchen Sie die verschlüsselten Werte über `/crx/de`, um sie dem Paket hinzuzufügen, das über verschiedene Installationen hinweg wiederverwendet werden soll.
* Installieren Sie jedes Mal, wenn Sie eine neue Instanz starten (entweder um sie durch eine neue Version zu ersetzen oder weil mehrere Entwicklungsumgebungen die gleichen Anmeldeinformationen zum Testen verwenden sollten), das in den Schritten 2 und 3 erstellte Paket, um den Inhalt wiederverwenden zu können, ohne eine manuelle Neukonfiguration vorzunehmen müssen. Das liegt daran, dass der CryptoKey jetzt synchronisiert ist.
