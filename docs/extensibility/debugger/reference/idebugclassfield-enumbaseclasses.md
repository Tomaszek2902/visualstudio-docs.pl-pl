---
title: 'IDebugClassField:: EnumBaseClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734476"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Tworzy moduł wyliczający dla klas bazowych tej klasy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\

określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę klas bazowych. Zwraca wartość null, jeśli nie ma klas bazowych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK, zwraca S_SH_NO_BASE_CLASSES, jeśli nie ma klas bazowych (a `ppEnum` parametr ma ustawioną wartość null); w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Klasy bazowe w obiekcie Enumerator są określone w kolejności najbardziej bezpośredniej (lub najbardziej pochodnej) klasy bazowej do najbardziej zdalnej klasy podstawowej. Na przykład, uwzględniając klasy języka C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Wyliczenie zwróci klasy bazowe w kolejności `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
