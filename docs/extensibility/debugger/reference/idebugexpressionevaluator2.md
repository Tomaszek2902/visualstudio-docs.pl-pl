---
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7041456bf0f3ae7930a73399d43dbf7cac6b3b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729141"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje rozszerzoną wersję ewaluatora wyrażeń (EE).

## <a name="syntax"></a>Składnia

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez ewaluatora wyrażeń.

## <a name="methods"></a>Metody
 Oprócz metod interfejsu [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Pobiera obiekt usługi z uwzględnieniem jego unikatowego identyfikatora.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Wstępne ładowanie modułów wyznaczonych przez określonego dostawcę symboli.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Umożliwia ewaluatora wyrażeń (EE) określenie interfejsu wywołania zwrotnego, który będzie używany przez aparat debugera (DE) do odczytu ustawień metryki.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Ustawia ścieżkę do środowiska uruchomieniowego języka wspólnego (CLR) załadowanego w debugerze.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Umożliwia aparatowi debugowania przekazywanie wywołania zwrotnego do ewaluatora wyrażeń podczas inicjacji.|
|[Zakończ](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Powoduje zatrzymanie i oczyszczenie ewaluatora wyrażeń.|

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
