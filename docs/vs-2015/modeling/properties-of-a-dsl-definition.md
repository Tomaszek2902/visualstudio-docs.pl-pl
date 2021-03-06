---
title: Właściwości definicji DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8755b1b70051c54157fa87ee0b66dbc9340b5024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668464"
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Właściwości DslDefinition definiują *specyficzne dla domeny* właściwości definicji języka, takie jak numer wersji. Właściwości DslDefinition są wyświetlane w oknie **Właściwości** po kliknięciu otwartego obszaru diagramu w *Projektant języka specyficznego dla domeny*.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition ma właściwości w poniższej tabeli:

|Właściwość|Opis|Domyślne|
|--------------|-----------------|-------------|
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny, czy wewnętrzny.|public|
|Atrybuty niestandardowe|Niestandardowe atrybuty zdefiniowane dla klasy domeny.<br /><br /> **Uwaga** Użyj przycisku Przeglądaj, aby dodać atrybut.|\<none>|
|Nazwa firmy|Nazwa bieżącej nazwy firmy w rejestrze systemowym.|Nazwa bieżącej firmy|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw stowarzyszona z tą klasą domeny.|Bieżąca przestrzeń nazw|
|Identyfikator GUID pakietu|Identyfikator GUID [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pakietu wygenerowanego dla tego języka DSL.|\<none>|
|Przestrzeń nazw pakietu|Przestrzeń nazw dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pakietu wygenerowanego dla tego języka DSL.|\<none>|
|Nazwa produktu|Nazwa produktu, która zostanie zarejestrowana dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pakietu wygenerowanego dla tego języka DSL.|\<none>|
|Uwagi|Uwagi skojarzone z tą klasą domeny.|\<none>|
|Opis|Opis tej klasy domeny.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe pomocy skojarzone z tą klasą domeny.|\<none>|
|Kompilacja|Numer kompilacji przyrostowej dla tej definicji języka specyficznego dla domeny.|0|
|Wersja główna|Przyrostowy numer kompilacji głównej dla tej definicji języka specyficznego dla domeny.|1|
|Wersja pośrednia|Przyrostowy numer kompilacji dla tej definicji języka specyficznego dla domeny.|0|
|Przegląd|Numer kompilacji poprawki przyrostowej dla tej definicji języka specyficznego dla domeny.|0|

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
