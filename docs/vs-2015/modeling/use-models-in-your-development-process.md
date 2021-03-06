---
title: Używaj modeli w procesie deweloperskim | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
ms.assetid: a33ac8fc-4ba0-4850-b71b-014dc8674e54
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4db3506ca21289c8ffda8582337cd8027a261438
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586362"
---
# <a name="use-models-in-your-development-process"></a>Używanie modeli w procesie tworzenia aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można użyć modelu, aby pomóc zrozumieć i zmienić system, aplikację lub składnik. Model może pomóc w wizualizowaniu świata, w którym działa system, wyjaśnić potrzeby użytkowników, definiować architekturę systemu, analizować kod i upewnić się, że kod spełnia wymagania. Zobacz [wideo Channel 9: ulepszanie architektury za pośrednictwem modelowania](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling).

 Aby sprawdzić, które wersje programu Visual Studio obsługują każdy typ modelu, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="how-to-use-models"></a>Jak używać modeli
 Modele mogą pomóc na kilku sposobów:

- Rysowanie diagramów modelowania ułatwia wyjaśnienie koncepcji związanych z wymaganiami, architekturą i projektowaniem wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

- Praca z modelami może pomóc w ujawnianiu niespójności w wymaganiach.

- Komunikacja z modelami ułatwia przekazywanie ważnych koncepcji mniej niejednoznacznych niż w przypadku języka naturalnego. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Czasami można używać modeli do generowania kodu lub innych artefaktów, takich jak schematy bazy danych lub dokumenty. Na przykład składniki modelowania programu [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] są generowane na podstawie modelu.  Aby uzyskać więcej informacji, zobacz [generowanie i Konfigurowanie aplikacji na podstawie modeli](../modeling/generate-and-configure-your-app-from-models.md).

  Można używać modeli w wielu różnych procesach, od najwyższej Agile do wysokiej procedury.

### <a name="use-models-to-reduce-ambiguity"></a>Używaj modeli, aby zmniejszyć niejednoznaczność
 Język modelowania jest mniej niejednoznaczny niż język naturalny i jest przeznaczony do wyrażania pomysłów zwykle wymaganych podczas opracowywania oprogramowania.

 Jeśli projekt ma niewielki zespół w ramach praktyk Agile, możesz używać modeli, aby pomóc w wyjaśnieniu scenariuszy użytkownika. W przypadku dyskusji z klientem o ich potrzebach Tworzenie modelu może znacznie szybciej generować przydatne pytania i w szerszym obszarze produktu niż w przypadku pisania lub tworzenia prototypów kodu.

 Jeśli projekt jest duży i zawiera zespoły w różnych częściach świata, można używać modeli, aby pomóc w bardziej wydajnym przekazywaniu wymagań i architektury niż w przypadku zwykłego tekstu.

 W obu przypadkach tworzenie modelu prawie zawsze skutkuje znaczącą redukcją niespójności i niejasności. Różne osoby zainteresowane często mają różne zrozumienia świata firmy, w których działa system, a różni deweloperzy często mają różne zrozumienie sposobu działania systemu. Korzystanie z modelu jako fokus dyskusji zwykle ujawnia te różnice. Aby uzyskać więcej informacji na temat sposobu ograniczania niespójności przy użyciu modelu, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

### <a name="use-models-with-other-artifacts"></a>Używanie modeli z innymi artefaktami
 Model nie należy do specyfikacji wymagań lub architektury. Jest to narzędzie, które umożliwia bardziej przejrzyste prezentowanie niektórych aspektów tych elementów, ale nie wszystkie pojęcia wymagane podczas projektowania oprogramowania. W związku z tym modele powinny być używane razem z innymi środkami komunikacji, takimi jak strony lub akapity programu OneNote, Microsoft Office dokumenty, elementy robocze w programie [!INCLUDE[esprfound](../includes/esprfound-md.md)] , lub notatki programu Sticky Notes na ścianie pokojowej. Oprócz ostatniego elementu wszystkie te typy obiektów mogą być połączone z elementami części modelu.

 Inne aspekty specyfikacji, które są zwykle używane razem z modelami, to m.in.: W zależności od skali i stylu projektu można użyć kilku z tych aspektów lub nie używać żadnego z nich w ogóle:

- Scenariusze użytkownika. Scenariusz użycia to krótki opis, omówiony dla użytkowników i innych uczestników projektu aspektów zachowania systemu, które zostaną dostarczone w jednym z iteracji w projekcie. Typowy scenariusz użytkownika rozpoczyna się od "klient będzie mógł..." W scenariuszu użycia może zostać utworzona grupa przypadków użytkowania lub można zdefiniować rozszerzenia przypadków użycia, które zostały wcześniej opracowane. Definiowanie lub rozszerzanie przypadków użycia ułatwia wyraźniejsze scenariusze użytkownika.

