---
title: Właściwości klas domeny
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b3ff1ece9e57239b49c5dcbef5091a14d8b0fa5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810031"
---
# <a name="properties-of-domain-classes"></a>Właściwości klas domeny
Klasy domeny mają właściwości w poniższej tabeli. Aby uzyskać informacje o klasach domen, zobacz [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślny|
|-|-|-|
|Modyfikator dostępu|Poziom dostępu do klasy domeny ( `public` lub `internal` ).|`public`|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z tej klasy domeny.|\<none>|
|Generuje podwójny pochodny|Jeśli `True` , zostanie wygenerowany zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ma Konstruktor niestandardowy|Jeśli `True` w kodzie źródłowym zostanie podany Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z klasy domeny ( `none` `abstract` lub `sealed` ).|`none`|
|Klasa bazowa|Jeśli ta klasa domeny jest pochodna, nazwa klasy podstawowej.|\<none>|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw tej klasy domeny.|Bieżąca przestrzeń nazw|
|Uwagi|Nieformalne uwagi, które są skojarzone z tą klasą domeny.|\<none>|
|Opis|Opis używany do dokumentowania interfejsu użytkownika wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<none>|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tej klasy domeny.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))