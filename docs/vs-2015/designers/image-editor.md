---
title: Edytor obrazów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
ms.assetid: fc71d502-c548-4863-8afc-12a1d3ec90d4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c30e6f1be9daf07f3685c06b21ed9d507b86a07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664389"
---
# <a name="image-editor"></a>Edytor obrazów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano sposób pracy z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorem obrazów w celu wyświetlania i modyfikowania zasobów tekstury i obrazów.

 Możesz użyć edytora obrazów do pracy z rodzajami bogatych formatów tekstury i obrazów, które są używane w rozwoju aplikacji DirectX. obejmuje to obsługę popularnych formatów plików obrazów i kodowania kolorów, funkcji, takich jak kanały alfa i usługi, i wiele wysoce skompresowanych, przyspieszanych sprzętowo formatów tekstury, które obsługuje program DirectX.

## <a name="supported-formats"></a>Obsługiwane formaty
 Edytor obrazów obsługuje następujące formaty obrazów:

|Nazwa formatu|Rozszerzenie nazwy pliku|
|-----------------|-------------------------|
|Portable Network Graphics|png|
|JPEG|. jpg,. jpeg,. jpe,. JFIF|
|Bezpośrednie rysowanie powierzchni|. DDS|
|Graphics Interchange Format|gif|
|Mapy|BMP, DIB|
|Tagged Image File Format|. tif,. TIFF|
|TGA (Targa)|. tga|

## <a name="getting-started"></a>Wprowadzenie
 W tej sekcji opisano sposób dodawania obrazu do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu i konfigurowania go pod kątem wymagań.

#### <a name="to-add-an-image-to-your-project"></a>Aby dodać obraz do projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, do którego chcesz dodać obraz, a następnie wybierz **Dodaj**, **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** w obszarze **zainstalowane**wybierz pozycję **grafika**, a następnie wybierz odpowiedni format pliku dla obrazu. Aby uzyskać informacje na temat wybierania formatu pliku zgodnie z wymaganiami, zobacz następującą sekcję.

3. Określ **nazwę** pliku obrazu i **lokalizację** , w której ma zostać utworzona.

4. Wybierz przycisk **Dodaj**.

### <a name="choosing-the-image-format"></a>Wybieranie formatu obrazu
 W zależności od sposobu, w jaki zamierzasz korzystać z obrazu, niektóre formaty plików mogą być bardziej odpowiednie niż inne. Na przykład niektóre formaty mogą nie obsługiwać potrzebnej funkcji, np. przejrzystości lub określonego formatu koloru, lub mogą nie zapewniać odpowiedniej kompresji dla rodzaju zamierzonej zawartości obrazu.

 Poniższe informacje mogą pomóc wybrać format obrazu, który odpowiada Twoim potrzebom.

 **Obraz mapy bitowej (. bmp)** Format obrazu mapy bitowej. Nieskompresowany format obrazu, który obsługuje 24-bitowy kolor. Format mapy bitowej nie obsługuje przezroczystości.

 **Obraz GIF (. gif)** Format obrazu Graphics Interchange Format (GIF). Format obrazu z kompresją LZW, który obsługuje do 256 kolorów. Nieodpowiednie dla zdjęć i obrazów, które mają znaczną ilość szczegółów koloru, ale zapewniają dobre proporcje dla obrazów o małym kolorze, które mają wysoki stopień spójności koloru.

 **Obraz jpg (. jpg)** Format obrazu Joint Photographic Experts Group (JPEG). Wysoce skompresowany, niestratny format obrazu, który obsługuje 24-bitowy kolor i jest odpowiedni do kompresji obrazów ogólnego przeznaczenia, które mają wysoki stopień spójności koloru.

 **Obraz PNG (. png)** Format obrazu Portable Network Graphics (PNG). Umiarkowanie skompresowany, bezstratny format obrazu, który obsługuje 24-bitowy kolor i przezroczystość alfa. Jest to odpowiednie dla obrazów naturalnych i sztucznych, ale nie zapewnia współczynnika kompresji tak jak formaty strat, takie jak JPG lub GIF.

 **Obraz TIFF (. tif)** Format obrazu Tagged Image File Format (TIFF lub TIF). Elastyczny format obrazu, który obsługuje kilka schematów kompresji.

 **Tekstura DDS (. DDS)** Format tekstury powierzchni programu DirectDraw (DDS). Wysoce skompresowany format tekstury, który obsługuje 24-bitowy kolor i przezroczystość alfa. Jego współczynnik kompresji może być tak duży, jak 8:1. Jest on oparty na kompresji tekstury S3, którą można zdekompresować na sprzęcie graficznym.

 **Obraz TGA (. TGA)** Format obrazu karty graficznej TrueVision (TGA) (znany również jako Targa). Format obrazu z kompresją RLE i bezstratny, który obsługuje zarówno obrazy z zamapowanymi kolorami (Paleta kolorów), jak i kolorami bezpośrednimi, do 24-bitowego koloru i przezroczystości alfa. Nieodpowiednie dla zdjęć i obrazów, które mają znaczną ilość szczegółów koloru, ale zapewniają dobre współczynniki kompresji dla obrazów, które mają długie zakresy identycznych kolorów.

