---
title: 'CA2207: zainicjuj pola statyczne typu wartości w tekście | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792fe18a4f472d0b8a4fd62c652f2ae34fcf6864
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546305"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Pola statyczne typu wartości inicjuj bezpośrednio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ wartości deklaruje jawny Konstruktor statyczny.

## <a name="rule-description"></a>Opis reguły
 Gdy typ wartości jest zadeklarowany, jest to domyślne inicjowanie, gdzie wszystkie pola typu wartości są ustawione na zero, a wszystkie pola typu odwołania są ustawione na `null` ( `Nothing` w Visual Basic). Jawny Konstruktor statyczny gwarantuje tylko uruchomienie przed wywołaniem konstruktora wystąpienia lub statycznego elementu członkowskiego typu. W związku z tym, jeśli typ jest tworzony bez wywoływania konstruktora wystąpienia, Konstruktor statyczny nie jest gwarantowany do uruchomienia.

 Jeśli wszystkie dane statyczne są inicjowane wewnętrznie i nie zadeklarowano jawnego konstruktora statycznego, kompilatory C# i Visual Basic dodają `beforefieldinit` flagę do definicji klasy MSIL. Kompilatory dodają również prywatny statyczny Konstruktor zawierający kod inicjalizacji statycznej. Ten prywatny statyczny Konstruktor jest gwarantowany do uruchomienia przed uzyskaniem dostępu do dowolnych pól statycznych typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zainicjuj wszystkie dane statyczne, gdy jest zadeklarowana, i Usuń Konstruktor statyczny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
