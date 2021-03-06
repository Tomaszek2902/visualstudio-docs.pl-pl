---
title: 'CA1011: Rozważ przekazanie typów podstawowych jako parametrów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f689dfd6c1d39bbd03d522a33ed8c5639a3da9f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545486"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Rozważ przekazywanie typów podstawowych jako parametrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Deklaracja metody zawiera formalny parametr, który jest typem pochodnym, a metoda wywołuje tylko elementy członkowskie typu podstawowego parametru.

## <a name="rule-description"></a>Opis reguły
 Jeśli typ podstawowy jest określony jako parametr w deklaracji metody, dowolny typ, który pochodzi od typu podstawowego, może zostać przekazany jako odpowiadający argument do metody. Gdy argument jest używany wewnątrz treści metody, określona metoda jest zależna od typu argumentu. Jeśli dodatkowe funkcje dostarczone przez typ pochodny nie są wymagane, użycie typu podstawowego umożliwia szersze użycie metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień typ parametru na jego typ podstawowy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły

- Jeśli metoda wymaga określonej funkcjonalności, która jest dostarczana przez typ pochodny

   \- oraz

- Aby wymusić, że tylko typ pochodny lub bardziej pochodny typ jest przekazanie do metody.

  W takich przypadkach kod będzie bardziej niezawodny ze względu na ścisłe sprawdzanie typu dostarczone przez kompilator i środowisko uruchomieniowe.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, `ManipulateFileStream` , która może być używana tylko z <xref:System.IO.FileStream> obiektem, co narusza tę regułę. Druga metoda, `ManipulateAnyStream` ,, spełnia regułę przez zastąpienie <xref:System.IO.FileStream> parametru za pomocą <xref:System.IO.Stream> .

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1059: Składowe nie powinny ujawniać niektórych typów konkretnych](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
