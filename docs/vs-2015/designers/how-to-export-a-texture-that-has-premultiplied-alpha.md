---
title: 'Instrukcje: eksportowanie tekstury z wstępnie przemnożoną alfa | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 452048a512a9e2f8d4d44d5db99cc005c0dac55c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664424"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Porady: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Potok zawartości obrazu może generować wstępnie przemnożone tekstury alfa z obrazu źródłowego. Te funkcje mogą być prostsze i bardziej niezawodne niż tekstury, które nie zawierają wstępnie przemnożonego kanału alfa.

 W tym dokumencie przedstawiono następujące działania:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzany przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu w celu wygenerowania wstępnie przemnożonego kanału alfa.

## <a name="premultiplied-alpha"></a>Wstępnie przemnożone alfa
 Wstępnie przemnożony kanał alfa oferuje kilka korzyści w porównaniu do konwencjonalnych, niewstępnie przemnożonych alfa, ponieważ lepiej reprezentuje rzeczywistą interakcję z materiałami fizycznymi, oddzielając Texel od koloru (kolor, który został dodany do sceny) od jego przezroczystości (ilość koloru bazowego, który umożliwia). Niektóre zalety korzystania z wstępnie przemnożonego kanału alfa są następujące:

- Mieszanie ze wstępnie przemnożonym alfa jest operacją asocjacyjną; wynik mieszania wielu przezroczystych tekstur jest taki sam, niezależnie od kolejności, w jakiej tekstury są mieszane.

- Ze względu na asocjacyjny charakter mieszania przy użyciu wstępnie przemnożonego kanału alfa jest uproszczone renderowanie wielu przebiegów przezroczystych obiektów.

- Za pomocą wstępnie przemnożonego kanału alfa, zarówno czysta mieszanie addytywne (poprzez ustawienie alfa na zero), jak i liniowo interpolowane mieszanie można osiągnąć jednocześnie. Na przykład w systemie cząsteczek, dostosowana mieszanina ognia może stać się przezroczystą cząstką dym, która jest zmieszana przy użyciu interpolacji liniowej. Bez wstępnie przemnożonego kanału alfa należy narysować cząstki pożarowe niezależnie od cząstek dymu i zmodyfikować stan renderowania między wywołaniami rysowania.

- Tekstury używające wstępnie przemnożonej kompresji alfa o wyższej jakości niż te, które nie są i nie wykazują odbarwnych krawędzi — lub "efektu otoczki", które mogą wynikać z mieszania tekstur, które nie używają wstępnie przemnożonego kanału alfa.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Aby utworzyć teksturę, która używa wstępnie przemnożonego kanału alfa

1. Zacznij od tekstury podstawowej. Załaduj istniejący plik obrazu lub utwórz go zgodnie z opisem w temacie [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md).

2. Skonfiguruj plik tekstury w taki sposób, aby był przetwarzany przez potok zawartości obrazu. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Właściwości konfiguracji**, **Ogólne** ustaw właściwość **Typ elementu** na **potok zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **wartość Yes (tak** ), **Wyklucz z kompilacji** jest ustawiony na **nie**, a następnie wybierz przycisk **Zastosuj** . Zostanie wyświetlona strona właściwości konfiguracja **potoku zawartości obrazu** .

3. Skonfiguruj potok zawartości obrazu w celu wygenerowania wstępnie przemnożonego kanału alfa. Na stronie **Właściwości konfiguracji**, **potok zawartości obrazu**, **Ogólne** ustaw właściwość **Konwertuj na wstępnie przemnożony format alfa** na **wartość tak (/generatepremultipliedalpha)**.

4. Wybierz przycisk **OK** .

   Podczas kompilowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś — obejmuje to konwersję obrazu na wstępnie przemnożony format alfa, a wynik jest kopiowany do katalogu wyjściowego projektu.
