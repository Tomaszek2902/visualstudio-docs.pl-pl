---
title: 'Porady: tworzenie modułu cieniującego gradientu geometrycznego'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e10fd5266ba39febe6261f41437c10c19b5c82f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769113"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Instrukcje: tworzenie cieniowania gradientu geometrycznego

W tym artykule pokazano, jak używać projektanta programu do cieniowania i języka ukierunkowanego modułu cieniującego Graph do tworzenia cieniowania gradientowego opartego na geometrii. Ten program do cieniowania skaluje stałą wartość koloru RGB o wysokości każdego punktu obiektu w przestrzeni światowej.

## <a name="create-a-geometry-based-gradient-shader"></a>Tworzenie cieniowania gradientu geometrycznego

Można zaimplementować cieniowanie oparte na geometrii, dołączając pozycję piksela do cieniowania. W językach cieniowania piksel zawiera więcej informacji niż tylko jego kolor i lokalizacja na ekranie 2D. Piksel — znany jako *fragment* w niektórych systemach — jest kolekcją wartości, które opisują powierzchnię, która odnosi się do piksela. Program do cieniowania, który jest opisany w tym dokumencie, wykorzystuje wysokość każdego piksela obiektu 3W w przestrzeni kosmicznej, aby mieć wpływ na końcowy kolor wyjściowy fragmentu.

Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

1. Utwórz program do cieniowania DGSL, który będzie działał. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

2. Odłącz węzeł **koloru punktu** od końcowego węzła **koloru** . Wybierz Terminal **RGB** w węźle **Kolor punktu** , a następnie wybierz polecenie **Przerwij linki**. Powoduje to powolne miejsce dla węzła, który jest dodawany w następnym kroku.

3. Dodaj węzeł **pomnóż** do grafu. W **przyborniku**, w obszarze **Math**, zaznacz opcję **pomnóż** i przenieś ją na powierzchnię projektu.

4. Dodaj węzeł **wektora maski** do grafu. W **przyborniku**w obszarze **Narzędzia**wybierz pozycję **maska wektora** i przenieś ją na powierzchnię projektu.

5. Określ wartości maski dla węzła **wektora maski** . W obszarze tryb **wyboru** wybierz węzeł **Vector Mask** , a następnie w oknie **Właściwości** ustaw właściwość **Green/Y** na **wartość true**, a następnie ustaw wartość **false**dla właściwości **Red/X**, **Blue/Z** i **Alpha/W** . W tym przykładzie właściwości **Red/X**, **Green/Y**i **Blue/Z** są zgodne ze składnikami X, Y i z w węźle **pozycja świata** , a **alfa/W** nie są używane. Ponieważ tylko **zielony/Y** ma **wartość true**, tylko składnik Y wektora wejściowego pozostaje po zamaskowanyu.

6. Dodaj węzeł **pozycji świata** do grafu. W **przyborniku**, w obszarze **stałe**wybierz **pozycję świat** i przenieś ją do powierzchni projektowej.

7. Maskowanie położenia obszaru na całym świecie. W trybie **wyboru** Przenieś Terminal **wyjściowy** węzła **pozycja świata** do terminalu **wektorowego** węzła **wektora maski** . To połączenie maskuje położenie fragmentu, aby zignorować składniki x i z.

8. Pomnóż wartość koloru RGB przez zamaskowane miejsce na całym świecie. Przenieś Terminal **RGB** węzła **koloru punktu** do terminalu **Y** węzła **pomnóż** , a następnie przenieś Terminal **wyjściowy** węzła **wektora maski** do terminalu **X** w **rozmnożonym** węźle. To połączenie skaluje wartość koloru o wysokości pikseli w przestrzeni świata.

9. Połącz wartość skalowanego koloru z końcowym kolorem. Przenieś Terminal **wyjściowy** węzła **mnożenia** do terminalu **RGB** **końcowego węzła Color** .

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do sfery.

> [!NOTE]
> Na tej ilustracji zostanie określony pomarańczowy kolor, aby lepiej zademonstrować efekt cieniowania, ale ponieważ kształt podglądu nie ma pozycji na świecie, cieniowanie nie może być w pełni przeglądane w projektancie cieniowania. Aby zademonstrować pełen efekt, cieniowanie musi być widoczne w prawdziwej scenie.

![Graf cieniowania i podgląd jego efektu](../designers/media/digit-gradient-effect-graph.png)

Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać informacje o tym, jak wyświetlić podgląd programów do cieniowania w projektancie cieniowania, zobacz **Podgląd** programów do cieniowania w [projektancie cieniowania](../designers/shader-designer.md).

Na poniższej ilustracji przedstawiono program do cieniowania opisany w tym dokumencie, który został zastosowany do sceny 3W, która została pokazana w temacie [How to: Modeling The 3D](../designers/how-to-model-3-d-terrain.md). Intensywność koloru zwiększa się o wysokość punktu na świecie.

![Efekt gradientu stosowany do modelu terenowego 3&#45;D](../designers/media/digit-gradient-effect-result.png)

Aby uzyskać więcej informacji na temat sposobu stosowania cieniowania do modelu 3D, zobacz [How to: Apply a Shader to a model 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Jak modelować tereny 3W](../designers/how-to-model-3-d-terrain.md)
- [Instrukcje: tworzenie cieniowania tekstury skali szarości](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Projektant programu do cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
