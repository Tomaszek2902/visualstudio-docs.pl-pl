---
title: 'IDebugEngineProgram2:: WatchForThreadStep | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59489af368c2e95a2d3cc93edbd6f7ab02a1c156
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195653"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Czujki do wykonania (lub przestaną być obserwowane na wykonanie) w danym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pOriginatingProgram`  
 podczas Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) reprezentujący wykonywany program.  
  
 `dwTid`  
 podczas Określa identyfikator wątku do obserwowania.  
  
 `fWatch`  
 podczas Wartość niezerowa ( `TRUE` ) oznacza rozpoczęcie oglądania w wątku identyfikowanym przez `dwTid` ; w przeciwnym razie zero ( `FALSE` ) oznacza zatrzymanie oglądania na `dwTid` .  
  
 `dwFrame`  
 podczas Określa indeks ramki, który kontroluje typ kroku. Jeśli wartość jest równa zero (0), typ kroku to "krok do", a program powinien zostać zatrzymany za każdym razem, gdy wątek identyfikowany przez `dwTid` wykonuje. Gdy `dwFrame` jest różna od zera, typ kroku to "krok od", a program powinien zatrzymać tylko wtedy, gdy wątek identyfikowany przez `dwTid` jest uruchomiony w ramce, której indeks jest równy lub większy na stosie niż `dwFrame` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy Menedżer debugowania sesji (SDM) uruchamia program, identyfikowany przez `pOriginatingProgram` parametr, powiadamia wszystkie inne dołączone programy przez wywołanie tej metody.  
  
 Ta metoda ma zastosowanie tylko do tego samego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
