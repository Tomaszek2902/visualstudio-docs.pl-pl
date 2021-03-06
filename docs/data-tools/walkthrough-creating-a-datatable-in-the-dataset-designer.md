---
title: Tworzenie elementu DataTable w Projektant obiektów Dataset
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7dd762c6df5eebc9ebbf142a3ad7dfe430800802
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036772"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Przewodnik: Tworzenie elementu DataTable w Projektant obiektów Dataset

W tym instruktażu wyjaśniono, jak utworzyć <xref:System.Data.DataTable> (bez TableAdapter) przy użyciu **Projektant obiektów DataSet**. Aby uzyskać informacje na temat tworzenia tabel danych zawierających TableAdapters, zobacz [Create and configure TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Utwórz nową aplikację Windows Forms

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **DataTableWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **DataTableWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-new-dataset-to-the-application"></a>Dodawanie nowego zestawu danych do aplikacji

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W okienku po lewej stronie wybierz pozycję **dane**, a następnie wybierz pozycję **zestaw danych** w środkowym okienku.

3. Wybierz pozycję **Dodaj**.

     Program Visual Studio dodaje plik o nazwie **pozycję DataSet1. xsd** do projektu i otwiera go w **Projektant obiektów DataSet**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Dodawanie nowej tabeli DataTable do zestawu danych

1. Przeciągnij element **DataTable** z karty **zestaw danych** **przybornika** na **Projektant obiektów DataSet**.

     Tabela o nazwie **datatabela1** jest dodawana do zestawu danych.

2. Kliknij pasek tytułu elementu **datatabela1** i zmień jego nazwę `Music` .

## <a name="add-columns-to-the-datatable"></a>Dodawanie kolumn do tabeli DataTable

1. Kliknij prawym przyciskiem myszy tabelę **muzyka** . Wskaż polecenie **Dodaj**, a następnie kliknij pozycję **kolumna**.

2. Nadaj nazwę kolumnie `SongID` .

3. W oknie **Właściwości** Ustaw <xref:System.Data.DataColumn.DataType%2A> Właściwość na <xref:System.Int16?displayProperty=fullName> .

4. Powtórz ten proces i Dodaj następujące kolumny:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Ustaw klucz podstawowy dla tabeli

Wszystkie tabele danych powinny mieć klucz podstawowy. Klucz podstawowy jednoznacznie identyfikuje konkretny rekord w tabeli danych.

Aby ustawić klucz podstawowy, kliknij prawym przyciskiem myszy kolumnę **SongID** , a następnie kliknij pozycję **Ustaw klucz podstawowy**. Obok kolumny **SongID** pojawia się ikona klucza.

## <a name="save-your-project"></a>Zapisz projekt

Aby zapisać projekt **DataTableWalkthrough** , w menu **plik** wybierz polecenie **Zapisz wszystko**.

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)
