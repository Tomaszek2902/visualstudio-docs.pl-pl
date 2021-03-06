---
title: Powiadamianie portu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738326"
---
# <a name="notify-the-port"></a>Powiadom port
Po uruchomieniu programu należy powiadomić port w następujący sposób:

1. Gdy port odbiera nowy węzeł programu, wysyła zdarzenie tworzenia programu z powrotem do sesji debugowania. To zdarzenie jest interfejsem, który reprezentuje program.

2. Sesja debugowania wysyła zapytanie do programu w celu uzyskania identyfikatora aparatu debugowania (DE), który może zostać dołączony do.

3. Sesja debugowania sprawdza, czy znajduje się na liście dozwolonych algorytmów DEs dla tego programu. Sesja debugowania pobiera tę listę z ustawień aktywnego programu rozwiązania, które zostały pierwotnie przesłane do niego przez pakiet debugowania.

    DE musi znajdować się na liście dozwolonych lub w innym przypadku nie zostanie dołączony do programu.

   Programowo, gdy port odbierze nowy węzeł programu, tworzy interfejs [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) do reprezentowania programu.

> [!NOTE]
> Nie należy mylić tego `IDebugProgram2` interfejsu z interfejsem utworzonym później przez aparat debugowania (de).

 Port wysyła zdarzenie tworzenia programu [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) z powrotem do Menedżera debugowania sesji (SDM) za pomocą `IConnectionPoint` interfejsu com.

> [!NOTE]
> Nie należy mylić tego `IDebugProgramCreateEvent2` interfejsu, który jest wysyłany później przez de.

 Wraz z samym interfejsem zdarzenia port wysyła interfejsy [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)i [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , które reprezentują odpowiednio port, proces i program. Model SDM wywołuje [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) , aby uzyskać identyfikator GUID de, który może debugować program. Identyfikator GUID został pierwotnie uzyskany z interfejsu [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

 Model SDM sprawdza, czy znajduje się na liście dozwolonych algorytmów DEs. Model SDM pobiera tę listę z ustawień aktywnego programu rozwiązania, pierwotnie przekazaną do niej przez pakiet debugowania. Element DE musi znajdować się na liście dozwolonych lub nie zostanie dołączony do programu.

 Gdy tożsamość jest znana, model SDM jest gotowy do dołączenia do programu.

## <a name="see-also"></a>Zobacz też
- [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)
- [Dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
