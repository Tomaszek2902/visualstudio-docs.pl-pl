---
title: Projektuj Windows Forms aplikacje
ms.date: 08/09/2019
ms.topic: overview
helpviewer_keywords:
- Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 03619582a30893c161c44c880a0d9cf6c9766d0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768759"
---
# <a name="windows-forms-designer-overview"></a>Projektant formularzy systemu Windows — omówienie

Projektant formularzy systemu Windows w programie Visual Studio oferuje szybkie rozwiązanie programistyczne do tworzenia aplikacji opartych na Windows Forms. Projektant formularzy systemu Windows pozwala łatwo dodawać kontrolki do formularza, rozmieścić je i pisać kod dla swoich zdarzeń. Aby uzyskać więcej informacji na temat Windows Forms, zobacz [Windows Forms Omówienie](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Funkcja

Za pomocą projektanta można:

- Dodawanie składników, kontrolek danych lub formantów opartych na systemie Windows do formularza.

- Kliknij dwukrotnie formularz w Projektancie i napisz kod w `Load` zdarzeniu dla tego formularza lub kliknij dwukrotnie formant w formularzu i napisz kod dla zdarzenia domyślnego formantu.

- Edytuj właściwość Text kontrolki, zaznaczając kontrolkę i wpisując nazwę.

- Dostosuj położenie zaznaczonego formantu, przenosząc je za pomocą myszy lub klawiszy strzałek. Podobnie Dostosuj umieszczanie przy użyciu klawiszy CTRL i strzałki. Na koniec Dostosuj rozmiar formantu przy użyciu klawiszy Shift i strzałka.

- Zaznacz opcję wiele kontrolek, wybierając **klawisz Shift** lub **Ctrl** po kliknięciu przycisku. W przypadku używania pojedynczo **SHIFT**+ kliknięcie pierwszy wybrany formant jest formantem dominującym podczas wyrównywania lub manipulowania rozmiarem. W przypadku korzystania z **kombinacji klawiszy CTRL**i kliknięcia Ostatnia wybrana kontrolka ma wartość dominującą, więc formant dominujący zmienia się z każdą dodaną nową kontrolką. Alternatywnie można wybrać wiele kontrolek, przeciągając prostokąt zaznaczenia wokół kontrolek, które chcesz wybrać.

> [!NOTE]
> Użyj Projektant formularzy systemu Windows, a nie edytora zasobów, aby wprowadzić zmiany w pliku zasobów formularza (*. resx*). Jeśli edytujesz plik resx oparty na formularzu, zobaczysz ostrzeżenie, że zmiany wprowadzone w edytorze zasobów mogą zostać utracone. Dzieje się tak, ponieważ Projektant formularzy systemu Windows generuje plik resx.

## <a name="see-also"></a>Zobacz też

- [Przegląd Windows Forms](/dotnet/framework/winforms/windows-forms-overview)
- [formanty Formularzy systemu Windows](/dotnet/framework/winforms/controls/)
- [Dane wejściowe użytkownika w Windows Forms](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Powiązanie danych w Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
- [Ulepszanie aplikacji Windows Forms](/dotnet/framework/winforms/advanced/)
- <xref:System.Windows.Forms?displayProperty=fullName> Dokumentacja interfejsu API
