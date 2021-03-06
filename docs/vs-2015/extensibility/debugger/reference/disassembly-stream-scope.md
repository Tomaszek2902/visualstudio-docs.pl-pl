---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0132aad5ad6e37e7bb811693afde7ebfe80b272d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198834"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa zakres strumienia demontażu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DSS_HUGE  
 Określa, że rozmontowanie kontekstu kodu spowoduje wygenerowanie większej ilości danych wyjściowych niż klient zazwyczaj chce pobrać w jednym wywołaniu.  
  
 DSS_FUNCTION  
 Określa, że funkcja zawarty w kontekście kodu powinna być rozmieszczona. Określa, że strumień demontażu reprezentuje funkcję zwracaną przez metodę [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .  
  
 DSS_MODULE  
 W przypadku zwrócenia przez `IDebugDisassemblyStream2::GetScope` metodę, określa, że strumień demontażu reprezentuje moduł.  
  
 DSS_ALL  
 Określa odzbiór dla całej przestrzeni adresowej.  
  
## <a name="remarks"></a>Uwagi  
 Przekazana jako argument do metody [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) i zwracany przez metodę [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .  
  
 Te wartości mogą być połączone z bitową `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
