---
title: ResolveManifestFiles — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2628f06ac4eafc7d57123460771793005597b039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632696"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles — zadanie

Rozwiązuje następujące elementy w procesie kompilacji do plików na potrzeby generowania manifestu: skompilowane elementy, zależności, satelity, zawartość, symbole debugowania i dokumentacja.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `ResolveManifestFiles` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa nazwę manifestu wdrożenia.|
|`EntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa zarządzany zestaw lub odwołanie do manifestu ClickOnce, które jest punktem wejścia do manifestu.|
|`ExtraFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa dodatkowe pliki.|
|`ManagedAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa zestawy zarządzane.|
|`NativeAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa zestawy natywne.|
|`OutputAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa wygenerowane zestawy.|
|`OutputDeploymentManifestEntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa punkt wejścia manifestu wdrożenia danych wyjściowych.|
|`OutputEntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa punkt wejścia danych wyjściowych.|
|`OutputFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa pliki wyjściowe.|
|`PublishFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa pliki do opublikowania.|
|`SatelliteAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa zestawy satelickie.|
|`SigningManifests`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` manifesty są podpisane.|
|`TargetCulture`|Opcjonalny `String` parametr.<br /><br /> Określa kulturę docelową dla zestawów satelickich.|
|`TargetFrameworkVersion`|Opcjonalny `String` parametr.<br /><br /> Określa docelową wersję .NET Framework.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
