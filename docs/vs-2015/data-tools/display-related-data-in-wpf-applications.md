---
title: Wyświetlanie powiązanych danych w aplikacjach WPF | Microsoft Docs
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6efa79fc59ed9812cf6162096dd462100b71fbca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672416"
---
# <a name="display-related-data-in-wpf-applications"></a>Wyświetlanie pokrewnych danych w aplikacjach WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W niektórych aplikacjach można chcieć korzystać z danych pochodzących z wielu tabel lub jednostek, które są ze sobą powiązane w relacji nadrzędny-podrzędny. Na przykład możesz chcieć wyświetlić siatkę wyświetlającą klientów z `Customers` tabeli. Gdy użytkownik wybierze określonego klienta, w innej siatce są wyświetlane zamówienia dla tego klienta z tabeli powiązanej `Orders` .

 Można tworzyć kontrolki powiązane z danymi, które wyświetlają powiązane dane, przeciągając elementy z okna **źródła danych** do projektanta WPF.

## <a name="to-create-controls-that-display-related-records"></a>Aby utworzyć kontrolki, które wyświetlają powiązane rekordy

1. W menu **dane** kliknij przycisk **Pokaż źródła danych** , aby otworzyć okno **źródła danych** .

2. Kliknij przycisk **Dodaj nowe źródło danych**i Ukończ pracę kreatora **konfiguracji źródła danych** .

3. Otwórz projektanta WPF i upewnij się, że projektant zawiera kontener, który jest prawidłowym obiektem docelowym upuszczania dla elementów w oknie **źródła danych** .

     Aby uzyskać więcej informacji na temat prawidłowych obiektów docelowych upuszczania, zobacz [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

4. W oknie **źródła danych** rozwiń węzeł, który reprezentuje tabelę nadrzędną lub obiekt w relacji. Tabela nadrzędna lub obiekt znajduje się po stronie "jeden" relacji jeden-do-wielu.

5. Przeciągnij węzeł nadrzędny (lub dowolne poszczególne elementy w węźle nadrzędnym) z okna **źródła danych** na prawidłowy element docelowy upuszczania w projektancie.

     Program Visual Studio generuje kod XAML, który tworzy nowe kontrolki powiązane z danymi dla każdego elementu, który przeciągniesz. KOD XAML dodaje również nowe <xref:System.Windows.Data.CollectionViewSource> dla tabeli nadrzędnej lub obiektu do zasobów docelowego upuszczania. W przypadku niektórych źródeł danych program Visual Studio generuje również kod umożliwiający załadowanie danych do tabeli nadrzędnej lub obiektu. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. W oknie **źródła danych** Znajdź powiązaną tabelę podrzędną lub obiekt. Powiązane tabele podrzędne i obiekty są wyświetlane jako węzły rozwijane w dolnej części listy danych węzła nadrzędnego.

7. Przeciągnij węzeł podrzędny (lub dowolne poszczególne elementy w węźle podrzędnym) z okna **źródła danych** na prawidłowy element docelowy upuszczania w projektancie.

     Program Visual Studio generuje kod XAML, który tworzy nowe kontrolki powiązane z danymi dla każdego z przeciąganych elementów. KOD XAML dodaje również nowe <xref:System.Windows.Data.CollectionViewSource> dla tabeli podrzędnej lub obiektu do zasobów docelowego upuszczania. Ta nowa <xref:System.Windows.Data.CollectionViewSource> jest powiązana z właściwością tabeli nadrzędnej lub obiektu, który właśnie został przeciągnięty do projektanta. W przypadku niektórych źródeł danych program Visual Studio generuje również kod służący do ładowania danych do podrzędnej tabeli lub obiektu.

     Na poniższej ilustracji przedstawiono tabelę powiązane **zamówienia** tabeli **Customers** w zestawie danych w oknie **źródła danych** .

     ![Okno źródeł danych z relacją](../data-tools/media/datasources2.gif "DataSources2")

## <a name="see-also"></a>Zobacz też
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [POWIĄZYWANIE kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Tworzenie tabel odnośników w instruktażu aplikacji WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
