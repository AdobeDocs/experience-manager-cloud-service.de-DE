---
title: Eigenschaften des Micro-Frontend-Inhaltsfragment-Selektors für Adobe Experience Manager as a Cloud Service
description: Eigenschaften zum Konfigurieren des Micro-Frontend-Inhaltsfragment-Selektors zum Suchen, Finden und Abrufen von Inhaltsfragmenten in Ihrer Anwendung.
role: Admin, User
exl-id: c81b5256-09fb-41ce-9581-f6d1ad316ca4
source-git-commit: a3d8961b6006903c42d983c82debb63ce8abe9ad
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 98%

---

# Inhaltsfragment-Selektor – Verwandte Eigenschaften {#content-fragment-selector-related-properties}

Über den Micro-Frontend-Inhaltsfragment-Selektor können Sie Inhaltsfragmente im Repository durchsuchen bzw. suchen und in Ihrer Anwendung verwenden.

Sie können mithilfe der folgenden Eigenschaften anpassen, wie der Inhaltsfragment-Selektor gerendert wird und wie er eingesetzt werden kann:

## Eigenschaften des Inhaltsfragment-Selektors {#content-fragment-selector-properties}

| Eigenschaft | Typ | Erforderlich | Standard | Beschreibung |
|--- |--- |--- |--- |--- |
| `imsToken` | Zeichenfolge | Nein | | Zur Authentifizierung verwendetes IMS-Token. |
| `repoId` | Zeichenfolge | Nein | | Zur Authentifizierung verwendete Repository-ID. |
| `orgId` | Zeichenfolge | Ja | | Zur Authentifizierung verwendete Organisations-ID. |
| `locale` | Zeichenfolge | Nein | | Gebietsschema-Daten. |
| `env` | Umgebung | Nein | | Bereitstellungsumgebung des Inhaltsfragment-Selektors. |
| `filters` | Fragmentfilter | Nein | | Für die Liste der Inhaltsfragmente anzuwendende Filter. Standardmäßig werden Fragmente unter `/content/dam` angezeigt. Standardwert: `{ folder: "/content/dam" }` |
| `isOpen` | Boolesch | Ja | `false` | Markierung, um auszulösen, dass der Selektor geöffnet oder geschlossen wird. |
| `onDismiss` | () => void | Ja | | Funktion, die aufgerufen werden soll, wenn **Verwerfen** ausgewählt wird. |
| `onSubmit` | ({ contentFragments: `{id: string, path: string}[]`, domainNames: `string[]` }) => void | Ja | | Funktion, die aufgerufen wird, wenn **Auswählen** nach Auswahl eines oder mehrerer Inhaltsfragmente verwendet wird. <br><br>Die Funktion empfängt:<br><ul><li> die ausgewählten Inhaltsfragmente mit den Feldern `id` und `path`</li><li>sowie Domain-Namen, die mit der Programm-ID und der Umgebungs-ID des Repositorys verknüpft sind, die den Status `ready` und „Veröffentlichen“ als `tier` aufweisen</li></ul><br>Wenn keine Domain-Namen vorhanden sind, wird die Veröffentlichungsinstanz als Fallback-Domain verwendet. |
| `theme` | „Hell“ oder „Dunkel“ | Nein | | Design des Inhaltsfragment-Selektors. Als Standard-Design ist das Design der UnifiedShell-Umgebung eingestellt. |
| `selectionType` | „Einzel“ oder „Mehrere“ | Nein | `single` | Auswahltyp, der zur Einschränkung der Auswahl für den Fragment-Selektor verwendet werden kann. |
| `dialogSize` | „fullscreen“ oder „fullscreenTakeover“ | Nein | `fullscreen` | Optionale Eigenschaft zum Steuern der Dialogfeldgröße. |
| `waitForImsToken` | Boolesch | Nein | `false` | Gibt an, ob der Inhaltsfragment-Selektor im Kontext des SUSI-Flusses gerendert wird und warten muss, bis das `imsToken` bereit ist. |
| `imsAuthInfo` | ImsAuthInfo | Nein | | Objekt, das die IMS-Authentifizierungsinformationen der bzw. des angemeldeten Benutzenden enthält |
| `runningInUnifiedShell` | Boolesch | Nein | | Gibt an, ob der Inhaltsfragment-Selektor unter UnifiedShell oder eigenständig ausgeführt wird. |
| `readonlyFilters` | ResourceReadonlyFiltersField | Nein | | Schreibgeschützte Filter, die auf die Inhaltsliste angewendet und nicht entfernt werden können. |

## ImsAuthProps-Eigenschaften {#imsauthprops-properties}

Die `ImsAuthProps`-Eigenschaften definieren die Authentifizierungsinformationen und den Fluss, mit dem der Inhaltsfragment-Selektor ein `imsToken` abruft. Durch Festlegen dieser Eigenschaften können Sie steuern, wie sich der Authentifizierungsfluss verhält, und Listener für verschiedene Authentifizierungsereignisse registrieren.

