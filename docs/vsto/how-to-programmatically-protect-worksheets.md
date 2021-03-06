---
title: 'Instrukcje: programowe Włączanie ochrony arkuszy'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d51a6557b2204d7b6ff3d8865c82de091f5a59d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545902"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Instrukcje: programowe Włączanie ochrony arkuszy
  Funkcja ochrony w programie Microsoft Office Excel pomaga zapobiegać modyfikowaniu obiektów w arkuszu przez użytkowników i kod. Domyślnie wszystkie komórki są blokowane po włączeniu ochrony.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W przypadku dostosowań na poziomie dokumentu można chronić arkusze przy użyciu programu Excel Designer. Można również programowo chronić arkusz w czasie wykonywania w dowolnym typie projektu.

> [!NOTE]
> Nie można dodać formantów Windows Forms do obszarów arkusza, które są chronione.

## <a name="use-the-designer"></a>Korzystanie z projektanta

### <a name="to-protect-a-worksheet-in-the-designer"></a>Aby chronić arkusz w projektancie

1. W grupie **zmiany** na karcie **Przegląd** kliknij pozycję **Chroń arkusz**.

    Zostanie wyświetlone okno dialogowe **Ochrona arkusza** . Można ustawić hasło i opcjonalnie określić pewne akcje, które użytkownicy mogą wykonywać w arkuszu, takie jak formatowanie komórek lub wstawianie wierszy.

   Możesz również umożliwić użytkownikom edytowanie określonych zakresów w chronionych arkuszach.

### <a name="to-allow-editing-in-specific-ranges"></a>Aby zezwolić na edytowanie w określonych zakresach

1. W grupie **zmiany** na karcie **Przegląd** kliknij pozycję **zezwól użytkownikom na edytowanie zakresów**.

     Zostanie wyświetlone okno dialogowe **Zezwalaj użytkownikom na edytowanie zakresów** . Można określić zakresy, które są odblokowane przy użyciu hasła, oraz użytkowników, którzy mogą edytować zakresy bez hasła.

## <a name="use-code-at-run-time"></a>Użyj kodu w czasie wykonywania
 Poniższy kod ustawia hasło (przy użyciu zmiennej getPasswordFromUser, która zawiera hasło uzyskane od użytkownika) i umożliwia tylko sortowanie.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Aby chronić arkusz przy użyciu kodu w dostosowaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metodę arkusza. W tym przykładzie założono, że pracujesz z arkuszem o nazwie `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Aby chronić arkusz przy użyciu kodu w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> metodę aktywnego arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowane usuwanie ochrony z arkuszy](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Instrukcje: programowane włączanie ochrony skoroszytów](../vsto/how-to-programmatically-protect-workbooks.md)
- [Instrukcje: programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
