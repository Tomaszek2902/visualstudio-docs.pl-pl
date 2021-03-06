---
title: Przyciski okna właściwości | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706172"
---
# <a name="properties-window-buttons"></a>Przyciski okna właściwości
W zależności od języka programowania i typu produktu niektóre przyciski są domyślnie wyświetlane na pasku narzędzi okna **Właściwości** . We wszystkich przypadkach są wyświetlane **przyciski z**przydzielonymi, **alfabetycznymi**, **właściwościami**i **stronami właściwości** . W Visual C# i Visual Basic jest również wyświetlany przycisk **zdarzenia** . W niektórych projektach Visual C++ są wyświetlane **komunikaty VC + +** i przyciski **zastąpień VC** . Dodatkowe przyciski mogą być wyświetlane dla innych typów projektów. Aby uzyskać więcej informacji o przyciskach w oknie **Właściwości** , zobacz [okno właściwości](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementacja przycisków okna właściwości
 Po kliknięciu przycisku z **kategoryzacją** program Visual Studio wywoła <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfejs na obiekcie, który ma fokus, aby posortować jego właściwości według kategorii. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> jest zaimplementowany dla `IDispatch` obiektu, który jest prezentowany w oknie **Właściwości** .

 Istnieją 11 wstępnie zdefiniowanych kategorii właściwości, które mają wartości ujemne. Można definiować niestandardowe kategorie, ale zalecamy przypisanie im wartości dodatnich, aby odróżnić je od wstępnie zdefiniowanych kategorii.

 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>Metoda zwraca odpowiednią wartość kategorii właściwości dla określonej właściwości. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>Metoda zwraca ciąg, który zawiera nazwę kategorii. Musisz zapewnić obsługę niestandardowych wartości kategorii, ponieważ program Visual Studio wie standardowe wartości kategorii właściwości.

 Po kliknięciu przycisku z **alfabetem** właściwości są wyświetlane w kolejności alfabetycznej według nazwy. Nazwy są pobierane przez `IDispatch` uwzględnienie zlokalizowanego algorytmu sortowania.

 Po otwarciu okna **Właściwości** przycisk **Właściwości** jest automatycznie pokazywany jako zaznaczony. W innych częściach środowiska zostanie wyświetlony ten sam przycisk, a następnie można kliknąć go, aby wyświetlić okno **Właściwości** .

 Przycisk **strony właściwości** jest niedostępny, jeśli `ISpecifyPropertyPages` nie jest zaimplementowany dla wybranego obiektu. Na stronach właściwości są wyświetlane właściwości zależne od konfiguracji, które są zwykle skojarzone z rozwiązaniami i projektami, ale można je także kojarzyć z elementami projektu (na przykład w Visual C++).

> [!NOTE]
> Nie można dodać przycisków paska narzędzi do okna **Właściwości** przy użyciu kodu niezarządzanego. Aby dodać przycisk paska narzędzi, należy utworzyć obiekt zarządzany, który pochodzi od <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
