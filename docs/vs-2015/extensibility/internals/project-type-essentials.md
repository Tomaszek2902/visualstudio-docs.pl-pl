---
title: Podstawowe informacje o typie projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e45d5f252deaf1788ae5093048ef8afb900fbe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704074"
---
# <a name="project-type-essentials"></a>Podstawowe informacje o typach projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawiera kilka typów projektów dla języków takich jak [!INCLUDE[csprcs](../../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pozwala również tworzyć własne typy projektów.  
  
 Jeśli chcesz tylko dodać niestandardowe polecenia, edytory lub okna narzędzi do programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , możesz to zrobić bez tworzenia nowego typu projektu. Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Podobnie, jeśli chcesz dostosować zachowanie [!INCLUDE[csprcs](../../includes/csprcs-md.md)] typów dostarczonych i projektów, możesz to [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] zrobić przy użyciu podtypów projektu. Aby uzyskać więcej informacji, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).  
  
  Należy utworzyć nowy typ projektu dla projektów opartych na języku innym niż [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Jeśli chcesz obsługiwać co najmniej jedną z następujących czynności:  
  
- Kompilacja  
  
- Wdrożenie  
  
- Wiele konfiguracji  
  
- Kontrola źródła  
  
- Debugowanie  
  
- Elementy projektu w Eksplorator rozwiązań  
  
- Okna dialogowe **Otwórz projekt** lub **Nowy projekt**  
  
- Zagnieżdżanie projektu  
  
- Aby uzyskać więcej informacji na temat możliwości typów projektów, zobacz następujące tematy:  
  
- Typy projektów to obiekty w pakietu VSPackage, które implementują zestaw interfejsów [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Jeśli używasz języka C# do tworzenia typu projektu, klasy projektu struktury pakietów zarządzanych implementują niezbędne interfejsy i umożliwiają dziedziczenie tej implementacji. Aby uzyskać więcej informacji, zobacz [Używanie struktury pakietu zarządzanego do implementowania typu projektu (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- W przypadku deweloperów języka C++ klasy w bibliotece HierUtil działają w podobny sposób. Aby uzyskać więcej informacji, zobacz [nie w kompilacji: używanie klas projektu HierUtil7 do implementowania typu projektu (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Typy projektów mogą obsługiwać dane inne niż typowe pliki kodu źródłowego, które kompilują do zestawu. exe lub. dll. Na przykład [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty bazy danych zawierają odwołania do plików skryptów i zapytań przechowywanych na dysku i Dodaj polecenia do **Eksplorator rozwiązań** , aby wykonać skrypty i zapytania względem bazy danych, ale projekty nie obsługują zachowania kompilacji. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Typ projektu nie musi używać plików w ogóle. Na przykład typ projektu może przechowywać wszystkie jego dane w bazie danych. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zapewnia, że typy projektów mają pełną kontrolę nad sposobem utrwalania danych dla projektów i elementów projektu. Aby uzyskać więcej informacji, zobacz [decyzje projektowe typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
- Typy projektów muszą dostarczać *fabrykę projektu*, która jest obiektem, który tworzy wystąpienie typu projektu za każdym razem, gdy jest wyświetlany komunikat o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] konieczności otwarcia lub utworzenia projektu opartego na tym typie projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Typy projektów muszą dostarczać szablony dla projektów i elementów projektu. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] program używa szablonów, gdy użytkownicy tworzą nowe projekty i dodają nowe elementy do istniejących projektów. Aby uzyskać więcej informacji, zobacz [Dodawanie projektów i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Typy projektów mogą obsługiwać wiele konfiguracji, takich jak debugowanie i wydanie. Użytkownicy mogą zmieniać różne konfiguracje projektu przy użyciu stron właściwości, które dostarczasz. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)
