---
title: ProcessOn i ProcessOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77e21a280700520b6861dd42e01a4aefa4faa704
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180203"
---
# <a name="processon-and-processoff"></a>ProcessOn i ProcessOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **ProcessOff** i **ProcessOn** podpolecenia wstrzymują i wznawiają profilowanie określonego procesu w sesji profilowania wiersza polecenia. **ProcessOff** przerywa proces profilowania procesu, a **ProcessOn** uruchamia profilowanie procesu.  
  
 W większości przypadków należy określić **ProcessOn** lub **ProcessOff** jako jedyną opcję w wierszu polecenia VSPerfCmd.exe, ale można je również łączyć z podpoleceniami **GlobalOn**, **GlobalOff**, **ThreadOn**i **ThreadOff** .  
  
 Podpolecenia **ProcessOn** i **ProcessOff** współpracują z podpoleceniami **GlobalOn** i **GlobalOff** , które kontrolują zbieranie danych dla wszystkich procesów w sesji profilowania wiersza polecenia i polecenia **ThreadOn** i **ThreadOff** , które kontrolują zbieranie danych dla określonego wątku.  
  
 Podpolecenia **ProcessOff** i **ProcessOn** wpływają również na licznik uruchomienia/zatrzymania procesu, który jest MANIPULOWANY przez funkcje interfejsu API profilera.  
  
- **ProcessOff** natychmiast ustawia liczbę uruchomień/zatrzymań procesu na 0, w związku z tym wstrzymuje profilowanie.  
  
- **ProcessOn** natychmiast ustawia liczbę uruchomień/zatrzymań procesu na 1, w związku z tym wznawia profilowanie.  
  
  Aby uzyskać więcej informacji, zobacz [narzędzia profilowania interfejsów API](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `PID`  
 Identyfikator liczby całkowitej procesu, który ma zostać uruchomiony lub zatrzymany. Identyfikatory procesów są wyświetlane na karcie proces Menedżera zadań systemu Windows.  
  
## <a name="required-subcommands"></a>Wymagane podpolecenia  
 Brak  
  
## <a name="valid-subcommands"></a>Prawidłowe podpolecenia  
 **ProcessOn** i **ProcessOff** można określić w wierszach poleceń, które również zawierają następujące podpolecenia.  
  
 **Rozpocznij:**`Method`  
 Inicjuje sesję profilowania wiersza polecenia i ustawia określoną metodę profilowania.  
  
 **Uruchom:**`AppName`  
 Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.  
  
 **Dołącz:**`PID`  
 Rozpoczyna profilowanie określonego procesu.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Powoduje zatrzymanie lub uruchomienie profilowania dla wszystkich procesów w sesji profilowania wiersza polecenia.  
  
 {**ThreadOff**&#124;**ThreadOn**} **:**`TID`  
 Kończy lub uruchamia profilowanie dla określonego wątku (tylko Metoda Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie podpolecenie **ProcessOff** służy do zbierania danych profilowania do uruchamiania aplikacji.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
