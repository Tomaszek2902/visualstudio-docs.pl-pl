---
title: 'Instrukcje: uruchamianie procesu roboczego w ramach konta użytkownika | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebb8ec1fe10f6fbc5c367cb0ed127e048351b0e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157869"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Porady: uruchamianie procesu roboczego z konta użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby skonfigurować komputer w taki sposób, aby można było uruchomić [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy (aspnet_wp.exe lub w3wp.exe) w ramach konta użytkownika, wykonaj następujące kroki.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Aby uruchomić aspnet_wp.exe w ramach konta użytkownika  
  
1. Otwórz plik machine.config znajdujący się na komputerze w folderze CONFIG pod ścieżką, w której zainstalowano środowisko uruchomieniowe.  
  
2. Znajdź &lt; sekcję processModel &gt; i zmień atrybuty użytkownika i hasła na nazwę i hasło konta użytkownika, które ma być uruchamiane aspnet_wp.exe.  
  
3. Zapisz plik machine.config.  
  
4. W systemie [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)] usługi IIS 6,0 są instalowane domyślnie. Odpowiedni proces roboczy jest w3wp.exe. Aby uruchomić w trybie usług IIS 6,0 z aspnet_wp.exe jako proces roboczy, należy wykonać następujące czynności:  
  
    1. Kliknij przycisk **Start**, kliknij pozycję **Narzędzia administracyjne** , a następnie wybierz pozycję **Internet Information Services**.  
  
    2. W oknie dialogowym **Internet Information Services** kliknij prawym przyciskiem myszy folder **witryny sieci Web** i wybierz polecenie **Właściwości**.  
  
    3. W oknie dialogowym **Właściwości witryn sieci Web** wybierz pozycję **Usługa**.  
  
    4. Wybierz pozycję **Uruchom usługę WWW w trybie izolacji usług IIS 6.0**.  
  
    5. Zamknij okno dialogowe **Właściwości** i **Menedżer usług internetowych**.  
  
5. Otwórz wiersz polecenia systemu Windows i zresetuj serwer, uruchamiając polecenie:  
  
    ```  
    iisreset  
    ```  

    oraz  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6. Znajdź [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] folder pliki tymczasowe, który powinien znajdować się w tej samej ścieżce co folder konfiguracji. Kliknij prawym przyciskiem myszy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] folder pliki tymczasowe i wybierz polecenie **Właściwości** w menu skrótów.  
  
7. W oknie dialogowym **właściwości plików tymczasowych ASP.NET** kliknij kartę **zabezpieczenia** .  
  
8. Kliknij pozycję **Zaawansowane**.  
  
9. W oknie dialogowym **Zaawansowane ustawienia zabezpieczeń dla plików tymczasowych ASP.NET** kliknij przycisk **Dodaj**.  
  
    Zostanie wyświetlone okno **dialogowe Wybieranie użytkownika, komputera lub grupy** .  
  
10. Wpisz nazwę użytkownika w polu **Wprowadź nazwę obiektu do wybrania** , a następnie kliknij przycisk **OK**. Nazwa użytkownika musi być zgodna z formatem: DomainName\UserName.  
  
11. W oknie dialogowym **wpis uprawnienia dla plików tymczasowych ASP.NET** nadaj użytkownikowi **pełną kontrolę**, a następnie kliknij przycisk **OK** , aby zamknąć **wpis dla tymczasowych plików ASP.NET** okno dialogowe.  
  
12. Zostanie wyświetlone okno dialogowe **zabezpieczenia** z pytaniem, czy naprawdę chcesz zmienić uprawnienia do folderu systemowego. Kliknij przycisk **Yes** (Tak).  
  
13. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **właściwości plików tymczasowych ASP.NET** .  
  
## <a name="see-also"></a>Zobacz też  
[Debugowanie ASP.NET: Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)  
