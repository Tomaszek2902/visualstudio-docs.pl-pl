---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2674381992bd86f0144af103615f0a3922fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153575"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa styl warunku punktu przerwania dla oczekujących i powiązanych punktów przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BP_COND_NONE  
 Uruchamia punkt przerwania po osiągnięciu położenia punktu przerwania. Nie określono warunku punktu przerwania.  
  
 BP_COND_WHEN_TRUE  
 Uruchamia punkt przerwania tylko wtedy, gdy wyrażenie warunkowe skojarzone z punktem przerwania szacuje się na `true` .  
  
 BP_COND_WHEN_CHANGED  
 Uruchamia punkt przerwania tylko wtedy, gdy wartość wyrażenia warunkowego skojarzonego z punktem przerwania zmieniła się od poprzedniej wersji ewaluacyjnej.  
  
## <a name="remarks"></a>Uwagi  
 Używane dla `styleCondition` elementu członkowskiego struktury [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
