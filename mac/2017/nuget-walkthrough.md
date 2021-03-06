---
title: Dołączanie pakietu NuGet do projektu
description: W tym dokumencie opisano sposób dołączania pakietu NuGet do projektu platformy Xamarin. Przeprowadza on wyszukiwanie i pobieranie pakietu, a także przedstawia funkcje integracji IDE.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 58d749a1d014288754dcd9eb7e620730933d742a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950406"
---
# <a name="include-a-nuget-package-in-your-project"></a>Dołącz pakiet NuGet do projektu

Pakiet NuGet jest najpopularniejszym menedżerem pakietów do programowania na platformie .NET i jest wbudowany w Visual Studio dla komputerów Mac i Visual Studio w systemie Windows. Można wyszukiwać i dodawać pakiety do projektów Xamarin. iOS i Xamarin. Android przy użyciu dowolnego środowiska IDE.

W tym artykule opisano sposób dołączania pakietu NuGet do projektu i zademonstrowania łańcucha narzędzi, który sprawia, że proces jest płynny.

## <a name="nuget-in-visual-studio-for-mac"></a>Pakiet NuGet w Visual Studio dla komputerów Mac

Aby zademonstrować funkcje pakietu NuGet, najpierw zawarto instrukcje tworzenia nowej aplikacji i dodawania do niej pakietu. Następnie będziemy omawiać funkcje środowiska IDE, które ułatwiają zarządzanie pakietami.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Najpierw utwórz projekt o nazwie `HelloNuget` jak pokazano poniżej. Ten przykład pokazuje szablon aplikacji z pojedynczym widokiem systemu iOS, ale każdy obsługiwany typ projektu będzie działał:

