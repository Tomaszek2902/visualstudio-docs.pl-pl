---
title: Mierzenie wydajności kodu Python
description: Użyj profilera programu Visual Studio, aby sprawdzić wydajność kodu Python podczas korzystania z interpreterów opartych na CPython.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bf10a1f4474c2916cd63402eac487af7545b0f8f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810669"
---
# <a name="profile-python-code"></a>Kod języka Python

Aplikację języka Python można profilować przy użyciu interpreterów opartych na CPython. (Zobacz [funkcje macierzy — profilowanie](overview-of-python-tools-for-visual-studio.md#matrix-profiling) dostępności tej funkcji dla różnych wersji programu Visual Studio).

## <a name="profiling-for-cpython-based-interpreters"></a>Profilowanie dla interpreterów opartych na CPython

Profilowanie jest uruchamiane za pomocą polecenia **Przeanalizuj**  >  **profilowanie uruchamiania Python** menu, które otwiera okno dialogowe konfiguracji:

![Okno dialogowe konfiguracji profilowania](media/profiling-start.png)

Po wybraniu **przycisku OK**Profiler uruchamia i otwiera raport dotyczący wydajności, za pomocą którego można dowiedzieć się, jak czas jest poświęcony na korzystanie z aplikacji:

![Raport dotyczący wydajności profilowania](media/profiling-results.png)

> [!Note]
> Obecnie program Visual Studio obsługuje tylko ten poziom profilowania pełnej aplikacji, ale na pewno chcemy poznać swoją opinię na temat przyszłych możliwości. Skorzystaj z przycisku **opinii o produkcie** w dolnej części tej strony.

## <a name="profiling-for-ironpython"></a>Profilowanie dla IronPython

Ponieważ IronPython nie jest interpreterem opartym na CPython, funkcja profilowania powyżej nie działa.

Zamiast tego należy użyć programu Visual Studio .NET Profiler, uruchamiając *ipy.exe* bezpośrednio jako aplikację docelową, używając odpowiednich argumentów do uruchomienia skryptu uruchomieniowego. Uwzględnij `-X:Debug` w wierszu polecenia, aby upewnić się, że cały kod w języku Python może być debugowany i profilowany. Ten argument generuje raport dotyczący wydajności, w tym czas spędzony zarówno w środowisku uruchomieniowym IronPython, jak i kodzie. Kod jest identyfikowany przy użyciu nazw zniekształcona.

Alternatywnie, IronPython ma własne wbudowane profilowanie, ale obecnie nie istnieje dobry wizualizator. Zobacz [IronPython Profiler](/archive/blogs/curth/an-ironpython-profiler) (blogi MSDN), aby uzyskać dostęp do dostępnych elementów.