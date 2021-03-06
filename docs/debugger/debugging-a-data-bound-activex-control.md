---
title: Debugowanie kontrolki ActiveX powiązanej z danymi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccca00387e701d62e47eee0a93adff44a4765fa2
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600071"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debugowanie kontrolki ActiveX powiązanego z danymi
Jeśli tworzysz formant ActiveX, który zostanie powiązany z kontrolą źródła danych, możesz utworzyć własną aplikację kontenera i użyć tego kontenera do debugowania kontrolki ActiveX.

 Na przykład możesz utworzyć aplikację MFC opartą na oknach dialogowych i umieścić formant powiązany z danymi oraz formant źródła danych w oknie dialogowym. Ta aplikacja MFC służy do testowania w czasie wykonywania oraz jako plik wykonywalny kontenera do debugowania formantu ActiveX powiązanego z danymi.

## <a name="using-the-test-container"></a>Korzystanie z kontenera testów
 Jeśli chcesz, aby kontener, który można łatwo zmodyfikować, aby obsługiwał różne interfejsy na formancie lub kontenerze, Użyj kontenera testów ActiveX jako pliku wykonywalnego dla sesji debugowania. W kontenerze Test ActiveX kliknij pozycję **Opcje** z menu **kontener** , aby włączyć różne interfejsy. Aby uzyskać więcej informacji, zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testów](/cpp/mfc/testing-properties-and-events-with-test-container).

 Jeśli musisz umieścić w kodzie kontenera podczas debugowania, użyj wersji debugowania kontenera lub użyj wersji debugowania kontenera testów ActiveX. Aby uzyskać więcej informacji, zobacz [przykład TSTCON: kontener testów kontrolki ActiveX](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Zobacz też
- [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)
- [Kontrolki ActiveX](/cpp/mfc/activex-controls)