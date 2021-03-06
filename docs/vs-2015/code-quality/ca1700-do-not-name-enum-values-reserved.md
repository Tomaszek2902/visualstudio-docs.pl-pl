---
title: 'CA1700: nie należy określać wartości wyliczeniowych &#39;zastrzeżony&#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57f2a2e5959860a99a921101ff5782f9bce9ace3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545655"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: nie należy określać wartości wyliczeniowych &#39;zastrzeżonych&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa elementu członkowskiego wyliczenia zawiera słowo "zarezerwowane".

## <a name="rule-description"></a>Opis reguły
 Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą. Nie powinno się oczekiwać, że użytkownicy ignorują element członkowski tylko dlatego, że jego nazwa zawiera "zastrzeżone", ani nie może polegać na przeczytaniu lub zapoznaniu się z dokumentacją. Ponadto ze względu na to, że zastrzeżone elementy członkowskie pojawiają się w przeglądarkach obiektów i inteligentnych zintegrowanych środowiskach programistycznych, mogą one spowodować pomyłkę, w której są faktycznie używane.

 Zamiast używać zastrzeżonego elementu członkowskiego, Dodaj nowy element członkowski do wyliczenia w przyszłej wersji. W większości przypadków dodanie nowego elementu członkowskiego nie jest istotną zmianą, o ile dodanie nie spowoduje zmiany wartości oryginalnych elementów członkowskich.

 W ograniczonej liczbie przypadków dodanie elementu członkowskiego jest istotną zmianą nawet wtedy, gdy pierwotne elementy członkowskie zachowują swoje oryginalne wartości. Przede wszystkim nie można zwrócić nowego elementu członkowskiego z istniejących ścieżek kodu bez przerywania wywołujących używających `switch` `Select` instrukcji (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) na zwracanej wartości, która obejmuje całą listę elementów członkowskich i która zgłasza wyjątek w domyślnym przypadku. Dodatkowy problem polega na tym, że kod klienta nie może obsłużyć zmiany zachowania z metod odbicia, takich jak <xref:System.Enum.IsDefined%2A?displayProperty=fullName> . W związku z tym, jeśli nowy element członkowski ma zostać zwrócony z istniejących metod lub znana niezgodność aplikacji jest spowodowana przez słabe użycie odbicia, jedynym rozwiązaniem do Nieprzerwania jest:

1. Dodaj nowe Wyliczenie zawierające pierwotnych i nowych członków.

2. Oznacz oryginalne Wyliczenie <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutem.

   Postępuj zgodnie z tą samą procedurą dla dowolnego widocznego na zewnątrz typów lub elementów członkowskich, które uwidaczniają oryginalne Wyliczenie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń element członkowski lub zmień jego nazwę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły dla elementu członkowskiego, który jest aktualnie używany lub dla bibliotek, które zostały wcześniej wysłane.

## <a name="related-rules"></a>Powiązane reguły
 [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Typy wyliczeniowe powinny mieć wartość zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
