---
title: Opcje refaktoryzacji statycznej funkcji lokalnej
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77144837"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Statyczne refaktoryzacje funkcji lokalnych i szybkie akcje

W tym artykule przedstawiono dwie funkcje produktywności związane ze statycznymi funkcjami lokalnymi. Jednym z nich jest Refaktoryzacja, która sprawia, że funkcja lokalna jest statyczna, a druga — szybka akcja, która generuje kod do przekazywania zmiennych do statycznej funkcji lokalnej.

## <a name="make-local-function-static"></a>Tworzenie funkcji statycznych z funkcji lokalnych

To Refaktoryzacja dotyczy:

- C#

**Co:** Sprawia, że funkcja lokalna static i passuje zmienne zdefiniowane poza funkcją do deklaracji i wywołań funkcji.

**Kiedy:** Chcesz, aby lokalna funkcja była statyczna i dla wszystkich zmiennych, które mają być zdefiniowane w zakresie funkcji.

**Dlaczego:** Statyczne funkcje lokalne zwiększają czytelność: wiedzą, że konkretny kod jest izolowany, ułatwia zrozumienie, ponowne odczytywanie i używanie. Statyczne funkcje lokalne zapewniają również określanie zakresu, aby zapobiec zanieczyszczaniu klasy za pomocą funkcji statycznej, która jest wywoływana tylko w jednej metodzie.

### <a name="how-to"></a>Porady

1. Umieść karetkę na nazwie funkcji lokalnej.

2. Naciśnij klawisz **Ctrl** + **.** (okres), aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Tworzenie funkcji statycznych z funkcji lokalnych](media/make-local-function-static.png)

3. Wybierz pozycję **Utwórz funkcję lokalną "static".**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Jawnie Przekaż zmienną w statycznej funkcji lokalnej

Ta szybka akcja dotyczy:

- C#

**Co:** Przekazuje zmienną jawnie do lokalnej funkcji statycznej.

**Kiedy:** Chcesz, aby funkcja lokalna była statyczna, ale nadal używa zmiennych zainicjowanych poza nią.

**Dlaczego:** Używanie statycznych funkcji lokalnych zapewnia użytkownikom wyjaśnienie, ponieważ wiedzą, że mogą być deklarowane i wywoływane tylko w określonym kontekście programu. Zapewnia elastyczność definiowania zmiennych poza tym kontekstem, ale nadal może przekazać je jako argumenty do statycznej funkcji lokalnej.

### <a name="how-to"></a>Porady

1. Umieść karetkę na zmiennej, w której jest używana w statycznej funkcji lokalnej.

2. Naciśnij klawisz **Ctrl** + **.** (okres), aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Jawnie przekazanie zmiennej w statycznej funkcji lokalnej](media/pass-variable-explicitly-static-local-function.png)

3. Wybierz pozycję **Przekaż jawnie zmienną do lokalnej funkcji statycznej**

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)