---
title: 'CA1400: punkty wejścia P-Invoke powinny istnieć | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548307"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Powinny istnieć punkty wejścia P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona jest oznaczona za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece. Jeśli reguła nie może znaleźć nazwy metody dokładnie tak, jak jest określona, szuka wersji ANSI lub znaków dwubajtowych metody przez sufiks nazwy metody z "A" lub "W". Jeśli nie zostanie znalezione dopasowanie, reguła próbuje zlokalizować funkcję przy użyciu formatu nazwy __stdcall ( _MyMethod@12 gdzie 12 reprezentuje długość argumentów). Jeśli nie zostanie znalezione dopasowanie, a nazwa metody rozpoczyna się od "#", reguła wyszukuje funkcję jako odwołanie porządkowe, a nie odwołanie do nazwy.

## <a name="rule-description"></a>Opis reguły
 Nie jest dostępny żaden test czasu kompilacji, aby upewnić się, że metody oznaczone za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> znajdują się w odwołującej się do niezarządzanej bibliotece DLL. Jeśli żadna funkcja, która ma określoną nazwę nie znajduje się w bibliotece lub argumenty metody nie są zgodne z argumentami funkcji, środowisko uruchomieniowe języka wspólnego zgłasza wyjątek.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy skorygować metodę, która ma <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut. Upewnij się, że biblioteka niezarządzana istnieje i znajduje się w tym samym katalogu, w którym znajduje się zestaw zawierający metodę. Jeśli biblioteka jest obecna i poprawnie przywoływana, sprawdź, czy nazwa metody, zwracany typ i sygnatura argumentu są zgodne z funkcją biblioteki.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, jeśli biblioteka niezarządzana znajduje się w tym samym katalogu, co zarządzany zestaw, który odwołuje się do niego. W przypadku, gdy nie można zlokalizować biblioteki niezarządzanej, może być bezpieczne pominięcie ostrzeżenia z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę. W kernel32.dll nie ma żadnej funkcji o nazwie `DoSomethingUnmanaged` .

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
