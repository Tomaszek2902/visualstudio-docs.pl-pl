---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715569"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Ten interfejs wylicza programy uruchomione w bieżącej sesji debugowania.

## <a name="syntax"></a>Składnia

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby zapewnić listę programów debugowanych przez DE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Program Visual Studio wywołuje [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , aby uzyskać ten interfejs. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) nie jest używany przez program Visual Studio.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugPrograms2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Pobiera określoną liczbę programów w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Pomija określoną liczbę programów w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Pobiera liczbę programów w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego interfejsu do:

- Wypełnij okno **moduły** (wywołując [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , a następnie wywołując [EnumModules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) w każdym z programów).

- Wypełnij listę **Dołącz do procesu** (wywołując, `IDebugProcess2::EnumPrograms` a następnie wywołując wywołanie [QueryInterface](/cpp/atl/queryinterface) dla każdego interfejsu [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , aby uzyskać Interfejs [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) ).

- Wygeneruj listę DEs, która może debugować każdy program w procesie (przy użyciu [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Zastosuj aktualizacje funkcji Edytuj i Kontynuuj (ENC) do każdego programu (wywołując IDebugProcess2:: EnumPrograms, a następnie wywołując [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
