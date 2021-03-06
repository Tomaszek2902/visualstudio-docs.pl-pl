---
title: 'Instrukcje: Tworzenie typów za pomocą Projektant klas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f87e3a3adda270f6b78b9134c7535bda6c73d952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533149"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Porady: tworzenie typów za pomocą Projektanta klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zaprojektować nowe typy dla projektów Visual C# .NET i Visual Basic .NET, utwórz je na diagramie klas. Aby wyświetlić istniejące typy, zobacz [How to: View Existing Types (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md).

- [Utwórz nowy typ](#CreateType)

- [Zastosuj atrybut niestandardowy do typu](#CustAttributeType)

- [Zastosuj atrybut niestandardowy do elementu członkowskiego typu](#CustAttributeMember)

## <a name="create-a-new-type"></a><a name="CreateType"></a> Utwórz nowy typ

1. W przyborniku, w obszarze Projektanta klas przeciągnij jeden z nich do diagramu klasy:

    - **Klasa** lub **Klasa abstrakcyjna**

    - **Wyliczenie**

    - **Interfejs**

    - **Structure** (VB) lub **Struktura** (C#)

    - **Delegat**

    - **Moduł** (tylko w języku VB)

2. Nadaj nazwę typowi. Następnie wybierz jego poziom dostępu.

3. Wybierz plik, do którego chcesz dodać kod początkowy dla typu:

    - Aby utworzyć nowy plik i dodać go do bieżącego projektu, wybierz opcję **Utwórz nowy plik** i Nazwij plik.

    - Aby dodać kod do istniejącego pliku, wybierz pozycję **Dodaj do istniejącego pliku**.

         Jeśli rozwiązanie ma projekt, który współużytkuje kod w wielu aplikacjach, można dodać nowy typ do diagramu klasy w projekcie aplikacji, ale tylko wtedy, gdy odpowiedni plik klasy znajduje się w tym samym projekcie aplikacji lub znajduje się w projekcie udostępnionym.

4. Teraz dodaj inne elementy, aby zdefiniować typ:

    |**Dla**|**Dodaj**|
    |-|-|
    |Klasy, klasy abstrakcyjne, struktury i obiekty struct|Metody, właściwości, pola, zdarzenia, konstruktory (metoda), destruktory (metoda) i stałe, które określają typ|
    |Wyliczenia|Wartości pól, które tworzą wyliczenie|
    |Interfejsy|Metody, właściwości i zdarzenia, które tworzą interfejs|
    |Delegat|Parametry, które definiują obiekt delegowany|
    |Moduł|Metody, właściwości, pola, zdarzenia, konstruktory (metoda) i stałe, które określają moduł|

     Zobacz [Tworzenie elementów członkowskich](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Zastosuj atrybut niestandardowy do typu

1. Kliknij typ kształtu na diagramie klasy.

2. W okno Właściwości obok właściwości **atrybuty niestandardowe** typu kliknij przycisk wielokropka (...).

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

     Kiedy skończysz, atrybuty niestandardowe są stosowane do typu.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Zastosuj atrybut niestandardowy do elementu członkowskiego typu

1. Kliknij nazwę składowej w jej kształcie typu na diagramie klasy lub kliknij jej wiersz w oknie Szczegóły klasy.

2. W okno Właściwości Znajdź właściwość **atrybuty niestandardowe** elementu członkowskiego.

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

     Kiedy skończysz, atrybuty niestandardowe są stosowane do typu.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md) [instrukcje: tworzenie skojarzeń między typami (Projektant klas)](../ide/how-to-create-associations-between-types-class-designer.md) [Tworzenie i konfigurowanie elementów członkowskich typu (Projektant klas)](../ide/creating-and-configuring-type-members-class-designer.md) [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md) [projektowanie klas i typów (Projektant klas)](../ide/designing-classes-and-types-class-designer.md)
