---
title: Wiele języków DSL w jednym rozwiązaniu
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2eef29db24da3be0a9376ea76a9a1a551af9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542600"
---
# <a name="multiple-dsls-in-one-solution"></a>Wiele języków DSL w jednym rozwiązaniu

W ramach jednego rozwiązania można spakować kilka językami DSL, aby zostały one zainstalowane razem.

Do integracji wielu językami DSL można użyć kilku technik. Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) i [instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) oraz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Kompiluj więcej niż jeden DSL w tym samym rozwiązaniu

1. Utwórz nowy projekt **projektu VSIX** .

2. Utwórz co najmniej dwa projekty DSL w katalogu rozwiązania VSIX.

   - Dla każdego DSL Otwórz nowe wystąpienie programu Visual Studio. Utwórz nowy DSL i określ ten sam folder rozwiązania jako rozwiązanie VSIX.

   - Upewnij się, że tworzysz każde DSL z innym rozszerzeniem nazwy pliku.

   - Zmień nazwy projektów **DSL** i **DslPackage** tak, aby były różne. Na przykład: `Dsl1` , `DslPackage1` , `Dsl2` , `DslPackage2` .

   - W każdym **DslPackage \* \ source.Extension.tt**zaktualizuj ten wiersz do prawidłowej nazwy projektu DSL:

      `string dslProjectName = "Dsl2";`

   - W rozwiązaniu VSIX Dodaj projekty DSL * i DslPackage \* . Możesz chcieć umieścić każdą parę w swoim własnym folderze rozwiązania.

2. Połącz manifesty VSIX językami DSL:

   1. Otwórz _YourVsixProject_**\source.Extension.manifest**.

   2. Dla każdego DSL wybierz pozycję **Dodaj zawartość** i Dodaj:

       - `Dsl*` projekt jako **składnik MEF**

       - `DslPackage*` projekt jako **składnik MEF**

       - `DslPackage*` projekt jako **pakiet programu vs**

3. Skompiluj rozwiązanie.

   W rezultacie program VSIX zainstaluje oba językami DSL. Można je przetestować przy użyciu klawisza F5 lub wdrożyć _YourVsixProject_**\bin\debug \\ \* . vsix**.

## <a name="see-also"></a>Zobacz też

- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)