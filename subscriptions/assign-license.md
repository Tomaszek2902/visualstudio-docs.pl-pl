---
title: Przypisywanie licencji do subskrypcji programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 09/21/2020
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do subskrybentów
ms.openlocfilehash: cd64aa058ab5c0518fc27bf1ee64acef3b5b79a2
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022203"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Przypisywanie licencji w portalu administratora subskrypcji programu Visual Studio
Jako administrator subskrypcji programu Visual Studio można używać portalu administracyjnego do przypisywania subskrypcji do poszczególnych użytkowników i grup użytkowników.

W przypadku grup użytkowników można wybrać sposób przypisywania subskrypcji.  
- Subskrypcje można przypisywać pojedynczo.
- Możesz również szybko i łatwo przekazywać listy subskrybentów i ich informacje o subskrypcji za pomocą funkcji [zbiorczego dodawania](assign-license-bulk.md) .
- Jeśli Twoja organizacja korzysta z usługi Microsoft Azure Active Directory (Azure AD), możesz [użyć grup usługi Azure AD do przypisywania subskrypcji](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) do grup użytkowników.  


## <a name="add-a-single-subscriber"></a>Dodaj pojedynczego abonenta
Obejrzyj wideo lub przeczytaj, aby dowiedzieć się, jak przypisać subskrypcję programu Visual Studio do nowego użytkownika, aby mogli uzyskać dostęp do korzyści z subskrypcji.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Zaloguj się do [portalu administracyjnego](https://manage.visualstudio.com).
2. Aby przypisać licencję do pojedynczego subskrybenta programu Visual Studio, w górnej części tabeli wybierz pozycję **Dodaj**, a następnie wybierz opcję **indywidualny subskrybent**.
   > [!div class="mx-imgBorder"]
   > ![Dodaj pojedynczego abonenta](_img/assign-license-add/add-subscriber-individual.png "Wybierz pozycję Dodaj, a następnie wybierz opcję indywidualny subskrybent, aby przypisać pojedynczą subskrypcję.")
3. Wprowadź informacje w polach formularza dla nowego subskrybenta. Jeśli Twoja organizacja używa Azure Active Directory, pole **name** działa jako funkcja wyszukiwania, aby znaleźć osoby w bieżącym katalogu, dzięki czemu można wybrać odpowiedniego użytkownika z wyników wyszukiwania. Po wybraniu tej osoby wiadomość e-mail z logowaniem i wiadomości e-mail z powiadomieniem będą automatycznie wypełniane.
   > [!div class="mx-imgBorder"]
   > ![Szczegóły subskrybenta](_img/assign-license-add/subscriber-details.png "Wprowadź nazwę abonenta i inne szczegóły lub wybierz spośród członków dzierżawy.")

    > [!NOTE]
    > Aby elementy członkowskie dzierżawy Azure Active Directory były widoczne po wprowadzeniu nazwy subskrybenta, administrator musi być członkiem dzierżawy. 


    Jeśli chcesz, aby ten subskrybent miał dostęp do pobierania oprogramowania po zalogowaniu się do [portalu subskrypcji programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), upewnij się, że włączono przełącznik pobierania w sekcji **ustawienia pobierania** . Jeśli zdecydujesz się wyłączyć pobieranie, użytkownik nie będzie miał dostępu do pobierania oprogramowania.  Dostęp do kluczy produktów również zostanie wyłączony.  Subskrybenci nadal będą mieć dostęp do wszystkich innych korzyści uwzględnionych w subskrypcji.
   > [!div class="mx-imgBorder"]
   > ! [Dostęp do plików do pobrania] (Media/access-to-downloads.png "Wybierz" Zezwól ", aby zapewnić subskrybentowi dostęp do pobierania oprogramowania").

    Jeśli chcesz dodać własne informacje referencyjne do subskrypcji, możesz to zrobić w sekcji **Dodaj odwołanie** .
   > [!div class="mx-imgBorder"]
   > ![Dodawanie własnych notatek referencyjnych do każdej subskrypcji](media/add-subscriber-reference-notes.png "Użyj pola odwołanie, aby zarejestrować wszelkie uwagi dotyczące tej subskrypcji.")

    Po zakończeniu wybierania opcji i wprowadzaniu danych dla subskrybenta wybierz pozycję **Dodaj** w dolnej części okna **Dodawanie subskrybenta** .
   > [!div class="mx-imgBorder"]
   > ![Wybierz przycisk Dodaj](media/add-button.png "Wybierz pozycję Dodaj, aby zapisać informacje i przypisać subskrypcję do subskrybenta.")

## <a name="resend-assignment-emails"></a>Wyślij ponownie wiadomości e-mail z przypisaniem
Po dodaniu subskrybenta wiadomość e-mail z przypisaniem zostanie automatycznie wysłana do nowego subskrybenta z dodatkowymi instrukcjami. W dowolnym momencie możesz wysłać wiadomość e-mail z przypisaniem, wybierając subskrybenta, a następnie wybierając przycisk **Wyślij ponownie** w górnym menu.  Aby ponownie wysyłać wiadomości e-mail do wielu użytkowników, przytrzymaj wciśnięty klawisz **Ctrl** podczas wybierania subskrybentów.  Po wybraniu przycisku **Wyślij ponownie** zobaczysz okno dialogowe z prośbą o potwierdzenie, że chcesz ponownie wysłać do tych subskrybentów.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
- Masz dużo użytkowników do dodania?  Dowiedz się, jak przypisać subskrypcje do [wielu subskrybentów](assign-license-bulk.md).
- Potrzebujesz pomocy?  Skontaktuj się z [pomocą techniczną programu Visual Studio Administration i subscriptions](https://visualstudio.microsoft.com/support/support-overview-vs).