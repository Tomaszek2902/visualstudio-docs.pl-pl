---
title: Właściwości sesji wydajności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b3bafa976c8e57f468a3f3f59a3b6b19308fd1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74772205"
---
# <a name="performance-session-properties"></a>Właściwości sesji wydajności

**Sesja wydajności** umożliwia skonfigurowanie ustawień, które określają, w jaki sposób aplikacja jest profilowana. Przechowuje również raporty, które są generowane dla sesji profilowania.

**Sesję wydajności** można utworzyć, uruchamiając **Kreatora wydajności** lub ręcznie tworząc sesję. **Sesja wydajności** zostanie wyświetlona w **Eksplorator wydajności** po utworzeniu **sesji wydajności** .

Aby wyświetlić właściwości **sesji wydajności** , wybierz nazwę sesji w **Eksplorator wydajności**, kliknij ją prawym przyciskiem myszy, a następnie wybierz polecenie **Właściwości**.

Sesja wydajności ma następujące strony właściwości:

## <a name="general"></a>Ogólne

Te ustawienia umożliwiają wybranie metody profilowania, dodanie kolekcji obiektów .NET i danych okresu istnienia oraz określenie domyślnej lokalizacji raportu i konwencji nazewnictwa.

Aby uzyskać więcej informacji, zobacz:

[Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)

[Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Instrukcje: ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Uruchom

Te ustawienia umożliwiają wybranie z listy plików binarnych i określenie kolejności uruchamiania plików binarnych.

Aby uzyskać więcej informacji, zobacz [How to: Określ plik binarny do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>Próbkowanie

Te ustawienia umożliwiają wybranie przykładowego zdarzenia i interwału próbkowania, gdy próbkowanie jest używane jako metoda profilowania. Przykładowe zdarzenie służy do zbierania danych profilowania w określonym interwale. Na przykład jeśli przykładowe zdarzenie to cykle zegara, a interwał próbkowania jest ustawiony na 10 000 000, dane profilowania są zbierane po każdym cyklu 10 000 000 cykli zegara. Dostępne są następujące cztery typy przykładowych zdarzeń:

- Cykle zegara — w przypadku problemów związanych z procesorem CPU
- Błędy stron — w przypadku problemów związanych z pamięcią
- Wywołania systemowe — w przypadku problemów związanych we/wy
- Liczniki wydajności — w przypadku problemów z wydajnością niskiego poziomu
- Dodatkowe przykładowe zdarzenia można określić na podstawie dostępnych liczników wydajności

Aby uzyskać więcej informacji, zobacz [How to: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>Binarne
Te ustawienia umożliwiają określenie, czy chcesz przenieść plik binarny instrumentacji do innej lokalizacji. Na przykład jeśli tworzysz profilowanie *My.DLL* i nie chcesz przenosić plików binarnych z instrumentacją, tworzona jest kopia zapasowa *My.DLL* o nazwie *My.Orig.DLL* . Następnie *My.DLL* jest modyfikowany przez wstawianie sond do zbierania danych. Jeśli zdecydujesz się przenieść plik binarny z instrumentacją, oryginalny plik binarny nie jest zmieniany, a plik binarny Instrumentacji jest kopiowany do określonej lokalizacji do użycia podczas Instrumentacji.

Aby uzyskać więcej informacji, zobacz [How to: Określ plik binarny do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Interakcje warstw

Aby uzyskać więcej informacji, zobacz [zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>Oprzyrządowanie

Te ustawienia umożliwiają zbieranie danych wydajności dla kodu JScript na [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stronach sieci Web i określanie wszelkich zdarzeń **Pre-instrument** przedprodukcyjnych i **po** instrumentacji, które mają być wykonywane przed lub po tym procesie.

Aby uzyskać więcej informacji, zobacz:

[Instrukcje: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Instrukcje: określanie poleceń przed i po instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>Liczniki procesora CPU

Te ustawienia umożliwiają zbieranie danych o licznikach wydajności procesora CPU podczas korzystania z metody profilowania Instrumentacji. Przenośne liczniki wydajności są dostępne niezależnie od projektu lub producenta procesora. Zdarzenia platformy są specyficzne dla projektowania i producenta procesora CPU. Więcej informacji o licznikach wydajności mikroukładów znajduje się w dokumentacji dotyczącej określonego procesora.

Aby uzyskać więcej informacji, zobacz [jak: zbierać dane licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Zdarzenia systemu Windows

Podczas profilowania można zbierać dane od dostawców śledzenia zdarzeń. Dane można wyświetlić przy użyciu *VSPerfReport.exe* opcji narzędzia wiersza polecenia `/calltrace` . Aby uzyskać więcej informacji na temat śledzenia zdarzeń systemu Windows (ETW), zobacz [Informacje o śledzeniu zdarzeń](/windows/win32/etw/about-event-tracing).

Aby uzyskać więcej informacji, zobacz:

[Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Liczniki systemu Windows

Ta opcja umożliwia zbieranie danych z liczników monitora wydajności systemu Windows. Aby zebrać te dane, zaznacz pole wyboru z etykietą **Zbieranie liczników wydajności systemu Windows**. Interwał kolekcji można ustawić w polu **Interwał kolekcji** . **Kategoria licznika** i **wystąpienie** mogą być również dostępne. Dostępne są niektóre domyślne liczniki Monitora wydajności systemu Windows.

 Aby uzyskać więcej informacji, zobacz [jak: zbierać dane liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md).

## <a name="advanced"></a>Zaawansowany

Te ustawienia umożliwiają dodanie opcji do procesu instrumentacji przez określenie co najmniej jednej opcji narzędzia profilowania wiersza polecenia [VSInstr](../profiling/vsinstr.md) . Możesz również określić wersję wspólnego środowiska uruchomieniowego do profilowania, gdy aplikacja korzysta z więcej niż jednej wersji.

Aby uzyskać więcej informacji, zobacz:

[Instrukcje: określanie środowiska uruchomieniowego programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Instrukcje: określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Zobacz też

[Omówienia](../profiling/overviews-performance-tools.md) 
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md) 
 [Zbieranie danych sterujących](../profiling/controlling-data-collection.md)
