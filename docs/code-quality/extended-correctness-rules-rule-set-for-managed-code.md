---
title: Rozszerzony zestaw reguł poprawności dla zarządzanego kodu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 00295a8485fa80d2aa6cf1977e014b191b28ba7e
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658610"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Rozszerzony zestaw reguł poprawności dla zarządzanego kodu

Zestaw reguł poprawności rozszerzonej firmy Microsoft maksymalizuje błędy użycia logiki i struktury, które są raportowane przez analizę kodu. Dodatkowy nacisk jest umieszczany w określonych scenariuszach, takich jak współdziałanie COM i aplikacje mobilne. Należy rozważyć uwzględnienie tego zestawu reguł, jeśli jeden z tych scenariuszy ma zastosowanie do Twojego projektu lub aby znaleźć dodatkowe problemy w projekcie.

Zestaw reguł poprawnego rozszerzenia Microsoft Extended zawiera reguły, które znajdują się w podstawowym zestawie reguł [poprawności](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) , który zawiera reguły, które znajdują się w zestawie reguł [zarządzanych zalecanych reguł](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

W poniższej tabeli opisano wszystkie reguły w zestawie reguł poprawnych rozszerzonych firmy Microsoft.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1009](../code-quality/ca1009.md)|Poprawnie deklaruj procedury obsługi zdarzeń|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Oznacz zestawy atrybutem AssemblyVersion|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049.md)|Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Przenieś metody P/Invoke do klasy NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Nie ukrywaj metod klasy bazowej|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Poprawnie zaimplementuj interfejs IDisposable|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301.md)|Unikaj duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Elementy P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404.md)|Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody rejestracji modelu COM powinny mieć swoje odpowiedniki|
|[CA1415](../code-quality/ca1415.md)|Poprawnie zadeklaruj elementy P/Invoke|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Usuwaj puste finalizatory|
|[CA1900](../code-quality/ca1900.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901.md)|Deklaracje metody P/Invoke powinny być przenośne|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Określ kierowanie dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA|
|[CA2122](../code-quality/ca2122.md)|Nie ujawniaj pośrednio metod żądaniami LinkDemand|
|[CA2123](../code-quality/ca2123.md)|Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi|
|[CA2124](../code-quality/ca2124.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126.md)|Żądania LinkDemand dla typu wymagają żądań dziedziczenia|
|[CA2131](../code-quality/ca2131.md)|Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów|
|[CA2132](../code-quality/ca2132.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133.md)|Delegaci muszą być powiązani z metodami ze spójną przezroczystością|
|[CA2134](../code-quality/ca2134.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137.md)|Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni|
|[CA2138](../code-quality/ca2138.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń|
|[CA2141](../code-quality/ca2141.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe|
|[CA2147](../code-quality/ca2147.md)|Metody przezroczyste nie mogą używać asercji zabezpieczeń|
|[CA2149](../code-quality/ca2149.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Ponowie zgłoś wyjątek, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202.md)|Nie likwiduj obiektów wielokrotnie|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Pola statyczne typu wartości inicjuj bezpośrednio|
|[CA2212](../code-quality/ca2212.md)|Nie oznaczaj składników usługi atrybutem WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Pola możliwe do likwidacji należy likwidować|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Nie wywołuj w konstruktorach metod, które można przesłaniać|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Typy możliwe do likwidacji powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220.md)|Finalizatory powinny wywoływać finalizator klasy bazowej|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Zaimplementuj konstruktory serializacji|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Oznacz wszystkie pola nieprzeznaczone do serializacji|
|[CA2236](../code-quality/ca2236.md)|Wywołuj metody klasy bazowej dla typów ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Poprawnie implementuj metody serializacji|
|[CA2240](../code-quality/ca2240.md)|Poprawnie zaimplementuj interfejs ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Podaj poprawne argumenty metod formatowania|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Poprawnie testuj nie-liczby (NaN)|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Typy wyliczeniowe powinny mieć wartość zero|
|[CA1013](../code-quality/ca1013.md)|Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Nie przekazuj literałów jako zlokalizowanych parametrów|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizuj ciągi do postaci zapisanej wielkimi literami|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|Nie ignoruj wyników metod|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|Poprawnie wywołaj metodę GC.SuppressFinalize|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Właściwości nie powinny zwracać tablic|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testuj obecność pustych ciągów przy użyciu długości ciągu|
|[CA1903](../code-quality/ca1903.md)|Używaj tylko interfejsu API platformy docelowej|
|[CA2004](../code-quality/ca2004.md)|Usuń wywołania funkcji GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych|
|[CA2102](../code-quality/ca2102.md)|Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi|
|[CA2104](../code-quality/ca2104.md)|Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu|
|[CA2105](../code-quality/ca2105.md)|Pola tablicy nie powinny być tylko do odczytu|
|[CA2106](../code-quality/ca2106.md)|Zabezpiecz asercje|
|[CA2115](../code-quality/ca2115.md)|Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Pieczętuj metody, które spełniają wymagania interfejsów prywatnych|
|[CA2120](../code-quality/ca2120.md)|Zabezpiecz konstruktory serializacji|
|[CA2121](../code-quality/ca2121.md)|Konstruktory statyczne powinny być prywatne|
|[CA2130](../code-quality/ca2130.md)|Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste|
|[CA2205](../code-quality/ca2205.md)|Użyj zarządzanych odpowiedników funkcji API Win32|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Metody Dispose powinny wywoływać metodę Dispose klasy bazowej|
|[CA2221](../code-quality/ca2221.md)|Finalizatory powinny być chronione|
|[CA2222](../code-quality/ca2222.md)|Nie obniżaj dziedziczonej widoczności składowych|
|[CA2223](../code-quality/ca2223.md)|Składowe powinny różnić się nie tylko zwracanym typem|
|[CA2224](../code-quality/ca2224.md)|Przesłaniaj metodę equals w przypadku przeciążania operatora równości|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operatory powinny mieć symetryczne przeciążenia|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Właściwości kolekcji powinny być tylko do odczytu|
|[CA2239](../code-quality/ca2239.md)|Udostępnij metody deserializacji dla pól opcjonalnych|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Zaimplementuj standardowe konstruktory wyjątków|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Parametry identyfikatora URI nie powinny być ciągami|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Wartości zwracane identyfikatora URI nie powinny być ciągami|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Właściwości identyfikatora URI nie powinny być ciągami|
|[CA1057](../code-quality/ca1057.md)|Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri|
|[CA1402](../code-quality/ca1402.md)|Unikaj przeciążeń w interfejsach widocznych dla modelu COM|
|[CA1406](../code-quality/ca1406.md)|Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6|
|[CA1407](../code-quality/ca1407.md)|Unikaj statycznych składowych w typach widocznych dla modelu COM|
|[CA1408](../code-quality/ca1408.md)|Nie używaj wartości AutoDual elementu ClassInterfaceType|
|[CA1409](../code-quality/ca1409.md)|Typy widoczne dla modelu COM powinny mieć możliwość utworzenia|
|[CA1411](../code-quality/ca1411.md)|Metody rejestracji modelu COM nie powinny być widoczne|
|[CA1412](../code-quality/ca1412.md)|Oznacz interfejsy ComSource atrybutem IDispatch|
|[CA1413](../code-quality/ca1413.md)|Unikaj niepublicznych pól w typach wartości widocznych w modelu COM|
|[CA1414](../code-quality/ca1414.md)|Oznacz argumenty typu boolean elementu P/Invoke argumentem MarshalAs|
|[CA1600](../code-quality/ca1600.md)|Nie używaj priorytetu procesu o wartości Bezczynny|
|[CA1601](../code-quality/ca1601.md)|Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania|
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001.md)|Unikaj wywoływania problematycznych metod|
|[CA2003](../code-quality/ca2003.md)|Nie traktuj włókien jak wątków|
|[CA2135](../code-quality/ca2135.md)|Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand|
|[CA2136](../code-quality/ca2136.md)|Adnotacje przezroczystości składowych nie powinny powodować konfliktu|
|[CA2139](../code-quality/ca2139.md)|Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142.md)|Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand|
|[CA2143](../code-quality/ca2143.md)|Metody przezroczyste nie powinny używać żądań zabezpieczeń|
|[CA2144](../code-quality/ca2144.md)|Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych|
|[CA2145](../code-quality/ca2145.md)|Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|Pisownia literałów powinna być poprawna|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Pola niebędące stałymi nie powinny być widoczne|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Nie oznaczaj typów wyliczeniowych atrybutem Flags|
|[CA2218](../code-quality/ca2218.md)|Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Nie zgłaszaj wyjątków w klauzulach wyjątków|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Przeciążenia operatorów mają nazwane elementy alternatywne|
|[CA2228](../code-quality/ca2228.md)|Nie publikuj zasobów w formatach z wersji wstępnych|
|[CA2230](../code-quality/ca2230.md)|Użyj elementu params dla argumentów zmiennych|
|[CA2233](../code-quality/ca2233.md)|Operacje nie powinny powodować przepełnienia|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Przekazuj obiekty System.Uri zamiast ciągów|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|Analiza literałów ciągów atrybutów powinna przebiegać poprawnie|
