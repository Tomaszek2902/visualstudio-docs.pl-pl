---
title: Właściwości kształtów przedziału | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3caf9828f678c72bf756063183f7d867c5c0e66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652048"
---
# <a name="properties-of-compartment-shapes"></a>Właściwości kształtów przedziałów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kształty przedziału są jednym z kształtów, których można użyć do wyświetlania klasy domeny w języku specyficznym dla domeny. Przedziały można rozwijać i zwijać.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Kształty przedziału mają właściwości, które są wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślne|
|--------------|-----------------|-------------|
|Domyślny stan zwijania rozwiń|Jeśli `Expanded` przedziały są pokazywane podczas tworzenia. Jeśli `Collapsed` nie, to nie.|Rozwinięte|
|Kolor wypełnienia|Kolor wypełnienia tego kształtu.|Biały|
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|Pozioma|
|Geometria|Geometria tego kształtu (prostokąt lub prostokąt zaokrąglony).|Prostokąt|
|Ma domyślne punkty połączenia|Jeśli `True` kształt będzie używać górnego, dolnego, lewego i prawego punktu połączenia w wygenerowanym projektancie.|Fałsz|
|Widoczny nagłówek pojedynczego przedziału|Jeśli `False` i kształt ma jeden przedział, nagłówek przedziału nie jest widoczny.|Prawda|
|Kolor konturu|Kolor konturu tego kształtu.|Czarnoskórzy|
|Styl kreskowania konturu|Styl kreskowania konturu tego kształtu (pełny, kreska, kropka, DashDot, DashDotDot, niestandardowy).|Ciągła|
|Grubość konturu|Grubość konturu tego kształtu.|0,03125|
|Kolor tekstu|Kolor używany dla dekoratory tekstu, które są skojarzone z tym kształtem.|Czarnoskórzy|
|Modyfikator dostępu|Poziom dostępu kształtu przedziału ( `public` lub `internal` ).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z tego kształtu przedziału|\<none>|
|Generuje podwójny pochodny|Jeśli `True` , zostanie wygenerowany zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma Konstruktor niestandardowy|Jeśli `True` w kodzie źródłowym zostanie podany Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z kształtu przedziału ( `none` `abstract` lub `sealed` ).|Brak|
|Podstawowy kształt przedziału|Klasa bazowa tego kształtu.|(brak)|
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z tym kształtem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Sposób definiowania etykietki narzędzia (stała, zmienna lub brak). Jeśli stała, wartość `Fixed Tooltip Text` właściwości jest używana jako etykietka narzędzia; Jeśli zmienna, a następnie etykietka narzędzia jest definiowana w kodzie niestandardowym.|brak|
|Uwagi|Nieformalne notatki, które są skojarzone z tym kształtem.|\<none>|
|Początkowa wysokość|Początkowa wysokość tego kształtu (w calach). W przypadku kształtów przedziału jest to wysokość sekcji tylko nagłówka i nie można zmienić jej rozmiaru.|1|
|Szerokość początkowa|Początkowa Szerokość tego kształtu (w calach).|1.5|
|Uwidoczniony kolor wypełnienia jako właściwość<br /><br /> Uwidaczniany tryb gradientu wypełnienia<br /><br /> Uwidoczniony kolor konturu jako właściwość<br /><br /> Uwidoczniony styl kreskowania konturu jako właściwość<br /><br /> Uwidoczniona grubość konturu jako właściwość<br /><br /> Uwidacznia kolor tekstu|Jeśli `True` użytkownik może ustawić właściwość wartość dla kształtu. Aby ustawić tę opcję, kliknij prawym przyciskiem myszy definicję kształtu, a następnie kliknij pozycję **Dodaj uwidocznione**.|Fałsz|
|Opis|Służy do dokumentowania wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego kształtu.|\<none>|
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałej etykietki narzędzia.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego kształtu.|\<none>|

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
