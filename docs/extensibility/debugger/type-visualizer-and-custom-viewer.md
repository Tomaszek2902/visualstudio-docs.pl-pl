---
title: Wizualizator typów i Podgląd niestandardowy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712464"
---
# <a name="type-visualizer-and-custom-viewer"></a>Wizualizator typów i Podgląd niestandardowy
Wizualizator typu jest składnikiem, który wyświetla dane w określonym formacie. Format jest całkowicie do osoby, która implementuje wizualizator, być użytkownikiem końcowym lub innym osobom wizualizatora.

 Przeglądarka niestandardowa jest częścią niestandardowej ewaluatora wyrażeń, która wyświetla dane w określonym formacie. Ten format jest całkowicie do realizatora niestandardowej przeglądarki, co oznacza, że format jest do realizatora ewaluatora wyrażeń (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa wizualizatorów typów w ewaluatora wyrażeń
 Program EE obsługuje Wizualizatory typów poprzez obsługę zestawu interfejsów dostępnych dla wizualizatorów: interfejsów, takich jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) i [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Jednak EE nie jest odpowiedzialny za wdrożenie wizualizatora typu: EE tylko umożliwia zewnętrznym wizualizatorom dostęp do informacji o typie. Takie Wizualizatory mogą być dostarczane wraz z EE i instalowane w odpowiednim miejscu w programie Visual Studio, dostarczane przez innego dostawcę innych firm, a nawet przez użytkownika końcowego.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa niestandardowych podglądów w ewaluatora wyrażeń
 W przypadku usługi EE można także obsługiwać niestandardowe osoby przeglądające, w których sama EE dostarczają kod służący do wyświetlania typu danych. Niestandardowa przeglądarka implementuje interfejs [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , który obsługuje wszystkie zadania pokazywania danych w dowolnym formacie. Podgląd ma pełną kontrolę nad wyświetlaniem i może nawet zezwolić na modyfikowanie danych. Wszystkie niestandardowe osoby przeglądające dostarczane przez program EE są dostarczane z EE, gdy produkt jest dostarczany.

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