### <a name="configuring-the-image"></a>Konfigurowanie obrazu
 Przed rozpoczęciem pracy z właśnie utworzonym obrazem można zmienić jego konfigurację domyślną. Można na przykład zmienić jej wymiary lub format koloru, którego używa. Aby uzyskać informacje na temat sposobu konfigurowania tych i innych właściwości obrazu, zobacz [Właściwości obrazu](#ImageProperties).

> [!NOTE]
> Przed zapisaniem pracy upewnij się, że ustawiono właściwość **Format koloru** , jeśli chcesz użyć określonego formatu koloru. Jeśli format pliku obsługuje kompresję, można dostosować ustawienia kompresji podczas pierwszego zapisywania pliku lub po wybraniu opcji **Zapisz jako**.

## <a name="working-with-the-image-editor"></a>Praca z edytorem obrazów
 W tej sekcji opisano, jak modyfikować tekstury i obrazy przy użyciu edytora obrazów.

### <a name="image-editor-toolbars"></a>Paski narzędzi edytora obrazów
 Paski narzędzi edytora obrazów zawierają polecenia, które ułatwiają współpracę z obrazami.

 Polecenia, które mają wpływ na stan edytora obrazu, znajdują się na pasku narzędzi **Tryb edytora obrazów** razem z zaawansowanymi poleceniami. Pasek narzędzi znajduje się wzdłuż górnej krawędzi powierzchni projektowej edytora obrazu. Narzędzia do rysowania znajdują się na pasku narzędzi **edytora obrazu** wzdłuż lewej krawędzi powierzchni projektowej edytora obrazu.

 Oto pasek narzędzi **Tryb edytora obrazów** :

 ![Modalny pasek narzędzi edytora obrazu.](../designers/media/digit-tre-modal-toolbar.png "Cyfra-TRE-modalny pasek narzędzi")

 W tej tabeli opisano elementy na pasku narzędzi **Tryb edytora obrazów** , które są wymienione w kolejności, w jakiej są wyświetlane od lewej do prawej.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Umożliwia wybór prostokątnego regionu obrazu. Po wybraniu regionu można wyciąć, skopiować, przenieść, skalować, obrócić, przerzucić lub usunąć. Gdy jest aktywny wybór, narzędzia do rysowania mają wpływ tylko na wybrany region.|
|**Nieregularne zaznaczenie**|Umożliwia wybór nieprawidłowego regionu obrazu. Po wybraniu regionu można wyciąć, skopiować, przenieść, skalować, obrócić, przerzucić lub usunąć. Gdy jest aktywny wybór, narzędzia do rysowania mają wpływ tylko na wybrany region.|
|**Wybór Różdżka**|Umożliwia wybór w podobnym regionie obrazu. *Tolerancja*— to znaczy, że maksymalna różnica między sąsiednimi kolorami, w których są one uznawane za podobne — można skonfigurować tak, aby obejmowała mniejszy lub szerszy zakres podobnych kolorów. Po wybraniu regionu można wyciąć, skopiować, przenieść, skalować, obrócić, przerzucić lub usunąć. Gdy jest aktywny wybór, narzędzia do rysowania mają wpływ tylko na wybrany region.|
|**Panoramowanie**|Włącza Przenoszenie obrazu względem ramki okna. W trybie **panoramowania** wybierz punkt na obrazie, a następnie przenieś go.<br /><br /> Aby tymczasowo aktywować tryb **panoramowania** , naciśnij i przytrzymaj klawisz Ctrl.|
|**Powiększenie**|Umożliwia wyświetlanie większej lub mniejszej szczegółowości obrazu względem ramki okna. W trybie **powiększenia** wybierz punkt na obrazie, a następnie przenieś go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć.<br /><br /> Możesz powiększyć lub pomniejszyć, naciskając i przytrzymując klawisz CTRL, gdy używasz kółka myszy lub naciśnij znak plus (+) lub znak minus (-).|
|**Powiększ do rzeczywistego rozmiaru**|Wyświetla obraz przy użyciu relacji 1:1 między pikselami obrazu a pikselami ekranu.|
|**Dopasuj do rozmiaru**|Wyświetla pełny obraz w ramce okna.|
|**Dopasuj do szerokości**|Wyświetla pełną szerokość obrazu w ramce okna.|
|**Siatka**|Włącza lub wyłącza siatkę, która pokazuje granice pikseli. Siatka może nie być wyświetlana do momentu powiększenia obrazu.|
|**Wyświetl następny poziom MIP**|Aktywuje następny większy poziom MIP w łańcuchu mapy MIP. Aktywny poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|**Wyświetl poprzedni poziom MCI**|Aktywuje następny mniejszy poziom MCI w łańcuchu mapy MIP. Aktywny poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|**Kanał czerwony**<br /><br /> **Kanał zielony**<br /><br /> **Kanał niebieski**<br /><br /> **Kanał alfa**|Włącza lub wyłącza konkretny kanał koloru. **Uwaga:**  Przez systematyczne włączanie lub wyłączanie kanałów kolorów można izolować problemy, które są związane z co najmniej jednym z nich. Można na przykład zidentyfikować niepoprawną przezroczystość alfa.|
|**Tle**|Włącza lub wyłącza wyświetlanie tła za pomocą przezroczystych części obrazu. Można skonfigurować sposób wyświetlania tła, wybierając z następujących opcji:<br /><br /> **Szachownic**<br /> Używa koloru zielonego wraz z określonym kolorem tła, aby wyświetlić tło jako wzór szachownicy. Za pomocą tej opcji można bardziej uwidocznić przezroczyste fragmenty obrazu.<br /><br /> Białe tło<br /> Używa koloru białego do wyświetlania tła.<br /><br /> Czarne tło<br /> Używa koloru czarnego do wyświetlania tła.<br /><br /> Tło animacji<br /> Pans z wzorcem szachownicy powoli. Za pomocą tej opcji można bardziej uwidocznić przezroczyste fragmenty obrazu.|
|**Właściwości**|Alternatywnie otwiera lub zamyka okno **Właściwości** .|
|**Zaawansowany**|Zawiera dodatkowe polecenia i opcje.<br /><br /> **Filtry**<br /><br /> Oferuje kilka popularnych filtrów obrazów: **czerń i biel**, **Rozmycie**, **Rozjaśnianie**, **ciemniej**, **wykrywanie krawędzi**, **płaskorzeźba**, **Odwracanie kolorów**, **Ripple**, **Sepia ton**i **Wyostrzanie**.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie przy użyciu D3D11**<br /> Program używa programu Direct3D 11 do renderowania powierzchni projektowej edytora obrazu.<br /><br /> **Renderowanie przy użyciu D3D11WARP**<br /> Używa platformy Direct3D 11 systemu Windows z zaawansowaną rasteryzacją (Wypaczenie) w celu renderowania powierzchni projektowej edytora obrazu.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć w poziomie**<br /> Obraz jest transponowany wokół jego poziomej lub osi x.<br /><br /> **Przerzuć w pionie**<br /> Obraz jest transponowany wokół osi pionowej, lub y.<br /><br /> **Generuj MIPS**<br /> Generuje poziomy MIP dla obrazu. Jeśli już istnieją poziomy MIP, są one odtworzone od największego poziomu MIP. Wszelkie zmiany wprowadzone do mniejszych poziomów MIP są tracone. Aby zapisać wygenerowane poziomy MIP, należy użyć formatu. dds do zapisania obrazu.<br /><br /> **Wyświetlanie**<br /><br /> **Szybkość klatek**<br /> Gdy ta funkcja jest włączona, zostanie wyświetlona szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. **Porada:**  Możesz wybrać przycisk **Zaawansowane** , aby ponownie uruchomić ostatnie polecenie.|

 Oto pasek narzędzi **edytora obrazu** .

 ![Pasek narzędzi edytora obrazów](../designers/media/digit-tre-toolbar.png "Cyfra — TRE — pasek narzędzi")

 W poniższej tabeli opisano elementy na pasku narzędzi **edytora obrazu** , które są wymienione w kolejności, w jakiej są wyświetlane od góry do dołu.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Ołówka**|Używa aktywnego wyboru koloru do rysowania pociągnięcia z aliasem. Możesz ustawić kolor i grubość pociągnięcia w oknie **Właściwości** .|
|**Ciągnięć**|Używa aktywnego wyboru koloru do rysowania pociągnięcia wygładzonego. Możesz ustawić kolor i grubość pociągnięcia w oknie **Właściwości** .|
|**Aerografu**|Używa aktywnego wyboru koloru do narysowania pociągnięcia antyaliasowego, które miesza się ze sobą i przewyższa wartość czasu. Możesz ustawić kolor i grubość pociągnięcia w oknie **Właściwości** .|
|**Służąc**|Ustawia aktywny wybór koloru na kolor wybranego piksela.|
|**Wypełnienie**|Używa aktywnego wyboru koloru do wypełnienia regionu obrazu. Region, którego to dotyczy, jest definiowany jako piksel, w którym zastosowano wypełnienie, wraz z każdym pikselem połączonym z nim przez piksele tego samego koloru, który jest tym samym kolorem. Jeśli wypełnienie jest stosowane w aktywnym zaznaczeniu, obszar, którego to dotyczy, jest ograniczony przez zaznaczenie.<br /><br /> Domyślnie aktywnym wyborem koloru jest mieszanie wraz z regionem, którego to dotyczy, zgodnie ze składnikiem Alpha. Aby użyć aktywnego wyboru kolorów w celu zastąpienia regionu, którego to dotyczy, naciśnij i przytrzymaj klawisz Shift podczas korzystania z narzędzia Fill.|
|**Gumka**|Ustawia piksele na pełny kolor przezroczysty, jeśli obraz obsługuje kanał alfa. W przeciwnym razie ustawia piksele na aktywny kolor tła.|
|**Linia**, **prostokąt**, **prostokąt zaokrąglony**, **Elipsa**|Rysuje kształt na obrazie. Możesz ustawić kolor i grubość konturu w oknie **Właściwości** .<br /><br /> Aby narysować pierwotną, która ma równą szerokość i wysokość, naciśnij i przytrzymaj klawisz Shift podczas rysowania.|
|**Tekst**|Używa wyboru koloru pierwszego planu do rysowania tekstu. Kolor tła jest określany przez wybór koloru tła. W przypadku przezroczystego tła wartość alfa wyboru koloru tła musi być równa 0. Gdy region tekstu jest aktywny, można określić, czy tekst jest rysowany przy użyciu pociągnięcia wygładzonego, i można ustawić **wartość**tekstową, **czcionkę**, **rozmiar**i styl —**pogrubiony**, **kursywa**lub **podkreślony**— w oknie **Właściwości** . Zawartość i wygląd tekstu są finalizowane, gdy region tekstu nie jest już aktywny.|
|**Obrót**|Obraca obraz o 90 stopni w prawo.|
|**Trim**|Przycina obraz do aktywnego zaznaczenia.|

### <a name="working-with-mip-levels"></a>Praca z poziomami MIP
 Niektóre formaty obrazów — na przykład powierzchnię programu DirectDraw (. DDS) — Obsługa poziomów MIP dla poziomu (LOD) w obszarze tekstury. Informacje o sposobach generowania i pracy z poziomu MIP można znaleźć w temacie [How to: Create and Modify Levels MIP](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="working-with-transparency"></a>Praca z przezroczystością
 Niektóre formaty obrazu — na przykład, powierzchnia programu DirectDraw (. DDS) — obsługuje przezroczystość. Istnieje kilka sposobów używania przejrzystości w zależności od używanego narzędzia. Aby określić poziom przezroczystości dla zaznaczenia koloru, w oknie **Właściwości** Ustaw **składnik (alfa** ) zaznaczonego koloru. Poniżej przedstawiono sposób, w jaki różne rodzaje narzędzi kontrolują sposób stosowania przezroczystości:

|Narzędzie|Opis|
|----------|-----------------|
|**Ołówek**, **pędzel**, **Aerograf**, **linia**, **prostokąt**, **prostokąt zaokrąglony**, **Elipsa**, **tekst**|Aby mieszać aktywny wybór kolorów wraz z obrazem, w oknie **Właściwości** rozwiń grupę właściwości **kanały** i Ustaw pole wyboru **Rysuj** w kanale **alfa** , a następnie narysuj normalne.<br /><br /> Aby narysować przy użyciu aktywnego koloru i pozostawić wartość alfa obrazu na miejscu, wyczyść pole wyboru **rysowania** kanału **alfa** , a następnie narysuj normalne.|
|**Wypełnienie**|Aby mieszać aktywny wybór kolorów wraz z obrazem, po prostu wybierz obszar do wypełnienia.<br /><br /> Aby użyć aktywnego wyboru kolorów — w tym wartości kanału alfa — aby zastąpić obraz, naciśnij i przytrzymaj klawisz Shift, a następnie wybierz obszar do wypełnienia.|

### <a name="image-properties"></a><a name="ImageProperties"></a> Właściwości obrazu
 Możesz użyć okna **Właściwości** , aby określić różne właściwości obrazu. Na przykład można ustawić właściwości width i height, aby zmienić rozmiar obrazu.

 W poniższej tabeli opisano właściwości obrazu.

|Właściwość|Opis|
|--------------|-----------------|
|Width|Szerokość obrazu.|
|Height|Wysokość obrazu.|
|Bity na piksel|Liczba bitów, które reprezentują poszczególne piksele. Wartość tej właściwości zależy od **formatu koloru** obrazu.|
|Zaznaczenie przezroczyste|**Wartość true** powoduje mieszanie warstwy wyboru wraz z obrazem głównym, na podstawie wartości alfa warstwy wyboru; w przeciwnym razie **false**. Ten element jest dostępny tylko dla obrazów, które obsługują Alpha.|
|Format|Format koloru obrazu. Można określić różne formaty kolorów, w zależności od formatu obrazu. Format koloru definiuje liczbę i rodzaj kanałów kolorów, które są zawarte w obrazie, a także rozmiar i kodowanie różnych kanałów.|
|Poziom MCI|Aktywny poziom MCI. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|Liczba poziomów MIP|Całkowita liczba poziomów MIP w obrazie. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|Liczba ramek|Całkowita liczba ramek w obrazie. Ten element jest dostępny tylko dla obrazów, które obsługują tablice tekstury.|
|Klatka|Bieżąca ramka. Można wyświetlić tylko pierwszą ramkę; Po zapisaniu obrazu wszystkie pozostałe ramki zostaną utracone.|
|Liczba wycinków głębi|Całkowita liczba wycinków głębokości w obrazie. Ten element jest dostępny tylko dla obrazów, które obsługują tekstury woluminów.|
|Wycinek głębokości|Bieżący wycink głębokości. Można wyświetlić tylko pierwszy wycink; wszystkie inne wycinki są tracone po zapisaniu obrazu.|

> [!NOTE]
> Ponieważ właściwość **Obróć według** ma zastosowanie do wszystkich narzędzi i wybranych regionów, zawsze pojawia się u dołu okna **Właściwości** wraz z innymi właściwościami narzędzia. Wartość **Obróć według** jest zawsze wyświetlana, ponieważ cały obraz jest wybierany niejawnie, gdy nie ma żadnego innego zaznaczenia lub aktywnego narzędzia. Aby uzyskać więcej informacji na temat właściwości **Obróć według** , zobacz [Właściwości narzędzia](#ToolProperties).

#### <a name="resizing-images"></a>Zmienianie rozmiarów obrazów
 Poniżej przedstawiono dwa sposoby zmiany rozmiaru obrazu. W obu przypadkach Edytor obrazów używa interpolacji dwuliniowej do próbkowania obrazu.

- W oknie **Właściwości** Określ nowe wartości właściwości **Width** i **Height** .

- Zaznacz cały obraz i Użyj znaczników obramowania, aby zmienić rozmiar obrazu.

### <a name="working-with-tools"></a>Praca z narzędziami

#### <a name="selected-regions"></a>Wybrane regiony
 Wybory w edytorze obrazu definiują aktywne regiony obrazu — to znaczy, że region będzie miał wpływ narzędzia i przekształcenia. W przypadku aktywnego wyboru obszary poza wybranym regionem nie wpływają na większość narzędzi i transformacji. Jeśli nie ma aktywnego wyboru, cały obraz jest aktywny.

 Większość narzędzi —**ołówek**, **pędzel**, **Aerograf**, **Fill**, **Gumka**i 2-D elementy pierwotne — i przekształcenia —**Obróć**, **przycinanie**, **Odwróć kolory**, **Przerzuć w poziomie**i **Przerzuć w pionie**— są ograniczone lub zdefiniowane przez aktywny wybór. Jednak niektóre narzędzia —**Kroplomierz** i **tekst**— i przekształcenia —**generowanie MIPS**— nie ma to żadnego aktywnego wyboru; Narzędzia te zawsze zachowują się tak, jakby cały obraz był aktywnym wyborem.

 Gdy wybierasz region, możesz nacisnąć i przytrzymać klawisz Shift, aby zwiększyć proporcjonalną (kwadrat) wybór; w przeciwnym razie zaznaczenie nie jest ograniczone.

##### <a name="resizing-selections"></a>Zmienianie rozmiarów zaznaczeń
 Po wybraniu regionu można zmienić jego rozmiar lub zawartość obrazu, zmieniając rozmiar znacznika wyboru. Podczas zmieniania rozmiaru wybranego regionu można użyć następujących klawiszy modyfikujących, aby zmienić zachowanie wybranego regionu w miarę jego zmiany. Możesz też nacisnąć klawisz w miarę zmieniania rozmiaru.

 Ctrl kopiuje zawartość wybranego regionu, zanim zostanie on zmieniony. Spowoduje to pozostawienie oryginalnego obrazu bez zmian podczas zmiany rozmiaru kopiowania.

 Shift zmienia rozmiar wybranego regionu proporcjonalnie do jego oryginalnego rozmiaru.

 Alt zmienia rozmiar regionu zaznaczenia. Spowoduje to pozostawienie niezmodyfikowanego obrazu.

 Oto prawidłowe kombinacje klawiszy modyfikujących:

|Ctrl|Przesunięcia|Alt|Opis|
|----------|-----------|---------|-----------------|
||||Zmienia rozmiar zawartości wybranego regionu.|
||Przesunięcia||Proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|
|||Alt|Zmienia rozmiar wybranego regionu. Definiuje nowy region wyboru.|
||Przesunięcia|Alt|Proporcjonalnie zmienia rozmiar wybranego regionu. Definiuje nowy region wyboru.|
|Ctrl|||Kopiuje, a następnie zmienia rozmiar zawartości wybranego regionu.|
|Ctrl|Przesunięcia||Kopiuje, a następnie proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|

#### <a name="tool-properties"></a><a name="ToolProperties"></a> Właściwości narzędzia
 Gdy wybrane jest narzędzie, można użyć okna **Właściwości** , aby określić szczegóły dotyczące wpływu na obraz. Na przykład można ustawić grubość narzędzia **ołówek** lub kolor narzędzia **pędzel** .

 Można ustawić kolor pierwszego planu i kolor tła. Oba obsługują kanał alfa w celu zapewnienia nieprzezroczystości zdefiniowanej przez użytkownika. Ustawienia są stosowane do wszystkich narzędzi. Jeśli używasz myszy, lewy przycisk myszy odpowiada kolorowi pierwszego planu, a prawy przycisk myszy odpowiada kolorowi tła.

 W poniższej tabeli opisano właściwości narzędzia.

|Narzędzie|Właściwości|
|----------|----------------|
|Wszystkie narzędzia i wybory|**Obróć o**<br /> Definiuje wartość w stopniach, w której zaznaczenie lub efekt narzędzia zostanie obrócony w kierunku w prawo.|
|**Ołówek**, **pędzel**, **Aerograf**, **Gumka**|**Grubość**<br /> Określa rozmiar obszaru, na który ma wpływ narzędzie.|
|**Tekst**|**Antyalias**<br /> Rysuje tekst, który ma wygładzone krawędzie. Daje to płynny wygląd tekstu.<br /><br /> **Wartość**<br /> Tekst do narysowania.<br /><br /> **Czcionka**<br /> Czcionka używana do rysowania tekstu.<br /><br /> **Rozmiar**<br /> Rozmiar tekstu.<br /><br /> **Pogrubiona**<br /> Powoduje pogrubienie czcionki.<br /><br /> **Kursywa**<br /> Powoduje, że czcionka jest kursywą.<br /><br /> **Podkreślone**<br /> Sprawia, że czcionka jest podkreślona.|
|**element podstawowy 2-D**|**Antyalias**<br /> Rysuje elementy pierwotne, które mają wygładzone krawędzie. Daje to płynny wygląd.<br /><br /> **Grubość**<br /> Definiuje grubość linii, która tworzy granicę elementu podstawowego.<br /><br /> **Promień X**<br /> (Tylko zaokrąglony prostokąt) Definiuje promień zaokrąglenia górnego i dolnego krawędzi elementu podstawowego.<br /><br /> **Promień Y**<br /> (Tylko zaokrąglony prostokąt) Definiuje promień zaokrąglenia dla lewej i prawej krawędzi elementu podstawowego.|
|**Ołówek**, **pędzel**, **Aerograf**, **2-D pierwotny**|**Kanały**<br /> Włącza lub wyłącza określone kanały kolorów do wyświetlania i rysowania. Jeśli **Widok** jest ustawiony dla określonego kanału koloru, ten kanał jest widoczny w obrazie. w przeciwnym razie nie jest widoczny. W przypadku wybrania opcji **rysowania** dla określonego kanału kolorów ten kanał ma wpływ na operacje rysowania. w przeciwnym razie nie jest.|
|**Wybór Różdżka**, **wypełnienie**|**Dzial**<br /> Definiuje maksymalną różnicę między sąsiednimi kolorami, w których są uważane za podobne, dzięki czemu mniej lub bardziej podobne kolory są częścią objętego lub wybranego regionu. Domyślnie wartością jest 32, co oznacza, że sąsiednie piksele w odcieniach 32 (jaśniejszy lub ciemniejszy) oryginalnego koloru są uważane za część regionu.|

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------|------------------------|
|Przełącz do trybu **wyboru**|S|
|Przełącz do trybu **powiększenia**|Z|
|Przełącz do trybu **kadrowania**|K|
|Zaznacz wszystko|Ctrl+A|
|Usuń bieżące zaznaczenie|Usuń|
|Anuluj bieżące zaznaczenie|Escape|
|Powiększanie|Ctrl + obrót kółkiem myszy do przodu<br /><br /> Ctrl+PageUp<br /><br /> Znak plus (+)|
|Pomniejszanie|CTRL — kółko myszy do tyłu<br /><br /> Ctrl-PageDown<br /><br /> Znak minusa (-)|
|Przesuń obraz do góry|Obrót kółkiem myszy do tyłu<br /><br /> PageDown|
|Przesuń obraz w dół|Obrót kółkiem myszy do przodu<br /><br /> PageUp|
|Przesuń obraz w lewo|Shift+obrót kółkiem myszy do tyłu<br /><br /> Ruch kółkiem myszy w lewo<br /><br /> Shift + PageDown|
|Przesuń obraz w prawo|Shift+obrót kółkiem myszy do przodu<br /><br /> Ruch kółkiem myszy w prawo<br /><br /> Shift + PageUp|
|Powiększ do rzeczywistego rozmiaru|Ctrl + 0 (zero)|
|Dopasuj obraz do okna|Ctrl + G, Ctrl + F|
|Dopasuj obraz do szerokości okna|Ctrl + G, Ctrl + I|
|Przełącz siatkę|Ctrl + G, Ctrl + G|
|Przytnij obraz do bieżącego zaznaczenia|Ctrl + G, Ctrl + C|
|Wyświetl następną (wyższą szczegóły) poziom MCI|Ctrl + G, Ctrl + 6|
|Wyświetl poprzedni (niższy szczegóły) poziom MCI|Ctrl + G, Ctrl + 7|
|Przełącz kanał koloru czerwonego|Ctrl + G, Ctrl + 1|
|Przełącz kanał zielony koloru|Ctrl + G, Ctrl + 2|
|Przełącz kanał niebieskiego koloru|Ctrl + G, Ctrl + 3|
|Przełącz kanał alfa (przezroczysty)|Ctrl + G, Ctrl + 4|
|Przełącz wzorzec szachownicy alfa|Ctrl + G, Ctrl + B|
|Przełącz do narzędzia nieregularnego wyboru|L|
|Przełącz do narzędzia wyboru Różdżka|M|
|Przejdź do narzędzia Ołówek|P|
|Przełącz do narzędzia Pędzel|B|
|Przełącz do narzędzia Fill|F|
|Przełącz do narzędzia Gumka|E|
|Przełącz do narzędzia tekstowego|T|
|Przejdź do narzędzia do zaznaczania kolorowego (Kroplomierz)|I|
|Przenieś aktywne zaznaczenie i jego zawartość.|Klawisze strzałek.|
|Zmień rozmiar aktywnego zaznaczenia i jego zawartość.|CTRL + klawisze strzałek|
|Przenieś aktywny wybór, ale nie jego zawartość.|Shift + klawisze strzałek|
|Zmień rozmiar aktywnego zaznaczenia, ale nie jego zawartość.|SHIFT + CTRL + klawisze strzałek|
|Zatwierdź bieżącą warstwę|Przesłać|
|Zmniejsz grubość narzędzia|[|
|Zwiększ grubość narzędzia|]|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z obiektami 3-D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie narzędzi, których można użyć w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do pracy z zasobami graficznymi, takimi jak tekstury i obrazy, modele trójwymiarowe i efekty cieniowania.|
|[Edytor modelu](../designers/model-editor.md)|Opisuje, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytora modelu do pracy z modelami 3-D.|
|[Projektant programu do cieniowania](../designers/shader-designer.md)|Opisuje, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektanta cieniowania do pracy z narzędziami do cieniowania.|
