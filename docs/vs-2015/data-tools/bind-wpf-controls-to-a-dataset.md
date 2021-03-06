---
title: Powiązywanie formantów WPF z zestawem danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 937e28e923c26a72940b0181da16cf34199bb9aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852159"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Powiązywanie kontrolek WPF z zestawem danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu utworzysz aplikację WPF, która zawiera kontrolki powiązane z danymi. Formanty są powiązane z rekordami produktów, które są hermetyzowane w zestawie danych. Dodasz również przyciski umożliwiające przeglądanie produktów i zapisywanie zmian w rekordach produktów.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie aplikacji WPF i zestawu danych, który jest generowany na podstawie danych z przykładowej bazy danych AdventureWorksLT.

- Tworzenie zestawu formantów powiązanych z danymi przez przeciąganie tabeli danych z okna **źródła danych** do okna w projektancie WPF.

- Tworzenie przycisków umożliwiających nawigowanie do przodu i do tyłu za poorednictwem rekordów produktów.

- Tworzenie przycisku, który zapisuje zmiany wprowadzane przez użytkowników w rekordach produktu do tabeli danych i bazowego źródła danych.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Dostęp do uruchomionego wystąpienia SQL Server lub SQL Server Express z dołączoną przykładową bazą danych AdventureWorksLT. Bazę danych AdventureWorksLT można pobrać z [witryny sieci Web CodePlex](https://codeplex.com/SqlServerSamples).

  Wcześniejsza znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończenia przewodnika:

- Zestawy danych i TableAdapters. Aby uzyskać więcej informacji, zobacz [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Praca z projektantem WPF. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia WPF i Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-project"></a>Tworzenie projektu
 Utwórz nowy projekt WPF. Projekt będzie wyświetlał rekordy produktów.

#### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. Rozwiń węzeł **Visual Basic** lub **Visual C#**, a następnie wybierz pozycję **Windows**.

4. Wybierz szablon projektu **aplikacji WPF** .

5. W polu **Nazwa** wpisz `AdventureWorksProductsEditor` i kliknij przycisk **OK**.

     Program Visual Studio tworzy `AdventureWorksProductsEditor` projekt.

## <a name="create-a-dataset-for-the-application"></a>Tworzenie zestawu danych dla aplikacji
 Aby można było tworzyć kontrolki powiązane z danymi, należy zdefiniować model danych dla aplikacji i dodać go do okna **źródła danych** . W tym instruktażu utworzysz zestaw danych, który będzie używany jako model danych.

#### <a name="to-create-a-dataset"></a>Aby utworzyć zestaw danych

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

     Zostanie otwarte okno **źródła danych** .

2. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

     Zostanie otwarty Kreator **konfiguracji źródła danych** .

3. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz model bazy danych** wybierz pozycję **zestaw danych**, a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wybierz jedną z następujących opcji:

    - Jeśli połączenie danych z przykładową bazą danych AdventureWorksLT jest dostępne na liście rozwijanej, wybierz ją, a następnie kliknij przycisk **dalej**.

    - Kliknij pozycję **nowe połączenie**i Utwórz połączenie z bazą danych AdventureWorksLT.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** zaznacz pole wyboru **tak, Zapisz połączenie jako** , a następnie kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele**, a następnie wybierz tabelę **Product (tabeli SalesLT)** .

8. Kliknij przycisk **Zakończ**.

     Program Visual Studio dodaje nowy plik XSD AdventureWorksLTDataSet do projektu i dodaje odpowiadający element **AdventureWorksLTDataSet** do okna **źródła danych** . Plik AdventureWorksLTDataSet. xsd definiuje określony zestaw danych o nazwie `AdventureWorksLTDataSet` i TableAdapter o nazwie `ProductTableAdapter` . W dalszej części tego instruktażu zostanie użyta funkcja `ProductTableAdapter` do wypełnienia zestawu danych danymi i zapisania zmian z powrotem w bazie danych.

9. Skompiluj projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Edytuj domyślną metodę Fill elementu TableAdapter
 Aby wypełnić zestaw danych danymi, użyj `Fill` metody `ProductTableAdapter` . Domyślnie `Fill` Metoda wypełnia `ProductDataTable` w programie `AdventureWorksLTDataSet` wszystkie wiersze danych z tabeli Product. Możesz zmodyfikować tę metodę, aby zwrócić tylko podzestaw wierszy. W tym instruktażu zmodyfikuj `Fill` metodę, aby zwracała tylko wiersze dla produktów mających zdjęcia.

#### <a name="to-load-product-rows-that-have-photos"></a>Aby załadować wiersze produktu z fotografiami

1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik AdventureWorksLTDataSet. xsd.

     Zostanie otwarty projektant obiektów DataSet.

2. W projektancie kliknij prawym przyciskiem myszy zapytanie **wypełnienie, GetData ()** i wybierz pozycję **Konfiguruj**.

     Zostanie otwarty Kreator **konfiguracji TableAdapter** .

3. Na stronie **wprowadzanie instrukcji SQL** Dodaj następującą klauzulę WHERE po `SELECT` instrukcji w polu tekstowym.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Kliknij przycisk **Zakończ**.

## <a name="define-the-user-interface"></a>Zdefiniuj interfejs użytkownika
 Dodaj kilka przycisków do okna, modyfikując kod XAML w projektancie WPF. W dalszej części tego instruktażu zostanie dodany kod umożliwiający użytkownikom przewijanie i zapisywanie zmian w rekordach produktów przy użyciu tych przycisków.

#### <a name="to-define-the-user-interface-of-the-window"></a>Aby zdefiniować interfejs użytkownika okna

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję MainWindow. XAML.

     Okno zostanie otwarte w projektancie WPF.

2. W [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] widoku projektanta Dodaj następujący kod między `<Grid>` tagami:

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Skompiluj projekt.

## <a name="createdata-bound-controls"></a>Kontrolki powiązane z danymi
 Utwórz kontrolki, które wyświetlają rekordy klientów, przeciągając `Product` tabelę z okna **źródła danych** do projektanta WPF.

#### <a name="to-create-data-bound-controls"></a>Aby utworzyć formanty powiązane z danymi

1. W oknie **źródła danych** kliknij menu rozwijane dla węzła **produkt** i wybierz polecenie **szczegóły**.

2. Rozwiń węzeł **produkt** .

3. W tym przykładzie niektóre pola nie będą wyświetlane, więc kliknij menu rozwijane obok następujących węzłów i wybierz opcję **Brak**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - danej

    - ModifiedDate

4. Kliknij menu rozwijane obok węzła **ThumbNailPhoto** i wybierz pozycję **obraz**.

    > [!NOTE]
    > Domyślnie elementy w oknie **źródła danych** , które reprezentują obrazy, mają ustawioną domyślną kontrolkę **none**. Dzieje się tak dlatego, że obrazy są przechowywane jako tablice bajtów w bazach danych, a tablice bajtowe mogą zawierać dowolne elementy z prostej tablicy bajtów do pliku wykonywalnego dużej aplikacji.

5. W oknie **źródła danych** przeciągnij węzeł **produktu** do wiersza siatki w wierszu, który zawiera przyciski.

     Program Visual Studio generuje kod XAML, który definiuje zestaw kontrolek, które są powiązane z danymi w tabeli **Products** . Generuje również kod, który ładuje dane. Aby uzyskać więcej informacji na temat wygenerowanej XAML i kodu, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. W projektancie kliknij pole tekstowe obok etykiety **Identyfikator produktu** .

7. W oknie **Właściwości** zaznacz pole wyboru obok właściwości **IsReadOnly** .

## <a name="navigating-product-records"></a>Nawigowanie po rekordach produktów
 Dodaj kod, który umożliwia użytkownikom przewijanie rekordów produktów za pomocą **\<** and **>** przycisków.

#### <a name="to-enable-users-to-navigate-product-records"></a>Aby umożliwić użytkownikom nawigowanie w rekordach produktów

1. W projektancie kliknij dwukrotnie **<** przycisk na powierzchni okna.

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy `backButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

2. Zmodyfikuj `Window_Loaded` procedurę obsługi zdarzeń, a więc `ProductViewSource` , `AdventureWorksLTDataSet` , i, `AdventureWorksLTDataSetProductTableAdapter` znajdują się poza metodą i dostępną dla całego formularza. Zadeklaruj tylko te, które mają być globalne dla formularza, i przypisz je w ramach `Window_Loaded` procedury obsługi zdarzeń podobne do następujących:

     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]

3. Dodaj następujący kod do `backButton_Click` programu obsługi zdarzeń:

     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]

4. Wróć do projektanta i kliknij dwukrotnie **>** przycisk.

5. Dodaj następujący kod do `nextButton_Click` programu obsługi zdarzeń:

     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]

## <a name="savechanges-to-product-records"></a>Metody SaveChanges do rekordów produktów
 Dodaj kod, który umożliwia użytkownikom zapisywanie zmian w rekordach produktu przy użyciu przycisku **Zapisz zmiany** .

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Aby dodać możliwość zapisywania zmian w rekordach produktu

1. W projektancie kliknij dwukrotnie przycisk **Zapisz zmiany** .

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy `saveButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

2. Dodaj następujący kod do `saveButton_Click` programu obsługi zdarzeń:

     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]

    > [!NOTE]
    > W tym przykładzie zastosowano `Save` metodę, `TableAdapter` Aby zapisać zmiany. Jest to odpowiednie w tym instruktażu, ponieważ zmieniana jest tylko jedna tabela danych. Jeśli zachodzi potrzeba zapisania zmian w wielu tabelach danych, można alternatywnie użyć `UpdateAll` metody `TableAdapterManager` , która generuje program Visual Studio z zestawem danych. Aby uzyskać więcej informacji, zobacz [TableAdapterManager Overview (przegląd](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)).

## <a name="test-the-application"></a>Testowanie aplikacji
 Skompiluj i uruchom aplikację. Sprawdź, czy można wyświetlać i aktualizować rekordy produktów.

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij klawisz **F5**.

     Aplikacja zostanie skompilowana i uruchomiona. Sprawdź następujące informacje:

    - Pola tekstowe wyświetlają dane z pierwszego rekordu produktu, który ma zdjęcie. Ten produkt ma identyfikator produktu 713, a nazwa w **logo z długą cyfrą**().

    - Możesz kliknąć przycisk **>** lub, **<** Aby nawigować po innych rekordach produktu.

2. W jednym z rekordów produktu Zmień wartość w polu **rozmiar** , a następnie kliknij przycisk **Zapisz zmiany**.

3. Zamknij aplikację, a następnie uruchom ponownie aplikację, naciskając klawisz **F5** w programie Visual Studio.

4. Przejdź do rekordu produktu, który został zmieniony, i sprawdź, czy zmiana została utrwalona.

5. Zamknij aplikację.

## <a name="next-steps"></a>Następne kroki
 Po zakończeniu tego instruktażu można wykonać następujące powiązane zadania:

- Dowiedz się, jak za pomocą okna **źródła danych** w programie Visual Studio POWIĄZAĆ formanty WPF z innymi typami źródeł danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Dowiedz się, jak używać okna **źródła danych** w programie Visual Studio, aby wyświetlić powiązane dane (czyli dane w relacji nadrzędny-podrzędny) w kontrolkach WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Zobacz też
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [POWIĄZYWANIE kontrolek WPF z danymi w](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [narzędziach zestawu danych programu Visual Studio w Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [WPF i](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) Omówienie [powiązań danych](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211) przegląd
