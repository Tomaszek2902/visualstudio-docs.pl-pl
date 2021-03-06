---
title: Find — pole polecenia
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591531"
---
# <a name="findcommand-box"></a>Find/Command — Pole

Możesz wyszukiwać tekst i uruchamiać polecenia programu Visual Studio z poziomu pola **Znajdź/polecenie** . Pole **Znajdź/polecenie** jest nadal dostępne jako kontrolka paska narzędzi, ale nie jest już widoczne domyślnie. Możesz wyświetlić okno **Znajdź/polecenie** , wybierając pozycję **Dodaj lub usuń przyciski** na pasku narzędzi **Standardowy** , a następnie wybierając pozycję **Znajdź**.

Aby uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenie, należy je **>** oznakować znakiem większym niż ().

Okno **Znajdź/polecenie** zachowuje ostatnie 20 wprowadzonych elementów i wyświetla je na liście rozwijanej. Możesz przechodzić przez listę, wybierając **klawisze strzałek**.

![Znajdź&#47;pole polecenia](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Wyszukiwanie tekstu

Domyślnie po określeniu tekstu w polu **Znajdź/polecenie** , a następnie wybraniu klawisza **Enter** , program Visual Studio przeszukuje bieżący dokument lub okno narzędzia przy użyciu opcji określonych w oknie dialogowym **Znajdź w plikach** . Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Wprowadzanie poleceń

Aby użyć pola **Znajdź/polecenie** do wystawienia pojedynczego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenia lub aliasu zamiast wyszukiwania tekstu, należy poprzedzić polecenie znakiem większym niż ( **>** ). Na przykład:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatywnie można także użyć okna **polecenia** do wprowadzania i wykonywania pojedynczych lub wielu poleceń. Niektóre polecenia lub aliasy mogą być wprowadzane i wykonywane samodzielnie; inne osoby mają wymagane argumenty w składni. Aby zapoznać się z listą poleceń, które mają argumenty, zobacz [Visual Studio Commands](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Znaki ucieczki

Znak daszka ( **^** ) w poleceniu oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Można go użyć do osadzenia prostych cudzysłowów (**"**), spacji, ukośników wiodących, karetki lub innych znaków literału w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład:

```
>Edit.Find ^^t /regex
```

Daszek działa tak samo, niezależnie od tego, czy znajduje się wewnątrz, czy poza cudzysłowem. Jeśli karetka jest ostatnim znakiem w wierszu, zostanie zignorowana.

## <a name="see-also"></a>Zobacz też

- [Okno polecenia](../ide/reference/command-window.md)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
