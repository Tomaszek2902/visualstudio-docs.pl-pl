---
title: Funkcja SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700584"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled, funkcja
Ta funkcja sprawdza, czy wtyczka do kontroli źródła zezwala na wiele wyewidencjonowania pliku.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametry
 pContext

podczas Struktura kontekstu wtyczki kontroli źródła.

 pbMultiCheckout

określoną Określa, czy dla tego projektu włączono wiele wyewidencjonowania (wartość nierówna oznacza, że obsługiwane są wiele wyewidencjonowania).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Sprawdzenie zakończyło się pomyślnie.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 IDE wykonuje dwie testy, aby określić, czy pliki mogą być wyewidencjonowane jednocześnie przez więcej niż jednego użytkownika. Po pierwsze system kontroli źródła musi obsługiwać wiele wyewidencjonowania. Wtyczka do kontroli źródła może określić tę możliwość podczas inicjowania, określając `SCC_CAP_MULTICHECKOUT` . Następnie jako drugie sprawdzenie, IDE wywołuje tę funkcję, aby określić, czy bieżący projekt obsługuje wiele wyewidencjonowania. Jeśli dla wybranego projektu są obsługiwane wiele wyewidencjonowania, Wtyczka zwraca kod sukcesu i ustawia `pbMultiCheckout` wartość różną od zera ( `TRUE` ) lub `FALSE` .

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
