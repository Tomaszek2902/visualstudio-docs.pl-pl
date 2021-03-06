---
title: Korzystanie z sekwencji ucieczki w szablonach tekstu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659420"
---
# <a name="using-escape-sequences-in-text-templates"></a>Korzystanie z sekwencji unikowych w szablonach tekstowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą sekwencji unikowych w szablonach tekstowych można generować Tagi szablonu tekstu i (tylko w kodzie C#) do ucieczki znaków kontrolnych i cudzysłowów.

 Aby wydrukować otwarte i zamykające Tagi dla standardowego bloku kodu do pliku wyjściowego, należy wprowadzić znaczniki w następujący sposób:

```
\<# ... \#>
```

 Można to zrobić z innymi dyrektywami szablonu tekstu i tagami bloków kodu.

 Jeśli blok tekstu zawiera ciągi używane do ucieczki tagów szablonu tekstu, można użyć następujących sekwencji unikowych:

- Jeśli tag szablonu tekstu jest poprzedzony parzystą liczbą znaków ucieczki ( \\ ), Analizator szablonu będzie zawierał połowę znaków ucieczki i dołączył sekwencję jako tag szablonu tekstu. Na przykład jeśli w szablonie tekstu znajdują się cztery znaki ucieczki, w wygenerowanym pliku będą się znajdować dwa \\ znaki.

- Jeśli tag szablonu tekstu jest poprzedzony przez nieparzystą liczbę znaków ucieczki ( \\ ), Analizator szablonu będzie zawierał połowę \\ znaków "" i sam tag ( \<# or #> ). Tag nie jest traktowany jako tag szablonu tekstu.

- Jeśli znak ucieczki ( \\ ) pojawia się w dowolnym miejscu w dowolnej innej kolejności niż w przypadku ucieczki znaku kontrolnego lub cudzysłowu (tylko w języku C#), znak będzie wyprowadzany bezpośrednio.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
