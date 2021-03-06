---
title: GenerateTrustInfo — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84007c9a10618c6d757a36debe58c272302fa3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634035"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo — zadanie

Generuje zaufanie aplikacji z manifestu podstawowego oraz z `TargetZone` `ExcludedPermissions` parametrów i.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `GenerateTrustInfo` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationDependencies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa zestawy zależne.|
|`BaseManifest`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa manifest podstawowy, z którego ma zostać wygenerowane zaufanie aplikacji.|
|`ExcludedPermissions`|Opcjonalny `String` parametr.<br /><br /> Określa jedną lub więcej wartości tożsamości uprawnień oddzielonych średnikami, które mają zostać wykluczone z domyślnego zestawu uprawnień strefy.|
|`TargetZone`|Opcjonalny `String` parametr.<br /><br /> Określa domyślny zestaw uprawnień strefy, który jest uzyskiwany z zasad komputera.|
|`TrustInfoFile`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa plik, który zawiera informacje o zaufaniu zabezpieczeń aplikacji.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)