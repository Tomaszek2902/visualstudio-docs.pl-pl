---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78088d6e5da61c32302c13b08143c9ed902452e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722631"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE) do Menedżera debugowania sesji (SDM), gdy program jest dołączony do programu.

## <a name="syntax"></a>Składnia

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowi dostawca portu implementuje ten interfejs, aby zgłosić, że program został utworzony, zazwyczaj w czasie, gdy program jest dołączony. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa `QueryInterface` metody, aby uzyskać dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Niestandardowa dostawca portu tworzy i wysyła ten obiekt zdarzenia w celu raportowania tworzenia programu. Po wysłaniu tego zdarzenia za pomocą funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest on dołączony do debugowanego programu. Dostawca portu niestandardowego wysyła to zdarzenie przy użyciu interfejsu [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="remarks"></a>Uwagi
 Dostawca DE lub Custom Ports publikuje nowy interfejs [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) przez wywołanie [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
