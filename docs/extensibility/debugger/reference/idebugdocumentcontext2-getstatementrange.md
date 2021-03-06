---
title: 'IDebugDocumentContext2:: GetStatementRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731770"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Pobiera zakres instrukcji pliku dla kontekstu dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
    TEXT_POSITION[] pBegPosition,
    TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametry
`pBegPosition`\
[in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana początkową pozycją. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.

`pEndPosition`\
[in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana pozycją końcową. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Zakres instrukcji jest zakresem wierszy, które tworzą kod, do którego odwołuje się ten kontekst dokumentu.

Aby uzyskać zakres kodu źródłowego (łącznie z komentarzami) w tym kontekście dokumentu, wywołaj metodę [GetSourceRange —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) .

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CDebugContext` obiektu, który uwidacznia Interfejs [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) . Ten przykład wypełnia pozycję końcową tylko wtedy, gdy pozycja początkowa nie jest wartością null.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
