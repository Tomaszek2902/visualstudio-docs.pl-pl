---
title: 'CA2201: nie zgłaszaj typów wyjątków zarezerwowanych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9533a597a33deaed17ff2a73d56ef306ea7b5613
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546344"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Nie zgłaszaj wyjątków o zastrzeżonych typach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda podnosi typ wyjątku, który jest zbyt ogólny lub jest zarezerwowany przez środowisko uruchomieniowe.

## <a name="rule-description"></a>Opis reguły
 Następujące typy wyjątków są zbyt ogólne, aby zapewnić użytkownikowi wystarczające informacje:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  Następujące typy wyjątków są zarezerwowane i powinny być zgłaszane tylko przez środowisko uruchomieniowe języka wspólnego:

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **Nie Generuj ogólnych wyjątków**

  W przypadku zgłaszania ogólnego typu wyjątku, takiego jak <xref:System.Exception> lub <xref:System.SystemException> w bibliotece lub strukturze, wymusza ona konsumentom przechwycenie wszystkich wyjątków, w tym nieznanych wyjątków, które nie wiedzą, jak obsłużyć.

  Zamiast tego należy zgłosić bardziej pochodny typ, który już istnieje w strukturze, lub utworzyć własny typ, który pochodzi od <xref:System.Exception> .

  **Zgłoś określone wyjątki**

  W poniższej tabeli przedstawiono parametry i wyjątki, które należy zgłosić podczas walidacji parametru, łącznie z parametrem value w metodzie dostępu zestawu właściwości:

|Opis parametru|Wyjątek|
|---------------------------|---------------|
|`null` odwoła|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Poza dozwolonym zakresem wartości (takich jak indeks kolekcji lub listy)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Nieprawidłowa `enum` wartość|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Zawiera format, który nie spełnia specyfikacji parametrów metody (na przykład ciąg formatu dla `ToString(String)` )|<xref:System.FormatException?displayProperty=fullName>|
|W przeciwnym razie nieprawidłowe|<xref:System.ArgumentException?displayProperty=fullName>|

 Gdy operacja jest nieprawidłowa dla bieżącego stanu rzutowania obiektu <xref:System.InvalidOperationException?displayProperty=fullName>

 Gdy operacja jest wykonywana na obiekcie, który został usunięty, zgłoś <xref:System.ObjectDisposedException?displayProperty=fullName>

 Gdy operacja nie jest obsługiwana (na przykład w przesłoniętym **strumieniu** ), zgłoś w strumieniu otwartym do odczytu <xref:System.NotSupportedException?displayProperty=fullName>

 Gdy konwersja spowoduje przepełnienie (na przykład w jawnym przeciążeniu operatora rzutowania) <xref:System.OverflowException?displayProperty=fullName>

 We wszystkich innych sytuacjach należy rozważyć utworzenie własnego typu, który pochodzi z <xref:System.Exception> i throw.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień typ zgłoszonego wyjątku na określony typ, który nie jest jednym z typów zastrzeżonych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1031: Nie przechwytuj typów wyjątków ogólnych](../code-quality/ca1031-do-not-catch-general-exception-types.md)
