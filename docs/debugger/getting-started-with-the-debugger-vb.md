---
title: Dowiedz się, jak debugowanie kodu języka Visual Basic, za pomocą debugera programu Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: debug-experiment
ms.date: 11/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f568c5785af1917827646d232ef3c6c8f0ad41b
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2018
ms.locfileid: "52825476"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Samouczek: Dowiedz się, jak debugowanie kodu języka Visual Basic, za pomocą programu Visual Studio

W tym artykule przedstawiono funkcje debugera programu Visual Studio w przewodnik krok po kroku. Jeśli potrzebujesz wyższego poziomu widoku funkcji debugera, zobacz [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md). Gdy użytkownik *debugowanie aplikacji*, zwykle oznacza to, że aplikacja jest uruchamiana w debugerze. Gdy to zrobisz, debuger zapewnia wiele sposobów, aby zobaczyć, co kod robi podczas jego uruchamiania. Można przejść przez kod i przyjrzyj się wartości przechowywane w zmiennych, można ustawić zegarki dla zmiennych, aby zobaczyć, kiedy zmienić wartości, można zbadać ścieżki wykonywania kodu, czy gałąź kodu nie jest uruchomiona, i tak dalej. Jeśli po raz pierwszy, próbujących przeprowadzić debugowania kodu, warto przeczytać [debugowania dla początkujących](../debugger/debugging-absolute-beginners.md) przed przejściem w tym artykule.

| | |
|---------|---------|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) debugowania, w którym pokazano podobne kroki. |

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom debuger i identyfikować punkty przerwania.
> * Dowiedz się więcej poleceń, aby przejść przez kod w debugerze
> * Sprawdzanie zmiennych w oknach debugera i porady dotyczące danych
> * Sprawdź stos wywołań

## <a name="prerequisites"></a>Wymagania wstępne

* Konieczne jest posiadanie programu Visual Studio 2017 i **programowanie aplikacji klasycznych dla platformy .NET** obciążenia.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

    Jeśli musisz zainstalować obciążenie, ale już program Visual Studio, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe (wybierz **pliku**  >  **Nowe** > **projektu**). Uruchamia Instalatora programu Visual Studio. Wybierz opcję. **Netto programowanie aplikacji klasycznych** obciążenia, wybierz **Modyfikuj**.

## <a name="create-a-project"></a>Tworzenie projektu

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

2. W obszarze **języka Visual Basic**, wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **aplikacja Konsolowa**.

    Jeśli nie widzisz **aplikację Konsolową** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz *programowanie aplikacji klasycznych dla platformy .NET** obciążenie, następnie wybierz **Modyfikuj**.

3. Wpisz nazwę, takich jak **get pracę debugowanie** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

4. W *Program.cs*, Zastąp następujący kod

    ```vb
    Module Module1

        Sub Main()
        End Sub

    End Module
    ```

    przy użyciu tego kodu:

    ```vb
    Imports System
    Imports System.Collections.Generic

    Public Class Shape

      ' A few example members
        Public Property X As Integer
            Get
                Return X
            End Get
            Set
            End Set
        End Property

        Public Property Y As Integer
            Get
                Return Y
            End Get
            Set
            End Set
        End Property

        Public Property Height As Integer
            Get
                Return Height
            End Get
            Set
            End Set
        End Property

        Public Property Width As Integer
            Get
                Return Width
            End Get
            Set
            End Set
        End Property

        ' Virtual method
        Public Overridable Sub Draw()
            Console.WriteLine("Performing base class drawing tasks")
        End Sub
    End Class

    Public Class Circle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a circle...
            Console.WriteLine("Drawing a circle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Rectangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Triangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a triangle...
            Console.WriteLine("Drawing a trangle")
            MyBase.Draw()
        End Sub
    End Class

    Module Module1

        Sub Main(ByVal args() As String)

            Dim shapes = New List(Of Shape) From
            {
                New Rectangle,
                New Triangle,
                New Circle
            }

            For Each shape In shapes
                shape.Draw()
            Next
            ' Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.")
            Console.ReadKey()

        End Sub

    End Module

    ' Output:
    '    Drawing a rectangle
    '    Performing base class drawing tasks
    '    Drawing a triangle
    '    Performing base class drawing tasks
    '    Drawing a circle
    '    Performing base class drawing tasks
    ```

## <a name="start-the-debugger"></a>Uruchom debuger!

1. Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub **Rozpocznij debugowanie** przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie ") na pasku narzędzi debugowania.

     **F5** uruchamia aplikacji za pomocą debugera dołączony do aplikacji, przetwarzania, ale teraz możemy jeszcze nie wykonano żadnych specjalnych badanie kodu. Dlatego właśnie ładowania aplikacji, a zostaną wyświetlone dane wyjściowe konsoli.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     W tym samouczku utworzymy Przyjrzyj się bliżej aplikacji przy użyciu debugera i pobrać spojrzenie na debugera funkcji.

2. Przerwij debugowanie, naciskając klawisz czerwony stop ![Zatrzymaj debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymaj debugowanie") przycisku.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustaw punkt przerwania i uruchomić debuger

1. W `For Each` pętli z `Main` funkcji, ustaw punkt przerwania, klikając w lewy margines następującego kodu:

    `shape.Draw()`

    Pojawi się czerwone kółko, gdzie ustawić punkt przerwania.

    ![Ustaw punkt przerwania](../debugger/media/get-started-set-breakpoint-vb.png)

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu. 

2. Naciśnij klawisz **F5** lub **Rozpocznij debugowanie** przycisku! [ Uruchamianie debugowania] (.. "Rozpocznij debugowanie", aplikacja rozpoczyna /Debugger/Media/dbg-Tour-Start-Debugging.PNG i debuger uruchamia wiersz kodu, gdzie ustawić punkt przerwania.

    ![Trafiony punkt przerwania](../debugger/media/get-started-hit-breakpoint-vb.png)

    Żółta strzałka reprezentuje instrukcji, w której debuger wstrzymany, również zawiesza wykonywanie aplikacji w tym samym punkcie (Ta instrukcja nie jeszcze wykonane).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **F5** uruchomienie debugera i przerywa w pierwszym punkcie przerwania. W przeciwnym razie **F5** będzie nadal działać w aplikacji do następnego punktu przerwania.

    Punkty przerwania są to przydatne, gdy wiadomo, wiersz kodu lub sekcji kodu, który chcesz zbadać szczegółowo.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Przechodzenie do kodu w debugerze, przy użyciu poleceń krokowych

Przede wszystkim, używamy skróty klawiaturowe w tym miejscu, ponieważ jest to dobry sposób, aby uzyskać szybkie na wykonywanie aplikacji w debugerze (równoważne polecenia takie jak menu poleceń są wyświetlane w nawiasach).

1. Podczas wstrzymania w `shape.Draw` metody wywołania w `Main` funkcji, naciśnij klawisz **F11** (lub wybierz **Debuguj > Step Into**) aby przejść do kodu, aby uzyskać `Rectangle` klasy.

     ![Użyj F11, aby kod Step Into](../debugger/media/get-started-f11-vb.png "F11 Step Into")

     Jest F11 **Step Into** poleceń i prowadzi aplikacji wykonanie jednej instrukcji w danym momencie. F11 jest dobrym sposobem na zbadanie przepływ wykonania w najbardziej szczegółowy. (Aby poruszać się szybciej za pomocą kodu, firma Microsoft dowiesz się także inne opcje również.) Domyślnie debuger pomija nad kodem niezwiązanych z użytkownikiem (Jeśli chcesz, aby uzyskać więcej informacji, zobacz [tylko mój kod](../debugger/just-my-code.md)).

2. Naciśnij klawisz **F10** (lub wybierz **Debuguj > Step Over**) kilka razy dopóki debuger zatrzymuje się na `MyBase.Draw` wywołania metody, a następnie klawisz **F10** jeszcze raz.

     ![Użyj F10 kodowi Step Over](../debugger/media/get-started-step-over-vb.png "F10 Step Over")

     Zauważ teraz, że debuger nie wkracza w `Draw` metody klasy bazowej (`Shape`). **F10** wyjście z kodu bez przechodzenie krok po kroku do funkcji lub metody w kodzie aplikacji (nadal wykonuje kod). Naciskając klawisz F10 `MyBase.Draw` wywołania metody (zamiast **F11**), firma Microsoft pominięty Kod implementacji dla `MyBase.Draw` (które firma Microsoft nie interesują teraz może).

## <a name="navigate-code-using-run-to-click"></a>Przechodzenie do kodu przy użyciu polecenia Uruchom do kliknięcia

1. W edytorze kodu, przewiń w dół, umieść kursor nad `Console.WriteLine` method in Class metoda `Triangle` klasy do momentu zielony **uruchamianie do kliknięcia** przycisk ![uruchamianie do kliknięcia](../debugger/media/dbg-tour-run-to-click.png "RunToClick")pojawia się po lewej stronie.

     ![Użyj Uruchom do kliknięcia funkcji](../debugger/media/get-started-run-to-click-vb.png "uruchamianie do kliknięcia")

   > [!NOTE]
   > **Uruchamianie do kliknięcia** przycisk jest nowego w programie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Jeśli nie widzisz przycisku zieloną strzałkę, użyj **F11** w tym przykładzie zamiast Aby awansować debugera we właściwym miejscu.

2. Kliknij przycisk **uruchamianie do kliknięcia** przycisk ![uruchamianie do kliknięcia](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Za pomocą tego przycisku jest podobna do ustawienia tymczasowy punkt przerwania. **Uruchamianie do kliknięcia** jest przydatna do poruszania się szybko w obrębie regionu widoczne dla kodu aplikacji (możesz kliknąć dowolny otwarty plik).

    Przejście do debugera `Console.WriteLine` implementacji metody dla `Triangle` klasy.

    Podczas wstrzymania, zauważysz błąd pisowni! Dane wyjściowe "Rysowanie trangle" jest błędnie wpisana. Będziemy mogli ją naprawić miejscu podczas uruchamiania aplikacji w debugerze.

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

1. Klikaj "Rysowanie trangle", a następnie wpisz korekty, zmiana "trangle" na "trójkąt".

1. Naciśnij klawisz **F11** raz i możesz zobaczyć ponownie przejście debugera.

    > [!NOTE]
    > W zależności od tego, jakiego typu kod edytowany w debugerze może zostać wyświetlony komunikat ostrzegawczy. W niektórych scenariuszach kod należy ponownie skompilować, zanim będzie można kontynuować.

## <a name="step-out"></a>Wyjdź

Załóżmy, że wszystko będzie gotowe badanie `Draw` method in Class metoda `Triangle` klasy i, o których chcesz uzyskiwać dostęp do najważniejszych funkcji, ale pozostanie w debugerze. Można to zrobić za pomocą **Step Out** polecenia.

1. Naciśnij klawisz **Shift** + **F11** (lub **Debuguj > Wyjdź**).

     To polecenie wznawia działanie aplikacji (i umożliwia przejście do) do momentu zwraca bieżącą funkcję.

     Powinien nastąpić powrót `For Each` pętli w `Main` metody.

## <a name="restart-your-app-quickly"></a>Szybko Uruchom ponownie swoją aplikację

Kliknij przycisk **ponowne uruchomienie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku na pasku narzędzi debugowania (**Ctrl** + **Shift**   +  **F5**).

Po naciśnięciu klawisza **ponowne uruchomienie**, można zaoszczędzić czas i zatrzymywanie aplikacji oraz ponownego uruchamiania debugera. Debuger wstrzymuje na pierwszy punkt przerwania zostanie osiągnięty przez wykonywanie kodu.

Debuger zatrzymuje się ponownie w punkcie przerwania, możesz ustawić na `shape.Draw()` metody.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych z poradami do danych

Funkcje, które pozwalają na sprawdzanie zmiennych są jednymi z najbardziej przydatnych funkcjach debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz sprawdzić, czy zmienne są przechowywane wartości, których można oczekiwać, aby użytkownicy posiadali w danym momencie.

1. Gdy wstrzymana na `shape.Draw()` metodę, umieść kursor nad `shapes` obiektu i wyświetlić jej wartości domyślnej właściwości `Count` właściwości.

1. Rozwiń `shapes` obiektu, aby wyświetlić wszystkie właściwości, takie jak pierwszy indeks tablicy `[0]`, który ma wartość `Rectangle`.

     ![Wyświetl etykietki danych](../debugger/media/get-started-data-tip-vb.png "wyświetlanie etykietki danych")

    Można rozwinąć obiektów, aby wyświetlić ich właściwości, takie jak `Height` właściwości prostokąta.

    Często podczas debugowania, chcesz, aby szybko sprawdzić wartości właściwości obiektów i porady dotyczące danych są dobrym sposobem, aby to zrobić.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

1. Przyjrzyj się **Autos** okna w dolnej części edytora kodu.

     ![Sprawdzanie zmiennych w oknie Autos](../debugger/media/get-started-autos-window-vb.png "okno zmiennych automatycznych")

    W **Autos** oknie zostanie wyświetlony, zmienne i ich bieżącą wartość. **Autos** okno pokazuje wszystkie zmienne używane w bieżącym wierszu lub poprzedni wiersz (zobacz dokumentację dla zachowania specyficzne dla języka).

2. Następnie Przyjrzyj się **lokalne** okna, na karcie obok **automatyczne** okna.

    **Lokalne** okno zawiera zmienne, które znajdują się w bieżącej [zakres](https://www.wikipedia.org/wiki/Scope_(computer_science)), oznacza to, że bieżący kontekst wykonywania.

## <a name="set-a-watch"></a>Ustawianie wyrażenia kontrolnego

1. W oknie edytora głównego kodu, kliknij prawym przyciskiem myszy `shapes` obiektu, a następnie wybierz **Dodaj czujkę**.

    **Obejrzyj** zostanie otwarte okno w dolnej części edytora kodu. Możesz użyć **Obejrzyj** okna, aby określić zmienną (lub wyrażenie), który chcesz śledzić na.

    Teraz masz wyrażenia kontrolnego nastavit `shapes` obiektu, aby sprawdzić jej wartość zmienić podczas przeglądania przez debuger. W przeciwieństwie do innych zmiennych systemu windows **Obejrzyj** okno zawsze zawiera zmienne, obserwujesz (są one wygaszone się kiedy poza zakresem).

## <a name="examine-the-call-stack"></a>Sprawdź stos wywołań

1. Gdy został wstrzymany w `For Each` pętli, kliknij przycisk **stos wywołań** okno, które jest domyślnie otwarty w dolnym okienku po prawej stronie.

2. Kliknij przycisk **F11** kilka razy, aż zostanie wyświetlony debugera wstrzymywania w `MyBase.Draw` metody `Rectangle` klasy w edytorze kodu. Przyjrzyj się **stos wywołań** okna.

    ![Sprawdź stos wywołań](../debugger/media/get-started-call-stack-vb.png "ExamineCallStack")

    **Stos wywołań** okno pokazuje kolejność, w którym są wprowadzenie wywoływane metody i funkcje. Górny wiersz zawiera bieżącą funkcję ( `Rectangle.Draw` metody w tej aplikacji). Drugi wiersz wskazuje, że `Rectangle.Draw` została wywołana z `Main` funkcji i tak dalej.

   > [!NOTE]
   > **Stos wywołań** jest podobne do perspektywy debugowania w niektórych środowiskach IDE, takich jak Eclipse.

    Stos wywołań jest dobrym sposobem na badania i informacje na temat wykonywania przepływu aplikacji.

    Możesz kliknąć dwukrotnie wiersz kodu, aby przyjrzeć się kodu źródłowego i zmienia także bieżący zakres kontrolowanym przez debuger. Ta akcja nie wcześniejsze debugera.

    Można również użyć menu kliknij prawym przyciskiem myszy **stos wywołań** okna, aby wykonywać inne czynności. Na przykład, wstawianie punktów przerwania do określonych funkcji, przejdź do debugera przy użyciu **Uruchom do kursora**i przejdź zbadanie kodu źródłowego. Aby uzyskać więcej informacji, zobacz [jak: Sprawdź stos wywołań](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmień przepływ wykonania

1. Za pomocą debugera został wstrzymany w `MyBase.Draw` wywołanie metody `Rectangle` klasy, za pomocą myszy Pobierz żółta strzałka (wskaźnik wykonania) po lewej stronie, a żółta strzałka w górę o jeden wiersz, aby przenieść `Console.WriteLine` wywołania metody.

1. Naciśnij klawisz **F11**.

    Debuger umożliwia ponowne wykonanie `Console.WriteLine` — metoda (widoczna zduplikowane dane wyjściowe w danych wyjściowych okna konsoli).

    Zmieniając przepływ wykonania, można wykonać czynności, jak przetestować różne ścieżki wykonywania lub uruchom ponownie kodu bez ponownego uruchamiania debugera.

    > [!WARNING]
    > Często muszą być ostrożnym z tej funkcji, a następnie zostanie wyświetlone ostrzeżenie w etykietce narzędzia. Zbyt mogą pojawić się inne ostrzeżenia. Przeniesienie wskaźnika nie można przywrócić aplikację do wcześniejszego stanu aplikacji.

1. Naciśnij klawisz **F5** ma kontynuować wykonywanie aplikacji.

    Gratulujemy wykonanie kroków tego samouczka!

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób uruchamiania debugera, Przechodź przez kod i Sprawdź zmienne. Możesz chcieć wysokiego poziomu poznać funkcje debugera, wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)