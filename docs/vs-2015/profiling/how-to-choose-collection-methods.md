---
title: 'Instrukcje: wybieranie metod kolekcji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ff14ce88f2032b998214ed11310a15550321dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199806"
---
# <a name="how-to-choose-collection-methods"></a>Porady: wybieranie metod kolekcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Narzędzia profilowania obsługuje trzy metody zbierania danych wydajności: próbkowanie, Instrumentacja i współbieżność. Można również użyć metody próbkowania lub Instrumentacji, aby zebrać dane alokacji pamięci .NET i okresu istnienia.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Aby określić najbardziej odpowiednią metodę kolekcji dla aplikacji, można użyć właściwości **Metoda** sesji wydajności. Można ustawić metodę kolekcji z Kreatora wydajności, Eksplorator wydajności lub ze stron właściwości sesji wydajności. Jeśli używasz narzędzi wiersza polecenia, zobacz [profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md) , aby uzyskać więcej informacji.  
  
## <a name="performance-wizard"></a>Kreator Wydajności  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Aby wybrać metodę kolekcji przy użyciu Kreatora wydajności  
  
- Na pierwszej stronie kreatora wybierz jedną z następujących opcji:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Próbkowanie procesora**|Zbiera dane statystyczne dotyczące aplikacji, które są przydatne do analizy początkowej i analizowania problemów z użyciem procesora CPU.|  
|**WMI**|Gromadzi szczegółowe dane o chronometrażu przydatne do celów analizy ukierunkowanej i analizowania problemów z wydajnością wejścia/wyjścia.|  
|**Alokacja pamięci platformy .NET**|Zbiera [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dane alokacji pamięci za pomocą metody profilowania próbkowania.|  
|**Współbieżność**|Zbiera dane o liczbie zasobów.|  
  
## <a name="performance-explorer"></a>Eksplorator wydajności  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Aby wybrać metodę kolekcji przy użyciu Eksplorator wydajności  
  
1. Na pasku narzędzi **Eksplorator wydajności** kliknij strzałkę obok listy rozwijanej **Metoda** .  
  
2. Kliknij preferowaną metodę kolekcji.  
  
## <a name="performance-session-property-pages"></a>Strony właściwości sesji wydajności  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Aby wybrać metodę próbkowania lub Instrumentacji przy użyciu właściwości sesji wydajności  
  
1. W **Eksplorator wydajności**wybierz sesję wydajności.  
  
     Nazwa pliku sesji wydajności ma rozszerzenie. psess.  
  
2. Kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.  
  
3. Na **stronie właściwości**kliknij pozycję **Ogólne**.  
  
4. Kliknij preferowaną metodę kolekcji.  
  
    - Aby uzyskać informacje o innych opcjach, które są dostępne podczas zbierania danych próbkowania, zobacz [zbieranie statystyk wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    - Aby uzyskać informacje o innych opcjach, które są dostępne podczas zbierania danych próbkowania, zobacz [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Aby wybrać zbieranie danych pamięci .NET przy użyciu właściwości sesji wydajności  
  
1. W **Eksplorator wydajności**wybierz sesję wydajności.  
  
     Nazwa pliku sesji wydajności ma rozszerzenie. psess.  
  
2. Kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.  
  
3. Na **stronie właściwości**kliknij pozycję **Ogólne**.  
  
4. Kliknij pozycję **próbkowanie** lub **Instrumentacja**.  
  
5. Kliknij pozycję **Zbierz informacje o alokacji obiektów .NET** , aby zebrać rozmiar i liczbę [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] alokacji obiektów.  
  
6. Obowiązkowe Kliknij **również pozycję Zbierz informacje o okresie istnienia obiektu .NET** , aby zebrać dane dotyczące generacji wyrzucania elementów bezużytecznych, w których odzyskuje się pamięć obiektu.  
  
     Aby uzyskać informacje o innych opcjach, które są dostępne podczas zbierania danych pamięci .NET, zobacz [zbieranie danych o alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Aby wybrać zbieranie danych współbieżności przy użyciu właściwości sesji wydajności  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.  
  
2. Na **stronie właściwości**kliknij pozycję **Ogólne**.  
  
3. Kliknij pozycję **współbieżność**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Omówienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)
