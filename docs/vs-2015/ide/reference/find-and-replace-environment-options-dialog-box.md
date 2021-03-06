---
title: Znajdź i Zamień, środowisko, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.FindReplace
- VS.ToolsOptionsPages.Environment.FindandReplace
helpviewer_keywords:
- Find and Replace, Options dialog box
- Find and Replace, customizing
ms.assetid: f804d6d5-6309-46e4-8294-b83e880b5ec9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c17b25d8a837f751b8bd8ec108c0b821d58c6df0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657699"
---
# <a name="find-and-replace-environment-options-dialog-box"></a>Znajdź i zamień, Środowisko, Opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta strona okna dialogowego **Opcje** służy do kontrolowania pól komunikatów i innych aspektów operacji znajdowania i zamieniania. Możesz uzyskać dostęp do tego okna dialogowego z menu **Narzędzia** , klikając **Opcje**, rozwijając **środowisko**, a następnie klikając przycisk **Znajdź i Zamień**. Jeśli ta strona nie jest wyświetlana na liście, wybierz pozycję **Pokaż wszystkie ustawienia** w oknie dialogowym **Opcje** .

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="uielement-list"></a>Lista elementów UI
 **Wyświetl komunikaty informacyjne** Wybierz tę opcję, aby wyświetlić wszystkie komunikaty informacyjne Znajdź i Zastąp, które mają opcję **Zawsze pokazuj tę wiadomość** . Jeśli na przykład nie zostanie wyświetlony komunikat "Znajdź osiągnął punkt początkowy wyszukiwania", wybranie tej opcji spowoduje, że ten komunikat informacyjny będzie wyświetlany ponownie, gdy użyjesz polecenia Znajdź i Zamień.

 Jeśli nie chcesz wyświetlać żadnych komunikatów informacyjnych dla Znajdź i Zamień, wyczyść tę opcję.

 Po wyczyszczeniu opcji **Zawsze pokazuj ten komunikat** na niektórych, ale nie wszystkich, **Znajdź i Zastąp** komunikaty informacyjne, pole wyboru **Wyświetlaj komunikaty informacyjne** wydaje się być wypełnione, ale nie zaznaczone. Aby przywrócić wszystkie opcjonalne komunikaty **Znajdź i Zamień** , usuń zaznaczenie tej opcji, a następnie wybierz ją ponownie.

> [!NOTE]
> Ta opcja nie ma wpływu na żadne komunikaty informacyjne **znajdowania i zastępowania** , które nie wyświetlają opcji **Zawsze pokazuj ten komunikat** .

 **Wyświetlanie komunikatów ostrzegawczych** Wybierz tę opcję, aby wyświetlić wszystkie ostrzeżenia dotyczące znajdowania i zamieniania, które mają opcję **Zawsze pokazuj tę wiadomość** . Jeśli na przykład nie zostanie wyświetlony komunikat **Zamień wszystkie** ostrzeżenia, który pojawia się podczas próby przeprowadzenia zamian w plikach, które nie są aktualnie otwarte do edycji, wybranie tej opcji spowoduje, że ten komunikat ostrzegawczy zostanie wyświetlony ponownie podczas próby zamiany wszystkich.

 Jeśli nie chcesz wyświetlać żadnych komunikatów ostrzegawczych dotyczących znajdowania i zastępowania, usuń zaznaczenie tej opcji.

 Po wyczyszczeniu opcji **Zawsze pokazuj ten komunikat** na niektórych, ale nie wszystkich, **Znajdź i Zamień** komunikaty ostrzegawcze, pole wyboru **Wyświetlaj komunikaty ostrzegawcze** wydaje się być wypełnione, ale nie zaznaczone. Aby przywrócić wszystkie opcjonalne komunikaty **Znajdź i Zamień** , usuń zaznaczenie tej opcji, a następnie wybierz ją ponownie.

> [!NOTE]
> Ta opcja nie ma wpływu na żadne komunikaty ostrzegawcze **Znajdź i Zamień** , które nie wyświetlają opcji **Zawsze pokazuj ten komunikat** .

 **Automatycznie Wypełnij wyszukiwanie tekstu z edytora** Zaznacz tę opcję, aby wkleić tekst po obu stronach punktu wstawiania bieżącego edytora do pola **Znajdź co** w przypadku wybrania dowolnego widoku okna **Znajdź i Zamień** w menu **Edycja** . Usuń zaznaczenie tej opcji, aby użyć ostatniego wzorca wyszukiwania z poprzedniego wyszukiwania jako **Znajdź** ciąg.

## <a name="see-also"></a>Zobacz też
 [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
