---
title: 'CA1719: nazwy parametrów nie powinny być zgodne z nazwami składowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545369"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Nazwy parametrów nie powinny być zgodne z nazwami składowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa elementu członkowskiego widocznego na zewnątrz, w porównaniu z uwzględnieniem wielkości liter, nazwa jednego z jego parametrów.

## <a name="rule-description"></a>Opis reguły
 Nazwa parametru powinna przekazywać znaczenie parametru, a nazwa elementu członkowskiego — znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę parametru, która nie jest zgodna z nazwą elementu członkowskiego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku nowych rozwiązań nie występują żadne znane scenariusze, w których należy pominąć ostrzeżenie z tej reguły. W przypadku bibliotek wysyłkowych może być konieczne pominięcie ostrzeżenia z tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identyfikatory nie powinny zawierać znaków podkreślenia](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
