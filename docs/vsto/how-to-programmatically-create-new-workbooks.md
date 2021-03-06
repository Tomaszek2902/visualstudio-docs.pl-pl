---
title: 'Instrukcje: Programowane tworzenie nowych skoroszytów'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a23f4b089d580d482193d278f22e4990d343097
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545980"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Instrukcje: Programowane tworzenie nowych skoroszytów
  Gdy tworzysz skoroszyt programowo, jest to obiekt macierzysty <xref:Microsoft.Office.Interop.Excel.Workbook> , a nie <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Można wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta dla <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu w projekcie dodatku VSTO. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Aby utworzyć nowy skoroszyt

1. Użyj <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji.

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Można utworzyć skoroszyt oparty na szablonie innym niż szablon domyślny: Przekaż szablon, którego chcesz użyć jako parametru do <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metody.

## <a name="see-also"></a>Zobacz też
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)
- [Instrukcje: Programowane otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md)
- [Instrukcje: programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)
- [Instrukcje: programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
