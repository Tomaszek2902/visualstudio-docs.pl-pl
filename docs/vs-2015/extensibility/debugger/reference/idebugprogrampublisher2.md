---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d49173a4c1f10be1544cf07b0b01640321d6d181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697297"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs umożliwia aparatowi debugowania (DE) lub dostawcom portów niestandardowych rejestrowanie programów na potrzeby debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio implementuje ten interfejs, aby zarejestrować debugowane programy, aby były widoczne dla debugowania w wielu procesach.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywoływanie `CoCreateInstance` funkcji com z `CLSID_ProgramPublisher` Aby uzyskać ten interfejs (Zobacz przykład). Niestandardowa dostawca portu używa tego interfejsu do rejestrowania węzłów programu, które reprezentują debugowane programy.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Sprawia, że węzeł programu jest dostępny dla algorytmu DEs i Menedżera debugowania sesji (SDM).|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Usuwa węzeł programu, dzięki czemu nie jest już dostępny.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Sprawia, że program jest dostępny dla algorytmu DEs i modelu SDM.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Usuwa program, aby nie był już dostępny.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Ustawia flagę wskazującą, że debuger jest obecny.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs sprawia, że programy i węzły programu są dostępne (czyli publikuje je) do użycia przez DEs i Menedżera debugowania sesji (SDM). Aby uzyskać dostęp do opublikowanych programów i węzłów programów, użyj interfejsu [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Jest to jedyny sposób, w jaki program Visual Studio może rozpoznać, że program jest debugowany.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak utworzyć wystąpienie wydawcy programu i zarejestrować węzeł programu. Jest to wykonywane z samouczka, [który publikuje węzeł Program](https://msdn.microsoft.com/d0100e02-4e2b-4e72-9e90-f7bc11777bae).  
  
```cpp#  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
