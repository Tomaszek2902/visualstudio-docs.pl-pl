---
title: 'IDebugReference2:: Compare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 41b183baa00f86c7a6e54d35b6188cd8c04946b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182494"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Porównuje jedno odwołanie z drugim. Zarezerwowane do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```csharp  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCompare`  
 podczas Wartość z wyliczenia [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) , która określa operacje porównania, na przykład równe, mniejsze niż lub większe niż.  
  
 `pReference`  
 podczas Obiekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) reprezentujący odwołanie, które ma zostać porównane z.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
