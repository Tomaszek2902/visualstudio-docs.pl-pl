---
title: 'CA2144: kod przezroczysty nie powinien ładować zestawów z tablic bajtowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 91a846d0f347916a22df54eb1f1a042bc686d132
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546422"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta ładuje zestaw z tablicy bajtowej przy użyciu jednej z następujących metod:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Opis reguły
 Przegląd zabezpieczeń dla kodu przezroczystego nie jest tak dokładny jak kodu krytycznego pod względem bezpieczeństwa, ponieważ przezroczysty kod nie może wykonywać czynności wrażliwych pod względem bezpieczeństwa. Zestawy, ładowane z tablicy bajtowej, mogą nie być niezauważone w przezroczystym kodzie, a ta tablica bajtów może zawierać krytyczny albo, co ważniejsze, krytyczny dla bezpieczeństwa kod, który powinien być poddany inspekcji. W związku z tym przezroczysty kod nie powinien ładować zestawów z tablicy bajtowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, oznacz metodę, która ładuje zestaw z <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybut.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Reguła jest uruchamiana na poniższym kodzie, ponieważ metoda przezroczysta ładuje zestaw z tablicy bajtowej.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2144.transparentmethodsshouldnotloadassembliesfrombytearrays/cs/ca2144 - transparentmethodsshouldnotloadassembliesfrombytearrays.cs#1)]
