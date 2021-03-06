---
title: Opcje, Projektant formularzy systemu Windows, Dostosowywanie interfejsu użytkownika danych
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e48777a50ddf66a8e5493698fb401ff7201de03e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114691"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Opcje — okno dialogowe: Projektant formularzy systemu Windows > dostosowywania interfejsu użytkownika danych

To okno dialogowe definiuje, które kontrolki są wyświetlane na liście dostępnych kontrolek dla elementów w oknie źródła danych. Aby go otworzyć, wybierz pozycję **Narzędzia**  >  **Opcje**, a następnie wybierz pozycję **Projektant formularzy systemu Windows**  >  **Dostosowywanie interfejsu użytkownika danych**.

Możesz wybrać formant z elementu w oknie źródła danych przed przeciągnięciem go do formularza w aplikacji Windows Forms. Dostępne kontrolki są określane przez typ danych elementu. Każdy typ danych ma listę prawidłowych skojarzonych kontrolek zdefiniowanych w tym oknie dialogowym, w tym kontrolki domyślnej. Po przeciągnięciu elementu z okna źródła danych na formularz bez wybierania kontrolki w formularzu zostanie dodany domyślny formant dla typu danych wybranego elementu.

Dostosuj listę skojarzonych kontrolek, zaznaczając i czyszcząc pola wyboru dostępnych kontrolek dla każdego typu danych. Aby dodać kontrolkę do listy, Dodaj kontrolkę, która implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute> <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> atrybut lub powiązania danych do przybornika. Kontrolka zostanie następnie wyświetlona na liście kontrolek dla tego typu danych. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowych kontrolek do okna źródła danych](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Typ danych

Wyświetla listę typów, z którymi są skojarzone formanty. Tabele są reprezentowane jako `[List]` Typ danych. Kolumny są reprezentowane jako rzeczywisty typ danych kolumny w źródłowym magazynie danych.

## <a name="associated-controls"></a>Skojarzone kontrolki

Wyświetla listę formantów, które są skojarzone z wybranym typem danych. Zaznacz lub usuń zaznaczenie pola wyboru obok kontrolki, aby skojarzyć lub usunąć jego skojarzenie. Wybrane kontrolki pojawiają się w oknie źródła danych dla kolumny bazy danych powiązanej z skojarzonym typem danych.

## <a name="set-default"></a>Ustaw Domyślne

Przypisuje wybrany typ kontrolki jako domyślny dla wybranego typu danych. Kontrolka domyślna jest wyświetlana jako pierwszy wybór w menu skrótów kolumny bazy danych w oknie źródła danych. Po przeciągnięciu elementu z okna źródła danych na formularz bez wybierania kontrolki w formularzu zostanie dodany domyślny formant dla typu danych wybranego elementu.

Tylko jeden typ kontrolki może być przypisany jako domyślny dla typu danych.

## <a name="clear-default"></a>Wyczyść domyślne

Usuwa oznaczenie formantu jako domyślny dla wybranego typu danych. Jeśli nie ma wartości domyślnej dla wybranego typu danych, `[None]` pojawia się jako pierwszy wybór w menu skrótów dla kolumny bazy danych tego typu.
