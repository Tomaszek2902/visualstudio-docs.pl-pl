---
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 054cfc305400e3916ed7ba796a74370dfc2c77a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386696"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Powoduje, że proces przechodzi krok po kroku jedną instrukcję lub instrukcję.

> [!NOTE]
> Ta metoda powinna być używana zamiast [kroku](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Składnia

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Parametry
`pThread`\
podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) reprezentujący poddany wątek.

`sk`\
podczas Jedna z wartości [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .

`step`\
podczas Jedna z wartości [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W przypadku każdej synchronizacji wątków lub komunikacji między wątkami inne wątki w procesie powinny być uruchamiane, gdy określony wątek działa.

 **Ostrzeżenie** Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
