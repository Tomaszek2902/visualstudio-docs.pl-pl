---
title: Analizowanie użycia bazy danych dla projektów .NET Core | Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 0aeb2341d905be8f34d47c477f35861b8575dc69
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352319"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Analizowanie wydajności bazy danych przy użyciu narzędzia bazy danych

Użyj narzędzia Database, aby zarejestrować zapytania bazy danych, które aplikacja wykonuje podczas sesji diagnostycznej. Następnie można analizować informacje o poszczególnych zapytaniach w celu znalezienia miejsc, aby zwiększyć wydajność aplikacji.

> [!NOTE]
> Narzędzie Database wymaga programu Visual Studio 2019 w wersji 16,3 lub nowszej oraz projektu .NET Core w systemie Windows przy użyciu [ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) lub [Entity Framework Core](/ef/core/).

## <a name="setup"></a>Konfigurowanie

1. Wybierz **kombinację klawiszy Alt + F2** , aby otworzyć Profiler wydajności w programie Visual Studio.

1. Zaznacz pole wyboru **baza danych** .

   ![Wybrane narzędzie bazy danych](./media/db-launch.png "Wybrane narzędzie bazy danych")

   > [!NOTE]
   > Jeśli narzędzie nie jest dostępne do wyboru, wyczyść każde inne narzędzie, ponieważ niektóre narzędzia muszą działać samodzielnie. Aby dowiedzieć się więcej o uruchamianiu narzędzi, zobacz [Korzystanie z narzędzi profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Jeśli narzędzie nadal nie jest dostępne, sprawdź, czy projekt spełnia powyższe wymagania. Upewnij się, że projekt jest w trybie wydania, aby przechwycić najbardziej dokładne dane.

1. Wybierz przycisk **Start** , aby uruchomić narzędzie.

1. Po uruchomieniu narzędzia Przejdź do scenariusza, który chcesz profilować w aplikacji. Następnie wybierz pozycję **Zatrzymaj zbieranie** lub Zamknij aplikację, aby zobaczyć swoje dane.

1. Po zatrzymaniu kolekcji zostanie wyświetlona tabela zapytań, które zostały uruchomione podczas sesji profilowania.

   ![Narzędzie bazy danych zostało zatrzymane](./media/db-after.png "Narzędzie bazy danych zostało zatrzymane")

Zapytania są zorganizowane chronologicznie, ale można je sortować według dowolnych kolumn. Aby wyświetlić więcej kolumn, kliknij prawym przyciskiem myszy tytuły kolumn. Wybranie kolumny **czas trwania** porządkuje zapytania od najdłuższego do najmniejszego do najniższego.

Po znalezieniu zapytania, które chcesz zbadać, kliknij prawym przyciskiem myszy zapytanie. Następnie wybierz pozycję **Przejdź do pliku źródłowego** , aby zobaczyć, jaki kod jest odpowiedzialny za to zapytanie.

![Wybierz wybrany plik źródłowy](./media/db-gotosource.png "Wybierz wybrany plik źródłowy")

Jeśli wybierzesz zakres czasu na wykresie, w tabeli zapytania są wyświetlane tylko zapytania, które wystąpiły w tym zakresie czasu. To zachowanie jest szczególnie przydatne, gdy uruchamiasz również [Narzędzie użycie procesora CPU](./cpu-usage.md?view=vs-2019&preserve-view=true).

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie ustawień profilera](../profiling/optimize-profiler-settings.md)