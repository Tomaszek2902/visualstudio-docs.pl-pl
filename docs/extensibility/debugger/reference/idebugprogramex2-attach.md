---
title: 'IDebugProgramEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722381"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Dołącz sesję do programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
podczas Obiekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , który reprezentuje funkcję wywołania zwrotnego, do której dołączony aparat debugowania wysyła zdarzenia.

`dwReason`\
podczas Wartość z wyliczenia [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) opisująca przyczynę operacji Attach.

`pSession`\
podczas Wartość, która jednoznacznie identyfikuje sesję dołączoną do programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Ta metoda powinna zostać zwrócona `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` , jeśli program jest już dołączony.

## <a name="remarks"></a>Uwagi
 Port, który zawiera program, może korzystać z wartości w `pSession` celu określenia sesji, która ma zostać dołączona do programu. Na przykład jeśli port umożliwia dołączenie do procesu tylko jednej sesji debugowania, port może określić, czy ta sama sesja jest już dołączona do innych programów w procesie.

> [!NOTE]
> Przekazany Interfejs `pSession` ma być traktowany tylko jako plik cookie, czyli wartość, która jednoznacznie identyfikuje Menedżera debugowania sesji dołączenia do tego programu; żadna z metod w interfejsie nie jest funkcjonalna.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
