---
title: CreateCSharpManifestResourceName — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8e72ef282911ecb36fb9a16838f6cc311e253e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634360"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName — zadanie

Tworzy nazwę manifestu w stylu C# na podstawie danej nazwy pliku *resx* lub innego zasobu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry [zadania CreateCSharpManifestResourceName —](../msbuild/createcsharpmanifestresourcename-task.md).

| Parametr | Opis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`wyjściowy parametr tylko do odczytu.<br /><br /> Nazwy manifestów. |
| `ResourceFiles` | Wymagany parametr interfejsu `String`.<br /><br /> Nazwa pliku zasobów, z którego ma zostać utworzona Nazwa manifestu języka C#. |
| `RootNamespace` | Opcjonalny `String` parametr.<br /><br /> Główna przestrzeń nazw pliku zasobów, zazwyczaj pobierana z pliku projektu. Może być `null` . |
| `PrependCultureAsDirectory` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli nazwa `true` kultury zostanie dodana jako nazwa katalogu tuż przed nazwą zasobu manifestu. Wartość domyślna to `true` . |
| `ResourceFilesWithManifestResourceNames` | Opcjonalny parametr wyjściowy tylko do odczytu `String` .<br /><br /> Zwraca nazwę pliku zasobu, który zawiera teraz nazwę zasobu manifestu. |

## <a name="remarks"></a>Uwagi

 [Zadanie CreateVisualBasicManifestResourceName —](../msbuild/createvisualbasicmanifestresourcename-task.md) określa odpowiednią nazwę zasobu manifestu, która ma zostać przypisana do danego pliku *resx* lub innego zasobu. Zadanie zawiera nazwę logiczną pliku zasobów, a następnie dołącza ją do parametru wyjściowego jako metadane.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
