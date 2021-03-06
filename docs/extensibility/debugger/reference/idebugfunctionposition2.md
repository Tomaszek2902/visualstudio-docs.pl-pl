---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c260b6316207b0079a2ca8893b851db8b1288ba6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728311"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Ten interfejs reprezentuje pozycję abstrakcyjną funkcji w dokumencie źródłowym.

## <a name="syntax"></a>Składnia

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować pozycję funkcji w dokumencie źródłowym.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest dostarczany jako część Unii [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (w odniesieniu do struktury [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) ), która jest z kolei częścią struktury [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) używanej podczas tworzenia oczekującego punktu przerwania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugFunctionPosition2` .

|Metoda|Opis|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Pobiera nazwę funkcji, względem której odnosi się ta pozycja.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Pobiera przesunięcie od początku funkcji.|

## <a name="remarks"></a>Uwagi
 Pozycja reprezentowana przez ten interfejs jest oparta na tekście, w specjalnej strukturze [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
