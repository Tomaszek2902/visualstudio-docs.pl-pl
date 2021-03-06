---
title: Znajdź błąd wywołania podczas wywoływania funkcji wiele razy
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de3d186b7800efc3e807e3f775b48d91b44072b4
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810487"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Skąd wiadomo, gdy funkcja jest wywoływana setki razy, które wywołanie nie powiodło się?
## <a name="problem-description"></a>Opis problemu
 Wystąpił błąd mojego programu w wywołaniu określonej funkcji `CnvtV` . Program prawdopodobnie wywołuje tę funkcję przez parę setek razy przed niepowodzeniem. Jeśli ustawiłem punkt przerwania lokalizacji na `CnvtV` , program zatrzyma się na każdym wywołaniu tej funkcji i nie chcę. Nie wiem, jakie warunki powodują Niepowodzenie wywołania, więc nie można ustawić warunkowego punktu przerwania. Co mogę zrobić?

## <a name="solution"></a>Rozwiązanie
 Możesz ustawić punkt przerwania dla funkcji z polem **Count liczby trafień** na wartość tak, aby była ona nigdy nieosiągalna. W tym przypadku, ponieważ sądzisz, że funkcja `CnvtV` jest wywoływana przez parę setek razy, można ustawić **liczbę trafień** na 1000 lub więcej. Następnie uruchom program i poczekaj, aż wywołanie zakończy się niepowodzeniem. Gdy to się nie powiedzie, Otwórz okno punkty przerwania i sprawdź listę punktów przerwania. Ustawiony punkt przerwania `CnvtV` jest wyświetlany, po którym następuje liczba trafień i liczba pozostałych iteracji:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Teraz wiesz, że w wywołaniu 101st nie powiodła się funkcja. Jeśli zresetujesz punkt przerwania z liczbą trafień 101 i ponownie uruchomisz program, program zatrzyma się w wywołaniu `CnvtV` , które spowodowało niepowodzenie.

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego — Często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Ustawianie punktów przerwania](/previous-versions/ktf38f66(v=vs.100))
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)