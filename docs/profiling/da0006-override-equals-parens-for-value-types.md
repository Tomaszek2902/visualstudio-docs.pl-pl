---
title: DA0006 — Przesłoń metodę Equals () dla typów wartości | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ba62555f786b2280de9a07c435a3e32d5cc3e7d9
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659293"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Przesłoń metodę Equals() dla typów wartości

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0006|
|Kategoria|Użycie .NET Framework|
|Metody Profiiling|Próbkowanie|
|Wiadomość|Przesłoń równości i operator równości dla typów wartości.|
|Typ messge|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania metody Equals lub operatory równości typu wartości publicznej są znaczną częścią danych profilowania. Rozważ zaimplementowanie bardziej wydajnej metody.

## <a name="rule-description"></a>Opis reguły
 W przypadku typów wartości dziedziczone implementacje Equals używa <xref:System.Reflection> biblioteki i porównuje zawartość wszystkich pól w typie. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli oczekujesz, że użytkownicy porównują lub sortują wystąpienia lub używają ich jako kluczy tabeli skrótów, typ wartości powinien implementować równą się. Jeśli język programowania obsługuje przeciążanie operatora, należy również podać implementację operatorów równości i nierówności.

 Aby uzyskać więcej informacji o sposobie przesłonięcia równości i operatory równości, zobacz [wytyczne dotyczące implementowania równości i operatora równości (= =)](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Aby zapoznać się z przykładem implementowania operatorów równości i równości, zobacz reguła analizy kodu [CA1815: override Equals i operator Equals dla typów wartości](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)
