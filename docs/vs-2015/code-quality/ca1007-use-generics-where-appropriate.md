---
title: 'CA1007: Użyj typów ogólnych, jeśli są odpowiednie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4ee33305c1ae0f15e5d8f390a4b65d62c87b6904
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547943"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Używaj typów ogólnych tam, gdzie to odpowiednie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda widoczna na zewnątrz zawiera parametr referencyjny typu <xref:System.Object?displayProperty=fullName> i zawierający elementy docelowe zestawu [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Opis reguły
 Parametr Reference jest parametrem, który jest modyfikowany przy użyciu `ref` `ByRef` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] słowa kluczowego (in). Typ argumentu, który jest dostarczony dla parametru reference musi dokładnie odpowiadać typowi parametru Reference. Aby użyć typu, który jest pochodną typu parametru odwołania, należy najpierw rzutować i przypisać do zmiennej typu parametru odwołania. Użycie metody generycznej pozwala na przekazywanie wszystkich typów, które podlegają ograniczeniom, do metody bez uprzedniego rzutowania typu na typ parametru odwołania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy określić metodę ogólną i zastąpić <xref:System.Object> parametr przy użyciu parametru typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje procedurę wymiany ogólnego przeznaczenia, która jest zaimplementowana jako metody nierodzajowe i rodzajowe. Zwróć uwagę na to, jak efektywnie ciągi są zamieniane przy użyciu metody ogólnej w porównaniu do metody niegenerycznej.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj statycznych składowych na typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie uwidaczniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w podpisach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
