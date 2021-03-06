---
title: Funkcja SccBackgroundGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701229"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet, funkcja
Ta funkcja pobiera z kontroli źródła każdego z określonych plików bez interakcji z użytkownikiem.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parametry
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

podczas Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

[in. out] Tablica nazw plików do pobrania.

> [!NOTE]
> Nazwy muszą być w pełni kwalifikowanymi nazwami plików lokalnych.

 flagiDW

podczas Flagi poleceń ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

podczas Unikatowa wartość skojarzona z tą operacją.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja została ukończona pomyślnie.|
|SCC_E_BACKGROUNDGETINPROGRESS|Trwa już pobieranie w tle (wtyczka do kontroli źródła powinna zwrócić tę wartość tylko wtedy, gdy nie obsługuje równoczesnych operacji wsadowych).|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest zawsze wywoływana na wątku innym niż ten, który załadował wtyczkę kontroli źródła. Ta funkcja nie powinna zostać zwrócona, dopóki nie zostanie ukończona; może jednak być wywoływana wielokrotnie z wieloma listami plików.

 Użycie `dwFlags` argumentu jest takie samo jak [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
