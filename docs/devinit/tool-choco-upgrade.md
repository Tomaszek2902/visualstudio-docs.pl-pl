---
title: choco-upgrade
description: devinit narzędzia Choco-Upgrade.
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
ms.openlocfilehash: 5a735b60fd318d86e97dc4db7570e952a0fcdfd8
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006037"
---
# <a name="choco-upgrade"></a>choco-upgrade

Za `choco-upgrade` pomocą tego narzędzia można instalować i aktualizować pakiety [czekoladowe](https://chocolatey.org/docs/commandsupgrade) .

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie nie będzie niczego robić.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                                          |
| [**klawiatur**](#input)                              | ciąg | Nie       | Pakiet do uaktualnienia. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                                                 |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Dodatkowe opcje do przekazania do narzędzia. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.       |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określenia nazwy pakietu do uaktualnienia (na przykład "MongoDB") lub ścieżki do pliku konfiguracji następujących formatów _packages.config_, _. nuspec_i _. nupkg_. Wartość `input` zostanie dołączona do `choco upgrade` polecenia (na przykład `choco upgrade mongodb` ) wraz z dowolnymi argumentami określonymi w [`additionalOptions`](#additional-options) i wbudowane `choco` Opcje (zdefiniowane [poniżej](#built-in-options)). Pakiety można znaleźć w [Galerii pakietów czekolady](https://chocolatey.org/packages). Przy użyciu pliku konfiguracji można przekazać ścieżkę do tego pliku we `input` właściwości na przykład: `"input":"packages.config"` .

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do argumentów używanych przez [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) i są zdefiniowane w dokumentacji czekoladowej.

## <a name="built-in-options"></a>Wbudowane opcje

`choco-upgrade`Narzędzie ustawia wiele `choco` argumentów wiersza polecenia, aby zapewnić `choco` możliwość uruchamiania bezobsługowego. Te argumenty są wymienione poniżej i dokumentacja na nich znajduje się w [dokumentacji czekoladowej](https://chocolatey.org/docs/).

| Nazwa                  | Opis                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--tak**             | Potwierdź wszystkie monity — wybierają odpowiedź twierdzącą zamiast monitowania. Oznacza `--accept-license` . |
| **--No-Progress**     | Nie pokazuj postępów — procent postępu nie będzie pokazywany.                                         |
| **--Skip-PowerShell** | Pomijanie programu PowerShell — chocolateyInstall.ps1 nie zostanie uruchomiony.                                              |

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of upgrading packages listed in a packages.config file.",
            "tool": "choco-upgrade",
            "input": "packages.config",
        },
        {
            "comments": "Example that will upgrade the package 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb"
        },
        {
            "comments": "Example that will upgrade the '4.2.7' version of 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```
