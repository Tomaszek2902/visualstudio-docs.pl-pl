---
title: Tworzenie niestandardowych widoków obiektów natywnych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63390672b246add079806c68a23b69f0e0132c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850205"
---
# <a name="create-custom-views-of-native-objects"></a>Tworzenie niestandardowych widoków obiektów natywnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Struktura programu Visual Studio Natvis pozwala dostosować sposób, w jaki program Visual Studio Wyświetla typy natywne w oknach zmiennych debugera (na przykład okna **czujki**, **lokalne**i **porady dotyczące danych** ).  

 Natvis zastępuje plik **autoexp. dat** , który był używany we wcześniejszych wersjach programu Visual Studio i oferuje składnię XML, lepszą diagnostykę, przechowywanie wersji i obsługę wielu plików.  

> [!NOTE]
> Struktury Natvis nie można używać do wizualizacji, gdy:  
> 
> - Debugujesz projekt pulpitu systemu Windows w języku C++ z typem debugera ustawionym na **mieszany**.  
>   - Przeprowadzasz debugowanie w trybie mieszanym w aplikacji klasycznej systemu Windows w trybie zgodności zarządzanej (**Narzędzia/Opcje/debugowanie/ogólne/Użyj trybu zgodności zarządzanej**).  
>   - Debugowanie jest w aplikacji klasycznej systemu Windows w trybie zgodności natywnej (**Narzędzia/Opcje/debugowanie/ogólne/Używanie trybu zgodności natywnej**).  

