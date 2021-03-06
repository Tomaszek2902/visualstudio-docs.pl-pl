---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e7bb6b014ef8aa662abd42ab2989d47f703880a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685968"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest używany przez aparat debugowania (DE) do wysyłania komunikatu do programu Visual Studio, który wymaga odpowiedzi od użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Usuń implementację tego interfejsu, aby wysłać komunikat do programu Visual Studio, który wymaga odpowiedzi użytkownika. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.  
  
 Implementacja tego interfejsu musi komunikować się z wywołaniem metody [Setresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) programu Visual Studio. Można na przykład wykonać tę czynność z komunikatem ogłoszonym w wątku obsługi komunikatów, lub obiekt implementujący ten interfejs może przechowywać odwołanie do DE i wywoływać z powrotem z odpowiedzią przekazaną do `IDebugMessageEvent2::SetResponse` .  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Element DE tworzy i wysyła ten obiekt Event, aby wyświetlić komunikat, który wymaga odpowiedzi. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugMessageEvent2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Pobiera komunikat do wyświetlenia.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Ustawia odpowiedź (jeśli istnieje) w oknie komunikatu.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja DE użyje tego interfejsu, jeśli wymaga określonej odpowiedzi od użytkownika w przypadku konkretnej wiadomości. Na przykład jeśli komunikat "odmowa dostępu" zostanie wyświetlony po próbie zdalnego dołączenia do programu, komunikat ten zostanie wysłany do programu Visual Studio w ramach `IDebugMessageEvent2` zdarzenia z stylem okna komunikatu `MB_RETRYCANCEL` . Pozwala to użytkownikowi na ponawianie próby lub anulowanie operacji dołączania.  
  
 DE określa sposób obsługi tego komunikatu przez konwencje funkcji Win32 `MessageBox` (zobacz [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) , aby uzyskać szczegółowe informacje).  
  
 Użyj interfejsu [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) , aby wysyłać komunikaty do programu Visual Studio, które nie wymagają odpowiedzi od użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
