---
title: Rejestrowanie niestandardowego aparatu debugowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a664385594f139e2c3c5a18a0d8a59e23c13df0a
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011843"
---
# <a name="register-a-custom-debug-engine"></a>Rejestrowanie niestandardowego aparatu debugowania
Aparat debugowania musi się zarejestrować jako fabryka klas, w ramach Konwencji COM, a także zarejestrować się w programie Visual Studio za pomocą podklucza rejestru programu Visual Studio.

> [!NOTE]
> Przykład sposobu rejestracji aparatu debugowania można znaleźć w przykładzie textinterpretera, który jest zbudowany jako część [samouczka: kompilowanie aparatu debugowania przy użyciu biblioteki ATL com](/previous-versions/bb147024(v=vs.90)).

## <a name="dll-server-process"></a>Proces serwera DLL
 Aparat debugowania jest zazwyczaj ustawiany we własnej bibliotece DLL jako serwer COM. W związku z tym aparat debugowania musi zarejestrować identyfikator CLSID fabryki klas z modelem COM, aby program Visual Studio mógł uzyskać do niego dostęp. Następnie aparat debugowania musi zarejestrować się przy użyciu programu Visual Studio, aby ustalić wszystkie właściwości (nazywane również metrykami) obsługiwane przez aparat debugowania. Wybór metryk Zapisano do podklucza rejestru programu Visual Studio zależy od funkcji obsługiwanych przez aparat debugowania.

 [Narzędzia zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) opisują nie tylko lokalizacje rejestru niezbędne do zarejestrowania aparatu debugowania. opisano w nim również bibliotekę *dbgmetric. lib* , która zawiera wiele przydatnych funkcji i deklaracji dla deweloperów języka C++, które ułatwiają manipulowanie rejestrem.

### <a name="example"></a>Przykład
 Poniższy przykład (z przykładu TextInterpreter) pokazuje, jak używać `SetMetric` funkcji (z *dbgmetric. lib*), aby zarejestrować aparat debugowania w programie Visual Studio. Przesyłane metryki są również zdefiniowane w *dbgmetric. lib*.

> [!NOTE]
> TextInterpreter to podstawowy aparat debugowania; nie jest on skonfigurowany i w związku z tym nie jest rejestrowany — wszystkie inne funkcje. Bardziej kompletny aparat debugowania będzie miał pełną listę `SetMetric` wywołań lub ich odpowiedniki, po jednym dla każdej funkcji obsługiwanej przez aparat debugowania.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Pomocnicy zestawu SDK na potrzeby debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Samouczek: kompilowanie aparatu debugowania przy użyciu biblioteki ATL COM](/previous-versions/bb147024(v=vs.90))