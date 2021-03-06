---
title: 'IDiaStackWalker:: getEnumFrames2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25090ae66d28ebd9eb62f62f14979de1e82c5302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144722"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera moduł wyliczający ramek stosu dla określonego typu platformy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpuid`  
 podczas Wartość z wyliczenia [CV_CPU_TYPE_e wyliczeniem](../../debugger/debug-interface-access/cv-cpu-type-e.md) określająca typ platformy.  
  
 `pHelper`  
 podczas Obiekt pomocnika [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .  
  
 `ppEnum`  
 określoną Zwraca obiekt [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) zawierający listę obiektów [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać listę ramek stosu tylko dla platformy x86, wywołaj metodę [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV_CPU_TYPE_e, Wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
