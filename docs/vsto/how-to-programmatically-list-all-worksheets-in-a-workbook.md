---
title: 'Instrukcje: programowe Wyświetlanie listy wszystkich arkuszy w skoroszycie'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b3132ee83d4752c0bc2f053e7c65e3c7b84831b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585174"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Instrukcje: programowe Wyświetlanie listy wszystkich arkuszy w skoroszycie
  <xref:Microsoft.Office.Interop.Excel.Workbook>Klasa udostępnia <xref:Microsoft.Office.Interop.Excel.Worksheets> obiekt. Ten obiekt zawiera kolekcję wszystkich <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektów w skoroszycie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Aby wyświetlić listę wszystkich istniejących arkuszy w skoroszycie w dostosowaniu na poziomie dokumentu

1. Wykonaj iterację <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji i Wyślij nazwę każdego arkusza do komórki przesuniętej od <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu.

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Aby wyświetlić listę wszystkich istniejących arkuszy w skoroszycie w dodatku narzędzi VSTO

1. Wykonaj iterację <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji i Wyślij nazwę każdego arkusza do komórki przesuniętej z <xref:Microsoft.Office.Interop.Excel.Range> obiektu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowane dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Instrukcje: Programowane przenoszenie arkuszy w skoroszytach](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
