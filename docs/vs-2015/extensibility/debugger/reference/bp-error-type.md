---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2317fafe410cacfca1c77b669a54669ea6e2224a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153534"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa typ błędu punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPET_NONE  
 Określa błąd punktu przerwania.  
  
 BPET_TYPE_WARNING  
 Określa błąd punktu przerwania stylu ostrzeżenia.  
  
 BPET_TYPE_ERROR  
 Określa błąd punktu przerwania w stylu błędu.  
  
 BPET_SEV_HIGH  
 Określa błąd punktu przerwania o wysokiej ważności.  
  
 BPET_SEV_GENERAL  
 Określa błąd punktu przerwania o średniej ważności.  
  
 BPET_SEV_LOW  
 Określa błąd punktu przerwania o niskiej ważności.  
  
 BPET_TYPE_MASK  
 Określa błąd punktu przerwania stylu maski.  
  
 BPET_SEV_MASK  
 Określa błąd punktu przerwania w stylu z maską ważności.  
  
 BPET_GENERAL_WARNING  
 Określa błąd punktu przerwania w stylu ogólnym ostrzeżenia.  
  
 BPET_GENERAL_ERROR  
 Określa błąd punktu przerwania z ogólnym stylem błędu.  
  
 BPET_ALL  
 Określa wszystkie typy błędów punktów przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości mogą być połączone z bitową `OR` i używane dla `dwType` elementu członkowskiego struktury [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) . Przekazanie jako parametr do metody [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .  
  
 Typ błędu punktu przerwania składa się z typu i ważności. Oznacza to, że typ błędu punktu przerwania nigdy nie jest tylko typem (na przykład, `BPET_TYPE_ERROR` ) lub ważności (na przykład `BPET_SEV_GENERAL` ). `BPET_GENERAL_WARNING` i `BPET_GENERAL_ERROR` Podaj wstępnie zdefiniowane wartości dla ogólnych ostrzeżeń i punktów przerwania błędów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
