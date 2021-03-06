---
title: IDebugParsedExpression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22069b8eedb06d67eafaf7333f379a057c1b6f23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725993"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje wyrażenie analizowane gotowe do oceny.

## <a name="syntax"></a>Składnia

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs, aby reprezentować wyrażenie analizowane, które jest gotowe do oceny.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie metody [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metodę `IDebugParsedExpression` .

|Metoda|Opis|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Szacuje przeanalizowane wyrażenie.|

## <a name="remarks"></a>Uwagi
 Gdy obiekt wywołujący jest gotowy do oceny wyrażenia, wywołuje [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , aby zwrócić [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który zawiera wynik oceny. To dwuczęściowe podejście do oceny, analizowanie i ocenianie, umożliwia Obliczanie wyrażenia przeanalizowanego wiele razy, pomijając czasochłonny proces analizowania wyrażenia.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Analizuj](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
