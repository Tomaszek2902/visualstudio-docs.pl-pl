---
title: 'CA2134: metody muszą zachować spójność przejrzystości podczas zastępowania metod podstawowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe9a84280b0124eed6bb0cfffae9c1ec2942bddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547722"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta reguła jest wyzwalana, gdy metoda oznaczona przy użyciu <xref:System.Security.SecurityCriticalAttribute> przesłonięć ma metodę, która jest przezroczysta lub oznaczona przy użyciu <xref:System.Security.SecuritySafeCriticalAttribute> . Zasada jest wyzwalana również wtedy, gdy metoda jest przezroczysta lub oznaczona przy użyciu <xref:System.Security.SecuritySafeCriticalAttribute> przesłonięć metody, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> .

 Reguła jest stosowana podczas zastępowania metody wirtualnej lub implementującej interfejs.

## <a name="rule-description"></a>Opis reguły
 Ta zasada jest uruchamiana przy próbie zmiany dostępu zabezpieczeń metody w celu dalszej części łańcucha dziedziczenia. Na przykład, jeśli metoda wirtualna w klasie bazowej jest przezroczysta lub bezpieczna-krytyczna, Klasa pochodna musi zastąpić ją metodą przezroczystą lub bezpieczną o krytycznym znaczeniu. Z drugiej strony, Jeśli wirtualna ma krytyczne zabezpieczenia, Klasa pochodna musi zastąpić ją metodą krytyczną zabezpieczeń. Ta sama reguła ma zastosowanie do implementowania metod interfejsu.

 Reguły przezroczystości są wymuszane, gdy kod jest kompilowany w trybie JIT zamiast w środowisku uruchomieniowym, dzięki czemu Obliczanie przezroczystości nie ma informacji o typie dynamicznym. W związku z tym wynik obliczeń przezroczystości musi być możliwy do ustalenia wyłącznie z typów statycznych, które są kompilowane JIT, niezależnie od typu dynamicznego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zmień przezroczystość metody zastępującej metodę wirtualną lub implementując interfejs, aby dopasować przezroczystość metody wirtualnej lub interfejsu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń z tej reguły. Naruszenia tej reguły spowodują powstanie środowiska uruchomieniowego <xref:System.TypeLoadException> dla zestawów, które używają przejrzystości poziomu 2.

## <a name="examples"></a>Przykłady

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
