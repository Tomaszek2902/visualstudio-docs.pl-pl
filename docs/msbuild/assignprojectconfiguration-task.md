---
title: AssignProjectConfiguration — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b543af39cbcd0301da7d0d353f8f7b6fa006f7ac
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508525"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration, zadanie

To zadanie akceptuje listę ciągów konfiguracji i przypisuje je do określonych projektów.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `AssignProjectConfiguration` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`ProjectReferences`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wejściowy.<br /><br /> Projekty do skonfigurowania.|
|`SolutionConfigurationContents`|Opcjonalny `string` parametr wyjściowy.<br /><br /> Zawiera ciąg XML zawierający konfigurację projektu dla każdego projektu. Konfiguracje są przypisywane do nazwanych projektów.|
|`DefaultToVcxPlatformMapping`|Opcjonalny `string` parametr wyjściowy.<br /><br /> Zawiera rozdzielaną średnikami listę mapowań z nazw platform używanych przez większość typów do tych, które są używane przez pliki *. vcxproj* .<br /><br /> Na przykład:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> `string` parametr wyjściowy.<br /><br /> Zawiera rozdzielaną średnikami listę mapowań z nazw platform *. vcxproj* na nazwy platform używane przez większość typów.<br /><br /> Na przykład:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Opcjonalny `string` parametr wyjściowy.<br /><br /> Zawiera konfigurację dla bieżącego projektu.|
|`CurrentProjectPlatform`|Opcjonalny `string` parametr wyjściowy.<br /><br /> Zawiera platformę dla bieżącego projektu.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Opcjonalny `bool` parametr wyjściowy.<br /><br /> Zawiera flagę wskazującą, że odwołania powinny zostać skompilowane, nawet jeśli zostały wyłączone w konfiguracji projektu.|
|`ShouldUnsetParentConfigurationAndPlatform`|Opcjonalny `bool` parametr wyjściowy.<br /><br /> Zawiera flagę wskazującą, czy konfiguracja nadrzędna i platforma mają być nieustawiane.|
|`OutputType`|Opcjonalny `string` parametr wyjściowy.<br /><br /> Zawiera typ danych wyjściowych dla projektu.|
|`ResolveConfigurationPlatformUsingMappings`|Opcjonalny `bool` parametr wyjściowy.<br /><br /> Zawiera flagę wskazującą, czy kompilacja powinna używać mapowań domyślnych, aby rozpoznać konfigurację i platformę zakończonych odwołań do projektu.|
|`AssignedProjects`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę rozwiązanych ścieżek referencyjnych.|
|`UnassignedProjects`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę elementów odwołań projektu, których nie można rozpoznać przy użyciu wstępnie rozwiązanej listy danych wyjściowych.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
