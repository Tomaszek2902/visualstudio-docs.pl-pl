---
title: 'IDebugPointerObject:: SetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725499"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Ustawia wartość wskazywaną przez serię kolejnych bajtów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parametry
`dwStart`\
podczas Przesunięcie w bajtach od początku obiektu wskazywanego przez.

`dwCount`\
podczas Liczba bajtów do ustawienia.

`pBytes`\
podczas Tablica bajtów reprezentująca nową wartość. Ta wartość jest przechowywana w obiekcie, rozpoczynając od danego przesunięcia.

`pdwBytes`\
określoną Zwraca liczbę rzeczywiście ustawionych bajtów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana, jeśli wskaźnik reprezentowany przez ten [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) wskazuje na typ pierwotny lub prostą tablicę typów pierwotnych (czyli tablicę, która może być reprezentowana przez prostą sekwencję bajtów). Ten `IDebugPointerObject` obiekt nie może być odwołaniem o wartości null (musi wskazywać na adres w pamięci).

## <a name="see-also"></a>Zobacz też
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
