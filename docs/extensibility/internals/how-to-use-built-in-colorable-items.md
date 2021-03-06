---
title: 'Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 762d1e53f7aafa11ed345859e68fc98766eec77d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905220"
---
# <a name="how-to-use-built-in-colorable-items"></a>Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania
Przed użyciem wbudowanych elementów, należy najpierw zasygnalizować zintegrowane środowisko programistyczne (IDE), które nie udostępniają własnych niestandardowych elementów, które w tym przypadku byłyby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> obiektami. W tym celu należy ustawić wpis rejestru dla usługi językowej.

## <a name="to-use-built-in-colorable-items"></a>Aby używać wbudowanych elementów z możliwością kolorowania

1. W obszarze **HKEY_LOCAL_MACHINE \visualstudio \\<X. Y> \languages\language Services \\<nazwa \> języka**, gdzie \<X.Y> jest wersją [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i \<Language Name> jest nazwą języka, utwórz wartość wpisu rejestru DWORD o nazwie **RequestStockColors**.

2. Ustaw wartość wpisu rejestru **RequestStockColors** na *1*.

    Po utworzeniu wpisu rejestru Metoda kolorowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> może użyć elementów członkowskich <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> wyliczenia, aby wypełnić tablicę atrybutów koloru używanych przez Edytor.

   > [!NOTE]
   > Nie ustawiaj tego wpisu rejestru, jeśli udostępniasz elementy niestandardowe. Aby uzyskać więcej informacji, zobacz [niestandardowe elementy do wykonania](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Zobacz też
- [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementy niestandardowe z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)
