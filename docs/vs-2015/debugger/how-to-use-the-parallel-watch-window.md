---
title: 'Instrukcje: korzystanie z okna czujki równoległej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 734a55cb06ee46afc6fc3518d6dffe349690d3d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697492"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Porady: korzystanie z okna czujki równoległej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W okno wyrażeń kontrolnych równoległym można jednocześnie wyświetlić wartości, które są przechowywane w jednym wyrażeniu na wielu wątkach. Każdy wiersz reprezentuje wątek, który jest uruchomiony w aplikacji, ale wątek może być reprezentowany w wielu wierszach. Dokładniej mówiąc, każdy wiersz reprezentuje wywołanie funkcji, którego sygnatura funkcji dopasowuje funkcję w bieżącej klatce stosu. Elementy, które znajdują się w kolumnach, można sortować, zmienić ich kolejność, usunąć i zgrupować. Wątki można flagować, anulować flagować, zamrażać (wstrzymywać) i rozmrażać (wznawiać). W oknie **czujki równoległej** są wyświetlane następujące kolumny:  
  
- Kolumna flagi, w której można oznaczyć wątek, do którego chcemy zwrócić szczególną uwagę.  
  
- Kolumna Frame, w której Strzałka wskazuje wybraną ramkę.  
  
- Konfigurowalna kolumna, która może wyświetlać maszynę, proces, kafelek, zadanie i wątek.  
  
  > [!TIP]
  > Należy otworzyć okno **zadań równoległych** , aby wyświetlić informacje o zadaniu w oknie **czujki równoległej** .  
  
- **\<Add Watch>** Kolumna, w której można wprowadzać wyrażenia, które mają być obserwowane.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Aby wyświetlić okno wyrażeń kontrolnych równoległy  
  
1. Ustaw punkt przerwania w kodzie.  
  
2. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie**. Poczekaj, aż aplikacja osiągnie punkt przerwania.  
  
3. Na pasku menu wybierz kolejno opcje **Debuguj**, **Windows**i **Parallel Watch**, a następnie okno Czujka. Możesz otworzyć maksymalnie cztery okna.  
  
### <a name="to-add-a-watch-expression"></a>Aby dodać wyrażenie czujki  
  
- Wybierz **\<Add Watch>** , a następnie określ wyrażenie czujki.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Aby oflagować lub Usuń flagę wątku  
  
- Wybierz kolumnę flag dla wiersza lub Otwórz menu skrótów dla wątku, a następnie wybierz **flagę** lub Usuń **flagę**.  
  
### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko Oflagowane wątki  
  
- Wybierz przycisk Pokaż tylko Oflagowane w lewym górnym rogu okna **czujki równoległej** .  
  
### <a name="to-switch-frames"></a>Aby przełączyć ramki  
  
- Kliknij dwukrotnie kolumnę Frame. (Klawiatura: zaznacz wiersz i naciśnij klawisz ENTER).  
  
### <a name="to-sort-a-column"></a>Aby posortować kolumnę  
  
- Wybierz nagłówek kolumny.  
  
### <a name="to-group-threads"></a>Do grup wątków  
  
- Otwórz menu skrótów dla okno wyrażeń kontrolnych równoległych, wybierz pozycję **Grupuj według**, a następnie wybierz odpowiedni element podmenu.  
  
### <a name="to-freeze-or-thaw-threads"></a>Aby zablokować lub odblokować wątki  
  
- Otwórz menu skrótów dla wiersza, a następnie wybierz polecenie **Zablokuj** lub **rozmrażaj**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Aby wyeksportować dane w okno wyrażeń kontrolnych równoległym  
  
- Wybierz przycisk **Otwórz w programie Excel** , a następnie wybierz **Otwórz w programie Excel** lub **Eksportuj do pliku CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Aby odfiltrować według wyrażenia logicznego  
  
- Wprowadź wyrażenie logiczne w polu **Filtruj według wartości logicznej** . Debuger oblicza wyrażenie dla każdego kontekstu wątku. Wyświetlane są tylko wiersze, w których jest `true` wyświetlana wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Instrukcje: korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Przewodnik: debugowanie aplikacji C++ AMP](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
