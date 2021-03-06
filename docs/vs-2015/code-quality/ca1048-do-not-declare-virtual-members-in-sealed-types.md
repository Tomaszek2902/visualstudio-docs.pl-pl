---
title: 'CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19ae3a4fdc620343f18aa0845c33e1d73529adfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546799"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny jest zapieczętowany i deklaruje metodę, która jest zarówno `virtual` ( `Overridable` w Visual Basic), a nie końcową. Ta reguła nie zgłasza naruszeń dla typów delegatów, które muszą być zgodne z tym wzorcem.

## <a name="rule-description"></a>Opis reguły
 Metody wirtualne są zadeklarowane w typach tak, aby typy dziedziczące mogły zmieniać implementację metod wirtualnych. Według definicji nie można dziedziczyć z typu zapieczętowanego, co oznacza, że metoda wirtualna w typie zapieczętowanym nie ma znaczenia.

 Kompilatory Visual Basic .NET i C# nie zezwalają, aby typy naruszają tę regułę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, ustaw metodę jako niewirtualną lub Zmień typ na dziedziczony.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie tego typu w bieżącym stanie może spowodować problemy z konserwacją i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
