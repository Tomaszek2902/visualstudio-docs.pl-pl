---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1b5cba13e439c69b3502b00c6ae159b6af28178
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153234"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa informacje, które mają zostać pobrane w przypadku awarii punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PERESI_BPRESLOCATION  
 Zainicjuj/Użyj `bpResLocation` pola (lokalizacja rozpoznawania punktów przerwania) struktury [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .  
  
 BPERESI_PROGRAM  
 Zainicjuj/Użyj `pProgram` pola `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_THREAD  
 Zainicjuj/Użyj `pThread` pola `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_MESSAGE  
 Zainicjuj/Użyj `bstrMessage` pola `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_TYPE  
 Zainicjuj/Użyj `dwType` pola (typ punktu przerwania) `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_ALLFIELDS  
 Inicjuj/używaj wszystkich pól `BP_ERROR_RESOLUTION_INFO` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Przekazuje jako parametr do metody [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) , aby wskazać, które pola struktury [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) mają być inicjowane.  
  
 Te wartości są również używane do wskazywania, które pola `BP_ERROR_RESOLUTION_INFO` struktury są używane i są prawidłowe podczas zwracania tej struktury.  
  
 Te wartości mogą być połączone z bitową `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
