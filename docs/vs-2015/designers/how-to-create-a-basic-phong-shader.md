---
title: 'Instrukcje: Tworzenie podstawowego modułu cieniującego podstawowego Phong | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 17ba5d143a5f4534b09b2aaff718af7ce99f2773
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664550"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Porady: tworzenie podstawowego modułu cieniowanie Phong
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób użycia projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) w celu utworzenia cieniowania oświetlenia implementującego klasyczny model oświetlenia podstawowego Phong.

 W tym dokumencie przedstawiono następujące działania:

- Dodawanie węzłów do wykresu cieniowania

- Odłączanie węzłów

- Łączenie węzłów

## <a name="the-phong-lighting-model"></a>Model oświetlenia podstawowego Phong
 Model oświetlenia podstawowego Phong rozszerza model oświetlenia Lamberta w taki sposób, aby obejmował wyróżnianie odblasków, które symuluje właściwości odbicia powierzchni. Składnik odblasków zapewnia dodatkowe oświetlenie z tych samych kierunkowych źródeł światła, które są używane w modelu oświetlenia Lamberta, ale jego udział w kolorze końcowym jest przetwarzany inaczej. Wyróżnianie odblasków ma wpływ na każdą powierzchnię w scenie, na podstawie relacji między kierunkiem widoku, kierunku źródeł światła i orientacji powierzchni. Jest to iloczyn koloru odblasków, mocy odblasków i orientacji powierzchni oraz kolor, intensywność i kierunek źródeł światła. Powierzchnie odzwierciedlające Źródło światła bezpośrednio w przeglądarce otrzymują maksymalny udział odblasków i powierzchnie, które odzwierciedlają Źródło światła od przeglądarki, nie otrzymują żadnego wkładu. W modelu oświetlenia podstawowego Phong, co najmniej jeden składnik odblasków jest połączony, aby określić kolor i intensywność wyróżniania odblasków dla każdego punktu w obiekcie, a następnie są dodawane do wyniku modelu oświetlenia Lamberta w celu uzyskania końcowego koloru piksela.

 Aby uzyskać więcej informacji na temat modelu oświetlenia Lamberta, zobacz [How to: Create a Basic Lamberta Shader](../designers/how-to-create-a-basic-lambert-shader.md).

 Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

#### <a name="to-create-a-phong-shader"></a>Aby utworzyć cieniowanie podstawowego Phong

1. Utwórz moduł cieniujący Lamberta, zgodnie z opisem w [instrukcje: Tworzenie podstawowego cieniowania Lamberta](../designers/how-to-create-a-basic-lambert-shader.md).

2. Odłącz węzeł **Lamberta** od końcowego węzła **koloru** . Wybierz Terminal **RGB** węzła **Lamberta** , a następnie wybierz polecenie **Przerwij linki**. Powoduje to powolne miejsce dla węzła, który jest dodawany w następnym kroku.

3. Dodaj węzeł **Dodaj** do grafu. W **przyborniku**w obszarze **matematyka**wybierz pozycję **Dodaj** i przenieś ją na powierzchnię projektu.

4. Dodaj węzeł **odblasków** do grafu. W **przyborniku**, w obszarze **Narzędzia**, wybierz pozycję **odblasków** i przenieś ją na powierzchnię projektu.

5. Dodaj udział odblasków. Przenieś Terminal **danych wyjściowych** węzła **odblasków** do terminalu **X** w **Dodaj** węzeł, a następnie przenieś Terminal **wyjściowy** węzła **Lamberta** do terminalu **Y** w **Dodaj** węzeł. Połączenia te łączą łączne odblasków, rozpraszania i koloru w pikselach.

6. Połącz obliczoną wartość koloru z końcowym kolorem. Przenieś Terminal **wyjściowy** węzła **Dodaj** do terminalu **RGB** **końcowego węzła Color** .

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modelu czajniczek.

> [!NOTE]
> Aby lepiej zademonstrować efekt cieniowania na tej ilustracji, kolor pomarańczowy został określony przy użyciu parametru **MaterialDiffuse** modułu cieniującego, a zakończenie w postaci metalicznej jest określone za pomocą parametrów **MaterialSpecular** i **MaterialSpecularPower** . Aby uzyskać informacje o parametrach materiału, zobacz sekcję podglądy programów do cieniowania w [projektancie cieniowania](../designers/shader-designer.md).

 ![Graf cieniowania i podgląd jego efektu](../designers/media/digit-lighting-graph.png "Oświetlenie cyfrowe — Graf")

 Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz sekcję podglądy programów do cieniowania w [projektancie cieniowania](../designers/shader-designer.md) .

 Na poniższej ilustracji przedstawiono program do cieniowania opisany w tym dokumencie, stosowany do modelu 3-D. Właściwość **MaterialSpecular** jest ustawiona na wartość (1,00, 0,50, 0,20, 0,00), a jej właściwość **MaterialSpecularPower** ma wartość 16.

> [!NOTE]
> Właściwość **MaterialSpecular** określa pozorne zakończenie materiału Surface. Wysoce błyszcząca powierzchnia, taka jak szkło lub plastik, ma kolor odblasków, który jest jasnego cienia bieli. Powierzchnia metaliczna ma kolor odblasków, który znajduje się blisko jego koloru rozpraszania. Powierzchnia SATINA jest kolorem odblasków, który jest ciemnym odcieniem szarości.
>
> Właściwość **MaterialSpecularPower** określa, jak intensywne są najważniejsze odblasków. Wysoki odblasków zapewnia symulację bardziej zlokalizowanych wyróżnień. Bardzo małe uprawnienia odblasków symulują intensywne, jasne wyróżnienia, które mogą zmniejszać nasycenie i ukrywać kolor całej powierzchni.

 ![Oświetlenie podstawowego Phong zastosowane do modelu](../designers/media/digit-lighting-model.png "Model oświetlenia cyfrowego")

 Aby uzyskać więcej informacji na temat sposobu stosowania cieniowania do modelu 3-D, zobacz [How to: Apply a Shader to a 3-d model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [instrukcje: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md) [instrukcje: Tworzenie podstawowego](../designers/how-to-create-a-basic-lambert-shader.md) [Shader Designer](../designers/shader-designer.md) [węzła projektanta](../designers/shader-designer-nodes.md) cieniowania lambertaego programu do cieniowania
