---
title: 'IDiaSession:: getEnumTables | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b9b229de3818b00379d95a5c19e35c7e83c845e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465427"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Pobiera moduł wyliczający dla wszystkich tabel znajdujących się w magazynie symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parametry
`ppEnumTables`

określoną Zwraca obiekt [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) . Użyj tego interfejsu, aby wyliczyć tabele w magazynie symboli.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Ten przykład przedstawia ogólną funkcję, która używa `getEnumTables` metody do uzyskania określonego obiektu modułu wyliczającego. W przypadku znalezienia modułu wyliczającego funkcja zwraca wskaźnik, który można rzutować na żądany interfejs; w przeciwnym razie funkcja zwraca wartość `NULL` .

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
