---
title: 'CA1414: Oznacz argumenty logiczne P-Invoke za pomocą elementu MarshalAs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 783f7fad05cad18efea2f83b6d76c4c9e644f119
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548385"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Oznacz logiczne argumenty P/Invoke za pomocą MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Deklaracja metody wywołania platformy zawiera <xref:System.Boolean?displayProperty=fullName> parametr lub wartość zwracaną, ale <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atrybut nie jest stosowany do parametru lub wartości zwracanej.

## <a name="rule-description"></a>Opis reguły
 Metoda Invoke platformy uzyskuje dostęp do kodu niezarządzanego i jest definiowana za pomocą `Declare` słowa kluczowego w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . <xref:System.Runtime.InteropServices.MarshalAsAttribute> Określa zachowanie organizowania, które służy do konwertowania typów danych między zarządzanym i niezarządzanym kodem. Wiele prostych typów danych, takich jak <xref:System.Byte?displayProperty=fullName> i <xref:System.Int32?displayProperty=fullName> , mają pojedynczą reprezentację w kodzie niezarządzanym i nie wymaga specyfikacji ich zachowania Marshaling. środowisko uruchomieniowe języka wspólnego automatycznie dostarcza poprawne zachowanie.

 <xref:System.Boolean>Typ danych ma wiele reprezentacji w kodzie niezarządzanym. Gdy <xref:System.Runtime.InteropServices.MarshalAsAttribute> nie jest określony, domyślnym zachowaniem organizowania dla tego <xref:System.Boolean> typu danych jest <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . Jest to 32-bitowa liczba całkowita, która nie jest odpowiednia w żadnym przypadku. Reprezentacja logiczna wymagana przez metodę niezarządzaną powinna być określona i zgodna z odpowiednią <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . UnmanagedType. bool jest typem BOOL Win32, który ma zawsze 4 bajty. Nie można używać elementu UnmanagedType. U1 dla języków C++ `bool` i innych typów 1-bajtowych. Aby uzyskać więcej informacji, zobacz [domyślne kierowanie dla typów logicznych](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> do <xref:System.Boolean> parametru lub wartości zwracanej. Ustaw wartość atrybutu na odpowiednią <xref:System.Runtime.InteropServices.UnmanagedType> .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet jeśli domyślne zachowanie kierowania jest odpowiednie, kod jest łatwiejszy do utrzymania, gdy zachowanie jest jawnie określone.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje dwie metody wywołania platformy, które są oznaczone odpowiednimi <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutami.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1901: deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Określ kierowanie dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[Kierowanie domyślne dla typów logicznych](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [współpracujących z niezarządzanym kodem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
