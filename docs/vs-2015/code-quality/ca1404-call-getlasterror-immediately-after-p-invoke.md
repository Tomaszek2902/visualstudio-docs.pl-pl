---
title: 'CA1404: wywołanie metody GetLastError natychmiast po wywołaniu P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 54ac9a4d56136d9e981ae038a0b219aa4cb4774e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544498"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Należy wywołać GetLastError natychmiast po P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Nastąpi wywołanie <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> metody lub równoważnej `GetLastError` funkcji Win32, a wywołanie, które jest bezpośrednio przed nie jest metodą wywołania platformy.

## <a name="rule-description"></a>Opis reguły
 Metoda Invoke platformy uzyskuje dostęp do kodu niezarządzanego i jest definiowana przy użyciu `Declare` słowa kluczowego in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu. Ogólnie rzecz biorąc, w przypadku awarii funkcje niezarządzane wywołują funkcję Win32, `SetLastError` Aby ustawić kod błędu, który jest skojarzony z błędem. Obiekt wywołujący nieudanej funkcji wywołuje funkcję Win32, `GetLastError` Aby pobrać kod błędu i określić przyczynę niepowodzenia. Kod błędu jest obsługiwany dla każdego wątku i jest zastępowany przez następne wywołanie do `SetLastError` . Po wywołaniu metody wywołania niepowodzenia platformy kod zarządzany może pobrać kod błędu przez wywołanie <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> metody. Ponieważ kod błędu może zostać zastąpiony przez wywołania wewnętrzne z innych metod biblioteki zarządzanej klasy, `GetLastError` Metoda or <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> powinna być wywoływana natychmiast po wywołaniu metody wywoływana przez platformę.

 Reguła ignoruje wywołania następujących elementów zarządzanych, gdy występują między wywołaniem metody wywołania platformy i wywołaniem do <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> . Te elementy członkowskie nie zmieniają kodu błędu i są przydatne do określania sukcesu niektórych wywołań metody wywołania.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Przenieś wywołanie do <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> tak, aby natychmiast po wywołaniu metody wywołania platformy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku, gdy kod między wywołaniem metody wywołania metod a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> wywołanie metody nie może jawnie lub niejawnie spowodować zmiany kodu błędu, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje metodę, która narusza regułę i metodę, która spełnia kryteria.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1060: Przenieś P/Invoke do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: punkty wejścia P/Invoke powinny istnieć](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke nie powinna być widoczna](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Określ kierowanie dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Użyj zarządzanych odpowiedników funkcji API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
