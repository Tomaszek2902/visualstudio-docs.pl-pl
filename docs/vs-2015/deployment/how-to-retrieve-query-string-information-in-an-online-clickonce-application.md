---
title: 'Instrukcje: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 588ff95f90c6d85526dfe931e8f0b8ab439d9b94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697579"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Porady: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Ciąg zapytania* jest częścią adresu URL zaczynającą się od znaku zapytania (?), który zawiera dowolne informacje w postaci *nazwa = wartość*. Załóżmy, że masz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację `WindowsApp1` , która jest hostem `servername` , i chcesz przekazać wartość zmiennej `username` podczas uruchamiania aplikacji. Twój adres URL może wyglądać następująco:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Poniższe dwie procedury pokazują, jak używać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji do uzyskiwania informacji o ciągu zapytania.  
  
> [!NOTE]
> Informacje można przekazać tylko w ciągu zapytania, gdy aplikacja jest uruchamiana przy użyciu protokołu HTTP, a nie przy użyciu udziału plików lub lokalnego systemu plików.  
  
 Pierwsza procedura pokazuje, w jaki sposób [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja może używać małego fragmentu kodu do odczytywania tych wartości podczas uruchamiania aplikacji.  
  
 W następnej procedurze pokazano, jak skonfigurować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację przy użyciu MageUI.exe, aby można było akceptować parametry ciągu zapytania. Należy to zrobić po każdym opublikowaniu aplikacji.  
  
> [!NOTE]
> Zapoznaj się z sekcją "zabezpieczenia" w dalszej części tego tematu przed podjęciem decyzji o włączeniu tej funkcji.  
  
 Aby uzyskać informacje dotyczące sposobu tworzenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia przy użyciu Mage.exe lub MageUI.exe, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
> Począwszy od .NET Framework 3,5 z dodatkiem SP1, możliwe jest przekazanie argumentów wiersza polecenia do aplikacji w trybie offline [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Jeśli chcesz podać argumenty do aplikacji, możesz przekazać parametry do pliku skrótu za pomocą. Rozszerzenie APPREF-MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Aby uzyskać informacje o ciągu zapytania z aplikacji ClickOnce  
  
1. Umieść poniższy kod w projekcie. Aby ten kod działał, trzeba mieć odwołanie do System. Web i `using` instrukcji Add lub `Imports` for for System. Web, system. Collections. specjalizowane i system. Deployment. Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs#1)]
     [!code-vb[ClickOnceQueryString#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb#1)]  
  
2. Wywołaj wcześniej zdefiniowaną funkcję, aby pobrać <xref:System.Collections.DictionaryBase.Dictionary%2A> parametry ciągu zapytania indeksowane według nazwy.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Aby włączyć przekazywanie ciągu zapytania w aplikacji ClickOnce przy użyciu MageUI.exe  
  
1. Otwórz wiersz polecenia programu .NET i wpisz:  
  
    ```  
    MageUI  
    ```  
  
2. Z menu **plik** wybierz polecenie **Otwórz**, a następnie otwórz manifest wdrożenia dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, czyli plik kończący się `.application` rozszerzeniem.  
  
3. Wybierz panel **Opcje wdrożenia** w oknie nawigacyjnym po lewej stronie, a następnie zaznacz pole wyboru **Zezwalaj na przekazywanie parametrów adresu URL do aplikacji** .  
  
4. Z menu **plik** wybierz pozycję **Zapisz**.  
  
> [!NOTE]
> Alternatywnie można włączyć przekazywanie ciągu zapytania w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Wybierz pole wyboru **Zezwalaj na przekazywanie parametrów adresu URL do aplikacji** , które można znaleźć, otwierając **właściwości projektu**, wybierając kartę **Publikowanie** , klikając przycisk **Opcje** , a następnie wybierając **manifesty**.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W przypadku używania parametrów ciągu zapytania należy zadbać o to, aby Twoja aplikacja została zainstalowana i aktywowana. Jeśli aplikacja jest skonfigurowana do instalacji na komputerze użytkownika z sieci Web lub z udziału sieciowego, prawdopodobnie użytkownik będzie aktywować aplikację tylko raz za pośrednictwem adresu URL. Następnie użytkownik zazwyczaj aktywuje aplikację przy użyciu skrótu w menu **Start** . W związku z tym aplikacja ma gwarancję otrzymywania argumentów ciągu zapytania tylko raz w okresie istnienia. Jeśli zdecydujesz się przechowywać te argumenty na komputerze użytkownika do użytku w przyszłości, użytkownik jest odpowiedzialny za przechowywanie ich w bezpieczny i bezpieczny sposób.  
  
 Jeśli aplikacja działa tylko w trybie online, będzie zawsze aktywowana za pomocą adresu URL. Nawet w takim przypadku aplikacja musi być poprawnie zapisywana, aby działała prawidłowo, jeśli brakuje parametrów ciągu zapytania lub są one uszkodzone.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zezwalaj na przekazywanie parametrów adresu URL do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji tylko wtedy, gdy planujesz oczyścić dane wejściowe ze wszystkich złośliwych znaków przed użyciem. Ciąg osadzony z cudzysłowami, ukośnikami lub średnikami może wykonywać dowolne operacje na danych, jeśli użyto niefiltrowanych w zapytaniu SQL z bazą danych. Aby uzyskać więcej informacji na temat zabezpieczeń ciągów zapytań, zobacz [Omówienie luk](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)w zabezpieczeniach.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
