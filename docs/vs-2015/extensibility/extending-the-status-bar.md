---
title: Rozszerzanie paska stanu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28fc1155279ec624cea576b5a70a25800d4ff837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204412"
---
# <a name="extending-the-status-bar"></a>Rozszerzanie paska stanu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wyświetlić informacje, można użyć paska stanu programu Visual Studio znajdującego się u dołu IDE.  
  
 Rozszerzając pasek stanu, można wyświetlić informacje i interfejs użytkownika w czterech regionach: region opinii, pasek postępu, region animacji oraz region projektanta. Region opinii umożliwia wyświetlenie tekstu i wyróżnienie wyświetlanego tekstu. Pasek postępu pokazuje przyrostowy postęp dla krótko działających operacji, takich jak zapisywanie pliku. W regionie animacji jest wyświetlana ciągła pętla pętli dla długotrwałych operacji lub operacji o nieokreślonej długości, takich jak kompilowanie wielu projektów w rozwiązaniu. Natomiast region projektanta pokazuje numer wiersza i kolumny lokalizacji kursora.  
  
 Pasek stanu można uzyskać przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfejsu (z <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> usługi). Ponadto każdy obiekt zlokalizowany w ramce okna może być zarejestrowany jako obiekt klienta paska stanu przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfejsu. Za każdym razem, gdy okno jest aktywowane, program Visual Studio wysyła zapytanie do obiektu zlokalizowanego w tym oknie dla `IVsStatusbarUser` interfejsu. Jeśli ta wartość zostanie znaleziona, wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodę w zwracanym interfejsie, a obiekt może zaktualizować pasek stanu z poziomu tej metody. Okna dokumentów, na przykład, mogą używać <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metody do aktualizowania informacji w regionie projektanta, gdy staną się aktywne.  
  
 W poniższych procedurach założono, że rozumiesz, jak utworzyć projekt VSIX i dodać niestandardowe polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Modyfikowanie paska stanu  
 Ta procedura pokazuje, jak ustawić i pobrać tekst, wyświetlić tekst statyczny i podświetlić wyświetlany tekst w obszarze opinii na pasku stanu.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Odczytywanie i zapisywanie na pasku stanu  
  
1. Utwórz projekt VSIX o nazwie **TestStatusBarExtension** i Dodaj polecenie menu o nazwie **TestStatusBarCommand**.  
  
2. W TestStatusBarCommand.cs Zastąp kod metody procedury obsługi poleceń (MenuItemCallback) następującym:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3. Skompiluj kod i Rozpocznij debugowanie.  
  
4. Otwórz menu **Narzędzia** w eksperymentalnym wystąpieniu programu Visual Studio. Kliknij przycisk **Wywołaj TestStatusBarCommand** .  
  
     Powinieneś zobaczyć, że tekst na pasku stanu jest teraz odczytywany **na pasku stanu.** i wyświetlone okno komunikatu ma ten sam tekst.  
  
#### <a name="updating-the-progress-bar"></a>Aktualizowanie paska postępu  
  
1. W tej procedurze pokazano, jak zainicjować i zaktualizować pasek postępu.  
  
2. Otwórz plik TestStatusBarCommand.cs i Zastąp metodę MenuItemCallback następującym kodem:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3. Skompiluj kod i Rozpocznij debugowanie.  
  
4. Otwórz menu **Narzędzia** w eksperymentalnym wystąpieniu programu Visual Studio. Kliknij przycisk **Wywołaj TestStatusBarCommand** .  
  
     Powinieneś zobaczyć, że tekst na pasku stanu odczytuje teraz **"Zapisywanie na pasku postępu".** Pasek postępu powinien również zostać zaktualizowany co sekundę przez 20 sekund. Gdy pasek stanu i pasek postępu zostaną wyczyszczone.  
  
#### <a name="displaying-an-animation"></a>Wyświetlanie animacji  
  
1. Na pasku stanu jest wyświetlana animacja pętli, która wskazuje długotrwałą operację (na przykład budowanie wielu projektów w rozwiązaniu). Jeśli animacja nie jest widoczna, upewnij się, że masz poprawne ustawienia **narzędzi/opcji** :  
  
     Przejdź do karty **Narzędzia/Opcje/ogólne** i usuń zaznaczenie pola wyboru **automatycznie Dostosuj środowisko wizualne na podstawie wydajności klienta**. Następnie zaznacz opcję sub, aby **włączyć rozbudowane wizualizacje klientów**. Teraz po skompilowaniu projektu w eksperymentalnym wystąpieniu programu Visual Studio powinna być widoczna animacja.  
  
     W tej procedurze zostanie wyświetlona standardowa animacja programu Visual Studio, która przedstawia Kompilowanie projektu lub rozwiązania.  
  
2. Otwórz plik TestStatusBarCommand.cs i Zastąp metodę MenuItemCallback następującym kodem:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3. Skompiluj kod i Rozpocznij debugowanie.  
  
4. Otwórz menu **Narzędzia** w eksperymentalnym wystąpieniu programu Visual Studio, a następnie kliknij pozycję **Wywołaj TestStatusBarCommand**.  
  
     Gdy zobaczysz okno komunikatu, na pasku stanu powinna pojawić się również animacja, która znajduje się po prawej stronie. Po odrzuceniu okna komunikatu animacja znika.
