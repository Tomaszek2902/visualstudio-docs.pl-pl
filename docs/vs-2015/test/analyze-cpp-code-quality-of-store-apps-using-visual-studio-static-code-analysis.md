---
title: Aplikacje ze sklepu ze statycznymi analizami kodu C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native.express
ms.assetid: c5355e43-a37c-4686-a969-18e3dfc59a9c
caps.latest.revision: 15
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c20fe8bccdf48cf307dda72a085b3c2a72f1d0cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672710"
---
# <a name="analyze-c-code-quality-of-store-apps-using-visual-studio-static-code-analysis"></a>Analizowanie jakości kodu C++ aplikacji ze sklepu przy użyciu statycznej analizy kodu programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Narzędzie do analizy kodu w wersjach programu Visual Studio Express analizuje swój kod w celu uzyskania zestawu typowych problemów i naruszeń dobrych rozwiązań programistycznych. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń kompilatora, ponieważ analiza kodu wyszukuje określone wzorce kodu, które są prawidłowe, ale mogą nadal tworzyć problemy dla Ciebie lub innych osób korzystających z Twojego kodu. Analiza kodu może również znaleźć wady w kodzie, które trudno wykryć poprzez testowanie. Uruchamianie narzędzia do analizy kodu w regularnych odstępach czasu w procesie tworzenia oprogramowania może zwiększyć jakość ukończonej aplikacji.

