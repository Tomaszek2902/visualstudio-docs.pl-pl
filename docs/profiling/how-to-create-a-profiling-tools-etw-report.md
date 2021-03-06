---
title: Tworzenie raportu ETW narzędzia profilowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 13de203a6a9082b33f5d68f8b4e2fbdc6f0e14b3
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851193"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Instrukcje: Tworzenie raportu ETW narzędzi profilowania
Raport śledzenie zdarzeń systemu Windows (ETW) zawiera listę zdarzeń ETW, które są rejestrowane w sesji wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania. Dane ETW są zbierane w postaci binarnej (.* ETL*). Aby uzyskać więcej informacji na temat tego raportu, zobacz [raport śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> W interfejsie nie można wyświetlać raportów ETW [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Informacje o sposobie zbierania danych ETW przy użyciu interfejsu dla programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] znajdują się w temacie [How to: zbierać dane śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Informacje o sposobie zbierania danych ETW z wiersza polecenia można znaleźć w temacie [VSPerfCmd](../profiling/vsperfcmd.md) and [Events (zdarzenia](../profiling/events-vsperfcmd.md)).

  Raport ETW jest generowany przy użyciu polecenia **VSReport/Summary: ETW** . Polu. *ETL* zawierający dane ETW musi znajdować się w tym samym katalogu co dane profilowania (.* VSP* lub. *vsps*) rozszerzeniem. Domyślnie raport jest generowany w postaci wartości rozdzielanych przecinkami (.* CSV*). Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Aby wygenerować raport ETW

- W oknie **wiersza polecenia** wpisz w wierszu polecenia następujący tekst:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary: ETW [/XML]**

    |Element|Opis|
    |-|-|
    |*ToolsPath*|Ścieżka narzędzia narzędzia profilowania. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Dane profilowania (.* VSP* lub. *vsps*) rozszerzeniem. Akceptowane są pełne i częściowe ścieżki.|
    |Xml|Generuje raport sformatowany w formacie XML.|
