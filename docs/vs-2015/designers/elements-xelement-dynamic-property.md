---
title: Elementy (właściwość dynamiczna XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664691"
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera indeksator używany do pobierania elementów podrzędnych bieżącego elementu, który jest zgodny z określoną rozwiniętą nazwą.

## <a name="syntax"></a>Składnia

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 Indeksator typu `IEnumerable<XElement> Item(String expandedName)` . Ten indeksator przyjmuje rozwiniętą nazwę żądanych elementów podrzędnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest równoważna z <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> metodą <xref:System.Xml.Linq.XContainer> klasy.

 Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu źródłowego XML.

 Ta właściwość używa wykonania odroczonego.

## <a name="see-also"></a>Zobacz też
 [Elementy podrzędne](../designers/descendants-xelement-dynamic-property.md) [elementów](../designers/element-xelement-dynamic-property.md) [właściwości dynamicznych klasy XElement](../designers/xelement-class-dynamic-properties.md)