![Utwórz nowy projekt dla systemu iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Dodawanie pakietu

Po otwarciu projektu w Visual Studio dla komputerów Mac kliknij prawym przyciskiem myszy folder **pakiety** w **okienko rozwiązania** i wybierz polecenie **Dodaj pakiety**:

![Dodaj nową akcję kontekstu pakietu NuGet](media/nuget-walkthrough-PackagesMenu.png)

Spowoduje to uruchomienie okna **Dodaj pakiety** . Upewnij się, że lista rozwijana źródła ma ustawioną wartość `nuget.org` :

![Lista rozwijana listy źródłowej](media/nuget-walkthrough-Source.png)

Gdy okno zostanie otwarte, ładuje listę pakietów z domyślnego źródła pakietów: nuget.org. Początkowe wyniki wyglądają następująco:

![Wyświetl listę pakietów NuGet](media/nuget-walkthrough-AddPackages1.png)

Użyj pola wyszukiwania w prawym górnym rogu, aby znaleźć konkretny pakiet, na przykład `azure` . Po znalezieniu pakietu, którego chcesz użyć, zaznacz go, a następnie kliknij przycisk **Dodaj pakiet** , aby rozpocząć instalację.

[Dodaj pakiet NuGet platformy Azure](media/nuget-walkthrough-AddPackages2.png)

Po pobraniu pakietu zostanie on dodany do projektu. Rozwiązanie zmieni się w następujący sposób:

* Węzeł **References** będzie zawierać listę wszystkich zestawów, które są częścią pakietu NuGet.
* Węzeł **pakiety** wyświetla każdy pobrany pakiet NuGet. Możesz zaktualizować lub usunąć pakiet z tej listy.
* Plik **packages.config** zostanie dodany do projektu. Ten plik XML jest używany przez IDE do śledzenia wersji pakietów, do których odwołuje się ten projekt. Ten plik nie powinien być edytowany ręcznie, ale powinien pozostać w kontroli wersji. Należy zauważyć, że project.jspliku można użyć zamiast pliku packages.config. project.jsw pliku to nowy format pliku pakietu wprowadzony z pakietem NuGet 3, który obsługuje przywracanie przechodnie. Więcej szczegółowych informacji na temat project.jsmożna znaleźć w dokumentacji programu [NuGet](/NuGet/Schema/Project-Json). project.jsw pliku należy dodać ręcznie, a projekt został zamknięty i ponownie otwarty przed użyciem project.jsna pliku w Visual Studio dla komputerów Mac.

## <a name="using-nuget-packages"></a>Korzystanie z pakietów NuGet

Po dodaniu pakietu NuGet wraz z aktualizacją projektu można programować względem interfejsów API, tak jak w przypadku dowolnego odwołania do projektu.

Upewnij się, że wszystkie wymagane `using` dyrektywy zostały dodane na początku pliku:

```csharp
using Newtonsoft.Json;
```

Większość NuGet udostępnia dodatkowe informacje, takie jak plik Readme lub link strony projektu do źródła NuGet. Zwykle można znaleźć link do tego elementu w blurb pakietu na stronie Dodawanie pakietów:

[Wyświetl link strony projektu](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Aktualizacje pakietu

Aktualizacje pakietu można wykonać w dowolnym momencie, klikając prawym przyciskiem myszy węzeł **pakiety** lub pojedynczo dla każdego składnika.

Kliknij prawym przyciskiem myszy pozycję **pakiety** , aby uzyskać dostęp do menu kontekstowego:

![Menu pakiety](media/nuget-walkthrough-PackagesMenu.png)

* **Dodaj pakiety** — otwiera okno, aby dodać więcej pakietów do projektu.
* **Update** — sprawdza serwer źródłowy dla każdego pakietu i pobiera nowsze wersje.
* **Restore** — pobiera wszystkie brakujące pakiety (bez aktualizowania istniejących pakietów do nowszych wersji).

Opcje aktualizacji i przywracania są również dostępne na poziomie rozwiązania i wpływają na wszystkie projekty w rozwiązaniu.

Możesz również kliknąć prawym przyciskiem myszy poszczególne pakiety, aby uzyskać dostęp do menu kontekstowego:

![Menu pakiety](media/nuget-walkthrough-PackageMenu.png)

* **Numer wersji** — numer wersji to wyłączony element menu, który jest dostarczany tylko do celów informacyjnych.
* **Update** — sprawdza serwer źródłowy i pobiera nowszą wersję (jeśli istnieje).
* **Usuń** — usuwa pakiet z tego projektu i usuwa odpowiednie zestawy z odwołań projektu.

## <a name="adding-package-sources"></a>Dodawanie źródeł pakietów

Pakiety dostępne do instalacji są początkowo pobierane z nuget.org. Można jednak dodać inne lokalizacje pakietu do Visual Studio dla komputerów Mac. Może to być przydatne do testowania własnych pakietów NuGet w środowisku deweloperskim lub do korzystania z prywatnego serwera NuGet w firmie lub organizacji.

W Visual Studio dla komputerów Mac przejdź do **okna preferencje > programu Visual Studio, > źródła > NuGet** , aby wyświetlić i edytować listę źródeł pakietów. Należy pamiętać, że źródła mogą być serwerem zdalnym (określonym za pomocą adresu URL) lub katalogiem lokalnym.

![Źródła pakietów](media/nuget-walkthrough-PackageSource.png)

Kliknij przycisk **Dodaj** , aby skonfigurować nowe źródło. Wprowadź przyjazną nazwę i adres URL (lub ścieżkę pliku) do źródła pakietu. Jeśli źródłem jest bezpieczny serwer sieci Web, wprowadź nazwę użytkownika i hasło. w przeciwnym razie pozostaw te wpisy puste:

![Dodawanie źródeł pakietów](media/nuget-walkthrough-PackageSource2.png)

Podczas wyszukiwania pakietów można wybrać różne źródła:

![Dodawanie źródeł pakietów](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Kontrola wersji

Dokumentacja programu NuGet omawia [Korzystanie z programu NuGet bez zatwierdzania pakietów do kontroli źródła](/nuget/consume-packages/packages-and-source-control). Jeśli wolisz, aby nie przechowywać plików binarnych i nieużywanych informacji w kontroli źródła, możesz skonfigurować Visual Studio dla komputerów Mac, aby automatycznie przywracać pakiety z serwera. Oznacza to, że gdy deweloper pobiera projekt z kontroli źródła po raz pierwszy, program Visual Studio dla komputerów Mac automatycznie pobierze i zainstaluje wymagane pakiety.

![Automatycznie Przywróć pakiety](media/nuget-walkthrough-AutoRestore.png)

Zapoznaj się z określoną dokumentacją kontroli źródła, aby uzyskać szczegółowe informacje na temat wykluczania `packages` śledzenia katalogu.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Zobacz też

* [Instalowanie i używanie pakietu w programie Visual Studio (w systemie Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
