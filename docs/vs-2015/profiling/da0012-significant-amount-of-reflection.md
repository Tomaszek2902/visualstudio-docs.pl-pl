---
title: 'DA0012: znaczna ilość odbicia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54626c07fb8d15f585e800f03911dd465395d795
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850260"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Znaczne odbicie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0012 |  
| Kategoria |. Użycie platformy NET Framework |  
| Metody profilowania | Próbkowanie |  
| Komunikat | Może być używane nadmierne odbicie. Jest to kosztowna operacja. |  
| Typ reguły | Ostrzeżenie |  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metody System. odbicia, takie jak InvokeMember i GetMember albo metody Type, takie jak MemberInvoke, są znaczną częścią danych profilowania. Jeśli to możliwe, rozważ zastąpienie tych metod wczesnym wiązaniem do metod zestawów zależnych.  
  
## <a name="rule-description"></a>Opis reguły  
 Odbicie jest elastyczną funkcją .NET Framework, która może służyć do wykonywania późnego powiązania aplikacji z zależnym zestawem czasu wykonywania lub do tworzenia i dynamicznego wykonywania nowych typów w czasie wykonywania. Jednak te techniki mogą zmniejszyć wydajność, jeśli są używane często lub wywoływane w ścisłych pętlach.  
  
 Aby uzyskać więcej informacji, zobacz sekcję [odbicie i późne wiązanie](https://msdn.microsoft.com/library/ms998547.aspx#scalenetchapt05_topic31) w rozdziale 5 — Poprawianie wydajności kodu zarządzanego w celu zwiększenia wydajności aplikacji .NET i skalowalności biblioteki wzorców i praktyk firmy Microsoft w witrynie MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku Szczegóły funkcji](../profiling/function-details-view.md) danych profilowania. Sprawdź wywołania funkcji metody System. Type lub system. odbicie, aby znaleźć sekcje programu, które najczęściej wykorzystują interfejsy API odbicia programu .NET. Unikaj używania metod, które zwracają metadane. Gdy wydajność aplikacji jest krytyczna, może być konieczne uniknięcie używania późnego powiązania i tworzenia typów dynamicznie w czasie wykonywania.
