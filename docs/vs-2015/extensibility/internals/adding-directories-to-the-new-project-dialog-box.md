---
title: Dodawanie katalogów do okna dialogowego Nowy projekt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203877"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Dodawanie katalogów do okna dialogowego Nowy projekt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas tworzenia nowych typów projektów można także zarejestrować nowy katalog w oknie dialogowym **Nowy projekt** , aby wyświetlić je do użycia jako szablony. Poniższy przykład kodu wyjaśnia sposób rejestrowania nowego katalogu, znanego również jako węzeł. W przykładzie zarejestrowano szablony udostępniane przez pakietu VSPackage CLSID_Package. W związku z tym lewa strona okna dialogowego **Nowy projekt** oferuje dodany węzeł, z nazwą określoną przez zasób Folder_Label_ResID. Ten zasób jest ładowany z satelitarnej biblioteki DLL pakietu VSPackage.  
  
 Wartość **folderu** reprezentuje identyfikator GUID folderu, w którym jest wyświetlany węzeł Folder_Label_ResID. W przykładzie identyfikator GUID reprezentuje folder **inne projekty** w okienku **typy projektów** w oknie dialogowym **Nowy projekt** . Jeśli wartość **innych projektów** jest nieobecna, etykieta jest umieszczana na najwyższym poziomie.  
  
 Wartość TemplatesDir określa pełną ścieżkę katalogu, który zawiera szablony projektu. Te pliki mogą być plikami vsz lub typowymi plikami szablonów do sklonowania.  
  
 Jeśli określisz TemplatesLocalizedSubDir, musi to być identyfikator zasobu ciągu, który zawiera nazwę podkatalogu TemplatesDir zawierającego zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ładuje zasób ciągu z satelickiej biblioteki DLL, jeśli taki istnieje, każda satelitarna Biblioteka DLL może zawierać inną nazwę podkatalogu. Wartość SortPriority określa priorytet sortowania.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie szablonów projektu i elementu](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Dodawanie elementów do okien dialogowych Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
