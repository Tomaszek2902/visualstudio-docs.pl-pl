---
title: 'Instrukcje: Przywracanie ukrytych poleceń debugera | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 297be3a3a4ad3c70ad28c627d5dc8d64c6ba1c7a
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2020
ms.locfileid: "64830865"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Porady: przywracanie ukrytych poleceń debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas konfigurowania programu Visual Studio zostanie wyświetlony monit o wybranie zestawu domyślnych ustawień IDE dla podstawowego języka programowania. W przypadku niektórych języków domyślne ustawienia środowiska IDE mogą ukrywać niektóre polecenia debugera.  
  
 Jeśli chcesz użyć funkcji debugera, która jest ukryta przez domyślne ustawienia środowiska IDE, możesz dodać polecenie z powrotem do menu przy użyciu poniższej procedury.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Przywracanie ukrytych poleceń debugera  
  
1. Po otwarciu projektu, w menu **Narzędzia** , kliknij przycisk **Dostosuj**.  
  
2. W oknie dialogowym **Dostosowywanie** kliknij kartę **polecenia** .  
  
3. Na **pasku menu** wybierz menu **Debuguj** , które ma zawierać przywrócone polecenie.  
  
4. Kliknij **polecenie Dodaj...** Edytuj...  
  
5. W polu **Dodaj polecenie** wybierz polecenie, które chcesz dodać, a następnie kliknij przycisk **OK**.  
  
6. Powtórz poprzedni krok, aby dodać kolejne polecenie.  
  
7. Po zakończeniu dodawania poleceń do menu kliknij przycisk **Zamknij** .  
  
    > [!WARNING]
    > Niektóre elementy menu pojawiają się tylko wtedy, gdy debuger znajduje się w określonych trybach, takich jak tryb uruchamiania lub tryb przerwania. W związku z tym dodany element może nie być od razu widoczny po wykonaniu tych kroków.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Polecenia przywracania nie są dostępne z okna dialogowego Dostosowywanie  
 Niektórych poleceń, szczególnie tych, które znajdują się w menu hierarchicznych, nie można przywrócić z okna dialogowego **Dostosowywanie** . Aby przywrócić te polecenia, należy zaimportować nową kolekcję ustawień IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Aby zaimportować nowe ustawienia środowiska IDE  
  
1. W menu **Narzędzia** kliknij pozycję **Importuj i Eksportuj ustawienia**.  
  
2. Na stronie **Witamy w Kreatorze importowania i eksportowania ustawień** kliknij przycisk **Importuj wybrane ustawienia środowiska**, a następnie kliknij przycisk **dalej**.  
  
3. Na stronie **Zapisz bieżące ustawienia** Zdecyduj, czy zapisać istniejące ustawienia, a następnie kliknij przycisk **dalej**.  
  
4. Na stronie **Wybierz kolekcję ustawień do zaimportowania** w folderze **Ustawienia domyślne** wybierz kolekcję ustawień deweloperskich z poleceniami, które mają być używane. Jeśli nie wiesz, którą kolekcję wybrać, wypróbuj **Ogólne ustawienia deweloperskie** lub **Visual C++ ustawienia deweloperskie**, które udostępniają większość poleceń debugera.  
  
5. Kliknij przycisk **Dalej**.  
  
6. Na stronie **Wybierz ustawienia do zaimportowania** w obszarze **Opcje**upewnij się, że wybrano opcję **debugowanie** . Wyczyść inne pola wyboru, chyba że chcesz zaimportować te ustawienia.  
  
7. Kliknij przycisk **Zakończ**.  
  
8. Na stronie **Importowanie** zapoznaj się ze wszystkimi błędami związanymi z resetowaniem ustawień w obszarze **szczegóły**.  
  
9. Kliknij przycisk **Zamknij**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
