---
title: Wykonaj transformację XSLT
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e74beb2903cd133dfdd322ce4c297692eae3411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817193"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Instrukcje: wykonywanie transformacji XSLT z edytora XML

Edytor XML umożliwia kojarzenie arkusza stylów XSLT z dokumentem XML, wykonywanie transformacji i wyświetlanie danych wyjściowych. Wynikowe wyniki transformacji XSLT są wyświetlane w nowym oknie dokumentu.

Właściwość **Output** określa nazwę pliku dla danych wyjściowych. Jeśli właściwość **Output** jest pusta, nazwa pliku jest generowana w katalogu tymczasowym. Rozszerzenie pliku jest zależne od `xsl:output` elementu w arkuszu stylów i może być.* XML*,. *txt* lub. *htm*.

Jeśli właściwość **Output** określa nazwę pliku z. *htm* lub. rozszerzenie *HTML* , dane wyjściowe XSLT są przeglądane przy użyciu przeglądarki sieci Web. Wszystkie inne rozszerzenia plików są otwierane przy użyciu domyślnego edytora wybranego przez program Visual Studio. Na przykład, jeśli rozszerzenie pliku to. *XML*, program Visual Studio używa edytora XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Wykonaj transformację XSLT z pliku XML

1. Otwórz dokument XML w edytorze XML.

2. Skojarz arkusz stylów XSLT z dokumentem XML.

    - Dodaj `xml-stylesheet` instrukcję przetwarzania do dokumentu XML. Na przykład Dodaj następujący wiersz do prologu dokumentu: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -lub-

    - Dodaj arkusz stylów XSLT przy użyciu okna **Właściwości** . Gdy plik XML jest otwarty w edytorze, kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze i wybierz polecenie **Właściwości**. W oknie **Właściwości** kliknij pole **stylesheet** i wybierz przycisk Przeglądaj (...). Wybierz arkusz stylów XSLT, a następnie wybierz **Otwórz**.

3. Na pasku menu wybierz pozycję **XML**  >  **Rozpocznij XSLT bez debugowania**. Lub naciśnij **klawisze CTRL** + **Alt** + **F5**.

   Dane wyjściowe transformacji XSLT są wyświetlane w nowym oknie dokumentu.

   > [!NOTE]
   > Jeśli z dokumentem XML nie jest skojarzony żaden arkusz stylów, okno dialogowe wyświetli komunikat z prośbą o podanie arkusza stylów, który ma być używany.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Wykonaj transformację XSLT z arkusza stylów XSLT

1. Otwórz arkusz stylów XSLT w edytorze XML.

2. Określ dokument XML w polu **wejściowym** okna **Właściwości** dokumentu.

   > [!NOTE]
   > Dokument XML jest dokumentem wejściowym używanym do przekształcania. Jeśli dokument nie zostanie określony po rozpoczęciu transformacji XSLT, pojawi się okno dialogowe **Otwórz plik** , w którym można określić dokument w tym czasie.

3. Na pasku menu wybierz pozycję **XML**  >  **Rozpocznij XSLT bez debugowania**. Lub naciśnij **klawisze CTRL** + **Alt** + **F5**.

   Dane wyjściowe transformacji XSLT są wyświetlane w nowym oknie dokumentu.

## <a name="specify-an-output-file-name"></a>Określ nazwę pliku wyjściowego

Można określić nazwę pliku wyjściowego dla plików XML i XSL. Otwórz okno **Właściwości** i podaj nazwę pliku w polu **dane wyjściowe** .

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
