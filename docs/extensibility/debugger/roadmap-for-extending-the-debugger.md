---
title: Plan rozszerzający debuger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d97a7edd62540d12a0a60d15b3179ca0a623c26
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011830"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plan rozszerzający debuger
Ta dokumentacja zawiera przewodnik i informacje referencyjne dotyczące rozszerzania [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] debugera za pomocą narzędzia [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dokumentacja dotycząca debugowania obejmuje przykłady, kompleksowe odwołanie i kilka reprezentatywnych scenariuszy, które przedstawiają typowe sposoby dostosowywania debugera.

 Kompilator i jego dane wyjściowe określają, co jest wymagane do skonfigurowania debugowania w produkcie. Jeśli kompilator:

- Jest przeznaczony dla systemu operacyjnego Windows Native i zapisuje *. Plik PDB* , można debugować programy z aparatem debugowania kodu natywnego (de), który jest zintegrowany z programem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Nie trzeba implementować Ewaluatora wyrażenia a ani. Ewaluatora wyrażeń jest zapisywana dla składni języka programowania C++.

- Tworzy dane wyjściowe języka pośredniego firmy Microsoft (MSIL), można debugować programy z aparatem debugowania kodu zarządzanego DE, który również jest zintegrowany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . W tym celu należy zaimplementować tylko ewaluatora wyrażeń. Zostanie udostępniona Przykładowa ewaluatora wyrażeń. Aby uzyskać więcej informacji, zobacz następujące tematy:

   [Obliczanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Ocenianie wyrażeń](../../extensibility/debugger/evaluating-expressions.md)

   [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md)

   [Obliczanie wyrażeń w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Napisz ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Dotyczy zastrzeżonego systemu operacyjnego lub innego środowiska wykonawczego, należy napisać własne. Podano samouczek, który tworzy prostą i nieużywaną ATL COM. Aby uzyskać więcej informacji, zobacz następujące tematy:

   [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Samouczek: Tworzenie aparatu debugowania przy użyciu biblioteki ATL COM](/previous-versions/bb147024(v=vs.90))

   [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Samples](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)