---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726312"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje obiekt tworzony przez spinacz w celu hermetyzowania wartości symboli i wyrażeń.

## <a name="syntax"></a>Składnia

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs, aby reprezentować obiekt.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest klasą bazową dla wszystkich obiektów używanych przez ewaluatora wyrażeń w wyrażeniach analizowanych. Jest zwracany przez wywołanie metody [bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) . Funkcja [QueryInterface](/cpp/atl/queryinterface) uzyskuje bardziej wyspecjalizowane interfejsy z tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugObject` .

|Metoda|Opis|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Pobiera rozmiar obiektu.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Pobiera wartość obiektu jako kolejne serie bajtów.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Ustawia wartość obiektu z kolejnej serii bajtów.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Ustawia wartość referencyjną tego obiektu.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Pobiera kontekst pamięci, który reprezentuje adres wartości obiektu.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Tworzy kopię zarządzanego obiektu w przestrzeni adresowej aparatu debugowania.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Sprawdza, czy ten obiekt jest odwołaniem o wartości null.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Porównuje obiekt z tym.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Określa, czy ten obiekt jest tylko do odczytu.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Określa, czy obiekt jest przezroczystym serwerem proxy.|

## <a name="remarks"></a>Uwagi
 Ewaluatora wyrażeń używa tego interfejsu jako klasy bazowej do reprezentowania obiektów w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Węglowodor](../../../extensibility/debugger/reference/idebugbinder-bind.md)
