---
title: Jak modelować tereny 3W
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12f19363d9024f8e7e2deb69a8038b8854eb50e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768963"
---
# <a name="how-to-model-3d-terrain"></a>Jak modelować tereny 3W

W tym artykule pokazano, jak za pomocą edytora modelu utworzyć model terenowy 3W.

## <a name="create-a-3d-terrain-model"></a>Tworzenie modelu terenowego 3W

Można utworzyć trójwymiarowe przedzielenie płaszczyzny, aby utworzyć dodatkowe twarze, a następnie operować swoimi wierzchołkami w celu utworzenia interesujących funkcji terenu.

Po zakończeniu model powinien wyglądać następująco:

![3&#45;D sceny, która przedstawia model terenu](../designers/media/digit-terrain-model.png)

Przed rozpoczęciem upewnij się, że okno **Właściwości** i **Przybornik** są wyświetlane.

1. Utwórz model 3W, z którym chcesz korzystać. Aby uzyskać informacje o sposobach dodawania modelu do projektu, zobacz sekcję Wprowadzenie w [Edytorze modelu](../designers/model-editor.md).

2. Dodaj płaszczyznę do sceny. W **przyborniku**, w obszarze **kształty**wybierz pozycję **płaszczyzna** i przenieś ją na powierzchnię projektu.

    > [!TIP]
    > Aby obiekt płaszczyzny był łatwiejszy do pracy, możesz go ramkować na powierzchni projektowej. W obszarze tryb **wyboru** wybierz obiekt płaszczyzny, a następnie na pasku narzędzi Edytor modelu wybierz przycisk **obiekt ramki** .

3. Przejdź do trybu wyboru kroju. Na pasku narzędzi Edytor modelu wybierz **pozycję Wybierz opcję**.

4. Podziel płaszczyznę. W trybie zaznaczania powierzchni wybierz płaszczyznę jednokrotną, aby ją uaktywnić do zaznaczenia, a następnie wybierz ją ponownie, aby zaznaczyć jej tylko. Na pasku narzędzi Edytor **modelu wybierz opcję**Podziel na siebie. Spowoduje to dodanie nowych wierzchołków do płaszczyzny dzielącej ją na cztery partycje o równym rozmiarze.

5. Utwórz więcej podziałów. Po wybraniu nowych **twarzy** wybierz pozycję Podziel na dwie godziny. Spowoduje to utworzenie łącznej liczby 64 twarzy. Tworząc więcej podziałów, można bardziej szczegółowo udostępnić teren.

6. Przejdź do trybu wyboru punktu. Na pasku narzędzi Edytor modelu wybierz pozycję **Wybierz punkt**.

7. Zmodyfikuj punkt, aby utworzyć funkcję terenu. W trybie wyboru punktu wybierz jeden z punktów, a następnie na pasku narzędzi Edytor modelu wybierz narzędzie **tłumaczenie** . Pole reprezentujące punkt pojawia się na powierzchni projektowej. Użyj zieloną strzałkę, aby przenieść pole, a tym samym zmodyfikować wysokość punktu. Powtórz ten krok dla różnych punktów, aby utworzyć interesujące funkcje terenu.

    > [!TIP]
    > Można wybrać kilka punktów jednocześnie, aby je zmodyfikować w jednolity sposób.

Model terenu został ukończony. Oto ponownie ostateczny model z zastosowanym cieniowaniem podstawowego Phong:

![3&#45;D sceny, która przedstawia model terenu](../designers/media/digit-terrain-model.png)

Możesz użyć tego modelu terenu, aby zademonstrować efekt cieniowania gradientu, który jest opisany w [instrukcje: Tworzenie cieniowania gradientowego opartego na geometrii](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Zobacz też

- [Edytor modelu](../designers/model-editor.md)
