---
title: 'CA2222: Nie obniżaj dziedziczonej widoczności składowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e566750d5a1cdd5f2671e47c71de57ab479cc0dd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680053"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Nie zmniejszaj widoczności dziedziczonego elementu członkowskiego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2222: nie obniżaj dziedziczonej widoczności składowych](https://docs.microsoft.com/visualstudio/code-quality/ca2222-do-not-decrease-inherited-member-visibility).  
  
Element TypeName | DoNotDecreaseInheritedMemberVisibility |  
| CheckId | CA2222 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 Prywatną metodę w niezamknięty typ ma podpis, który jest identyczny z publiczną metodę zadeklarowane w typie podstawowym. Metoda prywatna nie jest ostateczny.  
  
## <a name="rule-description"></a>Opis reguły  
 Nie należy zmieniać modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej. Jeśli element członkowski składa się prywatny i typ jest niezapieczętowany, typy dziedziczące wywołać ostatniego publicznych implementacji metody w hierarchii dziedziczenia. Jeśli musisz zmienić modyfikator dostępu, metoda powinna być oznaczona jako ostatecznego lub jego typ powinny być zapieczętowane tak, aby zapobiec zastąpieniu metody.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy zmienić dostęp jako nieprywatny. Alternatywnie Jeśli język programowania obsługuje tę funkcję, można wprowadzić metody końcowego.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje typ, który narusza tę regułę.  
  
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]


