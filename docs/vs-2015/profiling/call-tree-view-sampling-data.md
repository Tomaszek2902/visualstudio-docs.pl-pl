---
title: Widok drzewa wywołań — dane próbkowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 720f37afbeea3c7440ad2ced9649039d671b1f1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805995"
---
# <a name="call-tree-view---sampling-data"></a>Widok drzewa wywołań — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W widoku drzewa wywołań są wyświetlane ścieżki wykonywania funkcji, które zostały przesunięte w profilowanej aplikacji.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich wywoływanych funkcji i danych wydajności dotyczących tych wywołań funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji z łączną liczbą próbek w przebiegu profilowania.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie gorącej ścieżki wykonywania  
 Widok drzewa wywołań może rozwijać i wyróżniać ścieżki wykonywania procesu lub funkcji, które były najczęściej próbkowane. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę gorącą**.  
  
## <a name="setting-the-call-tree-root-node"></a>Ustawianie węzła głównego drzewa wywołań  
 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku drzewa wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz pozycję **Ustaw katalog główny**.  
  
 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku, z wyjątkiem poddrzewa wybranego węzła. Aby przywrócić węzeł główny z powrotem do oryginalnego węzła, kliknij prawym przyciskiem myszy w oknie widok drzewa wywołań i wybierz polecenie **Zresetuj katalog główny**.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|  
|**Nazwa procesu**|Nazwa procesu|  
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres funkcji.|  
|**Poziomie**|Głębokość tej funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|  
|**Próbki wyłączne**|Liczba próbek zebranych w tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań. Ta liczba nie zawiera próbek zebranych w funkcjach, które zostały wywołane przez funkcję.|  
|**Wyłącznych próbek%**|Procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|  
|**Próbki włączne**|Liczba próbek zebranych w tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań. Ta liczba zawiera próbki, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|  
|**Próbki włączne%**|Wartość procentowa wszystkich próbek w przebiegu profilowania, które były włączonych próbek tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok drzewa wywołań — dane próbkowania profilera](../profiling/call-tree-view-sampling-data.md)   
 [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Widok drzewa wywołań-Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)
