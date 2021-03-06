---
title: Rozszerzalność debugera programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983665"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzalność debugera programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Program Visual Studio zawiera w pełni interaktywny debuger kodu źródłowego, który zapewnia zaawansowane i łatwe w użyciu narzędzie do śledzenia błędów w programie. Debuger ma pełną pomoc techniczną Visual Basic, C#, C/C++ i JavaScript. Jednak w przypadku programu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , który jest dostępny w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), inne języki programowania mogą być obsługiwane w debugerze z tymi samymi, bogatymi funkcjami.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Debuger jest wspólnym frontonem (czyli interfejsem użytkownika) do składników debugowania, które są z kolei charakterystyczne dla debugowanego języka. W przypadku nowych języków wszystkie te, które są niezbędne do obsługi przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debuger, to tworzenie niezbędnych składników zaplecza, takich jak aparat debugowania (de). Jest to miejsce, w którym się znajduje [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Obejmuje kompletne odwołanie do wszystkich [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementów wymaganych do utworzenia nowego elementu de. Ponadto istnieją przykłady i samouczki, które pomogą Ci rozpocząć pracę.  
  
 Aby uzyskać kompleksowy przykład systemu projektu języka z obsługą debugowania, zobacz [przykład IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 W poniższych sekcjach opisano, jak zwiększyć debuger za pomocą [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Opisuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , jakie oferty debugowania oraz jak zainstalować zestaw SDK.  
  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Dokumentuje niestandardowy proces usuwania od przygotowania programu do odłączenia.  
  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Wyjaśnia, czy należy napisać ewaluatora wyrażeń.  
  
 [Wybieranie strategii implementacji aparatu debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 W tym artykule omówiono sposób implementacji programu DE.  
  
 [Odwołanie](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumentuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejs API debugowania.  
  
 [Samples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Zawiera linki do przykładowej ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego i próbki aparatu debugowania.
