---
title: Model dla pakietów kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707069"
---
# <a name="model-for-source-control-packages"></a>Model pakietów kontroli kodu źródłowego
Poniższy model reprezentuje przykład implementacji kontroli źródła. W modelu widoczne są interfejsy, które należy zaimplementować, oraz usługi środowiska, które należy wywołać. Podobnie jak wszystkie usługi, w rzeczywistości wywołujemy metody określonego interfejsu, które uzyskuje się w ramach usługi. Nazwy klas są identyfikowane, aby ułatwić sprawdzenie, jak jest przeprowadzana kontrola źródła.

 ![Przykłady instalacyjnya SCC&#95;](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Przykładowy projekt kontroli źródła

## <a name="interfaces"></a>Interfejsy
 Można zaimplementować kontrolę źródła dla nowych typów projektów w programie Visual Studio przy użyciu listy interfejsów przedstawionych w poniższej tabeli.

|Interfejs|Zastosowanie|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wywoływane przez projekty i edytory, zanim zapiszą lub zmienią (zanieczyszczony) pliki. Dostęp do tego interfejsu uzyskuje się za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Wywoływane przez projekty, aby zażądać uprawnień do dodawania, usuwania lub zmiany nazwy pliku lub katalogu. Ten interfejs jest również wywoływany przez projekty w celu informowania środowiska o zakończeniu zatwierdzonej akcji dodawania, usuwania lub zmiany nazwy. Dostęp do niego odbywa się za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> usługi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Zaimplementowane przez każdą jednostkę, która ma zostać powiadomiona, gdy projekty dodają, zmienią nazwę lub usuwają plik lub katalog. Aby zarejestrować się w celu powiadomienia o zdarzeniach, wywołaj polecenie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wywoływane przez projekty, aby zarejestrować się w pakiecie kontroli źródła i uzyskać informacje o stanie kontroli źródła. Dostęp do tego interfejsu uzyskuje się za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> usługi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Zaimplementowane przez projekt, aby odpowiedzieć na żądania kontroli źródła informacji o plikach i uzyskać ustawienia kontroli źródła wymagane dla pliku projektu.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
