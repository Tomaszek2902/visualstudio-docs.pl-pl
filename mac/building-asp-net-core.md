---
title: Kompilowanie aplikacji ASP.NET Core
description: W tym artykule opisano, jak rozpocząć pracę z usługą ASP.NET w Visual Studio dla komputerów Mac, w tym instalację i tworzenie nowego projektu.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: 47ddfa11b4c05896037c1fb18e285d46fc79520b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88214621"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Tworzenie aplikacji platformy ASP.NET Core w programie Visual Studio dla komputerów Mac

ASP.NET Core to platforma typu "open source" i międzyplatformowa do tworzenia nowoczesnych, opartych na chmurze aplikacji internetowych, takich jak aplikacje sieci Web i usługi, aplikacje IoT i frontony mobilne. Aplikacje ASP.NET Core mogą być uruchamiane w [środowisku .NET Core](https://www.microsoft.com/net/core/platform) lub w środowisku uruchomieniowym .NET Framework. Został zaprojektowany w celu zapewnienia zoptymalizowanego środowiska programistycznego dla aplikacji, które są wdrażane w chmurze lub działają lokalnie. Składa się z modularnych komponentów o minimalnym obciążeniu, dzięki czemu można zachować elastyczność podczas konstruowania rozwiązań. Możesz tworzyć i uruchamiać aplikacje ASP.NET Core na wielu platformach w systemach Windows, Mac i Linux. ASP.NET Core to Open Source w serwisie [GitHub](https://github.com/aspnet/home).

W tym laboratorium utworzysz i eksplorujesz aplikację ASP.NET Core przy użyciu Visual Studio dla komputerów Mac.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Tworzenie aplikacji internetowej ASP.NET Core
> * Poznaj ASP.NET Core hosting, konfigurację i model oprogramowania pośredniczącego
> * Debugowanie ASP.NET Core aplikacji sieci Web

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio dla komputerów Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Docelowi odbiorcy

To laboratorium jest przeznaczone dla deweloperów, którzy znają język C#, chociaż głębokie środowisko nie jest wymagane.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Zadanie 1. Tworzenie nowej aplikacji ASP.NET Core

1. Uruchom **Visual Studio dla komputerów Mac**.

2. Wybierz pozycję **plik > nowe rozwiązanie**.

3. Wybierz kategorię **aplikacji .NET Core >** i szablon **aplikacji sieci Web ASP.NET Core (C#)** . Kliknij przycisk **Dalej**.

    ![Zrzut ekranu przedstawiający sposób wybierania szablonu aplikacji sieci Web dla nowego projektu.](media/netcore-image1.png)

4. Wprowadź nazwę **"CoreLab"** i kliknij przycisk **Utwórz** , aby utworzyć projekt. Ukończenie tej czynności zajmie chwilę.

    ![Zrzut ekranu konfiguracji aplikacji sieci Web, Dodawanie nazwy projektu.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Zadanie 2: Przewodnik po rozwiązaniu

1. Szablon domyślny spowoduje utworzenie rozwiązania z pojedynczym ASP.NET Core projektu o nazwie **CoreLab**. Rozwiń węzeł projektu, aby uwidocznić jego zawartość.

    ![Zrzut ekranu węzła projektu rozwiązania wybranego do wyświetlenia jego zawartości, w tym folderów i plików.](media/netcore-image3.png)

2. Ten projekt jest zgodny z odmianą modelu-View-Controller (MVC), aby zapewnić jasny podział obowiązków między danymi (modelami), prezentacją (widokami) i funkcją (controllers). Otwórz plik **HomeController.cs** z folderu **controllers** .

    ![Zrzut ekranu przedstawiający projekt rozwiązania z klasą języka C# o nazwie HomeController Selected.](media/netcore-image4.png)

3. Klasa **HomeController** — według Konwencji — obsługuje wszystkie żądania przychodzące, które zaczynają się od **/Home**. Metoda **index** obsługuje żądania do katalogu głównego katalogu ( `http://site.com/Home` na przykład), a inne metody obsługują żądania do ich nazwanych ścieżek na podstawie Konwencji, takich jak **About ()** obsługują żądania do `http://site.com/Home/About` . Oczywiście wszystko to można skonfigurować. Jednym z nich jest to, że **HomeController** jest domyślnym kontrolerem w nowym projekcie, dlatego żądania kierowane do katalogu głównego witryny ( `http://site.com` ) przechodzą przez **indeks ()** **HomeController** , podobnie jak żądania do `http://site.com/Home` lub `http://site.com/Home/Index` .

    ![Zrzut ekranu klasy C# o nazwie HomeController.](media/netcore-image5.png)

4. Projekt zawiera również folder **widoki** , który zawiera inne foldery, które są mapowane na każdy kontroler (a także jeden dla widoków **udostępnionych** . Na przykład, widok pliku CSHTML (rozszerzenie HTML) dla ścieżki **/Home/about** będzie w **widokach/Home/about. cshtml**. Otwórz ten plik.

    ![Zrzut ekranu przedstawiający projekt rozwiązania z plikiem C S H T M L o nazwie o wybranym.](media/netcore-image6.png)

5. Ten plik CSHTML używa składnia Razor do renderowania HTML na podstawie kombinacji standardowych tagów i wbudowanego języka C#. Więcej informacji na ten temat można znaleźć w [dokumentacji online](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![Zrzut ekranu przedstawiający część pliku C S H T M z pokazanym składnia Razor.](media/netcore-image7.png)

6. Rozwiązanie zawiera również folder **wwwroot** , który będzie katalogiem głównym witryny sieci Web. Możesz umieścić statyczną zawartość witryny, taką jak CSS, images i biblioteki JavaScript, bezpośrednio w ścieżkach, na które mają znajdować się podczas wdrażania lokacji.

    ![Zrzut ekranu rozwiązania z wybranym folderem głównym w w usłudze.](media/netcore-image8.png)

7. Istnieją również różne pliki konfiguracji, które służą do zarządzania projektem, jego pakietami i aplikacją w środowisku uruchomieniowym. Na przykład domyślna [Konfiguracja](/aspnet/core/fundamentals/configuration) aplikacji jest przechowywana w **appsettings.jsna**. Zagnieżdżony poniżej appsettings.jsw pliku jest **appsettings.Development.jsna** pliku. W tym miejscu można zastąpić niektóre/wszystkie te ustawienia dla poszczególnych środowisk. Visual Studio dla komputerów Mac będzie zagnieżdżać pliki w ten sam sposób przy użyciu tej samej logiki, co program Visual Studio dla systemu Windows, dzięki czemu pliki, do których trzeba uzyskać dostęp częściej, znajdują się w programie Forefront. 

    ![Zrzut ekranu przedstawiający widok szczegółowy z wybranym plikiem JSON.](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Zadanie 3: zrozumienie, w jaki sposób aplikacja jest hostowana

1. W **Eksplorator rozwiązań**Otwórz **program.cs**. Jest to program inicjujący, na którym będzie uruchamiana aplikacja.

    ![Zrzut ekranu rozwiązania z plikiem źródłowym C# o nazwie program wybrany.](media/netcore-image10.png)

2. Chociaż w tym miejscu istnieje tylko dwa wiersze kodu, są one istotne. Podziel się nimi. Najpierw zostanie utworzony nowy **WebHostBuilder** . Aplikacje ASP.NET Core wymagają hosta, który ma zostać uruchomiony. Host musi implementować interfejs **IWebHost** , który uwidacznia kolekcje funkcji i usług oraz metodę **startową** . Host jest zwykle tworzony przy użyciu wystąpienia **WebHostBuilder**, które kompiluje i zwraca wystąpienie **webhost** . Serwer **webhost** odwołuje się do serwera, który będzie obsługiwał żądania.

    ![Zrzut ekranu przedstawiający metodę Main języka C# z instrukcją, która inicjuje zmienną o nazwie host z typem WebHostBuilder.](media/netcore-image11.png)

3. Mimo że **WebHostBuilder** jest odpowiedzialny za utworzenie hosta, który będzie mógł zainicjować serwer dla aplikacji, wymaga podania serwera implementującego **IServer**. Domyślnie jest to **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)**, wieloplatformowy serwer sieci web dla ASP.NET Core oparty na **libuv**, który jest międzyplatformową biblioteką asynchronicznych operacji we/wy.

    ![Zrzut ekranu przedstawiający podstawową metodę języka C# wyróżnienie zmiennej hosta ustawiającej serwer przy użyciu metody UseKestrel.](media/netcore-image12.png)

4. Następnie zostanie ustawiony katalog główny zawartości serwera. Określa miejsce, w którym wyszukuje pliki zawartości, takie jak pliki widoku MVC. Domyślnym katalogiem zawartości jest folder, z którego aplikacja jest uruchamiana.

    ![Zrzut ekranu przedstawiający podstawową metodę języka C# wyróżnienie zmiennej hosta ustawienia katalogu głównego zawartości dla serwera przy użyciu metody UseContentRoot.](media/netcore-image13.png)

5. Jeśli aplikacja musi działać z serwerem sieci Web Internet Information Services (IIS), Metoda **UseIISIntegration** powinna być wywoływana w ramach konstruowania hosta. To nie konfiguruje serwera, na przykład **UseKestrel** . Aby używać usług IIS z ASP.NET Core, należy określić zarówno **UseKestrel** , jak i **UseIISIntegration**. **Kestrel** jest przeznaczony do uruchamiania za serwerem proxy i nie należy go wdrażać bezpośrednio do Internetu. **UseIISIntegration** określa usługi IIS jako serwer zwrotnego serwera proxy, ale jest to istotne tylko w przypadku uruchamiania na maszynach z usługami IIS. Jeśli aplikacja jest wdrażana w systemie Windows, należy ją pozostawić. Nie ma inaczej.

    ![Zrzut ekranu przedstawiający podstawową metodę języka C# wyróżnienie zmiennej hosta ustawiającej odwrotny serwer proxy za pomocą metody UseIISIntegration.](media/netcore-image14.png)

6. Jest to przejrzyste rozwiązanie umożliwiające oddzielenie ładowania ustawień od uruchomienia aplikacji. Aby to ułatwić, **UseStartup** jest wywoływana, aby określić, że Klasa **startowa** ma zostać wywołana w celu załadowania ustawień i innych zadań uruchamiania, takich jak wstawianie oprogramowania pośredniczącego do potoku HTTP. Może istnieć wiele wywołań **UseStartup** z oczekiwaniami, że każdy z nich zastępuje poprzednie ustawienia, zgodnie z wymaganiami.

    ![Zrzut ekranu przedstawiający podstawową metodę języka C# wyróżnienie zmiennej hosta ustawienia klasy uruchamiania z opcją UseStartup.](media/netcore-image15.png)

7. Ostatnim krokiem tworzenia **IWebHost** jest wywołanie metody **Build**.

    ![Zrzut ekranu przedstawiający podstawową metodę języka C# wyróżnienie zmiennej hosta za pomocą metody Build.](media/netcore-image16.png)

8. Gdy klasy **IWebHost** są wymagane do zaimplementowania **uruchamiania**bez blokowania, ASP.NET Core projekty mają metodę rozszerzającą o nazwie **Run** , która zawija **się od kodu** blokującego, więc nie trzeba ręcznie blokować metody od razu.

    ![Zrzut ekranu przedstawiający metodę Main języka C# z wyróżnieniem przebiegu punktu hosta instrukcji.](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Zadanie 4. Uruchamianie i debugowanie aplikacji

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **CoreLab** i wybierz polecenie **Opcje**.

    ![Zrzut ekranu przedstawiający menu kontekstowe dla rozwiązania CoreLab, wyróżnianie opcji.](media/netcore-image18.png)

2. Okno dialogowe **Opcje projektu** zawiera wszystko, czego potrzebujesz, aby dostosować sposób kompilowania i uruchamiania aplikacji. Wybierz węzeł **Uruchom konfiguracje > > default** z panelu po lewej stronie.

3. Zaznacz opcję **Uruchom w konsoli zewnętrznej** i usuń zaznaczenie pola **Wstrzymaj dane wyjściowe konsoli**. Zwykle aplikacja samodzielnie hostowana nie będzie miała widocznej konsoli, ale zamiast tego rejestruje wyniki w konsoli **wyjściowej** . Na potrzeby tego laboratorium zobaczymy go również w osobnym oknie, chociaż nie trzeba tego robić podczas normalnego opracowywania.

4. Kliknij przycisk **OK**.

    ![Zrzut ekranu przedstawiający kartę Konfiguracja ogólna uruchamiania z opcją Uruchom w konsoli zewnętrznej i Wstrzymaj dane wyjściowe konsoli nie zostały wybrane.](media/netcore-image19.png)

5. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację. Alternatywnie możesz wybrać polecenie **uruchom > Rozpocznij debugowanie**.

6. Visual Studio dla komputerów Mac uruchomi dwa okna. Pierwszym z nich jest okno konsoli, które udostępnia widok aplikacji serwera samoobsługowego.

    ![Zrzut ekranu przedstawiający okno konsoli dla aplikacji serwera samoobsługowego.](media/netcore-image20.png)

7. Drugim jest typowym oknem przeglądarki, aby przetestować lokację. W odniesieniu do znanej przeglądarki ta aplikacja może być hostowana w dowolnym miejscu. Kliknij **, aby przejść do tej** strony.

    ![Zrzut ekranu przedstawiający okno przeglądarki umożliwiające przetestowanie lokacji, wyróżnianie opcji informacje.](media/netcore-image21.png)

8. Na stronie informacje są renderowane niektóre elementy tekstowe ustawione w kontrolerze.

    ![Zrzut ekranu przedstawiający wynik wyboru opcji informacje, która jest stroną informacje.](media/netcore-image22.png)

9. Zachowaj otwarte okna i wróć do Visual Studio dla komputerów Mac. Otwórz plik **controllers/HomeController. cs** , jeśli nie jest jeszcze otwarty.

    ![Zrzut ekranu przedstawiający rozwiązanie z klasą C# HomeController ponownie wybrane.](media/netcore-image23.png)

10. Ustaw punkt przerwania w pierwszym wierszu metody **about** . Możesz to zrobić, klikając margines lub ustawiając kursor w wierszu i naciskając klawisz **F9**. Ten wiersz ustawia niektóre dane w kolekcji **Viewdata** , które są renderowane na stronie cshtml w **widokach/Home/about. cshtml**.

    ![Zrzut ekranu przedstawiający metodę about z ustawionym punktem przerwania.](media/netcore-image24.png)

11. Wróć do przeglądarki i Odśwież stronę informacje. Spowoduje to wyzwolenie punktu przerwania w Visual Studio dla komputerów Mac.

12. Wskaźnik myszy nad składową **Viewdata** , aby wyświetlić jego dane. Możesz również rozwinąć jego podrzędne elementy członkowskie, aby zobaczyć zagnieżdżone dane.

    ![Zrzut ekranu przedstawiający punkt przerwania z rozwiniętymi danymi.](media/netcore-image25.png)

13. Usuń punkt przerwania aplikacji, używając tej samej metody, która została użyta do dodania.

14. Otwórz **Widok/Home/about. cshtml**.

15. Zmień tekst **"dodatkowy"** na **"zmieniony** " i Zapisz plik.

    ![Zrzut ekranu przedstawiający plik C S H T M L o nazwie informacje z zmianą tekstu.](media/netcore-image26.png)

16. Naciśnij przycisk **Kontynuuj** , aby kontynuować wykonywanie.

    ![Zrzut ekranu przedstawiający okno programu Visual Studio z wyróżnionym przyciskiem Kontynuuj.](media/netcore-image27.png)

17. Wróć do okna przeglądarki, aby zobaczyć zaktualizowany tekst. Tę zmianę można wykonać w dowolnym momencie i niekoniecznie wymagało punktu przerwania debugera. Odśwież przeglądarkę, jeśli zmiany nie są widoczne bezpośrednio.

    ![Zrzut ekranu przedstawiający stronę informacje, tym razem ze zmienionym tekstem.](media/netcore-image28.png)

18. Zamknij okno przeglądarki testowej i konsolę aplikacji. Spowoduje to zatrzymanie debugowania.

## <a name="task-5-application-startup-configuration"></a>Zadanie 5. Konfiguracja uruchamiania aplikacji

1. W **Eksplorator rozwiązań**Otwórz **Startup.cs**. Możesz zauważyć, że niektóre czerwone zygzaky początkowo jako pakiety NuGet są przywracane w tle, a kompilator Roslyn tworzy pełny obraz zależności projektu.

    ![Zrzut ekranu rozwiązania z plikiem klasy C# o nazwie Startup Selected.](media/netcore-image29.png)

2. Znajdź metodę **uruchamiania** . Ta sekcja definiuje początkową konfigurację aplikacji i jest gęsto spakowana. Podzielmy ją na kroki.

    ![Zrzut ekranu przedstawiający metodę uruchamiania klasy startowej.](media/netcore-image30.png)

3. Metoda zostanie wyłączona przez zainicjowanie **ConfigurationBuilder** i ustawienie jej ścieżki podstawowej.

    ![Zrzut ekranu przedstawiający metodę uruchamiania pokazującą instrukcję inicjującą zmienną o nazwie Builder z typem ConfigurationBuilder.](media/netcore-image31.png)

4. Następnie ładuje wymagane **appsettings.js** pliku.

    ![Zrzut ekranu przedstawiający metodę uruchamiania pokazującą zmienną konstruktora przy użyciu metody AddJsonFile, aby dodać plik JSON o nazwie appSettings.](media/netcore-image32.png)

5. Następnie próbuje załadowaćappsettings.jsspecyficzne dla środowiska ** w** pliku, co spowodowałoby zastąpienie istniejących ustawień. Na przykład jest to podano **appsettings.Development.jsw** pliku używanym dla danego środowiska. Aby dowiedzieć się więcej na temat konfiguracji w ASP.NET Core, zapoznaj [się z](/aspnet/core/fundamentals/configuration)dokumentacją.

    ![Zrzut ekranu przedstawiający metodę uruchamiania pokazującą zmienną konstruktora przy użyciu metody AddJsonFile, aby dodać plik JSON specyficzny dla środowiska.](media/netcore-image34.png)

6. Na koniec zmienne środowiskowe są dodawane do programu Configuration Builder, a konfiguracja jest skompilowana i ustawiana pod kątem użycia.

    ![Zrzut ekranu przedstawiający metodę uruchamiania pokazującą zmienną konstruktora dodając zmienne środowiskowe, a następnie używając metody Build do kompilowania konfiguracji.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Zadanie 6. Wstawianie oprogramowania pośredniczącego aplikacji

1. Znajdź metodę **Configure** w klasie **Startup** . Jest to miejsce, w którym skonfigurowano wszystkie oprogramowanie pośredniczące, aby można je było wstawić do potoku HTTP i użyć do przetwarzania każdego żądania do serwera. Chociaż ta metoda jest wywoływana tylko raz, zawartość metod (takich jak **UseStaticFiles**) może być wykonywana dla każdego żądania.

    ![Zrzut ekranu przedstawiający metodę Configure w klasie uruchomieniowej.](media/netcore-image36.png)

2. Możesz również dodać kolejne oprogramowanie pośredniczące, które ma zostać wykonane w ramach potoku. Dodaj poniższy kod po **aplikacji. UseStaticFiles** do automatycznego dodawania nagłówka **X-test** do każdej odpowiedzi wychodzącej. Technologia IntelliSense pomoże Ci zakończyć kod w trakcie pisania.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

4. Możemy użyć przeglądarki do sprawdzenia nagłówków, aby sprawdzić, czy są one dodawane. Poniższe instrukcje dotyczą programu Safari, ale można to zrobić w przeglądarce [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) lub [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Gdy przeglądarka załaduje lokację, wybierz pozycję **Safari > Preferences (Preferencje**).

6. Na karcie **Zaawansowane** zaznacz opcję **Pokaż menu rozwijane na pasku menu** , a następnie zamknij okno dialogowe.

    ![Zrzut ekranu przedstawiający okienko zaawansowane w oknie dialogowym preferencji przeglądarki Safari z wybranym menu Pokaż Programowanie na pasku menu.](media/netcore-image37.png)

7. Wybierz pozycję **opracowywanie > Pokaż zasoby strony**.

8. Odśwież okno przeglądarki, aby nowo otwarte narzędzia programistyczne mogły śledzić i analizować ruch i zawartość.

9. Stroną HTML localhost renderowaną przez serwer będzie element wybrany domyślnie.

    ![Zrzut ekranu przedstawiający stronę localhost H T M L.](media/netcore-image38.png)

10. Rozwiń **pasek boczny szczegóły**.

    ![Zrzut ekranu z wyróżnioną kontrolką, która ma zostać użyta, aby rozwinąć pasek boczny szczegóły.](media/netcore-image39.png)

11. Przewiń w dół paska bocznego, aby zobaczyć nagłówek odpowiedzi dodany we wcześniejszej części kodu.

    ![Zrzut ekranu wyróżnienie nagłówka odpowiedzi o nazwie XTest wartością testu.](media/netcore-image40.png)

12. Zamknij okno przeglądarki i konsolę po spełnieniu.

## <a name="summary"></a>Podsumowanie

W tym laboratorium dowiesz się, jak rozpocząć tworzenie aplikacji ASP.NET Core przy użyciu Visual Studio dla komputerów Mac. Jeśli chcesz poznać tworzenie bardziej kompletnych aplikacji bazy danych filmów, zobacz samouczek wprowadzenie do [ASP.NET Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc) .
