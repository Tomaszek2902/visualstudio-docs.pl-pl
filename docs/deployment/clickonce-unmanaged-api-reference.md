---
title: Niezarządzana dokumentacja interfejsu API ClickOnce | Microsoft Docs
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b536a17df4f54158aa6f157a0d9795cf359ddc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900281"
---
# <a name="clickonce-unmanaged-api-reference"></a>Dokumentacja niezarządzanego interfejsu API ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] niezarządzane publiczne interfejsy API z dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Czyści lub Odinstalowuje wszystkie aplikacje online z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pamięci podręcznej aplikacji.

### <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca wartość HRESULT, która reprezentuje błąd. Jeśli wystąpi wyjątek zarządzany, zwraca 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Uwagi
 Wywołanie CleanOnlineAppCache spowoduje uruchomienie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usługi, jeśli nie została jeszcze uruchomiona.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Pobiera informacje o wdrożeniu z manifestu i adresu URL aktywacji.

### <a name="parameters"></a>Parametry

|Parametr|Opis|Typ|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Wskaźnik do elementu `ActivationURL` .|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Wskaźnik do elementu `PathToDeploymentManifest` .|LPCWSTR|
|`pwzApplicationIdentity`|Wskaźnik do buforu, aby otrzymać ciąg zakończony znakiem NULL, który określa pełną tożsamość aplikacji zwracaną.|LPWSTR|
|`pdwIdentityBufferLength`|Wskaźnik do typu DWORD, który jest długością `pwzApplicationIdentity` buforu w WCHARs. Obejmuje to miejsce dla znaku zakończenia o wartości NULL.|LPDWORD|
|`pwzProcessorArchitecture`|Wskaźnik do buforu, aby otrzymać ciąg zakończony znakiem NULL, który określa architekturę procesora wdrożenia aplikacji, z manifestu.|LPWSTR|
|`pdwArchitectureBufferLength`|Wskaźnik do typu DWORD, który jest długością `pwzProcessorArchitecture` buforu w WCHARs.|LPDWORD|
|`pwzApplicationManifestCodebase`|Wskaźnik do buforu, aby otrzymać ciąg zakończony znakiem NULL, który określa bazę kodu manifestu aplikacji, z manifestu.|LPWSTR|
|`pdwCodebaseBufferLength`|Wskaźnik do typu DWORD, który jest długością `pwzApplicationManifestCodebase` buforu w WCHARs.|LPDWORD|
|`pwzDeploymentProvider`|Wskaźnik do buforu, aby otrzymać ciąg zakończony znakiem NULL, który określa dostawcę wdrożenia z manifestu, jeśli jest obecny. W przeciwnym razie zwracany jest pusty ciąg.|LPWSTR|
|`pdwProviderBufferLength`|Wskaźnik do typu DWORD, który jest długością `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca wartość HRESULT, która reprezentuje błąd. Zwraca HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER), jeśli bufor jest za mały.

### <a name="remarks"></a>Uwagi
 Wskaźniki nie mogą mieć wartości null. `pcwzActivationUrl` i `pcwzPathToDeploymentManifest` nie mogą być puste.

 Jest on odpowiedzialny za wyczyszczenie adresu URL aktywacji. Na przykład dodawanie znaków ucieczki w razie potrzeby lub usuwanie ciągu zapytania.

 Jest on odpowiedzialny za ograniczenie długości danych wejściowych. Na przykład maksymalna długość adresu URL to 2KB.

## <a name="launchapplication"></a>LaunchApplication
 Uruchamia lub instaluje aplikację przy użyciu adresu URL wdrożenia.

### <a name="parameters"></a>Parametry

|Parametr|Opis|Typ|
|---------------|-----------------|----------|
|`deploymentUrl`|Wskaźnik do ciągu zakończonego wartością NULL, który zawiera adres URL manifestu wdrożenia.|LPCWSTR|
|`data`|Zarezerwowane do użytku w przyszłości. Musi mieć wartość NULL.|LPVOID|
|`flags`|Zarezerwowane do użytku w przyszłości. Musi mieć wartość 0.|DWORD|

### <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca wartość HRESULT, która reprezentuje błąd. Jeśli wystąpi wyjątek zarządzany, zwraca 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Zobacz też
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>