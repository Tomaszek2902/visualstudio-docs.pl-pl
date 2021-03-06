---
title: Zabezpieczenia debugera | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8b7ac2aed43bcb39b4bb5924ad6f1cf2c438b64
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600083"
---
# <a name="debugger-security"></a>Zabezpieczenia debugera
Możliwość debugowania innego procesu daje użytkownikowi wyjątkowo szerokie uprawnienia, zwłaszcza w przypadku zdalnego debugowania. Złośliwy debuger może spowodować rozległe uszkodzenie na debugowanym komputerze.

 Jednak wielu deweloperów nie zakłada, że zagrożenie bezpieczeństwa może również przepływać w odwrotnym kierunku. Złośliwy kod w procesie debugowanego obiektu może zagrażać bezpieczeństwu maszyny debugowania: istnieje wiele luk w zabezpieczeniach, które muszą być chronione.

## <a name="security-best-practices"></a>Najlepsze praktyki w zakresie zabezpieczeń
 Istnieje niejawna relacja zaufania między debugowanym kodem a debugerem. Jeśli chcesz debugować coś, należy również je uruchomić. Dolna linia polega na tym, że musisz mieć możliwość zaufania do elementów debugowania. Jeśli nie można go zaufać, nie należy go debugować lub należy go debugować z komputera, który można zagrażać, i w środowisku izolowanym.

 Aby zmniejszyć potencjalną podatność na ataki, debugowanie powinno być wyłączone na maszynach produkcyjnych. Z tego samego powodu debugowanie nie powinno być nigdy włączone na czas nieokreślony.

### <a name="managed-debugging-security"></a>Zabezpieczenia debugowania zarządzanego
 Poniżej przedstawiono niektóre ogólne zalecenia dotyczące wszystkich zarządzanych debugowania.

- Należy zachować ostrożność podczas dołączania do procesu niezaufanego użytkownika: po wykonaniu tej czynności należy założyć, że jest ona godna zaufania. Podczas próby dołączenia do procesu niezaufanego użytkownika zostanie wyświetlone potwierdzenie okna dialogowego ostrzeżenia o zabezpieczeniach z pytaniem, czy chcesz dołączyć do procesu. "Zaufani użytkownicy" obejmują użytkownika i zestaw standardowych użytkowników, które są powszechnie zdefiniowane na komputerach, na których zainstalowano .NET Framework, takich jak **ASPNET**, **LocalSystem**, **NetworkService**i **LocalService**. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

- Należy zachować ostrożność podczas pobierania projektu z Internetu i ładowania go do programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jest to bardzo ryzykowne, nawet bez debugowania. Gdy to zrobisz, zakładasz, że projekt i kod, który zawiera, są wiarygodne.

  Aby uzyskać więcej informacji, zobacz [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md).

### <a name="remote-debugging-security"></a>Zabezpieczenia debugowania zdalnego
 Debugowanie lokalne jest ogólnie bezpieczniejsze niż debugowanie zdalne. Debugowanie zdalne zwiększa łączny obszar powierzchni, który może być sondowany.

 Program Visual Studio Monitor zdalnego debugowania (msvsmon.exe) jest używany podczas zdalnego debugowania i istnieje kilka zaleceń dotyczących zabezpieczeń dotyczących jego konfigurowania. Preferowanym sposobem skonfigurowania trybu uwierzytelniania jest uwierzytelnianie systemu Windows, ponieważ tryb uwierzytelniania nie jest bezpieczny.

 ![Okno dialogowe błędu](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 W przypadku korzystania z trybu uwierzytelniania systemu Windows należy pamiętać, że udzielenie niezaufanego uprawnienia użytkownika do nawiązania połączenia z usługą msvsmon jest niebezpieczne, ponieważ użytkownik otrzymuje wszystkie uprawnienia na komputerze hostującym msvsmon.

 Nie Debuguj nieznanego procesu na komputerze zdalnym: istnieją potencjalne luki w zabezpieczeniach, które mogą mieć wpływ na maszynę z uruchomionym debugerem lub które mogą spowodować naruszenie msvsmon. Jeśli konieczne jest debugowanie nieznanego procesu, należy przeprowadzić debugowanie lokalnie i użyć zapory, aby mieć zlokalizowane potencjalne zagrożenia.

 Aby uzyskać informacje na temat konfigurowania msvsmon, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#bkmk_setup).

### <a name="web-services-debugging-security"></a>Zabezpieczenia debugowania usług sieci Web
 Istnieje bezpieczniejsze debugowanie lokalne, ale ponieważ prawdopodobnie nie zostały [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane na serwerze sieci Web, debugowanie lokalne może nie być praktyczne. Ogólnie rzecz biorąc, debugowanie usług sieci Web odbywa się zdalnie, z wyjątkiem sytuacji, w której zalecenia dotyczące zdalnego debugowania zabezpieczeń mają zastosowanie również do debugowania usług sieci Web. Poniżej przedstawiono kilka dodatkowych najlepszych rozwiązań. Aby uzyskać więcej informacji, zobacz [debugowanie usług sieci Web XML](/previous-versions/ms241873(v=vs.100)).

- Nie należy włączać debugowania na serwerze sieci Web, którego zabezpieczenia zostały naruszone.

- Przed debugowaniem upewnij się, że serwer sieci Web jest bezpieczny. Jeśli nie masz pewności, czy jest to bezpieczne, nie Debuguj.

- Należy zachować szczególną ostrożność w przypadku debugowania usługi sieci Web, która jest dostępna w Internecie.

### <a name="external-components"></a>Składniki zewnętrzne
 Należy pamiętać o stanie zaufania zewnętrznych składników, z którymi korzysta Twój program, szczególnie jeśli kod nie został napisany. Należy również zwrócić uwagę na składniki, które [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mogą być używane przez debuger.

### <a name="symbols-and-source-code"></a>Symbole i kod źródłowy
 Dwa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Narzędzia, które wymagają zamyślenia o zabezpieczeniach, są następujące:

- Serwer źródłowy, który udostępnia wersje kodu źródłowego z repozytorium kodu źródłowego. Jest to przydatne, gdy nie masz bieżącej wersji kodu źródłowego programu. [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufane polecenie](../debugger/security-warning-debugger-must-execute-untrusted-command.md).

- Serwer symboli, który służy do dostarczania symboli wymaganych do debugowania awarii podczas wywołania systemowego.

  Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufane polecenie](../debugger/security-warning-debugger-must-execute-untrusted-command.md)