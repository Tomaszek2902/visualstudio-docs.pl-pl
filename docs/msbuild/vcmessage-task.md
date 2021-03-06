---
title: VCMessage — — zadanie | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631214"
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie

Rejestruje ostrzeżenia i komunikaty o błędach podczas kompilacji.

## <a name="remarks"></a>Uwagi

 To zadanie ułatwia implementację programu MSBuild dla projektów języka C++ i nie jest przeznaczone do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **VCMessage —** .

|Parametr|Opis|
|---------------|-----------------|
|**Argumenty**|Opcjonalny parametr **ciągu** .<br /><br /> Rozdzielana średnikami lista komunikatów do wyświetlenia.|
|**Kod**|Wymagany parametr **ciągu** .<br /><br /> Numer błędu, który uprawnia do wiadomości.|
|**Typ**|Opcjonalny parametr **ciągu** .<br /><br /> Określa rodzaj komunikatu do emisji. Określ "ostrzeżenie", aby emitować komunikat ostrzegawczy, lub "błąd", aby wyemitować komunikat o błędzie.|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
