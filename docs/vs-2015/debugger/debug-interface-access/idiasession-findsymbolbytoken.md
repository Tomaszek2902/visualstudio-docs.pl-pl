---
title: 'IDiaSession:: findSymbolByToken | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByToken method
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d42be946db927603412670d30e2f4c9a1cab43fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144775"
---
# <a name="idiasessionfindsymbolbytoken"></a>IDiaSession::findSymbolByToken
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera symbol zawierający określony token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findSymbolByToken (   
   ULONG        token,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `token`  
 podczas Określa token.  
  
 `symtag`  
 podczas Typ symbolu, który ma zostać znaleziony. Wartości są pobierane z wyliczenia [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje pobrany symbol.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
