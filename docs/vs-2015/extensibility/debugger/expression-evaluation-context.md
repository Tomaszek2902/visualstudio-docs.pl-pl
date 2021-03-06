---
title: Kontekst oceny wyrażenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377609cb9f971b667872c198a53b45a6288f2c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152779"
---
# <a name="expression-evaluation-context"></a>Kontekst oceny wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowaniu **kontekst oceny wyrażenia**:  
  
- Reprezentuje kontekst oceny wyrażenia. Ogólnie rzecz biorąc, kontekst oceny odnosi się do zakresu leksykalnego, w którym można ocenić zmienne, parametry, funkcje i metody. Na przykład kontekst oceny wyrażenia skojarzonego z ramką stosu zapewni kontekst do oceny zmiennych lokalnych, parametrów metody i elementów członkowskich klasy (jeśli dotyczy).  
  
- Istnieje, gdy program został zatrzymany w punkcie przerwania. Samo wyrażenie jest strukturą danych reprezentującą przeanalizowane wyrażenie, które jest gotowe do powiązania i oceny w danym kontekście.  
  
     W bardziej szczegółowym przypadku wyrażenia są tworzone przy użyciu metody [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . Gdy wyrażenie jest oceniane, generuje ciąg drukowalny zawierający nazwę i typ zmiennej lub argumentu oraz jego wartość. Ten ciąg jest wyświetlany w okno wyrażeń kontrolnych lub w oknie zmiennych środowiska IDE.  
  
     Za pomocą `BSTR` i interfejsu [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) aparat debugowania (de) może utworzyć interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) przez analizowanie wyrażenia. `IDebugExpression2`Za pomocą interfejsu, można uzyskać wartość przez obliczenie wyrażenia synchronicznego lub asynchronicznego. Ta wartość oraz nazwa i typ zmiennej lub argumentu są wysyłane do IDE w celu wyświetlenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażeń](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
