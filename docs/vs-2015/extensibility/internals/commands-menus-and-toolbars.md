---
title: Polecenia, menu i paski narzędzi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 337bc4de9171d2f98bf0be0068b298b7f600b979
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155838"
---
# <a name="commands-menus-and-toolbars"></a>Polecenia, menu i paski narzędzi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Menu i paski narzędzi to sposób, w jaki użytkownicy uzyskują dostęp do poleceń w pakietu VSPackage. Polecenia to funkcje wykonujące zadania, takie jak drukowanie dokumentu, odświeżanie widoku lub tworzenie nowego pliku. Menu i paski narzędzi są wygodnym sposobem na prezentowanie poleceń użytkownikom. Zazwyczaj powiązane polecenia są klastrowane w tym samym menu lub pasku narzędzi.  
  
- Menu są zwykle wyświetlane jako ciągi jednowyrazowe klastrowane w wierszu w górnej części zintegrowanego środowiska programistycznego (IDE) lub okna narzędzi. Menu można także wyświetlać jako wynik zdarzenia prawym przyciskiem myszy i są nazywane menu skrótów w tym kontekście. Po kliknięciu menu rozwijane, aby wyświetlić jedno lub więcej poleceń. Polecenia po kliknięciu mogą wykonywać zadania i uruchamiać podmenu zawierające dodatkowe polecenia. Niektóre dobrze znane nazwy menu to plik, Edycja, widok i okno. Aby uzyskać więcej informacji, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
- Paski narzędzi zwykle są wierszami przycisków i innych kontrolek, takimi jak pola kombi, pola listy, pola tekstowe i kontrolery menu. Wszystkie kontrolki paska narzędzi są skojarzone z poleceniami. Po kliknięciu przycisku paska narzędzi jego skojarzone polecenie jest uaktywniane. Przyciski paska narzędzi mają zwykle ikony sugerujące podstawowe polecenia, takie jak drukarka dla polecenia Print. W kontrolce listy rozwijanej każdy element na liście jest skojarzony z innym poleceniem. Kontroler menu jest hybrydowy, w którym jedna strona kontrolki jest przyciskiem paska narzędzi, a druga strona jest strzałką w dół, która wyświetla dodatkowe polecenia po kliknięciu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolera menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Podczas tworzenia polecenia należy również utworzyć procedurę obsługi zdarzeń. Program obsługi zdarzeń określa, kiedy polecenie jest widoczne lub włączone, umożliwia zmodyfikowanie tekstu i gwarantuje, że polecenie będzie odpowiadać odpowiednio ("trasy") po aktywowaniu. W większości wystąpień IDE obsługuje polecenia przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Polecenia w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] trasie w sposób hierarchiczny, zaczynając od wewnętrznego kontekstu poleceń, na podstawie wyboru lokalnego i przechodząc do zewnętrznego kontekstu, oparte na globalnym wyborze. Polecenia dodane do menu głównego są natychmiast dostępne dla skryptów. Aby uzyskać więcej informacji, zobacz [MenuCommands a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) i [obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md).  
  
  Aby zdefiniować nowe menu i paski narzędzi, należy je opisać w pliku tabeli poleceń programu Visual Studio (. vsct). Szablon pakietu programu Visual Studio tworzy ten plik wraz z niezbędnymi elementami do obsługi poleceń, pasków narzędzi i edytorów wybranych w szablonie. Alternatywnie można napisać własny plik. vsct, używając schematu XML opisanego tutaj: [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
  Aby uzyskać więcej informacji na temat pracy z plikami. vsct, zobacz [Visual Studio Command Table (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  W tematach w tej sekcji wyjaśniono, jak polecenia, menu i paski narzędzi działają w pakietów VSPackage.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Szczegółowy opis specyfikacji formatu tabeli poleceń.  
  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Opisuje składnię i kompilator oparty na języku XML dla tabel poleceń.  
  
 [Domyślne położenie poleceń, grup i pasków narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Opisuje wstępnie zdefiniowane polecenia, grupy, menu i paski narzędzi.  
  
 [Polecenia, menu i grupy definiowane w środowisku IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Określa wstępnie zdefiniowane menu, polecenia i grupy poleceń dostępne do użycia przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Projektowanie poleceń](../../extensibility/internals/command-design.md)  
 Wyjaśnia, jak projektować polecenia.  
  
 [Optymalizacja poleceń menu i paska narzędzi](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Zapewnia wytyczne dla poleceń.  
  
 [Udostępnianie poleceń](../../extensibility/internals/making-commands-available.md)  
 Wyjaśnia, jak udostępnić polecenia dla programu Visual Studio.  
  
 [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Wyjaśnia, jak zaimplementować polecenia korzystające z zestawów międzyoperacyjnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Wyjaśnia routing poleceń w pakietów VSPackage.
