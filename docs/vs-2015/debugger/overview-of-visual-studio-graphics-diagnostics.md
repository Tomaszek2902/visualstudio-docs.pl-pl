---
title: Przegląd Diagnostyka grafiki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2dc0d0bf4efd8c30d874a24e94d3933d2eef713a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186534"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Omówienie diagnostyki grafiki w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio *Diagnostyka grafiki* to zestaw narzędzi do nagrywania, a następnie analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Diagnostyka grafiki można używać w aplikacjach, które są uruchamiane lokalnie na komputerze z systemem Windows, w emulatorze urządzenia z systemem Windows lub na komputerze zdalnym lub urządzeniu.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Używanie Graphics Diagnostics do debugowania problemów z renderowaniem
 Debugowanie problemów z renderowaniem w aplikacji rozbudowanej graficznie nie jest tak proste, jak uruchomienie debugera i krokowe wykonywanie kodu. W każdej klatce są produkowane setki tysięcy unikatowych pikseli, każdy na podstawie złożonego zestawu stanu, danych, parametrów i kodu — możliwe, że tylko kilka z powyższych pikseli pokaże problem, który próbujesz zdiagnozować. Aby jeszcze bardziej skomplikować sprawy, kod, który generuje każdy piksel, jest wykonywany na wyspecjalizowanym sprzęcie, który przetwarza setki pikseli równolegle. Tradycyjne narzędzia i techniki debugowania, z których trudno się korzysta nawet w kodzie mało skomplikowanym pod względem wątków, są nieskuteczne w obliczu tak dużej ilości danych.

 Narzędzia Diagnostyka grafiki w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mają pomóc w znalezieniu problemów z renderowaniem, rozpoczynając od artefaktów wizualizacji, które wskazują na problem, a następnie śledzenia z powrotem do źródła problemu przez skoncentrowanie się tylko na odpowiednim kodzie programu do cieniowania, etapach potoku, nawiązaniu połączenia, zasobach i stanie urządzenia — w kodzie źródłowym aplikacji.

## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX
 Diagnostyka grafiki obsługuje aplikacje korzystające z funkcji Direct3D 12, Direct3D 11 i Direct3D 10 oraz ograniczoną obsługę aplikacji korzystających z Direct2D. Nie obsługuje aplikacji, które używają starszych wersji Direct3D, DirectDraw lub innych graficznych interfejsów API.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 i Direct3D 12
 W systemie Windows 10 wprowadzono następną wersję Direct3D, *Direct3D 12*, która znacznie różni się od Direct3D 10 i Direct3D 11. Te różnice powodują, że program DirectX jest gotowy do wyrównania przy użyciu nowoczesnego sprzętu graficznego i z możliwością pełnego działania, ale również wprowadza zmiany w dużym interfejsie API i zwiększa odpowiedzialność za programistę do zarządzania okresami istnienia zasobów i rywalizacją. Wspaniałe narzędzia debugowania mają kluczowe znaczenie dla programistów tworzących takie przejścia, dlatego Diagnostyka grafiki w programie Visual Studio 2015 obsługuje prawo od samego początku. Pomimo różnic Diagnostyka grafiki program Direct3D 12 zachowuje funkcję-parzystość z Diagnostyka grafiki z programem Direct3D 11,2, z wyjątkiem bieżącego wyjątku funkcji analizy klatek. Wkrótce zostanie dodana obsługa analizy klatek w programie Direct3D 12, a następnie nowe narzędzia diagnostyczne, które ułatwiają rozwiązywanie nowych rodzajów błędów, które mogą wystąpić w programie Direct3D 12.

 System Windows 10 utrzymuje również obsługę wcześniejszych wersji programu Direct3D oraz gier i aplikacji, które są na nich zależne. Diagnostyka grafiki w programie Visual Studio 2015 nadal obsługuje Direct3D 10 i Direct3D 11 w systemie Windows 10, a także na Windows 8.1.

### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 i Direct3D 11,2
 W programie w programie [!INCLUDE[win81](../includes/win81-md.md)] DirectX 11,2 wprowadzono nowe funkcje, które obejmują obsługę przechwytywania informacji graficznych przez środowisko uruchomieniowe. [!INCLUDE[win81](../includes/win81-md.md)] używa nowego przechwytywania opartego na czasie wykonywania — znanego jako *niezawodne przechwytywanie*— wyłącznie dla wszystkich wersji programu DirectX obsługiwanych przez program [!INCLUDE[win81](../includes/win81-md.md)] . Niezawodna Funkcja przechwytywania obsługuje również nowe funkcje programu Direct3D 11,2.

### <a name="limited-direct2d-support"></a>Ograniczona obsługa Direct2D
 Ponieważ Direct2D to API trybu użytkownika, który jest zbudowany na bazie Direct3D, możesz skorzystać z Graphics Diagnostics, aby debugować problemy z renderowaniem w aplikacjach, które używają Direct2D. Jednak ponieważ rejestrowane są tylko podstawowe zdarzenia Direct3D, a nie zdarzenia Direct2D wyższego poziomu, zdarzenia Direct2D nie pojawią się na liście zdarzeń grafiki. Ponadto, ponieważ relacja między zdarzeniami Direct2D i wynikowymi zdarzeniami Direct3D nie jest zawsze jasna, używanie Graphics Diagnostics do debugowania problemów z renderowaniem w aplikacjach, które używają Direct2D, nie jest proste. Nadal można korzystać z Graphics Diagnostics, aby uzyskać informacje dotyczące problemów renderowania niskiego poziomu w aplikacjach, które korzystają z Direct2D.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Funkcje Diagnostyka grafiki w programie Visual Studio
 Diagnostyka grafiki ma dedykowany interfejs — okno Analizator grafiki — do diagnozowania problemów z renderowaniem, ale również dodaje narzędzia do interfejsu programu Visual Studio.

### <a name="the-graphics-toolbar-visual-studio"></a>Pasek narzędzi grafiki (Visual Studio)
 Pasek narzędzi grafiki zapewnia szybki dostęp do Diagnostyka grafiki poleceń.

 Przycisk **Rozpocznij diagnostykę** uruchamia aplikację w obszarze Diagnostyka grafiki. Gdy aplikacja działa w Diagnostyka grafiki, przycisk **Przechwyć następną renderowaną ramkę** jest włączony.

### <a name="diagnostics-capture-interface"></a>Interfejs przechwytywania diagnostyki
 Po uruchomieniu aplikacji w obszarze Diagnostyka grafiki program Visual Studio wyświetla interfejs sesji diagnostycznej, którego można użyć do przechwytywania ramek, a także wyświetla bieżące obciążenie procesora CPU i procesora GPU. Zostanie wyświetlone obciążenie procesora CPU i procesora GPU ułatwiające zidentyfikowanie ramek, które mogą być przechwytywane ze względu na ich charakterystykę wydajności zamiast błędów renderowania.

 Nie jest to jedynym sposobem przechwytywania ramek. Możesz również przechwytywać ramki przy użyciu interfejsu przechwytywania programistycznego lub programu w celu przechwycenia wiersza polecenia dxcap.exe.

 Aby uzyskać więcej informacji, zobacz [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md) .

### <a name="gpu-usage"></a>Użycie procesora GPU
 Diagnostyka grafiki może również profilować wydajność aplikacji Direct3D. Ze względu na to, że dane profilowania byłyby pochylone przez zapisanie szczegółów zdarzeń graficznych, nie jest to oddzielone od przechwytywania ramek, które mają być używane, badane z analizatorem grafiki.

 Aby uzyskać więcej informacji, zobacz [użycie procesora GPU](../debugger/gpu-usage.md) .

