---
title: Zbieranie danych alokacji pamięci .NET i okresu istnienia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68decc73e14f8748d8434e05e50d6d3b48612d40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816115"
---
# <a name="collecting-net-memory-allocation-and-lifetime-data"></a>Zbieranie alokacji pamięci .NET i okres istnienia obiektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia profilowania obsługiwać zbieranie danych alokacji pamięci .NET i okresu istnienia obiektów, co pomaga wykrywać problemy z wydajnością związane z pamięcią w aplikacji.  
  
- Dane dotyczące alokacji pamięci .NET obejmują rozmiar i liczbę przydzielonych .NET Framework obiektów pamięci.  
  
- Dane okresu istnienia obiektu obejmują rozmiar i liczbę .NET Framework obiektów pamięci, które zostały odebrane w trzech generacjach wyrzucania elementów bezużytecznych.  
  
  **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Dane można zbierać przy użyciu próbkowania lub metody profilowania Instrumentacji.  
  
- W przypadku korzystania z metody próbkowania Profiler śledzi wszystkie alokacje pamięci .NET i obiekty, które są generowane przez proces, który został uruchomiony lub dołączony do.  
  
- Korzystając z metody instrumentacji, profiler śledzi tylko te przydziały pamięci .NET i obiekty, które są generowane przez moduły Instrumentacji.  
  
> [!IMPORTANT]
> Gdy zbierasz dane pamięci .NET (alokacje, okresy istnienia obiektów lub oba) przy użyciu metody próbkowania, wszystkie zdarzenia próbkowania określone przez użytkownika są ignorowane, a odpowiednie zdarzenia alokacji pamięci są używane do zbierania danych.  
  
 W przypadku włączenia profilowania of.NET alokacji pamięci należy również włączyć widok alokacja. W przypadku włączenia profilowania danych okresu istnienia programu .NET można również włączyć widok okresu istnienia obiektów. Aby uzyskać więcej informacji, zobacz widok [Alokacje](../profiling/dotnet-memory-allocations-view.md) i [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).  
  
 Aby uzyskać informacje dotyczące sposobu zbierania danych pamięci .NET przy użyciu narzędzi wiersza polecenia narzędzia profilowania, zobacz Korzystanie z metod pamięci .NET do zbierania danych alokacji pamięci i okresu istnienia obiektów przy [użyciu metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### <a name="to-collect-net-memory-data"></a>Zbieranie danych pamięci .NET  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.  
  
2. Na**stronie właściwości** _sesji wydajności_okno dialogowe, kliknij kartę **Ogólne** , a następnie zaznacz pole wyboru **Zbierz informacje o alokacji obiektu .NET** .  
  
3. Aby zebrać dane okresu istnienia obiektu platformy .NET, zaznacz pole wyboru **Zbieraj także informacje o okresie istnienia obiektu .NET** .  
  
## <a name="common-tasks"></a>Typowe zadania  
 Dodatkowe opcje można określić w oknie dialogowym _Performance Session_**strony właściwości** sesji wydajności. Aby otworzyć to okno dialogowe:  
  
- W **Eksplorator wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.  
  
  Zadania w poniższej tabeli zawierają opis opcji, które można określić w oknie dialogowym**strony właściwości** _sesji wydajności_podczas zbierania danych pamięci .NET.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na stronie **Ogólne** Określ szczegóły nazewnictwa dla wygenerowanego pliku danych profilowania (. vsp).|-   [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na stronie **Uruchamianie** wybierz aplikację do uruchomienia, jeśli masz wiele projektów. exe w rozwiązaniu kodu.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na stronie **interakcja warstwy** Dodaj dane wywołania ADO.NET do przebiegu profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na stronie **zdarzenia systemu Windows** Określ jedno lub więcej zdarzeń śledzenia zdarzeń systemu Windows (ETW), które mają być zbierane z danymi próbkowania.|-   [Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na stronie **liczniki systemu Windows** Określ co najmniej jeden licznik wydajności systemu operacyjnego, który ma zostać dodany do danych profilowania jako znaczniki.|-   [Instrukcje: zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na stronie **Zaawansowane** Określ wersję środowiska uruchomieniowego .NET Framework, która ma być używana do profilowania, jeśli moduły aplikacji korzystają z wielu wersji. Domyślnie pierwsza ładowana wersja jest profilowana.|-   [Instrukcje: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## <a name="instrumentation-tasks"></a>Zadania Instrumentacji  
 Zadania w poniższej tabeli są opcjami w oknie dialogowym **strony właściwości** , które są specyficzne dla profilowania przy użyciu metody instrumentacji.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na stronie **pliki binarne** Określ lokalizację przynoszącą instrumentację kopii modułów. Domyślnie oryginalne pliki binarne są przenoszone do folderu kopii zapasowej.|-   [Instrukcje: Zmienianie położenia plików binarnych z instrumentacją](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Na stronie **Instrumentacja** Wyklucz małe funkcje z profilowania, aby zmniejszyć obciążenie profilowania, kod JavaScript profilu w ASP.NET stronach sieci Web i określić polecenia do uruchomienia w wierszu polecenia przed i po procesie Instrumentacji.|-   [Instrukcje: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Instrukcje: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Instrukcje: Określanie poleceń przed i po Instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Na stronie **liczniki procesora** Określ co najmniej jeden licznik wydajności procesora, który ma zostać dodany do danych profilowania.|-   [Instrukcje: zbieranie danych licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|Na stronie **Zaawansowane** określ wszelkie dodatkowe opcje VSInstr.exe, takie jak opcje dołączania lub wykluczania określonych funkcji. Aby uzyskać więcej informacji na temat opcji VSInstr, zobacz [VSInstr](../profiling/vsinstr.md)|-   [Instrukcje: Określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)
