---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737595"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Określa informacje do pobrania dotyczące kontekstu pamięci.

## <a name="syntax"></a>Składnia

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Pola
`CIF_MODULEURL`\
Zainicjuj/Użyj `bstrModuleUrl` pola struktury [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) .

`CIF_FUNCTION`\
Zainicjuj/Użyj `bstrFunction` pola `CONTEXT_INFO` struktury.

`CIF_FUNCTIONOFFSET`\
Zainicjuj/Użyj `posFunctionOffset` pola `CONTEXT_INFO` struktury.

`CIF_ADDRESS`\
Zainicjuj/Użyj `bstrAddress` pola `CONTEXT_INFO` struktury.

`CIF_ADDRESSOFFSET`\
Zainicjuj/Użyj `bstrAddressOffset` pola `CONTEXT_INFO` struktury.

`CIF_ALLFIELDS`\
Inicjuj/używaj wszystkich pól `CONTEXT_INFO` struktury.

## <a name="remarks"></a>Uwagi
Te wartości są przekazywane do metody [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) , aby wskazać, które pola struktury [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) mają być inicjowane.

Te flagi są również używane do wskazywania, które pola `CONTEXT_INFO` struktury są używane i są prawidłowe podczas zwracania struktury.

Te wartości mogą być połączone z bitowym lub.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
