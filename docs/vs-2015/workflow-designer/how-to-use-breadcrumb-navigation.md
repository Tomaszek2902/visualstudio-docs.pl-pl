---
title: 'Instrukcje: korzystanie z nawigacji z nawigacją | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c01e48e6aa34513e57b373150c605cb0a7f5b18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659153"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Instrukcje: Używanie nawigacji za pomocą linków do stron nadrzędnych
Istnieją trzy podstawowe sposoby zmiany zestawu działań, które są wyświetlane w programie [!INCLUDE[wfd1](../includes/wfd1-md.md)] :

1. Kliknij dwukrotnie, aby przejść do działania podrzędnego.

2. Kliknij przycisk na pasku nawigacyjnym, aby przejść do działania nadrzędnego.

3. Rozwiń lub Zwiń działania na miejscu.

### <a name="using-breadcrumb-navigation"></a>Używanie nawigacji ze stron nadrzędnych

1. Kliknij dwukrotnie działanie, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Aby zmienić działanie elementu głównego na kliknięte działanie. Kliknięte działanie jest następnie w pełni rozwinięte w katalogu głównym, a jego elementy nadrzędne są wyświetlane na pasku nawigacyjnym. Jest to czasami nazywane drążeniem do lub z działania.

2. Aby przejść do elementu nadrzędnego bieżącego działania głównego, kliknij działanie na pasku nawigacyjnym.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Rozwijanie lub zwijanie działania w miejscu

1. Kliknięcie cudzysłowów w działaniu rozszerza lub zwija działanie na miejscu.

2. Gdy stan rozwinięcia zostanie zmieniony przez kliknięcie przycisku, nowy stan rozwinięcia zostanie zapisany w języku XAML.

    > [!WARNING]
    > Nie wszystkie działania mogą być rozwinięte. Istnieją dwa przypadki, w których działanie nie może być rozwinięte: element nadrzędny działania nie zezwala na rozszerzanie jego elementów podrzędnych, (na przykład działania w schemacie blokowym nie mogą być rozwinięte) lub Projektant działań nie zezwala na rozszerzanie się w miejscu. Chociaż żaden z projektantów działań nie uwzględnionych w programie [!INCLUDE[wfd2](../includes/wfd2-md.md)] ma takie samo zachowanie, niektóre działania niestandardowe mogą spowodować takie zachowanie.

### <a name="expanding-all-or-collapsing-all-activities"></a>Rozwijanie wszystkich lub zwijanie wszystkich działań

1. Użyj przycisków **Rozwiń wszystko** i **Zwiń wszystkie** w interfejsie użytkownika, aby rozwinąć lub zwinąć wszystkie działania w ramach bieżącego katalogu głównego. Należy pamiętać, że Rozwiń wszystkie i Zwiń wszystkie są stanami globalnymi. Oznacza to, że po zmianie działania głównego przy użyciu nawigacji nawigacyjnej cały stan rozwiń wszystko lub Zwiń wszystko do momentu kliknięcia opcji **Przywróć**.

2. Po zastosowaniu stanu rozwiń wszystko lub Zwiń wszystko można kliknąć przycisk **Przywróć** , który pojawia się z powrotem do przeglądania stanu poprzednio zastosowanego do poszczególnych działań.

    > [!WARNING]
    > Jeśli działanie, takie jak <xref:System.Activities.Statements.Flowchart> , wybrało rozwinięte miejsce, funkcjonalność skojarzona z przyciskami **Rozwiń wszystko** i **Zwiń wszystko** jest wyłączona w projektancie **schematów blokowych** . [!INCLUDE[crabout](../includes/crabout-md.md)] Projektant **schematów blokowych** , zobacz temat [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > Rozszerzenie ALL ma również szczególny efekt w projektantach działań **Switch** i **TryCatch** . Po kliknięciu przycisku **Rozwiń wszystko**wszystkie przypadki przełączania i wszystkie bloki try/catch/finally są wyświetlane. Kliknięcie przycisku **Przywróć** lub **Zwiń wszystko** zwraca tych projektantów do ich domyślnego stanu, z którego można kliknąć pojedynczy przypadek/blok, aby wyświetlić jego zawartość.