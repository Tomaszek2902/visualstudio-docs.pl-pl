---
title: 'Instrukcje: Zmiana opcji stopniowego debugowania (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663438"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Instrukcje: Opcja zmiany debugowania krokowego (starsza wersja)
W tym temacie opisano, jak zmienić opcję wykonywania debugowania dla [!INCLUDE[wf](../includes/wf-md.md)] aplikacji w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] , która ma współbieżne akcje. Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 W przypadku debugowania starszych działań, które są wykonywane współbieżnie, takich jak **działaniu ParallelActivity** lub **ConditionedActivityGroup**, można użyć jednej z dwóch opcji, aby krokowo przekroczyć swój kod.

 Wykonaj następujące kroki, aby zmienić opcję stopniowego debugowania w projekcie starszego przepływu pracy.

## <a name="procedures"></a>Procedury

#### <a name="to-change-the-debug-stepping-option"></a>Aby zmienić opcję stopniowego debugowania

1. Uruchom program Visual Studio.

2. Otwórz istniejący projekt starszego przepływu pracy lub Utwórz nowy projekt, który wykorzystuje współbieżne działania i który jest przeznaczony dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

3. W menu **przepływu pracy** w starszej wersji [!INCLUDE[wfd2](../includes/wfd2-md.md)] wskaż polecenie **Debuguj**, a następnie wskaż polecenie **Opcje krok po kroku**.

4. Wybierz jedno z **wystąpień** lub **gałęzi**.

## <a name="see-also"></a>Zobacz też
 [Debugowanie starszych przepływów pracy](../workflow-designer/debugging-legacy-workflows.md) [debugowania opcji wykonywania (starsza wersja)](../workflow-designer/debug-stepping-options-legacy.md)