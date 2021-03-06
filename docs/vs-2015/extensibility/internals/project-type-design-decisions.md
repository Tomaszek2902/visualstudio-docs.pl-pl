---
title: Decyzje projektowe typu projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd26e08ab153e96fc601e89788008cb0e9ca38c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704085"
---
# <a name="project-type-design-decisions"></a>Decyzje projektowe dotyczące typów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przed utworzeniem nowego typu projektu należy podjąć kilka decyzji projektowych dotyczących typu projektu. Należy zdecydować, jakie typy elementów zawiera projekt, jak zostaną utrwalone pliki projektu i jakiego modelu zobowiązań będziesz używać.  
  
## <a name="project-items"></a>Elementy projektu  
 Czy projekt będzie używać plików lub obiektów abstrakcyjnych? Jeśli używasz plików, czy będą one plikami referencyjnymi lub opartymi na katalogu? Czy pliki lub obiekty abstrakcyjne mają być lokalne lub zdalne?  
  
 Elementy projektu mogą być plikami lub mogą być bardziej abstrakcyjnymi obiektami, takimi jak obiekty w repozytorium bazy danych lub połączenia danych przez Internet. Jeśli elementy są plikami, projekt może być projektem opartym na odwołania lub w katalogu.  
  
 W projektach opartych na odwołaniach elementy mogą znajdować się w więcej niż jednym projekcie. Jednak rzeczywisty plik reprezentowany przez element znajduje się tylko w jednym katalogu. W projektach opartych na katalogu wszystkie elementy projektu istnieją w strukturze katalogów. Aby uzyskać więcej informacji, zobacz [NIB: Management Item in projects](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Elementy lokalne są przechowywane na tym samym komputerze, na którym zainstalowano aplikację. Elementy zdalne mogą być przechowywane na osobnym serwerze w sieci lokalnej lub w innym miejscu w Internecie.  
  
## <a name="project-file-persistence"></a>Trwałość pliku projektu  
 Czy dane będą przechowywane w popularnych zwykłych systemach plików, czy w magazynie strukturalnym? Czy pliki będą otwierane przy użyciu standardowego edytora czy edytora specyficznego dla projektu?  
  
 Aby zachować swoje dane, większość aplikacji zapisuje swoje dane w pliku, a następnie odczytuje je ponownie, gdy użytkownik musi przejrzeć lub zmienić informacje.  
  
 Magazyn strukturalny, nazywany również plikami złożonymi, jest zwykle używany, gdy kilka obiektów Component Object Model (COM) musi przechowywać utrwalone dane w jednym pliku. W przypadku magazynu strukturalnego niektóre różne składniki oprogramowania mogą współużytkować jeden plik na dysku.  
  
 Istnieje kilka opcji, które należy wziąć pod uwagę w odniesieniu do elementów w projekcie. Można wykonać jedną z następujących czynności:  
  
- Zapisz każdy plik indywidualnie, gdy został zmieniony.  
  
- Przechwyć wiele transakcji w ramach jednej operacji **zapisywania** .  
  
- Zapisz lokalnie pliki, a następnie opublikuj je na serwerze lub użyj innego podejścia do zapisywania elementów projektu, gdy element reprezentuje połączenie danych z obiektem zdalnym.  
  
  Aby uzyskać więcej informacji na temat trwałości, zobacz temat [trwałość projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Model zobowiązania projektu  
 Czy utrwalane obiekty danych będą otwierane w trybie bezpośrednim czy w trybie transakcyjnym?  
  
 Gdy obiekty danych są otwierane w trybie bezpośrednim, zmiany wprowadzone do danych są włączane natychmiast lub po ręcznym zapisaniu pliku przez użytkownika.  
  
 Gdy obiekty danych są otwierane przy użyciu trybu transakcyjnego, zmiany są zapisywane w tymczasowej lokalizacji w pamięci i nie są zatwierdzane, dopóki użytkownik nie zdecyduje się ręcznie zapisać pliku. W tym czasie wszystkie zmiany muszą następować razem lub nie będą wprowadzane żadne zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB: Zarządzanie elementami w projektach](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Trwałość projektu](../../extensibility/internals/project-persistence.md)   
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
