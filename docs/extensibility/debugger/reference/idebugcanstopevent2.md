---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734508"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Ten interfejs jest używany do poproszenia Menedżera debugowania sesji (SDM) o tym, czy ma zostać zatrzymana w bieżącej lokalizacji kodu.

## <a name="syntax"></a>Składnia

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby obsługiwać krokowe przechodzenie przez kod źródłowy. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs (model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu).

 Implementacja tego interfejsu musi komunikować się z wywołaniem [zatrzymywania](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) modelu SDM w aparacie debugowania. Można na przykład wykonać tę czynność z komunikatem ogłoszonym w wątku obsługi komunikatów w aparacie debugowania lub obiekt implementujący ten interfejs może przechowywać odwołanie do aparatu debugowania i wywoływać z powrotem do aparatu debugowania z flagą przekazaną do `IDebugCanStopEvent2::CanStop` .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Właściwość DE może wysyłać tę metodę za każdym razem, gdy nie zostanie wyświetlony monit o kontynuowanie wykonywania, a destopniowe przechodzenie przez kod. To zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugCanStopEvent2` .

|Metoda|Opis|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Pobiera przyczynę tego zdarzenia.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Określa, czy debugowany program powinien zostać zatrzymany w lokalizacji tego zdarzenia (i wysłać Zdarzenie opisujące powód zatrzymywania), czy tylko kontynuować wykonywanie.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Pobiera kontekst dokumentu opisujący lokalizację tego zdarzenia.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Pobiera kontekst kodu opisujący lokalizację tego zdarzenia.|

## <a name="remarks"></a>Uwagi
 Program ANULUJe wysyłanie tego interfejsu, jeśli użytkownik przeprowadzi procedurę do funkcji, a nie odnajdzie informacji debugowania tam, gdzie nie istnieje lub informacje debugowania istnieją, ale nie wiadomo, czy można wyświetlić kod źródłowy dla tej lokalizacji.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
