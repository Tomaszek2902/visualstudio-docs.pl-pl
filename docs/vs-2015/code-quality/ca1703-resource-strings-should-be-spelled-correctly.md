---
title: 'CA1703: ciągi zasobów powinny mieć poprawną pisownię | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e720c1c491e88b6d89fb4b1f0175e8bc8a56e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544056"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Pisownia ciągów zasobów powinna być poprawna
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.

## <a name="rule-description"></a>Opis reguły
 Ta reguła analizuje ciąg zasobu w słowach (tokenizowanie złożone wyrazy) i sprawdza pisownię każdego wyrazu/tokenu. Aby uzyskać informacje na temat algorytmu analizy, zobacz [CA1704: Identyfikatory powinny być poprawnie napisane](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Domyślnie używana jest wersja angielskojęzyczna (EN) modułu sprawdzania pisowni.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, użyj kompletnych słów, które są poprawnie napisane lub Dodaj wyrazy do słownika niestandardowego. Aby uzyskać informacje o sposobach używania słowników niestandardowych, zobacz [CA1704: Identyfikatory powinny mieć poprawną pisownię](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Prawidłowo napisane wyrazy skracają czas wymagany do nauczenia się nowych bibliotek oprogramowania.

## <a name="related-rules"></a>Powiązane reguły
 [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Pisownia identyfikatorów powinna być poprawna](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Pisownia literałów powinna być poprawna](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
