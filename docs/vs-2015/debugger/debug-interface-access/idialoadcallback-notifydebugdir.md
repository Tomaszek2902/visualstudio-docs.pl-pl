---
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8fe8ffe9d7d495e40c8c84b08aeaefb03e8d17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151997"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wywoływana, gdy w pliku exe znaleziono katalog debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fExecutable`  
 [w] `TRUE` Jeśli katalog debugowania jest odczytywany z pliku wykonywalnego (a nie pliku. dbg).  
  
 `cbData`  
 podczas Liczba bajtów danych w katalogu debugowania.  
  
 `data[]`  
 podczas Tablica, która jest wypełniana katalogiem debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Kod powrotny jest zwykle ignorowany.  
  
## <a name="remarks"></a>Uwagi  
 Metoda [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) wywołuje to wywołanie zwrotne, gdy odnajdzie katalog debugowania podczas przetwarzania pliku wykonywalnego.  
  
 Ta metoda eliminuje konieczność odtwarzania pliku wykonywalnego i/lub debugowania przez klienta w celu obsługi informacji debugowania innych niż Znalezione w pliku. pdb. Za pomocą tych danych klient może rozpoznać typ dostępnych informacji debugowania i określić, czy znajduje się on w pliku wykonywalnym lub pliku. dbg.  
  
 Większość klientów nie będzie potrzebować tego wywołania zwrotnego, ponieważ `IDiaDataSource::loadDataForExe` Metoda w sposób przezroczysty otwiera zarówno pliki. pdb, jak i. dbg, gdy jest to niezbędne do obsłużynia symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
