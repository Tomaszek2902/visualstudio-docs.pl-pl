---
title: Krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f5d58533f6f2207d1b07883ab741eb900cdfbbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851112"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8. Wpisywanie kodu dla obsługi zdarzeń pokazywania przycisków obrazowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku zostanie wykonane działanie przycisku **Pokaż obraz** w następujący sposób:

- Gdy użytkownik wybierze ten przycisk, program otworzy okno dialogowe **Otwórz plik** .

- Jeśli użytkownik otworzy plik obrazu, program wyświetli ten obraz w elemencie PictureBox.

  Środowisko IDE ma zaawansowane narzędzie o nazwie IntelliSense, które ułatwia pisanie kodu. Podczas wprowadzania kodu środowisko IDE otwiera okno z sugerowanymi uzupełnianiem dla wprowadzanych słów częściowych. Próbuje określić, co chcesz zrobić dalej, i automatycznie przechodzi do ostatniego wybranego elementu z listy. Możesz użyć strzałek w górę lub w dół, aby przenieść się na listę, lub wpisać litery, aby zawęzić wybór. Gdy zobaczysz wybór, wybierz klawisz TAB, aby go zaznaczyć. Lub możesz zignorować sugestie, jeśli nie jest to konieczne.

  ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 4](https://msdn.microsoft.com/vbasic/gg315355.aspx) lub [Samouczek 1: Tworzenie przeglądarki obrazów w języku C# — wideo 4](https://msdn.microsoft.com/vcsharp/gg278412.aspx). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Aby napisać kod dla programu obsługi zdarzeń przycisku Pokaż obraz

1. Przejdź do Projektant formularzy systemu Windows i kliknij dwukrotnie przycisk **Pokaż obraz** . IDE natychmiast przechodzi do projektanta kodu i przenosi kursor tak, aby znajdował się wewnątrz `showButton_Click()` metody, która została dodana wcześniej.

2. Wpisz `i` w pustym wierszu między dwa nawiasy klamrowe {}. (W Visual Basic wpisz pusty wiersz między prywatnym sub... i End Sub). Zostanie otwarte okno **IntelliSense** , jak pokazano na poniższej ilustracji.

     ![Technologia IntelliSense z kodem&#35; Visual C](../ide/media/express-ifintellisense.png "Express_IfIntellisense") Technologia IntelliSense z kodem Visual C#

3. W oknie **IntelliSense** należy podświetlić słowo **if**. (Jeśli nie, wprowadź małą literę `f` i.) Zwróć uwagę, jak zostanie wyświetlone małe pole *etykietki narzędzia* obok okna **IntelliSense** z opisem, **fragment kodu dla instrukcji if**. (W Visual Basic, etykietka narzędzia wskazuje również, że jest to fragment, ale nieco inny wyraz). Chcesz użyć tego fragmentu kodu, więc wybierz klawisz TAB, **Aby wstawić go** w kodzie. Następnie ponownie wybierz klawisz **Tab, aby użyć fragmentu** kodu. (W przypadku wybrania opcji w innym miejscu, gdy okno funkcji **IntelliSense** zniknie, nadpisać **i ponownie** wpisz je), a okno **IntelliSense** zostanie otwarte.)

     ![Kod&#35; języka Visual C](../ide/media/express-highlighttrue.png "Express_HighlightTrue") Kod języka Visual C#

4. Następnie użyj funkcji IntelliSense, aby wprowadzić więcej kodu, aby otworzyć okno dialogowe **Otwórz plik** . Jeśli użytkownik wybrał przycisk **OK** , PictureBox załaduje plik wybrany przez użytkownika. Poniższe kroki pokazują, jak wprowadzić kod, a chociaż jest to wiele kroków, wystarczy kilka naciśnięć klawiszy:

    1. Zacznij od zaznaczonego tekstu **true** w fragmencie kodu. Wpisz, `op` Aby go zastąpić. (W Visual Basic zaczynasz od początkowej litery, więc wpisz `Op` ).

    2. Zostanie otwarte okno **IntelliSense** z **openFileDialog1**. Wybierz klawisz TAB, aby go zaznaczyć. (W Visual Basic zaczyna się od początkowej Cap, więc zobaczysz **openFileDialog1**. Upewnij się, że wybrano **openFileDialog1** .)

         Aby dowiedzieć się więcej na temat `OpenFileDialog` , zobacz [OpenFileDialog](https://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).

    3. Wpisz kropkę ( `.` ) (wielu programistów wywołuje to kropkę). Ponieważ wpisano kropkę bezpośrednio po **openFileDialog1**, zostanie otwarte okno **IntelliSense** z właściwościami i metodami składnika **OpenFileDialog** . Są to te same właściwości, które pojawiają się w oknie **Właściwości** w przypadku wybrania go w Projektant formularzy systemu Windows. Możesz również wybrać metody, które poinformują składnik, aby wykonali czynności (na przykład otwierając okno dialogowe).

        > [!NOTE]
        > W oknie **IntelliSense** można wyświetlić właściwości i metody. Aby określić, co jest wyświetlane, przyjrzyj się ikonie po lewej stronie każdego elementu w oknie **IntelliSense** . Zobaczysz obraz bloku obok każdej metody, a obraz klucza (lub kolei) obok każdej właściwości. Obok każdego zdarzenia znajduje się również ikona błyskawicy. Te obrazy są wyświetlane w następujący sposób.

         ![Ikona metody](../ide/media/express-iconmethod.png "Express_IconMethod") Ikona metody

         ![Ikona właściwości](../ide/media/express-iconproperty.png "Express_IconProperty") Ikona właściwości

         ![Ikona zdarzenia](../ide/media/express-iconevent.png "Express_IconEvent") Ikona zdarzenia

    4. Zacznij pisać `ShowDialog` (wielkie litery jest nieważne dla IntelliSense). `ShowDialog()`Metoda wyświetli okno dialogowe **Otwórz plik** . Gdy okno zostanie wyróżnione **ShowDialog**, wybierz klawisz Tab. Możesz również wyróżnić "ShowDialog" i wybrać klawisz F1, aby uzyskać pomoc dotyczącą tego.

         Aby dowiedzieć się więcej na temat `ShowDialog()` metody, zobacz [Metoda ShowDialog](https://msdn.microsoft.com/library/c7ykbedk.aspx).

    5. W przypadku korzystania z metody dla formantu lub składnika (nazywanego *wywołaniem metody*) należy dodać nawiasy. Wprowadź nawias otwierający i zamykający bezpośrednio po "g" w `ShowDialog` : `()` powinien teraz wyglądać podobnie jak "openFileDialog1. ShowDialog ()".

        > [!NOTE]
        > Metody są ważną częścią każdego programu, a w tym samouczku przedstawiono kilka sposobów korzystania z metod. Można wywołać metodę składnika, aby poinformować go o tym, jak nazywamy metodę składnika **OpenFileDialog** `ShowDialog()` . Możesz utworzyć własne metody, aby umożliwić programowi wykonywanie zadań, takich jak ten, który tworzysz teraz, zwanej `showButton_Click()` metodą, która otwiera okno dialogowe i obraz, gdy użytkownik wybierze przycisk.

    6. Dla języka Visual C# Dodaj spację, a następnie Dodaj dwa znaki równości ( `==` ). Na Visual Basic Dodaj spację, a następnie użyj pojedynczego znaku równości ( `=` ). (W języku Visual C# i Visual Basic są używane różne operatory równości).

    7. Dodaj kolejną spację. Gdy tylko to zrobisz, zostanie otwarte inne okno **IntelliSense** . Rozpocznij wpisywanie `DialogResult` i wybierz klawisz Tab, aby go dodać.

        > [!NOTE]
        > Podczas pisania kodu w celu wywołania metody, czasami zwraca wartość. W takim przypadku metoda składnika **OpenFileDialog** `ShowDialog()` zwraca wartość DialogResult. DialogResult to specjalna wartość informująca o tym, co się stało w oknie dialogowym. Składnik **OpenFileDialog** może spowodować, że użytkownik wybierze **przycisk OK** lub **Anuluj**, więc `ShowDialog()` Metoda zwraca wartość DialogResult. OK lub DialogResult. Cancel.

    8. Wpisz kropkę, aby otworzyć okno **IntelliSense** wartości DialogResult. Wprowadź literę `O` i wybierz klawisz Tab, aby wstawić **przycisk OK**.

         Aby dowiedzieć się więcej na temat `DialogResult` , zobacz [DialogResult](https://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).

        > [!NOTE]
        > Należy ukończyć pierwszy wiersz kodu. Dla języka Visual C# powinien być następujący.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  W przypadku Visual Basic należy wykonać następujące czynności.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Teraz Dodaj jeszcze jeden wiersz kodu. Możesz ją wpisać (lub skopiować i wkleić), ale rozważ użycie funkcji IntelliSense, aby ją dodać. Im bardziej znająsz technologię IntelliSense, tym szybciej możesz napisać własny kod. Ostatnia `showButton_Click()` Metoda wygląda następująco. (Wybierz kartę **VB** , aby wyświetlić Visual Basic wersję kodu).

         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 9: przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).
