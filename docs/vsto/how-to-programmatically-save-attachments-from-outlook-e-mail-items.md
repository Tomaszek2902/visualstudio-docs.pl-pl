---
title: Programowo Zapisuj załączniki z elementów poczty e-mail programu Outlook
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3ade05e936397f72a0b370cb69d8be3310c3aee8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584771"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Instrukcje: programowe zapisywanie załączników z elementów poczty e-mail programu Outlook

Ten przykład zapisuje załączniki wiadomości e-mail do określonego folderu po odebraniu wiadomości w skrzynce odbiorczej.

> [!IMPORTANT]
> Ten przykład działa tylko w przypadku dodania folderu o nazwie **TestFileSave** w katalogu głównym katalogu C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz też

- [Pracuj z elementami poczty](../vsto/working-with-mail-items.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowane wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Instrukcje: programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
