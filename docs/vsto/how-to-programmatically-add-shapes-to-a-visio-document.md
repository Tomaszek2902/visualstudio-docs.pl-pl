---
title: 'Instrukcje: Programowane dodawanie kształtów do dokumentu programu Visio'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8eb3ad837f699a1bb0bbc327b6e892a20866e0a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584233"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Instrukcje: Programowane dodawanie kształtów do dokumentu programu Visio
  Możesz dodać kształty do dokumentu programu Microsoft Office Visio, pobierając wzorce z wzornika i upuszczając kształty na aktywnej stronie.

 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną języka VBA dla [Microsoft.Office.Interop.Visio.Documents. Dodaj](/office/vba/api/Visio.Documents.Add) metodę, właściwość [Microsoft. Office. Interop. Visio. Application. ActivePage](/office/vba/api/Visio.Application.ActivePage) oraz [Microsoft. Office. Interop. Visio. Page. Drop](/office/vba/api/Visio.Page.Drop) .

## <a name="add-shapes-to-a-visio-document"></a>Dodawanie kształtów do dokumentu programu Visio

### <a name="to-add-shapes-to-a-visio-document"></a>Aby dodać kształty do dokumentu programu Visio

- Gdy dokument jest aktywny, Pobierz wzorce z kolekcji Documents. Masters i upuść je w aktywnym dokumencie. Można pobrać wzorzec przy użyciu indeksu lub nazwy głównej.

     Poniższy przykład kodu tworzy pusty dokument programu Visio, a następnie otwiera go z wzornikem **podstawowe kształty** zadokowane. Następnie kod pobiera kilka kształtów i opuszcza je na aktywnej stronie.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Współpraca z kształtami programu Visio](../vsto/working-with-visio-shapes.md)
- [Instrukcje: Programowane kopiowanie i wklejanie kształtów w dokumencie programu Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
