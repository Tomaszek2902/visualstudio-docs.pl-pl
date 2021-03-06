---
title: AutoRecover, środowisko, opcje — Okno dialogowe
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f35424089b293b858c609d19f59459693373eb4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250291"
---
# <a name="autorecover-environment-options-dialog-box"></a>Autoodzyskiwanie, środowisko, Opcje — okno dialogowe

Użyj tej strony w oknie dialogowym **Opcje** , aby określić, czy automatycznie tworzyć kopie zapasowe plików, czy nie. Możesz również określić, czy chcesz przywrócić zmodyfikowane pliki, jeśli program Visual Studio nieoczekiwanie się zamknie.

Aby uzyskać dostęp do tego okna dialogowego, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **środowisko**  >  **Autoodzyskiwanie**.

:::image type="content" source="media/autorecover-options.png" alt-text="Zrzut ekranu przedstawiający sekcję Autoodzyskiwanie w oknie dialogowym Opcje":::

**Zapisuj informacje Autoodzyskiwania co [n] min**

::: moniker range="vs-2019"

Użyj tej opcji, aby dostosować częstotliwość automatycznego zapisywania pliku w edytorze. W przypadku wcześniej zapisanych plików program Visual Studio 2019 w wersji 16,2 i nowszej zapisuje kopię pliku w ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [ProjectName]***. Jeśli plik jest nowy i jeszcze go nie zapisano, program Visual Studio automatycznie zapisze go przy użyciu losowo wygenerowanej nazwy pliku.

> [!NOTE]
> Jeśli używasz programu Visual Studio 2019 w wersji 16,1 lub starszej, lokalizacja pliku to *%USERPROFILE%\Documents\Visual Studio [wersja] \backup pliki \\ [ProjectName]*. Aby uzyskać więcej informacji, zobacz stronę [historii informacji o wersji programu Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/) .

::: moniker-end

::: moniker range="vs-2017"

Użyj tej opcji, aby dostosować częstotliwość automatycznego zapisywania pliku w edytorze. W przypadku wcześniej zapisanych plików program Visual Studio 2017 zapisuje kopię pliku w programie *%USERPROFILE%\Documents\Visual Studio [Version] \backup Files \\ [ProjectName]*. Jeśli plik jest nowy i jeszcze go nie zapisano, program Visual Studio automatycznie zapisze go przy użyciu losowo wygenerowanej nazwy pliku.

::: moniker-end

**Zachowaj informacje Autoodzyskiwania dla [n] dni**

Użyj tej opcji, aby określić, jak długo program Visual Studio ma nadal tworzyć pliki do odzyskania.

### <a name="see-also"></a>Zobacz też

- [Opcje — Okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md)
