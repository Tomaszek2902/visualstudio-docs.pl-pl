---
title: Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24152bf2e6acfcb1ed20b75a5c817e0336cdd4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851594"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Zapisywanie kodu dla dodatkowych przycisków i pola wyboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Teraz wszystko jest gotowe do wykonania innych czterech metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz poznać większość z tego samouczka, wpisz kod i użyj funkcji IntelliSense.

 Ten kod dodaje funkcję do przycisków, które zostały dodane wcześniej. Bez tego kodu przyciski nie wykonują żadnych czynności. Przyciski używają kodu w swoich `Click` zdarzeniach (a pole wyboru używa `CheckChanged` zdarzenia) do wykonywania różnych czynności podczas aktywowania kontrolek. Na przykład `clearButton_Click` zdarzenie, które aktywuje się po wybraniu przycisku **Wyczyść obraz** , powoduje wymazanie bieżącego obrazu przez ustawienie jego `Image` właściwości na `null` (lub `nothing` ). Każde zdarzenie w kodzie zawiera komentarze objaśniające, jak działa kod.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) lub [Samouczek 1: Tworzenie przeglądarki obrazów w języku C# — wideo 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

> [!NOTE]
> Najlepszym rozwiązaniem jest zawsze Dodawanie komentarzy do kodu. Komentarze są informacjami dla osoby, które mają być odczytane, i warto pamiętać o tym, aby kod był zrozumiały. Wszystkie elementy w wierszu komentarza są ignorowane przez program. W języku Visual C# można skomentować wiersz, wpisując dwa ukośniki do przodu (//), a w Visual Basic komentarz wiersza, zaczynając od pojedynczego cudzysłowu (').

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Aby napisać kod dla dodatkowych przycisków i pola wyboru

- Dodaj następujący kod do pliku kodu Form1 (Form1.cs lub Form1. vb). Wybierz kartę **VB** , aby wyświetlić kod Visual Basic.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 11. Uruchamianie programu i wypróbuj inne funkcje](../ide/step-11-run-your-program-and-try-other-features.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).