## <a name="why-create-natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a> Dlaczego warto tworzyć wizualizacje Natvis?  
 Możesz użyć struktury Natvis do tworzenia reguł wizualizacji dla tworzonych typów, aby deweloperzy mogli je łatwo widzieć podczas debugowania.  

 Na przykład na poniższym obrazie przedstawiono zmienną typu [Windows:: UI:: XAML:: Controls:: TextBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textbox.aspx) , która jest wyświetlana w debugerze bez zastosowanych niestandardowych wizualizacji.  

 ![Wizualizacja domyślna TextBox](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 Wyróżniony wiersz pokazuje `Text` Właściwość `TextBox` klasy. Złożona hierarchia klas utrudnia znalezienie tej wartości; Ponadto debuger nie wie, jak interpretować niestandardowy typ ciągu używany przez obiekt, dlatego nie można zobaczyć ciągu przechowywanego wewnątrz pola tekstowego.  

 To samo `TextBox` wygląda znacznie prostsze n okna zmiennych, gdy są stosowane niestandardowe reguły wizualizacji. Ważne elementy członkowskie klasy mogą być wyświetlane razem, a debuger pokazuje podstawową wartość ciągu niestandardowego typu ciągu.  

 ![Dane TextBox przy użyciu wizualizatora](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

## <a name="using-natvis-files"></a><a name="BKMK_Using_Natvis_files"></a> Korzystanie z plików Natvis  
 pliki. Natvis są plikami XML z rozszerzeniem. Natvis. Schemat jest zdefiniowany w **%VSInstallDir%\Xml\Schemas\natvis.xsd**.  

 Podstawowa struktura pliku. Natvis to jeden lub więcej `Type` elementów, gdzie każdy `Type` element reprezentuje wpis wizualizacji dla typu, którego w pełni kwalifikowana nazwa jest określona w `Name` atrybucie.  

```xml  

<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  

  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  

 Program Visual Studio udostępnia pliki. Natvis w folderze **%VSInstallDir%\Common7\Packages\Debugger\Visualizers** . Te pliki zawierają reguły wizualizacji dla wielu typów wspólnych i mogą być używane jako przykłady podczas pisania wizualizacji dla nowych typów.  

## <a name="adding-natvis-files-to-your-projects"></a>Dodawanie plików Natvis do projektów  
 Pliki. Natvis można dodawać do dowolnego projektu języka C++.  

 Aby dodać nowy plik. Natvis, z otwartym projektem języka C++, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Dodaj/nowy element/Visual C++/narzędzie/plik wizualizacji debugera (. Natvis)**. Debuger będzie automatycznie ładować pliki Natvis z projektów języka C++. Domyślnie pliki Natvis w projekcie są również wstawiane do pliku. pdb skompilowanego przez projekt. Oznacza to, że jeśli debugujesz dane binarne skompilowane przez ten projekt, debuger ładuje plik Natvis z pliku. pdb, nawet jeśli nie ma otwartego projektu. Jeśli nie chcesz, aby plik. Natvis został uwzględniony w pliku. pdb, kliknij prawym przyciskiem myszy plik. Natvis w **Eksplorator rozwiązań**, a w oknie **Właściwości konfiguracji** wybierz opcję **wykluczone z opcji Kompiluj** na **tak**.  

 Zalecane jest edytowanie plików Natvis przy użyciu programu Visual Studio wszelkie zmiany wprowadzone podczas debugowania są automatycznie wprowadzane podczas zapisywania pliku. Ulepszono również środowisko edycji funkcji IntelliSense.  

 Pliki Natvis, które są ładowane z pliku. pdb, mają zastosowanie tylko do typów w module, do którego odwołuje się plik PDB. Na przykład jeśli Module1. pdb definiuje wpis dla typu o nazwie `Test` , ten wpis jest stosowany tylko do klasy **testowej** w Module1.dll. Jeśli inny moduł również definiuje klasę o nazwie **test**, Module1. pdb wpis Natvis nie ma zastosowania do tego.  

## <a name="deploying-natvis-files"></a><a name="BKMK_natvis_location"></a> Wdrażanie plików. Natvis  
 Jeśli plik. Natvis dotyczy tylko typów, które tworzysz w projekcie programu Visual Studio, nie trzeba nic robić. plik Natvis jest zawarty w pliku PDB. Można jednak dodać pliki Natvis do katalogu użytkownika lub do katalogu systemowego, jeśli mają być stosowane do wielu projektów.  

 Kolejność, w jakiej są oceniane pliki. Natvis, jest następująca:  

1. pliki. Natvis osadzone w pliku. pdb są debugowane (chyba że plik o tej samej nazwie istnieje w załadowanym projekcie)  

2. pliki. Natvis, które są częścią załadowanych projektów C++ lub elementu rozwiązania najwyższego poziomu. Obejmuje to wszystkie załadowane projekty języka C++, w tym biblioteki klas, ale nie obejmuje projektów innych języków (np. nie można załadować pliku. Natvis z projektu C#). W przypadku projektów wykonywalnych należy użyć elementów rozwiązania do hostowania dowolnych plików. Natvis, które nie znajdują się już w pliku. pdb, ponieważ nie ma dostępnego projektu języka C++.  

3. Katalog Natvis specyficzny dla użytkownika (**%USERPROFILE%\My Documents\Visual Studio 2015 \ Wizualizatory**  

4. Katalog Natvis całego systemu (**%VSInstallDir%\Common7\Packages\Debugger\Visualizers**). W tym miejscu są kopiowane pliki Natvis, które są instalowane z programem Visual Studio. Możesz również dodać inne pliki do tego katalogu, jeśli masz uprawnienia administratora.  

## <a name="modifying-natvis-files-while-debugging"></a>Modyfikowanie plików Natvis podczas debugowania  
 Można zmodyfikować plik. Natvis w środowisku IDE podczas debugowania projektu, w którym jest on uwzględniony. Otwórz plik w IDE (przy użyciu tego samego wystąpienia programu Visual Studio, które jest debugowane), zmodyfikuj go i Zapisz. Gdy tylko plik zostanie zapisany, należy zaktualizować okna **czujki** i **lokalne** , aby odzwierciedlić zmiany. Jeśli zmodyfikujesz plik. Natvis poza IDE, zmiany nie zaczną obowiązywać automatycznie. Aby zaktualizować okna, można oszacować polecenie **. natvisreload** w oknie **czujki** . Powoduje to, że zmiany zaczną obowiązywać bez ponownego uruchomienia sesji debugowania.  

 Pliki Natvis można także dodawać lub usuwać do rozwiązania, które jest debugowane, a program Visual Studio doda lub usunie odpowiednie wizualizacje.  

 Nie można zmodyfikować pliku. Natvis podczas debugowania, jeśli jest on osadzony w. pdb.  

 Użyj polecenia **. natvisreload** , gdy uaktualniasz plik Natvis do nowszej wersji (na przykład jeśli jest on sprawdzany w kontroli źródła i chcesz pobrać ostatnie zmiany wprowadzone przez kogoś innego do pliku). Zalecane jest edytowanie plików Natvis przy użyciu edytora XML programu Visual Studio.  

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Wyrażenia i formatowanie  
 Wizualizacje Natvis używają wyrażeń języka C++ do określania elementów danych do wyświetlenia. Oprócz ulepszeń i ograniczeń języka C++ w debugerze, które są opisane w [operatorze kontekstu (c++)](../debugger/context-operator-cpp.md), należy pamiętać o następujących różnicach:  

- Wyrażenia Natvis są oceniane w kontekście wizualizacji obiektu, a nie od bieżącej ramki stosu. Na przykład, jeśli używasz `x` w wyrażeniu Natvis, odnosi się to do pola o nazwie `x` w wizualizacji obiektu, a nie do zmiennej lokalnej o nazwie `x` w obecnie wykonywanej funkcji. Nie można uzyskać dostępu do zmiennych lokalnych w wyrażeniach Natvis, chociaż można uzyskać dostęp do zmiennych globalnych.  

- Wyrażenia Natvis nie umożliwiają oceny funkcji ani efektów ubocznych. Oznacza to, że wywołania funkcji i operatory przypisania są ignorowane. Ponieważ [funkcje wewnętrzne debugera](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) są wolne od efektów ubocznych, mogą być swobodnie wywoływane z dowolnego wyrażenia Natvis, nawet jeśli inne wywołania funkcji są niedozwolone.  

  Aby kontrolować sposób wyświetlania wyrażenia w oknie zmiennych, można użyć dowolnego specyfikatora formatu, które są opisane w sekcji [specyfikatory](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) formatu [w temacie języka C++](../debugger/format-specifiers-in-cpp.md) . Należy zauważyć, że specyfikatory formatu są ignorowane, gdy wpis wirtualizacji jest używany wewnętrznie przez Natvis, takich jak `Size` wyrażenie w rozwinięciu ArrayItems.  

## <a name="natvis-views"></a>Widoki Natvis  
 Widoki Natvis umożliwiają wyświetlanie dowolnego typu w więcej niż jeden sposób. Na przykład można zdefiniować widok o nazwie **Simple** , który zapewnia uproszczony widok typu. Na przykład Oto Wizualizacja `std::vector` :  

```xml  
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

 `DisplayString`I `ArrayItems` elementy są używane w widoku domyślnym i widoku prostym, podczas gdy `[size]` `[capacity]` elementy i są wykluczone z widoku prostego. Możesz użyć specyfikatora formatu **widoku,** aby określić widok alternatywny. W oknie **czujka** należy określić widok prosty jako **VEC, widok (prosty)**:  

 ![okno wyrażeń kontrolnych z widokiem prostym](../debugger/media/watch-simpleview.png "Watch-SimpleView")  

## <a name="diagnosing-natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Diagnozowanie błędów Natvis  
 Diagnostyki Natvis można użyć do rozwiązywania problemów z składnią i analizowania błędów. Gdy debuger napotyka błędy w wpisie wizualizacji, ignoruje błędy i wyświetla typ w jego pierwotnej postaci lub wybiera inną odpowiednią wizualizację. Aby zrozumieć, dlaczego określony wpis wizualizacji został zignorowany i zobaczyć, jakie są te błędy, możesz włączyć opcję narzędzia diagnostyki Natvis **/Opcje/debugowanie/okno dane wyjściowe/obraz diagnostyczny Natvis (tylko C++)** . Błędy są wyświetlane w oknie **dane wyjściowe** .  

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Dokumentacja składni Natvis  

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Element autowizualizatora  
 `AutoVisualizer`Element jest węzłem głównym pliku. Natvis i zawiera atrybut przestrzeni nazw `xmlns:` .  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

### <a name="type-element"></a><a name="BKMK_Type"></a> Element Type  
 Typ podstawowy wygląda następująco:  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Określa:  

1. Typ, dla którego ta Wizualizacja powinna być używana ( `Type Name` atrybut).  

2. Wartość obiektu tego typu powinna wyglądać jak ( `DisplayString` element).  

3. Elementy członkowskie typu powinny wyglądać podobnie, gdy użytkownik poszerzy ją w oknie zmiennych ( `Expand` węzeł).  

   **Klasy z szablonami** `Name` Atrybut `Type` elementu akceptuje gwiazdkę `*` jako symbol wieloznaczny, który może być używany dla nazw klas z szablonami:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 W tym przykładzie zostanie użyta ta sama Wizualizacja, niezależnie od tego, czy obiekt jest, czy `CAtlArray<int>` `CAtlArray<float>` . Jeśli istnieje konkretny wpis wizualizacji dla elementu, `CAtlArray<float>` ma pierwszeństwo przed ogólnym.  

 Należy pamiętać, że parametry szablonu można przywoływać w wpisie wizualizacji, używając makr $T 1, $T 2 i tak dalej. Aby znaleźć przykłady tych makr, zobacz pliki Natvis dostarczone z programem Visual Studio.  

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Dopasowanie typu wizualizatora  
 Jeśli nie można zweryfikować wpisu wizualizacji, zostanie użyta Następna dostępna Wizualizacja.  

#### <a name="inheritable-attribute"></a>Dziedziczony atrybut  
 Można określić, czy wizualizacja ma zastosowanie tylko do typu podstawowego, czy do typu podstawowego i wszystkich typów pochodnych z opcjonalnym `Inheritable` atrybutem. W poniższej tabeli Wizualizacja dotyczy tylko `BaseClass` typu:  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 Wartość domyślna `Inheritable` to `true` .  

#### <a name="priority-attribute"></a>Priorytet — atrybut  
 Ten `Priority` atrybut określa kolejność, w której definicje alternatywne są używane, jeśli nie można przeanalizować definicji. Możliwe wartości `Priority` to: `Low` ,,, `MediumLow` `Medium` `MediumHigh` i `High` i wartość domyślna to `Medium` .  

 Atrybut Priority powinien być używany tylko w celu rozróżnienia między priorytetami w tym samym pliku. Natvis, nie między różnymi plikami.  

 W poniższym przykładzie najpierw analizujemy wpis pasujący do 2015 STL i jeśli nie zostanie on przeanalizowany, użyjemy alternatywnego wpisu dla wersji 2013 biblioteki STL:  

```xml  
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  

<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  

#### <a name="version-element"></a><a name="BKMK_Versioning"></a> Element wersji  
 Użyj `Version` elementu, aby ograniczyć zakres wizualizacji do określonych modułów i ich wersji, aby można było zminimalizować kolizje nazw i różne wizualizacje mogą być używane dla różnych wersji typów. Na przykład:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 W tym przykładzie Wizualizacja dotyczy tylko `DirectUI::Border` typu znalezionego w `Windows.UI.Xaml.dll` wersji od 1,0 do 1,5. Należy zauważyć, że dodanie elementów wersji zakresów wizualizacji do określonego modułu i wersji i zmniejsza nieumyślne niezgodności, ale jeśli typ jest zdefiniowany we wspólnym pliku nagłówkowym, który jest używany przez różne moduły, Wizualizacja wersji nie zostanie zastosowana, gdy typ nie znajduje się w określonym module.  

#### <a name="optional-attribute"></a>Opcjonalny atrybut  
 Ten `Optional` atrybut może znajdować się w dowolnym węźle. Jeśli dowolne Podwyrażenie w opcjonalnym węźle nie zostanie przeanalizowane, ten węzeł jest ignorowany, ale pozostała część typu elementu jest nadal ważna. Następujący typ nie `[State]` jest opcjonalny, ale `[Exception]` jest opcjonalny.  Oznacza to, że jeśli `MyNamespace::MyClass` zawiera pole o nazwie _ `M_exceptionHolder` , nadal będzie `[State]` węzeł i `[Exception]` węzeł, ale jeśli `_M_exceptionHolder` brakuje, zobaczysz tylko `[State]` węzeł.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Atrybut warunku  
 Opcjonalny `Condition` atrybut jest dostępny dla wielu elementów wizualizacji i określa, kiedy należy używać reguły wizualizacji. Jeśli wyrażenie wewnątrz atrybutu warunku jest rozpoznawane jako `false` , reguła wizualizacji określona przez element nie jest stosowana. Jeśli wartość jest równa true, lub jeśli nie ma `Condition` atrybutu, reguła wizualizacji zostanie zastosowana do typu. Tego atrybutu można użyć dla `if-else` logiki w wpisach wizualizacji. Na przykład Wizualizacja poniżej ma dwa `DisplayString` elementy dla typu inteligentnego wskaźnika:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Gdy `_Myptr` element członkowski jest `null` , warunek pierwszego `DisplayString` elementu jest rozpoznawany jako `true` , co spowoduje wyświetlenie formularza. Gdy `_Myptr` element członkowski nie jest `null` , warunek jest obliczany `false` , a drugi `DisplayString` element jest wyświetlany.  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView i ExcludeView — atrybuty  
 Te atrybuty określają elementy, które mają być wyświetlane lub nie są wyświetlane w różnych widokach. Na przykład, uwzględniając specyfikację Natvis `std::vector` :  

```xml  
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

 Widok prosty nie wyświetla elementów [size] i [pojemność] w widoku prostym. Jeśli użyto `IncludeView="simple"` zamiast `ExcludeView` , `[size]` `[capacity]` elementy i będą widoczne w widoku prostym, a nie w widoku domyślnym.  

 Można użyć `IncludeView` `ExcludeView` atrybutów i dla typów, jak również dla poszczególnych członków.  

### <a name="displaystring"></a><a name="BKMK_DisplayString"></a> Klasie  
 `DisplayString`Element określa ciąg, który ma być pokazywany jako wartość zmiennej. Akceptuje dowolne ciągi zmieszane z wyrażeniami. Wszystkie elementy wewnątrz nawiasów klamrowych są interpretowane jako wyrażenie. Na przykład wpis taki `DisplayString` jak:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 Oznacza, że zmienne typu `CPoint` są wyświetlane w następujący sposób:  

 ![Korzystanie z elementu DisplayString](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 W `DisplayString` wyrażeniu `x` i `y` , które są elementami członkowskimi `CPoint` , znajdują się wewnątrz nawiasów klamrowych i dlatego ich wartości są oceniane. W wyrażeniu pokazano również, jak można wyjść z nawiasów klamrowych przy użyciu podwójnych nawiasów klamrowych ( `{{` lub `}}` ).  

> [!NOTE]
> `DisplayString`Element jest jedynym elementem, który akceptuje dowolne ciągi i składnię nawiasów klamrowych. Wszystkie inne elementy wizualizacji akceptują tylko wyrażenia, które są oceniane przez debuger.  

### <a name="stringview"></a><a name="BKMK_StringView"></a> StringView  
 `StringView`Element definiuje wyrażenie, którego wartość ma zostać wysłana do wbudowanego wizualizatora tekstu. Załóżmy na przykład, że dla typu jest dostępna następująca Wizualizacja `ATL::CStringT` :  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 `CStringT`Obiekt wygląda następująco:  

 ![CStringT — element klasy DisplayString](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Wizualizacja wyświetla `CStringT` obiekt w oknie zmiennych w następujący sposób:  

 Dodanie `StringView` elementu wskazuje debugerowi, że ta wartość może być wyświetlana przez wizualizację tekstu:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Zwróć uwagę na ikonę lupy widoczną obok poniższej wartości. Wybranie ikony spowoduje uruchomienie wizualizatora tekstu, który będzie wyświetlał ciąg, który `m_pszData` wskazuje.  

 ![CStringT danych za pomocą wizualizatora StringView](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
> Należy zauważyć, że wyrażenie `{m_pszData,su}` zawiera specyfikator formatu języka C++, `su` Aby wyświetlić wartość jako ciąg Unicode. Aby uzyskać więcej informacji, zobacz [specyfikatory formatu w języku C++](../debugger/format-specifiers-in-cpp.md) .  

### <a name="expand"></a><a name="BKMK_Expand"></a> Rozszerzone  
 `Expand`Węzeł jest używany do dostosowywania elementów podrzędnych typu wizualizacji, gdy użytkownik poszerzy ją w oknach zmiennych. Akceptuje listę węzłów podrzędnych, które definiują elementy podrzędne.  

 `Expand`Węzeł jest opcjonalny.  

- Jeśli `Expand` węzeł nie jest określony w wpisie wizualizacji, używane są domyślne reguły rozszerzania programu Visual Studio.  

- Jeśli `Expand` węzeł jest określony bez węzłów podrzędnych, typ nie będzie rozwijany w oknach debugera.  

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Rozszerzenie elementu  
 `Item`Element to najbardziej podstawowy i najbardziej typowy element, który ma być używany w `Expand` węźle. `Item` definiuje pojedynczy element podrzędny. Załóżmy na przykład, że masz `CRect` klasę z `top` , `left` , `right` , i `bottom` jako pola i następujący wpis wizualizacji:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 `CRect`Typ będzie wyglądać następująco:  

 ![CRect z rozwinięciem elementu elementu](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Wyrażenia określone w `Width` i `Height` elementy są oceniane i wyświetlane w kolumnie wartość. `[Raw View]`Węzeł jest automatycznie tworzony przez debuger za każdym razem, gdy zostanie użyte rozszerzenie niestandardowe. Jest rozwinięty na poniższym zrzucie ekranu, aby pokazać, jak nieprzetworzony widok obiektu różni się od jego wizualizacji. Domyślne Rozszerzanie programu Visual Studio tworzy poddrzewo dla klasy bazowej i wyświetla wszystkie elementy członkowskie danych klasy podstawowej jako elementy podrzędne.  

> [!NOTE]
> Jeśli wyrażenie elementu Item wskazuje typ złożony, `Item` sam węzeł jest rozwijany.  

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> Rozwinięcie ArrayItems  
 Użyj `ArrayItems` węzła, aby debuger programu Visual Studio interpretuje typ jako tablicę i wyświetlał jego poszczególne elementy. Wizualizacja dla programu `std::vector` jest dobrym przykładem:  

```xml  
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  

```  

 A `std::vector` pokazuje poszczególne elementy po rozwinięciu w oknie zmiennych:  

 ![std:: Vector przy użyciu rozszerzenia ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 W `ArrayItems` węźle musi znajdować się co najmniej:  

1. `Size`Wyrażenie (które musi oszacować do liczby całkowitej), aby debuger mógł zrozumieć długość tablicy  

2. `ValuePointer`Wyrażenie, które powinno wskazywać na pierwszy element (który musi być wskaźnikiem typu elementu, który nie jest `void*` ).  

   Wartość domyślna dolnej granicy tablicy wynosi 0. Wartość można zastąpić za pomocą `LowerBound` elementu (przykłady można znaleźć w plikach. Natvis dostarczanych z programem Visual Studio).  

   Teraz można używać `[]` operatora z `ArrayItems` rozwinięciem, na przykład `vector[i]` . Operatora [] można używać razem z dowolną wizualizacją tablicy jednowymiarowej, która używa `ArrayItems` lub `IndexListItems` , nawet jeśli sam typ nie zezwala na ten operator (na przykład `CATLArray` ).  

   Można również określić wielowymiarowe tablice. Debuger potrzebuje zaledwie nieco więcej informacji, aby prawidłowo wyświetlać elementy podrzędne w tym przypadku:  

```xml  
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  

```  

 `Direction` Określa, czy tablica jest kolejnością w wierszu czy główną kolumną. `Rank` Określa rangę tablicy. `Size`Element akceptuje niejawny `$i` parametr, który zastępuje indeks wymiaru, aby znaleźć długość tablicy w tym wymiarze. Na przykład w poprzednim przykładzie powyżej wyrażenie `_M_extent.M_base[0]` powinno zawierać długość wymiaru 0th, `_M_extent._M_base[1]` 1 i tak dalej.  

 Poniżej przedstawiono sposób, w jaki obiekt dwuwymiarowy `Concurrency::array` wygląda w debugerze:  

 ![Dwuwymiarowa tablica z rozwinięciem ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Rozwinięcie IndexListItems  
 Można użyć `ArrayItems` rozszerzania, tylko wtedy, gdy elementy tablicy są ułożone w sposób ciągły w pamięci. Debuger przechodzi do następnego elementu, po prostu zwiększając jego wskaźnik do bieżącego elementu. Aby obsługiwać przypadki, w których należy manipulować indeksem w węźle Value, `IndexListItems` można użyć węzłów. Oto Wizualizacja przy użyciu `IndexListItems` węzła:  

```xml  
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  

```  

 Teraz można używać `[]` operatora z `IndexListItems` rozwinięciem, na przykład `vector[i]` . `[]`Operatora można używać z dowolną wizualizacją tablicy jednowymiarowej, która używa `ArrayItems` lub `IndexListItems` , nawet jeśli sam typ nie zezwala na ten operator (na przykład `CATLArray` ).  

 Jedyną różnicą między `ArrayItems` i `IndexListItems` jest `ValueNode` oczekiwanie pełne wyrażenie do i<sup>ty</sup> elementu z niejawnym `$i` parametrem.  

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Rozwinięcie LinkedListItems  
 Jeśli typ wizualizacji reprezentuje listę połączoną, debuger może wyświetlić jego elementy podrzędne przy użyciu `LinkedListItems` węzła. Oto Wizualizacja dla tego `CAtlList` typu za pomocą tej funkcji:  

```xml  
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  

```  

 `Size`Element odnosi się do długości listy. `HeadPointer` wskazuje na pierwszy element, `NextPointer` odnosi się do następnego elementu i `ValueNode` odwołuje się do wartości elementu.  

- `NextPointer`Wyrażenia i `ValueNode` są oceniane w kontekście elementu węzła listy połączonej, a nie typu listy nadrzędnej. W powyższym przykładzie `CAtlList` ma `CNode` klasę (znalezioną w elemencie `atlcoll.h` ), która reprezentuje węzeł listy połączonej. `m_pNext` i `m_element` są polami tej `CNode` klasy, a nie z `CAtlList` klasą.  

- `ValueNode`Może pozostać puste lub musi `this` odwoływać się do węzła listy połączonej.  

#### <a name="customlistitems-expansion"></a>Rozwinięcie CustomListItems  
 `CustomListItems`Rozszerzenie umożliwia pisanie logiki niestandardowej do przechodzenia ze strukturą danych, taką jak Hashtable. Należy użyć `CustomListItems` do wizualizacji struktur danych, w których wszystko, czego potrzebujesz do oszacowania, jest można wyrazić elementu za pośrednictwem wyrażeń języka C++, ale nie pasuje do Mold dla `ArrayItems` , `TreeItems` , lub `LinkedListItems.`  

 Wizualizator dla CAtlMap to doskonały przykład, gdzie `CustomListItems` jest odpowiedni.  

```xml  
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  

        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Rozwinięcie TreeItems  
 Jeśli typ wizualizacji reprezentuje drzewo, debuger może przeprowadzić drzewo i wyświetlić jego elementy podrzędne przy użyciu `TreeItems` węzła. Oto Wizualizacja dla tego `std::map` typu za pomocą tej funkcji:  

```xml  
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  

```  

 Składnia jest bardzo podobna do `LinkedListItems` węzła. `LeftPointer`, `RightPointer` , i `ValueNode` są oceniane w kontekście klasy węzła drzewa i `ValueNode` mogą pozostać puste lub muszą `this` odwoływać się do samego węzła drzewa.  

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Rozwinięcie ExpandedItem  
 `ExpandedItem`Element może służyć do generowania zagregowanego widoku podrzędnego przez wyświetlanie właściwości klas bazowych lub składowych danych, tak jakby były elementami podrzędnymi typu wizualizacji. Określone wyrażenie jest oceniane i węzły podrzędne wyniku są dołączane do podrzędnej listy wizualizacji typu. Załóżmy na przykład, że mamy typ inteligentnego wskaźnika, `auto_ptr<vector<int>>` który zwykle będzie wyświetlany jako:  

 ![Auto&#95;PTR&#60;wektor&#60;int&#62;&#62; domyślne rozwinięcie](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Aby wyświetlić wartości wektora, należy przejść do szczegółów dwóch poziomów w oknie zmiennych przechodzącym przez _Myptr elementu członkowskiego. Poprzez dodanie `ExpandedItem` elementu można wyeliminować `_Myptr` zmienną z hierarchii i bezpośrednio przeglądać elementy wektorowe::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![Funkcja Auto&#95;PTR&#60;wektor&#60;int&#62;&#62; rozwinięcie ExpandedItem](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 W poniższym przykładzie pokazano, jak agregować właściwości z klasy podstawowej w klasie pochodnej. Załóżmy, że `CPanel` Klasa pochodzi od `CFrameworkElement` . Zamiast powtarzania właściwości, które pochodzą z klasy bazowej `CFrameworkElement` , `ExpandedItem` węzeł umożliwia dołączenie tych właściwości do podrzędnej listy `CPanel` klasy. Specyfikator formatu **ND** , który wyłącza dopasowanie wizualizacji dla klasy pochodnej, jest tutaj niezbędny. W przeciwnym razie wyrażenie `*(CFrameworkElement*)this` spowoduje `CPanel` ponowne zastosowanie wizualizacji, ponieważ domyślne reguły dopasowywania typów są traktowane jako najbardziej odpowiednie. Użycie specyfikatora formatu **ND** powoduje, że debuger używa wizualizacji klasy bazowej lub domyślnego rozszerzania klasy bazowej, jeśli klasa bazowa nie ma wizualizacji.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Rozwinięcie elementu syntetycznego  
 Gdzie `ExpandedItem` element udostępnia Flatter widok danych, eliminując hierarchie, `Synthetic` węzeł jest odwrotny. Umożliwia tworzenie sztucznego elementu podrzędnego (czyli elementu podrzędnego, który nie jest wynikiem wyrażenia). Ten element podrzędny może zawierać własne elementy podrzędne. W poniższym przykładzie Wizualizacja dla `Concurrency::array` typu używa `Synthetic` węzła, aby pokazać użytkownikowi komunikat diagnostyczny:  

```xml  
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  

```  

 ![Concurrency:: Array z Sythentic element expansio](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

### <a name="hresult"></a><a name="BKMK_HResult"></a> Wynik  
 `HResult`Element umożliwia dostosowanie informacji wyświetlanych dla HRESULT w oknach debugera. `HRValue`Element musi zawierać 32-bitową wartość HRESULT, która ma zostać dostosowana. `HRDescription`Element zawiera informacje, które są wyświetlane w debugerze.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

### <a name="uivisualizer"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer  
 `UIVisualizer`Element rejestruje wtyczkę wizualizacji graficznej przy użyciu debugera. Wtyczka wizualizatora graficznego tworzy okno dialogowe lub inny interfejs do wyświetlania zmiennej lub obiektu w sposób, który jest odpowiedni dla typu danych. Wtyczka wizualizatora musi zostać utworzona jako [pakietu VSPackage](../extensibility/internals/vspackages.md) i musi uwidaczniać usługę, która może być używana przez debuger. Plik. Natvis zawiera informacje rejestracyjne dla wtyczki, takie jak jej nazwa, identyfikator GUID uwidocznionej usługi, a także typy, które można wizualizować.  

 Oto przykład elementu UIVisualizer:  

```xml  

<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  

 A `UIVisualizer` jest identyfikowany przez `ServiceId`  -  `Id` parę atrybutów. `ServiceId` jest identyfikatorem GUID usługi uwidocznionej przez pakiet wizualizatora, `Id` jest unikatowym identyfikatorem, który może służyć do rozróżniania wizualizatorów, jeśli usługa zawiera więcej niż jeden wizualizator. W powyższym przykładzie ta sama usługa wizualizatora udostępnia dwa Wizualizatory.  

 Ten `MenuName` atrybut jest widoczny dla użytkowników jako nazwa wizualizatora po otwarciu menu rozwijanego obok ikony lupy w oknach zmiennych debugera, na przykład:  

 ![Menu skrótów menu UIVisualizer](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 Każdy typ zdefiniowany w pliku Natvis musi jawnie zawierać Wizualizatory interfejsu użytkownika, które mogą je wyświetlić. Debuger dopasowuje odwołania wizualizatora w wpisach typu w celu dopasowania typów do zarejestrowanych wizualizatorów. Na przykład następujący wpis typu w odniesieniu do `std::vector` UIVisualizer znajduje się w powyższym przykładzie.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Można zobaczyć przykład UIVisualizer w rozszerzeniu Obserwuj obraz używanym do wyświetlania map bitowych w pamięci: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>CustomVisualizer, element  
 `CustomVisualizer` jest punktem rozszerzalności, który określa rozszerzenie VSIX, które można napisać, aby sterować wizualizacją w kodzie, który działa w programie Visual Studio. Aby uzyskać więcej informacji na temat pisania rozszerzeń VSIX, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Pisanie niestandardowego wizualizatora to znacznie więcej pracy niż w przypadku pisania definicji pliku Natvis XML, ale nie są one zgodne z ograniczeniami, które są obsługiwane przez Natvis lub nie są obsługiwane. Wizualizacje niestandardowe mają dostęp do pełnego zestawu interfejsów API rozszerzalności debugera, które mogą służyć do wykonywania zapytań i modyfikowania procesu debugowanego obiektu lub komunikowania się z innymi częściami programu Visual Studio.  

 Można użyć `Condition` `IncludeView` atrybutów, i `ExcludeView` dla elementów CustomVisualizer.
