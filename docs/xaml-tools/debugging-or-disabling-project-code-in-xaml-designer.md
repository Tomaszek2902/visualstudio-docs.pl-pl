---
title: Debugowanie lub wyłączanie kodu projektu w projektancie XAML
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: fba240c29cb8142a9ec4b4d28c71112c1974a5b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331057"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>Debugowanie lub wyłączanie kodu projektu w projektancie XAML

W wielu przypadkach Nieobsłużone wyjątki w projektant XAML mogą być spowodowane przez kod projektu próbujący uzyskać dostęp do właściwości lub metod, które zwracają różne wartości lub pracują w inny sposób, gdy aplikacja działa w projektancie. Te wyjątki można rozwiązać przez Debugowanie kodu projektu w innym wystąpieniu programu Visual Studio lub tymczasowe zapobieganie wyjątkom przez wyłączenie kodu projektu w projektancie.

Kod projektu obejmuje:

- Formanty niestandardowe i kontrolki użytkownika

- Biblioteki klas

- Konwertery wartości

- Powiązania z danymi czasu projektowania generowanymi na podstawie kodu projektu

Gdy kod projektu jest wyłączony, Visual Studio Wyświetla symbole zastępcze. Na przykład program Visual Studio Wyświetla nazwę właściwości dla powiązania, gdzie dane nie są już dostępne, lub symbol zastępczy kontrolki, która nie jest już uruchomiona.

![Okno dialogowe nieobsłużonego wyjątku](media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Aby określić, czy kod projektu jest przyczyną wyjątku

1. W oknie dialogowym nieobsługiwany wyjątek wybierz **pozycję kliknij tutaj, aby ponownie załadować link projektanta** .

2. Na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie** , aby skompilować i uruchomić aplikację.

     Jeśli aplikacja zostanie pomyślnie skompilowana i uruchomiona, wyjątek czasu projektowania może być spowodowany przez kod projektu uruchomiony w projektancie.

## <a name="to-debug-project-code-running-in-the-designer"></a>Aby debugować kod projektu uruchomiony w projektancie

1. W oknie dialogowym nieobsługiwany wyjątek wybierz **pozycję kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i ponownie załaduj projektanta** .

2. W Menedżerze zadań systemu Windows wybierz przycisk **Zakończ zadanie** , aby zamknąć wszystkie wystąpienia Projektant XAML programu Visual Studio, które są obecnie uruchomione.

     ![Wystąpienia projektanta XAML w taskmanager](media/xaml_taskmanager.png)

3. W programie Visual Studio Otwórz stronę XAML, która zawiera kod lub kontrolkę, którą chcesz debugować.

4. Otwórz nowe wystąpienie programu Visual Studio, a następnie otwórz drugie wystąpienie projektu.

5. Ustaw punkt przerwania w kodzie projektu.

6. W nowym wystąpieniu programu Visual Studio na pasku menu wybierz polecenie **Debuguj**  >  **Dołącz do procesu**.

7. W oknie dialogowym **Dołącz do procesu** na liście **dostępne procesy** wybierz pozycję **XDesProc.exe**, a następnie wybierz przycisk **Dołącz** .

     ![Proces projektanta XAML](media/xaml_attach.png)

     Jest to proces projektanta XAML w pierwszym wystąpieniu programu Visual Studio.

8. W pierwszym wystąpieniu programu Visual Studio na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie**.

     Teraz możesz przejść do kodu działającego w projektancie.

## <a name="to-disable-project-code-in-the-designer"></a>Aby wyłączyć kod projektu w projektancie

- W oknie dialogowym nieobsługiwany wyjątek wybierz **pozycję kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i ponownie załaduj projektanta** .

- Alternatywnie na pasku narzędzi w **projektancie XAML**wybierz przycisk **Wyłącz kod projektu** .

     ![Przycisk Wyłącz kod projektu](media/xaml_disablecode.png)

     Można ponownie przełączyć przycisk, aby ponownie włączyć kod projektu.

    > [!NOTE]
    > W przypadku projektów przeznaczonych dla procesorów ARM lub x64 program Visual Studio nie może uruchomić kodu projektu w projektancie, dlatego przycisk **Wyłącz kod projektu** jest wyłączony w projektancie.

- Każda opcja powoduje ponowne załadowanie projektanta, a następnie wyłączenie całego kodu dla skojarzonego projektu.

    > [!NOTE]
    > Wyłączenie kodu projektu może prowadzić do utraty danych czasu projektowania. Alternatywą jest debugowanie kodu działającego w projektancie.

## <a name="control-display-options"></a>Opcje wyświetlania kontrolki

> [!NOTE]
> **Opcje wyświetlania kontrolki** są dostępne tylko dla aplikacji platforma uniwersalna systemu Windows, które są przeznaczone do aktualizacji Windows 10 dla twórców (kompilacja 16299) lub nowszych. Funkcja **opcji wyświetlania kontrolki** jest dostępna w programie Visual Studio 2017 w wersji 15,9 lub nowszej.

W projektancie XAML można zmienić opcje wyświetlania kontrolki tak, aby wyświetlały tylko kontrolki platformy z Windows SDK. Może to poprawić niezawodność projektanta XAML.

Aby zmienić opcje wyświetlania kontroli, kliknij ikonę w lewym dolnym rogu okna projektanta, a następnie wybierz opcję w obszarze **Opcje wyświetlania kontrolki**:

![Opcje wyświetlania kontrolki](media/control_display_options.png)

W przypadku wybrania opcji **tylko wyświetlanie kontrolek platformy**wszystkie kontrolki niestandardowe pochodzące z zestawów SDK, kontrolki użytkownika klienta i inne nie zostaną całkowicie wyrenderowane. Zamiast tego są one zastępowane przez kontrolki rezerwowe w celu pokazania rozmiaru i położenia formantu.

## <a name="see-also"></a>Zobacz też

- [Projektuj kod XAML w programie Visual Studio i Blend for Visual Studio](designing-xaml-in-visual-studio.md)
