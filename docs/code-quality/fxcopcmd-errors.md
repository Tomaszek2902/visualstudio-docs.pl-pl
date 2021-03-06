---
title: błędy FxCopCmd
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b72f419331b2a02c55d885a2b8855070698879a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "78167614"
---
# <a name="fxcopcmd-tool-errors"></a>Błędy narzędzi plik FxCopCmd

Plik FxCopCmd nie uwzględnia wszystkich błędów jako krytycznych. Jeśli plik FxCopCmd ma wystarczające informacje do przeprowadzenia analizy częściowej, wykonuje analizę i zgłasza błędy, które wystąpiły. Kod błędu, który jest 32-bitową liczbą całkowitą, zawiera bitową kombinację wartości liczbowych, które odnoszą się do błędów.

W poniższej tabeli opisano kody błędów zwracane przez plik FxCopCmd:

|Błąd|Wartość liczbowa|
|-----------|-------------------|
|Brak błędów|0x0|
|Błąd analizy|0x1|
|Wyjątki reguł|0x2|
|Błąd ładowania projektu|0x4|
|Błąd ładowania zestawu|0x8|
|Błąd ładowania biblioteki reguł|0x10|
|Zaimportuj błąd ładowania raportu|0x20|
|Błąd danych wyjściowych|0x40|
|Błąd przełączania wiersza polecenia|0x80|
|Błąd inicjowania|0x100|
|Błąd odwołań do zestawu|0x200|
|BuildBreakingMessage|0x400|
|Nieznany błąd|0x1000000|

**Błąd analizy** jest zwracany w przypadku błędów krytycznych. Oznacza to, że analiza nie mogła zostać ukończona. Jeśli ma to zastosowanie, kod błędu zawiera również podstawową przyczynę błędu krytycznego. Poniższe warunki generują błędy krytyczne:

- Nie można wykonać analizy z powodu niewystarczających danych wejściowych.

- Analiza zgłosiła wyjątek, który nie jest obsługiwany przez plik FxCopCmd.

- Nie można znaleźć określonego pliku projektu lub jest on uszkodzony.

- Nie określono opcji Output lub nie można zapisać pliku.

> [!NOTE]
> Zestaw kodu powrotu plik FxCopCmd **odwołuje** się do błędu 0x200 przez siebie, jest to ostrzeżenie, a nie błąd. Ten kod powrotny wskazuje, że brakuje pośrednich odwołań, ale plik FxCopCmd mógł je obsłużyć. Ostrzeżenie oznacza, że istnieje możliwość, że niektóre wyniki analizy mogły zostać naruszone. Traktuj **błąd odwołania do zestawu** jako błąd, gdy jest on połączony z innym kodem zwrotnym.

## <a name="see-also"></a>Zobacz też

- [Błędy aplikacji analizy kodu](../code-quality/code-analysis-application-errors.md)
