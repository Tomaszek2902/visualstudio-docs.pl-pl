---
title: ResolveKeySource — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa4e2454a0216e697ed12404091eb0ef16416cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632709"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource — zadanie

Określa źródło klucza o silnej nazwie.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `ResolveKeySource` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Opcjonalny `Int32` parametr.<br /><br /> Pobiera lub ustawia czas (w sekundach) wyświetlania komunikatu o pomniejszeniu.|
|`AutoClosePasswordPromptTimeout`|Opcjonalny `Int32` parametr.<br /><br /> Pobiera lub ustawia czas (w sekundach) oczekiwania przed zamknięciem okna dialogowego monitu o hasło.|
|`CertificateFile`|Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia ścieżkę pliku certyfikatu.|
|`CertificateThumbprint`|Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu.|
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia ścieżkę pliku klucza.|
|`ResolvedKeyContainer`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozpoznany kontener kluczy.|
|`ResolvedKeyFile`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozpoznany plik klucza.|
|`ResolvedThumbprint`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia odcisk palca rozpoznanego certyfikatu.|
|`ShowImportDialogDespitePreviousFailures`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , Pokaż okno dialogowe importowania pomimo poprzednich błędów.|
|`SuppressAutoClosePasswordPrompt`|Opcjonalny `Boolean` parametr.<br /><br /> Pobiera lub ustawia wartość logiczną określającą, czy okno dialogowe monitu o hasło nie powinno być autozamykane.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
