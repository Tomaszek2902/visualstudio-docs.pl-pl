---
title: 'Instrukcje: Programowane otwieranie skoroszytów'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10a849d8545565e450cd099b32a9e3e8f7f11b56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537907"
---
# <a name="how-to-programmatically-open-workbooks"></a>Instrukcje: Programowane otwieranie skoroszytów
  <xref:Microsoft.Office.Interop.Excel.Workbooks>Kolekcja w programie Microsoft Office Excel umożliwia współpracę ze wszystkimi otwartymi skoroszytami i otwieranie skoroszytów.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Aby otworzyć istniejący skoroszyt

1. Użyj <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metody <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji, przekazując ścieżkę do skoroszytu.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład kodu wymaga następujących czynności:

- Skoroszyt o nazwie `YourWorkbook.xls` musi znajdować się w katalogu o nazwie `Test` na dysku C.

## <a name="see-also"></a>Zobacz też
- [Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)
- [Instrukcje: programowe otwieranie plików tekstowych jako skoroszytów](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Instrukcje: Programowane tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Instrukcje: programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)
- [Instrukcje: programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
