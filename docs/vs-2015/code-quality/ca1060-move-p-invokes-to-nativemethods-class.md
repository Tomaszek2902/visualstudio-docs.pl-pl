---
title: 'CA1060: Przenieś P-Invoke do klasy NativeMethods | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e01ad9fc4fc57917c123404d8863d04240585793
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533435"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Przenieś P/Invokes do klasy NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda używa usług wywołania platformy w celu uzyskania dostępu do kodu niezarządzanego i nie jest elementem członkowskim jednej z klas **NativeMethods** .

## <a name="rule-description"></a>Opis reguły
 Metody wywołania platformy, takie jak te, które są oznaczone przy użyciu <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu lub metod, które są zdefiniowane za pomocą `Declare` słowa kluczowego w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , uzyskują dostęp do niezarządzanego kodu. Metody te powinny znajdować się w jednej z następujących klas:

- **NativeMethods** — Ta klasa nie pomija przechodzenia stosu dla niezarządzanego kodu. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> nie może być zastosowany do tej klasy). Ta klasa jest dla metod, które mogą być używane w dowolnym miejscu, ponieważ zostanie wykonane przeszukiwanie stosu.

- **SafeNativeMethods** — Ta klasa pomija przeszukiwania stosu dla niezarządzanego kodu. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest zastosowany do tej klasy). Ta klasa jest dla metod, które są bezpieczne dla każdego do wywołania. Osoby wywołujące te metody nie są wymagane do przeprowadzenia pełnego przeglądu zabezpieczeń, aby upewnić się, że użycie jest bezpieczne, ponieważ metody są nieszkodliwe dla każdego obiektu wywołującego.

- **UnsafeNativeMethods** — Ta klasa pomija przeszukiwania stosu dla niezarządzanego kodu. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest zastosowany do tej klasy). Ta klasa jest dla metod, które są potencjalnie niebezpieczne. Każdy obiekt wywołujący te metody musi wykonać pełny przegląd zabezpieczeń, aby upewnić się, że użycie jest bezpieczne, ponieważ nie zostanie wykonane żadne przeszukiwanie stosu.

  Klasy te są zadeklarowane jako `internal` ( `Friend` , w Visual Basic) i deklarują Konstruktor prywatny, aby zapobiec tworzeniu nowych wystąpień. Metody w tych klasach powinny mieć wartość `static` i `internal` ( `Shared` i `Friend` w Visual Basic).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Przenieś metodę do odpowiedniej klasy **NativeMethods** . W przypadku większości aplikacji przeniesienie P/Invoke do nowej klasy o nazwie **NativeMethods** jest wystarczające.

 Jeśli jednak tworzysz biblioteki do użycia w innych aplikacjach, należy rozważyć zdefiniowanie dwóch innych klas o nazwie **SafeNativeMethods** i **UnsafeNativeMethods**. Klasy te przypominają klasę **NativeMethods** ; są one jednak oznaczone przy użyciu specjalnego atrybutu o nazwie **SuppressUnmanagedCodeSecurityAttribute**. Gdy ten atrybut jest stosowany, środowisko uruchomieniowe nie wykonuje pełnego sprawdzenia stosu, aby upewnić się, że wszyscy wywołujący mają uprawnienie **UnmanagedCode** . Środowisko uruchomieniowe zwykle sprawdza dla tego uprawnienia podczas uruchamiania. Ponieważ sprawdzenie nie jest wykonywane, może znacznie poprawić wydajność wywołań tych metod niezarządzanych, a także kod, który ma ograniczone uprawnienia do wywoływania tych metod.

 Tego atrybutu należy jednak używać bardzo ostrożnie. Jeśli jest zaimplementowany nieprawidłowo, może to mieć poważne konsekwencje dla bezpieczeństwa.

 Aby uzyskać informacje na temat sposobu implementacji metod, zobacz przykład **NativeMethods** , **SafeNativeMethods** example i **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład deklaruje metodę, która narusza tę regułę. Aby poprawić naruszenie, **RemoveDirectory** p/Invoke należy przenieść do odpowiedniej klasy, która jest przeznaczona do przechowywania tylko P/Invoke.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Przykład NativeMethods

### <a name="description"></a>Opis
 Ponieważ Klasa **NativeMethods** nie powinna być oznaczona przy użyciu **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke, które są umieszczane, będzie wymagały uprawnienia **UnmanagedCode** . Ponieważ większość aplikacji jest uruchamiana z komputera lokalnego i działa z pełnym zaufaniem, zazwyczaj nie jest to problem. Jeśli jednak tworzysz biblioteki wielokrotnego użytku, należy rozważyć zdefiniowanie klasy **SafeNativeMethods** lub **UnsafeNativeMethods** .

 Poniższy przykład przedstawia sposób **interakcji. dźwięk** , który otacza funkcję **MessageBeep** z user32.dll. **MessageBeep** P/Invoke jest umieszczana w klasie **NativeMethods** .

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Przykład SafeNativeMethods

### <a name="description"></a>Opis
 Metody P/Invoke, które mogą być bezpiecznie uwidocznione dla dowolnej aplikacji i które nie mają żadnych efektów ubocznych, powinny być umieszczane w klasie o nazwie **SafeNativeMethods**. Nie musisz zażądać uprawnień i nie musisz zwracać uwagi do lokalizacji, z której są wywoływane.

 W poniższym przykładzie przedstawiono Właściwość **Environment.** nieruchomości, która zawija funkcję **GetTickCount** z kernel32.dll.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Przykład UnsafeNativeMethods

### <a name="description"></a>Opis
 Metody P/Invoke, które nie mogą być bezpiecznie wywoływane i mogą spowodować, że efekty uboczne powinny zostać umieszczone w klasie o nazwie **UnsafeNativeMethods**. Metody te powinny być ściśle sprawdzone, aby upewnić się, że nie są narażone na użytkownika przypadkowo. Reguła [CA2118: przegląd użycia SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) może Ci pomóc. Alternatywnie metody powinny mieć inne uprawnienia, które są żądane, zamiast **UnmanagedCode** , gdy ich używają.

 Poniższy przykład przedstawia **kursor. Ukryj** metodę, która zawija funkcję **ShowCursor** z user32.dll.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia projektu](../code-quality/design-warnings.md)
