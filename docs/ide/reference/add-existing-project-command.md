---
title: Dodaj istniejący projekt — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008802546d87bd44137c6d13ee2aef802877e308
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595881"
---
# <a name="add-existing-project-command"></a>Dodaj istniejący projekt — Polecenie
Dodaje istniejący projekt do bieżącego rozwiązania.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumenty
`filename`\
Opcjonalny. Pełna ścieżka i nazwa projektu, z rozszerzeniem, projektu do dodania do rozwiązania.

Jeśli `filename` argument zawiera spacje, musi być ujęty w cudzysłów.

Jeśli nazwa pliku nie zostanie określona, polecenie spowoduje otwarcie okna dialogowego plików, dzięki czemu użytkownik może wybrać projekt.

## <a name="remarks"></a>Uwagi
Funkcja automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.

## <a name="example"></a>Przykład
Ten przykład dodaje [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekt, TestProject1 do bieżącego rozwiązania.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
