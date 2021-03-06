---
title: Wyświetlanie zdarzeń za pomocą IntelliTrace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffbe0b8365948dc5a69edca390f308cb55ba5a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62929399"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Wyświetlanie zdarzeń za pomocą IntelliTrace w Visual Studio Enterprise (C#, Visual Basic)

Za pomocą IntelliTrace można zbierać informacje o określonych zdarzeniach lub kategoriach zdarzeń albo o pojedynczych wywołaniach funkcji oprócz zdarzeń. Poniższe procedury pokazują, jak to zrobić.

Możesz użyć IntelliTrace w wersji Visual Studio Enterprise, ale nie wersji Professional ani Community.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Konfigurowanie IntelliTrace

Możesz wypróbować debugowanie za pomocą tylko zdarzeń IntelliTrace. Zdarzenia IntelliTrace to zdarzenia debugera, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe. Należy włączyć lub wyłączyć określone zdarzenia, aby kontrolować zdarzenia, które IntelliTrace rekordy przed rozpoczęciem debugowania. Aby uzyskać więcej informacji, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md).

- Włącz zdarzenie IntelliTrace, aby uzyskać dostęp do plików. Przejdź do strony **narzędzia > opcje > IntelliTrace > IntelliTrace Events** i rozwiń kategorię **plik** . Sprawdź kategorię zdarzenia **pliku** . Powoduje to sprawdzenie wszystkich zdarzeń plików (dostęp, zamykanie, usuwanie).

## <a name="create-your-app"></a>Tworzenie aplikacji

1. Utwórz aplikację konsolową języka C#. W pliku Program.cs Dodaj następującą `using` instrukcję:

    ```csharp
    using System.IO;
    ```

2. Utwórz <xref:System.IO.FileStream> w metodzie Main, Odczytaj z niej, zamknij ją i Usuń plik. Dodaj kolejny wiersz, aby ustawić punkt przerwania:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Ustaw punkt przerwania na `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Rozpocznij debugowanie i Wyświetl zdarzenia IntelliTrace

1. Rozpocznij debugowanie w zwykły sposób. (Naciśnij klawisz **F5** lub kliknij pozycję **Debuguj > Rozpocznij debugowanie**).

    > [!TIP]
    > Zachowaj otwarte okna **lokalne** i **Autotekstu** w trakcie debugowania, aby zobaczyć i zapisać wartości w tych oknach.

2. Wykonywanie jest zatrzymane w punkcie przerwania. Jeśli nie widzisz okna **Narzędzia diagnostyczne** , kliknij pozycję **Debuguj > zdarzenia IntelliTrace systemu Windows >**.

    W oknie **Narzędzia diagnostyczne** Znajdź kartę **zdarzenia** (powinny być widoczne 3 karty, **zdarzenia**, **użycie pamięci**i **użycie procesora**). Karta **zdarzenia** zawiera chronologiczną listę zdarzeń kończącą się ostatnim zdarzeniem, zanim debuger przerwał wykonywanie operacji. Powinno zostać wyświetlone zdarzenie o nazwie **WordSearchInputs.txtdostępu **.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace — Update1")

3. Wybierz zdarzenie, aby rozwinąć jego szczegóły.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")

    Możesz wybrać link ścieżki, aby otworzyć plik. Jeśli pełna nazwa ścieżki jest niedostępna, pojawi się okno dialogowe **Otwórz plik** .

    Kliknij pozycję **Aktywuj debugowanie historyczne**, które ustawia kontekst debugera na czas zebrania wybranego zdarzenia, pokazując dane historyczne w **stosie wywołań**, **zmiennych lokalnych** i innych oknach debugera. Jeśli kod źródłowy jest dostępny, program Visual Studio przesuwa wskaźnik do odpowiedniego kodu w oknie źródłowym, aby można było go przeanalizować.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging — Update1")

4. Jeśli usterka nie została znaleziona, spróbuj sprawdzić inne zdarzenia prowadzące do błędu. Istnieje również możliwość rejestrowania informacji o wywołaniach IntelliTrace, dzięki czemu można przechodzić przez wywołania funkcji.

## <a name="next-steps"></a>Następne kroki

Możesz użyć niektórych zaawansowanych funkcji IntelliTrace z debugowaniem historycznym:

- Aby wyświetlić migawki, zobacz [Inspekcja poprzednich stanów aplikacji przy użyciu IntelliTrace](../debugger/view-historical-application-state.md)
- Aby dowiedzieć się, jak zbadać zmienne i poruszać się po kodzie, zobacz [Inspekcja aplikacji za pomocą debugowania historycznego](../debugger/historical-debugging-inspect-app.md)
