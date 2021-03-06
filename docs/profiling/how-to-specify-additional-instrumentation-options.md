---
title: Określ dodatkowe opcje Instrumentacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42c5500d03e815bad1666da7b52918479715e861
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851817"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Instrukcje: określanie dodatkowych opcji instrumentacji

Pliki binarne można instrumentować za pomocą środowiska IDE programu Visual Studio lub za pomocą narzędzi wiersza polecenia. W przypadku Instrumentacji pliku binarnego z poziomu IDE można kontrolować ilość danych zbieranych w ramach usługi Instrumentation, określając dodatkowe opcje Instrumentacji dla narzędzia [VSInstr](../profiling/vsinstr.md) . Te opcje są dostępne w sesji lub na poziomie docelowym. Na przykład aby dołączyć lub wykluczyć określone funkcje podczas procesu instrumentacji, użyj opcji dodatkowe Instrumentacja na poziomie docelowym.

> [!IMPORTANT]
> Każda sonda, która jest wstawiana modyfikuje zachowanie oryginalnego programu. Ta modyfikacja powoduje obciążenie w czasie analizy. Nawet w przypadku odejmowania zbliżania się tego kosztu, nadal ma delikatne efekty chronometrażu w aplikacjach wielowątkowych. Opcje narzędzia [VSInstr](../profiling/vsinstr.md) ułatwiają kontrolowanie zbierania danych podczas profilowania.

## <a name="to-specify-additional-instrumentation-option"></a>Aby określić dodatkową instrumentację

1. W **Eksplorator wydajności**wybierz **sesję wydajności** , a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**.

2. Na **stronie właściwości**kliknij pozycję **Zaawansowane** właściwości.

3. Wpisz opcje w polu **dodatkowe opcje Instrumentacji** .

     Na przykład użyj/CONTROL: THREAD, aby określić poziom profilowania. Aby uzyskać pełną listę opcji, zobacz [VSInstr](../profiling/vsinstr.md).

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md) 
 [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
