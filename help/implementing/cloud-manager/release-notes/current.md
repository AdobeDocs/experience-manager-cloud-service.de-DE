---
title: Versionshinweise für Cloud Manager 2024.10.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Versionshinweise für Cloud Manager 2024.10.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: aa8d4c8c69a96054492b886893414c3e82b2f4ad
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 13%

---

# Versionshinweise für Cloud Manager 2024.10.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2024.10.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager-Version 2024.10.0 in AEM as a Cloud Service wurde am 3. Oktober 2024 veröffentlicht.

Die nächste Version ist für den Freitag, 14. November 2024 geplant.

## Neue Funktionen {#what-is-new}

* <!-- BOTH CS & AMS --> Die in Cloud Manager verwendete AEM Archetyp-Version wird jetzt auf Version 26 aktualisiert. Siehe [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)

<!-- (CMGR-59817) -->

* <!-- CS ONLY --> Beim Hinzufügen einer neuen benutzerdefinierten Domäne umfasste die vorherige Überprüfungsmethode einen langwierigen DNS-Validierungsprozess. Adobe hat diesen Prozess für Kunden vereinfacht. Jetzt müssen Sie nur noch ein gültiges SSL-Zertifikat (EV oder OV) bereitstellen, das als Eigentumsnachweis dient. Es ist nicht mehr erforderlich, TXT-Einträge im DNS zu aktualisieren.

  >[!NOTE]
  >
  >Diese Funktion gilt nur für vom Kunden verwaltete EV- und OV-Zertifikate. Von Adobe verwaltete DV-Zertifikate erfordern weiterhin einen CNAME-Eintrag.

  Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

  ![Verifizierung der Domäne für ein kundenverwaltetes E/V-Zertifikat](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png)

* <!-- CS ONLY --> Beim Hinzufügen oder Bearbeiten einer Netzwerkinfrastruktur werden die Werte in den Feldern IP-Adresse und Netzwerkmaske anhand der folgenden Regeln validiert:

   * Die Adresszeile darf sich nicht mit den im Bereich der Verbindungsadresse definierten Adressen überschneiden.
   * DNS-Adressen müssen entweder zur Netzwerkmaske gehören, die im Verbindungsadressenbereich definiert ist, oder öffentlich sein.

  ![Dialogfeld &quot;Netzwerkinfrastruktur hinzufügen&quot;](/help/implementing/cloud-manager/release-notes/assets/network-infrastructure-add.png)

* <!-- CS ONLY --> Das Format der Implementierungsprotokolle für die Umgebung für die Indizierung, die Installation veränderlicher Inhalte und die Umwandlung von Aufträgen wird geändert.

  >[!NOTE]
  >
  >Diese Änderung soll schrittweise eingeführt werden, wobei im Dezember 2024 ein Abschlussdatum erwartet wird.

  ![Auf Produktionskarte bereitstellen](/help/implementing/cloud-manager/release-notes/assets/deploy-to-production-card.png)

  Das Format des Protokolls ändert sich von einem einfachen Eintrag wie im Folgenden gezeigt:

  ![Protokolldatei mit einfachen Einträgen](/help/implementing/cloud-manager/release-notes/assets/log-file-simple-entry.png)

  Für einen JSON-Eintrag, der im Folgenden angezeigt wird:

  ![Protokolldatei mit JSON-Einträgen](/help/implementing/cloud-manager/release-notes/assets/log-file-json-entry.png)


## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Cloud Manager-Programm teil und haben Sie die Möglichkeit, bevorstehende Funktionen zu testen.

### Eigenes Git - jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion **Eigenes Git holen** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Enterprise-GitHub-Repositorys. Wenn Sie diese neuen Repos hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit einer konstanten Codesynchronisation mit dem Adobe-Repository und bietet die Möglichkeit, Pull-Anforderungen zu validieren, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Siehe [Hinzufügen externer Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind die vordefinierten Qualitätsprüfungen für Pull-Anforderungscode ausschließlich für von GitHub gehostete Repositorys verfügbar. Es wird jedoch ein Update vorgenommen, um diese Funktion auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie eine E-Mail von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Stellen Sie sicher, dass Sie angeben, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder Enterprise-Repository-Struktur befinden.


<!-- ## Bug fixes




## Known Issues {#known-issues} -->
