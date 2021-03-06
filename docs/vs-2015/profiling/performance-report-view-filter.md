---
title: Filtr widoku raportu wydajności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8620e5a372d764fef3a75126af52a6212ecc6cd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161973"
---
# <a name="performance-report-view-filter"></a>Filtr widoku raportów wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno filtru profilera raportu profiler znajduje się u góry okna Raport o wydajności. Jeśli nie widzisz go, kliknij przycisk **Pokaż filtr** .  
  
 Każdą klauzulę filtru można zmodyfikować, aby uściślić wyniki. W konstruktorze filtrów są dostępne następujące kolumny:  
  
|Element filtru|Opis|  
|-----------------|-----------------|  
|I/lub|Wybierz **i** czy klauzula i klauzula Next muszą mieć obie wartości prawda, aby dopasować wynik. Wybierz **lub** , jeśli ta klauzula lub Następna klauzula może mieć wartość true, aby dopasować wynik.|  
|Pole|Wybierz pole, które ma być używane w klauzuli Filter z listy pól danych, które są dostępne w bieżącym pliku raportu.|  
|Operator|Wybierz operator, który określa relację między polem a wartością.<br /><br /> = Równa się<br /><br /> <>  nie równa się<br /><br /> < mniejsze niż<br /><br /> > większe niż<br /><br /> <= mniejsze niż lub równe<br /><br /> >= większe niż lub równe|  
|Wartość|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola wyświetlają dostępne wartości dla pola.|  
  
 Można dodać klauzule filtru do momentu, w którym filtr zapewni najlepsze wyniki. Kliknij przycisk **Wykonaj filtr** , aby zastosować filtr do pliku danych.  
  
 W widoku raportu **znaczniki** można generować klauzule filtru, aby ograniczyć dane w widokach raportu do danych zbieranych między dwoma znakami. Wybierz znaczniki, które mają zostać uruchomione i końcowe dane raportu, a następnie kliknij prawym przyciskiem myszy i wybierz opcję **Dodaj filtr dla znaczników** lub **Dodaj filtr dla sygnatur czasowych**. Oba filtry ograniczają dane w bieżącym pliku danych do tego samego zakresu; **Dodaj filtr dla znaczników** można zastosować do innych plików. vsp.  
  
 Aby zapisać filtr, kliknij przycisk **Eksportuj filtr** na pasku narzędzi raport wydajności, a następnie określ lokalizację i nazwę pliku. vspf. Aby załadować wcześniej zapisany filtr, kliknij przycisk **Importuj filtr** i Znajdź zapisany plik filtru. Pliki filtrów mogą również służyć do filtrowania plików danych na komputerach, na których zainstalowano autonomiczną narzędzia profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
