---
title: Debugowanie kontrolki ActiveX powiązanej z danymi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6945d1ccf72385b4d2fbe76736668e84b804e446
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686755"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debugowanie kontrolki ActiveX powiązanego z danymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli tworzysz formant ActiveX, który zostanie powiązany z kontrolą źródła danych, możesz utworzyć własną aplikację kontenera i użyć tego kontenera do debugowania kontrolki ActiveX.  
  
 Na przykład możesz utworzyć aplikację MFC opartą na oknach dialogowych i umieścić formant powiązany z danymi oraz formant źródła danych w oknie dialogowym. Ta aplikacja MFC służy do testowania w czasie wykonywania oraz jako plik wykonywalny kontenera do debugowania formantu ActiveX powiązanego z danymi.  
  
## <a name="using-the-test-container"></a>Korzystanie z kontenera testów  
 Jeśli chcesz, aby kontener, który można łatwo zmodyfikować, aby obsługiwał różne interfejsy na formancie lub kontenerze, Użyj kontenera testów ActiveX jako pliku wykonywalnego dla sesji debugowania. W kontenerze Test ActiveX kliknij pozycję **Opcje** z menu **kontener** , aby włączyć różne interfejsy. Aby uzyskać więcej informacji, zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testów](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Jeśli musisz umieścić w kodzie kontenera podczas debugowania, użyj wersji debugowania kontenera lub użyj wersji debugowania kontenera testów ActiveX. Aby uzyskać więcej informacji, zobacz [przykład TSTCON: kontener testów kontrolki ActiveX](https://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie modelu COM i ActiveX](../debugger/com-and-activex-debugging.md)   
 [Kontrolki ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
