---
title: 'Przewodnik: Dodawanie funkcji do edytora niestandardowego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d14fb36298518409df34302f9346e186f0b0263
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825165"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Przewodnik: dodawanie funkcji do edytora niestandardowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po utworzeniu edytora niestandardowego można dodać do niego więcej funkcji.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Aby utworzyć Edytor dla elementu pakietu VSPackage  
  
1. Utwórz niestandardowy Edytor przy użyciu szablonu projektu pakietu programu Visual Studio.  
  
     Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego edytora](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2. Zdecyduj, czy edytor ma obsługiwać pojedynczy widok, czy wiele widoków.  
  
     Edytor obsługujący nowe polecenie **okna** lub widok formularza i widok kodu wymaga oddzielnych obiektów danych dokumentu i obiektów widoku dokumentu. W edytorze, który obsługuje tylko jeden widok, obiekt danych dokumentu i obiekt widoku dokumentu można zaimplementować dla tego samego obiektu.  
  
     Przykład wielu widoków można znaleźć w temacie [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).  
  
3. Zaimplementuj fabrykę edytora przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu.  
  
     Aby uzyskać więcej informacji, zobacz [fabryki edytora](../extensibility/editor-factories.md).  
  
4. Zdecyduj, czy edytor ma używać aktywacji w miejscu czy uproszczonego osadzania, aby zarządzać oknem obiektu widoku dokumentu.  
  
     Uproszczone okno edytora osadzania zawiera standardowy widok dokumentu, podczas gdy okno edytora aktywacji w miejscu obsługuje formant ActiveX lub inny aktywny obiekt jako widok dokumentu. Aby uzyskać więcej informacji, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md) i [Aktywacja w miejscu](../misc/in-place-activation.md).  
  
5. Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu w celu obsługi poleceń.  
  
6. Podaj trwałość dokumentu i odpowiedź na zmiany plików zewnętrznych, wykonując następujące czynności:  
  
    1. Aby zachować plik, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> w obiekcie danych dokumentu edytora.  
  
    2. Aby odpowiedzieć na zmiany w pliku zewnętrznym, zaimplementuj i przejdź do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> obiektu danych dokumentu edytora.  
  
        > [!NOTE]
        > Wywołaj, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> Aby uzyskać wskaźnik do `IVsFileChangeEx` .  
  
7. Koordynuj zdarzenia edycji dokumentu z kontrolą kodu źródłowego. W tym celu:  
  
    1. Uzyskaj wskaźnik do `IVsQueryEditQuerySave2` przez wywołanie metody `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .  
  
    2. Gdy wystąpi pierwsze zdarzenie edycji, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodę.  
  
         Zostanie wyświetlony komunikat z prośbą o wyewidencjonowanie pliku, jeśli nie został jeszcze wyewidencjonowany. Pamiętaj, aby obsłużyć warunek "niewyewidencjonowany plik" w celu zapobieżenia błędom  
  
    3. Podobnie przed zapisaniem pliku Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metodę.  
  
         Ta metoda poprosi użytkownika o zapisanie pliku, jeśli nie został on zapisany lub został zmieniony od ostatniego zapisu.  
  
8. Włącz okno **Właściwości** , aby wyświetlić właściwości tekstu zaznaczonego w edytorze. W tym celu:  
  
    1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> każdą zmianę zaznaczenia tekstu, przekazując ją w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
    2. Zadzwoń do `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> usługi, aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
