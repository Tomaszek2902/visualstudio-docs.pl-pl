---
title: 'IEnumDebugObjects:: Clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Clone
helpviewer_keywords:
- IEnumDebugObjects::Clone method
ms.assetid: cb7df109-d29a-4218-b900-6809091459dd
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40d4c11aa40467b707a7d780478e7a0579d83a2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160959"
---
# <a name="ienumdebugobjectsclone"></a>IEnumDebugObjects::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 określoną Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopia wyliczenia ma taki sam stan jak oryginał w momencie wywołania tej metody. Jednak kopia i stan pierwotny są oddzielone i mogą być zmieniane indywidualnie.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