- Żądania zmiany. Żądanie zmiany w bardziej formalnym projekcie jest bardzo podobne do scenariusza użytkownika w projekcie agile. Podejście Agile traktuje wszystkie wymagania jako zmiany, które zostały opracowane w poprzednich iteracjach.

- Opis przypadku użycia. Przypadek użycia reprezentuje jeden sposób, w którym użytkownik współdziała z systemem w celu osiągnięcia określonego celu. Pełny opis obejmuje cel, główną i alternatywną sekwencję zdarzeń oraz wyjątkowe wyniki. Diagram przypadków użycia służy do podsumowywania i udostępniania omówienia przypadków użycia.

- Sytuacji. Scenariusz to dość szczegółowy opis sekwencji zdarzeń pokazujących, jak system, użytkownicy i inne systemy współpracują ze sobą w celu zapewnienia wartości dla zainteresowanych stron. Może to mieć postać pokazu slajdów interfejsu użytkownika lub prototypu interfejsu użytkownika. Można opisać jeden przypadek użycia lub sekwencję przypadków użycia.

- Słownik. Słownik wymagań projektu zawiera opis wyrazów, w których klienci omawiają swój świat. Dla modeli interfejsu użytkownika i wymagań należy również użyć tych warunków. Diagram klas może pomóc w wyjaśnieniu relacji między większością tych warunków. Tworzenie diagramów i słownika nie tylko zmniejsza liczbę niezrozumiałych użytkowników i deweloperów, ale również prawie zawsze ujawnia niezrozumiałe zrozumienie między różnymi uczestnikami biznesowymi.

- Reguły biznesowe. Wiele reguł firmy może być wyrażonych jako ograniczenia niezmiennej dla skojarzeń i atrybutów w modelu klasy wymagań oraz jako ograniczenia na diagramach sekwencji.

- Projektowanie wysokiego poziomu. Opisuje główne części i ich dopasowanie. Diagramy składników, sekwencji i interfejsów są głównym elementem projektu wysokiego poziomu.

- Wzorce projektowe. Opisz reguły projektowania, które są współużytkowane przez różne części systemu.

- Specyfikacje testu. Skrypty testowe i projekty dla kodu testu mogą być dobrym sposobem użycia diagramów działań i sekwencji do opisywania sekwencji kroków testu. Testy systemowe powinny być wyrażone w warunkach modelu wymagań, aby można je było łatwo zmienić w przypadku zmiany wymagań.

- Plan projektu. Plan projektu lub zaległości określa, kiedy każda funkcja zostanie dostarczona. Każdą funkcję można zdefiniować, wskazując, jakie przypadki użycia i reguły biznesowe są implementowane lub rozszerzane. Możesz odwołać się do przypadków użycia i reguł firmy bezpośrednio w planie lub zdefiniować zestaw funkcji w osobnym dokumencie i użyć tytułów funkcji w planie.

### <a name="use-models-in-iteration-planning"></a>Używanie modeli w planowaniu iteracji
 Mimo że wszystkie projekty są różne w ich skali i organizacji, typowy projekt jest planowany jako seria iteracji między dwa i sześć tygodni. Ważne jest zaplanowanie wystarczającej liczby iteracji, aby umożliwić zwroty ze wczesnych iteracji, aby dostosować zakres i plany dla późniejszych iteracji.

 Poniższe sugestie mogą pomóc w zrozumieniu korzyści z modelowania w projekcie iteracyjnym.

#### <a name="sharpen-focus-as-each-iteration-approaches"></a>Wyostrz fokus w miarę podejścia iteracji
 Zgodnie z poszczególnymi iteracjami należy używać modeli, aby pomóc w określeniu, jakie elementy mają być dostarczane na końcu iteracji.

- Nie należy modelować wszystkich szczegółów w wczesnych iteracjach. W pierwszej iteracji Utwórz Diagram klas dla głównych elementów w słowniku użytkownika, narysuj diagram najważniejszych przypadków użycia i narysuj diagram głównych składników. Nie należy opisywać żadnego z tych elementów szczegółowo, ponieważ szczegóły zmienią się w dalszej części projektu. Użyj warunków zdefiniowanych w tym modelu, aby utworzyć listę funkcji lub główne historie użytkowników. Przypisz funkcje do iteracji, aby w przybliżeniu zrównoważyć szacowane obciążenie w całym projekcie. Te przypisania zostaną zmienione w dalszej części projektu.

