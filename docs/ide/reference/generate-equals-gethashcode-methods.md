---
title: Generuj zastąpienia metody Equals i GetHashCode języka C#
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569286"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generuj zastąpienia metody Equals i GetHashCode w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** Umożliwia generowanie metod **Equals** i **GetHashCode** .

**Kiedy:** Generuj te zastąpienia, gdy masz typ, który powinien być porównywany przez co najmniej jedno pole, a nie lokalizację obiektu w pamięci.

**Zalet**

- W przypadku implementowania typu wartości należy rozważyć Zastępowanie metody **Equals** , aby uzyskać większą wydajność w porównaniu z domyślną implementacją metody Equals dla elementu ValueType.

- Jeśli wdrażasz typ referencyjny, należy rozważyć Zastępowanie metody **Equals** , jeśli typ wygląda jak typ podstawowy, taki jak Point, String, BigNumber itd.

- Zastąp metodę **GetHashCode** , aby umożliwić prawidłowe działanie typu w tabeli skrótów. Przeczytaj więcej wskazówek na temat [operatorów równości](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym miejscu w wierszu deklaracji typu.

   ![Wyróżniony kod](media/overrides-highlight-cs.png)

   > [!TIP]
   > Nie klikaj dwukrotnie opcji zaznacz nazwę typu lub opcja menu nie będzie dostępna. Umieść kursor w dowolnym miejscu w wierszu.

1. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij pozycję ![śrubokręt](../media/screwdriver-icon.png) ikona wyświetlana na lewym marginesie.

   ![Generuj Podgląd przesłonięć](media/overrides-preview-cs.png)

1. Wybierz pozycję **Generuj wartość Equals (Object)** lub **Generuj wartość Equals i GetHashCode** z menu rozwijanego.

1. W oknie dialogowym **Wybierz członków** wybierz członków, dla których chcesz wygenerować metody:

    ![Generowanie okna dialogowego zastąpień](media/overrides-dialog-cs.png)

    > [!TIP]
    > Możesz również generować operatory z tego okna dialogowego przy użyciu pola wyboru w dolnej części okna dialogowego.

   `Equals`Metody i `GetHashCode` są generowane z domyślnymi implementacjami.

   ![Generowanie wyniku metody](media/overrides-result-cs.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
