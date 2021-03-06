---
title: Dodawanie katalogów do okna dialogowego Dodaj nowy element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710252"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Dodawanie katalogów do okna dialogowego Dodaj nowy element
Poniższy przykład kodu demonstruje sposób rejestrowania nowego zestawu katalogów dla okna dialogowego **Dodaj nowy element** . Katalogi dla okna dialogowego **Dodawanie nowego elementu** są różne dla każdego projektu. W związku z tym katalogi są rejestrowane w podkluczu **projekty** , które znajdują się w **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Skrypt rejestru

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 `%Template_Path%`Wartość określa pełną ścieżkę katalogu, który zawiera szablony projektu. Te szablony mogą być plikami *vsz* lub plikami szablonów prototypowe do sklonowania.

 `SortPriority`Wartość określa priorytet sortowania.

## <a name="add-items-to-an-existing-project"></a>Dodaj elementy do istniejącego projektu
 Możesz również dodać elementy do istniejącego projektu. Na przykład dla [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu można dodać elementy do folderu * \<root> \Program Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* . W tym przypadku `%GUID_Project%` jest identyfikatorem GUID dla projektu C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Można także rozciągnąć istniejący projekt przez programowanie podtypu projektu. W przypadku podtypu projektu można zwiększyć projekt bez tworzenia nowego typu projektu. Aby uzyskać więcej informacji na temat podtypów projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz też
- [Rejestruj szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Dodaj elementy do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