### <a name="directx-control-panel"></a>Panel sterowania DirectX
 Panel sterowania DirectX to składnik DirectX, którego można użyć, aby zmienić sposób zachowania DirectX — na przykład włączyć wersję składników wykonawczych DirectX przeznaczoną do debugowania, wybrać rodzaj komunikatów debugowania, które są raportowane, oraz uniemożliwić korzystanie z niektórych funkcji sprzętowych karty graficznej w celu emulacji mniej zaawansowanego sprzętu. Ten poziom kontroli nad DirectX może pomóc w debugowaniu i testowaniu aplikacji DirectX. Dostęp do panelu sterowania DirectX można uzyskać z Visual Studio.

##### <a name="to-open-the-directx-control-panel"></a>Aby otworzyć panel sterowania DirectX

- Na pasku menu wybierz kolejno opcje **Debuguj**, **grafika**i **Panel sterowania DirectX**.

## <a name="graphics-analyzer"></a>Analizator grafiki
 Analizator grafiki programu Visual Studio to dedykowany interfejs do badania problemów z renderowaniem i wydajnością w ramkach, które zostały już przechwycone. Wewnątrz analizatora grafiki znajdziesz kilka narzędzi ułatwiających eksplorowanie i zrozumienie zachowań aplikacji. Każde narzędzie uwidacznia różne rodzaje informacji na temat testowanej ramki, a narzędzia te są przeznaczone do użycia w sposób intuicyjny w sposób niezgodny ze źródłem problemu z renderowaniem, rozpoczynając od jego wyglądu w bufor ramki.

 Na tej ilustracji przedstawiono typowy układ narzędzi w analizatorze grafiki.

 ![Wszystkie okna debugera grafiki](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Pasek narzędzi grafiki (Analizator grafiki)
 Pasek narzędzi grafiki zapewnia szybki dostęp do okien narzędzi analizatora grafiki.

 ![Pasek narzędzi grafiki w trybie diagnostyki grafiki](../debugger/media/vsg-toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Dokument dziennika grafiki
 Wewnątrz analizatora grafiki dokument dziennika grafiki to najbardziej uwidocznione okno narzędzi. To okno reprezentuje wszystkie ramki przechwycone przez uruchomienie aplikacji w obszarze Diagnostyka grafiki. W tym miejscu możesz wybrać inną ramkę, aby przeanalizować lub wybrać konkretny piksel, który ma być badany za pomocą narzędzia Historia pikseli. Obraz bufor ramki wyświetlany w tym dokumencie zmienia się w celu odzwierciedlenia aktualnie wybranego zdarzenia, dzięki czemu można zobaczyć, w jaki sposób bufor ramki ma wpływ na czas.

 [Dokument dziennika grafiki](../debugger/graphics-log-document.md) jest również punktem wejścia do narzędzia do analizy klatek, które ułatwia zrozumienie wydajności ramki przez zmianę sposobu, w jaki niektóre aspekty renderowania są skonfigurowane i dają wyniki testów porównawczych do porównania z oryginałem.

### <a name="event-list"></a>Lista zdarzeń
 Zdarzenia graficzne oznaczają każde wywołanie interfejsu API Direct3D i zdarzenie zdefiniowane przez użytkownika.

 [Lista zdarzeń](../debugger/graphics-event-list.md) zawiera wszystkie zdarzenia grafiki, które zostały zarejestrowane podczas badania badanej klatki. Aby ułatwić znalezienie ważnych informacji, lista zdarzeń może być wyświetlana hierarchicznie — z ostatnim stanem — zmiany poniżej kolejnego wywołania rysowania — lub jako oś czasu. Ponadto zdarzenia są kodowane kolorami w oparciu o kolejkę, do której należą, i można filtrować listę, tak aby zawierała tylko interesujące Cię zdarzenia.

 Po wybraniu zdarzenia na liście pozostałe narzędzia do analizy grafiki odzwierciedlają stan ramki w czasie tego zdarzenia. W ten sposób można zobaczyć wpływ dowolnego zdarzenia na procesor GPU. Na przykład można zobaczyć natychmiastowy efekt dowolnego wywołania rysowania na bufor ramki, nawet jeśli zostanie on zasłonięty przez kolejne wywołania rysowania. Niektóre zdarzenia mają również hiperłącza, które można wykonać, aby zobaczyć więcej szczegółów na temat jego parametrów lub powiązanych obiektów zasobów.

### <a name="pipeline-stages"></a>Etapy potoku
 Każde wywołanie rysowania w aplikacji przechodzi przez potok graficzny dostarczany przez program Direct3D. Na każdym etapie potoku dane wyjściowe z poprzedniego etapu są przekształcane przez niewielki program, nazywany cieniami, a następnie przekazywane do następnego etapu do momentu, gdy jest on ostatecznie renderowany na ekranie. Wiele błędów renderowania występuje na granicy między etapami potoku, gdy format danych wyjściowych jest inny niż oczekiwano, lub gdy jeden z etapów powoduje po prostu nieprawidłowe wyniki. Zwykle wyniki są uzyskiwane tylko w taki sposób, jak widać na ekranie, i nie można łatwo określić, gdzie w potoku Wystąpił błąd.

 Okno [etapy potoku](../debugger/graphics-pipeline-stages.md) przedstawia niezależny wynik każdego etapu, dzięki czemu można łatwiej określić etap, w którym występuje problem z renderowaniem. Po ustaleniu, który etap jest, możesz rozpocząć debugowanie swojego programu do cieniowania bezpośrednio z okna etapy potoku.

### <a name="graphics-state"></a>Stan grafiki
 Operacje renderowania są zależne od wielu stanów, które zazwyczaj są rozłożone na wiele obiektów. Wiele rodzajów problemów z renderowaniem jest spowodowanych przez błędną konfigurację stanu.

 W oknie [stanu](../debugger/graphics-state.md) są zbierane informacje o stanie odpowiednie dla każdego wywołania rysowania w jednym miejscu, co ułatwia znalezienie, a także wyróżnia zmiany stanu, które wystąpiły od momentu poprzedniego wywołania rysowania.

### <a name="pixel-history"></a>Historia pikseli
 W złożonych scenach nie jest zdarza się, aby piksel był zacieniowany wiele razy w jednej ramce. Czasami wcześniejszy kolor jest po prostu zastępowany, ale inne kolory są łączone ze sobą w celu osiągnięcia efektów takich jak przezroczystość. Jeśli wynik łączenia ich ze sobą nie ma odpowiedniego wyglądu, nie można łatwo stwierdzić, czy jest to spowodowane błędem jednego z kolorów, lub jeśli wystąpił problem ze sposobem, w jaki zostały połączone. Czasami obiekt może wydawać się nieobecny, ponieważ jego udział w pikselu został odrzucony z jakiegoś powodu.

 Okno [Historia pikseli](../debugger/graphics-pixel-history.md) wizualizuje kompletną historię cieniowania każdego piksela w ramce, w tym odrzucone wkłady. W przypadku udziałów, które nie zostały odrzucone, są wyświetlane nieprzetworzone wyniki programu do cieniowania oraz sposób, w jaki każdy nowy kolor został połączony z poprzednim. Dzięki tym informacjom znacznie łatwiej jest zlokalizować źródło błędów w pikselach, które mieszają się z wynikami cieniowania, lub gdy brakuje renderowanego obiektu, ponieważ jego udział w pikselach został nieprawidłowo odrzucony.

### <a name="event-call-stack"></a>Stos wywołań zdarzeń
 Kod programu do cieniowania nie jest jedynym źródłem problemów z renderowaniem w aplikacji Direct3D, czasami kod źródłowy aplikacji przekazuje błędny parametr lub nie konfiguruje go w pełni. Jeden rodzaj błędu, który wcześniej omawiana funkcja, Historia pikseli, może pomóc znaleźć w przypadku braku renderowanego obiektu, ponieważ wszystkie jego piksele zostały odrzucone. Ten rodzaj błędu zwykle występuje w przypadku błędnego skonfigurowania ustawienia, takiego jak ten, który kontroluje sposób wykonywania testu głębokości, i zazwyczaj można znaleźć błąd w dowolnym miejscu w stosie wywołania wywołania rysowania brakującego obiektu.

 Okno [stosu wywołań zdarzeń](../debugger/graphics-event-call-stack.md) wyświetla kompletny stos wywołań każdego zdarzenia grafiki na liście zdarzeń, a nawet umożliwia przechodzenie do kodu źródłowego aplikacji, jeśli dostępne są informacje debugowania. Jest to zaawansowane narzędzie, za pomocą którego po raz pierwszy pojawia się na procesorze GPU, z powrotem do miejsca, w którym pochodzi w kodzie źródłowym aplikacji.

### <a name="object-table"></a>Tabela obiektów
 Wszystkie ramki renderowane przez aplikację są prawdopodobnie obsługiwane przez setki lub nawet tysiące obiektów zasobów. Mogą one obejmować bufory wsteczne i elementy docelowe renderowania, tekstury, bufory wierzchołków, bufory indeksów, ogólne bufory, a niemal wszystkie elementy członkowskie Direct3D to obiekt.

 W [tabeli obiektów](../debugger/graphics-object-table.md) są wyświetlane wszystkie obiekty, które istnieją w momencie zdarzenia grafiki wybranego na liście zdarzeń. Ponieważ większość obiektów w typowej aplikacji jest teksturą, lista zdarzeń jest zoptymalizowana pod kątem szybkiego wyświetlania szczegółów dotyczących obrazów. Kolumna Typ zawiera informacje o rodzaju obiektu znajdującego się w każdym wierszu, a w kolumnie format w dalszej części tego typu znajduje się podtype lub wersja obiektu. Wyświetlane są również inne szczegóły. Niektóre obiekty mają również hiperłącza, które można wykonać, aby wyświetlić obiekt z bardziej wyspecjalizowaną przeglądarką, taką jak tekstury (można wyświetlić teksturę jako obraz) lub bufory (można wybrać sposób analizowania i wyświetlania nieprzetworzonych bajtów przez program, definiując format buforu).

### <a name="frame-analysis"></a>Analiza klatek
 Grafiki Twojej aplikacji nie muszą być poprawnie — muszą być one również szybkie. Nawet w przypadku mniej wydajnych urządzeń, takich jak laptopy ze zintegrowaną grafiką lub telefonami przenośnymi. I nadal muszą wyglądać zbyt dobrze.

 Narzędzie do [analizy klatek](../debugger/graphics-frame-analysis.md) umożliwia Eksplorowanie potencjalnych optymalizacji wydajności przez automatyczne zmienianie sposobu używania Direct3D przez aplikację oraz dostarczanie wyników testów porównawczych. Na przykład analiza klatek może włączyć mapowanie MIP dla każdej tekstury, co może spowodować, że tekstury, które mogłyby skorzystać z mapowania MIP, ale nie są obecnie włączone. Na sprzęcie, który obsługuje tę funkcję, analiza klatek zawiera również informacje zbierane z liczników wydajności procesora GPU — ten poziom informacji może identyfikować problemy z wydajnością na poziomie sprzętu, takie jak duża liczba wstrzymań lub chybień w pamięci podręcznej.

 Jednak analiza klatek nie tylko szybko się przełączy — pozwala uzyskać największą wydajność, dzięki czemu można uzyskać najmniejszą jakość wizualną. Czasami kosztowny efekt, który wygląda doskonale na dużym wyświetlaczu, nie ma takiego samego wpływu, gdy jest wyświetlany na małym ekranie telefonu, gdzie łatwiejszy efekt może wyglądać podobnie, bez opróżniania baterii. Automatyczne zmiany i testy porównawcze zapewniane przez analizę grafiki mogą pomóc w znalezieniu równowagi odpowiednich dla aplikacji na różnych urządzeniach.

## <a name="see-also"></a>Zobacz też
 [Debuger HLSL](../debugger/hlsl-shader-debugger.md) [Narzędzia do przechwytywania wiersza polecenia](../debugger/command-line-capture-tool.md)
