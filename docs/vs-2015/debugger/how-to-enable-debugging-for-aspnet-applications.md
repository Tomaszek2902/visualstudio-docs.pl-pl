---
title: 'Instrukcje: Włączanie debugowania dla aplikacji ASP.NET | Microsoft Docs'
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
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726e964a0db2fae1b902f54a14e206dbc03a148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477008"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Porady: włączanie debugowania dla aplikacji ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby włączyć debugowanie, należy włączyć ją zarówno na stronie **właściwości projektu** , jak i w pliku web.config aplikacji.  
  
> [!NOTE]  
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](/previous-versions/zbhkx167(v=vs.140)).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Aby włączyć debugowanie ASP.NET we właściwościach projektu (Visual Basic/C#)  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu sieci Web i wybierz polecenie **Właściwości**.  
  
2. Na stronie właściwości projektu kliknij kartę **Sieć Web** .  
  
3. W obszarze **debugery**zaznacz pole wyboru **ASP.NET** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Aby włączyć debugowanie w pliku web.config  
  
1. Otwórz plik web.config przy użyciu dowolnego standardowego edytora tekstu lub parsera XML.  
  
    > [!NOTE]  
    > Nie można uzyskać dostępu do pliku zdalnie przy użyciu przeglądarki sieci Web. Ze względów bezpieczeństwa program [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] konfiguruje usługi Microsoft IIS, aby zapobiec bezpośredniemu dostępowi do Web.config plików przez przeglądarkę. Jeśli spróbujesz uzyskać dostęp do pliku konfiguracji przy użyciu przeglądarki, zostanie wyświetlony błąd dostępu HTTP 403 (dostęp zabroniony).  
  
2. Web.config jest plikiem XML i dlatego zawiera zagnieżdżone sekcje oznaczone przez Tagi. Znajdź `configuration/system.web/compilation` element. Jeśli element kompilacja nie istnieje, utwórz go.  
  
3. Jeśli `compilation` element nie zawiera `debug` atrybutu, Dodaj atrybut do elementu.  
  
4. Upewnij się, że `debug` wartość atrybutu jest ustawiona na `true` .  
  
Plik web.config powinien wyglądać podobnie do poniższego przykładu. Należy pamiętać, że między elementami konfiguracji i system. Web mogą znajdować się sekcje  
  
- sekcje elementów między elementami konfiguracji i system. Web  
  
- sekcje elementów między elementami system. Web i compilation  
  
- Element compilation może zawierać inne atrybuty i elementy  
  
## <a name="example"></a>Przykład  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Program automatycznie wykrywa wszelkie zmiany w plikach Web.config i stosuje nowe ustawienia konfiguracji. Aby zmiany zaczęły obowiązywać, nie trzeba ponownie uruchamiać komputera ani ponownie uruchamiać serwera IIS.  
  
Witryna sieci Web może zawierać wiele katalogów wirtualnych i podkatalogów, a pliki Web.config mogą znajdować się w każdym z nich. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacje dziedziczą ustawienia z plików Web.config na wyższych poziomach w ścieżce URL. Hierarchiczne pliki konfiguracji umożliwiają zmianę ustawień dla kilku [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji w tym samym czasie, na przykład dla wszystkich aplikacji znajdujących się poniżej w hierarchii. Jednak jeśli `debug` jest ustawiona w pliku znajdującym się niżej w hierarchii, zostanie przesłonięta wyższa wartość.  
  
Na przykład można określić `debug="true"` w `www.microsoft.com/aaa/Web.config` , a dowolna aplikacja w folderze AAA lub w dowolnym podfolderze AAA będzie dziedziczyć to ustawienie. W związku z [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tym, jeśli aplikacja jest w systemie `www.microsoft.com/aaa/bbb` , dziedziczy to ustawienie, tak jak wszystkie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacje w `www.microsoft.com/aaa/ccc` , `www.microsoft.com/aaa/ddd` i tak dalej. Jedynym wyjątkiem jest to, że jedna z tych aplikacji zastępuje ustawienie za pomocą własnego pliku Web.config niższej.  
  
Włączenie trybu debugowania znacznie będzie miało wpływ na wydajność [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji. Należy pamiętać, aby wyłączyć tryb debugowania przed wdrożeniem aplikacji wydania lub przeprowadzeniem pomiarów wydajności.  
  
## <a name="see-also"></a>Zobacz też  
[Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
