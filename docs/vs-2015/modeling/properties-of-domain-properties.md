---
title: Właściwości właściwości domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cdba41913273b9db574afd87f5542df0fb597ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671482"
---
# <a name="properties-of-domain-properties"></a>Właściwości właściwości domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Właściwość domeny* jest funkcją elementu modelu, która może zawierać wartość. Na przykład `Person` Klasa domeny może mieć właściwości `Name` i `BirthDate` . W definicji DSL właściwości domeny są wyświetlane w polu Klasa domeny na diagramie i w obszarze klasy domeny w Eksploratorze DSL. Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> Słowo "Property" ma dwa zastosowania. *Właściwość domeny* to funkcja zdefiniowana w klasie domeny. Z kolei wiele elementów DSL ma *Właściwości*, które są wyświetlane w oknie **Właściwości** w definicji DSL. Na przykład Każda właściwość domeny ma zestaw właściwości, które są opisane w tym temacie.

 W czasie wykonywania, gdy użytkownik tworzy wystąpienia klasy domeny, wartości właściwości domeny mogą być widoczne w okno Właściwości i mogą być wyświetlane na kształtach.

 Większość właściwości domeny jest implementowana jako zwykłe właściwości środowiska CLR. Jednak z punktu widzenia programowania właściwości domeny mają bogatsze funkcje niż zwykłe właściwości programu:

- Można zdefiniować reguły i zdarzenia, które monitorują stan właściwości. Aby uzyskać więcej informacji, zobacz [reagowanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

- Transakcje uniemożliwiają niespójne Stany. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Po wybraniu właściwości domeny w diagramie lub w Eksploratorze DSL można zobaczyć następujące elementy w okno Właściwości. Aby uzyskać więcej informacji na temat sposobu korzystania z tych elementów, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Wartość domyślna|
|--------------|-----------------|-------------------|
|**Opis**|Opis używany do dokumentowania interfejsu użytkownika (UI) wygenerowanego projektanta.|\<none>|
|**Nazwa wyświetlana**|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej właściwości domeny. Może zawierać spacje i znaki interpunkcyjne, na przykład "tytuł utworu".|\<none>|
|**Dostawca nazw elementów**|Ma to zastosowanie tylko wtedy, gdy ustawiono `Is Element Name` `true` . Można napisać kod, który zawiera nazwę nowego elementu klasy domeny, zastępując zachowanie domyślne.<br /><br /> W pliku kodu w projekcie DSL Utwórz klasę, która pochodzi od <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> .<br /><br /> Następnie w Eksploratorze DSL kliknij prawym przyciskiem myszy katalog główny DSL, a następnie kliknij polecenie Dodaj typ zewnętrzny. Wprowadź nazwę klasy.<br /><br /> Ponownie wybierz tę właściwość domeny i wybierz nazwę klasy z listy rozwijanej.|\<none>|
|**Modyfikator dostępu metody pobierającej**|Poziom dostępu do klasy domeny ( `public` lub `internal` ). Określa zakres, w którym kod programu może uzyskać dostęp do właściwości.|`public`|
|**Słowo kluczowe pomocy**|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tej właściwości domeny.|\<none>|
|**Jest umożliwia przeglądania**|Jeśli `True` Właściwość domena jest wyświetlana użytkownikowi w oknie właściwości, gdy modele tego typu DSL są otwarte.<br /><br /> Jeśli `False` Właściwość domena jest ukryta w interfejsie użytkownika.<br /><br /> Jeśli chcesz, aby właściwość domeny była widoczna, ale tylko do odczytu, ustaw opcję **jest tylko do odczytu interfejsu użytkownika**.|`True`|
|**Jest nazwą elementu**|Jeśli `True` Ta właściwość domeny będzie wyświetlana jako nazwa elementu modelu w EKSPLORATORZE DSL.<br /><br /> Nowy element modelu otrzyma unikatową wartość domyślną dla tej właściwości. Jeśli chcesz kontrolować sposób generowania tych wartości, ustaw opcję **dostawca nazw elementów**.|`False`|
|**Jest tylko do odczytu interfejsu użytkownika**|Jeśli `True` nie można zmienić wartości właściwości domeny przy użyciu interfejsu użytkownika. Nadal może być ustawiony przez programy i będzie widoczny w okno Właściwości.<br /><br /> Jeśli chcesz ukryć właściwość domeny od użytkownika, ustaw wartość **umożliwia przeglądania**. Jeśli chcesz kontrolować dostęp przez programy, ustaw **modyfikator dostępu do metody ustawiającej**.|`False`|
|**Rodzaj**|Rodzaj właściwości domeny ( `Normal` , `Calculated` lub `CustomStorage` ). Aby uzyskać więcej informacji, zobacz [właściwości magazynu obliczeniowego i niestandardowego](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Nazwa**|Nazwa tej właściwości domeny. Musi być prawidłowym identyfikatorem, na przykład **SongTitle**.|\<none>|
|**Uwagi**|Nieformalne uwagi, które są skojarzone z tą właściwością domeny.|\<none>|
|**Modyfikator dostępu metody ustawiającej**|Modyfikator dostępu dla metody ustawiającej. Określa zakres, w którym kod programu może ustawić właściwość.|`public`|
|**Typ**|Typ właściwości. Aby dodać do listy dostępnych typów, kliknij prawym przyciskiem myszy katalog główny DSL w Eksploratorze DSL, a następnie kliknij polecenie **Dodaj typ zewnętrzny**.|`String`|

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
