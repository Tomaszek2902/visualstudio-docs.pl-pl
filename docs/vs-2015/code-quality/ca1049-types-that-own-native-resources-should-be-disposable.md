---
title: 'CA1049: typy posiadające zasoby natywne powinny być jednorazowe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49c56b98e3be01675c2c21cd11c2961dd75f4877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546812"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ odwołuje się do <xref:System.IntPtr?displayProperty=fullName> pola, <xref:System.UIntPtr?displayProperty=fullName> pola lub <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> pola, ale nie implementuje <xref:System.IDisposable?displayProperty=fullName> .

## <a name="rule-description"></a>Opis reguły
 Ta reguła zakłada <xref:System.IntPtr> , że <xref:System.UIntPtr> pola, i <xref:System.Runtime.InteropServices.HandleRef> przechowują wskaźniki do niezarządzanych zasobów. Typy, które przydzielą zasoby niezarządzane, powinny być implementowane w <xref:System.IDisposable> celu umożliwienia wywołującym wydawania tych zasobów na żądanie i skrócenia okresu istnienia obiektów, które zawierają zasoby.

 Zalecany Wzorzec projektowy w celu oczyszczenia zasobów niezarządzanych polega na dostarczeniu zarówno niejawnego, jak i jawnego środka do zwolnienia tych zasobów przy użyciu <xref:System.Object.Finalize%2A?displayProperty=fullName> metody i <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metody. Moduł zbierający elementy bezużyteczne wywołuje <xref:System.Object.Finalize%2A> metodę obiektu w pewnym nieokreślonym czasie po ustaleniu obiektu, aby nie był już osiągalny. Po <xref:System.Object.Finalize%2A> wywołaniu jest wymagane dodatkowe wyrzucanie elementów bezużytecznych w celu zwolnienia obiektu. <xref:System.IDisposable.Dispose%2A>Metoda umożliwia obiektowi wywołującemu jawne zwolnienie zasobów na żądanie, w przypadku gdy pozostawiono do modułu wyrzucania elementów bezużytecznych. Po oczyszczeniu zasobów niezarządzanych <xref:System.IDisposable.Dispose%2A> należy wywołać <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodę, aby pozwolić modułowi wyrzucania elementów bezużytecznych, który <xref:System.Object.Finalize%2A> nie musi być już wywoływany; eliminuje to konieczność dodatkowego wyrzucania elementów bezużytecznych i skraca okres istnienia obiektu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj <xref:System.IDisposable> .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli typ nie odwołuje się do niezarządzanego zasobu, można bezpiecznie pominąć ostrzeżenie z tej reguły. W przeciwnym razie nie pomijaj ostrzeżenia z tej reguły, ponieważ niepowodzenie implementacji <xref:System.IDisposable> może spowodować, że niezarządzane zasoby staną się niedostępne lub nieużywane.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ, który implementuje <xref:System.IDisposable> czyszczenie niezarządzanego zasobu.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Zobacz też
  [Wzorzec Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
