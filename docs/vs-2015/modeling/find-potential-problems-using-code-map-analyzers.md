---
title: Znajdowanie potencjalnych problemów za pomocą analizatorów mapy kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc5d185640c9623a2213aaf7ad50fa68a088b15c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669618"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uruchamiaj analizatory na mapach kodu, aby ułatwić identyfikację kodu, który może być zbyt skomplikowany lub który może wymagać poprawy. Można na przykład użyć następujących analizatorów:

|**Aby znaleźć kod, który ma**|**Sprawdź te obszary, aby sprawdzić, czy**|
|-------------------------------|--------------------------------------------|
|Pętle lub zależności cykliczne|Można uprościć je i rozważyć, czy można przerwać te cykle.|
|Zbyt wiele zależności|Są one wykonywane zbyt wiele funkcji lub w celu określenia wpływu zmiany tych obszarów. Poprawnie sformułowana Mapa kodu będzie zawierać minimalną liczbę zależności. Aby ułatwić przechowywanie, zmianę, testowanie i ponowne użycie kodu, należy rozważyć, czy można resłużyć do refaktoryzacji tych obszarów tak, aby były bardziej wyraźnie zdefiniowane lub czy można scalić kod, który wykonuje podobne funkcje.|
|Brak zależności|Są one niezbędne lub niezależnie od tego, czy należy usunąć ten kod.|

## <a name="analyze-code-maps"></a>Analizuj mapy kodu

1. Na pasku narzędzi mapy wybierz pozycję **Układ**, analizatory, a następnie kliknij polecenie **analizatorze, które**chcesz uruchomić:

   |**Analizator**|**Aby zidentyfikować węzły, które**|
   |------------------|--------------------------------|
   |**Analizator odwołań cyklicznych**|Mają zależności cykliczne względem siebie. **Uwaga:**  Zależności cykliczne, które znajdują się w grupie **generycznej** , nie są wyświetlane na mapie po rozszerzeniu grupy.|
   |**Znajdź Analizator centrów**|Znajdują się w pierwszych 25% węzłów o wysokim stopniu połączenia<br /><br /> **Aby ukryć wszystkie inne węzły na mapie**<br /><br /> -Otwórz menu skrótów dla mapy, wybierz **Zaawansowane**, **zaznacz**, **Ukryj niezaznaczone**.<br />     Mapa ukrywa niewybrane węzły, a Analizator identyfikuje nowe węzły jako centra.|
   |**Analizator węzłów, do których nie istnieją odwołania**|Nie ma odwołań z innych węzłów. **Przestroga:**  Sprawdź wszystkie te przypadki przed założeniem, że kod nie jest używany. Niektóre zależności, takie jak zależności XAML i zależności w czasie wykonywania, nie mogą być statycznie w kodzie.|

   Po zastosowaniu analizatory mapy kodu będą nadal działać. Jeśli zmienisz mapę, wszelkie zastosowane analizatory automatycznie przetworzyją zaktualizowaną mapę. Aby zatrzymać działanie analizatora, na pasku narzędzi Mapa wybierz **Układ**, **analizatory**. Wyłącz wybrany Analizator.

> [!TIP]
> W przypadku bardzo dużej mapy uruchomienie analizatora może spowodować wyjątek braku pamięci. W takim przypadku należy zmodyfikować mapę, aby zmniejszyć jej zakres lub wygenerować mniejszą, a następnie uruchomić Analizator.

## <a name="see-also"></a>Zobacz też
 [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) [używają map kodu do debugowania](../modeling/use-code-maps-to-debug-your-applications.md) [metod mapowania aplikacji na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
