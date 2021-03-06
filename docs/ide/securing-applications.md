---
title: Zabezpieczenia
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e02900c96991a402d7ea7b789a47f8f2dea447c3
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2020
ms.locfileid: "91781020"
---
# <a name="secure-applications"></a>Zabezpieczanie aplikacji

Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Uruchom program Visual Studio jak najszybciej, jak to możliwe. Zobacz [uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).

Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.

## <a name="code-for-security"></a>Kod dla zabezpieczeń

Większość błędów kodowania, które powodują powstanie luk w zabezpieczeniach, gdy deweloperzy wprowadzają nieprawidłowe założenia podczas pracy z danymi wejściowymi użytkownika lub nie mają w pełni zrozumienia platformy, dla której są one opracowywane.

- [Zasady bezpiecznego kodowania](/dotnet/standard/security/secure-coding-guidelines) — w tym artykule opisano różne metody kodu platformy .NET, które mogą być przeznaczone do pracy z systemem zabezpieczeń.
- [Najlepsze rozwiązania w zakresie zabezpieczeń dla języka c++](/cpp/top/security-best-practices-for-cpp) zawierają informacje o narzędziach i wskazówkach dotyczących zabezpieczeń dla deweloperów języka c++.

## <a name="build-for-security"></a>Kompiluj pod kątem zabezpieczeń

Bezpieczeństwo jest również ważnym zagadnieniem w procesie kompilacji. Kilka dodatkowych kroków może zwiększyć bezpieczeństwo wdrożonej aplikacji i uniemożliwić nieautoryzowane odwrócenie, fałszowanie lub inne ataki:

- [Dotfuscator](dotfuscator/index.md) jest bezpłatna i pomaga w ochronie zestawów .NET przed odtwarzaniem i nieautoryzowanym użyciem, takim jak debugowanie nieautoryzowane.
- [Podpisywanie silnej nazwy](managing-assembly-and-manifest-signing.md) może służyć do unikatowego identyfikowania składników oprogramowania i zapobiegania fałszowaniu nazw.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia w .NET](/dotnet/standard/security/index)
- [Zabezpieczenia platformy Azure](/azure/security/)
- [Przewodnik po zabezpieczeniach systemu Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Funkcje zabezpieczeń platformy Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017&preserve-view=true)
- [Zabezpieczenia ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1&preserve-view=true)
- [Zabezpieczenia Windows Forms](/dotnet/framework/winforms/windows-forms-security)
