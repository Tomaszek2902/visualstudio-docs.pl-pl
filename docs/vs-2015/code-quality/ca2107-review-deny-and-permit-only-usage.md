---
title: 'CA2107: Przejrzyj użycie akcji deny i zezwolić na użycie tylko | Dokumentacja firmy Microsoft'
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
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ae13dab744841023b1e1b9723604e6a22c67c745
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681274"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Przejrzyj użycie akcji Deny i Permit Only
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2107: Przejrzyj użycie akcji deny i zezwolić na użycie tylko](https://docs.microsoft.com/visualstudio/code-quality/ca2107-review-deny-and-permit-only-usage).  
  
Element TypeName | ReviewDenyAndPermitOnlyUsage |  
| CheckId | CA2107 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Metoda zawiera sprawdzanie zabezpieczeń, które określa akcji zabezpieczeń PermitOnly lub Odmów.  
  
## <a name="rule-description"></a>Opis reguły  
 [Korzystanie z metody PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649) i <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> akcje zabezpieczeń powinny być używane tylko przez tych, którzy mają zaawansowaną wiedzę o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zabezpieczeń. Kod, który używa tych akcji zabezpieczeń, należy poddać przeglądowi zabezpieczeń.  
  
 Odmów zmienia domyślne zachowanie przeszukiwania stosu, który występuje w odpowiedzi na żądania zabezpieczeń. Dzięki temu można określić uprawnienia, które nie muszą być przyznawane na czas trwania odmowy metody, niezależnie od rzeczywistego uprawnień obiektów wywołujących w stosie wywołań. Jeśli przejście przez stos wykrywa metody, która jest zabezpieczony przez Odmów, a Jeśli żądane uprawnienie jest zawarte w odmówionych uprawnień, przejście przez stos nie powiedzie się. PermitOnly również zmienia domyślne zachowanie przeszukiwania stosu. Umożliwia ona kod, aby określić te uprawnienia, które mogą być udzielane, niezależnie od uprawnień obiektom wywołującym. Jeśli przejście przez stos wykrywa metody, która jest zabezpieczony przez PermitOnly i żądane uprawnienie nie jest uwzględniony w uprawnieniach, które są określone przez PermitOnly, przejście przez stos nie powiedzie się.  
  
 Kod, który opiera się na te akcje należy dokładnie ocenić dla luki w zabezpieczeniach ze względu na ograniczone użyteczność i zachowanie subtelne. Rozważ następujące opcje:  
  
-   [Link zapotrzebowanie](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) nie dotyczy Deny lub PermitOnly.  
  
-   Jeśli Deny lub PermitOnly występuje w tej samej ramki stosu jako żądanie, która powoduje przejście przez stos, akcje zabezpieczeń nie mają wpływu.  
  
-   Zazwyczaj można określić wartości, które są używane do konstruowania uprawnień opartych na ścieżkę na wiele sposobów. Odmowa dostępu do tego samego formularza ścieżki nie odmowa dostępu do wszystkich formularzy. Na przykład jeśli udział pliku \\\Server\Share jest zamapowany dysk sieciowy X:, aby odmówić dostępu do plików w udziale, należy odmówić \\\Server\Share\File, X:\File i każdej innej ścieżki, który uzyskuje dostęp do pliku.  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Przed osiągnięciem Deny lub PermitOnly może zakończyć przeszukiwania stosu.  
  
-   Jeśli stan odmowa ma żadnego efektu, to znaczy, gdy obiekt wywołujący ma uprawnienie, który jest zablokowany przez Odmów, obiekt wywołujący można dostępu do chronionego zasobu bezpośrednio, pomijanie Odmów. Podobnie jeśli obiekt wywołujący nie ma odmowy uprawnień, przejście przez stos może zakończyć się niepowodzeniem bez Odmów.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Naruszenie zasad spowoduje, że każde użycie tych akcji zabezpieczeń. Aby naprawić naruszenie, nie należy używać tych akcji zabezpieczeń.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomijaj ostrzeżeń dla tej reguły, tylko w przypadku, po zakończeniu przeglądu zabezpieczeń.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kilka ograniczeń Odmów.  
  
 Następująca biblioteka zawiera klasę, która ma dwie metody, które są identyczne, z wyjątkiem wymogów bezpieczeństwa, które je chronić.  
  
 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji przedstawia skutki Odmów zabezpieczonej metod z biblioteki.  
  
 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]  
  
 Ten przykład generuje następujące dane wyjściowe.  
  
 **Żądanie: Odmowa wywołującego nie ma wpływu na żądanie z uprawnieniem potwierdzone.**  
**Żądanie LinkDemand: Odmowa wywołującego nie ma wpływu na żądanie LinkDemand z uprawnieniem potwierdzone.**  
**Żądanie LinkDemand: Odmów wywołującego nie ma znaczenia z kodem chronionej przez żądanie LinkDemand.**  
**Żądanie LinkDemand: Odmów to nie ma wpływu kodem chronionej przez żądanie LinkDemand.**   
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Wytyczne dotyczące bezpiecznego programowania](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)   
 [Zastępowanie sprawdzania zabezpieczeń](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Korzystanie z metody PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)


