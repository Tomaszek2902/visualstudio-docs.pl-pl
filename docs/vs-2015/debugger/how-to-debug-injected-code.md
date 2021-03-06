---
title: 'Instrukcje: debugowanie wstrzykniętego kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df35a25534961c6ab94891d2da6fe54f05c37a3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681089"
---
# <a name="how-to-debug-injected-code"></a>Porady: Debugowanie wprowadzonego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Używanie atrybutów może znacznie uprościć programowanie w języku C++. Aby uzyskać więcej informacji, zobacz [pojęcia](https://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Niektóre atrybuty są interpretowane bezpośrednio przez kompilator. Inne atrybuty wstrzyknąć kod do źródła programu, które następnie Kompilator kompiluje. Ten wstrzyknięty kod ułatwia programowanie przez zmniejszenie ilości kodu, który trzeba napisać. Czasami jednak usterka może spowodować niepowodzenie aplikacji podczas wykonywania wstrzykniętego kodu. Gdy tak się stanie, prawdopodobnie zechcesz przyjrzeć się wprowadzonym kodem. Program Visual Studio oferuje dwa sposoby wyświetlania wstrzykiwanego kodu:  
  
- Wprowadzany kod można wyświetlić w oknie **demontażu** .  
  
- Za pomocą [/FX](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560)można utworzyć scalony plik źródłowy zawierający oryginalny i wprowadzający kod.  
  
  Okno **demontażowe** zawiera instrukcje dotyczące języka zestawu, które odpowiadają kodowi źródłowej i kod wstrzykiwany przez atrybuty. Ponadto w oknie **demontażu** można wyświetlić adnotację kodu źródłowego.  
  
### <a name="to-turn-on-source-annotation"></a>Aby włączyć adnotację źródłową  
  
- Kliknij prawym przyciskiem myszy okno **demontaż** i wybierz polecenie **Pokaż kod źródłowy** z menu skrótów.  
  
     Jeśli znasz lokalizację atrybutu w oknie źródłowym, możesz użyć menu skrótów, aby znaleźć wprowadzony kod w oknie **demontażu** .  
  
### <a name="to-view-injected-code"></a>Aby wyświetlić wstrzyknięty kod  
  
1. Debuger musi być w trybie przerwania.  
  
2. W oknie kod źródłowy Umieść kursor przed atrybutem, którego kod został dodany.  
  
3. Kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Przejdź do demontażu** z menu skrótów.  
  
     Jeśli lokalizacja atrybutu znajduje się w bliskim bieżącym punkcie wykonywania, możesz wybrać okno **demontaż** z menu **debugowanie** .  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Aby wyświetlić kod demontażu w bieżącym punkcie wykonywania  
  
1. Debuger musi być w trybie przerwania.  
  
2. Z menu **Debuguj** wybierz opcję **Windows**, a następnie kliknij pozycję **demontaż**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
