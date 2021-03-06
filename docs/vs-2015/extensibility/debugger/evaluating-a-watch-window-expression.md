---
title: Ocenianie wyrażenia okna czujki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f13573cfecbd81f36e3b77e9b23beeaa558c08dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820420"
---
# <a name="evaluating-a-watch-window-expression"></a>Ocenianie wyrażenia okna wyrażeń kontrolnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Po wstrzymaniu wykonywania program Visual Studio wywołuje aparat debugowania (DE), aby określić bieżącą wartość każdego wyrażenia na liście obserwowanych elementów. Polecenie DE oblicza każde wyrażenie przy użyciu ewaluatora wyrażeń (EE), a program Visual Studio wyświetla jego wartość w oknie **czujki** .  
  
 Poniżej przedstawiono omówienie sposobu oceniania wyrażenia listy obserwowanych elementów:  
  
1. Program Visual Studio wywołuje [GETEXPRESSIONCONTEXT](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) de, aby uzyskać kontekst wyrażenia, którego można użyć do obliczenia wyrażeń.  
  
2. Dla każdego wyrażenia na liście czujki program Visual Studio wywołuje [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , aby przekonwertować tekst wyrażenia na przeanalizowane wyrażenie.  
  
3. `IDebugExpressionContext2::ParseText` wywołania [analizują](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) w celu wykonania rzeczywistej pracy analizy tekstu i utworzenia obiektu [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
4. `IDebugExpressionContext2::ParseText` Tworzy obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) i umieszcza `IDebugParsedExpression` w nim obiekt. Ten `DebugExpression2` obiekt jest następnie zwracany do programu Visual Studio.  
  
5. Program Visual Studio wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , aby obliczyć przeanalizowane wyrażenie.  
  
6. `IDebugExpression2::EvaluateSync` przekazuje wywołanie [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , aby wykonać rzeczywistą ocenę i utworzyć obiekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który jest zwracany do programu Visual Studio.  
  
7. Program Visual Studio wywołuje [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , aby uzyskać wartość wyrażenia, które jest wyświetlane na liście obserwowanych elementów.  
  
## <a name="parse-then-evaluate"></a>Analizuj i Szacuj  
 Ponieważ analizowanie złożonego wyrażenia może trwać znacznie dłużej niż ocenianie, proces oceny wyrażenia jest podzielony na dwa kroki: 1) analizowanie wyrażenia i 2) ocenianie przeanalizowanego wyrażenia. W ten sposób Ocena może wystąpić wiele razy, ale wyrażenie musi być analizowane tylko raz. Pośrednie wyrażenie analizowane jest zwracane z EE w obiekcie [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) , który jest z kolei przyhermetyzowane i zwracane z elementu de jako obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpression`Obiekt uwzględnia wszystkie oceny do `IDebugParsedExpression` obiektu.  
  
> [!NOTE]
> Nie jest konieczne, aby EE była zgodna z tym dwuetapowym procesem, mimo że program Visual Studio zakłada to; EE można analizować i testować w tym samym kroku, gdy [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) jest wywoływana (na przykład jak działa przykład mycee). Jeśli Twój język może tworzyć złożone wyrażenia, możesz chcieć oddzielić krok Analizuj od kroku oceny. Może to zwiększyć wydajność w debugerze programu Visual Studio, gdy jest wyświetlanych wiele wyrażeń Czujka.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykład implementacji oceny wyrażenia](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Używa przykładu MyCEE, aby przejść przez proces obliczania wyrażenia.  
  
 [Ocenianie wyrażenia kontrolnego](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Wyjaśnia, co dzieje się po pomyślnym przeanalizowaniu wyrażenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Dostarcza argumenty, które są przesyłane, gdy aparat debugowania (DE) wywołuje ewaluatora wyrażeń (EE).  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