- Spróbuj zaimplementować uproszczone wersje wszystkich najważniejszych przypadków użycia we wczesnej iteracji. Zwiększ te przypadki użycia w późniejszych iteracjach. Takie podejście ułatwia zmniejszenie ryzyka związanego z odnajdywaniem wad w wymaganiach lub architekturę zbyt późno w projekcie, aby wykonać dowolne czynności.

- Przed końcem każdej iteracji należy posiadać warsztat dotyczący wymagań, aby szczegółowo definiować wymagania lub historie użytkownika, które zostaną opracowane w następnej iteracji. Zapraszaj użytkowników i uczestników współpracy, którzy mogą decydować o priorytetach, a także deweloperów i testerów systemu. Zezwalaj na trzy godziny, aby zdefiniować wymagania dla iteracji 2-tygodniowej.

- Celem warsztatu jest to, że wszyscy zgadzają się na to, co zostanie osiągnięte przez zakończenie następnej iteracji. Używaj modeli jako jednego z narzędzi, które ułatwią wyjaśnienie wymagań. Dane wyjściowe warsztatu to zaległość iteracji: to jest lista zadań deweloperskich w programie [!INCLUDE[esprfound](../includes/esprfound-md.md)] i zestawów testów w programie [!INCLUDE[TCMext](../includes/tcmext-md.md)] .

- W warsztatach dotyczących wymagań należy omówić projekt tylko w miarę potrzeb, aby określić oszacowania dla zadań deweloperskich. W przeciwnym razie należy zachować dyskusję z zachowaniem systemu, które użytkownicy mogą bezpośrednio korzystać z programu. Zachowaj model wymagań niezależnie od modelu architektury.

- Udziałowcy nietechniczne nie mają zwykle żadnych problemów z zrozumieniem diagramów UML z pewnymi wskazówkami.

#### <a name="link-model-to-work-items"></a>Połącz model z elementami roboczymi
 Po określeniu wymagań warsztatowych należy opracować szczegóły modelu wymagań i połączyć model z zadaniami deweloperskimi. Można to zrobić, łącząc elementy robocze w [!INCLUDE[esprfound](../includes/esprfound-md.md)] z elementami w modelu. Aby dowiedzieć się, jak to zrobić, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).

 Można połączyć dowolny element z elementami roboczymi, ale najbardziej przydatne są następujące elementy:

- Przypadki użycia. Możesz połączyć przypadek użycia z zadaniami deweloperskimi, które będą je wdrażać.

- Rozszerzenia przypadku użycia. Jeśli tylko jeden aspekt przypadku użycia zostanie zaimplementowany w iteracji, można go rozdzielić do podstawowego przypadku użycia razem z co najmniej jednym rozszerzeniem. Rozszerzenia to przypadki użycia połączone z przypadkiem podstawowym z relacją «rozszerza». Aby uzyskać więcej informacji o rozszerzeniu przypadku użycia, zobacz [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md).

- Komentarze opisujące reguły biznesowe lub wymagania dotyczące jakości usług. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

#### <a name="link-model-to-tests"></a>Połącz model z testami
 Użyj modelu wymagań, aby zaprojektować testy akceptacji. Twórz te testy równolegle z pracą programistyczną.

 Aby dowiedzieć się więcej o tej metodzie, zobacz [Tworzenie testów z modelu](../modeling/develop-tests-from-a-model.md).

#### <a name="estimate-remaining-work"></a>Szacowanie pracy pozostałej
 Model wymagań może pomóc oszacować łączny rozmiar projektu w odniesieniu do rozmiaru każdej iteracji. Ocenianie liczby i złożoności przypadków użycia i klas może pomóc oszacować prace programistyczne, które będą wymagane. Po zakończeniu kilku pierwszych iteracji porównanie wymagań objętych usługą i wymagania, które nadal obejmują, mogą dać Przybliżony pomiar kosztów i zakresu reszty projektu.

 Przed końcem każdej iteracji Przejrzyj przypisanie wymagań do przyszłych iteracji. Może być przydatne do reprezentowania stanu oprogramowania na końcu każdej iteracji jako podsystem na diagramie przypadków użycia. W dyskusjach można przenosić przypadki użycia i rozszerzenia przypadków użycia z jednego z tych podsystemów do innej.

