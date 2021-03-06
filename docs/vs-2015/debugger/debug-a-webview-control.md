---
title: Debugowanie kontrolki WebView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f2da5b3122bd97fcbef0db7124049372c21983f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817166"
---
# <a name="debug-a-webview-control"></a>Debugowanie kontrolki WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Aby przeprowadzić inspekcję i debugowanie `WebView` formantów w aplikacji środowisko wykonawcze systemu Windows, można skonfigurować program Visual Studio do dołączania debugera skryptów podczas uruchamiania aplikacji. Począwszy od Visual Studio 2013 Update 2, istnieją dwa sposoby współpracy z `WebView` kontrolkami przy użyciu debugera:  
  
- Otwórz [dom Explorer](../debugger/quickstart-debug-html-and-css.md) `WebView` wystąpienia i sprawdź elementy dom, zbadaj problemy z stylem CSS i przetestuj dynamicznie renderowane zmiany stylów.  
  
- Wybierz stronę sieci Web lub `iFrame` wyświetloną w `WebView` wystąpieniu jako element docelowy w oknie [konsoli JavaScript](../debugger/javascript-console-commands.md) , a następnie posługując się z tą stroną przy użyciu poleceń konsoli. Konsola zapewnia dostęp do bieżącego kontekstu wykonywania skryptu.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Dołącz debuger (C#, Visual Basic, C++)  
  
1. W programie Visual Studio Dodaj `WebView` kontrolkę do aplikacji środowisko wykonawcze systemu Windows.  
  
2. W Eksplorator rozwiązań otwórz właściwości projektu, wybierając **Właściwości** z menu skrótów dla projektu.  
  
3. Wybierz **Debuguj**. Na liście **proces aplikacji** wybierz pozycję **skrypt**.  
  
     ![Dołącz debuger skryptów](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4. Obowiązkowe W przypadku wersji nieekspresowych programu Visual Studio Wyłącz debugowanie just-in-Time (JIT), wybierając **Narzędzia**, **Opcje**, **debugowanie**, **just in Time**, a następnie wyłączając debugowanie JIT dla skryptu.  
  
    > [!NOTE]
    > Wyłączenie debugowania JIT pozwala ukryć okna dialogowe dla nieobsłużonych wyjątków, które występują na niektórych stronach sieci Web. W Visual Studio Express debugowanie JIT jest zawsze wyłączone.  
  
5. Naciśnij klawisz F5, aby uruchomić debugowanie.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Użyj DOM Explorer, aby przeprowadzić inspekcję i debugowanie kontrolki WebView  
  
1. (C#, Visual Basic, C++) Dołącz debuger skryptów do aplikacji. Zapoznaj się z pierwszą sekcją, aby uzyskać instrukcje.  
  
2. Jeśli jeszcze tego nie zrobiono, Dodaj `WebView` kontrolkę do aplikacji i naciśnij klawisz F5, aby rozpocząć debugowanie.  
  
3. Przejdź do strony zawierającej `Webview` kontrolki.  
  
4. Otwórz okno DOM Explorer dla `WebView` kontrolki, wybierając **Debuguj**, **Windows**, **dom Explorer**, a następnie wybierz adres URL, `WebView` który chcesz sprawdzić.  
  
     ![Otwieranie DOM Explorer](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     DOM Explorer skojarzona z `WebView` wyświetlaną jako nowa karta w programie Visual Studio.  
  
5. Wyświetlaj i Modyfikuj elementy na żywo i style CSS zgodnie z opisem w artykule [debugowanie stylów CSS przy użyciu dom Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Korzystanie z okna konsoli JavaScript do sprawdzania i debugowania kontrolki WebView  
  
1. (C#, Visual Basic, C++) Dołącz debuger skryptów do aplikacji. Zapoznaj się z pierwszą sekcją, aby uzyskać instrukcje.  
  
2. Jeśli jeszcze tego nie zrobiono, Dodaj `WebView` kontrolkę do aplikacji i naciśnij klawisz F5, aby rozpocząć debugowanie.  
  
3. Otwórz okno konsoli JavaScript dla `WebView` kontrolki, wybierając kolejno opcje **Debuguj**, **Windows**i **JavaScript**.  
  
     Zostanie wyświetlone okno konsoli JavaScript.  
  
4. Przejdź do strony zawierającej `Webview` kontrolki.  
  
5. W oknie konsoli wybierz stronę sieci Web lub `iFrame` wyświetlaną przez `WebView` formant na liście **cel** .  
  
     ![Wybór elementu docelowego w oknie konsoli JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    > Za pomocą konsoli programu można `WebView` w danym momencie korzystać z pojedynczego, `iFrame` , udostępnić umowę lub proces roboczy sieci Web. Każdy element wymaga oddzielnego wystąpienia hosta platformy sieci Web (WWAHost.exe). Można korzystać z jednego hosta naraz.  
  
6. Wyświetlaj i Modyfikuj zmienne w aplikacji lub korzystaj z poleceń konsoli, zgodnie z opisem w [przewodniku szybki start: debugowanie](../debugger/quickstart-debug-javascript-using-the-console.md) [poleceń konsoli](../debugger/javascript-console-commands.md)JavaScript i JavaScript.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)
