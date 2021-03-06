---
title: 'Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18c8dd4d0bc79ac2f3af44b8b5f8dd6faacb9f45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796756"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Porady: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wszystkie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje wymagają, aby poprawna wersja .NET Framework była zainstalowana na komputerze, zanim będzie można go uruchomić. wiele aplikacji również ma inne wymagania wstępne. Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji można wybrać zestaw wstępnie wymaganych składników do spakowania wraz z aplikacją. Podczas instalacji dla każdego wymagania wstępnego zostanie wykonane sprawdzenie w celu ustalenia, czy już istnieje; w przeciwnym razie zostanie zainstalowana przed zainstalowaniem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
 Zamiast pakowania i publikowania wymagań wstępnych można także określić lokalizację pobierania dla składników. Na przykład zamiast uwzględniać wymagania wstępne dla każdej opublikowanej aplikacji, można użyć scentralizowanego udziału plików lub lokalizacji sieci Web, która zawiera Instalatory dla wszystkich wymagań wstępnych — w czasie instalacji składniki zostaną pobrane i zainstalowane z tej lokalizacji.  
  
> [!IMPORTANT]
> Przed opublikowaniem pierwszej aplikacji należy dodać wstępnie wymagane pakiety Instalatora do komputera deweloperskiego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Aby uzyskać więcej informacji, zobacz [How to: dołączanie wymagań wstępnych do aplikacji ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Wymagania wstępne są zarządzane w oknie dialogowym **wymagania wstępne** dostępne z okienka **Publikowanie** **projektanta projektu**.  
  
> [!NOTE]
> Oprócz wstępnie określonej listy wymagań wstępnych można dodać własne składniki do listy. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Aby określić wymagania wstępne instalacji przy użyciu aplikacji ClickOnce  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Wybierz okienko **Publikowanie** .  
  
3. Kliknij przycisk **wymagania wstępne** , aby otworzyć okno dialogowe **wymagania wstępne** .  
  
4. W oknie dialogowym **wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** .  
  
5. Na liście **wymagania wstępne** zaznacz składniki, które chcesz zainstalować, a następnie kliknij przycisk **OK**.  
  
     Wybrane składniki zostaną spakowane i opublikowane razem z aplikacją.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Aby określić inną lokalizację pobierania dla wymagań wstępnych  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Wybierz okienko **Publikowanie** .  
  
3. Kliknij przycisk **wymagania wstępne** , aby otworzyć okno dialogowe **wymagania wstępne** .  
  
4. W oknie dialogowym **wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** .  
  
5. W sekcji **Określ lokalizację instalacji dla wymagań wstępnych** wybierz pozycję **Pobierz wymagania wstępne z następującej lokalizacji**.  
  
6. Wybierz lokalizację z listy rozwijanej lub wprowadź adres URL, ścieżkę pliku lub lokalizację FTP, a następnie kliknij przycisk **OK.**  
  
    > [!NOTE]
    > Należy upewnić się, że Instalatory dla określonych składników istnieją w określonej lokalizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
