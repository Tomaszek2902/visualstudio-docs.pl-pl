---
title: Operator kontekstu w debugerze (C++) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: aa16bd6f93198e5360139dbc5a6a0d96f02a1e41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62564707"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Operator kontekstu w debugerze programu Visual Studio (C++)
Operatora kontekstu w języku C++ można użyć do kwalifikowania lokalizacji punktu przerwania, nazwy zmiennej lub wyrażenia. Operator kontekstu jest przydatny do określania nazwy z zewnętrznego zakresu, który jest w inny sposób ukryty przez lokalną nazwę.

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Obowiązuje
 Istnieją dwa sposoby określania kontekstu:

1. {,, [*moduł*]} *wyrażenie*

     Nawiasy klamrowe muszą zawierać dwa przecinki i nazwę modułu (plik wykonywalny lub DLL) lub pełną ścieżkę.

     Na przykład, aby ustawić punkt przerwania w `SomeFunction` funkcji EXAMPLE.dll:

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *moduł*! *wyrażenie*

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *module* jest nazwą modułu. Możesz użyć pełnej ścieżki, aby odróżnić moduły o tej samej nazwie.

   Jeśli ścieżka *modułu* zawiera przecinek, spację osadzoną lub nawias klamrowy, należy użyć cudzysłowu wokół ścieżki, aby Analizator kontekstu mógł prawidłowo rozpoznać ciąg. Znaki pojedynczego cudzysłowu są uważane za część nazwy pliku systemu Windows, więc należy używać podwójnych cudzysłowów. Przykład:

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *wyrażenie* jest dowolnym prawidłowym wyrażeniem języka C++, które jest rozpoznawane jako prawidłowe miejsce docelowe, takie jak nazwa funkcji, nazwa zmiennej lub adres wskaźnika w *module*.

  Gdy ewaluatora wyrażeń napotka symbol w wyrażeniu, wyszukuje symbol w następującej kolejności:

1. Zakres leksykalny na zewnątrz, zaczynający się od bieżącego bloku, serii instrukcji ujętych w nawiasy klamrowe i kontynuowania na zewnątrz otaczającego bloku. Bieżący blok to kod zawierający bieżącą lokalizację, adres wskaźnika instrukcji.

2. Zakres funkcji. Bieżąca funkcja.

3. Zakres klasy, jeśli bieżąca lokalizacja znajduje się wewnątrz funkcji członkowskiej języka C++. Zakres klasy obejmuje wszystkie klasy bazowe. Ewaluatora wyrażeń używa normalnych reguł dominacji.

4. Symbole globalne w bieżącym module.

5. Symbole publiczne w bieżącym programie.