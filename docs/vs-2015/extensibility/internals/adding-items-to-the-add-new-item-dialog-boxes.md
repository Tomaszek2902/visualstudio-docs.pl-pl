---
title: Dodawanie elementów do okien dialogowych Dodawanie nowego elementu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdacfc4ac65e0dc18512bfb56eb870545c66a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64790709"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Dodawanie elementów do okien dialogowych Dodawanie nowego elementu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proces dodawania elementów do okna dialogowego **Dodaj nowy element** rozpoczyna się od kluczy rejestru. Jak pokazano w poniższych wpisach rejestru, sekcja AddItemTemplates zawiera ścieżkę i nazwę katalogu, w którym są umieszczane elementy udostępniane w oknie dialogowym **Dodaj nowy element** .  
  
> [!NOTE]
> Tabela bezpośrednio po segmencie kodu zawiera dodatkowe informacje o wpisie rejestru.  
  
 Ta sekcja znajduje się w obszarze [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Pierwszy identyfikator GUID jest identyfikatorem CLSID dla projektów tego typu; drugi identyfikator GUID wskazuje zarejestrowany typ projektu dla szablonów dodawania elementów.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \ 1  
  
 @ = "#6"  
  
 "TemplatesDir" = " \< ścieżka instalacji zestawu Visual Studio SDK \\ \VSIntegration \\ \SomeFolder \\ \SomePackage \\ \SomeProject \\ \SomeProjectItems"  
  
 "SortPriority" = DWORD: 00000064  
  
|Nazwa|Typ|Dane (z pliku. RGS)|Opis|  
|----------|----------|-----------------------------|-----------------|  
|@ (Domyślnie)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY%|Identyfikator zasobu dla szablonów **dodawania elementów** .|  
|Val TemplatesDir|REG_SZ|% TEMPLATE_PATH% \ SomeProjectItems|Ścieżka elementów projektu wyświetlanych w oknie dialogowym kreatora **dodawania nowego elementu** .|  
|Val SortPriority|REG_DWORD|100 ( [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)] )|Określa kolejność sortowania w węźle drzewa plików wyświetlanych w oknie dialogowym **Dodaj nowy element** .|  
  
