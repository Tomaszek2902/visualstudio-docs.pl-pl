---
title: Zdarzenia (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d24fc7a01a8eebe356f37704c1a821332f5dca1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850764"
---
# <a name="events-vsperfcmd"></a>Zdarzenia (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **zdarzenia** VSPerfCmd.exe steruje rejestrowaniem śledzenia zdarzeń systemu Windows (ETW). Dane ETW są zapisywane w pliku ETL, który jest oddzielony od pliku danych profilera. Dane można wyświetlić w raporcie za pomocą polecenia [VSPerfReport](../profiling/vsperfreport.md) /Summary: ETW.  
  
 Opcję **zdarzenia** można wywołać w dowolnym momencie przed wywołaniem polecenia VSPerfCmd **Shutdown** w celu zatrzymania profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Na**&#124;**wyłączone**  
 Uruchamia lub kończy zbieranie danych zdarzeń.  
  
 `Guid`  
 Identyfikator GUID kontrolki dostawcy.  
  
 `ProviderName`  
 Nazwa dostawcy, który jest zarejestrowany w Instrumentacja zarządzania Windows (WMI).  
  
 `Flags`  
 Wartość "0x" — wstępnie ustalonych flag szesnastkowych, które są definiowane przez dostawcę zdarzeń.  
  
 `Level`  
 Określa ilość zbieranych danych. `Level` jest definiowana przez dostawcę zdarzeń.  
  
 Opcja **Events** umożliwia zrozumienie następujących słów kluczowych jądra jako nazw dostawców:  
  
 **Proces**  
 Przetwarzanie zdarzeń  
  
 **Nici**  
 Zdarzenia wątku  
  
 **Obraz**  
 Ładowanie i zwalnianie obrazów  
  
 **Dysk**  
 Zdarzenia we/wy dysku  
  
 **Plik**  
 Zdarzenia we/wy pliku  
  
 **Hardfault**  
 Błędy stron twardych  
  
 **Pagefault**  
 Słabe błędy stron  
  
 **Sieć**  
 Zdarzenia sieciowe  
  
 **Rejestr**  
 Zdarzenia dostępu do rejestru  
  
 Należy pamiętać, że dostawca jądra może być tylko włączony. Nie można go wyłączyć ani zmienić jego flag, dopóki monitor nie zostanie zamknięty.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Po włączeniu zdarzeń ETW CLR dodatkowe dane uruchamiania są również zbierane w raporcie widoku śledzenia. Aby wykluczyć zdarzenia uruchamiania z wyświetlania w raporcie, użyj następującego polecenia:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> Jeśli zdarzenia uruchamiania nie zostaną wykluczone, ponieważ te zdarzenia nie są wymienione w pliku Managed Object Format (MOF), są one wyświetlane jako identyfikatory GUID w raporcie. Aby uzyskać więcej informacji, zobacz Tę stronę w witrynie sieci Web firmy Microsoft: [przykładowy plik Managed Object Format (MOF)](https://msdn.microsoft.com/library/default.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
