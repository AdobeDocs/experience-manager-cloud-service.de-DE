---
title: Löschen eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
description: Löschen eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
exl-id: 43f66871-cca4-4709-95d0-68aa715c0da2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---

# Löschen eines SSL-Zertifikats {#deleting-an-ssl-certificate}

>[!IMPORTANT]
>Das Entfernen von Zertifikaten aus Cloud Manager ist eine dauerhafte Aktion, die nicht rückgängig gemacht werden kann. Es empfiehlt sich, alle erforderlichen SSL-Dateien lokal zu speichern, bevor Sie sie in der Benutzeroberfläche von Cloud Manager löschen.

Ein Anwender muss die Rolle „Geschäftsinhaber“ oder „Bereitstellungs-Manager“ innehaben, um ein SSL-Zertifikat in Cloud Manager löschen zu können. Cloud Manager ermöglicht es nicht, ein SSL-Zertifikat zu löschen, dem eine oder mehrere Domains zugeordnet sind.  Alle verknüpften Domains müssen vor dem Löschen des SSL-Zertifikats gelöscht werden. Weitere Informationen finden Sie unter [Löschen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md).

Gehen Sie wie folgt vor, um ein SSL-Zertifikat zu löschen:

1. Navigieren Sie auf der Seite **Umgebungen** zum Bildschirm **SSL-Zertifikate**.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)
1. Identifizieren Sie die Zeile, in der der Name des SSL-Zertifikats aufgeführt ist, das Sie löschen möchten.
1. Wählen Sie das Menü **...** ganz rechts in der Zeile aus.
1. Wählen Sie **Löschen** aus.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete01.png)
1. Bestätigen Sie Ihre Übermittlung über das Dialogfeld **SSL-Zertifikat löschen**.
