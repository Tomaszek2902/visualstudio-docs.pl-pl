---
title: Określanie ścieżki do profilowania narzędzi wiersza polecenia
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fb445e23b5d507bafb7fece40bf606bbfb76c370
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809188"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Określanie ścieżki do narzędzi wiersza polecenia narzędzi profilowania

Ścieżka [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do narzędzia profilowania narzędzi wiersza polecenia nie jest dodawana do zmiennej środowiskowej PATH. Na komputerach 32-bitowych narzędzia znajdują się w jednym katalogu. Na komputerach 64-bitowych istnieją 32-bitowe i 64-bitowe wersje narzędzi profilowania.

## <a name="32-bit-computers"></a>32-bitowe komputery

W przypadku kodu natywnego interfejsy API programu Visual Studio profiler są w *VSPerf.dll*. Plik nagłówkowy, *VSPerf. h*i Biblioteka Imports *VSPerf. lib*znajdują się w katalogu *programu Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* .

 W przypadku kodu zarządzanego interfejs API profilera znajduje się w *Microsoft.VisualStudio.Profiler.dll*. Ta biblioteka DLL znajduje się w katalogu *programu Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* .

## <a name="64-bit-computers"></a>Komputery 64-bitowe

Na komputerach 64-bitowych określ ścieżkę zgodną z platformą docelową profilowanej aplikacji.

- W przypadku aplikacji 32-bitowych domyślnym katalogiem narzędzi profilera jest:

     trybu *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     zarządzanych *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- W przypadku aplikacji 64-bitowych domyślnym katalogiem narzędzi profilera jest:

     trybu *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     zarządzanych *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
