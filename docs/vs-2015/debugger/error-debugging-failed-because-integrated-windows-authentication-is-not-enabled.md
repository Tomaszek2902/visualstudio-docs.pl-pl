---
title: 'Błąd: debugowanie nie powiodło się, ponieważ zintegrowane uwierzytelnianie systemu Windows nie jest włączone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 89afba591899b626863b0157f6d9d955d46e46cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851919"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Błąd: debugowanie nie powiodło się ponieważ zintegrowane uwierzytelnianie systemu Windows nie jest włączone
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Błąd uwierzytelniania uniemożliwił uwierzytelnienie użytkownika, który zażądał debugowania. Taka sytuacja może wystąpić podczas próby przekroczenia kroku do aplikacji sieci Web lub usługi sieci Web XML. Jedną z przyczyn tego błędu jest to, że zintegrowane uwierzytelnianie systemu Windows nie jest włączone. Aby je włączyć, wykonaj kroki opisane w sekcji "aby włączyć zintegrowane uwierzytelnianie systemu Windows".  
  
 Jeśli włączono zintegrowane uwierzytelnianie systemu Windows i nadal pojawia się ten błąd, może to być spowodowane tym, że jest włączone **uwierzytelnianie szyfrowane dla serwerów domeny systemu Windows** . W takiej sytuacji należy skontaktować się z administratorem sieci.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Aby włączyć zintegrowane uwierzytelnianie systemu Windows  
  
1. Zaloguj się na serwerze sieci Web przy użyciu konta administratora.  
  
2. Kliknij przycisk **Start** , a następnie kliknij pozycję **Panel sterowania**.  
  
3. W **Panelu sterowania**kliknij dwukrotnie ikonę **Narzędzia administracyjne**.  
  
4. Kliknij dwukrotnie **Internet Information Services**.  
  
5. Kliknij węzeł serwer sieci Web.  
  
     Folder **witryn sieci Web** zostanie otwarty pod nazwą serwera.  
  
6. Można skonfigurować uwierzytelnianie dla wszystkich witryn sieci Web lub poszczególnych witryn sieci Web. Aby skonfigurować uwierzytelnianie dla wszystkich witryn sieci Web, kliknij prawym przyciskiem myszy folder **witryny sieci Web** , a następnie kliknij polecenie **Właściwości**. Aby skonfigurować uwierzytelnianie dla pojedynczej witryny sieci Web, Otwórz folder **witryny sieci Web** , kliknij prawym przyciskiem myszy poszczególne witryny sieci Web, a następnie kliknij polecenie **Właściwości**.  
  
     Zostanie wyświetlone okno dialogowe **Właściwości** .  
  
7. Kliknij kartę **Zabezpieczenia katalogów** .  
  
8. W sekcji **dostęp anonimowy i kontrola uwierzytelnienia** kliknij przycisk **Edytuj**.  
  
     Zostanie wyświetlone okno dialogowe **metody uwierzytelniania** .  
  
9. W obszarze **dostęp uwierzytelniony**wybierz pozycję **zintegrowane uwierzytelnianie systemu Windows**.  
  
10. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **metody uwierzytelniania** .  
  
11. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Właściwości** .  
  
12. Zamknij okno **Internet Information Services** .  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Aby włączyć zintegrowane uwierzytelnianie systemu Windows w systemie Windows Vista/IIS 7  
  
1. Zaloguj się na serwerze sieci Web przy użyciu konta administratora.  
  
2. Włącz uwierzytelnianie systemu Windows i zgodność zarządzania II6, jeśli nie zostało to zrobione wcześniej, wykonując następujące czynności:  
  
    1. Kliknij przycisk **Start**, kliknij pozycję **Panel sterowania** , a następnie kliknij pozycję **programy**.  
  
    2. W obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.  
  
         Zostanie wyświetlone okno dialogowe Access Control użytkownika i zostanie wyświetlony komunikat z prośbą o zgodę na kontynuowanie.  
  
    3. Kliknij pozycję **Kontynuuj**.  
  
         Zostanie wyświetlone okno dialogowe funkcje systemu Windows.  
  
    4. Na liście funkcja rozwiń węzeł **Internet Information Services** .  
  
    5. W obszarze **Internet Information Services**rozwiń węzeł **usługi World Wide Web Services** .  
  
    6. W obszarze **World Wide Web Services**kliknij pozycję **zabezpieczenia**.  
  
    7. Kliknij pozycję **uwierzytelnianie systemu Windows**.  
  
    8. W obszarze **Internet Information Services**rozwiń węzeł **Narzędzia do zarządzania siecią Web** .  
  
    9. W obszarze **Narzędzia do zarządzania siecią Web**rozwiń węzeł **zgodność zarządzania usługami IIS** w wersji 6, a następnie zaznacz pole wyboru **Zgodność konfiguracji metabazy usług IIS 6 i usług IIS 6** .  
  
    10. W obszarze **Narzędzia do zarządzania siecią Web**wybierz pozycję **Konsola zarządzania usługami IIS** , a następnie kliknij przycisk **OK.**  
  
    11. Uruchom ponownie komputer, aby te zmiany zaczęły obowiązywać.  
  
3. Kliknij przycisk **Start** , a następnie kliknij pozycję **Panel sterowania**.  
  
4. Kliknij pozycję **Widok klasyczny**, a następnie kliknij dwukrotnie ikonę **Narzędzia administracyjne**.  
  
5. W kolumnie **Nazwa** kliknij dwukrotnie pozycję **Menedżer Internet Information Services (IIS)**.  
  
6. W kolumnie **połączenia** rozwiń węzeł serwera.  
  
     Folder **witryn sieci Web** zostanie otwarty pod nazwą serwera.  
  
7. Rozwiń węzeł **witryny sieci Web** , a następnie kliknij witrynę sieci Web, dla której chcesz włączyć zintegrowane uwierzytelnianie systemu Windows.  
  
8. Tytuł środkowego okienka zmienia nazwę wybranej witryny sieci Web. W tym okienku w obszarze nagłówek **usług IIS** kliknij dwukrotnie pozycję **uwierzytelnianie**.  
  
     Tytuł okienka zmieni się na **uwierzytelnianie**.  
  
9. W okienku **uwierzytelnianie** w kolumnie **Nazwa** kliknij prawym przyciskiem myszy pozycję **uwierzytelnianie systemu Windows** , a następnie kliknij pozycję **Włącz**.  
  
10. Zamknij okno **menedżera Internet Information Services (IIS)** .  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Uwierzytelnianie Microsoft Digest](https://msdn2.microsoft.com/library/Aa378744.aspx)   
 [Uruchamianie aplikacji sieci Web w systemie Windows Vista przy użyciu usług IIS 7,0 i programu Visual Studio](https://msdn.microsoft.com/library/262a82ac-dd0e-4096-86c6-fb463e88be66)
