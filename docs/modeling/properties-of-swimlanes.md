---
title: Właściwości torów
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec27b9b4f90b1f3ec75edef6dca01b1ed7b8adf
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90807849"
---
# <a name="properties-of-swimlanes"></a>Właściwości torów
Można dodać tory do diagramu. Tory dzielą diagram na obszary pionowe lub poziome. Można definiować inne kształty, które będą wyświetlane wewnątrz torów. Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Tory mają właściwości, które są wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślny|
|-|-|-|
|Kolor wypełnienia treści|Kolor wypełnienia dla treści toru.|Biały|
|Kolor wypełnienia nagłówka|Kolor wypełnienia nagłówka toru.|DarkGray|
|Kolor separatora|Kolor linii separatora.|LightGray|
|Styl linii separatora|Styl linii separatora ( `Solid` ,,, `Dash` , `Dot` `DashDot` `DashDotDot` lub `Custom` ).|`Dash`|
|Grubość separatora|Grubość linii separatora w calach.|0,03125|
|Kolor tekstu|Kolor używany dla dekoratory tekstu, które są skojarzone z tym torem.|Czarnoskórzy|
|Modyfikator dostępu|Poziom dostępu klasy ( `public` lub `internal` ).|Public|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu, która jest generowana z tego toru.|\<none>|
|Generuje podwójny pochodny|Jeśli `True` , zostanie wygenerowany zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma Konstruktor niestandardowy|Jeśli `True` w kodzie źródłowym zostanie podany Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana na podstawie toru ( `none` `abstract` lub `sealed` ).|brak|
|Tor podstawowy|Klasa bazowa tego toru.|(brak)|
|Nazwa|Nazwa tego toru.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z tym torem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Sposób definiowania etykietki narzędzia ( `fixed` , `variable` lub `none` ). Jeśli `fixed` , wówczas `Fixed Tooltip Text` zostanie użyta wartość właściwości; Jeśli `variable` , wówczas etykietka narzędzia jest definiowana w kodzie niestandardowym.|\<none>|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym torem.|\<none>|
|Wyrównanie|Wyrównanie w poziomie lub w pionie.|Pionowa|
|Początkowa wysokość|Początkowa wysokość tego toru, w calach. Dotyczy tylko torów poziomych.|0|
|Szerokość początkowa|Początkowa Szerokość tego toru, w calach. Dotyczy tylko torów pionowych.|0|
|Uwidacznia kolor tekstu|Jeśli `True` użytkownik może ustawić kolor toru w wygenerowanym projektancie. Aby ustawić tę opcję, kliknij prawym przyciskiem myszy kształt toru, a następnie kliknij pozycję **Dodaj uwidocznione**.|Fałsz|
|Opis|Służy do dokumentowania wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie do odwoływania się do tej klasy toru.|\<none>|
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałej etykietki narzędzia.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego toru.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))