> [!NOTE]
> Identyfikatory GUID dla typów projektów Visual C# i Visual Basic są następujące: [!INCLUDE[csprcs](../../includes/csprcs-md.md)] : {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] : {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Katalog wymieniony dla TemplateDirs, który jest% TEMPLATE_PATH% \ SomeProjectItems, jest węzłem po lewej stronie drzewa okna dialogowego **Dodaj nowy element** . Dodatkowe elementy w drzewie są oparte na podkatalogu w katalogu głównym. Pliki dostępne do dodania do projektu to elementy w prawym okienku okna dialogowego **Dodaj nowy element** .  
  
 Zazwyczaj ten folder będzie zawierać pliki szablonów dla projektu, takie jak plik HTML szablonu lub. cpp, a także wszystkie pliki. vsz do uruchamiania kreatorów. Aby kontrolować sposób wyświetlania elementów, można również dołączyć pliki. vsdir do lokalizowania nazw katalogów i ikon. Zlokalizowany ciąg jest podpisem, który pojawia się w oknie dialogowym, które reprezentuje ten węzeł w drzewie okna dialogowego Dodaj nowy element.  
  
 Nie trzeba jednak mieć wszystkich elementów w jednym pliku. vsdir. Dla każdego elementu w katalogu można mieć jeden plik. vsdir. Aby uzyskać więcej informacji, zobacz [Kreator (. Vsz) Opis pliku](../../extensibility/internals/wizard-dot-vsz-file.md) i [katalogu szablonu (. VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
> Pliki. vsdir w katalogach szablonów są opcjonalne. Jeśli chcesz tylko umieścić element projektu w katalogu i wyświetlić go w oknie dialogowym **Dodaj nowy element** , możesz umieścić ten plik w katalogu szablonów określonym w instrukcji TemplatesDir. Plik zostanie następnie wyświetlony w prawym okienku okna dialogowego **Dodaj nowy element** dla tego projektu. Jeśli jednak chcesz wyświetlić zlokalizowany podpis pliku lub ikony, musisz dołączyć co najmniej jeden plik. vsdir w katalogu templates.  
  
## <a name="grouping-project-items"></a>Grupowanie elementów projektu  
 Jeśli chcesz zawierać grupy szablonów w folderach w drzewie okna dialogowego **Dodaj nowy element** , musisz mieć podkatalogów w katalogu głównym szablonu z elementami w nich. Gdy zostanie wyświetlone okno dialogowe **Dodaj nowy element** dla użytkowników, zostaną one również wyświetlone podfoldery i będzie można wybrać z nich elementy projektu.  
  
 Priorytet sortowania w segmencie kodu określa, gdzie ten katalog szablonów zostanie utworzony w drzewie względem innych elementów węzła drzewa. W oknie dialogowym **Dodaj nowy element** priorytet sortowania to wszystkie elementy, które należy uwzględnić, tak aby były wyświetlane w prawidłowej lokalizacji w oknie dialogowym.  
  
 Możesz również zaimplementować interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Aby odfiltrować, co jest wyświetlane w oknie dialogowym **Dodaj nowy element** . Implementując ten interfejs, można skonfigurować jeden katalog szablonów na dysku, który zawiera, na przykład, szablony i pliki kreatora 50. W ten sposób można mieć różne typy projektów z 20 plikami, które należą do jednego typu projektu, inne 30 plików, które należą do innego typu projektu i wszystkie pliki dostępne w ogólnym typie projektu. W ten sposób, w zależności od tego, który szablon projektu jest tworzony, można wyświetlić inny zestaw plików szablonów.  
  
 Na przykład w projekcie Visual Basic mogą istnieć projekty sieci Web i projekty klientów. Formularze sieci Web nie są przydatne do dodawania do projektu klienta, a formularze systemu Windows nie są przydatne do dodawania do projektu serwera sieci Web. W związku z tym można utworzyć jeden katalog szablonów, który zawiera wszystkie pliki dla obu typów projektu. Następnie implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> , można ukryć elementy, które nie powinny być wyświetlane na podstawie typu projektu lub ustawienia projektu w projekcie.  
  
## <a name="filtering-project-items"></a>Filtrowanie elementów projektu  
 `IVsFilterAddProjectItemDlg2` umożliwia filtrowanie elementów w drzewie (lewe okienko) i plików projektu (prawego okienka) w następujący sposób:  
  
- Nazwy zlokalizowane (napisy wyświetlane w oknie dialogowym, które znajdują się w pliku. vsdir) dostarczone przez `IVsFilterAddProjectItemDlg` .  
  
- Według rzeczywistej nazwy plików i folderów na dysku (Niezlokalizowany — plik VSDIR) udostępniony przez program `IVsFilterAddProjectItemDlg` .  
  
- Według kategorii, dostarczone przez `IVsFilterAddProjectItemDlg2` .  
  
  Aby filtrować według kategorii, podaj ciąg kategorii dla elementu w pliku. vsdir, na przykład "formularz sieci Web" lub "element klienta" w Visual Basic. Następnie kod okna dialogowego pobiera klasyfikację kategorii z pliku. vsdir i przekazuje ją do użytkownika. Następnie można przekazać te informacje do implementacji programu, `IVsFilterAddProjectItemDlg2` Aby odfiltrować okno dialogowe **Dodaj nowy element** według kategorii. Można również filtrować elementy dla stron sieci Web lub jako klienckie przypadki aplikacji Win32. Ponadto można zidentyfikować [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] elementy oznaczone jako Microsoft Foundation Classes (MFC) lub Active Template Library (ATL). Po zidentyfikowaniu tych elementów system projektu może definiować własne klasyfikacje, aby można było filtrować system w oparciu o kategorie i klasyfikacje.  
  
  W przypadku zaimplementowania tej funkcji filtru nie ma potrzeby mapowania tabeli dla każdego elementu, który powinien być ukryty. Można po prostu sklasyfikować elementy na typy i umieścić klasyfikacje w pliku. vsdir lub plikach. Następnie można ukryć dowolne elementy, które mają określoną klasyfikację przez implementację interfejsu. W ten sposób można sprawić, aby elementy w oknie dialogowym **Dodaj nowy element** były dynamiczne w zależności od stanu w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Rejestrowanie szablonów projektu i elementu](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID dla obiektów, które są zwykle używane do rozszerania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Dodawanie projektów i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Opis katalogu szablonów (. VSDIR) — pliki](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
