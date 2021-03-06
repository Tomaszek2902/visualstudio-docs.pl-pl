---
title: 'Przewodnik: korzystanie z interfejsów API profilera | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5fc0f5a11d29fdb1ee570dc32066fdd492ed8db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68871535"
---
# <a name="walkthrough-using-profiler-apis"></a>Wskazówki: korzystanie z interfejsów API profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przewodniku użyto aplikacji języka C# do zademonstrowania sposobu używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsów api narzędzia profilowania. Użyjesz interfejsów API profilera, aby ograniczyć ilość danych zbieranych podczas profilowania Instrumentacji.

 Kroki opisane w tym instruktażu dotyczą zwykle aplikacji C/C++. Dla każdego języka trzeba będzie odpowiednio skonfigurować środowisko kompilacji.

 Zazwyczaj należy rozpocząć analizowanie wydajności aplikacji przy użyciu profilowania przykładowych. Jeśli przykładowe Profilowanie nie zawiera informacji, które wykreślą wąskie gardło, profilowanie Instrumentacji może zapewnić wyższy poziom szczegółowości. Profilowanie Instrumentacji jest bardzo przydatne do badania interakcji wątku.

 Jednak wyższy poziom szczegółowości oznacza, że zbierane są więcej danych. Może się okazać, że profilowanie Instrumentacji tworzy duże pliki danych. Ponadto Instrumentacja może mieć wpływ na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie wartości danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md) i [zrozumienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)

 Program Visual Studio profiler umożliwia ograniczenie zbierania danych. Ten Instruktaż zawiera przykład sposobu ograniczania zbierania danych przy użyciu interfejsów API profilera. Profiler programu Visual Studio udostępnia interfejs API służący do kontrolowania zbierania danych z poziomu aplikacji.

 W przypadku kodu natywnego interfejsy API programu Visual Studio profiler są w VSPerf.dll. Plik nagłówkowy, VSPerf. h i Biblioteka Imports VSPerf. lib znajdują się w katalogu narzędzi Microsoft Visual Studio 9 \ Team Tools\Performance Tools.

 W przypadku kodu zarządzanego interfejs API profilera znajduje się w Microsoft.VisualStudio.Profiler.dll. Ta biblioteka DLL znajduje się w katalogu narzędzi Microsoft Visual Studio 9 \ Team Tools\Performance Tools. Aby uzyskać więcej informacji, zobacz [Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Wymagania wstępne
 W tym instruktażu przyjęto założenie, że wybór środowiska programistycznego jest skonfigurowany do obsługi debugowania i próbkowania. W poniższych tematach omówiono wymagania wstępne:

 [Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)

 [Instrukcje: odwołania do informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)

 Domyślnie po uruchomieniu profilera profiler zbiera dane na poziomie globalnym. Poniższy kod na początku programu powoduje wyłączenie profilowania globalnego.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Zbieranie danych można wyłączyć w wierszu polecenia bez użycia wywołania interfejsu API. W poniższych krokach przyjęto założenie, że środowisko kompilacji wiersza polecenia jest skonfigurowane do uruchamiania narzędzi profilowania i narzędzi deweloperskich. Obejmuje to ustawienia niezbędne dla VSInstr i VSPerfCmd. Zobacz narzędzia profilowania wiersza polecenia.

## <a name="limiting-data-collection-using-profiler-apis"></a>Ograniczanie zbierania danych przy użyciu interfejsów API profilera

#### <a name="to-create-the-code-to-profile"></a>Aby utworzyć kod do profilowania

1. Utwórz nowy projekt C# w programie Visual Studio lub użyj kompilacji wiersza polecenia w zależności od preferencji.

    > [!NOTE]
    > Kompilacja musi odwoływać się do biblioteki Microsoft.VisualStudio.Profiler.dll znajdującej się w katalogu narzędzi Microsoft Visual Studio 9 \ Team Tools\Performance Tools.

2. Skopiuj i wklej następujący kod do projektu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication2
    {
        class Program
        {
            public class A
            {
             private int _x;

             public A(int x)
             {
              _x = x;
             }

             public int DoNotProfileThis()
             {
              return _x * _x;
             }

             public int OnlyProfileThis()
             {
              return _x + _x;
             }

             public static void Main()
             {
            DataCollection.StopProfile(
            ProfileLevel.Global,
            DataCollection.CurrentId);
              A a;
              a = new A(2);
              int x;
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());
              DataCollection.StartProfile(
                  ProfileLevel.Global,
                  DataCollection.CurrentId);
              x = a.OnlyProfileThis();
              DataCollection.StopProfile(
                  ProfileLevel.Global,
                  DataCollection.CurrentId);
              Console.WriteLine("2 doubled is {0}", x);
             }
            }

        }
    }
    ```

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Aby zbierać i wyświetlać dane w środowisku IDE programu Visual Studio

1. Otwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowisko IDE. W menu **Analizuj** wskaż polecenie **Profiler**, a następnie wybierz pozycję **Nowa sesja wydajności.**

2. Dodaj skompilowany plik binarny do listy **targets** w oknie **Eksplorator wydajności** . Kliknij prawym przyciskiem myszy element **docelowy**, a następnie wybierz polecenie **Dodaj docelowy plik binarny**. Zlokalizuj plik binarny w oknie dialogowym **Dodaj docelowy plik binarny** , a następnie kliknij przycisk **Otwórz**.

3. Wybierz pozycję **Instrumentacja** z listy **Metoda** na pasku narzędzi **Eksplorator wydajności** .

4. Kliknij przycisk **Uruchom z profilem**.

    Profiler będzie Instrumentacją i wykonywaniem pliku binarnego oraz utworzyć plik raportu wydajności. Plik raportu wydajności zostanie wyświetlony w węźle **raporty** w **Eksplorator wydajności**.

5. Otwórz wynikowy plik raportu wydajności.

   Domyślnie po uruchomieniu profilera Profiler będzie zbierać dane na poziomie globalnym. Poniższy kod na początku programu powoduje wyłączenie profilowania globalnego.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Aby zbierać i wyświetlać dane w wierszu polecenia

1. Skompiluj wersję Debug przykładowego kodu, który został utworzony w procedurze "Tworzenie kodu do profilu" wcześniej w tym instruktażu.

2. Aby profilować aplikację zarządzaną, wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:

     **VsPefCLREnv /traceon**

3. Wpisz następujące polecenie:**VSInstr \<filename> . exe**

4. Wpisz następujące polecenie:**VSPerfCmd/Start: Trace/Output: \<filename> . vsp**

5. Wpisz następujące polecenie:**VSPerfCmd/globaloff**

6. Wykonaj swój program.

7. Wpisz następujące polecenie:**VSPerfCmd/shutdown**

8. Wpisz następujące polecenie:**VSPerfReport/calltrace: \<filename> . vsp**

     Plik CSV jest tworzony w bieżącym katalogu z wynikowymi danymi o wydajności.

## <a name="see-also"></a>Zobacz też

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)
- [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)