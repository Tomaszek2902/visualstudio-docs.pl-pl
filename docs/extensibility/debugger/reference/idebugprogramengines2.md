---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722400"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Ten interfejs jest używany przez węzły programu w celu określenia wszystkich możliwych aparatów debugowania (DE), które mogą debugować ten program.

## <a name="syntax"></a>Składnia

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowa dostawca portu implementuje ten interfejs w tym samym obiekcie, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) do obsługi ustanowienia konkretnego elementu de do użycia dla określonego programu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgramNode2` interfejsie, aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProgramEngines2` .

|Metoda|Opis|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Wskazuje wszystkie możliwe metody DEs, które mogą debugować ten program.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wybiera wartość DE do użycia na potrzeby debugowania tego programu.|

## <a name="remarks"></a>Uwagi
 Po wybraniu przez użytkownika tego wyboru zostanie on zarejestrowany w węźle program, wywołując metodę [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Wybrany aparat przejdzie do aparatu zwróconego przez [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
