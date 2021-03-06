---
title: wsl-install
description: devinit narzędzie WSL — Zainstaluj.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 950ca7f1e9c43123b206893dbc6a07da7c3743ec
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862856"
---
# <a name="wsl-install"></a>wsl-install

`wsl-install`Narzędzie to służy do instalowania dystrybucje systemu Linux dla [podsystemu Windows w systemie Linux](/windows/wsl/) (WSL).

`wsl-install`Narzędzie wymaga, aby WSL 2 było już włączone w systemie Windows. Jeśli z jakiegoś powodu WSL2 nie jest włączona, można włączyć WSL2 przy użyciu narzędzia [WindowsFeature-Enable](tool-windowsfeature-enable.md) i nazwy funkcji `Microsoft-Windows-Subsystem-Linux` .

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                             |
| [**klawiatur**](#input)                              | ciąg | Tak      | Dystrybucji do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .     |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.  |

### <a name="input"></a>Dane wejściowe

Identyfikator URI pakietu dystrybucji aplikacji AppX ( `.appx` ) zawierającego dystrybucji do wdrożenia. Identyfikator URI musi wskazywać na `.appx` archiwum, które zawiera jeden z nich `install.tar.gz` w katalogu głównym archiwum lub wewnątrz Archiwum wewnętrznym `.appx` . Przykłady obsługiwanych dystrybucje obejmują:

| Dystrybucji                          | Adresu                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE przestępnie 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> System ARM Linux dystrybucje nie jest obecnie obsługiwany w usłudze GitHub Codespaces.

### <a name="additional-options"></a>Opcje dodatkowe

Obsługiwane są wiele dodatkowych opcji:

| Nazwa                      | Typ      | Wymagane | Wartość                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-Version             | ciąg    | Nie       | WSL wersja do użycia. Wartość domyślna to 2.                                                                                                                                  |
| --Po utworzeniu polecenia     | ciąg    | Nie       | Polecenie do wykonania w dystrybucji systemu Linux po zakończeniu instalacji. Polecenie powinno być sformatowane jako pojedyncze słowo lub opakowane w cudzysłów. Wartość domyślna to No.  |

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `wsl-install` narzędzia to błąd, który jest `input` wymagany do zainstalowania dystrybucji.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and echo 'Hello from Ubuntu!' after installing.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```