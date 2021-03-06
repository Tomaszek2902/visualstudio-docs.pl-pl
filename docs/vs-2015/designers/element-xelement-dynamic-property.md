---
title: Element (właściwość dynamiczna XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c6171a5dedfd6985a6f54e748011bf86e03f4d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664650"
---
# <a name="element-xelement-dynamic-property"></a>Element (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera indeksator używany do pobrania wystąpienia elementu podrzędnego, który odnosi się do określonej rozwiniętej nazwy.

## <a name="syntax"></a>Składnia

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 Indeksator typu `XElement Item(String expandedName)` . Ten indeksator przyjmuje rozwinięty parametr name i zwraca odpowiednie <xref:System.Xml.Linq.XElement> lub `null` Jeśli nie ma elementu o określonej nazwie.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Element%2A> metodzie <xref:System.Xml.Linq.XContainer?displayProperty=fullName> klasy.

## <a name="see-also"></a>Zobacz też
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>[Elementy](../designers/elements-xelement-dynamic-property.md) [właściwości dynamicznych klasy XElement](../designers/xelement-class-dynamic-properties.md)
