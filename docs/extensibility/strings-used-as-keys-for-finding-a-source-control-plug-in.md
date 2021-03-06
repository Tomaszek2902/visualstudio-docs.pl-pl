---
title: Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67e1a9c73c13632cf766b0536f2b7cfc1b456394
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037136"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
Następujące ciągi są kluczami służącymi do uzyskiwania dostępu do rejestru w celu znalezienia informacji o wtyczce kontroli źródła.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` i `STR_SCCPROVIDERNAME` są kluczami rejestru lub wartościami używanymi do rejestrowania biblioteki DLL jako wtyczki kontroli źródła dla programu Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` i `SCC_STATUS_FILE` są używane do opisywania formatu MSSCCPRJ. Plik SCC.

## <a name="string-keys-and-values"></a>Klucze i wartości ciągów

|Klucz|Wartość|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Kontrola kodu źródłowego|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Plik kontroli kodu źródłowego|
|`SCC_NSE`|Rozszerzenie przestrzeni nazw|
|`SCC_NSE_PREFIX`|Prefiks Protocal|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Zobacz także
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
