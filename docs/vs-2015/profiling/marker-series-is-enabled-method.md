---
title: 'marker_series:: is_enabled Metoda | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ccef8ebbf63835a71027643b518280d5f4f867b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156413"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled — Metoda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy dowolna sesja włączyła dostawcę.  
  
## <a name="syntax"></a>Składnia  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Importance`  
 Poziom ważności.  
  
 `_Category`  
 Kategorii.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj. h  
  
 **Przestrzeń nazw:** Współbieżność::d przesła  
  
## <a name="see-also"></a>Zobacz też  
 [marker_series — Klasa](../profiling/marker-series-class.md)
