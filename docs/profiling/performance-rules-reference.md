---
title: Informacje o regułach wydajności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5280226aaba40de42052d72e58928a53af53f631
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543640"
---
# <a name="performance-rules-reference"></a>Zasady wydajności — Odwołanie
Reguły wydajności narzędzia profilowania zawierają dodatkowe ostrzeżenia i informacje o wydajności aplikacji. Reguły wydajności analizują dane w przebiegu profilowania, który jest zbierany ze źródeł, takich jak liczniki wydajności systemu Windows i procesora. Komunikaty reguły są wyświetlane w oknie dane wyjściowe błędu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zintegrowanego środowiska deweloperskiego. Komunikaty są wyświetlane z jednym z następujących poziomów reguł:

|Kategoria|Opis|
|-|-|
|**Błąd**|Niektóre reguły generują komunikaty o błędach, ponieważ większość problemów z wydajnością nie jest błędem. Komunikat o błędzie może wskazywać na awarię zbierania danych profilowania.|
|**Ostrzeżenie**|Ostrzeżenia wskazują obszar aplikacji, który może być źródłem problemów z wydajnością lub które mogą korzystać z optymalizacji.|
|**Informacje**|Komunikaty informacyjne wskazują, że analiza warunku reguły nie osiągnęła progu w celu wygenerowania komunikatu o błędzie lub że informacje w komunikacie są przydatne, ale nie odzwierciedlają problemu z wydajnością.|

## <a name="in-this-section"></a>W tej sekcji

[Reguły wydajności według identyfikatora](../profiling/performance-rules-by-id.md)

Reguły wydajności narzędzia profilowania są zorganizowane w czterech kategoriach:

|Kategoria|Opis|
|-|-|
|[Reguły wydajności .NET Framework użycia](../profiling/dotnet-framework-usage-performance-rules.md)|Reguły ułatwiające korzystanie z .NET Framework wydajnie.|
|[Reguły wydajności pamięci i stronicowania](../profiling/memory-and-paging-performance-rules.md)|Reguły, które analizują pamięć zarządzaną i zachowanie stronicowania aplikacji.|
|[narzędzia profilowania reguł użycia](../profiling/profiling-tools-usage-rules.md)|Reguły ułatwiające korzystanie z narzędzia profilowania wydajnie.|
|[Reguły wydajności monitorowania zasobów](../profiling/resource-monitoring-performance-rules.md)|Komunikaty informacyjne dotyczące użycia procesora i pamięci w przebiegu profilowania.|
