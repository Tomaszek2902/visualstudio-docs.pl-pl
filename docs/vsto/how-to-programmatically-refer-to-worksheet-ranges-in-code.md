---
title: 'Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 319be5ad6c878e08a862d1e20e826c2800c33512
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584836"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie
  Podobny proces służy do odwoływania się do zawartości <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Korzystanie z kontrolki NamedRange
 Poniższy przykład dodaje <xref:Microsoft.Office.Tools.Excel.NamedRange> do arkusza, a następnie dodaje tekst do komórki w zakresie.

### <a name="to-refer-to-a-namedrange-control"></a>Aby odwołać się do kontrolki NamedRange

1. Przypisz ciąg do <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Użyj natywnych zakresów programu Excel
 Poniższy przykład dodaje natywny zakres programu Excel do arkusza, a następnie dodaje tekst do komórki w zakresie.

### <a name="to-refer-to-a-native-range-object"></a>Aby odwołać się do natywnego obiektu zakresu

1. Przypisz ciąg do <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> Właściwości zakresu.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z zakresami](../vsto/working-with-ranges.md)
- [Instrukcje: Programowane sprawdzanie pisowni w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Instrukcje: Programowane automatyczne wypełnianie zakresów przyrostowo zmieniającymi się danymi](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Instrukcje: programowe wyszukiwanie tekstu w zakresach arkusza](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
