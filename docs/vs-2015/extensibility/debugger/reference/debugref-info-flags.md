---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05a073b3663ff85fe3d68878999aaf1dfa9e0017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198847"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jakie informacje mają być pobierane na temat obiektu odwołania debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DEBUGREF_INFO_NAME  
 Zainicjuj/Użyj `bstrName` pola w strukturze.  
  
 DEBUGREF_INFO_TYPE  
 Zainicjuj/Użyj `bstrType` pola w strukturze.  
  
 DEBUGREF_INFO_VALUE  
 Zainicjuj/Użyj `bstrValue` pola w strukturze.  
  
 DEBUGREF_INFO_ATTRIB  
 Zainicjuj/Użyj `dwAttrib` pola w strukturze.  
  
 DEBUGREF_INFO_REFTYPE  
 Zainicjuj/Użyj `dwRefType` pola w strukturze.  
  
 DEBUGREF_INFO_REF  
 Zainicjuj/Użyj `pReference` pola w strukturze.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 Pole Value powinno zawierać wartość autoexpanded (jeśli jest dostępna) dla tego typu obiektu.  
  
 DEBUGREF_INFO_NONE  
 Wskazuje, że flagi nie są ustawione.  
  
 DEBUGREF_INFO_ALL  
 Wskazuje maskę flag.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są przesyłane do metod [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) i [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) , aby wskazać, które pola struktury [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) mają być inicjowane.  
  
 Używane dla `dwFields` składowej struktury, `DEBUG_REFERENCE_INFO` Aby wskazać, które pola są używane i są ważne podczas zwracania struktury.  
  
 Te wartości mogą być połączone z bitową `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
