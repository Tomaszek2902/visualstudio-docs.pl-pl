---
title: Konfigurowanie projektu usługi w chmurze platformy Azure
description: Dowiedz się, jak skonfigurować projekt usługi w chmurze platformy Azure w programie Visual Studio, w zależności od wymagań dla tego projektu.
author: ghogen
manager: jillfra
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: bc56163c5fe2e6f52eed7db1d75d8e6194dfce7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62989844"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Konfigurowanie projektu usługi w chmurze platformy Azure przy użyciu programu Visual Studio
Możesz skonfigurować projekt usługi w chmurze platformy Azure, w zależności od wymagań dla tego projektu. Można ustawić właściwości projektu dla następujących kategorii:

- **Publikowanie usługi w chmurze na platformie Azure** — Właściwość można ustawić, aby upewnić się, że istniejąca usługa w chmurze wdrożona na platformie Azure nie została przypadkowo usunięta.
- **Uruchom lub Debuguj usługę w chmurze na komputerze lokalnym** — możesz wybrać konfigurację usługi do użycia i wskazać, czy chcesz uruchomić emulator usługi Azure Storage.
- **Sprawdza poprawność pakietu usługi w chmurze podczas jego tworzenia** — możesz zdecydować się na podjęcie wszelkich ostrzeżeń jako błędów, aby upewnić się, że pakiet usługi w chmurze zostanie wdrożony bez żadnych problemów.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Procedura konfigurowania projektu usługi w chmurze platformy Azure
1. Otwieranie lub tworzenie projektu usługi w chmurze w programie Visual Studio

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Właściwości**.

1. Na stronie właściwości projektu wybierz kartę **programowanie** .

    ![Menu właściwości projektu](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Ustaw **wiersz polecenia przed usunięciem istniejącego wdrożenia** do **wartości true**. To ustawienie pomaga upewnić się, że nie usunięto przypadkowo istniejącego wdrożenia na platformie Azure

1. Wybierz żądaną **konfigurację usługi** , aby wskazać konfigurację usługi, która ma być używana podczas lokalnego uruchamiania lub debugowania usługi w chmurze. Aby uzyskać więcej informacji na temat modyfikowania konfiguracji usługi dla roli, zobacz [jak skonfigurować role dla usługi w chmurze platformy Azure za pomocą programu Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Ustaw **początkowy emulator usługi Azure Storage** na **wartość true** , aby uruchomić emulator usługi Azure Storage, gdy uruchamiasz lub debugujesz lokalną usługę w chmurze.

1. Dla opcji **Traktuj ostrzeżenia jako błędy** wybierz **wartość true** , aby upewnić się, że nie można opublikować w przypadku wystąpienia błędów walidacji pakietu.

1. Ustaw dla **opcji Użyj portów projektu sieci Web** **wartość true** , aby upewnić się, że rola sieci Web używa tego samego portu przy każdym uruchomieniu lokalnym w IIS Express.

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="next-steps"></a>Następne kroki
- [Konfigurowanie projektu platformy Azure przy użyciu wielu konfiguracji usługi](vs-azure-tools-multiple-services-project-configurations.md)
