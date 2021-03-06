---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97a38b4296668cb287f34e5b1afcbd7c90477011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153210"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wylicza prawidłowe wartości określające pobieranie informacji o żądaniu punktu przerwania. To Wyliczenie rozszerza [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Wyliczenie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 BPREQI90_BPLOCATION  
 Zainicjuj lub Użyj `bpLocation` pola (Lokalizacja punktu przerwania) struktury [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 BPREQI90_LANGUAGE  
 Zainicjuj lub Użyj `guidLanguage` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_PROGRAM  
 Zainicjuj lub Użyj `pProgram` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_PROGRAMNAME  
 Zainicjuj lub Użyj `bstrProgramName` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_THREAD  
 Zainicjuj lub Użyj `pThread` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_THREADNAME  
 Zainicjuj lub Użyj `bstrThreadName` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_PASSCOUNT  
 Zainicjuj lub Użyj `bpPassCount` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_CONDITION  
 Zainicjuj lub Użyj `bpCondition` pola (warunek punktu przerwania) `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_FLAGS  
 Zainicjuj lub Użyj `dwFlags` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.  
  
 BPREQI90_ALLOLDFIELDS  
 Zainicjuj lub użyj wszystkich pól dla `BP_REQUEST_INFO` struktury.  
  
 BPREQI90_VENDOR  
 Zainicjuj lub Użyj `guidVendor` pola `BP_REQUEST_INFO2` struktury.  
  
 BPREQI90_CONSTRAINT  
 Zainicjuj lub Użyj `bstrConstraint` pola `BP_REQUEST_INFO2` struktury.  
  
 BPREQI90_TRACEPOINT  
 Zainicjuj lub Użyj `bstrTracepoint` pola `BP_REQUEST_INFO2` struktury.  
  
 BPREQI90_MACROTRACEPOINT  
 Zainicjuj lub Użyj `bstrMacroTracepoint` pola `BP_REQUEST_INFO2` struktury. BPREQI_ALLFIELDS nie zawiera tego pola.  
  
 BPREQI90_ALLFIELDS  
 Określa wszystkie pola `BP_REQUEST_INFO2` struktury.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg90. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
