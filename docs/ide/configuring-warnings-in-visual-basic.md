---
title: 'Konfigurowanie ostrzeżeń w Visual Basic:'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33302a4a686d80621cc64ee018371a2d03ea30ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114730"
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurowanie ostrzeżeń w Visual Basic

[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Kompilator zawiera zestaw ostrzeżeń dotyczących kodu, który może spowodować błędy w czasie wykonywania. Te informacje służą do pisania oczyszczarki, szybszego i lepszego kodu z mniejszą liczbą błędów. Na przykład kompilator generuje ostrzeżenie, gdy użytkownik próbuje wywołać element członkowski zmiennej nieprzypisanego obiektu, zwrócić z funkcji bez ustawienia wartości zwracanej lub wykonać `Try` blok z błędami w logice, aby przechwytywać wyjątki.

Czasami kompilator oferuje dodatkową logikę w imieniu użytkownika, dzięki czemu użytkownik może skupić się na zadaniu w stanie, a nie na przewidywaniu ewentualnych błędów. W poprzednich wersjach programu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] **opcja Strict** została użyta w celu ograniczenia dodatkowej logiki [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zapewnianej przez kompilator. Skonfigurowanie ostrzeżeń pozwala ograniczyć tę logikę w bardziej szczegółowy sposób, na poziomie poszczególnych ostrzeżeń.

Możesz chcieć dostosować projekt i wyłączyć niektóre ostrzeżenia, które nie są związane z aplikacją, przy jednoczesnym wyłączaniu innych ostrzeżeń do błędów. Na tej stronie wyjaśniono, jak włączyć i wyłączyć poszczególne ostrzeżenia.

## <a name="turning-warnings-off-and-on"></a>Wyłączanie i włączanie ostrzeżeń
Istnieją dwa różne sposoby konfigurowania ostrzeżeń: można je skonfigurować za pomocą **projektanta projektu**lub można użyć opcji kompilatora **/warnaserror** i **/nowarn** .

Karta **kompilacja** na stronie **Projektant projektu** umożliwia włączanie i wyłączanie ostrzeżeń. Zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia** , aby wyłączyć wszystkie ostrzeżenia; Wybierz pozycję **Traktuj wszystkie ostrzeżenia jako błędy** , aby traktować wszystkie ostrzeżenia jako błędy. Niektóre poszczególne ostrzeżenia mogą być przełączane jako błąd lub ostrzeżenie zgodnie z potrzebami w wyświetlonej tabeli.

Jeśli **opcja Strict** jest ustawiona na **off**, nie można niezależnie traktować **opcji Option Strict** pokrewnych ostrzeżeń. Gdy **opcja Strict** jest ustawiona na wartość **on**, skojarzone ostrzeżenia są traktowane jako błędy, niezależnie od ich stanu. Jeśli **opcja Strict** jest ustawiona na wartość **Custom** przez określenie `/optionstrict:custom` w kompilatorze wiersza polecenia, **Opcje rygorystyczne** ostrzeżenia mogą być włączane lub wyłączane niezależnie.

Opcja wiersza polecenia **/warnaserror** kompilatora może również służyć do określenia, czy ostrzeżenia są traktowane jako błędy. Można dodać listę rozdzielaną przecinkami do tej opcji, aby określić, które ostrzeżenia mają być traktowane jako błędy lub ostrzeżenia przy użyciu + lub-. Poniższa tabela zawiera szczegółowe informacje o możliwych opcjach.

|Opcja wiersza polecenia|Określa|
| - |---------------|
|`/warnaserror+`|Traktuj wszystkie ostrzeżenia jako błędy|
|`/warnsaserror`-|Nie Traktuj jako ostrzeżeń jako błędy. Jest to opcja domyślna.|
|`/warnaserror+:<warning list` `>`|Traktuj określone ostrzeżenia jako błędy, wymienione przez ich numer identyfikatora błędu na liście rozdzielanej przecinkami.|
|`/warnaserror-:<warning list>`|Nie Traktuj określonych ostrzeżeń jako błędów, które są wyświetlane na podstawie ich identyfikatora błędu na liście rozdzielanej przecinkami.|
|`/nowarn`|Nie zgłaszaj ostrzeżeń.|
|`/nowarn:<warning list>`|Nie zgłaszaj określonych ostrzeżeń, które są wyświetlane w postaci listy rozdzielanej przecinkami.|

Lista ostrzeżeń zawiera numery identyfikatorów błędów ostrzeżeń, które powinny być traktowane jako błędy, które mogą być używane z opcjami wiersza polecenia do włączania lub wyłączania określonych ostrzeżeń. Jeśli lista ostrzeżeń zawiera nieprawidłową liczbę, zostanie zgłoszony błąd.

## <a name="examples"></a>Przykłady
Ta tabela przykładów argumentów wiersza polecenia opisuje działanie każdego z argumentów.

|Argument|Opis|
|--------------|-----------------|
|`vbc /warnaserror`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|
|`vbc /warnaserror:42024`|Określa, że ostrzeżenie 42024 powinno być traktowane jako błąd.|
|`vbc /warnaserror:42024,42025`|Określa, że ostrzeżenia 42024 i 42025 powinny być traktowane jako błędy.|
|`vbc /nowarn`|Określa, że nie mają być raportowane ostrzeżenia.|
|`vbc /nowarn:42024`|Określa, że ostrzeżenie 42024 nie powinno być zgłaszane.|
|`vbc /nowarn:42024,42025`|Określa, że ostrzeżenia 42024 i 42025 nie powinny być zgłaszane.|

## <a name="types-of-warnings"></a>Typy ostrzeżeń
Poniżej znajduje się lista ostrzeżeń, które warto traktować jako błędy.

### <a name="implicit-conversion-warning"></a>Ostrzeżenie o niejawnej konwersji
Generowane dla wystąpień niejawnej konwersji. Nie zawierają one niejawnych konwersji z wewnętrznego typu liczbowego do ciągu podczas korzystania z `&` operatora. Wartość domyślna dla nowych projektów jest wyłączona.

IDENTYFIKATOR: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Ostrzeżenie wywołania metody z późnym wiązaniem i rozpoznawania przeciążenia
Wygenerowano dla wystąpień późnego wiązania. Wartość domyślna dla nowych projektów jest wyłączona.

IDENTYFIKATOR: 42017

### <a name="operands-of-type-object-warnings"></a>Argumenty operacji typu "Object"
Generowane, gdy wystąpią operandy typu `Object` , które spowodują utworzenie błędu z **opcją Strict dla**. Wartość domyślna dla nowych projektów jest włączona.

ID: 42018 i 42019

### <a name="declarations-require-as-clause-warnings"></a>Deklaracje wymagają ostrzeżeń klauzuli "As"
Generowane, gdy w deklaracji zmiennej, funkcji lub właściwości brakuje klauzuli, `As` Wystąpił błąd z **ustawieniem Strict On**. Przyjmuje się, że zmienne, które nie mają przypisanego typu, są typu `Object` . Wartość domyślna dla nowych projektów jest włączona.

ID: 42020 (Deklaracja zmiennej), 42021 (deklaracja funkcji) i 42022 (Deklaracja właściwości).

### <a name="possible-null-reference-exception-warnings"></a>Możliwe ostrzeżenia wyjątku odwołania o wartości null
Generowane, gdy zmienna jest używana, zanim zostanie do niej przypisana wartość. Wartość domyślna dla nowych projektów jest włączona.

IDENTYFIKATOR: 42104, 42030

### <a name="unused-local-variable-warning"></a>Ostrzeżenie dotyczące nieużywanej zmiennej lokalnej
Generowane, gdy zmienna lokalna jest zadeklarowana, ale nigdy nie jest określana. Wartość domyślna to on.

IDENTYFIKATOR: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Ostrzeżenie o dostępie udostępnionego elementu członkowskiego za poorednictwem zmiennej wystąpienia
Generowane podczas uzyskiwania dostępu do udostępnionej składowej za pomocą wystąpienia mogą mieć skutki uboczne lub podczas uzyskiwania dostępu do udostępnionej składowej za pomocą zmiennej wystąpienia nie jest prawą stroną wyrażenia lub jest przekazywany jako parametr. Wartość domyślna dla nowych projektów jest włączona.

IDENTYFIKATOR: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Cykliczne ostrzeżenia operatora lub dostępu do właściwości
Generowane, gdy treść procedury używa tego samego operatora lub właściwości, który jest zdefiniowany w. Wartość domyślna dla nowych projektów jest włączona.

ID: 42004 (operator), 42026 (Właściwość)

### <a name="function-or-operator-without-return-value-warning"></a>Ostrzeżenie funkcji lub operatora bez wartości zwracanej
Generowane, gdy funkcja lub operator nie ma określonej wartości zwracanej. Obejmuje pomijanie `Set` do niejawnej zmiennej lokalnej o takiej samej nazwie jak funkcja. Wartość domyślna dla nowych projektów jest włączona.

ID: 42105 (funkcja), 42016 (operator)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modyfikator przeciążenia użyty w ostrzeżeniu modułu
Generowane `Overloads` , gdy jest używany w `Module` . Wartość domyślna dla nowych projektów jest włączona.

IDENTYFIKATOR: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Zduplikowane lub nakładające się ostrzeżenia dotyczące bloków catch
Generowane, gdy `Catch` blok nigdy nie został osiągnięty ze względu na jego relację z innymi `Catch` zdefiniowanymi blokami. Wartość domyślna dla nowych projektów jest włączona.

IDENTYFIKATOR: 42029, 42031

## <a name="see-also"></a>Zobacz też

- [Typy błędów](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Spróbuj... Catch... Finally — instrukcja](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Strona kompilowania, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Domyślnie wyłączone ostrzeżenia kompilatora](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
