---
title: -Deploy (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8eeb1a03e584b0b39030ec56ca6945a2d5ced78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570131"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Wdraża rozwiązanie po kompilacji lub odbudowywaniu. Dotyczy tylko projektów kodu zarządzanego.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.

- *SolnConfigName*

  Opcjonalny. Nazwa konfiguracji rozwiązania ( `Debug` na przykład lub `Release` ), która ma zostać użyta do skompilowania rozwiązania o nazwie w *SolutionName*. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32` ). Jeśli ten argument jest nieokreślony lub jest ciągiem pustym ( `""` ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Możesz również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*ProjConfigName*

  Opcjonalny. Nazwy konfiguracji kompilacji projektu (takie jak `Debug` lub `Release` ), które mają być używane podczas kompilowania `/Project` nazwanego. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32` ). Jeśli ten przełącznik jest określony, zastępuje argument *SolnConfigName* .

- `/Out`*OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

Określony projekt musi być projektem wdrożenia. Jeśli określony projekt nie jest projektem wdrożenia, podczas przekazywania projektu, który został skompilowany do wdrożenia, kończy się niepowodzeniem z powodu błędu.

Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika [/out](out-devenv-exe.md) .

## <a name="example"></a>Przykład

Ten przykład wdraża projekt `CSharpWinApp` przy użyciu `Release` konfiguracji kompilacji projektu w programie `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
