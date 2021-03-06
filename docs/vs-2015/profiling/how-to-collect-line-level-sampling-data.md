---
title: 'Instrukcje: zbieranie danych próbkowania na poziomie wiersza | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65890bf31a1257c3a41bc1fd7ed3f732c50eda14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185952"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Porady: zbieranie danych pobierania próbek na poziomie wiersza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Próbkowanie na poziomie wiersza jest zdolnością profilera do określenia, gdzie w kodzie funkcji intensywnie korzystających z procesora, takiej jak funkcja, która ma duże wykluczające się próbki, procesor musi spędzać większość czasu.  
  
## <a name="overview"></a>Omówienie  
 W przypadku próbkowania na poziomie wiersza Profiler wyszukuje stos wywołań programu w ustalonych odstępach czasu i agreguje te wyniki. Wyniki te pokazują, jakie instrukcje procesor wykonał podczas wykonywania przykładów. Zebrane dane dotyczące próbek wyłącznych są następnie analizowane w celu zidentyfikowania wierszy kodu i wskaźnika instrukcji (IP).  
  
 Próbkowanie na poziomie wiersza działa w przypadku zarządzanych, a także kodu natywnego. Raporty dotyczące wydajności, które wyświetlają te dane, obejmują widok wiersze i widok moduły.  
  
 Informacje o początku/końcu znaku nie są dostępne dla kodu natywnego. W przypadku instrukcji wielowierszowych informacje o rozpoczęciu wiersza nie są dostępne dla kodu natywnego; dostępne są tylko informacje o końcu wiersza.  
  
### <a name="available-data"></a>Dostępne dane  
 Dostępne dane próbkowania na poziomie wiersza zawierają następujące informacje:  
  
- Nazwa funkcji.  
  
- Adres funkcji.  
  
- Początek wiersza — numer wiersza przykładowego kodu.  
  
- Koniec wiersza — końcowy numer wiersza. Jest to zazwyczaj takie samo jak dane "początek wiersza" z wyjątkiem przypadków, gdy instrukcja pojedynczego programu obejmuje wiele wierszy kodu źródłowego.  
  
- Początek znaku — początkowa kolumna próbki agregowanej. Zwykle jest to wartość 0, chyba że pojedynczy wiersz zawiera wiele instrukcji programu.  
  
- Koniec znaku — kolumna końcowa próbki agregowanej.  
  
- IP — adres, na który został pobrany próbka zagregowana (tylko w widoku IP).  
  
  W widoku **moduły** , jeśli funkcja ma statystyki na poziomie wiersza, statystyki są zagnieżdżone w każdej funkcji. Ponadto są prezentowane statystyki na poziomie protokołu IP, które są zagnieżdżone w poszczególnych wierszach.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Wyłącz próbkowanie na poziomie wiersza dla kodu zarządzanego  
 Domyślnie próbkowanie na poziomie wiersza jest włączone. Można wyłączyć zbieranie danych na poziomie wiersza dla kodu zarządzanego, wykonując jedną z następujących czynności:  
  
- Przed przeprowadzeniem profilowania wpisz **VSPerfCLREnv/samplelineoff**. Dotyczy to zarówno aplikacji, jak i usług.  
  
     oraz  
  
- Podczas uruchamiania aplikacji wpisz **VSPerfCmd/LineOff \<other arguments> **.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
