---
title: IDebugQueryEngine2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f80e8b44326cb082c8f6428365bad2575c317da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673952"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugQueryEngine2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugqueryengine2).  
  
Ten interfejs umożliwia sesji debugowania manager (SDM) pobrać interfejs, który reprezentuje aparat debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs na obiektach, które implementują najpopularniejsze interfejsy DE (takie jak [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), i [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) w Aby zezwolić na dostęp do [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejsu DE, sam.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) w typowym interfejsie DE uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugQueryEngine2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Pobiera interfejs aparatu (DE) niestandardowe debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle implementowany w obiekcie, który implementuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejs w celu zapewnienia obsługi uporządkowane przyczynowości krokowego wykonywania funkcji, czyli gdy debuger jest przechodzenie z funkcji, dalej funkcję do wykonania, nie może być poprzedniej funkcji na stosie, ale funkcja w innym wątku całkowicie. Aby uzyskać pełną definicję "przyczynowości", zobacz [słownik debugera w usłudze Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
