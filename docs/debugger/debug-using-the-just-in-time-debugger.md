---
title: Debugowanie przy użyciu debugera just-in-Time | Microsoft Docs
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40b6a0e43a8d0980615087c946e5dd14deef1b0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350579"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debugowanie przy użyciu debugera just-in-Time w programie Visual Studio

Debugowanie just in time może automatycznie uruchamiać program Visual Studio, gdy aplikacja działa poza błędami lub awariami programu Visual Studio. Dzięki debugowaniu just-in-time można testować aplikacje poza programem Visual Studio, a następnie otwierać program Visual Studio, aby rozpocząć debugowanie w przypadku wystąpienia problemu.

Debugowanie just in Time działa w przypadku aplikacji klasycznych systemu Windows. Nie działa w przypadku aplikacji uniwersalnych systemu Windows lub kodu zarządzanego hostowanego w aplikacji natywnej, takiej jak Wizualizatory.

> [!TIP]
> Jeśli chcesz zatrzymać wyświetlanie okna dialogowego debugera just in Time, ale nie masz zainstalowanego programu Visual Studio, zobacz temat [Wyłączanie debugera just in Time](../debugger/just-in-time-debugging-in-visual-studio.md). Jeśli masz zainstalowany program Visual Studio, może być konieczne [wyłączenie debugowania just in Time z rejestru systemu Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Włączanie lub wyłączanie debugowania just-in-Time w programie Visual Studio

>[!NOTE]
>Aby włączyć lub wyłączyć debugowanie just-in-Time, musisz mieć uruchomiony program Visual Studio jako administrator. Włączenie lub wyłączenie debugowania just in Time ustawia klucz rejestru, a uprawnienia administratora mogą być wymagane do zmiany tego klucza. Aby otworzyć program Visual Studio jako administrator, kliknij prawym przyciskiem myszy aplikację Visual Studio i wybierz polecenie **Uruchom jako administrator**.

Debugowanie just in time można skonfigurować za pomocą okna dialogowego Opcje **narzędzi**programu Visual Studio  >  **Options** (lub **Debug**  >  **Opcje**debugowania).

**Aby włączyć lub wyłączyć debugowanie just in Time:**

1. W menu **Narzędzia** lub **Debuguj** wybierz pozycję **Opcje**  >  **debugowanie**  >  **just-in-Time**.

   ![Włącz lub Wyłącz debugowanie JIT](../debugger/media/dbg-jit-enable-or-disable.png "Włącz lub Wyłącz debugowanie JIT")

1. W polu **Włącz debugowanie just in Time dla tych typów kodu** wybierz typy kodu, które mają być debugowane debugowania just-in-Time: **zarządzane**, **natywne**i/lub **skrypt**.

1. Wybierz przycisk **OK**.

Jeśli włączysz debuger just in Time, ale nie zostanie on otwarty w przypadku awarii lub błędów aplikacji, zobacz [Rozwiązywanie problemów z debugowaniem just in Time](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Wyłącz debugowanie just in Time z rejestru systemu Windows

Debugowanie just in Time nadal może być włączone nawet wtedy, gdy program Visual Studio nie jest już zainstalowany na komputerze. Jeśli program Visual Studio nie jest już zainstalowany, można wyłączyć debugowanie just in Time, edytując rejestr systemu Windows.

**Aby wyłączyć debugowanie just in Time, edytując rejestr:**

1. W menu **Start** systemu Windows uruchom **edytor rejestru** (*regedit.exe*).

2. W oknie **Edytor rejestru** zlokalizuj i Usuń następujące wpisy rejestru:

    - **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Klucz rejestru JIT](../debugger/media/dbg-jit-registry.png "Klucz rejestru JIT")

3. Jeśli na komputerze jest uruchomiony 64-bitowy system operacyjny, Usuń również następujące wpisy rejestru:

    - **HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Pamiętaj, aby nie usuwać ani zmieniać żadnych innych kluczy rejestru.

5. Zamknij okno **Edytor rejestru** .

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Włącz debugowanie just in Time formularza systemu Windows

Domyślnie aplikacje formularzy systemu Windows mają program obsługi wyjątków najwyższego poziomu, który pozwala aplikacji na działanie, jeśli może ją odzyskać. Jeśli aplikacja Windows Forms zgłasza nieobsługiwany wyjątek, zostanie wyświetlone następujące okno dialogowe:

![Nieobsługiwany wyjątek w formularzu systemu Windows](../debugger/media/windowsformsunhandledexception.png "Nieobsługiwany wyjątek w formularzu systemu Windows")

Aby włączyć debugowanie just in Time zamiast standardowej obsługi błędów formularzy systemu Windows, Dodaj następujące ustawienia:

- W `system.windows.forms` sekcji pliku *machine.config* lub * \<app name>.exe.config* Ustaw `jitDebugging` wartość na `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- W aplikacji formularza systemu Windows w języku C++ Ustaw `DebuggableAttribute` również `true` w pliku *config* lub w kodzie. Jeśli kompilujesz z [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) i bez [/og](/cpp/build/reference/og-global-optimizations), kompilator ustawi dla Ciebie ten atrybut. Jeśli jednak chcesz debugować niezoptymalizowaną kompilację wydania, musisz ustawić, `DebuggableAttribute` dodając następujący wiersz w pliku *AssemblyInfo. cpp* aplikacji:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Korzystanie z debugowania just in Time
Ten przykład przeprowadzi Cię przez debugowanie just in Time, gdy aplikacja zgłosi błąd.

- Aby wykonać te kroki, musisz mieć zainstalowany program Visual Studio. Jeśli nie masz programu Visual Studio, możesz pobrać bezpłatny [program Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Upewnij się, że debugowanie just in time jest [włączone](#BKMK_Enabling) w **Tools**  >  **opcjach**narzędzi  >  **debugowanie**  >  **just in Time**.

W tym przykładzie utworzysz aplikację konsolową w języku C# w programie Visual Studio, która zgłasza [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. W programie Visual Studio Utwórz aplikację konsolową w języku C# (**plik**  >  **New**  >  **Project**  >  **Visual C#**  >  **Aplikacja konsolowa**) o nazwie *ThrowsNullException*. Aby uzyskać więcej informacji na temat tworzenia projektów w programie Visual Studio, zobacz [Przewodnik: tworzenie prostej aplikacji](../get-started/csharp/tutorial-wpf.md).

1. Gdy projekt zostanie otwarty w programie Visual Studio, Otwórz plik *program.cs* . Zastąp metodę Main () następującym kodem, który drukuje linię do konsoli programu, a następnie zgłasza NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Aby skompilować rozwiązanie, wybierz opcję **debugowanie** (ustawienie domyślne) lub **wydawanie** , a następnie wybierz opcję **Kompiluj**  >  **Kompiluj rozwiązanie**.

   > [!NOTE]
   > - Wybierz konfigurację **debugowania** , aby uzyskać pełne środowisko debugowania.
   > - W przypadku wybrania opcji konfiguracja [wydania](../debugger/how-to-set-debug-and-release-configurations.md) należy wyłączyć [tylko mój kod](../debugger/just-my-code.md) , aby ta procedura działała. W obszarze **Narzędzia**  >  **Opcje**  >  **debugowania**, usuń zaznaczenie opcji **Włącz tylko mój kod**.

   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).

1. Otwórz aplikację skompilowaną *ThrowsNullException.exe* w folderze projektu C# (*. ..\ThrowsNullException\ThrowsNullException\bin\Debug* lub *. ..\ThrowsNullException\ThrowsNullException\bin\Release*).

   Powinno zostać wyświetlone następujące okno poleceń:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. Zostanie otwarte okno dialogowe **Wybierz debuger just in Time** .

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   W obszarze **dostępne debugery**wybierz pozycję ** \<your preferred Visual Studio version/edition> nowe wystąpienie **, jeśli nie została jeszcze wybrana.

1. Wybierz przycisk **OK**.

   Projekt ThrowsNullException zostanie otwarty w nowym wystąpieniu programu Visual Studio, a wykonywanie zostało zatrzymane w wierszu, który wywołał wyjątek:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Debugowanie można rozpocząć od tego momentu. W przypadku debugowania rzeczywistej aplikacji należy dowiedzieć się, dlaczego kod zgłasza wyjątek.

> [!CAUTION]
> Jeśli aplikacja zawiera niezaufany kod, pojawi się okno dialogowe Ostrzeżenie o zabezpieczeniach, które pozwala zdecydować, czy kontynuować debugowanie. Przed kontynuowaniem debugowania Zdecyduj, czy ufasz kodowi. Czy udało Ci się napisać kod samodzielnie? Jeśli aplikacja jest uruchomiona na komputerze zdalnym, czy nazwa procesu jest rozpoznawana? Jeśli aplikacja działa lokalnie, weź pod uwagę możliwość złośliwego kodu uruchomionego na komputerze. Jeśli zdecydujesz, że kod jest godny zaufania, wybierz **przycisk OK**. W przeciwnym razie wybierz pozycję **Anuluj**.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Rozwiązywanie problemów z debugowaniem just in Time

Jeśli debugowanie just in Time nie rozpocznie się, gdy aplikacja ulega awarii, mimo że jest włączona w programie Visual Studio:

- Raportowanie błędów systemu Windows może przejąć obsługę błędów na komputerze.

  Aby rozwiązać ten problem, użyj Edytora rejestru w celu dodania **wartości DWORD** z **wyłączonymi** **danymi o wartości** **1**do następujących kluczy rejestru:

  - **Raportowanie błędów \Software\Microsoft\Windows\Windows HKEY_LOCAL_MACHINE**

  - (Dla maszyn 64-bitowych): **HKEY_LOCAL_MACHINE \Software\wow6432node\microsoft\windows\windows raportowanie błędów**

  Aby uzyskać więcej informacji, zobacz [. Ustawienia raportowania błędów systemu Windows](/windows/desktop/wer/wer-settings).

- Znany problem z systemem Windows może spowodować niepowodzenie debugera just in Time.

  Poprawka polega na dodaniu **wartości DWORD** z danymi **o** **wartości** **1**do następujących kluczy rejestru:

  - **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Dla maszyn 64-bitowych): **HKEY_LOCAL_MACHINE \Software\wow6432node\microsoft\windows NT\CurrentVersion\AeDebug**

Podczas debugowania just in Time mogą pojawić się następujące komunikaty o błędach:

- **Nie można dołączyć do procesu powodującego awarię. Określony program nie jest programem systemu Windows lub MS-DOS.**

    Debuger podjął próbę dołączenia do procesu działającego w innym użytkowniku.

    Aby obejść ten problem, w programie Visual Studio Otwórz pozycję **Debuguj**  >  **dołączanie do procesu**i Znajdź proces, który chcesz debugować, na liście **dostępne procesy** . Jeśli nie znasz nazwy procesu, Znajdź identyfikator procesu w oknie dialogowym **debuger just in Time programu Visual Studio** . Wybierz proces z listy **dostępne procesy** , a następnie wybierz pozycję **Dołącz**. Wybierz pozycję **nie** , aby odrzucić okno dialogowe debugera just in Time.

- **Nie można uruchomić debugera, ponieważ żaden użytkownik nie jest zalogowany.**

    Nie ma użytkownika zalogowanego w konsoli, dlatego nie istnieje sesja użytkownika do wyświetlania okna dialogowego debugowania just-in-Time.

    Aby rozwiązać ten problem, zaloguj się na komputerze.

- **Klasa nie jest zarejestrowana.**

    Debuger próbował utworzyć klasę COM, która nie jest zarejestrowana, prawdopodobnie z powodu problemu z instalacją.

    Aby rozwiązać ten problem, użyj Instalator programu Visual Studio do ponownego zainstalowania lub naprawy instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Opcje, debugowanie, just-in-Time — okno dialogowe](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