> [!NOTE]
> W Visual Studio Ultimate, Visual Studio Premium i Visual Studio Professional można użyć pełnej funkcjonalności narzędzi do analizy kodu. Zobacz [Analizowanie jakości aplikacji za pomocą narzędzi do analizy kodu](https://msdn.microsoft.com/library/dd264897.aspx) w bibliotece MSDN.

## <a name="running-code-analysis"></a><a name="BKMK_Run"></a> Uruchamianie analizy kodu
 Aby uruchomić analizę kodu w rozwiązaniu programu Visual Studio:

- W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w rozwiązaniu**.

  Aby automatycznie uruchomić analizę kodu przy każdej kompilacji projektu:

1. Wybierz nazwę projektu w Eksplorator rozwiązań a następnie wybierz **Właściwości**.

2. Na stronie właściwości projektu wybierz pozycję **Analiza kodu** , a następnie wybierz pozycję **Włącz analizę kodu C/C++ podczas kompilacji**.

   Rozwiązanie jest kompilowane i zostanie uruchomiona Analiza kodu. Wyniki pojawiają się w oknie Analiza kodu.

   ![Okno analizy kodu](../test/media/ca-cpp-collapsed.png "CA_CPP_Collapsed")

## <a name="analyzing-and-resolving-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu
 Aby przeanalizować określone ostrzeżenie, wybierz tytuł ostrzeżenia w oknie Analiza kodu. Ostrzeżenie zostanie rozwinięte, aby wyświetlić szczegółowe informacje o problemie. Gdy jest to możliwe, analizy kodu wyświetlają numer wiersza i logikę analizy, które doprowadziły do ostrzeżenia.

 ![Ostrzeżenie o rozszerzonej analizie kodu](../test/media/ca-cpp-expanded-callout.png "CA_CPP_Expanded_Callout")

 Po rozszerzeniu ostrzeżenia wiersze kodu, które spowodowały ostrzeżenie, są wyróżnione w edytorze kodu programu Visual Studio.

 ![Wyróżniony kod źródłowy](../test/media/ca-cpp-sourceline.png "CA_CPP_SourceLine")

 Po zrozumieniu problemu można go rozwiązać w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie pojawia się już w oknie Analiza kodu i że poprawka nie wywołała nowych ostrzeżeń.

> [!TIP]
> Możesz ponownie uruchomić analizę kodu z okna Analiza kodu. Wybierz przycisk **Analizuj** , a następnie wybierz zakres analizy. Możesz ponownie uruchomić analizę całego rozwiązania lub w wybranym projekcie.

## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Pomijanie ostrzeżeń analizy kodu
 Istnieją przypadki, w których można zrezygnować z naprawienia ostrzeżenia analizy kodu. Użytkownik może zdecydować, że rozwiązanie tego problemu wymaga zbyt dużo ponownego kodowania w odniesieniu do prawdopodobieństwa, że problem będzie występował w jakiejkolwiek rzeczywistej implementacji kodu. Można też zastanowić się, że analiza, która jest używana w ostrzeżeniu, jest nieodpowiedni dla danego kontekstu. Możesz pominąć poszczególne ostrzeżenia, aby nie były wyświetlane w oknie Analiza kodu.

 Aby pominąć ostrzeżenie:

1. Jeśli szczegółowe informacje nie są wyświetlane, rozwiń tytuł ostrzeżenia.

2. Wybierz łącze **Akcje** u dołu ostrzeżenia.

3. Wybierz, aby **pominąć komunikat** , a następnie wybierz pozycję **w polu Źródło**.

   Pominięcie komunikatu powoduje wstawienie `#pragma(warning:` *WarningId* `)` , który pomija Ostrzeżenie dla wiersza kodu.

## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Wyszukiwanie i filtrowanie wyników analizy kodu
 Można wyszukiwać długie listy komunikatów ostrzegawczych i filtrować ostrzeżenia w rozwiązaniach w ramach projektu.

 ![Wyszukiwanie i filtrowanie okna Analiza kodu](../test/media/ca-searchfilter.png "CA_SearchFilter")

## <a name="c-code-analysis-warnings"></a><a name="Warnings"></a> Ostrzeżenia analizy kodu w języku C++
 Analiza kodu wywołuje następujące ostrzeżenia dla kodu C++:

|                                      Reguła                                      |                                                  Opis                                                  |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
|                       [C6001](../code-quality/c6001.md)                        |                                          Używanie niezainicjowanej pamięci                                           |
|                       [C6011](../code-quality/c6011.md)                        |                                          Wyłuskanie wskaźnika o wartości null                                           |
|                       [C6029](../code-quality/c6029.md)                        |                                            Użycie niesprawdzonej wartości                                             |
|                       [C6053](../code-quality/c6053.md)                        |                                          Zakończenie zerowe od wywołania                                           |
|                       [C6059](../code-quality/c6059.md)                        |                                               Złe łączenie                                               |
|                       [C6063](../code-quality/c6063.md)                        |                                  Brak argumentu ciągu do funkcji formatowania                                   |
|                       [C6064](../code-quality/c6064.md)                        |                                  Brak argumentu typu Integer dla funkcji formatowania                                  |
|                       [C6066](../code-quality/c6066.md)                        |                                  Brak argumentu wskaźnika dla funkcji formatowania                                  |
|                       [C6067](../code-quality/c6067.md)                        |                              Brak argumentu wskaźnika ciągu do funkcji formatowania                               |
|                       [C6101](../code-quality/c6101.md)                        |                                        Zwracanie niezainicjowanej pamięci                                         |
|                       [C6200](../code-quality/c6200.md)                        |                                         Indeks przekracza maksymalny rozmiar buforu                                          |
|                       [C6201](../code-quality/c6201.md)                        |                                      Indeks przekracza maksymalną wartość buforu stosu                                       |
|                       [C6270](../code-quality/c6270.md)                        |                                   Brak argumentu zmiennoprzecinkowego do funkcji formatowania                                   |
|                       [C6271](../code-quality/c6271.md)                        |                                       Dodatkowy argument funkcji formatowania                                       |
|                       [C6272](../code-quality/c6272.md)                        |                                     Argument inny niż zmiennoprzecinkowy do formatowania funkcji                                     |
|                       [C6273](../code-quality/c6273.md)                        |                                    Argument niebędący liczbą całkowitą do sformatowania funkcji                                     |
|                       [C6274](../code-quality/c6274.md)                        |                                   Argument niebędący znakiem do funkcji formatowania                                   |
|                       [C6276](../code-quality/c6276.md)                        |                                              Nieprawidłowe rzutowanie ciągu                                              |
|                       [C6277](../code-quality/c6277.md)                        |                                          Nieprawidłowe wywołanie metody CreateProcess                                           |
|                       [C6284](../code-quality/c6284.md)                        |                                  Nieprawidłowy argument obiektu dla funkcji formatowania                                   |
|                       [C6290](../code-quality/c6290.md)                        |                                      Niestandardowa koniunkcja logiczna                                       |
|                       [C6291](../code-quality/c6291.md)                        |                                       Niestandardowa koniunkcja logiczna                                       |
|                       [C6302](../code-quality/c6302.md)                        |                             Nieprawidłowy argument ciągu znaków dla funkcji formatowania                              |
|                       [C6303](../code-quality/c6303.md)                        |                           Nieprawidłowy argument ciągu znaków dwubajtowych do funkcji formatowania                           |
|                       [C6305](../code-quality/c6305.md)                        |                                         Użycie niedopasowanego rozmiaru i liczby                                         |
|                       [C6306](../code-quality/c6306.md)                        |                                   Nieprawidłowe wywołanie funkcji zmiennej argumentu                                   |
|                       [C6328](../code-quality/c6328.md)                        |                                       Niezgodność typu argumentu potencjalnego                                        |
|                       [C6385](../code-quality/c6385.md)                        |                                                 Przepełnienie odczytu                                                  |
|                       [C6386](../code-quality/c6386.md)                        |                                                 Przepełnienie zapisu                                                 |
|                       [C6387](../code-quality/c6387.md)                        |                                            Nieprawidłowa wartość parametru                                            |
|                       [C6500](../code-quality/c6500.md)                        |                                          Nieprawidłowa właściwość atrybutu                                           |
|                       [C6501](../code-quality/c6501.md)                        |                                     Sprzeczne wartości właściwości atrybutów                                     |
|                       [C6503](../code-quality/c6503.md)                        |                                           Odwołania nie mogą być puste                                           |
|                       [C6504](../code-quality/c6504.md)                        |                                              Wartość zerowa przy niewskaźniku                                              |
|                       [C6505](../code-quality/c6505.md)                        |                                               MustCheck na void                                               |
|                       [C6506](../code-quality/c6506.md)                        |                                      Rozmiar buforu dla elementu nie będącego wskaźnikiem lub tablicą                                      |
| [C6507](https://msdn.microsoft.com/18f88cd1-d035-4403-a6a4-12dd0affcf21)        |                                       Niezgodność wartości null przy wyzerowaniu odwołania                                       |
|                       [C6508](../code-quality/c6508.md)                        |                                           Dostęp do zapisu dla stałej                                            |
|                       [C6509](../code-quality/c6509.md)                        |                                          Return użyty w warunku wstępnym                                          |
|                       [C6510](../code-quality/c6510.md)                        |                                        Przerwano wartość null dla niebędącego wskaźnikiem                                         |
|                       [C6511](../code-quality/c6511.md)                        |                                          MustCheck musi mieć wartość yes lub No                                          |
|                       [C6513](../code-quality/c6513.md)                        |                                       Rozmiar elementu bez rozmiaru buforu                                        |
|                       [C6514](../code-quality/c6514.md)                        |                                        Rozmiar buforu przekracza rozmiar tablicy                                         |
|                       [C6515](../code-quality/c6515.md)                        |                                          Rozmiar buforu dla elementu nie będącego wskaźnikiem                                           |
|                       [C6516](../code-quality/c6516.md)                        |                                          Brak właściwości dla atrybutu                                           |
|                       [C6517](../code-quality/c6517.md)                        |                                       Prawidłowy rozmiar dla bufora bez możliwości odczytu                                       |
|                       [C6518](../code-quality/c6518.md)                        |                                     Rozmiar zapisywalny bufora bez możliwości zapisu                                      |
| [C6521](https://msdn.microsoft.com/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)  |                                        Nieprawidłowe odwołanie do ciągu rozmiaru                                        |
|                       [C6522](../code-quality/c6522.md)                        |                                           Nieprawidłowy typ ciągu rozmiaru                                            |
| [C6523](https://msdn.microsoft.com/11397a31-b224-46b0-afb7-d49ca576a3bb)  |                                         Nieprawidłowy parametr ciągu rozmiaru                                         |
|                       [C6525](../code-quality/c6525.md)                        |                                   Nieprawidłowy ciąg rozmiaru nieosiągalnej lokalizacji                                    |
| [C6526](https://msdn.microsoft.com/59c590c7-0098-4166-a1ac-87f324596002)  |                                        Nieprawidłowy typ buforu ciągu rozmiaru                                        |
|                       [C6527](../code-quality/c6527.md)                        |              Nieprawidłowa Adnotacja: Właściwość "NeedsRelease" nie może być użyta dla wartości typu void               |
|                       [C6530](../code-quality/c6530.md)                        |                                       Nierozpoznany styl ciągu formatu                                        |
|                       [C6540](../code-quality/c6540.md)                        | Użycie adnotacji atrybutów dla tej funkcji spowoduje unieważnienie wszystkich istniejących adnotacji __declspec  |
|                       [C6551](../code-quality/c6551.md)                        |                              Nieprawidłowa specyfikacja rozmiaru: nie przeanalizować wyrażenia                              |
|                       [C6552](../code-quality/c6552.md)                        |                              Nieprawidłowe DEREF = lub Notref =: nie możliwy do przeanalizowania wyrażenia                               |
|                       [C6701](../code-quality/c6701.md)                        |                                  Wartość nie jest prawidłową wartością tak/nie/może                                  |
|                       [C6702](../code-quality/c6702.md)                        |                                        Wartość nie jest wartością ciągu.                                        |
|                       [C6703](../code-quality/c6703.md)                        |                                           Wartość nie jest liczbą                                           |
|                       [C6704](../code-quality/c6704.md)                        |                                    Nieoczekiwany błąd wyrażenia adnotacji                                     |
|                       [C6705](../code-quality/c6705.md)                        |     Oczekiwana liczba argumentów adnotacji jest niezgodna z rzeczywistą liczbą argumentów dla adnotacji      |
|                       [C6706](../code-quality/c6706.md)                        |                                  Nieoczekiwany błąd adnotacji dla adnotacji                                   |
|                      [C28021](../code-quality/c28021.md)                       |                                Parametr, którego typem jest adnotacja, musi być wskaźnikiem                                |
|                      [C28182](../code-quality/c28182.md)                       |         Wyłuskanie wskaźnika o wartości NULL. Wskaźnik zawiera taką samą wartość NULL jak inny wskaźnik.          |
|                      [C28202](../code-quality/c28202.md)                       |                                    Niedozwolone odwołanie do niestatycznej składowej                                     |
|                      [C28203](../code-quality/c28203.md)                       |                                     Niejednoznaczne odwołanie do składowej klasy.                                      |
|                      [C28205](../code-quality/c28205.md)                       |                           \_Powodzenie \_ lub \_ On_failure \_ używane w niedozwolonym kontekście                            |
|                      [C28206](../code-quality/c28206.md)                       |                                   Lewy argument operacji wskazuje na strukturę, użyj "->"                                   |
|                      [C28207](../code-quality/c28207.md)                       |                                       Lewy argument operacji jest strukturą, użyj "."                                       |
|                      [C28210](../code-quality/c28210.md)                       |                 Adnotacje dla kontekstu __on_failure nie mogą być w jawnym kontekście wstępnym                  |
|                      [C28211](../code-quality/c28211.md)                       |                                 Oczekiwano nazwy kontekstu statycznego dla SAL_context                                  |
|                      [C28212](../code-quality/c28212.md)                       |                                  Oczekiwano wyrażenia wskaźnika dla adnotacji                                   |
|                      [C28213](../code-quality/c28213.md)                       | \_ \_ Adnotacja Use_decl_annotations musi być używana do odwoływania się, bez modyfikacji, wcześniejszej deklaracji. |
|                      [C28214](../code-quality/c28214.md)                       |                                   Nazwy parametrów atrybutu muszą być P1... P9                                   |
|                      [C28215](../code-quality/c28215.md)                       |                    Nie można zastosować typefix do parametru, który ma już typefix                    |
|                      [C28216](../code-quality/c28216.md)                       |        Adnotacja Checkreturn dotyczy ma zastosowanie tylko do warunki końcowe dla określonego parametru funkcji.         |
|                      [C28217](../code-quality/c28217.md)                       |            W przypadku funkcji liczba parametrów do adnotacji jest niezgodna z znalezionymi w pliku             |
|                      [C28218](../code-quality/c28218.md)                       |             Dla parametru funkcji parametr adnotacji nie jest zgodny z znalezionym w pliku              |
|                      [C28219](../code-quality/c28219.md)                       |                 Oczekiwano składowej wyliczenia dla adnotacji, parametr w adnotacji                 |
|                      [C28220](../code-quality/c28220.md)                       |                  Oczekiwano wyrażenia liczby całkowitej dla adnotacji, parametr w adnotacji                   |
|                      [C28221](../code-quality/c28221.md)                       |                        Oczekiwano wyrażenia ciągu dla parametru w adnotacji                         |
|                      [C28222](../code-quality/c28222.md)                       |                               \_oczekiwano __yes, _NO lub \_ _maybe dla adnotacji                               |
|                      [C28223](../code-quality/c28223.md)                       |                       Nie znaleziono oczekiwanego tokenu/identyfikatora dla adnotacji, parametr                        |
|                      [C28224](../code-quality/c28224.md)                       |                                        Adnotacja wymaga parametrów                                         |
|                      [C28225](../code-quality/c28225.md)                       |                     Nie znaleziono poprawnej liczby wymaganych parametrów w adnotacji                      |
|                      [C28226](../code-quality/c28226.md)                       |                          Adnotacja nie może być PrimOp (w bieżącej deklaracji)                          |
|                      [C28227](../code-quality/c28227.md)                       |                          Adnotacja nie może być PrimOp (patrz wcześniejsza deklaracja)                           |
|                      [C28228](../code-quality/c28228.md)                       |                             Parametr adnotacji: nie można użyć typu w adnotacjach                              |
|                      [C28229](../code-quality/c28229.md)                       |                                    Adnotacja nie obsługuje parametrów                                     |
|                      [C28230](../code-quality/c28230.md)                       |                                     Typ parametru nie ma składowej.                                      |
|                      [C28231](../code-quality/c28231.md)                       |                                       Adnotacja jest prawidłowa tylko na tablicy                                       |
|                      [C28232](../code-quality/c28232.md)                       |                               pre, post lub DEREF nie zostały zastosowane do żadnej adnotacji                               |
|                      [C28233](../code-quality/c28233.md)                       |                                    pre, post lub DEREF zastosowany do bloku                                     |
|                      [C28234](../code-quality/c28234.md)                       |                              wyrażenie __at nie ma zastosowania do bieżącej funkcji                               |
|                      [C28235](../code-quality/c28235.md)                       |                               Funkcja nie może być autonomiczna jako adnotacja                                |
|                      [C28236](../code-quality/c28236.md)                       |                                Nie można użyć adnotacji w wyrażeniu                                 |
|                      [C28237](../code-quality/c28237.md)                       |                              Adnotacja w parametrze nie jest już obsługiwana                               |
|                      [C28238](../code-quality/c28238.md)                       |      Adnotacja dla parametru ma więcej niż jedną wartość, stringValue i longValue. Użyj paramn = XXX       |
|                      [C28239](../code-quality/c28239.md)                       |  Adnotacja dla parametru ma wartość Value, stringValue lub longValue; i paramn = xxx. Używaj tylko paramn = XXX   |
|                      [C28240](../code-quality/c28240.md)                       |                             Adnotacja dla parametru ma Param2, ale nie param1                              |
|                      [C28241](../code-quality/c28241.md)                       |                          Nie rozpoznano adnotacji dla funkcji w parametrze                           |
|                      [C28243](../code-quality/c28243.md)                       |   Adnotacja dla funkcji dla parametru wymaga większej liczby odniesień, niż pozwala na to rzeczywisty typ z adnotacją   |
|                      [C28245](../code-quality/c28245.md)                       |                     Adnotacja dla funkcji zawiera adnotacje "This" dla funkcji nie będącej składową                     |
|                      [C28246](../code-quality/c28246.md)                       |                Adnotacja parametru funkcji jest niezgodna z typem parametru                 |
|                      [C28250](../code-quality/c28250.md)                       |                    Niespójna adnotacja dla funkcji: poprzednie wystąpienie zawiera błąd.                     |
|                      [C28251](../code-quality/c28251.md)                       |                       Niespójna adnotacja dla funkcji: to wystąpienie zawiera błąd.                       |
|                      [C28252](../code-quality/c28252.md)                       |           Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.           |
|                      [C28253](../code-quality/c28253.md)                       |           Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.           |
|                      [C28254](../code-quality/c28254.md)                       |                               dynamic_cast<> () nie jest obsługiwane w adnotacjach                                |
|                      [C28262](../code-quality/c28262.md)                       |                    Znaleziono błąd składniowy w adnotacji w funkcji dla adnotacji                     |
|                      [C28263](../code-quality/c28263.md)                       |                 Znaleziono błąd składni w adnotacji warunkowej dla wewnętrznej adnotacji                 |
|                      [C28267](../code-quality/c28267.md)                       |                    W adnotacji znaleziono błąd składni w funkcji.                    |
|                      [C28272](../code-quality/c28272.md)                       |      Adnotacja dla funkcji, parametr podczas badania, jest niespójna z deklaracją funkcji      |
|                      [C28273](../code-quality/c28273.md)                       |                    W przypadku funkcji wskazówki są niespójne z deklaracją funkcji                     |
|                      [C28275](../code-quality/c28275.md)                       |                                   Parametr do \_ Macro_value \_ ma wartość null                                    |
|                      [C28279](../code-quality/c28279.md)                       |                           Dla symbolu znaleziono "BEGIN" bez odpowiadającego mu "End"                            |
|                      [C28280](../code-quality/c28280.md)                       |                           Dla symbolu znaleziono element "End" bez odpowiadającego mu elementu "BEGIN                           |
|                      [C28282](../code-quality/c28282.md)                       |                                    Ciągi formatu muszą znajdować się w warunkach wstępnych                                    |
|                      [C28285](../code-quality/c28285.md)                       |                                    Dla funkcji, błąd składni w parametrze                                    |
|                      [C28286](../code-quality/c28286.md)                       |                                    Dla funkcji, błąd składniowy blisko końca                                    |
|                      [C28287](../code-quality/c28287.md)                       |                Dla funkcji, błąd składni w \_ elemencie \_ adnotacji at () (Nierozpoznana Nazwa parametru)                |
|                      [C28288](../code-quality/c28288.md)                       |                  Dla funkcji, błąd składni w \_ elemencie \_ Annotation () (Nieprawidłowa nazwa parametru)                   |
|                      [C28289](../code-quality/c28289.md)                       |                Dla funkcji: ReadableTo lub WritableTo nie ma specyfikacji limitu jako parametru                |
|                      [C28290](../code-quality/c28290.md)                       |           Adnotacja dla funkcji zawiera więcej elementów zewnętrznych niż rzeczywista liczba parametrów            |
|                      [C28291](../code-quality/c28291.md)                       |                        wpis o wartości null/notnull na poziomie DEREF 0 jest bezużyteczne dla funkcji.                        |
|                      [C28300](../code-quality/c28300.md)                       |                            Operandy wyrażenia niezgodnych typów dla operatora                             |
|                      [C28301](../code-quality/c28301.md)                       |                               Brak adnotacji dla pierwszej deklaracji funkcji.                               |
|                      [C28302](../code-quality/c28302.md)                       |                             Znaleziono dodatkowy \_ \_ operator DEREF w adnotacji.                              |
|                      [C28303](../code-quality/c28303.md)                       |                           \_Znaleziono niejednoznaczny \_ operator DEREF w adnotacji.                            |
|                      [C28304](../code-quality/c28304.md)                       |                     Znaleziono niepoprawnie umieszczony \_ operator Notref \_ został zastosowany do tokenu.                      |
|                      [C28305](../code-quality/c28305.md)                       |                                Wykryto błąd podczas analizowania tokenu.                                 |
|                      [C28350](../code-quality/c28350.md)                       |                  Adnotacja zawiera opis sytuacji, która nie jest stosowana warunkowo.                   |
|                      [C28351](../code-quality/c28351.md)                       |         Adnotacja opisuje, gdzie w warunku nie można używać wartości dynamicznej (zmiennej).          |
