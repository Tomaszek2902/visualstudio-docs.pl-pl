---
title: -Run (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7468fbd6422248f2f15bf74e70cdf9c5bee849c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593632"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Kompiluje i uruchamia określony projekt lub rozwiązanie.

## <a name="syntax"></a>Składnia

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Pełna ścieżka i nazwa pliku rozwiązania.

- *ProjectName*

  Pełna ścieżka i nazwa pliku projektu.

- `/Out`*OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

Kompiluje i uruchamia określony projekt lub rozwiązanie zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik uruchamia środowisko IDE i pozostawia go jako aktywny po zakończeniu działania projektu lub rozwiązania.

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą `/Out` przełącznika.

## <a name="example"></a>Przykład

W tym przykładzie uruchomiono rozwiązanie `MySolution` przy użyciu aktywnej konfiguracji wdrożenia.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
