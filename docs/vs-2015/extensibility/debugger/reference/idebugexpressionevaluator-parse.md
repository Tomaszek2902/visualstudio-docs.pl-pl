---
title: IDebugExpressionEvaluator::P arse | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4039534b139eeeaf20f938c6d6c358c602f96227
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155342"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda konwertuje ciąg wyrażenia na wyrażenie analizowane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `upstrExpression`  
 podczas Ciąg wyrażenia, który ma zostać przeanalizowany.  
  
 `dwFlags`  
 podczas Kolekcja stałych [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) , które określają, w jaki sposób wyrażenie ma być analizowane.  
  
 `nRadix`  
 podczas Podstawy do interpretowania wszelkich informacji numerycznych.  
  
 `pbstrError`  
 określoną Zwraca błąd jako tekst czytelny dla człowieka.  
  
 `pichError`  
 określoną Zwraca pozycję znaku początku błędu w ciągu wyrażenia.  
  
 `ppParsedExpression`  
 określoną Zwraca przeanalizowane wyrażenie w obiekcie [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda generuje wyrażenie analizowane, a nie wartość rzeczywistą. Wyrażenie analizowane jest gotowe do obliczenia, czyli jest konwertowane na wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
