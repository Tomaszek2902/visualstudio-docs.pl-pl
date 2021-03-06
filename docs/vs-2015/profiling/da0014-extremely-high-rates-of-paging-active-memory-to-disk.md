---
title: 'DA0014: niezwykle wysokie stawki stronicowania aktywnej pamięci na dysk | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf391f96cd21f0c473589d4992083963ff65d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64813392"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0014 |  
| Kategoria | Pamięć i stronicowanie |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Występuje bardzo wysoki stopień stronicowania aktywnej pamięci na dysk. Twoja aplikacja może być powiązana z pamięcią. |  
| Typ reguły | Ostrzeżenie |  
  
 Podczas profilowania przy użyciu metod próbkowania, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.  
  
## <a name="cause"></a>Przyczyna  
 Dane wydajności systemu, które zostały zebrane w ramach uruchomienia profilowania, wskazują na to, że w trakcie przebiegu profilowania wystąpił bardzo wysoki stopień stronicowania aktywnej pamięci do i z dysku. Stawki stronicowania na tym poziomie mają zwykle wpływ na wydajność i czas odpowiedzi aplikacji. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji. ponowne uruchamianie profilowania na komputerze z większą ilością pamięci.  
  
## <a name="rule-description"></a>Opis reguły  
 Nadmierne stronicowanie na dysku może być spowodowane brakiem pamięci fizycznej. Jeśli operacje stronicowania korzystają z dysku fizycznego, w którym znajduje się plik stronicowania, mogą spowolnić inne operacje na dysku zorientowanym na aplikacje na tym samym dysku.  
  
 Często strony są odczytywane z dysku lub zapisywane na dysku w operacjach stronicowania zbiorczego. Liczba stron wyjściowych/s jest często znacznie większa niż liczba operacji zapisu stron/s, na przykład. Ponieważ strony wyjściowe/s zawierają również zmienione strony danych z pamięci podręcznej plików systemowych. Jednak nie zawsze można łatwo ustalić, który proces jest bezpośrednio odpowiedzialny za stronicowanie lub dlaczego.  
  
> [!NOTE]
> Ta zasada jest wyzwalana, gdy poziomy stronicowania aktywnej pamięci osiągną dużą szybkość. Gdy poziom stronicowania jest znaczący, ale nie skrajny, reguła informacyjna [DA0017: wysokie stawki stronicowania aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) .  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku [znaczniki](../profiling/marks-view.md) . Znajdowanie kolumny **pamięć \ strony/s** . Ustal, czy istnieją określone fazy wykonywania programu, w których operacje we/wy stronicowania są większe niż inne.  
  
 Jeśli zbierasz dane profilu dla aplikacji ASP.NET w scenariuszu testowania obciążenia, spróbuj ponownie uruchomić test obciążenia na komputerze skonfigurowanym z dodatkową pamięcią fizyczną (lub pamięcią RAM).  
  
 Należy rozważyć zmniejszenie alokacji pamięci przez skorygowanie algorytmów i uniknięcie interfejsów API intensywnie korzystających z pamięci, takich jak String. Concat i String. substring.
