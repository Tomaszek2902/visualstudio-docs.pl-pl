---
title: Zbieranie śladu ETL za pomocą narzędzia PerfView
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 9ac4d90a0da15fe2415ada02d6e8e1cdbe11af56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770820"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Zbieranie śladu ETL za pomocą narzędzia PerfView

Narzędzia PerfView to narzędzie, które tworzy pliki ETL (Dziennik śledzenia zdarzeń) w oparciu o [Śledzenie zdarzeń systemu Windows](/windows/desktop/ETW/event-tracing-portal) , które mogą być przydatne podczas rozwiązywania problemów niektórych rodzajów problemów z programem Visual Studio. Czasami w przypadku zgłaszania problemu zespół produktu może zażądać uruchomienia programu narzędzia PerfView w celu zebrania dodatkowych informacji.

## <a name="install-perfview"></a>Zainstaluj narzędzia PerfView

Pobierz narzędzia PerfView z usługi [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Uruchom narzędzia PerfView

1. Kliknij prawym przyciskiem myszy pozycję **PerfView.exe** w Eksploratorze Windows i wybierz polecenie **Uruchom jako administrator** jako administrator
1. W menu zbieranie wybierz polecenie **Zbierz**
1. Sprawdź plik **zip**, **Scal**i **ThreadTime**.
1. Zwiększ liczbę **okrągłych MB** do 1000.
1. Zmień **bieżący katalog** na Zapisz ślady ETL w określonym folderze i pliku danych, jeśli chcesz zbierać więcej niż jeden raz.
1. Aby rozpocząć rejestrowanie danych, wybierz przycisk **Rozpocznij zbieranie** .
1. Aby zatrzymać rejestrowanie danych, wybierz przycisk **Zatrzymaj zbieranie** . Plik PrefView.etl.zip zostanie zapisany w określonym katalogu.

Narzędzia PerfView może przechowywać tylko najnowsze dane, które pasują do buforu. W związku z tym spróbuj zatrzymać zbieranie najszybciej, jak to możliwe po rozpoczęciu lub spowolnieniu programu Visual Studio. Nie Zbieraj dłużej niż 30 sekund po napotkaniu problemu.

Aby uzyskać więcej informacji, zobacz [samouczek narzędzia PerfView na channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
