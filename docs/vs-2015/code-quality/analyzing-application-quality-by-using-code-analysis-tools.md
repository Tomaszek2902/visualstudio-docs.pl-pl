---
title: Analizowanie jakości aplikacji za pomocą narzędzi do analizy kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8ec0706530cd61653d44533654cf453d25eb42e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919076"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analiza jakości aplikacji za pomocą narzędzi analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji [Analiza zarządzanego](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) kodu programu Visual Studio Code Analysis dla kodu zarządzanego zawiera informacje dotyczące zestawów zarządzanych, takich jak naruszenia reguł programowania i projektowania, które zostały określone w wytycznych dotyczących projektowania Microsoft .NET Framework. Komunikaty ostrzegawcze identyfikują wszelkie istotne problemy związane z programowaniem i projektowaniem oraz, gdy jest to możliwe, dostarczają informacji na temat sposobu rozwiązania problemu.

 [Analizowanie jakości kodu C/C++ za pomocą analizy kodu](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) Narzędzie do analizy kodu C/C++ zawiera informacje dla deweloperów o możliwych defektach w kodzie źródłowym języka C/C++. Typowe błędy kodowania zgłoszone przez narzędzie obejmują przepełnienia buforów, niezainicjowaną pamięć, odwołania wskaźnika NULL oraz przecieki pamięci i zasobów.

 [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Wybierz i Utwórz *zestawy reguł* , które mają być stosowane do projektu.

 [Błędy aplikacji analizy kodu](../code-quality/code-analysis-application-errors.md) Naprawianie błędów w funkcji analizy kodu.

 [Zwiększanie jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Korzystając z Kontrola wersji serwera Team Foundation (TFVC), można utworzyć zasady ewidencjonowania dla projektów zespołowych, które wymuszają praktyki, które prowadzą do lepszego kodu i wydajniejszego opracowywania grup. Zasady ewidencjonowania są regułami ustawionymi na poziomie projektu zespołowego i wymuszanymi na komputerach deweloperskich, zanim kod będzie mógł zostać zaewidencjonowany.

### <a name="code-analysis-for-drivers"></a>Analiza kodu dla sterowników
 Narzędzia do analizy kodu mogą pomóc w zwiększeniu stabilności i niezawodności sterownika przez systematyczne Analizowanie kodu źródłowego sterownika.

 [Analizowanie jakości sterowników przy użyciu narzędzi do analizy kodu](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Analiza kodu dla sterowników to narzędzie do weryfikacji statycznej w czasie kompilacji, które wykrywa podstawowe błędy kodowania w programach C i C++ oraz zawiera wyspecjalizowany moduł, który jest przeznaczony do wykrywania błędów w (głównie) kodu sterownika trybu jądra. Analizator sterownika statycznego (SDV) to statyczne narzędzie weryfikacyjne, które systematycznie analizuje kod źródłowy sterowników trybu jądra systemu Windows. SDV określa, czy sterownik prawidłowo współdziała z jądrem systemu operacyjnego Windows.

 [Analiza kodu dla ostrzeżeń dotyczących sterowników](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings) Opisuje ostrzeżenia, które są raportowane przez analizę kodu dla sterowników, gdy wykryje możliwy błąd w kodzie sterownika.

## <a name="related-tasks"></a>Powiązane zadania
 [Mierzenie złożoności i łatwość utrzymania w kodzie zarządzanym](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Tutaj Wstaw opis.

 [Testowanie jednostkowe kodu](../test/unit-test-your-code.md) Tutaj Wstaw opis.
