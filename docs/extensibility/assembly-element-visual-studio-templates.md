---
title: Assembly — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740032"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly — element (szablony Visual Studio)
Określa informacje dotyczące zestawu, którego szablon używa do dodawania odwołania do tego zestawu do projektów.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>Składnia

```
<Assembly> AssemblyName </Assembly>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Odwołanie](../extensibility/reference-element-visual-studio-templates.md)|Określa odwołanie do zestawu, które ma zostać dodane, gdy element zostanie dodany do projektu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ten tekst Określa zestaw, który ma zostać dodany do projektu po utworzeniu wystąpienia szablonu elementu. Ta nazwa zestawu musi być określona w jeden z następujących sposobów:

- Jako pełna nazwa zestawu. Na przykład:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Jako proste odwołanie do tekstu. Na przykład:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Uwagi
 `Assembly` jest wymaganym elementem podrzędnym `Reference` .

 `Reference` `References,` `Assembly` Elementy i mogą być używane tylko w plikach *. vstemplate* , które mają `Type` wartość atrybutu `Item` .

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje `TemplateContent` element szablonu elementu. Ten kod XML dodaje odwołania do zestawów *System.dll* i *System.Data.dll* .

```
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
