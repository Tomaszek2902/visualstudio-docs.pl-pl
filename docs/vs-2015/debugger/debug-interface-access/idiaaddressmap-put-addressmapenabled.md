---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198684"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa, czy mapa adresów ma być używana do tłumaczenia adresów symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 podczas Ustaw `TRUE` , aby włączyć tłumaczenie symboli lub `FALSE` wyłączyć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wykonywalne przetwórcy czasami aktualizują plik wykonywalny. DIA zawiera mechanizm do obsługi tłumaczenia symboli do nowego układu.  
  
 Po załadowaniu pliku PDB Mapa adresów przechowywana w pliku jest włączona. Istnieją jednak przypadki, gdy aplikacja kliencka może wymagać dostarczenia własnej mapy adresów przez wywołanie metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Jeśli metoda zakończy `set_addressMap` się pomyślnie, aplikacja kliencka musi wywołać `put_addressMapEnabled` metodę z `NewVal` parametrem, `TRUE` Aby umożliwić korzystanie z tej mapy adresów.  
  
 Bieżący stan włączonego mapowania adresów można pobrać z wywołaniem metody [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
