---
title: 'IDebugStackFrame2:: GetExpressionContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb1a075d04ed53fdbe2181975a56eddfcbc3b683
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719740"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Pobiera kontekst oceny dla oceny wyrażenia w bieżącym kontekście ramki stosu i wątku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>Parametry
`ppExprCxt`\
określoną Zwraca obiekt [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) , który reprezentuje kontekst oceny wyrażenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ogólnie rzecz biorąc, kontekst oceny wyrażenia może być uważany za zakres do wykonywania obliczeń wyrażeń. Wywołaj metodę [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , aby przeanalizować wyrażenie, a następnie Wywołaj wynikowe metody [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby obliczyć przeanalizowane wyrażenie.

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
