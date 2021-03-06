---
title: Zarządzanie zasobami aplikacji (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1815b0efeebf98587fe07384ea0b2c8d1f5e1d90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88992371"
---
# <a name="manage-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)

Pliki zasobów są plikami, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub pliki audio. Ponieważ te pliki nie są częścią procesu kompilacji, można je zmienić bez konieczności ponownego kompilowania plików binarnych. Jeśli planujesz lokalizowanie aplikacji, należy używać plików zasobów dla wszystkich ciągów i innych zasobów, które należy zmienić podczas lokalizowania aplikacji.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources).

Aby uzyskać więcej informacji na temat zasobów w aplikacjach .NET, zobacz [zasoby w aplikacjach .NET](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Pracuj z zasobami

W projekcie kodu zarządzanego Otwórz okno właściwości projektu. Aby otworzyć okno właściwości, można wykonać jedną z:

- Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**
- Wpisywanie **właściwości projektu** w **Ctrl** + polu wyszukiwania Ctrl**Q**
- Wybieranie **klawisza** + **Enter** w **Eksplorator rozwiązań**

Wybierz kartę **zasoby** . Plik *. resx* można dodać, jeśli projekt nie zawiera już jednego z nich, dodawać i usuwać różne rodzaje zasobów oraz modyfikować istniejące zasoby.

## <a name="resources-in-other-project-types"></a>Zasoby w innych typach projektów

Zasoby są zarządzane inaczej w projektach .NET niż w innych typach projektów. Aby uzyskać więcej informacji na temat zasobów w programie:

- Aplikacje platforma uniwersalna systemu Windows (platformy UWP), zobacz [zasoby aplikacji i system zarządzania zasobami](/windows/uwp/app-resources/)
- Projekty języka C++, zobacz [Work with pliki zasobów](/cpp/windows/working-with-resource-files) i [instrukcje: Tworzenie zasobu](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Zobacz też

- [Zasoby w aplikacjach .NET (.NET Framework)](/dotnet/framework/resources/index)
- [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources)
