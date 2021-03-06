---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 04a8756fd7eb2a4b938ebcd2d5f4754509b704e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205222"
---
# <a name="module_info"></a>MODULE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Opisuje określony moduł (DLL, EXE lub Assembly).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```csharp  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwValidFields  
 Kombinacja flag z wyliczenia [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) , która określa, które pola są wypełniane.  
  
 m_bstrName  
 Nazwa modułu.  
  
 m_bstrUrl  
 Adres URL modułu.  
  
 m_bstrVersion  
 Wersja modułu.  
  
 m_bstrDebugMessage  
 Opcjonalna wiadomość dotycząca modułu, na przykład "symbole nie mogą zostać załadowane".  
  
 m_addrLoadAddress  
 Adres ładowania modułu.  
  
 m_addrPreferredLoadAddress  
 Preferowany adres ładowania modułu.  
  
 m_dwSize  
 Rozmiar modułu.  
  
 m_dwLoadOrder  
 Kolejność ładowania modułu.  
  
 m_TimeStamp  
 Godzina ostatniej modyfikacji pliku symboli.  
  
 m_bstrUrlSymbolLocation  
 Lokalizacja pliku symboli (na przykład ". \\ ") określonego w module. Używane jako początkowa lokalizacja do znajdowania symboli dla modułu.  
  
 m_dwModuleFlags  
 Kombinacja flag z wyliczenia [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) opisującego moduł.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przenoszona do metody [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) , w której jest wypełniana.  
  
 Ta struktura odnosi się do każdego modułu wymienionego w oknie **moduły** .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
