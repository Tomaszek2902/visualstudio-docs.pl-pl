---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204799"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jakie informacje o wątku mają być pobierane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 TPF_ID  
 Zainicjuj/Użyj `dwThreadId` pola struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
 TPF_SUSPENDCOUNT  
 Zainicjuj/Użyj `dwSuspendCount` pola `THREADPROPERTIE` struktury S.  
  
 TPF_STATE  
 Zainicjuj/Użyj `dwThreadState` pola `THREADPROPERTIE` struktury S.  
  
 TPF_PRIORITY  
 Zainicjuj/Użyj `bstrPriority` pola `THREADPROPERTIE` struktury S.  
  
 TPF_NAME  
 Zainicjuj/Użyj `bstrName` pola `THREADPROPERTIE` struktury S.  
  
 TPF_LOCATION  
 Zainicjuj/Użyj `bstrLocation` pola `THREADPROPERTIE` struktury S.  
  
 TPF_ALLFIELDS  
 Określa wszystkie pola.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przesyłane jako argument do metody [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) , aby wskazać, które pola struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) mają być inicjowane.  
  
 Te wartości są również używane w `dwFields` składowej `THREADPROPERTIES` struktury, aby wskazać, które pola są używane i są prawidłowe.  
  
 Flagi te mogą być połączone z bitową `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
