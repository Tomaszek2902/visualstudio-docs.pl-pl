---
title: Wyświetlanie i diagnozowanie kontenerów i obrazów platformy Docker
description: Opisuje sposób ulepszania możliwości debugowania i diagnozowania aplikacji opartych na kontenerach w programie Visual Studio przy użyciu okna narzędzi, aby zobaczyć, co się dzieje w kontenerach, które obsługują aplikację.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 626666fc912fcff85fcfcc49425d59018778d1f6
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742788"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Jak wyświetlać i diagnozować kontenery oraz obrazy w programie Visual Studio

Możesz zobaczyć, co się dzieje w kontenerach, które obsługują aplikację przy użyciu okna **kontenery** . Jeśli używasz wiersza polecenia do uruchamiania poleceń platformy Docker w celu wyświetlenia i zdiagnozowania, co się dzieje z kontenerami, to okno zapewnia wygodniejszy sposób monitorowania kontenerów bez opuszczania środowiska IDE programu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

- [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual studio 2019 w wersji 16,4 Preview 2](https://visualstudio.microsoft.com/downloads) lub nowszej lub jeśli używasz wcześniejszej wersji programu Visual Studio 2019, zainstaluj [rozszerzenie okna kontenerów](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Wyświetlanie informacji o kontenerach

Okno **kontenery** jest otwierane automatycznie po uruchomieniu kontenera projektu .NET. Aby w dowolnym momencie wyświetlić kontenery w programie Visual Studio, użyj **klawisza Ctrl** + **Q** , aby aktywować pole wyszukiwania programu Visual Studio, a `Containers` następnie wpisz i wybierz pierwszy element. Możesz również otworzyć okno **kontenery** z menu głównego. Użyj ścieżki menu **Przeglądaj**  >  **inne**  >  **kontenery**systemu Windows.  

![Zrzut ekranu karty środowisko w oknie kontenery](media/view-and-diagnose-containers/container-window.png)

Po lewej stronie zostanie wyświetlona lista kontenerów na komputerze lokalnym. Kontenery skojarzone z rozwiązaniem są wyświetlane w obszarze **kontenery rozwiązań**. Po prawej stronie zobaczysz okienko z kartami dla **środowiska**, **portów**, **dzienników**i **plików**.

> [!TIP]
> Możesz łatwo dostosować lokalizację okna narzędzia **kontenerów** w programie Visual Studio. Zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Domyślnie okno **kontenerów** jest zadokowane przy użyciu okna **czujki** , gdy debuger jest uruchomiony.

## <a name="view-environment-variables"></a>Wyświetl zmienne środowiskowe

Na karcie **środowisko** są wyświetlane zmienne środowiskowe w kontenerze. W przypadku kontenera aplikacji można ustawić te zmienne na wiele sposobów, na przykład w pliku dockerfile, w pliku. ENV lub przy użyciu opcji-e podczas uruchamiania kontenera przy użyciu polecenia Docker.

![Zrzut ekranu karty środowisko w oknie kontenery](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Wszelkie zmiany zmiennych środowiskowych nie są odzwierciedlone w czasie rzeczywistym. Ponadto zmienne środowiskowe na tej karcie są systemowymi zmiennymi środowiskowymi w kontenerze i nie odzwierciedlają zmiennych środowiskowych użytkownika lokalnych dla aplikacji.

## <a name="view-port-mappings"></a>Wyświetl mapowania portów

Na karcie **porty** można sprawdzić mapowania portów obowiązujące dla danego kontenera.

![Zrzut ekranu karty porty w oknie kontenery](media/view-and-diagnose-containers/containers-ports.png)

Dobrze znane porty są połączone, dlatego jeśli na porcie jest dostępna zawartość, możesz kliknąć link, aby otworzyć przeglądarkę.

## <a name="view-logs"></a>Wyświetlanie dzienników

Na karcie **dzienniki** są wyświetlane wyniki `docker logs` polecenia. Domyślnie karta pokazuje strumienie stdout i stderr w kontenerze, ale można skonfigurować dane wyjściowe. Aby uzyskać szczegółowe informacje, zobacz [Rejestrowanie platformy Docker](https://docs.docker.com/config/containers/logging/).  Domyślnie karta **dzienniki** przesyła strumieniowo dzienniki, ale można je wyłączyć, wybierając przycisk **Zatrzymaj** na karcie.

![Zrzut ekranu karty Dzienniki w oknie kontenery](media/view-and-diagnose-containers/containers-logs.png)

Aby wyczyścić dzienniki, użyj przycisku **Wyczyść** na karcie **dzienniki** .  Aby pobrać wszystkie dzienniki, użyj przycisku **Odśwież** .

> [!NOTE]
> Program Visual Studio automatycznie przekierowuje stdout i stderr do okna **danych wyjściowych** w przypadku uruchamiania bez debugowania z kontenerami systemu Windows, więc kontenery systemu Windows uruchomione z programu Visual Studio przy użyciu **klawisza Ctrl** + **F5** nie będą wyświetlały dzienników na tej karcie; zamiast tego użyj okna **danych wyjściowych** .

## <a name="view-the-filesystem"></a>Wyświetlanie systemu plików

Na karcie **pliki** można wyświetlić system plików kontenera, w tym folder aplikacji zawierający projekt.

![Zrzut ekranu karty pliki w oknie kontenerów](media/view-and-diagnose-containers/container-filesystem.png)

Aby otworzyć pliki w programie Visual Studio, przejdź do pliku, kliknij go dwukrotnie lub kliknij prawym przyciskiem myszy i wybierz polecenie **Otwórz**. Program Visual Studio otwiera pliki w trybie tylko do odczytu.

![Zrzut ekranu przedstawiający plik otwarty do wyświetlania w programie Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Za pomocą karty **pliki** można wyświetlać dzienniki aplikacji, takie jak dzienniki usług IIS, pliki konfiguracji i inne pliki zawartości w systemie plików kontenera.

## <a name="start-stop-and-remove-containers"></a>Uruchamianie, zatrzymywanie i usuwanie kontenerów

Domyślnie w oknie **kontenerów** są wyświetlane wszystkie kontenery na komputerze zarządzanym przez platformę Docker. Za pomocą przycisków paska narzędzi można uruchamiać, zatrzymywać i usuwać (usuwać) kontenerów, które nie są już potrzebne.  Ta lista jest aktualizowana dynamicznie w miarę tworzenia lub usuwania kontenerów.

## <a name="open-a-terminal-window-in-a-running-container"></a>Otwórz okno terminalu w działającym kontenerze

Możesz otworzyć okno terminalu (wiersz polecenia lub powłokę interaktywną) w kontenerze za pomocą przycisku **Otwórz okno terminalu** w oknie **kontenera** .

![Zrzut ekranu przedstawiający okno otwieranie terminalu w oknie kontenery](media/view-and-diagnose-containers/containers-open-terminal-window.png)

W przypadku kontenerów systemu Windows zostanie otwarty wiersz polecenia systemu Windows. W przypadku kontenerów systemu Linux otwiera okno przy użyciu powłoki bash.

![Zrzut ekranu okna bash](media/view-and-diagnose-containers/container-bash-window.png)

Zwykle okno terminalu jest otwierane poza programem Visual Studio jako osobne okno. Jeśli chcesz, aby środowisko wiersza polecenia było zintegrowane z Visual Studio IDE jako okno narzędzi było dokować, możesz zainstalować [Terminal/Swagger/docs/v1./Swagger/docs/v1.](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Dołącz debuger do procesu

Można dołączyć debuger do procesu, który jest uruchomiony w kontenerze za pomocą przycisku **Dołącz do procesu** na pasku narzędzi okna kontenery. Po wybraniu tego przycisku zostanie wyświetlone okno dialogowe **Dołącz do procesu** zawierające dostępne procesy, które są uruchomione w kontenerze.  

![Zrzut ekranu przedstawiający okno dialogowe Dołączanie do procesu](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Można dołączyć do zarządzanych procesów w kontenerze. Aby wyszukać proces w innym kontenerze, użyj przycisku **Znajdź** i wybierz inny kontener w oknie dialogowym **Wybieranie kontenera platformy Docker** .

## <a name="viewing-images"></a>Wyświetlanie obrazów

Możesz również wyświetlać obrazy na komputerze lokalnym za pomocą karty **obrazy** w oknie **kontenery** . Obrazy pobierane z zewnętrznych repozytoriów są pogrupowane w widoku TreeView. Wybierz obraz, aby sprawdzić szczegóły dotyczące obrazu.

Aby usunąć obraz, kliknij prawym przyciskiem myszy obraz w widoku drzewa, a następnie wybierz polecenie **Usuń**lub wybierz obraz, a następnie użyj przycisku **Usuń** na pasku narzędzi.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o narzędziach kontenera dostępnych w programie Visual Studio, odczytując informacje o narzędziach [kontenerów](overview.md).

## <a name="see-also"></a>Zobacz także

[Programowanie kontenerów w programie Visual Studio](./index.yml)

[Witryna Marketplace dla rozszerzeń dla programu Visual Studio](https://marketplace.visualstudio.com/)