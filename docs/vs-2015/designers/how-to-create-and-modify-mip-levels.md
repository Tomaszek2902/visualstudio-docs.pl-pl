---
title: 'Instrukcje: Tworzenie i modyfikowanie poziomów MIP | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99d2b07a64781929962ff37823ddcbf219598331
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664481"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Porady: tworzenie i modyfikacja poziomów MIP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie pokazano, jak za pomocą **edytora obrazów** wygenerować i zmodyfikować *poziomy MIP* dla poziomu (LOD) tekstury w miejscu.

## <a name="generating-mip-levels"></a>Generowanie poziomów MIP
 *Mipmapping* to technika, która służy do zwiększenia szybkości renderowania i zmniejszania artefaktów aliasów w obiektach z teksturą przez wstępne obliczenie i przechowywanie kilku kopii tekstury w różnych rozmiarach. Każda kopia, która jest znana jako poziom MIP, ma połowę szerokości i wysokości poprzedniej kopii. Gdy tekstura jest renderowana na powierzchni obiektu, jest automatycznie wybierana wartość MCI, która najlepiej odpowiada obszarowi miejsca na ekranie powierzchni tekstury. Oznacza to, że sprzęt graficzny nie musi odfiltrować dużych tekstur w celu utrzymania spójnej jakości wizualnej. Mimo że koszt pamięci na przechowywanie poziomów MIP wynosi około 33% więcej niż w przypadku oryginalnej samej tekstury, zyski wydajności i jakości obrazu są uzasadniane.

#### <a name="to-generate-mip-levels"></a>Aby wygenerować poziomy MIP

1. Zacznij od podstawowej tekstury, zgodnie z opisem w temacie [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md). Aby uzyskać najlepsze wyniki, należy określić teksturę, która ma szerokość i wysokość, które są potęgami dwóch rozmiarów, na przykład 256, 512, 1024 i tak dalej.

2. Generuj poziomy MIP. Na pasku narzędzi **Tryb edytora obrazów** wybierz kolejno opcje **Zaawansowane**, **Narzędzia**i **Generuj MIPS**.

     Należy zauważyć, że przyciski **Przejdź do następnego poziomu MIP** i **Przejdź do poprzedniego poziomu MIP** są teraz wyświetlane na pasku narzędzi **Tryb edytora obrazów** . Jeśli zostanie wyświetlone okno **Właściwości** , Zauważ, że właściwość tylko do odczytu na **poziomie MCI** i na **poziomie MCI** jest teraz wyświetlana we właściwościach obrazu.

## <a name="modifying-mip-levels"></a>Modyfikowanie poziomów MIP
 Aby osiągnąć efekty specjalne lub zwiększyć jakość obrazu na określonych poziomach szczegółowości, można zmodyfikować każdy poziom MCI osobno. Na przykład można nadać obiektowi tekstury inny wygląd na odległość (większa odległość odpowiada mniejszym poziomom MIP) lub można zagwarantować, że tekstury, które zawierają tekst lub symbole, pozostaną czytelne nawet na mniejszych poziomach MCI.

#### <a name="to-modify-an-individual-mip-level"></a>Aby zmodyfikować indywidualny poziom MCI

1. Wybierz poziom MIP, który chcesz zmodyfikować. Na pasku narzędzi **Tryb edytora obrazów** Użyj przycisków **Przejdź do następnego MIP** i **Przejdź do poprzedniego poziomu MIP** , aby przejść między poziomami MCI.

2. Po wybraniu poziomu MIP, który chcesz zmodyfikować, można użyć narzędzi do rysowania, aby zmodyfikować go bez zmiany zawartości innych poziomów MIP. Narzędzia do rysowania są dostępne na pasku narzędzi **edytora obrazów** . Po wybraniu narzędzia można zmienić jego właściwości w oknie **Właściwości** . Aby uzyskać informacje o narzędziach rysowania i ich właściwościach, zobacz [Edytor obrazów](../designers/image-editor.md).

> [!NOTE]
> Jeśli nie trzeba modyfikować zawartości poszczególnych poziomów MIP, jak można osiągnąć pewne efekty — zalecamy generowanie mipmapy z tekstury źródłowej w czasie kompilacji. Pozwala to zagwarantować, że poziomy MCI pozostają zsynchronizowane ze teksturą źródłową, ponieważ modyfikacje poziomu MIP nie są propagowane do innych poziomów automatycznie. Aby uzyskać więcej informacji na temat generowania mipmapy w czasie kompilacji, zobacz [How to: Export a tekstury, która zawiera mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md)