9. Zezwól użytkownikom na przeciąganie i upuszczanie elementów między edytorem i **przybornikiem**albo między edytorami zewnętrznymi (takimi jak program Microsoft Word) i **przybornikiem**. W tym celu:  
  
    1. Zaimplementuj `IDropTarget` w edytorze, aby ostrzec IDE, że edytorem jest obiekt docelowy upuszczania.  
  
    2. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfejs w widoku, aby Edytor mógł włączać i wyłączać elementy **w przyborniku**.  
  
    3. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> i zadzwoń `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> do usługi, aby uzyskać wskaźnik <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> do <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfejsów i.  
  
         Dzięki temu pakietu VSPackage może dodawać nowe elementy do **przybornika**.  
  
10. Zdecyduj, czy chcesz, aby wszystkie inne funkcje opcjonalne dla edytora.  
  
    - Jeśli chcesz, aby Edytor obsługiwał polecenia Znajdź i Zamień, zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> .  
  
    - Jeśli chcesz użyć okna narzędzia konspektu dokumentu w edytorze, zaimplementuj `IVsDocOutlineProvider` .  
  
    - Jeśli chcesz użyć paska stanu w edytorze, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> i Wywołaj metodę, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Aby uzyskać wskaźnik do `IVsStatusBar` .  
  
         Na przykład, Edytor może wyświetlać informacje o wierszu/kolumnie, tryb wyboru (strumień/pole) i tryb wstawiania (Wstawianie/przekreślenie).  
  
    - Jeśli chcesz, aby Edytor obsługiwał `Undo` polecenie, zalecana metoda to użycie modelu Menedżera obiektów OLE Undo. Alternatywnie, możesz mieć Edytor bezpośrednio obsłużyć `Undo` polecenie.  
  
11. Utwórz informacje rejestru, w tym identyfikatory GUID dla pakietu VSPackage, menu, Edytor i inne funkcje.  
  
     Poniżej przedstawiono ogólny przykład kodu, który można umieścić w skrypcie pliku. RGS, aby pokazać, jak prawidłowo zarejestrować Edytor.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Zaimplementuj obsługę pomocy kontekstowej.  
  
     Pozwala to zapewnić Pomoc F1 i dynamiczną obsługę okna pomocy dla elementów w edytorze. Aby uzyskać więcej informacji na ten temat, zobacz [How to: zapewnianie kontekstu dla edytorów](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Udostępnienie modelu obiektów automatyzacji z edytora przez implementację `IDispatch` interfejsu.  
  
     Aby uzyskać więcej informacji, zobacz temat Tworzenie [modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
- Wystąpienie edytora jest tworzone, gdy IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodę. Jeśli Edytor obsługuje wiele widoków, program `CreateEditorInstance` tworzy zarówno dane dokumentu, jak i obiekty widoku dokumentu. Jeśli obiekt danych dokumentu jest już otwarty, `punkDocDataExisting` do `IVsEditorFactory::CreateEditorInstance` . Implementacja fabryki edytora musi określać, czy istniejący obiekt danych dokumentu jest zgodny przez wykonywanie zapytań dotyczących odpowiednich interfejsów. Aby uzyskać więcej informacji, zobacz [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).  
  
- Jeśli używasz uproszczonego podejścia do osadzania, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejs.  
  
- W przypadku podjęcia decyzji o użyciu aktywacji w miejscu należy zaimplementować następujące interfejsy:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    > `IOleInPlaceComponent`Interfejs jest używany, aby uniknąć scalania menu OLE 2.  
  
     `IOleCommandTarget`Implementacja obsługuje polecenia, takie jak **wycinanie**, **Kopiowanie**i **wklejanie**. Podczas wdrażania `IOleCommandTarget` należy zdecydować, czy Edytor wymaga własnego pliku. vsct, aby zdefiniować własną strukturę menu poleceń lub jeśli może zaimplementować standardowe polecenia zdefiniowane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Zazwyczaj edytory używają i zwiększają menu środowiska IDE oraz definiują własne paski narzędzi. Jednak często jest to konieczne, aby Edytor mógł definiować własne poszczególne polecenia oprócz używania standardowego zestawu poleceń IDE. Aby to zrobić, Edytor musi deklarować standardowe polecenia, z których korzysta, a następnie definiować nowe polecenia, menu kontekstowe, menu najwyższego poziomu i paski narzędzi w pliku. vsct. Jeśli utworzysz Edytor aktywacji w miejscu, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> i zdefiniuj menu i paski narzędzi dla edytora w pliku. vsct, a nie za pomocą scalania menu OLE 2.  
  
- Aby zapobiec zapisywaniu poleceń menu w interfejsie użytkownika, należy użyć istniejących poleceń w IDE przed wyjęciem nowych poleceń. Polecenia udostępnione są zdefiniowane w SharedCmdDef. vsct i ShellCmdDef. vsct. Te pliki są instalowane domyślnie w podkatalogu VisualStudioIntegration\Common\Inc [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] instalacji.  
  
- `ISelectionContainer` może wyrazić wybór pojedynczy i wielokrotny. Każdy zaznaczony obiekt jest zaimplementowany jako `IDispatch` obiekt.  
  
- IDE implementuje `IOleUndoManager` jako usługę dostępną z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> lub jako obiekt, w którym można utworzyć wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . Edytor implementuje `IOleUndoUnit` interfejs dla każdej `Undo` akcji.  
  
- Istnieją dwa miejsca, w których Edytor niestandardowy może uwidaczniać obiekty automatyzacji:  
  
  - `Document.Object`  

  - `Window.Object`  
  
## <a name="see-also"></a>Zobacz też  
 [Współtworzenie modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Instrukcje: dostarczanie kontekstu edytorom](../extensibility/how-to-provide-context-for-editors.md)