## <a name="levels-of-abstraction"></a>Poziomy abstrakcji
 Modele mają asortyment abstrakcji w odniesieniu do oprogramowania. Najbardziej konkretne modele odzwierciedlają bezpośrednio kod programu i najbardziej abstrakcyjne modele reprezentują koncepcje biznesowe, które mogą lub nie być reprezentowane w kodzie.

 Model można przeglądać za pomocą kilku rodzajów diagramów. Aby uzyskać informacje o modelach i diagramach, zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).

 Różne rodzaje diagramów są przydatne do opisywania projektu na różnych poziomach abstrakcji. Wiele typów diagramów jest przydatnych na więcej niż jednym poziomie. W tej tabeli przedstawiono, w jaki sposób można używać poszczególnych typów diagramów.

|Poziom projektu|Typy diagramów|
|------------------|-------------------|
|Proces biznesowy<br /><br /> Zrozumienie kontekstu, w którym używany jest system, pomaga zrozumieć, czego potrzebują użytkownicy.|-Diagramy aktywności opisują przepływ pracy między osobami i systemami, aby osiągnąć cele biznesowe.<br />Diagramy klasy koncepcyjnej opisują koncepcje biznesowe używane w procesie biznesowym.|
|Wymagania dotyczące użytkownika<br /><br /> Definicja czego potrzebują użytkownicy z systemu.|— Diagramy przypadków użycia podsumowują interakcje, które użytkownicy i inne systemy zewnętrzne korzystają z opracowywanego systemu. Możesz dołączyć inne dokumenty do każdego przypadku użycia, aby szczegółowo opisać go.<br />— Diagramy klas UML opisują typy informacji, o których komunikują się użytkownicy i system.<br />— Reguły biznesowe i wymagania dotyczące jakości usług można znaleźć w oddzielnych dokumentach.|
|Projektowanie wysokiego poziomu<br /><br /> Ogólna struktura systemu: główne składniki i sposób ich łączenia.|— Diagramy warstw opisują sposób, w jaki system jest podzielony na części zależne. Możesz sprawdzić poprawność kodu programu względem diagramów warstwowych, aby upewnić się, że są one zgodne z architekturą.<br />-Diagramy składników pokazują interfejsy części, określając komunikaty i usługi, które są dostarczane i wymagane przez poszczególne składniki.<br />-Diagramy sekwencji pokazują, jak składniki komunikują się, aby zaimplementować każdy przypadek użycia.<br />— Diagramy klas UML opisują interfejsy składników i typy danych przenoszone między składnikami.|
|Wzorce projektowe<br /><br /> Konwencje i metody rozwiązywania problemów z projektowaniem, które są używane we wszystkich częściach projektu|— Diagramy klas UML opisują struktury wzorca<br />-Diagramy sekwencji lub działań pokazują interakcje i algorytmy|
|Analiza kodu<br /><br /> Na podstawie kodu można generować kilka typów diagramów.|-Diagramy sekwencji pokazują interakcje między obiektami w kodzie.<br />-Diagramy warstwowe pokazują zależności między klasami. Zaktualizowany kod można zweryfikować na diagramie warstwowym.<br />Klasy diagramy pokazują klasy w kodzie.|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|------------------|---------------|
|**Filmy wideo**|![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN: jak tworzyć i używać modeli i diagramów UML (Visual Studio 2010 Ultimate)](https://msdn.microsoft.com/vstudio/gg418384)<br /><br /> ![link do kanału wideo](../data-tools/media/playvideo.gif "PlayVideo") [9: UML z programem Visual Studio 2010](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-1-Brainstorming-a-Project/)<br /><br /> ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN: jak serie — narzędzia i rozszerzalność UML (Visual Studio 2010 Ultimate)](https://msdn.microsoft.com/vstudio/ff859492)|
|**Fora**|-   [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Wizualizacja & modelowania SDK (narzędzia DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogi**|[Blog programu Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Artykuły techniczne i dzienniki**|[Centrum architektury MSDN](https://msdn.microsoft.com/architecture/default.aspx)<br /><br /> [Architektura Visual Studio — wskazówki dotyczące oprzyrządowania](../modeling/visual-studio-architecture-tooling-guidance.md)|

## <a name="see-also"></a>Zobacz też
 [Używanie modeli w programowaniu Agile](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [Tworzenie modeli dla modelu](../modeling/create-models-for-your-app.md) [wymagań użytkownika model](../modeling/model-user-requirements.md) aplikacji [Architektura aplikacji](../modeling/model-your-app-s-architecture.md) [opracowywanie testów z struktury modelu](../modeling/develop-tests-from-a-model.md) [rozwiązania do modelowania](../modeling/structure-your-modeling-solution.md)
