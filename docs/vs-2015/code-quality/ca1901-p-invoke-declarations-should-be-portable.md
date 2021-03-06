---
title: 'CA1901: deklaracje P-Invoke powinny być przenośne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e669d87ad5ecc53c1523db16ab77578c6a703a33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545265"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklaracje P/Invoke powinny być przenośne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Kategoria|Microsoft. przenośność|
|Zmiana kluczowa|Przerywanie — jeśli P/Invoke jest widoczny poza zestawem. Bez przerywania — jeśli P/Invoke nie jest widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
 Ta reguła służy do obliczania rozmiaru każdego parametru oraz wartości zwracanej P/Invoke i sprawdza, czy ich rozmiar w przypadku przekierowania do kodu niezarządzanego na 32-bitowych i 64-bitowych platformach jest poprawny. Najbardziej typowym naruszeniem tej reguły jest przekazanie liczby całkowitej o stałym rozmiarze, gdy wymagana jest zmienna o rozmiarze wskaźnika zależnym od platformy.

## <a name="rule-description"></a>Opis reguły
 Jeden z następujących scenariuszy narusza tę regułę:

- Wartość zwracana lub parametr są wpisywane jako liczba całkowita o stałym rozmiarze, gdy powinna być wpisana jako `IntPtr` .

- Wartość zwracana lub parametr są wpisywane jako typ, który `IntPtr` powinien być typem w postaci liczby całkowitej o stałym rozmiarze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Możesz naprawić to naruszenie, używając `IntPtr` lub `UIntPtr` do reprezentowania dojść zamiast `Int32` lub `UInt32` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie należy pomijać tego ostrzeżenia.

## <a name="example"></a>Przykład
 Poniższy przykład demonstruje naruszenie tej reguły.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 W tym przykładzie `nIconIndex` parametr jest zadeklarowany jako `IntPtr` , który ma 4 bajty na platformie 32-bitowej i 8 bajtów na platformie 64-bitowej. W następującej deklaracji niezarządzanej można zobaczyć, że `nIconIndex` jest to 4-bajtowa liczba całkowita bez znaku na wszystkich platformach.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Przykład
 Aby naprawić naruszenie, zmień deklarację na następujący:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)
