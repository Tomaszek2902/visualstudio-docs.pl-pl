---
title: 'CA2119: metody plomby, które spełniają interfejsy prywatne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0afa6950a6ad876cdcfdcc1a56dd143422b9d44f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544355"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Dziedziczony typ publiczny zapewnia implementację metody `internal` `Friend` w interfejsie (w Visual Basic).

## <a name="rule-description"></a>Opis reguły
 Metody interfejsu mają publiczny dostęp, którego nie można zmienić przez typ implementujący. Wewnętrzny interfejs tworzy kontrakt, który nie jest przeznaczony do wdrożenia poza zestawem, który definiuje interfejs. Typ publiczny implementujący metodę interfejsu wewnętrznego przy użyciu `virtual` `Overridable` modyfikatora (w Visual Basic) umożliwia przesłanianie metody przez typ pochodny, który znajduje się poza zestawem. Jeśli drugi typ w definicji zestawu wywołuje metodę i oczekuje kontraktu tylko wewnętrznego, zachowanie może zostać naruszone, gdy zamiast tego zostanie wykonana zastąpiona metoda w zewnętrznym zestawie. Powoduje to utworzenie luki w zabezpieczeniach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zapobiec zastąpieniu metody poza zestaw przy użyciu jednego z następujących elementów:

- Oznacz typ deklarujący `sealed` ( `NotInheritable` w Visual Basic).

- Zmień dostępność typu deklarującego na `internal` ( `Friend` w Visual Basic).

- Usuń wszystkie konstruktory publiczne z typu deklarującego.

- Zaimplementuj metodę bez użycia `virtual` modyfikatora.

- Zaimplementuj metodę jawnie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli po dokładnym przejrzeniu Metoda zostanie przesłonięta poza zestawem, bezpieczniej jest pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ, `BaseImplementation` który narusza tę regułę.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie wykorzystuje implementację metody wirtualnej z poprzedniego przykładu.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Interfejsy](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b) interfejsów
