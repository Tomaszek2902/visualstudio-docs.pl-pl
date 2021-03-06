---
title: Generowanie plików za pomocą narzędzia TextTransform
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec659bfee9253dfb198c2747e1b5d7fb6b78f2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596557"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generowanie plików za pomocą narzędzia TextTransform

TextTransform.exe jest narzędziem wiersza polecenia, które służy do przekształcania szablonu tekstu. Podczas wywoływania TextTransform.exe należy określić nazwę pliku szablonu tekstu jako argument. TextTransform.exe wywołuje aparat transformacji tekstu i przetwarza szablon tekstu. TextTransform.exe jest zazwyczaj wywoływana ze skryptów. Jednak zazwyczaj nie jest to wymagane, ponieważ można wykonać transformację tekstu w Visual Studio lub w procesie kompilacji.

> [!NOTE]
> Jeśli chcesz przeprowadzić transformację tekstu jako część procesu kompilacji, rozważ użycie zadania transformacji tekstu programu MSBuild. Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md). Na komputerze, na którym jest zainstalowany program Visual Studio, możesz również napisać rozszerzenie aplikacji lub programu Visual Studio, które umożliwia przekształcanie szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform.exe znajduje się w następującym katalogu:

::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

w wersji Professional lub

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

w wersji Enterprise.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

w wersji Professional lub

**\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

w wersji Enterprise.

W poprzednich wersjach programu Visual Studio plik znajduje się w następującej lokalizacji:

**\Program Files (x86) \Common Files\Microsoft Shared\TextTemplating \{ Version}**

miejsce, w którym zainstalowano poprzednią wersję, zależy od wersji {Version}.

::: moniker-end

## <a name="syntax"></a>Składnia

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|-|-|
|`templateName`|Określa nazwę pliku szablonu, który ma zostać przekształcony.|

|**Opcja**|**Opis**|
|-|-|
|**-out** \<filename>|Plik, do którego zostanie zapisany wynik transformacji.|
|**-r**\<assembly>|Zestaw używany do kompilowania i uruchamiania szablonu tekstu.|
|**-u**\<namespace>|Przestrzeń nazw, która jest używana do kompilowania szablonu.|
|**-I**\<includedirectory>|Katalog zawierający szablony tekstowe zawarte w określonym szablonie tekstu.|
|**-P**\<referencepath>|Katalog, w którym mają zostać wyszukane zestawy określone w szablonie tekstowym lub przy użyciu opcji **-r** .<br /><br /> Na przykład, aby dołączyć zestawy używane dla interfejsu API programu Visual Studio, użyj<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className>\<assemblyName&#124;codeBase>|Nazwa, pełna nazwa typu oraz zestaw procesorów dyrektywy, których można użyć do przetwarzania dyrektyw niestandardowych w ramach szablonu tekstu.|
|**-a** [procesorname]! [dyrektywaname]! \<parameterName> !\<parameterValue>|Określ wartość parametru procesora dyrektywy. W przypadku określenia tylko nazwy parametru i wartości, parametr będzie dostępny dla wszystkich procesorów dyrektywy. Jeśli określisz procesor dyrektywy, parametr jest dostępny tylko dla określonego procesora. Jeśli określisz nazwę dyrektywy, parametr jest dostępny tylko wtedy, gdy określona dyrektywa jest przetwarzana.<br /><br /> Aby uzyskać dostęp do wartości parametrów z procesora dyrektywy lub szablonu tekstu, należy użyć [ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). W szablonie tekstowym Dołącz do `hostspecific` dyrektywy Template i Wywołaj komunikat `this.Host` . Na przykład:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zawsze należy wpisywać znaczniki "!", nawet w przypadku pominięcia opcjonalnych nazw procesorów i dyrektyw. Na przykład:<br /><br /> `-a !!param!value`|
|**-h**|Zapewnia pomoc.|

## <a name="related-topics"></a>Powiązane tematy

|Zadanie|Temat|
|-|-|
|Generuj pliki w rozwiązaniu programu Visual Studio.|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Napisz procesory dyrektywy, aby przekształcić własne źródła danych.|[Dopasowanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md)|
|Napisz hosta tworzenia szablonów tekstu, który umożliwia wywoływanie szablonów tekstowych z własnej aplikacji.|[Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)|
