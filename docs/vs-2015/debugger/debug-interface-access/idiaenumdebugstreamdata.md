---
title: IDiaEnumDebugStreamData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 378fc75c3bd392f228ea30d1736f059e0def6d52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695893"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zapewnia dostęp do rekordów w strumieniu danych debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDiaEnumDebugStreamData` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Pobiera wersję [interfejsu IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) tego modułu wyliczającego.|  
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|Pobiera liczbę rekordów w strumieniu danych debugowania.|  
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|Pobiera nazwę strumienia danych debugowania.|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|Pobiera określony rekord.|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Pobiera określoną liczbę rekordów z kolejności wyliczanej.|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|Pomija określoną liczbę rekordów w wyliczonej kolejności.|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|Resetuje wyliczeniową sekwencję na początek.|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Tworzy moduł wyliczający zawierający taką samą sekwencję wyliczaną jak bieżący moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs reprezentuje strumień rekordów w strumieniu danych debugowania. Rozmiar i interpretacja każdego rekordu zależy od strumienia danych, z którego pochodzi rekord. Ten interfejs skutecznie zapewnia dostęp do nieprzetworzonych bajtów danych w pliku symboli.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj metodę [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) lub [IDiaEnumDebugStreams:: Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) , aby uzyskać `IDiaEnumDebugStreamData` obiekt.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak uzyskać dostęp do pojedynczego strumienia danych i jego rekordów.  
  
```cpp#  
void PrintStreamData(IDiaEnumDebugStreamData* pStream)  
{  
    BSTR  wszName;  
    LONG  dwElem;  
    ULONG celt    = 0;  
    DWORD cbData;  
    DWORD cbTotal = 0;  
    BYTE  data[1024];  
  
    if(pStream->get_name(&wszName) != S_OK)  
    {  
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");  
    }  
    else  
    {  
        wprintf_s(L"Stream: %s", wszName);  
        SysFreeString(wszName);  
    }  
    if(pStream->get_Count(&dwElem) != S_OK)  
    {  
        wprintf(L"ERROR - PrintStreamData() get_Count\n");  
    }  
    else  
    {  
        wprintf(L"(%d)\n", dwElem);  
    }  
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)  
    {  
        DWORD i;  
        for (i = 0; i < cbData; i++)  
        {  
            wprintf(L"%02X ", data[i]);  
            if(i && i % 8 == 7 && i+1 < cbData)  
            {  
                wprintf(L"- ");  
            }  
        }  
        wprintf(L"| ");  
        for(i = 0; i < cbData; i++)  
        {  
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');  
        }  
        wprintf(L"\n");  
        cbTotal += cbData;  
    }  
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",  
            cbTotal/dwElem, dwElem);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2. h  
  
 Biblioteka: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
