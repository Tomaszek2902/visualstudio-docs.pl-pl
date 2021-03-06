---
title: Plik konfiguracji devinit
description: Dokumentacja .devinit.jsw pliku manifestu dla devinit.
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
ms.openlocfilehash: b0cfb1c41d7721598bae44f950ced01d17ff494a
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005361"
---
# <a name="devinit-configuration-file"></a>plik konfiguracji devinit

## <a name="file-location"></a>Lokalizacja pliku

`devinit.exe init`Polecenie jest realizowane za pośrednictwem _.devinit.js_ pliku. Domyślnie program `devinit.exe` szuka pliku w następujących lokalizacjach:

- _{Current-Directory}\\_
- _{Current-Directory} \\ . devinit\\_
- _{Current-Directory} \\ . devcontainer\\_

_._ w katalogu i nazwy plików można pominąć.

_.devinit.jsw_ pliku można również jawnie określić za pomocą `--file` / `-f` opcji.

### <a name="directories-and-relative-paths"></a>Katalogi i ścieżki względne

Ścieżki są względne dla lokalizacji, w której działa devinit. Jest to zazwyczaj bieżący katalog roboczy, z którego `devinit` wykonano.

## <a name="file-format"></a>Format pliku

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Wartości właściwości

| Nazwa         | Typ   | Wymagane | Wartość                              |
|--------------|--------|----------|------------------------------------|
| **komentarz** | ciąg | Nie       | Komentarze do pliku.             |
| **wykonane**      | array  | Tak      | [Obiekt RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Uruchom obiekt narzędzia

| Nazwa                  | Typ   | Wymagane | Wartość                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **komentarz**          | ciąg | Nie       | Komentarze dotyczące wpisu narzędzia.                                                                               |
| **narzędziem**              | ciąg | Tak      | Nazwa narzędzia. Zobacz `devinit list` polecenie, aby uzyskać listę dostępnych narzędzi.                            |
| **klawiatur**             | ciąg | Nie       | Dane wejściowe narzędzia. Różni się według narzędzia. Na przykład wymagana wersja, identyfikator pakietu, nazwa pliku lub folder.|
| **additionalOptions** | ciąg | Nie       | Dodatkowe argumenty wiersza polecenia, które mają zostać przekazane do narzędzia.                                                |

## <a name="examples"></a>Przykłady

Aby uzyskać więcej przykładów użycia devinit, zobacz [sekcję Samples (przykłady](sample-readme.md)).
