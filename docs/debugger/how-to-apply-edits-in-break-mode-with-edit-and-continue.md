---
title: Zastosuj edycje w trybie przerwania za pomocą Edytuj i Kontynuuj | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acdd5b85c77b177dfb5f6d8129594967e902337c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350304"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Instrukcje: stosowanie edycji w trybie przerwania za pomocą Edytuj i Kontynuuj (Visual Basic)
Możesz użyć Edytuj i Kontynuuj, aby edytować swój kod w trybie przerwania, a następnie kontynuować bez zatrzymywania i ponownego uruchamiania.

Aby uzyskać ograniczenia dotyczące używania funkcji Edytuj i Kontynuuj podczas debugowania, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Aby edytować kod w trybie przerwania

1. Przejdź do trybu przerwania, wykonując jedną z następujących czynności:

    - Ustaw punkt przerwania w kodzie, a następnie wybierz **Rozpocznij debugowanie** z menu **Debuguj** i poczekaj, aż aplikacja osiągnie punkt przerwania.

         -lub-

    - Rozpocznij debugowanie, a następnie wybierz polecenie **Przerwij wszystko** w menu **Debuguj** .

         -lub-

    - Gdy wystąpi wyjątek, wybierz pozycję **Włącz edytowanie** w **Asystencie wyjątków**.

2. Wprowadź odpowiednie i obsługiwane zmiany w kodzie.

     Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Jeśli spróbujesz wprowadzić zmianę kodu, która nie jest dozwolona przez edytowanie i kontynuowanie, Edycja zostanie podkreślona purpurową linią falistą i zostanie wyświetlone zadanie w Lista zadań. Nie będzie można kontynuować wykonywania kodu, chyba że zostanie cofnięta niedozwolona zmiana kodu.

3. W menu **debugowanie** kliknij pozycję **Kontynuuj** , aby wznowić wykonywanie.

     Kod jest teraz wykonywany z zastosowaniem zmian wprowadzonych w projekcie.

## <a name="see-also"></a>Zobacz też
- [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Edytuj i kontynuuj (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