| Eigenschaftsname | Beschreibung |
|--- |--- |
| `imsClientId` | Ein Zeichenfolgenwert, der die für Authentifizierungszwecke verwendete IMS-Client-ID darstellt. Dieser Wert wird von Adobe bereitgestellt und ist spezifisch für Ihre Adobe AEM CS-Organisation. |
| `imsScope` | Beschreibt die bei der Authentifizierung verwendeten Bereiche. Die Bereiche bestimmen den Umfang des Zugriffs, den die Anwendung auf die Ressourcen Ihrer Organisation hat. Mehrere Bereiche werden durch Kommas voneinander getrennt. |
| `redirectUrl` | Stellt die URL dar, an die Benutzende nach der Authentifizierung weitergeleitet werden. Dieser Wert wird normalerweise auf die aktuelle URL der Anwendung gesetzt. Wenn keine `redirectUrl` angegeben wird, verwendet `ImsAuthService` die zum Registrieren der `imsClientId` verwendete redirectUrl. |
| `modalMode` | Ein boolescher Wert, der angibt, ob der Authentifizierungsfluss in einem Modal (Popup-Fenster) angezeigt werden soll oder nicht. Wenn `true` festgelegt ist, wird der Authentifizierungsfluss in einem Popup-Fenster angezeigt. Wenn `false` festgelegt ist, wird der Authentifizierungsfluss bei vollständigem Neuladen der Seite angezeigt. <br>**Hinweis:** Für ein besseres Anwendererlebnis können Sie diesen Wert dynamisch steuern, wenn Popup-Fenster des Browsers deaktiviert sind. |
| `onImsServiceInitialized` | Eine Rückruffunktion, die aufgerufen wird, wenn der Adobe IMS-Authentifizierungsdienst initialisiert wird. Diese Funktion akzeptiert einen Parameter namens `service`, ein Objekt, das den Adobe IMS-Dienst darstellt. Siehe [`ImsAuthService`](#imsauthservice-ims-auth-service) für weitere Informationen. |
| `onAccessTokenReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn ein `imsToken` vom Adobe IMS-Authentifizierungsdienst empfangen wird. Diese Funktion akzeptiert einen Parameter namens `imsToken`, eine Zeichenfolge, die das Zugriffstoken darstellt. |
| `onAccessTokenExpired` | Eine Rückruffunktion, die aufgerufen wird, wenn ein Zugriffstoken abgelaufen ist. Diese Funktion wird normalerweise verwendet, um einen neuen Authentifizierungsfluss auszulösen und so ein neues Zugriffstoken zu erhalten. |
| `onErrorReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn während der Authentifizierung ein Fehler auftritt. Diese Funktion akzeptiert zwei Parameter: den Fehlertyp und die Fehlermeldung. Der Fehlertyp ist eine Zeichenfolge, die den Fehlertyp darstellt, und die Fehlermeldung ist eine Zeichenfolge, die die Fehlermeldung darstellt. |

## Eigenschaften von ImsAuthService {#imsauthservice-properties}

Die Klasse `ImsAuthService` regelt den Authentifizierungsfluss für den Ihaltsfragment-Selektor. Sie ist für den Erhalt eines `imsToken` über den Adobe IMS-Authentifizierungsdienst verantwortlich. Das `imsToken` wird verwendet, um die Benutzerin oder den Benutzer zu authentifizieren und den Zugriff auf das Adobe Experience Manager (AEM) CS-Repository zu autorisieren. Der ImsAuthService verwendet die `ImsAuthProps`-Eigenschaften, um den Authentifizierungsfluss zu steuern und Listener für verschiedene Authentifizierungsereignisse zu registrieren. Sie können die praktische Funktion `registerContentFragmentSelectorAuthService` zum Registrieren der Instanz `ImsAuthService` beim Inhaltsfragment-Selektor verwenden. Die folgenden Funktionen sind in der Klasse `ImsAuthService` verfügbar. Wenn Sie jedoch die Funktion `registerContentFragmentSelectorAuthService` verwenden, müssen Sie diese Funktionen nicht direkt aufrufen.

| Funktionsname | Beschreibung |
|--- |--- |
| `isSignedInUser` | Bestimmt, ob die Person derzeit beim Dienst angemeldet ist, und gibt entsprechend einen booleschen Wert zurück. |
| `getImsToken` | Ruft das Authentifizierungs-`imsToken` für die derzeit angemeldete Person ab, das zum Authentifizieren von Anfragen bei anderen Diensten verwendet werden kann, z. B. zum Generieren von Asset-_Ausgabedarstellungen_. |
| `signIn` | Startet den Anmeldeprozess für die Person. Diese Funktion verwendet die `ImsAuthProps`, um die Authentifizierung in einem Popup oder beim vollständigem Neuladen einer Seite anzuzeigen. |
| `signOut` | Meldet die Person vom Dienst ab, macht ihr Authentifizierungs-Token ungültig und fordert sie auf, sich erneut anzumelden, um auf geschützte Ressourcen zuzugreifen. Durch Aufrufen dieser Funktion wird die aktuelle Seite neu geladen. |
| `refreshToken` | Aktualisiert das Authentifizierungs-Token für die derzeit angemeldete Person, verhindert das Ablaufen des Tokens und stellt einen unterbrechungsfreien Zugriff auf geschützte Ressourcen sicher. Gibt ein neues Authentifizierungs-Token zurück, das für nachfolgende Anforderungen verwendet werden kann. |
